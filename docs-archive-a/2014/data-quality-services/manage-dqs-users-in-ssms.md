---
title: Administrar usuarios de DQS en SSMS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 955af01d-00da-4c51-9311-f3848749df54
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bf8789abb59d168f39562f6486bb5c54bfc0fc50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676669"
---
# <a name="manage-dqs-users-in-ssms"></a>Administrar usuarios de DQS en SSMS
  En este tema se describe cómo crear usuarios adicionales en la instancia de SQL Server con SQL Server Management Studio y cómo concederles roles de [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) adecuados en la base de datos DQS_MAIN.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="security"></a><a name="Security"></a> Seguridad  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permisos  
 Para crear el inicio de sesión de SQL y concederle los roles de DQS adecuados, debe usarse una cuenta de usuario de Windows que sea miembro del rol fijo de servidor adecuado (como securityadmin, serveradmin o sysadmin).  
  
##  <a name="create-a-sql-login-and-grant-dqs-role"></a><a name="GrantRoles"></a>Crear un inicio de sesión de SQL y conceder el rol de DQS  
  
1.  Inicie Microsoft SQL Server Management Studio.  
  
2.  En Microsoft SQL Server Management Studio, expanda la instancia de SQL Server y, a continuación, expanda **Seguridad**.  
  
3.  Haga clic con el botón derecho en la carpeta **Seguridad** , seleccione **Nuevo**y, después, haga clic en **Inicio de sesión**.  
  
4.  En el cuadro de diálogo **Inicio de sesión-nuevo** , especifique el nombre de un usuario de Windows en el cuadro **nombre de inicio de sesión** , especifique el tipo de autenticación como autenticación de **Windows**y haga clic en **Buscar** para validar el usuario.  
  
    > [!NOTE]  
    >  DQS solo admite la autenticación de Windows; la autenticación de SQL Server no se admite.  
  
5.  Después de validar el usuario, haga clic en la página **Asignación de usuarios** en el panel izquierdo.  
  
6.  En el panel derecho, active la casilla en la columna **Asignar** para la base de datos **DQS_MAIN** y, después, active la casilla **dqs_administrator**, **dqs_kb_editor**o **dqs_kb_operator** en el panel **Pertenencia al rol de base de datos para: DQS_MAIN** , dependiendo del nivel de acceso necesario para el usuario.  
  
7.  En el cuadro de diálogo **Inicio de sesión - Nuevo**, haga clic en **Aceptar** para aplicar los cambios.  
  
    > [!NOTE]  
    >  Si concede el rol **dqs_administrator** a un usuario, aplica los cambios y, tras ello, vuelve a revisar los permisos de usuario, las otras dos casillas de roles de DQS (**dq_kb_editor** y **dqs_kb_operator**) también se activan.  
  
  
