---
title: 'Ejemplo: Especificación de la directiva HIDE | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- HIDE directive
ms.assetid: 87504d87-1cbd-412a-9041-47884b6efcec
author: rothja
ms.author: jroth
ms.openlocfilehash: 423ee36f679467c07a604b9754172f6e261971b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676389"
---
# <a name="example-specifying-the-hide-directive"></a><span data-ttu-id="c4725-102">Ejemplo: Especificación de la directiva HIDE</span><span class="sxs-lookup"><span data-stu-id="c4725-102">Example: Specifying the HIDE Directive</span></span>
  <span data-ttu-id="c4725-103">En este ejemplo se muestra el uso de la directiva **HIDE** .</span><span class="sxs-lookup"><span data-stu-id="c4725-103">This example illustrates the use of the **HIDE** directive.</span></span> <span data-ttu-id="c4725-104">Esta directiva es útil cuando se desea que la consulta devuelva un atributo para ordenar las filas de la tabla universal devuelta por la consulta, pero no se desea que ese atributo aparezca en el documento XML resultante.</span><span class="sxs-lookup"><span data-stu-id="c4725-104">This directive is useful when you want the query to return an attribute for ordering the rows in the universal table that is returned by the query, but you do not want that attribute in the final resulting XML document.</span></span>  
  
 <span data-ttu-id="c4725-105">Esta consulta genera este XML:</span><span class="sxs-lookup"><span data-stu-id="c4725-105">This query constructs this XML:</span></span>  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription>  
           <Summary> element from XML stored in CatalogDescription column  
    </SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
 <span data-ttu-id="c4725-106">Esta consulta genera el XML deseado.</span><span class="sxs-lookup"><span data-stu-id="c4725-106">This query generates the XML you want.</span></span> <span data-ttu-id="c4725-107">La consulta identifica dos grupos de columnas con valores 1 y 2 de Tag en los nombres de columna.</span><span class="sxs-lookup"><span data-stu-id="c4725-107">The query identifies two column groups having 1 and 2 as Tag values in the column names.</span></span>  
  
 <span data-ttu-id="c4725-108">Esta consulta usa el [método query()](/sql/t-sql/xml/query-method-xml-data-type) del tipo de datos **xml** para consultar la columna CatalogDescription de tipo **xml** y recuperar la descripción resumida.</span><span class="sxs-lookup"><span data-stu-id="c4725-108">This query uses the [query() Method (xml Data Type)](/sql/t-sql/xml/query-method-xml-data-type) of the **xml** data type to query the CatalogDescription column of **xml** type in order to retrieve the summary description.</span></span> <span data-ttu-id="c4725-109">Esta consulta también usa el [método value()](/sql/t-sql/xml/value-method-xml-data-type) del tipo de datos **xml** para recuperar el valor ProductModelID de la columna CatalogDescription.</span><span class="sxs-lookup"><span data-stu-id="c4725-109">The query also uses the [value() Method (xml Data Type)](/sql/t-sql/xml/value-method-xml-data-type) of the **xml** data type to retrieve the ProductModelID value from the CatalogDescription column.</span></span> <span data-ttu-id="c4725-110">Este valor no se requiere en el XML resultante, pero sí es necesario para ordenar el conjunto de filas resultante.</span><span class="sxs-lookup"><span data-stu-id="c4725-110">This value is not required in the resulting XML, but is required to sort the resulting rowset.</span></span> <span data-ttu-id="c4725-111">Por consiguiente, el nombre de columna, `[Summary!2!ProductModelID!HIDE]`, incluye la directiva **HIDE** .</span><span class="sxs-lookup"><span data-stu-id="c4725-111">Therefore, the column name, `[Summary!2!ProductModelID!HIDE]`, includes the **HIDE** directive.</span></span> <span data-ttu-id="c4725-112">Si esta columna no se incluye en la instrucción SELECT, habrá que ordenar el conjunto de filas según `[ProductModel!1!ProdModelID]` y `[Summary!2!SummaryDescription]` , que es de tipo **xml** , y no se podrá usar la columna de tipo **xml** en ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="c4725-112">If this column is not included in the SELECT statement, you will have to sort the rowset by `[ProductModel!1!ProdModelID]` and `[Summary!2!SummaryDescription]` that is **xml** type and you cannot use the **xml** type column in ORDER BY.</span></span> <span data-ttu-id="c4725-113">Por tanto, se agrega la columna adicional `[Summary!2!ProductModelID!HIDE]` y luego se especifica en la cláusula ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="c4725-113">Therefore, the additional `[Summary!2!ProductModelID!HIDE]` column is added and is then specified in the ORDER BY clause.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID     as [ProductModel!1!ProdModelID],  
        Name               as [ProductModel!1!Name],  
        NULL               as [Summary!2!ProductModelID!hide],  
        NULL               as [Summary!2!SummaryDescription]  
FROM    Production.ProductModel  
WHERE   CatalogDescription is not null  
UNION ALL  
SELECT  2 as Tag,  
        1 as Parent,  
        ProductModelID,  
        Name,  
        CatalogDescription.value('  
         declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
       (/PD:ProductDescription/@ProductModelID)[1]', 'int'),  
        CatalogDescription.query('  
         declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
         /pd:ProductDescription/pd:Summary')  
FROM    Production.ProductModel  
WHERE   CatalogDescription is not null  
ORDER BY [ProductModel!1!ProdModelID],[Summary!2!ProductModelID!hide]  
FOR XML EXPLICIT  
go  
```  
  
 <span data-ttu-id="c4725-114">El resultado es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="c4725-114">This is the result:</span></span>  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription>  
      <pd:Summary xmlns:pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription" xmlns="">  
        <p1:p xmlns:p1="http://www.w3.org/1999/xhtml">Our top-of-the-line competition mountain bike. Performance-enhancing options include the innovative HL Frame, super-smooth front suspension, and traction for all terrain. </p1:p>  
      </pd:Summary>  
    </SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4725-115">Consulte también</span><span class="sxs-lookup"><span data-stu-id="c4725-115">See Also</span></span>  
 [<span data-ttu-id="c4725-116">Usar el modo EXPLICIT con FOR XML</span><span class="sxs-lookup"><span data-stu-id="c4725-116">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
