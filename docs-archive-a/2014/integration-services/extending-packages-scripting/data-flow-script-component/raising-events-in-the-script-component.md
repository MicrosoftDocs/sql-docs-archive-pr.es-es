---
title: Provocar eventos en el componente de script | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], raising events
ms.assetid: bb389073-e1d0-4794-8d29-c8b293b6a5e3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 78eb44239f4e58e43bdd65c41d5fdeb58d053a6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674200"
---
# <a name="raising-events-in-the-script-component"></a>Provocar eventos en el componente de script
  Los eventos proporcionan una manera de notificar errores, advertencias y otra información, como el progreso o el estado de una tarea, al paquete contenedor. El paquete proporciona controladores de eventos para administrar las notificaciones de eventos. El componente de script puede provocar eventos mediante una llamada a los métodos en la propiedad <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> de la clase `ScriptMain`. Para obtener más información sobre la manera en que los paquetes [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] controlan los eventos, vea [Controladores de eventos de Integration Services &#40;SSIS&#41;](../../integration-services-ssis-event-handlers.md).  
  
 Los eventos se pueden registrar en cualquier proveedor de registro habilitado en el paquete. Los proveedores de registro almacenan información sobre los eventos en un almacén de datos. El componente de script también puede usar el método <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> para registrar información en un proveedor de registro sin provocar un evento. Para obtener más información acerca de cómo usar el método <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A>, vea la siguiente sección.  
  
 Para provocar un evento, la tarea Script llama a uno de los siguientes métodos de la interfaz <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> expuestos por la propiedad <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A>:  
  
|Evento|Descripción|  
|-----------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>|Provoca un evento personalizado definido por el usuario en el paquete.|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A>|Informa al paquete de una condición de error.|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireInformation%2A>|Proporciona información al usuario.|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireProgress%2A>|Informa al paquete del progreso del componente.|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A>|Informa al paquete de que el componente está en un estado que garantiza la notificación del usuario, pero no es una condición de error.|  
  
 Aquí se proporciona un ejemplo simple de cómo provocar un evento Error:  
  
 `Dim myMetadata as IDTSComponentMetaData100`  
  
 `myMetaData = Me.ComponentMetaData`  
  
 `myMetaData.FireError(...)`  
  
![Integration Services icono (pequeño)](../../media/dts-16.gif "Icono de Integration Services (pequeño)")  **Manténgase al día con Integration Services**<br /> Para obtener las descargas, artículos, ejemplos y vídeos más recientes de Microsoft, así como soluciones seleccionadas de la comunidad, visite la página de [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] en MSDN:<br /><br /> [Visite la página de Integration Services en MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Para recibir notificaciones automáticas de estas actualizaciones, suscríbase a las fuentes RSS disponibles en la página.  
  
## <a name="see-also"></a>Consulte también  
 [Controladores de eventos de Integration Services &#40;SSIS&#41;](../../integration-services-ssis-event-handlers.md)   
 [Agregar un controlador de eventos a un paquete](../../add-an-event-handler-to-a-package.md)  
  
  
