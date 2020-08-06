---
title: MSSQLSERVER_1904 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1904 (Database Engine error)
ms.assetid: 2a35d57d-74e2-45a2-8f67-3f2e51d69712
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 568cfe7499c041c2ee6a8ac3698b31698171bece
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672071"
---
# <a name="mssqlserver_1904"></a>MSSQLSERVER_1904
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre de producto|SQL Server|  
|Id. de evento|1904|  
|Origen de eventos|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|KEYCOUNT|  
|Texto del mensaje|%S_MSG '%.*ls' en la tabla '%.\*ls' tiene %d nombres de columna en la lista de claves %S_MSG. El límite máximo para la lista de columnas de clave de índice o estadísticas es %d.|  
  
## <a name="explanation"></a>Explicación  
 La lista de columnas de clave para el índice o estadística especificados supera el número máximo permitido de columnas.  
  
## <a name="user-action"></a>Acción del usuario  
 Modifique la lista de columnas de clave para que no incluya más columnas del número máximo especificado.  
  
 Con los índices no clúster, considere utilizar la cláusula INCLUDE en la instrucción CREATE INDEX para agregar columnas al índice como columnas sin clave. Este método impide superar la limitación de tamaño de índice actual de 16 columnas de clave como máximo. Para más información, consulte [Create Indexes with Included Columns](../indexes/create-indexes-with-included-columns.md).  
  
## <a name="see-also"></a>Consulte también  
 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)   
 [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql)  
  
  
