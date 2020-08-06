---
title: Introducción al uso de consultas XPath (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], about XPath queries
- W3C XPath specification
- XPath queries [SQLXML], functionality
ms.assetid: 01050a8e-0ccc-4a02-a4eb-b48be5c3f4f3
author: rothja
ms.author: jroth
ms.openlocfilehash: dd173f16ee0e97dac1c45039f75022bbf2dc0782
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662774"
---
# <a name="introduction-to-using-xpath-queries-sqlxml-40"></a><span data-ttu-id="2a683-102">Introducción al uso de consultas XPath (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="2a683-102">Introduction to Using XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="2a683-103">Una consulta XPath (Lenguaje de rutas XML) puede especificarse como parte de una dirección URL o dentro de una plantilla.</span><span class="sxs-lookup"><span data-stu-id="2a683-103">An XML Path Language (XPath) query can be specified as part of a URL or within a template.</span></span> <span data-ttu-id="2a683-104">El esquema de asignación determina la estructura de este fragmento resultante y los valores se recuperan de la base de datos.</span><span class="sxs-lookup"><span data-stu-id="2a683-104">The mapping schema determines the structure of this resulting fragment, and the values are retrieved from the database.</span></span> <span data-ttu-id="2a683-105">Este proceso es conceptualmente similar a crear vistas utilizando la instrucción CREATE VIEW y escribir consultas SQL en ellas.</span><span class="sxs-lookup"><span data-stu-id="2a683-105">This process is conceptually similar to creating views using the CREATE VIEW statement and writing SQL queries against them.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2a683-106">Para entender las consultas XPath en SQLXML 4.0, debe estar familiarizado con las vistas XML y otros conceptos relacionados, como las plantillas y el esquema de asignación.</span><span class="sxs-lookup"><span data-stu-id="2a683-106">To understand XPath queries in SQLXML 4.0, you must be familiar with XML views and related concepts such as templates and mapping schema.</span></span> <span data-ttu-id="2a683-107">Para obtener más información, vea [Introducción a los esquemas XSD anotados &#40;SQLXML 4,0&#41;](../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)y el estándar XPath definido por el World Wide Web Consortium (W3C).</span><span class="sxs-lookup"><span data-stu-id="2a683-107">For more information, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md), and the XPath standard defined by the World Wide Web Consortium (W3C).</span></span>  
  
 <span data-ttu-id="2a683-108">Un documento XML consta de nodos, como un nodo de elemento, un nodo de atributo, un nodo de texto, etc.</span><span class="sxs-lookup"><span data-stu-id="2a683-108">An XML document consists of nodes such as an element node, attribute node, text node, and so on.</span></span> <span data-ttu-id="2a683-109">Por ejemplo, fíjese en este documento XML:</span><span class="sxs-lookup"><span data-stu-id="2a683-109">For example, consider this XML document:</span></span>  
  
