---
title: Separar una base de datos | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.detachdatabase.f1
helpviewer_keywords:
- database detaching [SQL Server]
- detaching databases [SQL Server]
ms.assetid: f63d4107-13e4-4bfe-922d-5e4f712e472d
author: stevestein
ms.author: sstein
ms.openlocfilehash: b8acc809b881012d18f78995bb8e521337fb02ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87677663"
---
# <a name="detach-a-database"></a>Separar una base de datos
  En este tema se describe cómo separar una base de datos en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Los archivos separados permanecen y se pueden volver a adjuntar utilizando CREATE DATABASE con la opción FOR ATTACH o FOR ATTACH_REBUILD_LOG. Los archivos se pueden mover a otro servidor y adjuntarse allí.  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Limitaciones y restricciones](#Restrictions)  
  
     [Seguridad](#Security)  
  
-   **Para separar una base de datos, utilizando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitaciones y restricciones  
 Para obtener una lista de las limitaciones y restricciones, vea [Adjuntar y separar bases de datos &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md).  
  
###  <a name="security"></a><a name="Security"></a> Seguridad  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permisos  
 Requiere pertenencia al rol fijo de base de datos db_owner.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Uso de SQL Server Management Studio  
  
#### <a name="to-detach-a-database"></a>Para separar una base de datos  
  
1.  En el Explorador de objetos de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , conéctese a la instancia del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] y expándala.  
  
2.  Expanda **Bases de datos**y seleccione el nombre de la base de datos de usuarios que desee separar.  
  
3.  Haga clic con el botón derecho en el nombre de la base de datos, seleccione **Tareas**y haga clic en **Separar**. Aparecerá el cuadro de diálogo **Separar base de datos** .  
  
     **Bases de datos que se van a separar**  
     Enumera las bases de datos que se van a separar.  
  
     **Nombre de la base de datos**  
     Muestra el nombre de la base de datos que se va a separar.  
  
     **Quitar conexiones**  
     Desconecta las conexiones a la base de datos especificada.  
  
    > [!NOTE]  
    >  No puede separar una base de datos con conexiones activas.  
  
     **Actualizar estadísticas**  
     De forma predeterminada, la operación de separación conserva las estadísticas de optimización obsoletas al separar la base de datos; para actualizar las estadísticas de optimización existentes, haga clic en esta casilla.  
  
     **Mantener catálogos de texto completo**  
     De forma predeterminada, la operación de separación conserva los catálogos de texto completo asociados a la base de datos. Para quitarlos, desactive la casilla **Mantener catálogos de texto completo** . Esta opción solo aparece cuando se está actualizando una base de datos desde [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
     **Estado**  
     Muestra uno de los siguientes estados: **Listo** o **No está listo**.  
  
     **Mensaje**  
     En la columna **Mensaje** puede aparecer información sobre la base de datos, tal y como se indica a continuación:  
  
    -   Cuando una base de datos está implicada en una replicación, el **Estado** es **No está listo** y la columna **Mensaje** muestra **Base de datos replicada**.  
  
    -   Cuando una base de datos tiene una o varias conexiones activas, el valor de **Estado** es **No está listo** y en la columna **Mensaje** se muestra _<número_de_conexiones_activas>_ **Conexiones activas** (por ejemplo: **1 conexión activa**). Antes de separar la base de datos, debe desconectar todas las conexiones activas seleccionando **Quitar conexiones**.  
  
     Para obtener más información acerca de un mensaje, haga clic en el texto con hipervínculo para abrir el Monitor de actividad.  
  
4.  Cuando esté listo para separar la base de datos, haga clic en **Aceptar**.  
  
> [!NOTE]  
>  La base de datos recién separada permanecerá visible en el nodo **Bases de datos** del Explorador de objetos hasta que se actualice la vista. Puede actualizar la vista en cualquier momento: haga clic en el panel del Explorador de objetos y en la barra de menús seleccione **Ver** y, a continuación, **Actualizar**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Usar Transact-SQL  
  
#### <a name="to-detach-a-database"></a>Para separar una base de datos  
  
1.  Conéctese con el [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**. En este ejemplo se separa la base de datos AdventureWorks2012 con el valor de skipchecks establecido en true.  
  
```  
EXEC sp_detach_db 'AdventureWorks2012', 'true';  
```  
  
## <a name="see-also"></a>Consulte también  
 [Adjuntar y separar bases de datos &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md)   
 [sp_detach_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql)  
  
  
