---
title: Detectar componentes de flujo de datos mediante programación | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- PipelineComponentInfos collection
- data flow task [Integration Services], components
- discovering data flow components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: ff92a96a-8af6-4532-82cc-c0bbff92401b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a18102f38f1ad06e918efe2ca529185d40deef9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745944"
---
# <a name="discovering-data-flow-components-programmatically"></a>Detectar componentes de flujo de datos mediante programación
  Una vez que se ha agregado una tarea de flujo de datos a un paquete, el siguiente paso puede ser determinar los componentes de flujo de datos que están disponibles para su uso. Puede detectar mediante programación los orígenes del flujo de datos, transformaciones y destinos que están instalados y disponibles en el equipo local. Para obtener información acerca de cómo agregar una tarea Flujo de datos al paquete, consulte [Agregar la tarea Flujo de datos mediante programación](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md).  
  
## <a name="discovering-components"></a>Detectar componentes  
 La clase <xref:Microsoft.SqlServer.Dts.Runtime.Application> proporciona la colección <xref:Microsoft.SqlServer.Dts.Runtime.Application.PipelineComponentInfos%2A>, que contiene un objeto <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> para cada componente instalado correctamente en el equipo local. Cada <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> contiene información acerca de un componente como su nombre, descripción y nombre de creación. Puede usar el valor devuelto en la propiedad <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo.CreationName%2A> para establecer la propiedad <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> de <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> cuando agrega un componente a un paquete.  
  
## <a name="next-step"></a>siguiente paso  
 Después de detectar los componentes disponibles, el paso siguiente es agregar y configurar los componentes. Esta acción se describe en el tema [Agregar componentes de flujo de datos mediante programación](../building-packages-programmatically/adding-data-flow-components-programmatically.md) siguiente.  
  
## <a name="sample"></a>Muestra  
 En el siguiente ejemplo de código se muestra cómo enumerar la colección <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfos> del objeto <xref:Microsoft.SqlServer.Dts.Runtime.Application> para detectar mediante programación los componentes de flujo de datos disponibles en el equipo local. En este ejemplo se requiere una referencia al ensamblado Microsoft.SqlServer.ManagedDTS.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Application application = new Application();  
      PipelineComponentInfos componentInfos = application.PipelineComponentInfos;  
  
      foreach (PipelineComponentInfo componentInfo in componentInfos)  
      {  
        Console.WriteLine("Name: " + componentInfo.Name + "\n" +  
          " CreationName: " + componentInfo.CreationName + "\n");  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim application As Application = New Application()  
  
    Dim componentInfos As PipelineComponentInfos = application.PipelineComponentInfos  
  
    For Each componentInfo As PipelineComponentInfo In componentInfos  
      Console.WriteLine("Name: " & componentInfo.Name & vbCrLf & _  
        " CreationName: " & componentInfo.CreationName & vbCrLf)  
    Next  
  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
![Integration Services icono (pequeño)](../media/dts-16.gif "Icono de Integration Services (pequeño)")  **Manténgase al día con Integration Services**<br /> Para obtener las descargas, artículos, ejemplos y vídeos más recientes de Microsoft, así como soluciones seleccionadas de la comunidad, visite la página de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] en MSDN:<br /><br /> [Visite la página de Integration Services en MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Para recibir notificaciones automáticas de estas actualizaciones, suscríbase a las fuentes RSS disponibles en la página.  
  
## <a name="see-also"></a>Consulte también  
 [Agregar componentes de flujo de datos mediante programación](../building-packages-programmatically/adding-data-flow-components-programmatically.md)  
  
  
