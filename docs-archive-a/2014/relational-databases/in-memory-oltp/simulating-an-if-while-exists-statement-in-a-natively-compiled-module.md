---
title: Simular una cláusula EXISTs en un procedimiento almacenado compilado de forma nativa | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c0e187c1-cbd9-463c-b417-8a734574f102
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b16491b9a3729ad4df71c7ddceaee6db21777ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750953"
---
# <a name="simulating-an-exists-clause-in-a-natively-compiled-stored-procedure"></a>Simular una cláusula EXISTS en un procedimiento almacenado compilado de forma nativa
  Los procedimientos almacenados compilados de forma nativa no admiten la cláusula `EXISTS`, pero existe una solución:  
  
```sql  
DECLARE @exists BIT = 0  
SELECT TOP 1 @exists = 1 FROM MyTable WHERE ...  
IF @exists = 1  
```  
  
## <a name="see-also"></a>Consulte también  
 [Problemas de migración para los procedimientos almacenados compilados de forma nativa](migration-issues-for-natively-compiled-stored-procedures.md)   
 [Construcciones de Transact-SQL no admitidas en In-Memory OLTP.](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
