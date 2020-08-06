---
title: MSSQLSERVER_41342 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41342 (Database Engine error)
ms.assetid: 28270d98-c543-4e7d-b40c-2200e38dce1c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c0269322b30cee88e5ba3d50b6d391464b735f54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674868"
---
# <a name="mssqlserver_41342"></a>MSSQLSERVER_41342
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre de producto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Id. de evento|41342|  
|Origen de eventos|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|HK_HW_NOT_SUPPORTED|  
|Texto del mensaje|El modelo del procesador del sistema no permite crear *construct*. Este error suele producirse con procesadores antiguos. Para obtener información sobre los modelos admitidos, vea los Libros en pantalla de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
## <a name="explanation"></a>Explicación  
 Las tablas con optimización para memoria requieren un modelo de procesador compatible con las operaciones atómicas de comparación e intercambio con valores de 128 bits, que requieren la instrucción CMPXCHG16B del lenguaje ensamblador. Ciertos modelos anteriores de procesadores AMD no admiten la instrucción CMPXCHG16B. Además, algunos entornos de virtualización no tienen habilitada esta instrucción de forma predeterminada.  
  
## <a name="user-action"></a>Acción del usuario  
 Actualice el procesador. Si su procesador admite la instrucción y está ejecutando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en una máquina virtual, cambie la configuración para admitir la instrucción CMPXCHG16B.  
  
## <a name="see-also"></a>Consulte también  
 [OLTP en memoria &#40;optimización en memoria&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
