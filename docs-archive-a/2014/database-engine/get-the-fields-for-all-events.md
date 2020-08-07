---
title: Obtener los campos de todos los eventos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], getting fields
- xe
ms.assetid: 4e4ee03f-5bca-42ed-a37c-db1c82e3aad2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 01d98e827121a0c47111dd601c6e1772f796849d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746421"
---
# <a name="get-the-fields-for-all-events"></a>Obtener los campos de todos los eventos
  Esta tarea se lleva a cabo con el Editor de consultas en [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
 Una vez finalizadas las instrucciones de este procedimiento, la pestaña **Resultados** del Editor de consultas mostrará las columnas siguientes:  
  
-   package_name  
  
-   event_name  
  
-   event_field  
  
-   field_type  
  
-   column_type  
  
 Puede utilizar la información anterior al configurar sesiones de evento que utilizan el destino de creación de depósitos. Para más información, consulte [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md).  
  
## <a name="before-you-begin"></a>Introducción  
 Antes de crear una sesión de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Extended Events, resulta útil obtener información sobre los campos asociados a los eventos.  
  
## <a name="to-get-the-fields-for-all-events-using-query-editor"></a>Para obtener los campos de todos los eventos mediante el Editor de consultas  
  
-   En el Editor de consultas, emita las instrucciones siguientes.  
  
    ```  
    select p.name package_name, o.name event_name, c.name event_field, c.type_name field_type, c.column_type column_type  
    from sys.dm_xe_objects o  
    join sys.dm_xe_packages p  
          on o.package_guid = p.guid  
    join sys.dm_xe_object_columns c  
          on o.name = c.object_name  
    where o.object_type = 'event'  
    order by package_name, event_name  
    ```  
  
## <a name="see-also"></a>Consulte también  
 [sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)   
 [sys.dm_xe_packages &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
