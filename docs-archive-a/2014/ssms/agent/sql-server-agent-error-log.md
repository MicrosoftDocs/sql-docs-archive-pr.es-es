---
title: Registro de errores del Agente SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- messages [SQL Server], SQL Server Agent
- errors [SQL Server], logs
- SQL Server Agent, errors
ms.assetid: 0b2d6e6e-cd2d-4b8b-9fa2-2bbd2fc0da41
author: stevestein
ms.author: sstein
ms.openlocfilehash: ea9a723695c6993f4f07897f49d8014a86ce78b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745617"
---
# <a name="sql-server-agent-error-log"></a>Registro de errores del Agente SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] El Agente crea un registro de errores que, de manera predeterminada, registra las advertencias y los errores. En el registro se visualizan los siguientes errores y advertencias:  
  
-   Mensajes de advertencia que proporcionan información acerca de posibles problemas, como "el trabajo \<*job_name*> se eliminó mientras se estaba ejecutando".  
  
-   Mensajes de error que normalmente requieren la intervención de un administrador del sistema, como "No se puede iniciar la sesión de correo". Los mensajes de error se pueden enviar a un usuario o equipo específicos mediante **net send**.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] puede mantener hasta nueve registros de errores del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Cada registro archivado tiene una extensión que indica la antigüedad relativa del registro de errores. Por ejemplo, una extensión de .1 indica que es el archivo de registro de errores más reciente y una extensión de .9 indica que es el archivo de registro de errores más antiguo.  
  
 De forma predeterminada, los mensajes de seguimiento de ejecución no se escriben en el registro de errores del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] porque lo pueden llenar, reduciendo así la posibilidad de seleccionar y analizar los errores más difíciles. Puesto que el registro de errores agrega una carga de proceso adicional al servidor, es importante considerar las ventajas que se obtienen al capturar los mensajes de seguimiento de ejecución en este registro de errores. Generalmente, es mejor capturar todos los mensajes solo cuando se está depurando un problema específico.  
  
 Cuando se detiene el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , se puede modificar la ubicación del registro de errores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Cuando el registro de errores está vacío, no se puede abrir. Se puede reciclar el registro del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en cualquier momento, sin necesidad de detener el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Para ver el registro de errores del Agente SQL Server**  
  
-   [Ver registro de errores del Agente SQL Server &#40;SQL Server Management Studio&#41;](view-sql-server-agent-error-log-sql-server-management-studio.md) 
  
 **Para cambiar el nombre del registro de errores del Agente SQL Server**  
  
-   [Cambiar el nombre del registro de errores del Agente SQL Server &#40;SQL Server Management Studio&#41;](rename-a-sql-server-agent-error-log-sql-server-management-studio.md)  
  
 **Para enviar mensajes de error del Agente SQL Server**  
  
-   [Send SQL Server Agent Error Messages](send-sql-server-agent-error-messages.md)  
  
 **Para escribir mensajes de seguimiento de ejecución en el registro de errores del Agente SQL Server**  
  
-   [Escribir mensajes de seguimiento de ejecución en el registro de errores del Agente SQL Server &#40;SQL Server Management Studio&#41;](write-execution-trace-messages-to-sql-server-agent-log-ssms.md)  
  
  
