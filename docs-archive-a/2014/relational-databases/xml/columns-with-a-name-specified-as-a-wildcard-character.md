---
title: Columnas con un nombre especificado como carácter comodín | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: d9551df1-5bb4-4c0b-880a-5bb049834884
author: rothja
ms.author: jroth
ms.openlocfilehash: 4b363baf8792628c2e17b1a695c19a6a338f4fb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672831"
---
# <a name="columns-with-a-name-specified-as-a-wildcard-character"></a>Columnas con un nombre especificado como carácter comodín
  Si el nombre de columna especificado es un carácter comodín (\*), su contenido se insertará como si no se hubiera especificado ningún nombre. Si esta columna no es del tipo `xml`, su contenido se insertará como un nodo de texto, tal y como se muestra en el ejemplo siguiente:  
  
```  
USE AdventureWorks2012;  
GO  
SELECT E.BusinessEntityID "@EmpID",   
       FirstName "*",   
       MiddleName "*",   
       LastName "*"  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
    ON E.BusinessEntityID = P.BusinessEntityID  
WHERE E.BusinessEntityID=1  
FOR XML PATH;  
```  
  
 El resultado es el siguiente:  
  
 `<row EmpID="1">KenJS??nchez</row>`  
  
 Si la columna es de tipo `xml`, se inserta el árbol XML correspondiente. Por ejemplo, la consulta siguiente especifica "*" para el nombre de columna que incluye el XML devuelto por XQuery con la columna Instructions.  
  
```  
SELECT   
       ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
                /MI:root/MI:Location   
              ') as "*"  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH;   
GO  
```  
  
 Éste es el resultado. El XML devuelto por XQuery se insertará sin un elemento de ajuste.  
  
 `<row>`  
  
 `<ProductModelID>7</ProductModelID>`  
  
 `<Name>HL Touring Frame</Name>`  
  
 `<MI:Location LocationID="10">...</MI:Location>`  
  
 `<MI:Location LocationID="20">...</MI:Location>`  
  
 `...`  
  
 `</row>`  
  
## <a name="see-also"></a>Consulte también  
 [Usar el modo PATH con FOR XML](use-path-mode-with-for-xml.md)  
  
  
