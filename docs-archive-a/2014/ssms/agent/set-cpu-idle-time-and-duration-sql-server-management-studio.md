---
title: Establecer la duración y el tiempo de inactividad de la CPU (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- CPU [SQL Server], idle conditions
- time [SQL Server], CPU idle and duration
- duration of CPU idle [SQL Server]
- SQL Server Agent, CPU idle conditions
- idle time [SQL Server]
ms.assetid: 8647b465-d899-4cc7-9640-134a506d0a2e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1660f6d70977b8f590a18adf952a6a19f32a26cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751634"
---
# <a name="set-cpu-idle-time-and-duration-sql-server-management-studio"></a>Establecer la duración y el tiempo de inactividad de la CPU (SQL Server Management Studio)
  En este tema se explica cómo definir la condición de inactividad de la CPU para el servidor en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. La definición de inactividad de CPU influye en cómo el [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agente responde a los eventos. Por ejemplo, supongamos que define la condición de inactividad de la CPU como el momento en que el uso de la CPU se sitúa por debajo del 10% y permanece en este nivel durante 10 minutos. En este caso, si ha definido trabajos que deben ejecutarse cuando la CPU del servidor alcance una condición de inactividad, estos trabajos se iniciarán cuando el uso de la CPU se sitúe por debajo del 10% y permanezca en este nivel durante 10 minutos. Si se trata de un trabajo que tiene consecuencias importantes sobre el rendimiento del servidor, es importante la forma en que define la condición de inactividad de la CPU.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Uso de SQL Server Management Studio  
  
#### <a name="to-set-cpu-idle-time-and-duration"></a>Para establecer la duración y el tiempo de inactividad de la CPU  
  
1.  En **Explorador de objetos,** Conéctese a una instancia de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] y, a continuación, expándala.  
  
2.  Haga clic con el botón derecho en el **Agente SQL Server**, haga clic en **Propiedades**y seleccione la página **Avanzadas** .  
  
3.  En **Condición de CPU inactiva**, haga lo siguiente:  
  
    -   Active la opción **Definir condición de CPU inactiva**.  
  
    -   Especifique un porcentaje para el cuadro **El promedio de uso de la CPU baja de** (para todas las CPU). Esto establece el nivel de uso por debajo del cual debe situarse la CPU para que se considere inactiva.  
  
    -   Especifique un número de segundos para el cuadro **Y permanece por debajo durante** . Esto establece la duración del uso mínimo de la CPU para que ésta se considere inactiva.  
  
  