```  
<root>  
  <Customer cid= "C1" name="Janine" city="Issaquah">  
      <Order oid="O1" date="1/20/1996" amount="3.5" />  
      <Order oid="O2" date="4/30/1997" amount="13.4">Customer was  
          very satisfied</Order>  
   </Customer>  
   <Customer cid="C2" name="Ursula" city="Oelde" >  
      <Order oid="O3" date="7/14/1999" amount="100" note="Wrap it blue white red">  
          <Urgency>Important</Urgency>  
      </Order>  
      <Order oid="O4" date="1/20/1996" amount="10000"/>  
   </Customer>  
</root>  
```  
  
 <span data-ttu-id="2a683-110">En este documento, **\<Customer>** es un nodo de elemento, **CID** es un nodo de atributo y **"importante"** es un nodo de texto.</span><span class="sxs-lookup"><span data-stu-id="2a683-110">In this document, **\<Customer>** is an element node, **cid** is an attribute node, and **"Important"** is a text node.</span></span>  
  
 <span data-ttu-id="2a683-111">XPath es un lenguaje de navegación de grafos que se usa para seleccionar un conjunto de nodos de un documento XML.</span><span class="sxs-lookup"><span data-stu-id="2a683-111">XPath is a graph navigation language used to select a set of nodes from an XML document.</span></span> <span data-ttu-id="2a683-112">Cada operador XPath selecciona un conjunto de nodos basándose en un conjunto de nodos seleccionado por un operador XPath anterior.</span><span class="sxs-lookup"><span data-stu-id="2a683-112">Each XPath operator selects a node-set based on a node-set selected by a previous XPath operator.</span></span> <span data-ttu-id="2a683-113">Por ejemplo, dado un conjunto de **\<Customer>** nodos, XPath puede seleccionar todos los **\<Order>** nodos con el valor de atributo de **fecha** **"7/14/1999"**.</span><span class="sxs-lookup"><span data-stu-id="2a683-113">For example, given a set of **\<Customer>** nodes, XPath can select all **\<Order>** nodes with the **date** attribute value of **"7/14/1999"**.</span></span> <span data-ttu-id="2a683-114">El conjunto de nodos resultante contiene todos los pedidos con la fecha de pedido 7/14/1999.</span><span class="sxs-lookup"><span data-stu-id="2a683-114">The resulting node-set contains all the orders with order date 7/14/1999.</span></span>  
  
 <span data-ttu-id="2a683-115">World Wide Web Consortium (W3C) define el lenguaje XPath como un lenguaje de navegación estándar.</span><span class="sxs-lookup"><span data-stu-id="2a683-115">The XPath language is defined by the World Wide Web Consortium (W3C) as a standard navigation language.</span></span> <span data-ttu-id="2a683-116">SQLXML 4,0 implementa un subconjunto de la especificación XPath de W3C, que se encuentra en http://www.w3.org/TR/1999/PR-xpath-19991008.html .</span><span class="sxs-lookup"><span data-stu-id="2a683-116">SQLXML 4.0 implements a subset of the W3C XPath specification, which is located at http://www.w3.org/TR/1999/PR-xpath-19991008.html.</span></span>  
  
 <span data-ttu-id="2a683-117">A continuación se muestran las diferencias que existen entre la implementación XPath de W3C y la implementación SQLXML 4.0.</span><span class="sxs-lookup"><span data-stu-id="2a683-117">The following are key differences between the W3C XPath implementation and the SQLXML 4.0 implementation.</span></span>  
  
-   <span data-ttu-id="2a683-118">**Consultas raíz**</span><span class="sxs-lookup"><span data-stu-id="2a683-118">**Root queries**</span></span>  
  
     <span data-ttu-id="2a683-119">SQLXML 4.0 no admite la consulta raíz (/).</span><span class="sxs-lookup"><span data-stu-id="2a683-119">SQLXML 4.0 does not support the root query (/).</span></span> <span data-ttu-id="2a683-120">Cada consulta XPath debe comenzar en un nivel superior **\<ElementType>** en el esquema.</span><span class="sxs-lookup"><span data-stu-id="2a683-120">Every XPath query must begin at a top-level **\<ElementType>** in the schema.</span></span>  
  
-   <span data-ttu-id="2a683-121">**Informes de errores**</span><span class="sxs-lookup"><span data-stu-id="2a683-121">**Reporting errors**</span></span>  
  
     <span data-ttu-id="2a683-122">La especificación XPath de W3C no define ninguna condición de error.</span><span class="sxs-lookup"><span data-stu-id="2a683-122">The W3C XPath specification defines no error conditions.</span></span> <span data-ttu-id="2a683-123">Las consultas XPath que no pueden seleccionar ningún nodo devuelven un conjunto de nodos vacío.</span><span class="sxs-lookup"><span data-stu-id="2a683-123">XPath queries that fail to select any nodes return an empty node-set.</span></span> <span data-ttu-id="2a683-124">En SQLXML 4.0, una consulta puede devolver muchos tipos de mensajes de error.</span><span class="sxs-lookup"><span data-stu-id="2a683-124">In SQLXML 4.0, a query can return many types of error messages.</span></span>  
  
