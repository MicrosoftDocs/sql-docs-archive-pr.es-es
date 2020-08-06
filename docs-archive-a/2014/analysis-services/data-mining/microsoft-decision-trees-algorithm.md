---
title: Algoritmo de árboles de decisión de Microsoft | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- predictions [Analysis Services], discrete attributes
- predictions [Analysis Services], continuous attributes
- algorithms [data mining]
- discrete attributes [Analysis Services]
- classification algorithms [Analysis Services]
- discrete columns [Analysis Services]
- decision tree algorithms [Analysis Services]
- decision trees [Analysis Services]
- continuous columns
- regression algorithms [Analysis Services]
ms.assetid: 95ffe66f-c261-4dc5-ad57-14d2d73205ff
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3c9a893a6f0cb02e5acd2e497e0b57c29d7ac2ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674433"
---
# <a name="microsoft-decision-trees-algorithm"></a>Algoritmo de árboles de decisión de Microsoft
  El [!INCLUDE[msCoName](../../includes/msconame-md.md)] algoritmo de árboles de decisión de es un algoritmo de clasificación y regresión proporcionado por [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] para su uso en el modelado de predicción de atributos discretos y continuos.

 Para los atributos discretos, el algoritmo hace predicciones basándose en las relaciones entre las columnas de entrada de un conjunto de datos. Utiliza los valores, conocidos como estados, de estas columnas para predecir los estados de una columna que se designa como elemento de predicción. Específicamente, el algoritmo identifica las columnas de entrada que se correlacionan con la columna de predicción. Por ejemplo, en un escenario para predecir qué clientes van a adquirir probablemente una bicicleta, si nueve de diez clientes jóvenes compran una bicicleta, pero solo lo hacen dos de diez clientes de edad mayor, el algoritmo infiere que la edad es un buen elemento de predicción en la compra de bicicletas. El árbol de decisión realiza predicciones basándose en la tendencia hacia un resultado concreto.

 Para los atributos continuos, el algoritmo usa la regresión lineal para determinar dónde se divide un árbol de decisión.

 Si se define más de una columna como elemento de predicción, o si los datos de entrada contienen una tabla anidada que se haya establecido como elemento de predicción, el algoritmo genera un árbol de decisión independiente para cada columna de predicción.

## <a name="example"></a>Ejemplo
 El departamento de marketing de la empresa [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] desea identificar las características de los clientes antiguos que podrían indicar si es probable que realicen alguna compra en el futuro. La base de datos [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] almacena información demográfica que describe a los clientes antiguos. Mediante el algoritmo de árboles de decisión de [!INCLUDE[msCoName](../../includes/msconame-md.md)] que analiza esta información, el departamento puede generar un modelo que predice si un determinado cliente va a comprar productos, basándose en el estado de las columnas conocidas sobre ese cliente, como la demografía o los patrones de compra anteriores.

