---
title: Tarea Lector de datos WMI | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmidatareadertask.f1
helpviewer_keywords:
- WQL [Integration Services]
- WMI Data Reader task [Integration Services]
ms.assetid: dae57067-0275-4ac3-8f34-1b9d169f1112
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1d2f16a28e8b6c94c7275468dedb6d2dfec76d8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669790"
---
# <a name="wmi-data-reader-task"></a>Tarea Lector de datos WMI
  La tarea Lector de datos WMI ejecuta consultas mediante el Lenguaje de consulta del Instrumental de administración de Windows (WMI), que devuelve información de WMI sobre un sistema informático. Puede usar la tarea Lector de datos WMI para los siguientes fines:  
  
-   Realizar consultas de los registros de eventos de Windows en un equipo local o remoto y escribir la información en un archivo o variable.  
  
-   Obtener información sobre la presencia, estado o propiedades de componentes del hardware y usar posteriormente esta información para determinar si se deben ejecutar otras tareas en el flujo de control.  
  
-   Obtener una lista de las aplicaciones y determinar qué versión de cada aplicación está instalada.  
  
 Puede configurar la tarea Lector de datos WMI de las maneras siguientes:  
  
-   Especificar el administrador de conexiones WMI que se debe usar.  
  
-   Especificar el origen de la consulta WQL. La consulta se puede almacenar en una propiedad de tarea, o bien fuera de la tarea, en una variable o archivo.  
  
-   Definir el formato de los resultados de la consulta WQL. La tarea admite una tabla, par de nombre/valor de la propiedad o formato de valor de propiedad.  
  
-   Especificar el destino de la consulta. El destino puede ser una variable o un archivo.  
  
-   Indicar si el destino de la consulta se sobrescribe, se conserva o anexa.  
  
 Si el origen o destino es un archivo, la tarea Lector de datos WMI usa un administrador de conexiones de archivo para conectarse al archivo. Para más información, consulte [Flat File Connection Manager](../connection-manager/file-connection-manager.md).  
  
 La tarea Lector de datos WMI usa un administrador de conexiones WMI para conectarse al servidor desde el cual lee la información de WMI. Para más información, consulte [WMI Connection Manager](../connection-manager/wmi-connection-manager.md).  
  
## <a name="wql-query"></a>WQL Query  
 WQL es un dialecto de SQL con extensiones para admitir la notificación de eventos de WMI y otras características específicas de WMI. Para obtener más información sobre WQL, vea la documentación sobre Instrumental de administración de Windows en [MSDN Library](https://go.microsoft.com/fwlink/?linkid=7022).  
  
> [!NOTE]  
>  Las clases de WMI varían en las diferentes versiones de Windows.  
  
 La siguiente consulta WQL devuelve entradas en el evento de registro de la aplicación.  
  
```  
SELECT * FROM Win32_NTLogEvent WHERE LogFile = 'Application' AND (SourceName='SQLISService' OR SourceName='SQLISPackage') AND TimeGenerated > '20050117'  
```  
  
 La siguiente consulta WQL devuelve información de disco lógica.  
  
```  
SELECT FreeSpace, DeviceId, Size, SystemName, Description FROM Win32_LlogicalDisk  
```  
  
 La siguiente consulta WQL devuelve una lista de las actualizaciones de Ingeniería de corrección rápida (QFE) al sistema operativo.  
  
```  
Select * FROM Win32_QuickFixEngineering  
```  
  
## <a name="custom-logging-messages-available-on-the-wmi-data-reader-task"></a>Mensajes de registro personalizados disponibles en la tarea Lector de datos WMI  
 La siguiente tabla contiene las entradas del registro personalizadas para la tarea Lector de datos WMI. Para obtener más información, vea [Registro de Integration Services &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md) y [Mensajes personalizados para registro](../custom-messages-for-logging.md).  
  
|Entrada del registro|Descripción|  
|---------------|-----------------|  
|`WMIDataReaderGettingWMIData`|Indica que la tarea inició la lectura de datos WMI.|  
|`WMIDataReaderOperation`|Informa de la consulta WQL que ejecutó la tarea.|  
  
## <a name="configuration-of-the-wmi-data-reader-task"></a>Configuración de la tarea Lector de datos WMI  
 Puede establecer propiedades mediante programación o a través del Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Para obtener información acerca de las propiedades que puede establecer en el Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] , haga clic en uno de los temas siguientes:  
  
-   [Editor de la tarea Lector de datos WMI &#40;página Opciones WMI&#41;](../wmi-data-reader-task-editor-wmi-options-page.md)  
  
-   [Página Expresiones](../expressions/expressions-page.md)  
  
 Para obtener información sobre cómo establecer estas propiedades mediante programación, haga clic en el tema siguiente:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WmiDataReaderTask.WmiDataReaderTask>  
  
## <a name="related-tasks"></a>Related Tasks  
 Para obtener más información sobre cómo establecer estas propiedades en el Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] , haga clic en el siguiente tema:  
  
-   [Establecer las propiedades de tareas o contenedores](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>Consulte también  
 [Tareas de Integration Services](integration-services-tasks.md)   
 [Flujo de control](control-flow.md)  
  
  
