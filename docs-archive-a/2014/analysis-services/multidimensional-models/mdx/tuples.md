---
title: Tuplas | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 35b629ae-b1ef-44b1-b556-96956aeb56e7
author: minewiskan
ms.author: owend
ms.openlocfilehash: c39d03d60cb66f3b2e26b2e660bd85f4e5e9d4ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748328"
---
# <a name="tuples"></a>Tuplas
  Una tupla identifica de forma inequívoca un segmento de datos de un cubo. Una combinación de miembros de dimensión forma la tupla, siempre que no haya dos o más miembros que pertenecen a la misma jerarquía.  
  
## <a name="implicit-or-default-attribute-members-in-a-tuple"></a>Miembros de atributo implícitos o predeterminados en una tupla  
 Al definir una tupla en una consulta o expresión MDX, no es necesario incluir explícitamente el miembro de atributo de cada jerarquía de atributo. Si no se incluye de manera explicita un miembro de una jerarquía de atributo en una consulta o expresión, el miembro predeterminado de esa jerarquía de atributo es el miembro de atributo implícitamente incluido en la tupla. A menos que se lo defina explícitamente de otra manera en un cubo, el miembro predeterminado de cada jerarquía de atributo es el miembro (All), si existe. Si no existe un miembro (All) dentro de una jerarquía de atributo, el miembro predeterminado es un miembro del nivel superior de la jerarquía de atributo. La medida predeterminada es la primera medida especificada en el cubo, a menos que se defina explícitamente una medida predeterminada. Para más información, vea [Definir un miembro predeterminado](../attribute-properties-define-a-default-member.md) y [DefaultMember &#40;MDX&#41;](/sql/mdx/defaultmember-mdx).  
  
 Por ejemplo, la siguiente tupla identifica a una celda única de la base de datos Adventure Works al definir explícitamente un solo miembro de la dimensión de medidas.  
  
```  
(Measures.[Reseller Sales Amount])  
```  
  
 El ejemplo anterior identifica de forma exclusiva la celda que consta del miembro Reseller Sales Amount de la dimensión de medidas y el miembro predeterminado de cada jerarquía de atributo del cubo. El miembro predeterminado es el miembro (All) de cada jerarquía de atributo que no sea la jerarquía de atributo Destination Currency. El miembro predeterminado de la jerarquía Destination Currency es US Dollar (este miembro predeterminado se define en el script MDX del cubo Adventure Works).  
  
 La consulta siguiente devuelve el valor de la celda a la que se hace referencia en la tupla especificada en el ejemplo anterior ($80.450,596,98).  
  
```  
SELECT   
Measures.[Reseller Sales Amount] ON COLUMNS   
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  Al especificar un eje para un conjunto (en este caso compuesto por una sola tupla) de una consulta, debe comenzar por especificar un conjunto para el eje de columna antes de especificar un conjunto para el eje de fila. También se puede hacer referencia al eje de columna como *eje(0)* o sencillamente *0*. Para más información sobre las consultas MDX, vea [Consulta de MDX básica &#40;MDX&#41;](mdx-query-the-basic-query.md).  
  
### <a name="tuples-as-values-or-member-references"></a>Tuplas como valores o referencias de miembro  
 Puede utilizar una tupla de una consulta para devolver el valor de la celda a la que se hace referencia en la tupla, como en el ejemplo anterior. De lo contrario, puede utilizar una tupla en una expresión para hacer referencia de forma explícita a los miembros especificados en la tupla. La consulta o la expresión pueden utilizar funciones que devuelvan o consuman tuplas. Una tupla puede utilizarse para hacer referencia al valor de la celda que especifica la tupla o para especificar una combinación de miembros cuando se utilicen en una función.  
  
### <a name="tuple-dimensionality"></a>Dimensionalidad de tuplas  
 La *dimensionalidad* de una tupla hace referencia a la secuencia o el orden de los miembros de la tupla. Debido a que los miembros implícitos siempre aparecen en el mismo orden, se piensa en la dimensionalidad generalmente en relación con los miembros explícitamente definidos de la tupla. El orden de los miembros de la tupla es importante al definir un conjunto de tuplas. El ejemplo siguiente incluye dos miembros de una tupla en el eje de columna.  
  
```  
SELECT   
([Measures].[Reseller Sales Amount],[Date].[Calendar Year].[CY 2004]) ON COLUMNS   
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  Al especificar explícitamente un miembro de una tupla de más de una dimensión, debe incluir toda la tupla entre paréntesis. Cuando solo se especifica un miembro de una tupla, los paréntesis son opcionales.  
  
 La tupla de la consulta del ejemplo anterior especifica la devolución de la celda del cubo en la intersección de la medida Reseller Sales Amount de la dimensión de medidas y el miembro CY 2004 de la jerarquía de atributo Calendar Year de la dimensión Date.  
  
> [!NOTE]  
>  Se puede hacer referencia a un miembro de atributo por su nombre de miembro o su clave de miembro. En el ejemplo anterior, se podía reemplazar la referencia a [CY 2004] con &[2004].  
  
## <a name="see-also"></a>Consulte también  
 [Conceptos clave de &#40;MDX Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md)   
 [Espacio de cubo](cube-space.md)   
 [Autoexists](autoexists.md)   
 [Trabajar con miembros, tuplas y conjuntos &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md)  
  
  
