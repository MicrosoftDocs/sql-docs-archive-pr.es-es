---
title: Especificar respuestas de trabajos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], responses
- SQL Server Agent jobs, responses
- actions [SQL Server Agent jobs]
- responding to jobs
ms.assetid: 050242e1-9b79-4ade-91a9-580707b9d2d9
author: stevestein
ms.author: sstein
ms.openlocfilehash: d41c5e1552a1ff16343bdb2c4e9feaafb51c5783
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743905"
---
# <a name="specify-job-responses"></a>Especificar respuestas de trabajos
  Las respuestas de trabajos especifican acciones que realizará el servicio del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tras completar un trabajo. Estas respuestas permiten a los administradores de las bases de datos saber cuándo se completan los trabajos y con qué frecuencia se ejecutan. Algunas respuestas de trabajos típicas son:  
  
-   Notificar al operador mediante correo electrónico, localizador electrónico o un mensaje de **net send** .  
  
     Use una de estas respuestas de trabajo si el operador debe realizar una acción de seguimiento. Por ejemplo, si un trabajo de copia de seguridad se realiza correctamente, se debe notificar de ello al operador para que quite la cinta de copia de seguridad y la guarde en un lugar seguro.  
  
-   Escribir un mensaje de evento en el registro de aplicación Windows.  
  
     Puede utilizar esta respuesta solo para trabajos con errores.  
  
-   Eliminar automáticamente el trabajo.  
  
     Utilice esta respuesta de trabajo si está seguro de que no necesita volver a ejecutar este trabajo.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**Descripción**|**Tema.**|  
|Describe cómo notificar a un operador el estado de un trabajo.|[Notify an Operator of Job Status](notify-an-operator-of-job-status.md)|  
|Describe cómo escribir el estado de un trabajo en el registro de aplicación Windows.|[Write the Job Status to the Windows Application Log](../../reporting-services/report-server/windows-application-log.md)|  
  
## <a name="see-also"></a>Consulte también  
 [Supervisar y responder a eventos](monitor-and-respond-to-events.md)  
  
  
