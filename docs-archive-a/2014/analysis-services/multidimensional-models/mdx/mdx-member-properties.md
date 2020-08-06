---
title: Usar las propiedades de miembro (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DIMENSION PROPERTIES keyword
- Properties function
- member properties [MDX]
- members [MDX], properties
ms.assetid: 26b5ad08-3799-4a5e-89f3-dca25e637d45
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5b7fdf989fc23ea70be7d7863f5d4c6ac0b61d8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745435"
---
# <a name="using-member-properties-mdx"></a>Usar las propiedades de miembro (MDX)
  Las propiedades de miembro cubren la información básica de todos los miembros de cada tupla. Esta información básica incluye el nombre del miembro, el nivel primario, el número de secundarios, etc. Las propiedades de miembro están disponibles para todos los miembros de un determinado nivel. En términos de organización, las propiedades de miembro se tratan como datos organizados dimensionalmente, almacenados en una sola dimensión.  
  
> [!NOTE]  
>  En [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], las propiedades de miembro se conocen como relaciones de atributo. Para obtener más información, vea [Relaciones de atributo](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
 Las propiedades de miembro pueden ser *intrínsecas* o *personalizadas*:  
  
 Propiedades de miembro intrínsecas  
 Todos los miembros admiten propiedades de miembro intrínsecas, como el valor con formato de un miembro, mientras que las dimensiones y los niveles proporcionan propiedades de miembro intrínsecas adicionales de nivel y dimensión, como el Id. de un miembro.  
  
 Para obtener más información, vea [Propiedades de miembro intrínsecas &#40;MDX&#41;](mdx-member-properties-intrinsic-member-properties.md).  
  
 Propiedades de miembro definidas por el usuario  
 Los miembros suelen tener propiedades adicionales asociadas. Por ejemplo, el nivel Products puede ofrecer las propiedades SKU, SRP, Weight y Volume para cada producto. Estas propiedades no son miembros, pero contienen información adicional sobre los miembros del nivel Products.  
  
 Para obtener más información, vea [Propiedades de miembro definidas por el usuario &#40;MDX&#41;](mdx-member-properties-user-defined-member-properties.md).  
  
 Las propiedades de miembro intrínsecas y definidas por el usuario se pueden recuperar mediante el uso de la `PROPERTIES` palabra clave o la función [Properties](/sql/mdx/properties-mdx) .  
  
## <a name="using-the-properties-keyword"></a>Usar la palabra clave PROPERTIES  
 La palabra clave `PROPERTIES` especifica las propiedades de miembro que deben utilizarse para una dimensión de eje determinada. La `PROPERTIES` palabra clave está incluida en la `<axis specification>` cláusula de la instrucción MDX [Select](/sql/mdx/mdx-data-manipulation-select) :  
  
```  
SELECT [<axis_specification>  
       [, <axis_specification>...]]  
  FROM [<cube_specification>]  
[WHERE [<slicer_specification>]]  
```  
  
 La cláusula `<axis_specification>` incluye una cláusula `<dim_props>` opcional, como se ilustra en la siguiente sintaxis:  
  
```  
<axis_specification> ::= <set> [<dim_props>] ON <axis_name>  
```  
  
> [!NOTE]  
>  Para obtener más información sobre los valores `<set>` y `<axis_name>`, vea [Especificar el contenido de un eje de consulta &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).  
  
 La cláusula `<dim_props>` permite realizar consultas sobre propiedades de dimensiones, niveles y miembros mediante la palabra clave `PROPERTIES`. En la siguiente sintaxis se muestra el formato de la cláusula `<dim_props>` :  
  
```  
<dim_props> ::= [DIMENSION] PROPERTIES <property> [,<property>...]  
```  
  
 El análisis detallado de la sintaxis `<property>` varía según la propiedad sobre la que se efectúe la consulta:  
  
-   Las propiedades de miembro intrínsecas contextuales deben ir precedidas del nombre de la dimensión o el nivel. Sin embargo, el nombre de las propiedades de miembro intrínsecas no contextuales no puede completarse con el de la dimensión o el nivel. Para obtener más información sobre cómo usar la `PROPERTIES` palabra clave con las propiedades de miembro intrínsecas, vea [propiedades de miembro intrínsecas &#40;&#41;MDX ](mdx-member-properties-intrinsic-member-properties.md).  
  
-   Las propiedades de miembro definidas por el usuario deben ir precedidas por el nombre del nivel en el que residen. Para obtener más información sobre cómo usar la `PROPERTIES` palabra clave con las propiedades de miembro definidas por el usuario, vea [propiedades de miembro definidas por el usuario &#40;MDX&#41;](mdx-member-properties-user-defined-member-properties.md).  
  
## <a name="see-also"></a>Consulte también  
 [Crear y usar los valores de propiedad &#40;MDX&#41;](../../creating-and-using-property-values-mdx.md)  
  
  
