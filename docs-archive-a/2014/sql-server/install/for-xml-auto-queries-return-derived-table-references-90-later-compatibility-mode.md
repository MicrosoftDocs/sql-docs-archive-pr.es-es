---
title: Las consultas FOR XML AUTO devuelven referencias de tabla derivadas en los modos de compatibilidad 90 o posterior | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- FOR XML AUTO [SQL Server]
ms.assetid: 10c32f06-f7e1-40e0-8f79-6d921f2bef1d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 702cb2ca1d437dff03cee09c98d72082500709d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87678041"
---
# <a name="for-xml-auto-queries-return-derived-table-references-in-90-or-later-compatibility-modes"></a>Las consultas FOR XML AUTO devuelven referencias a tablas derivadas en los modos de compatibilidad 90 o superiores
  Cuando el nivel de compatibilidad de la base de datos está establecido en 90 o más, las consultas FOR XML que se ejecutan en modo AUTO devuelven referencias a alias de tabla derivadas. Cuando el nivel de compatibilidad de la base de datos está establecido en 80, las consultas FOR XML AUTO devuelven referencias a las tablas base que definen una tabla derivada.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Descripción  
 Considere, por ejemplo, la siguiente tabla:  
  
```  
CREATE TABLE Test(id int);  
INSERT INTO Test VALUES(1);  
INSERT INTO Test VALUES(2);  
```  
  
 La siguiente consulta, que incluye una tabla derivada, genera resultados diferentes en los niveles de compatibilidad 80, 90 y posteriores:  
  
```  
SELECT * FROM   
   (SELECT a.id AS a, b.id AS b   
    FROM Test a JOIN Test b ON a.id=b.id)  
AS DerivedTest   
FOR XML AUTO;  
```  
  
 En el nivel de compatibilidad 80, la consulta devuelve los resultados siguientes. Los resultados hacen referencia a los alias de la tabla base `a` y `b` de la tabla derivada, en lugar del alias de la tabla derivada.  
  
```  
<a a="1"><b b="1"/></a><a a="2"><b b="2"/></a>  
```  
  
 En el nivel de compatibilidad 90 o superior, la consulta devuelve referencias a los alias de la tabla derivada `DerivedTest` en lugar de a las tablas base de la tabla derivada.  
  
```  
<DerivedTest a="1" b="1"/><DerivedTest a="2" b="2"/>  
```  
  
## <a name="corrective-action"></a>Acción correctora  
 Modifique su aplicación de acuerdo a los cambios en los resultados de las consultas FOR XML AUTO que incluyen tablas derivadas y que se ejecutan en el nivel de compatibilidad 90 o superior.  
  
## <a name="see-also"></a>Consulte también  
 [Problemas de actualización Motor de base de datos](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server el asesor de actualizaciones de 2014 &#91;nuevo&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
