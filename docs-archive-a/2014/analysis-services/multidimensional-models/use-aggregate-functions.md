---
title: Usar funciones de agregado | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- aggregate functions [Analysis Services]
ms.assetid: c42166ef-b75c-45f4-859c-09a3e9617664
author: minewiskan
ms.author: owend
ms.openlocfilehash: 83cdc571019cffd8ae99e00f119541736c6f503b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674397"
---
# <a name="use-aggregate-functions"></a>Usar funciones de agregado
  Al usar una dimensión para segmentar una medida, la medida se resume en las jerarquías contenidas en la dimensión. El comportamiento de suma depende de la función de agregado especificada en la medida. Para la mayoría de las medidas que contienen datos numéricos, la función de agregado es `Sum`. El valor de la medida se suma a cantidades diferentes dependiendo del nivel de la jerarquía que esté activo.  
  
 En Analysis Services, todas las medidas que se crean están respaldadas por una función de agregación que determina la operación de la medida. Entre los tipos de agregación predefinidos se incluyen `Sum` , `Min` , `Max` , `Count` , **recuento distintivo**y otras funciones más especializadas. O bien, si necesita agregaciones basadas en fórmulas complejas o personalizadas, puede crear un cálculo MDX en vez de usar una función de agregación creada previamente. Por ejemplo, si quiere definir una medida para un valor de porcentaje, lo haría en MDX con una medida calculada. Vea, [CREATE MEMBER &#40;instrucción MDX&#41;](/sql/mdx/mdx-data-definition-create-member).  
  
 A las medidas que se crean mediante el Asistente para cubos se les asigna un tipo de agregación como parte de la definición de la medida. El tipo de agregación es siempre `Sum`, asumiendo que la columna de origen contiene datos numéricos. `Sum` se asigna independientemente del tipo de datos de la columna de origen. Por ejemplo, si usó el Asistente para cubos para crear medidas y extrajo todas las columnas de una tabla de hechos, notará que todas las medidas resultantes tienen una agregación de `Sum`, incluso si el origen es una columna de fecha y hora. Debe revisar siempre los métodos de agregación asignados previamente para las medidas creadas mediante el asistente para asegurarse de que la función de agregación sea la adecuada.  
  
 Puede asignar o cambiar el método de agregación en la definición del cubo, a través de [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)]o por medio de MDX. Vea [Crear medidas y grupos de medida en modelos multidimensionales](create-measures-and-measure-groups-in-multidimensional-models.md) o [Aggregate &#40;MDX&#41;](/sql/mdx/aggregate-mdx) para obtener más instrucciones.  
  
##  <a name="aggregate-functions"></a><a name="AggFunction"></a>Funciones de agregado  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] proporciona funciones para agregar medidas a las dimensiones que se incluyen en los grupos de medida. El *grado de agregación* de una función de agregación determina cómo se agrega la medida en todas las dimensiones del cubo. Las funciones de agregación pertenecen a uno de tres niveles de grado de agregación:  
  
 Aditivo  
 Una medida aditiva, también denominada medida completamente aditiva, se puede agregar en todas las dimensiones que están incluidas en el grupo de medida que contiene la medida, sin restricciones.  
  
 Semiaditiva  
 Una medida semiaditiva se puede agregar en algunas, pero no todas, las dimensiones que están incluidas en el grupo de medida que contiene la medida. Por ejemplo, una medida que representa la cantidad disponible para inventario puede agregarse en una dimensión de geografía para generar una cantidad total disponible para todos los almacenes, pero la medida no se puede agregar en una dimensión de tiempo porque representa una instantánea periódica de las cantidades disponibles. Agregar dicha medida en una dimensión de tiempo generaría resultados incorrectos. Para obtener información detallada, vea [Define Semiadditive Behavior](define-semiadditive-behavior.md) .  
  
 No aditiva  
 Una medida no aditiva no se puede agregar en ninguna dimensión en el grupo de medida que contiene la medida. En su lugar, la medida debe calcularse de forma individual para cada celda del cubo que representa la medida. Por ejemplo, una medida calculada que devuelve un porcentaje, por ejemplo, un margen de beneficio, no se puede agregar a partir de los valores de porcentaje de los miembros secundarios en cualquier dimensión.  
  
 En la siguiente tabla se enumeran las funciones de agregación en [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]y se describen el grado de agregación y el resultado esperado de la función.  
  
|Función de agregación|grado de agregación|Valor devuelto|  
|--------------------------|----------------|--------------------|  
|`Sum`|Aditivo|Calcula la suma de valores de todos los miembros secundarios. Es la función de agregación predeterminada.|  
|`Count`|Aditivo|Recupera el recuento de todos los miembros secundarios.|  
|`Min`|Semiaditiva|Recupera el valor más bajo para todos los miembros secundarios.|  
|`Max`|Semiaditiva|Recupera el valor más alto para todos los miembros secundarios.|  
|`DistinctCount`|No aditiva|Recupera el recuento de todos los miembros secundarios únicos. Para más detalles, vea [About Distinct Count Measures](use-aggregate-functions.md#bkmk_distinct) en la próxima sección.|  
|`None`|No aditiva|No se realiza una agregación y todos los valores para los miembros hoja y no hoja de una dimensión se suministran directamente desde la tabla de hechos para el grupo de medida que contiene la medida. Si no se puede leer ningún valor desde la tabla de hechos para un miembro, se establece el valor para dicho miembro en null.|  
|`ByAccount`|Semiaditiva|Calcula la agregación según la función de agregación asignada al tipo de cuenta para un miembro en una dimensión de cuenta. Si no existe ninguna dimensión de tipo de cuenta en el grupo de medida, se trata como la función de agregación `None`.<br /><br /> Para más información sobre las dimensiones de cuenta, vea [Crear una cuenta financiera de una dimensión de tipo primario-secundario](database-dimensions-finance-account-of-parent-child-type.md).|  
|`AverageOfChildren`|Semiaditiva|Calcula el promedio de los valores de todos los miembros secundarios no vacíos.|  
|`FirstChild`|Semiaditiva|Recupera el valor del primer miembro secundario.|  
|`LastChild`|Semiaditiva|Recupera el valor del último miembro secundario.|  
|`FirstNonEmpty`|Semiaditiva|Recupera el valor del primer miembro secundario no vacío.|  
|`LastNonEmpty`|Semiaditiva|Recupera el valor del último miembro secundario no vacío.|  
  
##  <a name="about-distinct-count-measures"></a><a name="bkmk_distinct"></a> About Distinct Count Measures  
 Una medida que tenga el valor **Distinct Count** en la propiedad **Aggregate Function** se denomina medida de recuento distintiva. Una medida de recuento distintiva se puede usar para contar el número de veces que aparecen los miembros del nivel inferior de una dimensión en la tabla de hechos. Como el recuento es distintivo, si un miembro aparece varias veces, solamente se cuenta una vez. Una medida de recuento distintiva se coloca siempre en un grupo de medida dedicado. Colocar una medida de recuento distintiva en su propio grupo de medida es una recomendación que se ha creado en el diseñador como una técnica de optimización del rendimiento.  
  
 Las medidas de recuento distintivas se usan normalmente para determinar, por cada miembro de una dimensión, cuántos miembros distintivos del nivel inferior de otra dimensión comparten filas en la tabla de hechos. Por ejemplo, en un cubo Sales, por cada cliente y grupo de clientes, ¿cuántos productos diferentes se adquirieron? Es decir, por cada miembro de la dimensión Customers, ¿cuántos miembros diferentes del nivel inferior de la dimensión Products comparten filas en la tabla de hechos? O, por ejemplo, en un cubo de visitas a un sitio de Internet, por cada visitante y grupo de visitantes del sitio, ¿cuántas páginas distintas del sitio de Internet se visitaron? Es decir, por cada miembro de la dimensión Site Visitors, ¿cuántos miembros diferentes del nivel inferior de la dimensión Pages comparten filas en la tabla de hechos? En cada uno de estos ejemplos, los miembros del nivel inferior de la segunda dimensión se cuentan mediante una medida de recuento distintiva.  
  
 Este tipo de análisis no tiene por qué limitarse a dos dimensiones. De hecho, una medida de recuento distintiva se puede separar y segmentar mediante cualquier combinación de dimensiones del cubo, incluida la dimensión que contiene los miembros contados.  
  
 Una medida de recuento distintiva que cuenta miembros se basa en una columna de clave externa de la tabla de hechos. (Es decir, la propiedad **Source Column** de la medida identifica esta columna). Esta columna se combina con la columna de la tabla de dimensiones que identifica a los miembros que cuenta la medida de recuento distintiva.  
  
## <a name="see-also"></a>Consulte también  
 [Medidas y grupos de medida](measures-and-measure-groups.md)   
 [Referencia de funciones MDX &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)   
 [Define Semiadditive Behavior](define-semiadditive-behavior.md)  
  
  
