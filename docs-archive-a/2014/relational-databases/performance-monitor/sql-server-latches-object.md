---
title: Latches (objeto de SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Latches object
- SQLServer:Latches
ms.assetid: 2393ea1c-2bf3-41c3-9f37-b9761144eeca
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6f49ac00114065e971c0893f9217ab883eb2d7f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669627"
---
# <a name="sql-server-latches-object"></a>Latches (objeto de SQL Server)
  El objeto **SQLServer:Latches** en Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proporciona contadores para supervisar los bloqueos de recursos internos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , denominados bloqueos temporales. La supervisión de los bloqueos temporales para determinar la actividad de los usuarios y el uso de los recursos puede ayudar a identificar puntos de congestión en el rendimiento.  
  
 En esta tabla se describen los contadores de **bloqueos temporales** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Contadores de bloqueos temporales de SQL Server|Descripción|  
|---------------------------------|-----------------|  
|**Promedio de tiempo de espera para los bloqueos temporales (ms)**|Promedio de tiempo de espera de los bloqueos temporales (en milisegundos) para solicitudes de bloqueos temporales que tuvieron que esperar.|  
|**Esperas de bloqueos temporales/seg.**|Número de solicitudes de bloqueo temporal que no se concedieron inmediatamente.|  
|**Número de SuperLatches**|Número de bloqueos temporales que actualmente son SuperLatches.|  
|**Degradaciones de SuperLatch/seg.**|Número de SuperLatches degradados a bloqueos temporales normales en el último segundo transcurrido.|  
|**Ascensos a SuperLatch/seg.**|Número de bloqueos temporales ascendidos a SuperLatches en el último segundo transcurrido.|  
|**Tiempo total de espera de los bloqueos temporales (ms)**|Tiempo total de espera para bloqueos temporales (en milisegundos) de las solicitudes de bloqueos temporales en el último segundo.|  
  
## <a name="see-also"></a>Consulte también  
 [Supervisar el uso de recursos&#40;Monitor de sistema&#41;](monitor-resource-usage-system-monitor.md)  
  
  
