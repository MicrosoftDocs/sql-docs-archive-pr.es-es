---
title: Tarea Ejecutar trabajo del Agente SQL Server (Plan de mantenimiento) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.executejob.f1
helpviewer_keywords:
- Execute SQL Server Agent Job Task dialog box
ms.assetid: 4ed75956-ebb8-4d8c-9c16-fc0eb00bd3a0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b997d5144b113102ba0ed2d9d1df59b6707acbee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87675349"
---
# <a name="execute-sql-server-agent-job-task-maintenance-plan"></a>Tarea Ejecutar trabajo del Agente SQL Server (Plan de mantenimiento)
  Utilice el cuadro de diálogo **Tarea Ejecutar trabajo del Agente SQL Server** para ejecutar trabajos del Agente Microsoft SQL Server dentro de un plan de mantenimiento. Esta opción no estará disponible si no tiene trabajos del Agente SQL Server en la conexión seleccionada.  
  
 Esta tarea usa la instrucción **.sp_start_job** .  
  
## <a name="ui-element-list"></a>Lista de elementos de la interfaz de usuario  
 **Connection**  
 Seleccione la conexión al servidor que va a utilizar para la realización de esta tarea.  
  
 **Nuevo**  
 Cree una nueva conexión de servidor que utilizará al realizar esta tarea. El cuadro de diálogo **Nueva conexión** se describe a continuación.  
  
 **Trabajos del Agente SQL Server disponibles**  
 Seleccione el trabajo que se ejecutará. La cuadrícula proporciona el **Nombre del trabajo** y la **Descripción** para identificar los trabajos.  
  
 **Ver T-SQL**  
 Muestra las instrucciones [!INCLUDE[tsql](../../includes/tsql-md.md)] realizadas en el servidor para esta tarea, en función de las opciones seleccionadas.  
  
> [!NOTE]  
>  Si el número de objetos afectados es elevado, es posible que deba esperar un rato hasta que se muestren.  
  
## <a name="new-connection-dialog-box"></a>Cuadro de diálogo Nueva conexión  
 **Nombre de la conexión**  
 Escriba un nombre para la nueva conexión.  
  
 **Seleccionar o especificar un nombre de servidor**  
 Seleccione un servidor al que conectarse cuando se realice esta tarea.  
  
 **Actualizar**  
 Actualiza la lista de servidores disponibles.  
  
 **Especificar información para iniciar sesión en el servidor**  
 Especifica el modo de autenticación en el servidor.  
  
 **Usar seguridad integrada de Windows NT**  
 Conéctese a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] con autenticación de Microsoft Windows.  
  
 **Utilizar un nombre de usuario y una contraseña específicos**  
 Conéctese a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] mediante autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Esta opción no está disponible.  
  
 **Nombre de usuario**  
 Proporcione un inicio de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para la autenticación. Esta opción no está disponible.  
  
 **Contraseña**  
 Proporcione una contraseña para que se utilice en la autenticación. Esta opción no está disponible.  
  
## <a name="see-also"></a>Consulte también  
 [sp_add_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)   
 [Crear un trabajo](../../ssms/agent/create-a-job.md)   
 [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)  
  
  
