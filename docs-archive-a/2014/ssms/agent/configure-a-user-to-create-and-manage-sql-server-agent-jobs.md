---
title: Configurar un usuario para crear y administrar trabajos del Agente SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, user configuration
- jobs [SQL Server Agent], user configuration
- SQLAgentUserRole database role
- proxy accounts [SQL Server Agent]
ms.assetid: 67897e3e-b7d0-43dd-a2e2-2840ec4dd1ef
author: stevestein
ms.author: sstein
ms.openlocfilehash: 83313389b3b872004fb23b0babdad19cfb5b8e7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87677368"
---
# <a name="configure-a-user-to-create-and-manage-sql-server-agent-jobs"></a>Configure a User to Create and Manage SQL Server Agent Jobs
  En este tema se describe cómo configurar un usuario para crear o ejecutar [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trabajos del agente.  
  
-   **Antes de empezar:**  [Seguridad](#Security)  
  
-   **Para configurar un usuario para crear y administrar trabajos del Agente SQL Server, usando:**  [SQL Server Management Studio](#SSMS)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="security"></a><a name="Security"></a> Seguridad  
 Para configurar un usuario para crear o ejecutar [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trabajos del agente, primero debe agregar un inicio de sesión de SQL Server existente o un rol msdb a uno de los siguientes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] roles fijos de base de datos del agente en la base de datos msdb: SQLAgentUserRole, SQLAgentReaderRole o SQLAgentOperatorRole.  
  
 De forma predeterminada, los miembros de estos roles de la base de datos pueden crear sus propios pasos de trabajo que se ejecutan como ellos mismos. Si estos usuarios no administrativos desean ejecutar trabajos que ejecuten otros tipos de pasos de trabajo (por ejemplo, paquetes [!INCLUDE[ssIS](../../includes/ssis-md.md)] ), necesitarán tener acceso a una cuenta de proxy. Todos los miembros del rol fijo de servidor sysadmin tienen permiso para crear, modificar o eliminar cuentas de proxy. Para más información sobre los permisos asociados con estos roles fijos de base de datos del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consulte [Roles fijos de base de datos del Agente SQL Server](sql-server-agent-fixed-database-roles.md).  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permisos  
 Para obtener información detallada, vea [Implementar la seguridad del Agente SQL Server](implement-sql-server-agent-security.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Uso de SQL Server Management Studio  
 **Para agregar un inicio de sesión de SQL o un rol msdb a un rol fijo de base de datos del Agente SQL Server**  
  
1.  En el **Explorador de objetos**, expanda un servidor.  
  
2.  Expanda **Seguridad**y, a continuación, **Inicios de sesión**.  
  
3.  Haga clic con el botón derecho en el inicio de sesión que desee agregar a un rol fijo de base de datos del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y seleccione **Propiedades**.  
  
4.  En la página **asignación de usuarios** del cuadro de diálogo Propiedades de inicio de **sesión** , seleccione la fila que contiene `msdb` .  
  
5.  En **Miembros del rol de base de datos para: msdb**, active el rol fijo de base de datos del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] adecuado.  
  
 **Para configurar una cuenta de proxy para crear y administrar pasos de trabajo del Agente SQL Server**  
  
1.  En el **Explorador de objetos**, expanda un servidor.  
  
2.  Expanda **Agente SQL Server**.  
  
3.  Haga clic con el botón derecho en **Servidores proxy** y seleccione **Nuevo proxy**.  
  
4.  En la página **General** del cuadro de diálogo **Nueva cuenta de proxy** , especifique el nombre del proxy, el nombre de credencial y la descripción del nuevo proxy. Tenga en cuenta que debe crear una credencial antes de crear un proxy del Agente SQL Server. Para obtener más información sobre cómo crear una credencial, vea [crear una credencial](../../relational-databases/security/authentication-access/create-a-credential.md) y [crear credenciales &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql).  
  
5.  Seleccione los subsistemas correspondientes para este proxy.  
  
6.  En la página **Entidades de seguridad** , agregue o quite inicios de sesión o roles para conceder o quitar el acceso a la cuenta de proxy.  
  
## <a name="see-also"></a>Consulte también  
 [Implementar la seguridad del Agente SQL Server](implement-sql-server-agent-security.md)  
  
  
