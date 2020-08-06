---
title: Propiedades de miembro definidas por el usuario (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- custom member properties [MDX]
ms.assetid: b64cc581-e784-42c4-bec8-932abd687423
author: minewiskan
ms.author: owend
ms.openlocfilehash: 75e5df5a0677ee205b5517f4c7ca89a390426971
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745436"
---
# <a name="user-defined-member-properties-mdx"></a>Propiedades de miembro definidas por el usuario (MDX)
  Las propiedades de miembro definidas por el usuario se pueden agregar a un nivel con nombre específico de una dimensión como relaciones de atributo. Las propiedades de miembro definidas por el usuario no se pueden agregar al nivel `(All)` de una jerarquía ni a la propia jerarquía.  
  
## <a name="creating-user-defined-member-properties"></a>Crear propiedades de miembro definidas por el usuario  
 Las propiedades de miembro definidas por el usuario pueden agregarse a las dimensiones basadas en servidor o a los cubos mediante la interfaz de usuario o mediante programación:  
  
-   Para agregar propiedades de miembro definidas por el usuario en la interfaz de usuario, se usa el Diseñador de dimensiones de [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Para obtener más información, vea [Definir relaciones de atributo](../attribute-relationships-define.md).  
  
-   Para agregar propiedades de miembro definidas por el usuario mediante programación, la aplicación puede utilizar objetos Analysis Manager Objects (AMO) o una combinación de XML for Analysis (XMLA) y Analysis Services Scripting Language (ASSL). Para obtener más información, vea [Relaciones de atributo](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
## <a name="retrieving-user-defined-member-properties"></a>Recuperar propiedades de miembro definidas por el usuario  
 Puede recuperar las propiedades de miembro definidas por el usuario mediante la `PROPERTIES` palabra clave o la función [Properties](/sql/mdx/properties-mdx) .  
  
### <a name="using-the-properties-keyword-to-retrieve-user-defined-member-properties"></a>Usar la palabra clave PROPERTIES para recuperar propiedades de miembro definidas por el usuario  
 La sintaxis para recuperar propiedades de miembro definidas por el usuario es similar a la utilizada para recuperar propiedades de miembro de nivel intrínsecas, como se muestra en el siguiente ejemplo de sintaxis:  
  
 `DIMENSION PROPERTIES [Dimension.]Level.<Custom_Member_Property>`  
  
 La palabra clave `PROPERTIES` aparece después de la expresión de conjuntos de la especificación del eje. Por ejemplo, en la siguiente consulta MDX, la palabra clave `PROPERTIES` recupera las propiedades de miembro definidas por el usuario `List Price` y `Dealer Price` y aparece después de la expresión de conjunto que identifica los productos vendidos en el mes de enero:  
  
```  
SELECT   
   CROSSJOIN([Ship Date].[Calendar].[Calendar Year].Members,   
             [Measures].[Sales Amount]) ON COLUMNS,  
   NON EMPTY Product.Product.MEMBERS  
   DIMENSION PROPERTIES   
              Product.Product.[List Price],  
              Product.Product.[Dealer Price]  ON ROWS  
FROM [Adventure Works]  
WHERE ([Date].[Month of Year].[January])   
```  
  
### <a name="using-the-properties-function-to-retrieve-user-defined-member-properties"></a>Usar la función Properties para recuperar propiedades de miembro definidas por el usuario  
 También puede obtener acceso a las propiedades de miembro personalizado con la función `Properties`. Por ejemplo, la siguiente consulta MDX utiliza la palabra clave `WITH` para crear un miembro calculado que contiene la propiedad de miembro `List Price`:  
  
```  
WITH   
   MEMBER [Measures].[Product List Price] AS  
   [Product].[Product].CurrentMember.Properties("List Price")  
SELECT   
   [Measures].[Product List Price] on COLUMNS,  
   [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
```  
  
 Para obtener más información sobre la creación de miembros calculados, vea [Generar miembros calculados en MDX &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md).  
  
## <a name="see-also"></a>Consulte también  
 [Usar las propiedades de miembro &#40;&#41;MDX](mdx-member-properties.md)   
 [Properties &#40;MDX&#41;](/sql/mdx/properties-mdx)  
  
  
