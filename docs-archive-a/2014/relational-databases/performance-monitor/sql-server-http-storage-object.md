---
title: SQL Server, HTTP_STORAGE_OBJECT | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: ae849f79-c581-42a5-a5cc-0a9ebea171b9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 62cd5b8422213624cfd8609027c477760f682239
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669629"
---
# <a name="sql-server-http_storage_object"></a>SQL Server, HTTP_STORAGE_OBJECT
  El objeto de rendimiento **SQLServer: HTTP_STORAGE_OBJECT** se compone de contadores de rendimiento que supervisan Azure Storage cuenta. Con [SQL Server archivos de datos en la característica de Azure](../databases/sql-server-data-files-in-microsoft-azure.md) , puede almacenar archivos de base de datos en Azure Storage BLOBs. Este objeto de rendimiento trata cada cuenta de Azure Storage como una unidad diferente.  
  
|Nombre del contador|Descripción|  
|------------------|-----------------|  
|**Lectura de bytes/seg**|Cantidad de datos que se transfieren desde almacenamiento HTTP por segundo durante las operaciones de lectura.|  
|**Escritura de bytes/seg**|Cantidad de datos que se transfieren desde almacenamiento HTTP por segundo durante las operaciones de escritura.|  
|**Total de bytes/seg**|Cantidad de datos que se transfieren desde almacenamiento HTTP por segundo durante las operaciones de lectura o escritura.|  
|**Lecturas/seg**|Número de lecturas por segundo en el almacenamiento HTTP.|  
|**lógicas/s**|Número de escrituras por segundo en el almacenamiento HTTP.|  
|**Transferencias/seg**|Número de operaciones de lectura y escritura por segundo en el almacenamiento HTTP.|  
|**Avg. bytes/lectura**|Promedio de bytes transferidos desde el almacenamiento HTTP por lectura.|  
|**Avg. bytes/escritura**|Promedio de bytes transferidos desde el almacenamiento HTTP por escritura.|  
|**Avg. bytes/transferidos**|Promedio de bytes transferidos desde el almacenamiento HTTP durante las operaciones de lectura o escritura.|  
|**Promedio de microsegundos/lectura**|Promedio de microsegundos que invierten en realizar cada lectura desde el almacenamiento HTTP.|  
|**Promedio de microsegundos/escritura**|Promedio de microsegundos que se invierten en realizar cada escritura en el almacenamiento HTTP.|  
|**Promedio de microsegundos/transferencia**|Promedio de microsegundos que se invierten en realizar cada transferencia en el almacenamiento HTTP.|  
|**E/S pendiente de almacenamiento HTTP**|Número total de E/S pendientes para su almacenamiento HTTP.|  
|**Reintento de e/s de Almacenamiento HTTP/s**|Número de solicitudes de reintento enviadas al almacenamiento HTTP por segundo.|  
  
## <a name="see-also"></a>Consulte también  
 [Supervisar el uso de recursos&#40;Monitor de sistema&#41;](monitor-resource-usage-system-monitor.md)  
  
  