## <a name="how-the-algorithm-works"></a>Cómo funciona el algoritmo
 El algoritmo de árboles de decisión de [!INCLUDE[msCoName](../../includes/msconame-md.md)] genera un modelo de minería de datos mediante la creación de una serie de divisiones en el árbol. Estas divisiones se representan como *nodos*. El algoritmo agrega un nodo al modelo cada vez que una columna de entrada tiene una correlación significativa con la columna de predicción. La forma en que el algoritmo determina una división varía en función de si predice una columna continua o una columna discreta.

 El algoritmo de árboles de decisión de [!INCLUDE[msCoName](../../includes/msconame-md.md)] utiliza la *selección de características* para guiar la selección de los atributos más útiles. Todos los algoritmos de minería de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilizan la selección de características para mejorar el rendimiento y la calidad del análisis. La selección de características es importante para evitar que los atributos irrelevantes utilicen tiempo de procesador. Si utiliza demasiados atributos de predicción o de entrada al diseñar un modelo de minería de datos, el modelo puede tardar mucho tiempo en procesarse o incluso quedarse sin memoria. Algunos métodos para determinar si hay que dividir el árbol son las métricas estándar del sector para la *entropía* y las redes Bayesianas *.* Para obtener más información sobre los métodos que se usan para seleccionar los atributos significativos y, después, puntuarlos y clasificarlos, vea [Selección de características &#40;minería de datos&#41;](feature-selection-data-mining.md).

 Un problema común de los modelos de minería de datos es que el modelo se vuelve demasiado sensible a pequeñas diferencias en los datos de entrenamiento, en cuyo caso se dice *que está sobrecargado o* *sobreentrenado*. Un modelo sobreajustado no se puede generalizar a otros conjuntos de datos. Para evitar sobreajustar un conjunto de datos determinado, el algoritmo de árboles de decisión de [!INCLUDE[msCoName](../../includes/msconame-md.md)] utiliza técnicas para controlar el crecimiento del árbol. Para obtener una explicación más detallada de cómo funciona el algoritmo de árboles de decisión de [!INCLUDE[msCoName](../../includes/msconame-md.md)] , vea [Referencia técnica del algoritmo de árboles de decisión de Microsoft](microsoft-decision-trees-algorithm-technical-reference.md).

### <a name="predicting-discrete-columns"></a>Predecir columnas discretas
 La forma en que el algoritmo de árboles de decisión de [!INCLUDE[msCoName](../../includes/msconame-md.md)] genera un árbol para una columna de predicción discreta puede mostrarse mediante un histograma. El siguiente diagrama muestra un histograma que seguimiento una columna de predicción, Bike Buyers, con una columna de entrada, Age. El histograma muestra que la edad de una persona ayuda a distinguir si esa persona comprará una bicicleta.

 ![Histograma del algoritmo de árboles de decisión de Microsoft](../media/dt-histogram.gif "Histograma del algoritmo de árboles de decisión de Microsoft")

 La correlación que aparece en el diagrama hará que el algoritmo de árboles de decisión de [!INCLUDE[msCoName](../../includes/msconame-md.md)] cree un nuevo nodo en el modelo.

 ![Nodo del árbol de decisión](../media/dt-tree.gif "Nodo del árbol de decisión")

 A medida que el algoritmo agrega nuevos nodos a un modelo, se forma una estructura en árbol. El nodo superior del árbol describe el desglose de la columna de predicción para la población global de clientes. A medida que el modelo crece, el algoritmo considera todas las columnas.

### <a name="predicting-continuous-columns"></a>Predecir columnas continuas
 Cuando el algoritmo de árboles de decisión de [!INCLUDE[msCoName](../../includes/msconame-md.md)] genera un árbol basándose en una columna de predicción continua, cada nodo contiene una fórmula de regresión. Se produce una división en un punto de no linealidad de la fórmula de regresión. Por ejemplo, considere el siguiente diagrama.

 ![Varias líneas de regresión en las que se muestra la no linealidad](../media/regression-tree1.gif "Varias líneas de regresión en las que se muestra la no linealidad")

 El diagrama contiene los datos que pueden modelarse utilizando una sola línea o dos líneas conectadas. Sin embargo, una sola línea realizará un pobre trabajo en la representación de los datos. En su lugar, si se usan dos líneas, el modelo hará un mejor trabajo en la aproximación a los datos. El punto donde las dos líneas se unen es el punto de no linealidad y donde se dividiría un nodo de un modelo de árbol de decisión. Por ejemplo, el nodo que corresponde al punto de no linealidad del gráfico anterior podría representarse mediante el siguiente diagrama. Las dos ecuaciones representan las ecuaciones de regresión de las dos líneas.

 ![Ecuación que representa un punto de no linealidad](../media/regression-tree2.gif "Ecuación que representa un punto de no linealidad")

## <a name="data-required-for-decision-tree-models"></a>Datos requeridos para los modelos de árboles de decisión
 Cuando prepare los datos para su uso en un modelo de árboles de decisión, conviene que comprenda qué requisitos son imprescindibles para el algoritmo concreto, incluidos el volumen de datos necesario y la forma en que estos se utilizan.

 Los requisitos para un modelo de árboles de decisión son los siguientes:

-   **Una columna de una sola clave** : cada modelo debe contener una columna numérica o de texto que identifique cada registro de manera única. No están permitidas las claves compuestas.

-   **Una columna de predicción** . Se requiere al menos una columna de predicción. Puede incluir varios atributos de predicción en un modelo y pueden ser de tipos diferentes, numérico o discreto. Sin embargo, el incremento del número de atributos de predicción puede aumentar el tiempo de procesamiento.

-   **Columnas de entrada** . Se requieren columnas de entrada, que pueden ser discretas o continuas. Aumentar el número de atributos de entrada afecta al tiempo de procesamiento.

 Para obtener información más detallada sobre los tipos de contenido y los tipos de datos compatibles con los modelos de árboles de decisión, vea la sección Requisitos de [Referencia técnica del algoritmo de árboles de decisión de Microsoft](microsoft-decision-trees-algorithm-technical-reference.md).

## <a name="viewing-a-decision-trees-model"></a>Ver un modelo de árboles de decisión
 Para examinar el modelo, puede utilizar el **Visor de árboles de Microsoft**. Si un modelo genera varios árboles, puede seleccionar uno y el visor muestra un esquema de cómo se clasifican los casos para cada atributo de predicción. También puede ver la interacción de los árboles utilizando el visor de redes de dependencias. Para obtener más información, vea [Examinar un modelo usando el Visor de árboles de Microsoft](browse-a-model-using-the-microsoft-tree-viewer.md).

 Si desea obtener información más detallada sobre cualquier bifurcación o nodo del árbol, también puede examinar el modelo utilizando el [Visor de árbol de contenido genérico de Microsoft](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md). El contenido almacenado para el modelo incluye la distribución para todos los valores de cada nodo, las probabilidades en cada nivel del árbol y las fórmulas de regresión para los atributos continuos. Para obtener más información, vea [Contenido del modelo de minería de datos para los modelos de árboles de decisión &#40;Analysis Services - Minería de datos&#41;](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md).

## <a name="creating-predictions"></a>Crear predicciones
 Una vez procesado el modelo, los resultados se almacenan como un conjunto de patrones y estadísticas que se pueden usar para explorar las relaciones o para realizar predicciones.

 Para obtener ejemplos de consultas que se van a usar con un modelo de árboles de decisión, vea [Ejemplos de consultas de modelos de árboles de decisión](decision-trees-model-query-examples.md).

 Para obtener información general sobre cómo crear consultas con modelos de minería de datos, vea [Consultas de minería de datos](data-mining-queries.md).

## <a name="remarks"></a>Observaciones

-   Admite el uso del Lenguaje de marcado de modelos de predicción (PMML) para crear modelos de minería de datos.

-   Admite la obtención de detalles.

-   Admite el uso de modelos de minería de datos OLAP y la creación de dimensiones de minería de datos.

## <a name="see-also"></a>Consulte también
 [Algoritmos de minería de datos &#40;Analysis Services-minería de datos&#41;algoritmo de](data-mining-algorithms-analysis-services-data-mining.md) árboles de decisión de [Microsoft algoritmo](microsoft-decision-trees-algorithm-technical-reference.md) de árboles de decisión [ejemplos de consulta modelo](decision-trees-model-query-examples.md) [de minería de datos para los modelos de árbol de decisión &#40;Analysis Services-minería de datos&#41;](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md)


