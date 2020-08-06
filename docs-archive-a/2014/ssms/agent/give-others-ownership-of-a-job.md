---
title: Asignar a otros usuarios la propiedad de un trabajo | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], owners
- owners [SQL Server], jobs
- SQL Server Agent jobs, owners
ms.assetid: 2ded5e9c-4251-4fb1-a047-99f13d150b61
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2cf03fdc9031ce9761125d95619438837f2959bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662474"
---
# <a name="give-others-ownership-of-a-job"></a>Give Others Ownership of a Job
  En este tema se describe cómo reasignar la propiedad de los [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trabajos del agente a otro usuario.  
  
-   **Antes de empezar:**  [Limitaciones y restricciones](#Restrictions), [Seguridad](#Security)  
  
-   **Para asignar a otros usuarios la propiedad de un trabajo, utilizando:**  
  
     [SQL Server Management Studio](#SSMSProc2)  
  
     [Transact-SQL](#TsqlProc2)  
  
     [objetos de administración de SQL Server](#SMOProc2)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitaciones y restricciones  
 Para crear un trabajo, el usuario debe ser miembro de uno de los roles fijos de base de datos del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o del rol fijo de servidor **sysadmin** . Solo pueden editar el trabajo el propietario de éste o los miembros del rol **sysadmin** . Para más información sobre los roles fijos de base de datos del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consulte [Roles fijos de base de datos del Agente SQL Server](sql-server-agent-fixed-database-roles.md).  
  
 Para cambiar el propietario de un trabajo debe ser administrador de sistema.  
  
 La asignación de un trabajo a otro inicio de sesión no garantiza que el nuevo propietario disponga de los permisos suficientes para ejecutar el trabajo.  
  
###  <a name="security"></a><a name="Security"></a> Seguridad  
 Por razones de seguridad, solo el propietario del trabajo o un miembro del rol **sysadmin** puede cambiar la definición del trabajo. Solo los miembros del rol fijo de servidor **sysadmin** pueden asignar la propiedad de un trabajo a otros usuarios y pueden ejecutar cualquier trabajo, independientemente de quién sea el propietario del mismo.  
  
> [!NOTE]  
>  Si cambia la propiedad de un trabajo a un usuario que no es miembro del rol fijo de servidor **sysadmin** y el trabajo está ejecutando unos pasos que necesitan las cuentas de un servidor proxy (por ejemplo, la ejecución de paquetes [!INCLUDE[ssIS](../../includes/ssis-md.md)] ), asegúrese de que el usuario tenga acceso a ese servidor proxy o, de lo contrario, se producirán errores en el trabajo.  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permisos  
 Para obtener información detallada, vea [Implementar la seguridad del Agente SQL Server](implement-sql-server-agent-security.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProc2"></a> Uso de SQL Server Management Studio  
 **Para asignar a otros usuarios la propiedad de un trabajo**  
  
1.  En **Explorador de objetos,** Conéctese a una instancia de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] y, a continuación, expándala.  
  
2.  Expanda el **Agente SQL Server**, expanda **Trabajos**, haga clic con el botón derecho en el trabajo y, a continuación, haga clic en **Propiedades**.  
  
3.  En la lista **Propietario** , seleccione un inicio de sesión. Para cambiar el propietario de un trabajo debe ser administrador de sistema.  
  
     La asignación de un trabajo a otro inicio de sesión no garantiza que el nuevo propietario disponga de los permisos suficientes para ejecutar el trabajo.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProc2"></a> Usar Transact-SQL  
 **Para asignar a otros usuarios la propiedad de un trabajo**  
  
1.  En el Explorador de objetos, conéctese a una instancia del Motor de base de datos y, a continuación, expándala.  
  
2.  En la barra de herramientas, haga clic en **Nueva consulta**.  
  
3.  En la ventana de consulta, escriba las siguientes instrucciones que utilizan el sp_manage_jobs_by_login &#40;procedimiento almacenado del sistema [&#41;de Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-manage-jobs-by-login-transact-sql) . En el siguiente ejemplo se reasignan todos los trabajos de `danw` a `fran??oisa`.  
  
    ```sql
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_manage_jobs_by_login  
        @action = N'REASSIGN',  
        @current_owner_login_name = N'danw',  
        @new_owner_login_name = N'fran??oisa' ;  
    GO  
    ```  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMOProc2"></a>Usar Objetos de administración de SQL Server  

### <a name="to-give-others-ownership-of-a-job"></a>Para asignar a otros usuarios la propiedad de un trabajo
  
1.  Llame a la clase `Job` mediante el lenguaje de programación que desee, como Visual Basic, Visual C# o PowerShell. Para el código de ejemplo, consulte [Programar tareas administrativas automáticas en el Agente SQL Server](sql-server-agent.md).  
  
## <a name="see-also"></a>Consulte también  
 [Implementar trabajos](implement-jobs.md)   
 [Crear trabajos](create-jobs.md)  
