---
title: MSSQLSERVER_41359 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41359 (Database Engine error)
ms.assetid: 02b717c7-9170-4676-b0f6-4dec9eb5b5d4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7cf45a117dcda0827672c6072c603a1fc0866a33
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676502"
---
# <a name="mssqlserver_41359"></a>MSSQLSERVER_41359
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre de producto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Id. de evento|41359|  
|Origen de eventos|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|SQL_READ_COMMITTED_SNAPSHOT_NOT_SUPPORTED|  
|Texto del mensaje|Una consulta que tiene acceso a las tablas optimizadas en memoria con el nivel de aislamiento READ COMMITTED no puede tener acceso a las tablas basadas en disco cuando la opción de base de datos READ_COMMITTED_SNAPSHOT está establecida en ON. Proporciona un nivel de aislamiento admitido para la tabla optimizada en memoria mediante una sugerencia de tabla, como WITH (SNAPSHOT).|  
  
## <a name="explanation"></a>Explicación  
 La base de datos con READ_COMMITTED_SNAPSHOT=ON no admite las transacciones que tienen acceso a las tablas optimizadas en memoria a las y tablas basadas en disco.  
  
## <a name="user-action"></a>Acción del usuario  
 Establezca READ_COMMITTED_SNAPSHOT en OFF o proporcione un nivel de aislamiento admitido para la tabla optimizada en memoria mediante una sugerencia de nivela de tabla, como WITH (SNAPSHOT). Para obtener más información, vea [OLTP en memoria &#40;optimización en memoria&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Consulte también  
 [OLTP en memoria &#40;optimización en memoria&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
