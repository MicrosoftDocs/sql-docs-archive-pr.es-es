---
title: Crear un paso de trabajo CmdExec | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- CmdExec jobs
ms.assetid: b48da5b4-6fe7-4eb7-bade-dc7d697c6d5c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 48c557b8ea4228d27b73d361c50aac62232d1e00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672352"
---
# <a name="create-a-cmdexec-job-step"></a>Create a CmdExec Job Step
  En este tema se describe cómo crear y definir un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] paso de trabajo [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] del agente en que usa un programa ejecutable o un comando del sistema operativo mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , [!INCLUDE[tsql](../../includes/tsql-md.md)] o objetos de administración de SQL Server.  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Seguridad](#Security)  
  
-   **Para crear un paso de trabajo de CmdExec, utilizando:**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [objetos de administración de SQL Server](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="security"></a><a name="Security"></a> Seguridad  
 De forma predeterminada, solo los miembros del rol fijo de servidor **sysadmin** pueden crear pasos de trabajo CmdExec. Estos pasos de trabajo se ejecutan en el contexto de la cuenta de servicio de Agente SQL Server salvo que el usuario **sysadmin** cree una cuenta de proxy. Los usuarios que no sean miembros del rol **sysadmin** pueden crear pasos de trabajo CmdExec si disponen de acceso a la cuenta de proxy CmdExec.  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permisos  
 Para obtener información detallada, vea [Implementar la seguridad del Agente SQL Server](implement-sql-server-agent-security.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Uso de SQL Server Management Studio  
  
#### <a name="to-create-a-cmdexec-job-step"></a>Para crear un paso de trabajo de CmdExec  
  
1.  En **Explorador de objetos,** Conéctese a una instancia de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] y, a continuación, expándala.  
  
2.  Expanda el **Agente SQL Server**, cree un trabajo o haga clic con el botón derecho en uno existente y, después, haga clic en **Propiedades**.  
  
3.  En el cuadro de diálogo **Propiedades del trabajo** , haga clic en la página **Pasos** y, a continuación, haga clic en **Nuevo**.  
  
4.  En el cuadro de diálogo **Nuevo paso de trabajo** , escriba un nombre para el paso de trabajo en **Nombre del paso**.  
  
5.  En la lista **Tipo** , elija **Sistema operativo (CmdExec)**.  
  
6.  En la lista **Ejecutar como** , seleccione la cuenta e proxy con las credenciales que utilizará el trabajo. De forma predeterminada, los pasos de trabajo de CmdExec se ejecutan en el contexto de la cuenta de servicio de Agente SQL Server.  
  
7.  En el cuadro **Procesar código de salida de un comando correcto** , escriba un valor de 0 a 999999.  
  
8.  En el cuadro **Comando** , escriba el comando del sistema operativo o el programa ejecutable. Vea "Usar T-Transact T-SQL" para obtener un ejemplo.  
  
9. Haga clic en la página **Avanzadas** para configurar las opciones del paso de trabajo como, por ejemplo: la acción que se realizará si el paso de trabajo es correcto o si es erróneo, el número de veces que Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] intentará ejecutar el paso de trabajo y el archivo en el que Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] puede escribir la salida del paso de trabajo. Solo los miembros del rol fijo de servidor **sysadmin** pueden escribir la salida de paso de trabajo en un archivo del sistema operativo.  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Usar Transact-SQL  
  
### <a name="to-create-a-cmdexec-job-step"></a>Para crear un paso de trabajo de CmdExec  
  
1.  En el **Explorador de objetos**, conéctese a una instancia del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En la barra de Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**.  
  
    ```sql
    -- creates a job step that uses CmdExec  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'CMDEXEC',  
        @command = C:\clickme_scripts\SQL11\PostBOLReorg GetHsX.exe',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 Para obtener más información, vea [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Usar Objetos de administración de SQL Server  

### <a name="to-create-a-cmdexec-job-step"></a>Para crear un paso de trabajo de CmdExec
  
 Utilice la clase `JobStep` mediante un lenguaje de programación que elija, como Visual Basic, Visual C# o PowerShell.  
