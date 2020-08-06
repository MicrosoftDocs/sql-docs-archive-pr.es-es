---
title: Locks (objeto de SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Locks object
- SQLServer:Locks
ms.assetid: ace04f0d-3993-4444-8317-ca39d7087e49
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f13d4ea1172d6b32b90c045a45445c5c87f48a94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669625"
---
# <a name="sql-server-locks-object"></a>Locks (objeto de SQL Server)
  El objeto **SQLServer:Locks** de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proporciona información acerca de los bloqueos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en tipos de recursos individuales. Se mantienen bloqueos en recursos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , como filas leídas o modificadas durante una transacción, para evitar que varias transacciones utilicen simultáneamente los recursos. Por ejemplo, si una transacción mantiene un bloqueo exclusivo (X) en una fila de una tabla, ninguna otra transacción podrá modificar esa fila hasta que se libere el bloqueo. La reducción de bloqueos aumenta la simultaneidad, lo que puede mejorar el rendimiento. Se pueden supervisar al mismo tiempo varias instancias del objeto **Locks** ; cada instancia representa un bloqueo en un tipo de recurso.  
  
 En esta tabla se describen los contadores de **bloqueos** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Contadores de bloqueos de SQL Server|Descripción|  
|-------------------------------|-----------------|  
|**Tiempo promedio de espera (ms)**|Promedio de tiempo de espera (en milisegundos) para cada solicitud de bloqueo que esperó.|  
|**Solicitudes de bloqueo/seg.**|Número de nuevos bloqueos y conversiones de bloqueos por segundo solicitados desde el administrador de bloqueos.|  
|**Tiempos de espera de bloqueos (tiempo de espera > 0)/s.**|Número de solicitudes de bloqueo por segundo cuyo tiempo de espera se agotó, pero excluidas las solicitudes de bloqueo NOWAIT.|  
|**Tiempos de espera de bloqueos/seg.**|Número de solicitudes de bloqueo por segundo cuyo tiempo de espera se agotó, incluidas las solicitudes de bloqueo NOWAIT.|  
|**Tiempo de espera de bloqueos (ms)**|Tiempo total de espera (en milisegundos) de bloqueos en el último segundo.|  
|**Esperas de bloqueo/seg.**|Número de solicitudes de bloqueo por segundo que necesitaron que el solicitante esperara.|  
|**Número de interbloqueos/seg.**|Número de solicitudes de bloqueo por segundo que causaron interbloqueos.|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] puede bloquear los siguientes recursos.  
  
|Elemento|Descripción|  
|----------|-----------------|  
|**_Total**|Información sobre todos los bloqueos.|  
|**Unidad de asignación**|Bloqueo en una unidad de asignación.|  
|**Aplicación**|Bloqueo en un recurso de una aplicación especificada.|  
|**Base de datos**|Bloqueo en una base de datos, incluidos todos los objetos de la base de datos.|  
|**Extensión**|Bloqueo en un grupo contiguo de 8 páginas.|  
|**Archivo**|Bloqueo en un archivo de base de datos.|  
|**Montón o árbol b**|Montón o árbol b (HOBT). Bloqueo en un montón de páginas de datos o en la estructura árbol b de un índice.|  
|**Clave**|Bloqueo en una fila de un índice.|  
|**Metadata**|Bloqueo en información de catálogo, también conocida como metadatos.|  
|**Object**|Bloqueo en una tabla, procedimiento almacenado, vista, etc. incluidos todos los datos e índices. El objeto puede ser cualquier elemento que tenga una entrada en **sys.all_objects**.|  
|**Page**|Bloqueo en una página de 8 kilobytes (KB) de una base de datos.|  
|**RID**|Id. de fila. Un bloqueo sobre una sola fila en un montón.|  
  
## <a name="see-also"></a>Consulte también  
 [Supervisar el uso de recursos&#40;Monitor de sistema&#41;](monitor-resource-usage-system-monitor.md)  
  
  
