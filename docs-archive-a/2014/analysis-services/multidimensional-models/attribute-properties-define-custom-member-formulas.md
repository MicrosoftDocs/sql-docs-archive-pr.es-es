---
title: Definir fórmulas de miembro personalizado | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- members [Analysis Services], custom
- custom rollup formulas [Analysis Services]
- MDX [Analysis Services], custom rollup formulas
- custom member formulas [Analysis Services]
ms.assetid: 258304e2-d900-4013-97e3-871f51dfdce2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 51649bea0c4134971b342b779c778b857343e62b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750341"
---
# <a name="define-custom-member-formulas"></a>Definir fórmulas de miembro personalizado
  Puede definir una expresión MDX (Expresiones multidimensionales), denominada fórmula de miembro personalizado, para suministrar los valores de los miembros de determinado atributo. Una columna de una tabla de una vista del origen de datos proporciona, para cada miembro de un atributo, la expresión utilizada para suministrar el valor para dicho miembro.  
  
 Las fórmulas de miembro personalizado determinan los valores de las celdas que se asocian a los miembros y reemplazan las funciones de agregado de medidas. Las fórmulas de miembro personalizado se escriben en MDX. Cada fórmula de miembro personalizado se aplica a un solo miembro. Las fórmulas de miembro personalizado se almacenan en la tabla de dimensión o en otra tabla que tenga una relación de clave externa con la tabla de dimensión.  
  
 La propiedad `CustomRollupColumn` de un atributo especifica la columna que contiene las fórmulas de miembro personalizado para miembros del atributo. Si una fila de la columna está vacía, el valor de la celda para el miembro se devolverá con normalidad. Si la fórmula de la columna no es válida, se producirá un error en tiempo de ejecución siempre que se recupere un valor de la celda que utilice el miembro.  
  
 Antes de especificar las fórmulas de miembro personalizado de un atributo, asegúrese de que la tabla de dimensiones que contiene el atributo, o una tabla directamente relacionada, tiene una columna de cadena para almacenar las fórmulas de miembro personalizado. En este caso, puede establecer la `CustomRollupColumn` propiedad en un atributo manualmente o utilizar la mejora de la fórmula de miembro personalizado del asistente de Business Intelligence para habilitar una fórmula de miembro personalizado en un atributo. Para obtener más información sobre cómo usar esta mejora, vea [Configurar fórmulas de miembro personalizado para los atributos de una dimensión](bi-wizard-custom-member-formulas-for-attributes-in-a-dimension.md).  
  
## <a name="evaluating-custom-member-formulas"></a>Evaluar fórmulas de miembro personalizado  
 Las fórmulas de miembro personalizado son distintas de los miembros calculados. Las fórmulas de miembro personalizado se aplican a los miembros que existen en las tablas de dimensión y solo proporcionan el valor del miembro. En contraste, los miembros calculados no se almacenan en tablas de dimensiones y las expresiones de miembro calculado definen los datos y los metadatos para miembros adicionales incluidos en una jerarquía o dimensión.  
  
 Las fórmulas de miembro personalizado reemplazan las funciones de agregado asociadas a medidas. Por ejemplo, antes de especificar una fórmula de miembro personalizado, una medida que utiliza la función de agregado `Sum` tiene los siguientes valores para los siguientes miembros de la dimensión Time:  
  
-   2003: 2100  
  
    -   Quarter 1: 700  
  
    -   Quarter 2: 500  
  
    -   Quarter 3: 100  
  
    -   Quarter 4: 800  
  
-   2004: 1500  
  
    -   Quarter 1: 600  
  
    -   Quarter 2: 200  
  
    -   Quarter 3: 300  
  
    -   Quarter 4: 400  
  
 Con una fórmula de miembro personalizado, el valor del miembro es un su lugar suministrado por la fórmula de resumen personalizado. Por ejemplo, la siguiente fórmula de miembro personalizado se puede utilizar para suministrar el valor del miembro secundario Quarter 4 del miembro 2004 en la dimensión Time como 450.  
  
```  
Time.[Quarter 3] * 1.5  
```  
  
 Las fórmulas de miembro personalizado se almacenan en una columna de la tabla de dimensión. Puede habilitar fórmulas de resumen personalizado estableciendo la propiedad `CustomRollupColumn` en un atributo.  
  
 Para aplicar una expresión MDX única a todos los miembros de un atributo, cree un cálculo con nombre en la tabla de dimensión que devuelva una expresión MDX como cadena literal. A continuación, especifique el cálculo con nombre con el valor de propiedad `CustomRollupColumn` en el atributo que desea configurar. Un cálculo con nombres es una columna de una tabla de vista del origen de datos que devuelve valores de filas definidos por una expresión SQL. Para obtener más información sobre cómo crear cálculos con nombre, vea [Definir cálculos con nombre en una vista del origen de datos &#40;Analysis Services&#41;](define-named-calculations-in-a-data-source-view-analysis-services.md).  
  
> [!NOTE]  
>  Para aplicar una expresión MDX a miembros de un nivel determinado, en lugar de a miembros de todos los niveles basados en un atributo concreto, puede definir la expresión como un script MDX en el nivel. Para más información, vea [Aspectos básicos de scripting MDX &#40;Analysis Services&#41;](mdx/mdx-scripting-fundamentals-analysis-services.md).  
  
 Si utiliza miembros calculados y fórmulas de resumen personalizado para los miembros de un atributo, debe tener en cuenta el orden de evaluación. Los miembros calculados se resuelven antes que las fórmulas de resumen personalizado.  
  
## <a name="see-also"></a>Consulte también  
 [Atributos y jerarquías de atributos](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Configurar fórmulas de miembro personalizado para los atributos de una dimensión](bi-wizard-custom-member-formulas-for-attributes-in-a-dimension.md)  
  
  
