---
title: Especificar predicados de selección en la ruta de acceso de ubicación (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], predicates
- predicates [SQLXML]
- position-based filtering [SQLXML]
- XPath queries [SQLXML], location paths
- filtering [SQLXML]
- location path for XPath query
ms.assetid: dbef4cf4-a89b-4d7e-b72b-4062f7b29a80
author: rothja
ms.author: jroth
ms.openlocfilehash: d323558556fb05d350e48ea9218a8e9b8dc9b5c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673576"
---
# <a name="specifying-selection-predicates-in-the-location-path-sqlxml-40"></a>Especificar predicados de selección en la ruta de acceso de ubicación (SQLXML 4.0)
  Un predicado filtra un conjunto de nodos con respecto a un eje (similar a una cláusula WHERE en una instrucción SELECT). El predicado se especifica entre corchetes. Para cada nodo del conjunto de nodos que se va a filtrar, la expresión de predicado se evalúa con ese nodo como el nodo de contexto, con el número de nodos del conjunto de nodos como tamaño de contexto. Si la expresión de predicado se evalúa como TRUE para ese nodo, el nodo se incluye en el conjunto de nodos resultante.  
  
 XPath también permite el filtrado basado en posición. Una expresión de predicado que se evalúa como un número selecciona ese nodo ordinal. Por ejemplo, la ruta de acceso de la ubicación `Customer[3]` devuelve el tercer cliente. No se admiten tales predicados numéricos. Solo se admiten expresiones de predicado que devuelven un resultado Booleano.  
  
> [!NOTE]  
>  Para obtener información acerca de las limitaciones de esta implementación XPath de XPath y las diferencias entre ella y la especificación W3C, vea [Introducción al uso de consultas xpath &#40;SQLXML 4,0&#41;](../introduction-to-using-xpath-queries-sqlxml-4-0.md).  
  
## <a name="selection-predicate-example-1"></a>Predicado de selección: ejemplo 1  
 La expresión XPath siguiente (ruta de acceso de ubicación) selecciona del nodo de contexto actual todos los **\<Customer>** elementos secundarios que tienen el atributo **CustomerID** con el valor ALFKI:  
  
```  
/child::Customer[attribute::CustomerID="ALFKI"]  
```  
  
 En esta consulta XPath, `child` y `attribute` son nombres de eje. `Customer`es la prueba de nodo (TRUE si `Customer` es **\<element node>** , porque **\<element>** es el tipo de nodo principal del `child` eje). `attribute::CustomerID="ALFKI"` es el predicado. En el predicado, `attribute` es el eje y `CustomerID` es la prueba de nodo (true si **CustomerID** es un atributo del nodo de contexto, porque **\<attribute>** es el tipo de nodo principal del `attribute` eje).  
  
 Con la sintaxis abreviada, la consulta XPath también se puede especificar como:  
  
```  
/Customer[@CustomerID="ALFKI"]  
```  
  
## <a name="selection-predicate-example-2"></a>Predicado de selección: ejemplo 2  
 La expresión XPath siguiente (ruta de acceso de ubicación) selecciona del nodo de contexto actual todos los **\<Order>** descendientes que tienen el atributo **SalesOrderID** con el valor 1:  
  
```  
/child::Customer/child::Order[attribute::SalesOrderID="1"]  
```  
  
 En esta expresión XPath, `child` y `attribute` son los nombres del eje. `Customer`, `Order` y `SalesOrderID` son las pruebas de nodo. `attribute::OrderID="1"` es el predicado.  
  
 Con la sintaxis abreviada, la consulta XPath también se puede especificar como:  
  
```  
/Customer/Order[@SalesOrderID="1"]  
```  
  
## <a name="selection-predicate-example-3"></a>Predicado de selección: ejemplo 3  
 La expresión XPath siguiente (ruta de acceso de ubicación) selecciona del nodo de contexto actual todos los **\<Customer>** elementos secundarios que tienen uno o más **\<ContactName>** elementos secundarios:  
  
```  
child::Customer[child::ContactName]  
```  
  
 En este ejemplo se da por supuesto que **\<ContactName>** es un elemento secundario del **\<Customer>** elemento en el documento XML, al que se hace referencia como *asignación centrada en elementos* en un esquema XSD anotado.  
  
 En esta expresión XPath, `child` es el nombre de eje. `Customer`es la prueba de nodo (TRUE si `Customer` es un **\<element>** nodo, porque **\<element>** es el tipo de nodo principal del `child` eje). `child::ContactName` es el predicado. En el predicado, `child` es el eje y `ContactName` es la prueba de nodo (true si `ContactName` es un **\<element>** nodo).  
  
 Esta expresión solo devuelve los elementos **\<Customer>** secundarios del nodo de contexto que tienen elementos **\<ContactName>** secundarios.  
  
 Con la sintaxis abreviada, la consulta XPath también se puede especificar como:  
  
```  
Customer[ContactName]  
```  
  
## <a name="selection-predicate-example-4"></a>Predicado de selección: ejemplo 4  
 La expresión XPath siguiente selecciona elementos **\<Customer>** secundarios del nodo de contexto que no tienen **\<ContactName>** elementos secundarios:  
  
```  
child::Customer[not(child::ContactName)]  
```  
  
 En este ejemplo se da por supuesto que **\<ContactName>** es un elemento secundario del **\<Customer>** elemento en el documento XML y el campo ContactName no es necesario en la base de datos.  
  
 En este ejemplo, `child` es el eje. `Customer`es la prueba de nodo (TRUE si `Customer` es un \<element> nodo). `not(child::ContactName)` es el predicado. En el predicado, `child` es el eje y `ContactName` es la prueba de nodo (true si `ContactName` es un \<element> nodo).  
  
 Con la sintaxis abreviada, la consulta XPath también se puede especificar como:  
  
```  
Customer[not(ContactName)]  
```  
  
## <a name="selection-predicate-example-5"></a>Predicado de selección: ejemplo 5  
 La expresión XPath siguiente selecciona del nodo de contexto actual todos los **\<Customer>** elementos secundarios que tienen el atributo **CustomerID** :  
  
```  
child::Customer[attribute::CustomerID]  
```  
  
 En este ejemplo, `child` es el eje y `Customer` es la prueba de nodo (true si `Customer` es un \<element> nodo). `attribute::CustomerID` es el predicado. En el predicado, `attribute` es el eje y `CustomerID` es el predicado (true si `CustomerID` es un **\<attribute>** nodo).  
  
 Con la sintaxis abreviada, la consulta XPath también se puede especificar como:  
  
```  
Customer[@CustomerID]  
```  
  
## <a name="selection-predicate-example-6"></a>Predicado de selección: Ejemplo 6  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 incluye compatibilidad para las consultas XPath que contienen un producto cruzado en el predicado, como se muestra en el ejemplo siguiente:  
  
```  
Customer[Order/@OrderDate=Order/@ShipDate]  
```  
  
 Esta consulta selecciona todos los clientes con algún elemento `Order` para el que `OrderDate` sea igual a `ShipDate` de cualquier `Order`.  
  
## <a name="see-also"></a>Consulte también  
 [Introducción a los esquemas XSD anotados &#40;SQLXML 4,0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)   
 [Formato XML del lado cliente &#40;SQLXML 4,0&#41;](../../sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)  
  
  
