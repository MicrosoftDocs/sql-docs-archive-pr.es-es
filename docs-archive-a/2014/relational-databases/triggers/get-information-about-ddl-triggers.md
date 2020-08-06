---
title: Obtener información sobre los desencadenadores DDL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- metadata [SQL Server], triggers
- status information [SQL Server], DDL triggers
- DDL triggers, metadata
ms.assetid: 462becea-292a-4b9e-bb98-533e89733911
author: rothja
ms.author: jroth
ms.openlocfilehash: 9cd71d188c2f53bd9872359199c07d700688552d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676925"
---
# <a name="get-information-about-ddl-triggers"></a>Obtener información acerca de los desencadenadores DDL
  Las vistas de catálogo que se enumeran en esta sección pueden utilizarse para obtener información sobre los desencadenadores DDL.  
  
 **Para obtener información sobre los eventos o grupos de eventos en que un desencadenador DDL puede activar**  
  
-   [sys.trigger_event_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-event-types-transact-sql)  
  
 **Para ver las dependencias de un desencadenador**  
  
-   [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
-   [sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)  
  
-   [sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql)  
  
## <a name="database-scoped-ddl-triggers"></a>Desencadenadores DDL con ámbito de base de datos  
 **Para obtener información acerca de los desencadenadores con ámbito de base de datos**  
  
-   [sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql)  
  
 **Para obtener información acerca de los desencadenadores que activan eventos de base de datos**  
  
-   [sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql)  
  
 **Para ver la definición de un desencadenador con ámbito de base de datos**  
  
-   [sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)  
  
 **Para obtener información acerca de los desencadenadores con ámbito de base de datos de CLR**  
  
-   [sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql)  
  
## <a name="server-scoped-ddl-triggers"></a>Desencadenadores DDL con ámbito de servidor  
 **Para obtener información acerca de los desencadenadores con ámbito de servidor**  
  
-   [sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql)  
  
 **Para obtener información acerca de los desencadenadores que activan eventos de base de datos**  
  
-   [sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql)  
  
 **Para ver la definición de un desencadenador con ámbito de servidor**  
  
-   [sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql)  
  
 **Para obtener información acerca de los desencadenadores con ámbito de servidor de CLR**  
  
-   [sys.server_assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql)  
  
## <a name="see-also"></a>Consulte también  
 [Desencadenadores DDL](../triggers/ddl-triggers.md)  
  
  
