---
title: Ejecutar trabajos de mantenimiento de replicación (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server replication]
ms.assetid: 0dc485a0-5a50-41eb-a29d-f2b2fb920174
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9dc27c65e96a9f956ffa6d3edf9c72ed52f721a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748082"
---
# <a name="run-replication-maintenance-jobs-sql-server-management-studio"></a>Ejecutar trabajos de mantenimiento de replicación (SQL Server Management Studio)
  La replicación utiliza los siguientes trabajos de mantenimiento:  
  
-   **Reinicializar suscripciones con errores de validación de datos**
-   **Limpieza de historial del agente: distribución**
-   **Actualizador de supervisión de replicación para distribución.**
-   **Comprobación de agentes de replicación**
-   **Limpieza de la distribución: distribución**
-   **Limpieza de suscripciones expiradas**  
  
 Inicie y detenga estos trabajos en la carpeta **Trabajos** en [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] y en la pestaña **Agentes** del Monitor de replicación. Para información sobre cómo iniciar el Monitor de replicación, vea [Iniciar el Monitor de replicación](../monitor/start-the-replication-monitor.md). Vea y modifique las propiedades de cada trabajo en el cuadro de diálogo **Propiedades del trabajo: \<Job>** , que está disponible en la misma carpeta y pestaña.  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-management-studio"></a>Para iniciar o detener un mantenimiento de replicación en Management Studio  
  
1.  Conéctese al distribuidor en [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]y expanda el nodo de servidor.  
  
2.  Expanda la carpeta **Agente SQL Server** y a continuación la carpeta **Trabajos** .  
  
3.  Haga clic con el botón secundario en un trabajo y, a continuación, haga clic en **Iniciar el trabajo** o **Detener el trabajo**.  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-replication-monitor"></a>Para iniciar o detener un mantenimiento de replicación en el Monitor de replicación  
  
1.  Expanda un grupo de publicador en el Monitor de replicación y, a continuación, seleccione un publicador.  
  
2.  Haga clic en la pestaña **Agentes** .  
  
3.  Haga clic con el botón secundario en la cuadrícula y, a continuación, haga clic en **Iniciar el trabajo** o **Detener el trabajo**.  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-management-studio"></a>Para ver y modificar las propiedades de un mantenimiento de replicación en Management Studio  
  
1.  Conéctese al distribuidor en [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]y expanda el nodo de servidor.  
  
2.  Expanda la carpeta **Agente SQL Server** y a continuación la carpeta **Trabajos** .  
  
3.  Haga clic con el botón derecho en un trabajo y, a continuación, haga clic en **Propiedades**.  
  
4.  En el cuadro de diálogo **Propiedades del trabajo: \<Job>** , realice las modificaciones necesarias y, después, haga clic en **Aceptar**.  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-replication-monitor"></a>Para ver y modificar las propiedades de un mantenimiento de replicación en el Monitor de replicación  
  
1.  Expanda un grupo de publicador en el Monitor de replicación y, a continuación, seleccione un publicador.  
  
2.  Haga clic en la pestaña **Agentes** .  
  
3.  Haga clic con el botón secundario en un trabajo en la cuadrícula y , a continuación, haga clic en **Propiedades**.  
  
4.  En el cuadro de diálogo **Propiedades del trabajo: \<Job>** , realice las modificaciones necesarias y, después, haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Consulte también  
 [Iniciar y detener un agente de replicación &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)   
 [Visualización de información y realización de tareas mediante el Monitor de replicación](../monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Administración del Agente de replicación](../agents/replication-agent-administration.md)  
  
  
