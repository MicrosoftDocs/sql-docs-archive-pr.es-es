---
title: Eliminar una instantánea de base de datos (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- removing database snapshots
- deleting database snapshots
- database snapshots [SQL Server], deleting
ms.assetid: ad70ec97-d5fb-41aa-b72a-915e74b61b76
author: stevestein
ms.author: sstein
ms.openlocfilehash: e0d9d912a092e581fad7d3d53504309f63ba1806
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662083"
---
# <a name="drop-a-database-snapshot-transact-sql"></a>Eliminar una instantánea de base de datos (Transact-SQL)
  Al quitar una instantánea de base de datos, ésta se elimina de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y se eliminan también los archivos dispersos que utiliza. Cuando se quita una instantánea de base de datos, se terminan también todas sus conexiones de usuario.  
  
## <a name="security"></a>Seguridad  
  
###  <a name="permissions"></a><a name="Permissions"></a> Permisos  
 Cualquier usuario con permisos DROP DATABASE puede quitar una instantánea de base de datos.  
  
##  <a name="how-to-drop-a-database-snapshot-using-transact-sql"></a><a name="TsqlProcedure"></a> Quitar una instantánea de base de datos (mediante Transact-SQL)  
 **Para quitar una instantánea de base de datos**  
  
1.  Identifique la instantánea de base de datos que desee quitar. Puede ver las instantáneas de una base de datos en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Para obtener más información, vea [Ver una instantánea de base de datos &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md).  
  
2.  Ejecute una instrucción [DROP DATABASE](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) especificando el nombre de la instantánea de base de datos que se quitará. La sintaxis es la siguiente:  
  
     DROP DATABASE *nombre_de_instantánea_de_base_de_datos* [ **,** ...*n* ]  
  
     Donde *nombre_de_instantánea_de_base_de_datos* es el nombre de la instantánea de base de datos que se va a quitar.  
  
####  <a name="example-transact-sql"></a><a name="TsqlExample"></a> Ejemplo (Transact-SQL)  
 En este ejemplo se quita una instantánea de base de datos, denominada SalesSnapshot0600, sin que la base de datos de origen se vea afectada.  
  
```  
DROP DATABASE SalesSnapshot0600 ;  
```  
  
 Finalizan todas las conexiones de usuario a SalesSnapshot0600 y se eliminan todos los archivos dispersos del sistema de archivos NTFS que utiliza la instantánea.  
  
> [!NOTE]  
>  Para obtener más información sobre cómo las instantáneas de base de datos usan archivos dispersos, vea [Instantáneas de base de datos &#40;SQL Server&#41;](database-snapshots-sql-server.md).  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tareas relacionadas  
  
-   [Crear una instantánea de base de datos &#40;Transact-SQL&#41;](create-a-database-snapshot-transact-sql.md)  
  
-   [Ver una instantánea de base de datos &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md)  
  
-   [Revertir una base de datos a una instantánea de base de datos](revert-a-database-to-a-database-snapshot.md)  
  

  
## <a name="see-also"></a>Consulte también  
 [DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql)   
 [Instantáneas de bases de datos &#40;SQL Server&#41;](database-snapshots-sql-server.md)  
  
  
