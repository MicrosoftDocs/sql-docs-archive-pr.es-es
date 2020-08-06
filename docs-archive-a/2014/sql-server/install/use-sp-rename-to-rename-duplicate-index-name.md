---
title: Usar sp_rename para cambiar el nombre del índice duplicado | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- table names [SQL Server]
- duplicate table names
- index names [SQL Server]
- sp_rename
- duplicate index names
ms.assetid: ee66c7a5-eb6d-4fcf-970c-ab099d78c8d9
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b8ffe3b9befd0c7239d32094e5738e0fb2947c5a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751661"
---
# <a name="use-sp_rename-to-rename-duplicate-index-name"></a>Utilizar sp_rename para cambiar el nombre de índice duplicado
  El Asesor de actualizaciones ha detectado nombres de índice de vista o tabla duplicados. Cambie los nombres de los índices o quite los duplicados antes de actualizar.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Acción correctora  
  
1.  Localice los índices duplicados ejecutando la siguiente consulta.  
  
    ```  
    SELECT DISTINCT OBJECT_NAME(o.id), name  
    FROM sysindexes as o  
    WHERE EXISTS   
        (SELECT name FROM sysindexes  as i  
          WHERE i.id = o.id  
          AND i.name = o.name and i.indid < o.indid);  
    ```  
  
2.  Utilice **sp_rename** para cambiar uno de los nombres de índice. Como los nombres de índice son los mismos, no puede determinar qué índice cambiará de nombre. Este paso le permite diferenciar los índices.  
  
    ```  
    EXEC sp_rename N'table_name.index_name', N'new_index_name', N'INDEX'  
    ```  
  
3.  Compruebe qué índice ha cambiado de nombre ejecutando la siguiente consulta. Esta consulta devuelve todos los índices (incluidos los nombres de columnas de clave) de la vista o tabla especificada.  
  
    ```  
    SELECT i.name AS IndexName, c.name AS ColumnName, ik.colid, ik.keyno  
    FROM sysindexes i  
    JOIN sysindexkeys ik ON i.id = ik.id and i.indid = ik.indid   
    JOIN syscolumns c ON c.id = ik.id and ik.colid = c.colid  
    WHERE i.id = OBJECT_ID('table_or_view_name')  
    ```  
  
4.  Si fuera necesario, utilice de nuevo **sp_rename** para corregir los nombres de índice.  
  
## <a name="see-also"></a>Consulte también  
 [Problemas de actualización Motor de base de datos](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server el asesor de actualizaciones de 2014 &#91;nuevo&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
