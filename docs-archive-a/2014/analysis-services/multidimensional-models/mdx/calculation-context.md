---
title: Contexto de cálculo | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: aec8aa98-b77d-4f8f-9684-2618b1d8e970
author: minewiskan
ms.author: owend
ms.openlocfilehash: e6d14df51c6ec37fb96520af7acf207227ae4ea5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746564"
---
# <a name="calculation-context"></a>Contexto de cálculo
  El contexto de cálculo es el subespacio conocido del cubo donde se evalúa una expresión y todas las coordenadas se conocen explícitamente o se pueden derivar de la expresión.  
  
## <a name="determining-the-calculation-context"></a>Determinar el contexto del cálculo  
 Cada conjunto, miembro, tupla o función numérica se ejecuta en el contexto de toda la expresión o instrucción MDX. Cuando se pasa un argumento, como una tupla, a una función, solo se proporcionan explícitamente algunas coordenadas del espacio de cubo. Las otras coordenadas se obtienen según el contexto de cálculo actual.  
  
 El contexto de cálculo de las coordenadas de celda y los miembros de atributo que no se han especificado se determina en el siguiente orden:  
  
1.  La cláusula FROM (si corresponde): esta cláusula puede especificar un cubo entero o un subcubo en forma de una instrucción SELECT.  
  
2.  La cláusula WHERE (si corresponde): esta cláusula, que también se conoce como el *eje segmentador*, en la que se especifica un conjunto, tupla o miembro que limita el número de miembros devuelto en el eje de columna y de fila por una consulta. Conceptualmente, el miembro predeterminado de cada jerarquía de atributo que no se especifica explícitamente en el eje de columna o de fila es parte del eje segmentador.  
  
    > [!NOTE]  
    >  Cuando se especifican las coordenadas de celda de un atributo en particular en el eje segmentador y en otro eje, las coordenadas especificadas en la función pueden tener prioridad al determinar los miembros del conjunto en el eje. Las funciones [Filter (MDX)](/sql/mdx/filter-mdx) y [Order (MDX)](/sql/mdx/order-mdx) son ejemplos de esas funciones. Se puede filtrar u ordenar un resultado por miembros de atributo que se excluyen del contexto de cálculo con la cláusula WHERE o mediante una instrucción SELECT de la cláusula FROM.  
  
3.  Los conjuntos con nombre y los miembros calculados definidos en la consulta o expresión.  
  
4.  Las tuplas y conjuntos especificados en los ejes de columna y fila, mediante el miembro predeterminado de los atributos que no aparecen en el eje de fila, de columna o segmentador.  
  
5.  Las celdas de cubo o subcubo en cada eje, lo que elimina las tuplas vacías del eje y aplica la cláusula HAVING.  
  
6.  Para más información, vea [Establecer el contexto de cubo en una consulta &#40;MDX&#41;](establishing-cube-context-in-a-query-mdx.md).  
  
 En la siguiente consulta, el contexto de cálculo del eje de fila está limitado por el miembro de atributo Country y el miembro de atributo Calendar Year especificados en la cláusula WHERE.  
  
```  
SELECT Customer.City.City.Members ON 0  
FROM [Adventure Works]  
WHERE (Customer.Country.France, [Date].[Calendar].[Calendar Year].[CY 2004],  
   Measures.[Internet Sales Amount])  
```  
  
 Sin embargo, si modifica esta consulta al especificar la función `FILTER` en el eje de fila y utiliza un miembro de jerarquía de atributo Calendar Year en la función `FILTER`, entonces se puede modificar el miembro de atributo de la jerarquía de atributo Calendar Year que se utiliza para proporcionar el contexto de cálculo para los miembros del conjunto en el eje de columna.  
  
```  
SELECT FILTER  
   (  
      Customer.City.City.Members,   
         ([Date].[Calendar].[Calendar Year].[CY 2003],  
            Measures.[Internet Order Quantity]) > 75   
   ) ON 0  
FROM [Adventure Works]  
WHERE (Customer.Country.France,  
   [Date].[Calendar].[Calendar Year].[CY 2004],  
   Measures.[Internet Sales Amount])  
```  
  
 En la consulta anterior, el contexto de cálculo para las celdas de las tuplas que aparecen en el eje de columna está filtrado por el miembro CY 2003 de la jerarquía de atributo Calendar Year, a pesar de que el contexto de cálculo nominal para la jerarquía de atributo Calendar Year es CY 2004. Además, está filtrado por la medida Internet Order Quantity. Sin embargo, una vez que se establecen los miembros del conjunto en el eje de columna, el contexto de cálculo de los valores para los miembros que aparecen en el eje se determina nuevamente mediante la cláusula WHERE.  
  
> [!IMPORTANT]  
>  Para aumentar el rendimiento de la consulta, debe eliminar los miembros y las tuplas lo más pronto posible en el proceso de resolución. De esta manera, los cálculos de tiempo de consulta complejos en el conjunto final de miembros operan en la menor cantidad de celdas posible.  
  
## <a name="see-also"></a>Consulte también  
 [Establecer el contexto de cubo en una consulta &#40;MDX&#41;](establishing-cube-context-in-a-query-mdx.md)   
 [Aspectos básicos de las consultas MDX &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)   
 [Conceptos clave de MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md)  
  
  
