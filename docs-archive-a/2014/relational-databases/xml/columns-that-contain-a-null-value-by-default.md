---
title: Columnas que incluyen un valor NULL de forma predeterminada | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- columns [XML in SQL Server], null default value
ms.assetid: 9381c07f-6887-4a62-9730-32661f9aa87c
author: rothja
ms.author: jroth
ms.openlocfilehash: 92ea51101f73695be2075a1b41deb62ca021f496
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662700"
---
# <a name="columns-that-contain-a-null-value-by-default"></a>Columnas que incluyen un valor NULL de forma predeterminada
  De forma predeterminada, un valor NULL en una columna se asigna a la ausencia del atributo, nodo u elemento. Este comportamiento predeterminado se puede sobrescribir solicitando XML centrado en elementos mediante la directiva ELEMENTS y especificando XSINIL a fin de solicitar la adición de elementos para valores NULL, tal y como se muestra en la consulta siguiente:  
  
```  
SELECT EmployeeID as "@EmpID",   
       FirstName  as "EmpName/First",   
       MiddleName as "EmpName/Middle",   
       LastName   as "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
AND    E.EmployeeID=1  
FOR XML PATH, ELEMENTS XSINIL  
```  
  
 A continuación se muestra el resultado. Tenga en cuenta que si no se especifica XSINIL, el elemento <`Middle`> estará ausente.  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Middle xsi:nil="true" />  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
## <a name="see-also"></a>Consulte también  
 [Usar el modo PATH con FOR XML](use-path-mode-with-for-xml.md)  
  
  