-   <span data-ttu-id="2a683-125">**Orden del documento**</span><span class="sxs-lookup"><span data-stu-id="2a683-125">**Document order**</span></span>  
  
     <span data-ttu-id="2a683-126">En SQLXML 4.0, el orden del documento no siempre viene determinado.</span><span class="sxs-lookup"><span data-stu-id="2a683-126">In SQLXML 4.0, document order is not always determined.</span></span> <span data-ttu-id="2a683-127">Por lo tanto, los predicados numéricos y ejes que usan el orden del documento (como `following`) no se implementan.</span><span class="sxs-lookup"><span data-stu-id="2a683-127">Therefore, numeric predicates and axes that use document order (such as `following`) are not implemented.</span></span>  
  
     <span data-ttu-id="2a683-128">La falta de orden del documento también significa que el valor de cadena de un nodo solamente puede evaluarse cuando ese nodo se asigna a una única columna en una única fila.</span><span class="sxs-lookup"><span data-stu-id="2a683-128">The lack of document order also means that the string value of a node can be evaluated only when that node maps to a single column in a single row.</span></span> <span data-ttu-id="2a683-129">Un elemento con elementos secundarios o un nodo NMTOKENS o IDREFS no puede convertirse en una cadena.</span><span class="sxs-lookup"><span data-stu-id="2a683-129">An element with child elements or an IDREFS or NMTOKENS node cannot be converted to string.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2a683-130">En algunos casos, la anotación `key-fields` o las claves de la anotación `relationship` pueden dar lugar a un orden del documento determinista.</span><span class="sxs-lookup"><span data-stu-id="2a683-130">In some cases, the `key-fields` annotation or keys from the `relationship` annotation can result in a deterministic document order.</span></span> <span data-ttu-id="2a683-131">Sin embargo, este no es el uso principal de estas anotaciones para obtener más información, vea [identificar columnas de clave mediante SQL: key-fields &#40;sqlxml 4,0&#41;](../sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md) y [especificar relaciones mediante sql: relationship &#40;SQLXML 4,0&#41;](../sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md).</span><span class="sxs-lookup"><span data-stu-id="2a683-131">However, this is not the primary use of these annotations For more information, see [Identifying Key Columns Using sql:key-fields &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md) and [Specifying Relationships Using sql:relationship &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md).</span></span>  
  
