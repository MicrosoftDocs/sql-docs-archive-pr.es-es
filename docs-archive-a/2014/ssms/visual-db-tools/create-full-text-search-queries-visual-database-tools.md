---
title: Crear consultas de búsqueda de texto completo (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- CONTAINS predicate (Transact-SQL)
- queries [full-text search], creating
- full-text queries [SQL Server], creating
ms.assetid: 537fa556-390e-4c88-9b8e-679848d94abc
author: stevestein
ms.author: sstein
ms.openlocfilehash: f84ab465da0a1b7ac1da1211de1d5199fd28ee95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745602"
---
# <a name="create-full-text-search-queries-visual-database-tools"></a>Crear consultas de búsqueda de texto completo (Visual Database Tools)
  Las búsquedas de texto completo utilizan el predicado CONTAINS para buscar las filas que contienen el texto especificado en una determinada columna. Las búsquedas de texto completo solo pueden realizarse en las columnas que tienen índices de texto completo activos. Si intenta utilizar la cláusula CONTAINS en una columna que no tiene un índice de texto completo activo, recibirá un error. Para obtener más información sobre los índices de texto completo y la cláusula Contains, vea [búsqueda de texto completo](../../relational-databases/search/full-text-search.md) y [contiene &#40;&#41;de Transact-SQL ](/sql/t-sql/queries/contains-transact-sql).  
  
### <a name="to-create-a-full-text-search-query"></a>Para crear una consulta de búsqueda de texto completo  
  
1.  Abra una consulta del Explorador de soluciones o cree una nueva.  
  
2.  Utilice la función CONTAINS en la cláusula WHERE de su consulta para buscar una columna de texto completo.  
  
## <a name="see-also"></a>Consulte también  
 [Tipos de consultas admitidos &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Temas de procedimientos de diseño de consultas y vistas &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [Realizar operaciones básicas con consultas (Visual Database Tools)](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
