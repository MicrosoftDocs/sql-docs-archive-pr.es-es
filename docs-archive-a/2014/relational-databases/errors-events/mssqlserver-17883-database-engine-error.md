---
title: MSSQLSERVER_17883 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17883 (Database Engine error)
ms.assetid: adaf1c04-e397-4a69-90b8-9353a37277ea
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 46488fb6f7adac2c1109871f2aad4c79352829ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744719"
---
# <a name="mssqlserver_17883"></a>MSSQLSERVER_17883
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre de producto|SQL Server|  
|Id. de evento|17883|  
|Origen de eventos|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|SRV_SCHEDULER_NONYIELDING|  
|Texto del mensaje|Parece que el proceso %ld:%ld:%ld (0x%lx) Trabajo 0x%p no rinde en el programador %ld. Thread creation time: %I64d. CPU usada por el subproceso (aprox.): kernel %I64d ms, usuario %I64d ms. Uso del proceso %d%%. Sistema inactivo %d%%. Intervalo: %I64d ms.|  
  
## <a name="explanation"></a>Explicación  
 Indica que hay un posible problema con un subproceso que no rinde en un programador.  Esto podría deberse a un error en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o a que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no esté obteniendo bastantes ciclos para ejecutarse.  Este error podría desaparecer si el subproceso rinde finalmente.  
  
## <a name="user-action"></a>Acción del usuario  
 Si la carga es excesiva en el sistema, redúzcala; de lo contrario, póngase en contacto con los servicios de soporte al cliente de Microsoft.  
  
  
