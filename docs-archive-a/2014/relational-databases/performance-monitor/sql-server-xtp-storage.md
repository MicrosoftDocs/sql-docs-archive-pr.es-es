---
title: Almacenamiento XTP | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 4070580b-880d-4f4c-abcc-626a4fe0c9a2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: efd4a9eba36060d3d4bab9b371678ab2b2c409ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673667"
---
# <a name="xtp-storage"></a>XTP Storage
  El objeto de rendimiento XTP Storage contiene contadores relacionados con el almacenamiento de XTP en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 En esta tabla se describen los contadores de **XTP Storage** .  
  
|Contador|Descripción|  
|-------------|-----------------|  
|**Checkpoints Closed**|Número de puntos de comprobación cerrados realizados por el agente en línea.|  
|**Checkpoints Completed**|Número de puntos de comprobación procesados por el subproceso de punto de comprobación sin conexión.|  
|**Core Merges Completed**|Número de mezclas básicas completadas por el subproceso de trabajo de mezcla. Todavía será necesario instalar estas mezclas.|  
|**Merge Policy Evaluations**|Número de evaluaciones de directivas de mezcla desde que el servidor se inició.|  
|**Merge Requests Outstanding**|Número de solicitudes de mezcla pendientes desde que el servidor se inició.|  
|**Merges Abandoned**|Número de mezclas abandonadas debido a un error.|  
|**Merges Installed**|Número de mezclas instaladas correctamente.|  
|**Total Files Merged**|Número total de archivos de origen mezclados. Este número se puede usar para determinar el número promedio de archivos de origen de la mezcla.|  
  
## <a name="see-also"></a>Consulte también  
 [Contadores de rendimiento de OLTP &#40;en memoria&#41;](../../integration-services/performance/performance-counters.md)  
  
  