-   <span data-ttu-id="2a683-132">**Tipos de datos**</span><span class="sxs-lookup"><span data-stu-id="2a683-132">**Data types**</span></span>  
  
     <span data-ttu-id="2a683-133">SQLXML 4.0 tiene limitaciones para implementar los tipos de datos XPath `string`, `number` y `boolean`.</span><span class="sxs-lookup"><span data-stu-id="2a683-133">SQLXML 4.0 has limitations in implementing the XPath `string`, `number`, and `boolean` data types.</span></span> <span data-ttu-id="2a683-134">Para obtener más información, vea [tipos de datos de XPath &#40;SQLXML 4,0&#41;](xpath-data-types-sqlxml-4-0.md).</span><span class="sxs-lookup"><span data-stu-id="2a683-134">For more information, see [XPath Data Types &#40;SQLXML 4.0&#41;](xpath-data-types-sqlxml-4-0.md).</span></span>  
  
-   <span data-ttu-id="2a683-135">**Consultas de varios productos**</span><span class="sxs-lookup"><span data-stu-id="2a683-135">**Cross-product queries**</span></span>  
  
     <span data-ttu-id="2a683-136">SQLXML 4.0 no admite consultas XPath de varios productos, como `Customers[Order/@OrderDate=Order/@ShipDate]`.</span><span class="sxs-lookup"><span data-stu-id="2a683-136">SQLXML 4.0 does not support cross-product XPath queries, such as `Customers[Order/@OrderDate=Order/@ShipDate]`.</span></span> <span data-ttu-id="2a683-137">Esta consulta selecciona todos los clientes (Customers) con algún pedido (Order) para el que la fecha de pedido (OrderDate) sea igual a la fecha de envío (ShipDate) de algún pedido (Order).</span><span class="sxs-lookup"><span data-stu-id="2a683-137">This query selects all Customers with any Order for which the OrderDate equals the ShipDate of any Order.</span></span>  
  
     <span data-ttu-id="2a683-138">Sin embargo, SQLXML 4.0 sí admite consultas como `Customer[Order[@OrderDate=@ShippedDate]]`, que selecciona los clientes (Customers) con algún pedido (Order) para el que la fecha de pedido (OrderDate) sea igual a la fecha de envío (ShipDate).</span><span class="sxs-lookup"><span data-stu-id="2a683-138">However, SQLXML 4.0 does support queries such as `Customer[Order[@OrderDate=@ShippedDate]]`, which selects Customers with any Order for which the OrderDate equals its ShipDate.</span></span>  
  
-   <span data-ttu-id="2a683-139">**Control de errores y seguridad**</span><span class="sxs-lookup"><span data-stu-id="2a683-139">**Error handling and security**</span></span>  
  
     <span data-ttu-id="2a683-140">En función del esquema y de la expresión de consulta XPath que se utilicen, los errores de [!INCLUDE[tsql](../../includes/tsql-md.md)] pueden exponerse a los usuarios en determinadas condiciones.</span><span class="sxs-lookup"><span data-stu-id="2a683-140">Depending on the schema and XPath query expression that are used, [!INCLUDE[tsql](../../includes/tsql-md.md)] errors could be exposed to users under certain conditions.</span></span>  
  
 <span data-ttu-id="2a683-141">En las tablas de las siguientes secciones se proporcionan detalles sobre las diferencias que existen entre la implementación de consultas XPath en SQLXML 4.0 y la especificación W3C en lo que respecta estas áreas.</span><span class="sxs-lookup"><span data-stu-id="2a683-141">The tables in the following sections provide details about how the implementation of XPath queries in SQLXML 4.0 differs from the W3C specification in these areas.</span></span>  
  
## <a name="supported-functionality"></a><span data-ttu-id="2a683-142">Funcionalidad compatible</span><span class="sxs-lookup"><span data-stu-id="2a683-142">Supported Functionality</span></span>  
 <span data-ttu-id="2a683-143">En la siguiente tabla se muestran las características del lenguaje XPath que se implementan en SQLXML 4.0.</span><span class="sxs-lookup"><span data-stu-id="2a683-143">The following table shows the features of the XPath language that are implemented in SQLXML 4.0.</span></span>  
  
|<span data-ttu-id="2a683-144">Característica</span><span class="sxs-lookup"><span data-stu-id="2a683-144">Feature</span></span>|<span data-ttu-id="2a683-145">Elemento</span><span class="sxs-lookup"><span data-stu-id="2a683-145">Item</span></span>|<span data-ttu-id="2a683-146">Vínculo a consultas de ejemplo</span><span class="sxs-lookup"><span data-stu-id="2a683-146">Link to sample queries</span></span>|  
|-------------|----------|----------------------------|  
|<span data-ttu-id="2a683-147">Ejes</span><span class="sxs-lookup"><span data-stu-id="2a683-147">Axes</span></span>|<span data-ttu-id="2a683-148">Ejes `attribute`, `child`, `parent` y `self`.</span><span class="sxs-lookup"><span data-stu-id="2a683-148">`attribute`, `child`, `parent`, and `self` axes</span></span>|[<span data-ttu-id="2a683-149">Especificar ejes en consultas XPath &#40;SQLXML 4,0&#41;</span><span class="sxs-lookup"><span data-stu-id="2a683-149">Specifying Axes in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-axes-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="2a683-150">Predicados con valores booleanos que incluyen predicados sucesivos y anidados</span><span class="sxs-lookup"><span data-stu-id="2a683-150">Boolean-valued predicates including successive and nested predicates</span></span>||[<span data-ttu-id="2a683-151">Especificar operadores aritméticos en consultas XPath &#40;SQLXML 4,0&#41;</span><span class="sxs-lookup"><span data-stu-id="2a683-151">Specifying Arithmetic Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="2a683-152">Todos los operadores relacionales</span><span class="sxs-lookup"><span data-stu-id="2a683-152">All relational operators</span></span>|<span data-ttu-id="2a683-153">=,! =, <, \<=, > , >=</span><span class="sxs-lookup"><span data-stu-id="2a683-153">=, !=, <, \<=, >, >=</span></span>|[<span data-ttu-id="2a683-154">Especificar operadores relacionales en consultas XPath &#40;SQLXML 4,0&#41;</span><span class="sxs-lookup"><span data-stu-id="2a683-154">Specifying Relational Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-relational-operators-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="2a683-155">Operadores aritméticos</span><span class="sxs-lookup"><span data-stu-id="2a683-155">Arithmetic operators</span></span>|<span data-ttu-id="2a683-156">+, -, \*, div</span><span class="sxs-lookup"><span data-stu-id="2a683-156">+, -, \*, div</span></span>|[<span data-ttu-id="2a683-157">Especificar operadores aritméticos en consultas XPath &#40;SQLXML 4,0&#41;</span><span class="sxs-lookup"><span data-stu-id="2a683-157">Specifying Arithmetic Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="2a683-158">Funciones de conversión explícita</span><span class="sxs-lookup"><span data-stu-id="2a683-158">Explicit conversion functions</span></span>|<span data-ttu-id="2a683-159">`number()`, `string()`, `Boolean()`</span><span class="sxs-lookup"><span data-stu-id="2a683-159">`number()`, `string()`, `Boolean()`</span></span>|[<span data-ttu-id="2a683-160">Especificar funciones de conversión explícitas en consultas XPath &#40;SQLXML 4,0&#41;</span><span class="sxs-lookup"><span data-stu-id="2a683-160">Specifying Explicit Conversion Functions in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="2a683-161">operadores booleanos</span><span class="sxs-lookup"><span data-stu-id="2a683-161">Boolean operators</span></span>|<span data-ttu-id="2a683-162">AND, OR</span><span class="sxs-lookup"><span data-stu-id="2a683-162">AND, OR</span></span>|[<span data-ttu-id="2a683-163">Especificar operadores booleanos en consultas XPath &#40;SQLXML 4,0&#41;</span><span class="sxs-lookup"><span data-stu-id="2a683-163">Specifying Boolean Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-boolean-operators-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="2a683-164">funciones booleanas</span><span class="sxs-lookup"><span data-stu-id="2a683-164">Boolean functions</span></span>|<span data-ttu-id="2a683-165">`true()`, `false()`, `not()`</span><span class="sxs-lookup"><span data-stu-id="2a683-165">`true()`, `false()`, `not()`</span></span>|[<span data-ttu-id="2a683-166">Especificar funciones booleanas en consultas XPath &#40;SQLXML 4,0&#41;</span><span class="sxs-lookup"><span data-stu-id="2a683-166">Specifying Boolean Functions in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-boolean-functions-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="2a683-167">variables de XPath</span><span class="sxs-lookup"><span data-stu-id="2a683-167">XPath variables</span></span>||[<span data-ttu-id="2a683-168">Especificar variables XPath en consultas XPath &#40;SQLXML 4,0&#41;</span><span class="sxs-lookup"><span data-stu-id="2a683-168">Specifying XPath Variables in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-xpath-variables-in-xpath-queries-sqlxml-4-0.md)|  
  
## <a name="unsupported-functionality"></a><span data-ttu-id="2a683-169">Funcionalidad incompatible</span><span class="sxs-lookup"><span data-stu-id="2a683-169">Unsupported Functionality</span></span>  
 <span data-ttu-id="2a683-170">En la siguiente tabla se muestran las características del lenguaje XPath que no se implementan en SQLXML 4.0.</span><span class="sxs-lookup"><span data-stu-id="2a683-170">The following table shows the features of the XPath language that are not implemented in SQLXML 4.0.</span></span>  
  
|<span data-ttu-id="2a683-171">Característica</span><span class="sxs-lookup"><span data-stu-id="2a683-171">Feature</span></span>|<span data-ttu-id="2a683-172">Elemento</span><span class="sxs-lookup"><span data-stu-id="2a683-172">Item</span></span>|  
|-------------|----------|  
|<span data-ttu-id="2a683-173">Ejes</span><span class="sxs-lookup"><span data-stu-id="2a683-173">Axes</span></span>|<span data-ttu-id="2a683-174">`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`</span><span class="sxs-lookup"><span data-stu-id="2a683-174">`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`</span></span>|  
|<span data-ttu-id="2a683-175">Predicados con valores numéricos</span><span class="sxs-lookup"><span data-stu-id="2a683-175">Numeric-valued predicates</span></span>||  
|<span data-ttu-id="2a683-176">Operadores aritméticos</span><span class="sxs-lookup"><span data-stu-id="2a683-176">Arithmetic operators</span></span>|<span data-ttu-id="2a683-177">mod</span><span class="sxs-lookup"><span data-stu-id="2a683-177">mod</span></span>|  
|<span data-ttu-id="2a683-178">Funciones de nodo</span><span class="sxs-lookup"><span data-stu-id="2a683-178">Node functions</span></span>|<span data-ttu-id="2a683-179">`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`</span><span class="sxs-lookup"><span data-stu-id="2a683-179">`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`</span></span>|  
|<span data-ttu-id="2a683-180">Funciones de cadena</span><span class="sxs-lookup"><span data-stu-id="2a683-180">String functions</span></span>|<span data-ttu-id="2a683-181">`string()`, `concat()`, `starts-with()`, `contains()`, `substring-before()`, `substring-after()`, `substring()`, `string-length()`, `normalize()`, `translate()`</span><span class="sxs-lookup"><span data-stu-id="2a683-181">`string()`, `concat()`, `starts-with()`, `contains()`, `substring-before()`, `substring-after()`, `substring()`, `string-length()`, `normalize()`, `translate()`</span></span>|  
|<span data-ttu-id="2a683-182">funciones booleanas</span><span class="sxs-lookup"><span data-stu-id="2a683-182">Boolean functions</span></span>|`lang()`|  
|<span data-ttu-id="2a683-183">Funciones numéricas</span><span class="sxs-lookup"><span data-stu-id="2a683-183">Numeric functions</span></span>|<span data-ttu-id="2a683-184">`sum()`, `floor()`, `ceiling()`, `round()`</span><span class="sxs-lookup"><span data-stu-id="2a683-184">`sum()`, `floor()`, `ceiling()`, `round()`</span></span>|  
|<span data-ttu-id="2a683-185">Operador de unión</span><span class="sxs-lookup"><span data-stu-id="2a683-185">Union operator</span></span>|<span data-ttu-id="2a683-186">&#124;</span><span class="sxs-lookup"><span data-stu-id="2a683-186">&#124;</span></span>|  
  
 <span data-ttu-id="2a683-187">Cuando especifique consultas XPath en una plantilla, tenga en cuenta el siguiente comportamiento:</span><span class="sxs-lookup"><span data-stu-id="2a683-187">When you specify XPath queries in a template, note the following behavior:</span></span>  
  
-   <span data-ttu-id="2a683-188">XPath puede contener caracteres como < o & que tienen significados especiales en XML (y la plantilla es un documento XML).</span><span class="sxs-lookup"><span data-stu-id="2a683-188">XPath can contain characters such as < or & that have special meanings in XML (and template is an XML document).</span></span> <span data-ttu-id="2a683-189">Debe escapar estos caracteres mediante la codificación & XML o especificar el XPath en la dirección URL.</span><span class="sxs-lookup"><span data-stu-id="2a683-189">You must escape these characters using XML &-encoding, or specify the XPath in the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a683-190">Consulte también</span><span class="sxs-lookup"><span data-stu-id="2a683-190">See Also</span></span>  
 [<span data-ttu-id="2a683-191">Utilizar consultas XPath en SQLXML 4.0</span><span class="sxs-lookup"><span data-stu-id="2a683-191">Using XPath Queries in SQLXML 4.0</span></span>](using-xpath-queries-in-sqlxml-4-0.md)  
  
  