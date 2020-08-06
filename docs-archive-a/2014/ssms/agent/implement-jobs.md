---
title: Implementar trabajos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent]
- SQL Server Agent jobs
- SQL Server Agent jobs, about jobs
- jobs [SQL Server Agent], about jobs
ms.assetid: 69e06724-25c7-4fb3-8a5b-3d4596f21756
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1925b3113db8d7c57ac4344958c0247763cfd1b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662471"
---
# <a name="implement-jobs"></a>Implementar trabajos
  Puede utilizar los trabajos del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para automatizar tareas administrativas rutinarias y ejecutarlas periódicamente, lo que permite que la administración sea más eficaz.  
  
 Un trabajo es una serie específica de operaciones que el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] realiza secuencialmente. Un trabajo puede realizar una amplia variedad de actividades, incluidos scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] , aplicaciones de línea de comandos, scripts de Microsoft ActiveX, paquetes de Integration Services, comandos y consultas de Analysis Services o tareas de replicación. Los trabajos pueden ejecutar tareas repetitivas o que se pueden programar y pueden notificar automáticamente a los usuarios el estado del trabajo mediante alertas, simplificando mucho la administración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Puede ejecutar los trabajos manualmente o configurarlos para que se ejecuten de acuerdo con una programación o en respuesta a alertas.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**Descripción**|**Tema.**|  
|Contiene información sobre cómo crear trabajos y asignar su propiedad.|[Crear trabajos](create-jobs.md)|  
|Contiene información sobre cómo organizar trabajos en categorías.|[organizar los trabajos](organize-jobs.md)|  
|Contiene información acerca de los diferentes tipos de pasos de trabajo que puede crear y cómo administrarlos.|[Administrar pasos de trabajo](manage-job-steps.md)|  
|Contiene información acerca de cómo definir cuándo se iniciarán los trabajos que se ejecutan y la frecuencia con la que deben ejecutarse.|[Crear y adjuntar programaciones a trabajos](create-and-attach-schedules-to-jobs.md)|  
|Contiene información acerca de la ejecución manual de trabajos (sin una programación).|[Ejecutar trabajos](run-jobs.md)|  
|Contiene información acerca de cómo se puede configurar el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para que responda a los trabajos. Por ejemplo, se puede configurar el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para que notifique a los administradores cuándo finalicen los trabajos.|[Especificar respuestas de trabajos](specify-job-responses.md)|  
|Contiene información acerca de cómo ver los trabajos existentes, su historial cuando se han ejecutado y cómo modificarlos.|[Ver o modificar trabajos](view-or-modify-jobs.md)|  
|Contiene información acerca de cómo eliminar trabajos.|[eliminar trabajos](delete-jobs.md)|  
  
## <a name="see-also"></a>Consulte también  
 [Implementar la seguridad del Agente SQL Server](implement-sql-server-agent-security.md)  
  
  
