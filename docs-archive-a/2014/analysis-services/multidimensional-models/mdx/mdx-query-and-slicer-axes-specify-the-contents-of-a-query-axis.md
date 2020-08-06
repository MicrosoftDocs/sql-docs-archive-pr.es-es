---
title: Especificar el contenido de un eje de consulta (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cellsets [MDX]
- query axis [MDX]
ms.assetid: c745ade0-738e-4a98-a3f0-3eabfd3eeba2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 28fd867b8f8caaf74e4dd704753c354368da2e89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87747203"
---
# <a name="specifying-the-contents-of-a-query-axis-mdx"></a>Especificar el contenido de un eje de consulta (MDX)
  Los ejes de consulta especifican los límites de un conjunto de celdas devuelto por una instrucción SELECT de Expresiones multidimensionales (MDX). Al especificar los límites de un conjunto de celdas puede restringir los datos devueltos que son visibles para el cliente.  
  
 Para especificar ejes de consulta, utilice `<SELECT query axis clause>` para asignar un conjunto a un eje de consulta determinado. Cada valor `<SELECT query axis clause>` define un eje de consulta. El número de ejes de un conjunto de datos es igual al número de valores `<SELECT query axis clause>` de la instrucción SELECT.  
  
## <a name="query-axis-syntax"></a>Sintaxis del eje de consulta  
 A continuación se muestra la sintaxis para `<SELECT query axis clause>`:  
  
```  
  
<SELECT query axis clause> ::=  
   [ NON EMPTY ] Set_Expression [ <SELECT dimension property list clause> ] [<HAVING clause>]  
   ON {  
      Integer_Expression |   
      AXIS( Integer_Expression ) |   
      {COLUMNS | ROWS | PAGES | SECTIONS | CHAPTERS}     
      }  
  
```  
  
 Cada eje de consulta tiene un número: cero (0) para el eje X, 1 para el eje Y, 2 para el eje Z, etc. En la sintaxis de `<SELECT query axis clause>`, el valor `Integer_Expression` especifica el número de eje. Una consulta de MDX puede admitir hasta 128 ejes especificados, pero muy pocas consultas MDX utilizarán más de cinco ejes. En los primeros cinco ejes, pueden utilizarse los alias COLUMNS, ROWS, PAGES, SECTIONS y CHAPTERS en su lugar.  
  
 Una consulta de MDX no puede ignorar los ejes de consulta. Es decir, una consulta que incluye uno o más ejes de consulta no debe excluir los ejes con números más bajos o intermedios. Por ejemplo, una consulta no puede tener un eje ROWS sin un eje COLUMNS, o los ejes COLUMNS y PAGES sin un eje ROWS.  
  
 Sin embargo, puede especificar una cláusula SELECT sin ejes (es decir, una cláusula SELECT vacía). En este caso, todas las dimensiones son dimensiones de segmentador y la consulta de MDX selecciona una celda.  
  
 En la sintaxis del eje de consulta mostrado más arriba, cada valor `Set_Expression` especifica el conjunto que define el contenido del eje de consulta. Para obtener más información sobre los conjuntos, vea [Trabajar con miembros, tuplas y conjuntos &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md).  
  
## <a name="examples"></a>Ejemplos  
 La instrucción SELECT simple siguiente devuelve la medida Internet Sales Amount en el eje de columnas y utiliza funciones MDX MEMBERS para devolver todos los miembros de la jerarquía Calendar de la dimensión Date en el eje de filas:  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
{[Date].[Calendar].MEMBERS} ON ROWS  
FROM [Adventure Works]  
  
```  
  
 Las dos consultas de siguientes devuelven exactamente los mismos resultados pero muestran el uso de números de eje en lugar de alias:  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON 0,  
{[Date].[Calendar].MEMBERS} ON 1  
FROM [Adventure Works]  
  
SELECT {[Measures].[Internet Sales Amount]} ON AXIS(0),  
{[Date].[Calendar].MEMBERS} ON AXIS(1)  
FROM [Adventure Works]  
  
```  
  
 La palabra clave NON EMPTY, utilizada antes de la definición específica, es una forma sencilla de quitar todas las tuplas vacías de un eje. Por ejemplo, en los ejemplos que hemos visto hasta ahora no hay datos en el cubo de agosto de 2004 en adelante. Para quitar todas las filas del conjunto que no tienen ningún dato en ninguna columna, agregue simplemente NON EMPTY antes del conjunto en la definición del eje de filas como sigue:  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
NON EMPTY  
{[Date].[Calendar].MEMBERS} ON ROWS  
FROM [Adventure Works]  
  
```  
  
 NON EMPTY se puede utilizar en todos los ejes de una consulta. Compare los resultados de las dos consultas siguientes; la primera no utiliza NON EMPTY y la segunda lo usa en ambos ejes:  
  
```  
SELECT {[Measures].[Internet Sales Amount]}   
* [Promotion].[Promotion].[Promotion].MEMBERS  
ON COLUMNS,  
{[Date].[Calendar].[Calendar Year].MEMBERS} ON ROWS  
FROM [Adventure Works]  
WHERE([Product].[Subcategory].&[19])  
  
SELECT NON EMPTY {[Measures].[Internet Sales Amount]}   
* [Promotion].[Promotion].[Promotion].MEMBERS  
ON COLUMNS,  
NON EMPTY  
{[Date].[Calendar].[Calendar Year].MEMBERS} ON ROWS  
FROM [Adventure Works]  
WHERE([Product].[Subcategory].&[19])  
  
```  
  
 La cláusula HAVING se puede usar para filtrar el contenido de un eje basándose en criterios concretos; es menos flexible que otros métodos que pueden lograr los mismos resultados, como la función FILTER, pero es más sencillo utilizar. A continuación se muestra un ejemplo que solo devuelve las fechas donde Internet Sales Amount es mayor que $15.000:  
  
```  
SELECT {[Measures].[Internet Sales Amount]}   
ON COLUMNS,  
NON EMPTY  
{[Date].[Calendar].[Date].MEMBERS}   
HAVING [Measures].[Internet Sales Amount]>15000  
ON ROWS  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Consulte también  
 [Especificar el contenido de un eje de división en sectores &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)  
  
  
