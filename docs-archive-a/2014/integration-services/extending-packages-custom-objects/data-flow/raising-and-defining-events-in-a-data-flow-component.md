---
title: Provocar y definir eventos en un componente de flujo de datos | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow components [Integration Services], events
- events [Integration Services], custom
- custom events [Integration Services]
- custom data flow components [Integration Services], events
- events [Integration Services], raising
- predefined events [Integration Services]
ms.assetid: 1d8c5358-9384-47a8-b7cb-7b0650384119
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 25f4572f8a8af829145da4e4d685f5dddad4a29a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744779"
---
# <a name="raising-and-defining-events-in-a-data-flow-component"></a>Provocar y definir eventos en un componente de flujo de datos
  Los desarrolladores de componentes pueden producir un subconjunto de los eventos definido en la interfaz <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> mediante una llamada a los métodos expuestos en la propiedad <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A>. También puede definir eventos personalizados con la colección <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A> y provocarlos durante la ejecución con el método <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>. En esta sección se describe cómo crear y provocar un evento y se proporcionan instrucciones sobre el momento en que se deben provocar los eventos en tiempo de diseño.

## <a name="raising-events"></a>Provocar eventos
 Los componentes generan eventos mediante los métodos **Fire\<X>** de la interfaz <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>. Puede provocar eventos durante el diseño y la ejecución de los componentes. Normalmente, en el diseño de los componentes, se llama a los métodos <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> y <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A> durante la validación. Estos eventos muestran mensajes en el panel **Lista de errores** de [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] y proporcionan información a los usuarios del componente cuando este está configurado incorrectamente.

 Los componentes también pueden provocar eventos en cualquier momento durante la ejecución. Los eventos permiten a los programadores de componentes proporcionar información a los usuarios del componente cuando éste se ejecuta. Es probable que la llamada al método <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> durante la ejecución produzca un error en el paquete.

## <a name="defining-and-raising-custom-events"></a>Definir y provocar eventos personalizados

### <a name="defining-a-custom-event"></a>Definir un evento personalizado
 Los eventos personalizados se crean mediante una llamada al método <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> de la colección <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A>. La tarea de flujo de datos establece esta colección, que se proporciona al programador de componentes a través de la clase base <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>. Esta clase contiene eventos personalizados definidos por la tarea de flujo de datos y eventos personalizados definidos por el componente durante el método <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A>.

 Los eventos personalizados de un componente no se conservan en el paquete XML. Por tanto, se llama al método <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> durante el diseño y la ejecución para permitir al componente definir los eventos que provoca.

 El parámetro *allowEventHandlers* del método <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> especifica si el componente permite crear objetos <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> para el evento. Observe que los objetos <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> son sincrónicos. Por tanto, el componente no reanuda la ejecución hasta que ha terminado de ejecutarse un objeto <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> adjuntado al evento personalizado. Si el parámetro *allowEventHandlers* es `true` , cada parámetro del evento pasa a estar disponible automáticamente para cualquier <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> objeto a través de variables que se crean y rellenan automáticamente en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] tiempo de ejecución.

### <a name="raising-a-custom-event"></a>Provocar un evento personalizado
 Los componentes provocan eventos personalizados mediante una llamada al método <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> y proporcionando el nombre, texto y parámetros del evento. Si el parámetro *allowEventHandlers* es `true` , <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> el motor en tiempo de ejecución ejecuta cualquier que se cree para el evento personalizado [!INCLUDE[ssIS](../../../includes/ssis-md.md)] .

### <a name="custom-event-sample"></a>Ejemplo de evento personalizado
 En el ejemplo de código siguiente se muestra un componente que define un evento personalizado durante el método <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> y, a continuación, provoca el evento en tiempo de ejecución mediante una llamada al método <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>.

```csharp
public override void RegisterEvents()
{
    string [] parameterNames = new string[2]{"RowCount", "StartTime"};
    ushort [] parameterTypes = new ushort[2]{ DtsConvert.VarTypeFromTypeCode(TypeCode.Int32), DtsConvert.VarTypeFromTypeCode(TypeCode.DateTime)};
    string [] parameterDescriptions = new string[2]{"The number of rows to sort.", "The start time of the Sort operation."};
    EventInfos.Add("StartingSort","Fires when the component begins sorting the rows.",false,ref parameterNames, ref parameterTypes, ref parameterDescriptions);
}
public override void ProcessInput(int inputID, PipelineBuffer buffer)
{
    while (buffer.NextRow())
    {
       // Process buffer rows.
    }

    IDTSEventInfo100 eventInfo = EventInfos["StartingSort"];
    object []arguments = new object[2]{buffer.RowCount, DateTime.Now };
    ComponentMetaData.FireCustomEvent("StartingSort", "Beginning sort operation.", ref arguments, ComponentMetaData.Name, ref FireSortEventAgain);
}
```

```vb
Public  Overrides Sub RegisterEvents() 
  Dim parameterNames As String() = New String(2) {"RowCount", "StartTime"} 
  Dim parameterTypes As System.UInt16() = New System.UInt16(2) {DtsConvert.VarTypeFromTypeCode(TypeCode.Int32), DtsConvert.VarTypeFromTypeCode(TypeCode.DateTime)} 
  Dim parameterDescriptions As String() = New String(2) {"The number of rows to sort.", "The start time of the Sort operation."} 
  EventInfos.Add("StartingSort", "Fires when the component begins sorting the rows.", False, parameterNames, parameterTypes, parameterDescriptions) 
End Sub 

Public  Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer) 
  While buffer.NextRow 
  End While 
  Dim eventInfo As IDTSEventInfo100 = EventInfos("StartingSort") 
  Dim arguments As Object() = New Object(2) {buffer.RowCount, DateTime.Now} 
  ComponentMetaData.FireCustomEvent("StartingSort", _
    "Beginning sort operation.", arguments, _
    ComponentMetaData.Name, FireSortEventAgain) 
End Sub
```

![Integration Services icono (pequeño)](../../media/dts-16.gif "Icono de Integration Services (pequeño)")  **Manténgase al día con Integration Services**<br /> Para obtener las descargas, artículos, ejemplos y vídeos más recientes de Microsoft, así como soluciones seleccionadas de la comunidad, visite la página de [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] en MSDN:<br /><br /> [Visite la página de Integration Services en MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Para recibir notificaciones automáticas de estas actualizaciones, suscríbase a las fuentes RSS disponibles en la página.

## <a name="see-also"></a>Consulte también
 [Integration Services los controladores de eventos de &#40;SSIS&#41;](../../integration-services-ssis-event-handlers.md) [Agregar un controlador de eventos a un paquete](../../add-an-event-handler-to-a-package.md)


