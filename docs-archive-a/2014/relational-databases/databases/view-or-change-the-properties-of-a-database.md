---
title: Ver o cambiar las propiedades de una base de datos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- displaying databases
- database viewing [SQL Server]
- databases [SQL Server], viewing
- viewing databases
ms.assetid: 9e8ac097-84b7-46c7-85e3-c1e79f94d747
author: stevestein
ms.author: sstein
ms.openlocfilehash: d6aee7503ca02d47575be4e8103641f61d9696d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87749961"
---
# <a name="view-or-change-the-properties-of-a-database"></a>Ver o cambiar las propiedades de una base de datos
  En este tema se describe cómo ver o cambiar las propiedades de una base de datos en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Después de cambiar una propiedad de la base de datos, la modificación surte efecto de inmediato.  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Recomendaciones](#Recommendations)  
  
     [Seguridad](#Security)  
  
-   **Para ver o cambiar las propiedades de una base de datos, use:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Recomendaciones  
  
-   Si AUTO_CLOSE es ON, algunas columnas de la vista de catálogo [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) y de la función DATABASEPROPERTYEX devuelven NULL porque la base de datos no está disponible para recuperar los datos. Para resolver este problema, ejecute la instrucción USE para abrir la base de datos.  
  
###  <a name="security"></a><a name="Security"></a> Seguridad  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permisos  
 Requiere el permiso ALTER en la base de datos.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Uso de SQL Server Management Studio  
  
#### <a name="to-view-or-change-the-properties-of-a-database"></a>Para ver o cambiar las propiedades de una base de datos  
  
1.  En el **Explorador de objetos**, conéctese a una instancia del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]y, a continuación, expándala.  
  
2.  Expanda **Bases de datos**, haga clic con el botón derecho en la base de datos que quiera ver y, después, haga clic en **Propiedades**.  
  
3.  En el cuadro de diálogo **Propiedades de la base de datos** , seleccione una página para ver la información correspondiente. Por ejemplo, seleccione la página **Archivos** para ver información acerca de los archivos de datos y de registro.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Usar Transact-SQL  
  
#### <a name="to-view-a-property-of-a-database-by-using-databasepropertyex"></a>Para ver una propiedad de una base de datos con DATABASEPROPERTYEX  
  
1.  Conéctese con el [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**. Este ejemplo usa la función de sistema [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) para devolver el estado de la opción de base de datos AUTO_SHRINK en la base de datos de [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Un valor devuelto de 1 significa que la opción está establecida en ON y un valor devuelto de 0 significa que la opción está establecida en OFF.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT DATABASEPROPERTYEX('AdventureWorks2012', 'IsAutoShrink');  
GO  
  
```  
  
#### <a name="to-view-the-properties-of-a-database-by-querying-sysdatabases"></a>Para ver las propiedades de una base de datos consultando sys.databases  
  
1.  Conéctese con el [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**. En este ejemplo se consulta la vista de catálogo [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) para ver varias propiedades de la base de datos [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Este ejemplo devuelve el número de id. de base de datos (`database_id`), un valor que indica si la base de datos es de solo lectura o de lectura y escritura (`is_read_only`), la intercalación de la base de datos (`collation_name`) y el nivel de compatibilidad de la base de datos (`compatibility_level`).  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT database_id, is_read_only, collation_name, compatibility_level  
FROM sys.databases WHERE name = 'AdventureWorks2012';  
GO  
  
```  
  
#### <a name="to-change-the-properties-of-a-database"></a>Para cambiar las propiedades de una base de datos  
  
1.  Conéctese con el [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el ejemplo siguiente en la ventana de consulta. El ejemplo determina el estado de aislamiento de instantánea en la base de datos [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] , cambia el estado de la propiedad y comprueba el cambio.  
  
     Para determinar el estado de aislamiento de instantánea, seleccione la primera instrucción `SELECT` y haga clic en **Ejecutar**.  
  
     Para cambiar el estado de aislamiento de instantánea, seleccione la instrucción `ALTER DATABASE` y haga clic en **Ejecutar**de.  
  
     Para comprobar el cambio, seleccione la segunda instrucción `SELECT` y haga clic en **Ejecutar**.  
  
 [!code-sql[DatabaseDDL#AlterDatabase9](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase9)]  
  
## <a name="see-also"></a>Consulte también  
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)   
 [ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-hadr)   
 [Opciones de ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)   
 [Reflejo de la base de datos ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)   
 [Nivel de compatibilidad de ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)   
 [Opciones File y Filegroup de ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)  
  
  
