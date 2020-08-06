---
title: Selección de características (minería de datos) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], feature selections
- attributes [data mining]
- feature selection algorithms [Analysis Services]
- data mining [Analysis Services], feature selections
- neural network algorithms [Analysis Services]
- naive bayes algorithms [Analysis Services]
- decision tree algorithms [Analysis Services]
- datasets [Analysis Services]
- clustering algorithms [Analysis Services]
- coding [Data Mining]
ms.assetid: b044e785-4875-45ab-8ae4-cd3b4e3033bb
author: minewiskan
ms.author: owend
ms.openlocfilehash: ef5ee56636e7710074a893aed733905e1bf983bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674448"
---
# <a name="feature-selection-data-mining"></a>Selección de características (minería de datos)
  La *selección de características* es un término que se usa habitualmente en la minería de datos para describir las herramientas y técnicas disponibles para reducir las entradas a un tamaño manejable para el procesamiento y el análisis. La selección de características implica no solo la *reducción de cardinalidad*, lo que significa imponer un límite arbitrario o predefinido en el número de atributos que se pueden tener en cuenta al crear un modelo, pero también la elección de atributos, lo que significa que el analista o la herramienta de modelado seleccionan o descartan atributos en función de su utilidad para el análisis.  
  
 La capacidad de aplicar la selección de características es esencial para un análisis eficiente, ya que los conjuntos de datos suelen contener mucha más información de la necesaria para la generación del modelo. Por ejemplo, un conjunto de datos puede contener 500 columnas que describen las características de los clientes, pero si los datos de algunas de ellas están muy dispersos, no obtendrá muchas ventajas al agregarlas al modelo. Si mantiene las columnas innecesarias durante la generación del modelo, se necesitarán más CPU y memoria durante el proceso de entrenamiento, así como más espacio de almacenamiento para el modelo completado.  
  
 Aunque los recursos no sean un problema, normalmente se deben quitar las columnas innecesarias porque pueden degradar la calidad de los patrones detectados por las razones siguientes:  
  
-   Algunas columnas son ruidosas o redundantes. Este ruido dificulta la detección de patrones significativos a partir de los datos.  
  
-   Para detectar patrones de calidad, la mayoría de los algoritmos de minería de datos requieren un conjunto de datos de entrenamiento mucho más grande en un conjunto de datos multidimensional. Sin embargo, en algunas aplicaciones de minería de datos se dispone de muy pocos datos de entrenamiento.  
  
 Si solo 50 de las 500 columnas del origen de datos tienen información útil para la generación de un modelo, puede dejar fuera del modelo las que no son útiles o usar técnicas de selección de características para detectar automáticamente las mejores características y excluir los valores estadísticamente no significativos. La selección de características ayuda a resolver el problema de tener demasiados datos de escaso valor o muy pocos datos de mucho valor.  
  
## <a name="feature-selection-in-analysis-services-data-mining"></a>Selección de características en minería de datos de Analysis Services  
 Normalmente, la selección de características se realiza automáticamente en [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], y cada algoritmo tiene un conjunto de técnicas predeterminadas para aplicar de forma inteligente la reducción de características. La selección de características siempre se realiza antes del entrenamiento del modelo y permite elegir automáticamente en un conjunto de datos los atributos que con toda probabilidad se usarán en el mismo. Sin embargo, también puede establecer parámetros manualmente para influir en el comportamiento de la selección de características.  
  
 En general, la selección de características funciona calculando una puntuación para cada atributo y seleccionando a continuación solo los atributos que han obtenido las mejores puntuaciones. También puede ajustar el umbral para las puntuaciones más altas. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] proporciona varios métodos para calcular estas puntuaciones, y el método exacto que se aplica en un modelo depende de estos factores:  
  
-   El algoritmo usado en el modelo  
  
-   El tipo de datos del atributo  
  
-   Otros parámetros que se hayan podido establecer en el modelo  
  
 La selección de características se aplica a las entradas, a los atributos de predicción o a los estados de una columna. Una vez completada la puntuación para la selección de características, solo se incluyen en el proceso de generación del modelo y se pueden usar en la predicción los atributos y los estados que selecciona el algoritmo. Si elige un atributo de predicción que no alcanza el umbral para la selección de características, dicho atributo se puede usar en la predicción, pero las predicciones se basarán únicamente en las estadísticas globales que existen en el modelo.  
  
> [!NOTE]  
>  La selección de características afecta solo a las columnas que se usan en el modelo y no tiene ningún efecto en el almacenamiento de la estructura de minería de datos. Las columnas que se dejan fuera del modelo de minería de datos siguen estando disponibles en la estructura, y los datos de las columnas de la estructura de minería de datos se almacenan en caché.  
  
### <a name="definition-of-feature-selection-methods"></a>Definición de los métodos de selección de características  
 Hay muchas maneras de implementar la selección de características, dependiendo del tipo de datos con los que se esté trabajando y del algoritmo que se elija para el análisis. SQL Server Analysis Services proporciona varios métodos conocidos y consolidados para puntuar los atributos. El método que se aplica en los algoritmos o conjuntos de datos depende de los tipos de datos, así como del uso de las columnas.  
  
 La puntuación *interestingness* (medida del interés) se usa para clasificar y ordenar los atributos de las columnas que contienen datos numéricos continuos no binarios.  
  
 La*entropía de Shannon* y dos puntuaciones *bayesianas* están disponibles para las columnas que contengan datos discretos y discretizados. Sin embargo, si el modelo contiene columnas continuas, se usará la puntuación de grado de interés para evaluar todas las columnas de entrada, con objeto de asegurarse de que son coherentes.  
  
 En la sección siguiente se describe cada uno de los métodos de selección de características.  
  
#### <a name="interestingness-score"></a>Puntuación interestingness  
 Una característica es interesante si ofrece información útil. Dado que la definición de lo que resulta útil varía en función del escenario, el sector de minería de datos ha desarrollado varias maneras de medir la *interés*. Por ejemplo, la *novedad* podría ser interesante en la detección de valores atípicos, pero la capacidad de discriminar entre elementos estrechamente relacionados, o *peso discriminador*, podría ser más interesante para la clasificación.  
  
 La medida de interés que se usa en SQL Server Analysis Services se basa en la *entropía*, lo que significa que los atributos con distribuciones aleatorias tienen una entropía más alta y una ganancia inferior de la información. por lo tanto, estos atributos son menos interesantes. La entropía para cualquier atributo se compara con la entropía de todos los demás atributos de la manera siguiente:  
  
 Interestingness(Atributo) = - (m - Entropy(Atributo)) * (m - Entropy(Atributo))  
  
 La entropía central (o m) es la entropía de todo el conjunto de características. Al restar la entropía del atributo de destino de la entropía central, se puede evaluar cuánta información proporciona el atributo.  
  
 Esta puntuación se utiliza de forma predeterminada cada vez que la columna contiene datos numéricos continuos no binarios.  
  
#### <a name="shannons-entropy"></a>Entropía de Shannon  
 La entropía de Shannon mide la incertidumbre de una variable aleatoria para un determinado resultado. Por ejemplo, la entropía de lanzar una moneda al aire para decidir algo a cara o cruz se puede representar como una función de la probabilidad de que salga cara.  
  
 Analysis Services usa la fórmula siguiente para calcular la entropía de Shannon:  
  
 H(X) = -∑ P(xi) log(P(xi))  
  
 Este método de puntuación está disponible para los atributos discretos y de datos discretos.  
  
#### <a name="bayesian-with-k2-prior"></a>Bayesiano con prioridad K2  
 Analysis Services proporciona dos puntuaciones de selección de características basadas en las redes bayesianas. Una red bayesiana es un gráfico *dirigido* o *acíclico* de estados y de transiciones entre ellos; esto significa que algunos estados siempre son anteriores al estado actual y otros son posteriores, y que el gráfico no se repite ni realiza bucles. Por definición, las redes bayesianas permiten el uso del conocimiento previo. Sin embargo, la pregunta sobre qué estados anteriores se deben utilizar para calcular las probabilidades de los estados posteriores es importante para la precisión, el rendimiento y el diseño del algoritmo.  
  
 Cooper y Herskovits desarrollaron el algoritmo K2 para el aprendizaje a partir de una red bayesiana y este algoritmo se utiliza a menudo en la minería de datos. Es escalable y puede analizar varias variables, pero requiere la ordenación de las variables utilizadas como entrada. Para obtener más información, vea el documento [Learning Bayesian Networks](https://go.microsoft.com/fwlink/?LinkId=105885) por Chickering, Geiger y Heckerman.  
  
 Este método de puntuación está disponible para los atributos discretos y de datos discretos.  
  
#### <a name="bayesian-dirichlet-equivalent-with-uniform-prior"></a>Equivalente Dirichlet bayesiano con prioridad uniforme  
 La puntuación Equivalente Dirichlet bayesiano (BDE) también utiliza el análisis bayesiano para evaluar una red dado un conjunto de datos. El método de puntuación BDE fue desarrollado por Heckerman y está basado en la métrica BD desarrollada por Cooper y Herskovits. La distribución Dirichlet es una distribución multinomial que describe la probabilidad condicional de cada variable de la red y dispone de muchas propiedades que son útiles para el aprendizaje.  
  
 El método Equivalente Dirichlet bayesiano con prioridad uniforme (BDEU) considera un caso especial de la distribución Dirichlet, en el que se utiliza una constante matemática para crear una distribución fija o uniforme de estados anteriores. La puntuación BDE también considera la equivalencia de probabilidad; esto significa que no es de esperar que los datos diferencien estructuras equivalentes. Es decir, si la puntuación de “Si A, entonces B” es la misma que la puntuación de “Si B, entonces A”, las estructuras no se pueden diferenciar basándose en los datos y no se puede deducir la causalidad.  
  
 Para obtener más información sobre las redes bayesianas y la implementación de estos métodos de puntuación, vea este artículo sobre las [redes bayesianas](https://go.microsoft.com/fwlink/?LinkId=105885).  
  
### <a name="feature-selection-methods-used-by-analysis-services-algorithms"></a>Métodos de selección de características empleados por los algoritmos de Analysis Services  
 La tabla siguiente contiene una lista de los algoritmos que admiten la selección de características, los métodos de selección de características utilizados por los algoritmos, y los parámetros que se establecen para controlar el comportamiento de la selección de características.  
  
|Algoritmo|Método de análisis|Comentarios|  
|---------------|------------------------|--------------|  
|Bayes naive|Entropía de Shannon<br /><br /> Bayesiano con prioridad K2<br /><br /> Dirichlet bayesiano con prioridad uniforme (predeterminado)|El algoritmo Bayes naive de Microsoft solo acepta atributos discretos o de datos discretos, por lo que no puede utilizar la puntuación interestingness.<br /><br /> Para obtener más información acerca de este algoritmo, vea [Microsoft Naive Bayes Algorithm Technical Reference](microsoft-naive-bayes-algorithm-technical-reference.md).|  
|Árboles de decisión|Puntuación interestingness<br /><br /> Entropía de Shannon<br /><br /> Bayesiano con prioridad K2<br /><br /> Dirichlet bayesiano con prioridad uniforme (predeterminado)|Si alguna columna contiene valores continuos no binarios, se utiliza la puntuación interestingness (grado de interés) en todas las columnas para asegurar la coherencia. De lo contrario, se usa el método de selección de características predeterminado o el método que se haya especificado al crear el modelo.<br /><br /> Para obtener más información acerca de este algoritmo, vea [Microsoft Decision Trees Algorithm Technical Reference](microsoft-decision-trees-algorithm-technical-reference.md).|  
|Red neuronal|Puntuación interestingness<br /><br /> Entropía de Shannon<br /><br /> Bayesiano con prioridad K2<br /><br /> Dirichlet bayesiano con prioridad uniforme (predeterminado)|El algoritmo de redes neuronales de Microsoft puede usar el método bayesiano y el método basado en la entropía, siempre y cuando los datos contengan columnas continuas.<br /><br /> Para obtener más información acerca de este algoritmo, vea [Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md).|  
|Regresión logística|Puntuación interestingness<br /><br /> Entropía de Shannon<br /><br /> Bayesiano con prioridad K2<br /><br /> Dirichlet bayesiano con prioridad uniforme (predeterminado)|Aunque el algoritmo de regresión logística de Microsoft se basa en el algoritmo de red neuronal de Microsoft, no se pueden personalizar los modelos de regresión logística para controlar el comportamiento de la selección de características; por lo tanto, la selección de características siempre usa de manera predeterminada el método más apropiado para el atributo.<br /><br /> Si todos los atributos son discretos o de datos discretos, el valor predeterminado es BDEU.<br /><br /> Para obtener más información acerca de este algoritmo, vea [Microsoft Logistic Regression Algorithm Technical Reference](microsoft-logistic-regression-algorithm-technical-reference.md).|  
|Agrupación en clústeres|Puntuación interestingness|El algoritmo de clústeres de Microsoft puede usar datos discretos o discretizados. Sin embargo, dado que la puntuación de cada atributo se calcula como una distancia y se representa como un número continuo, se debe usar la puntuación interestingness.<br /><br /> Para obtener más información acerca de este algoritmo, vea [Microsoft Clustering Algorithm Technical Reference](microsoft-clustering-algorithm-technical-reference.md).|  
|Regresión lineal|Puntuación interestingness|El algoritmo de regresión lineal de Microsoft solo puede usar la puntuación interestingness porque solamente admite columnas continuas.<br /><br /> Para obtener más información acerca de este algoritmo, vea [Microsoft Linear Regression Algorithm Technical Reference](microsoft-linear-regression-algorithm-technical-reference.md).|  
|Reglas de asociación<br /><br /> Agrupación en clústeres de secuencia|No se usa|La selección de características no se invoca con estos algoritmos.<br /><br /> Sin embargo, se puede controlar el comportamiento del algoritmo y reducir el tamaño de los datos de entrada, si es necesario, al establecer el valor de los parámetros MINIMUM_SUPPORT y MINIMUM_PROBABILITY.<br /><br /> Para obtener más información, consulte [Microsoft Association Algorithm Technical Reference](microsoft-association-algorithm-technical-reference.md) y [Microsoft Sequence Clustering Algorithm Technical Reference](microsoft-sequence-clustering-algorithm-technical-reference.md).|  
|Serie temporal|No se usa|La selección de características no se aplica a los modelos de serie temporal.<br /><br /> Para obtener más información acerca de este algoritmo, vea [Microsoft Time Series Algorithm Technical Reference](microsoft-time-series-algorithm-technical-reference.md).|  
  
## <a name="feature-selection-parameters"></a>Parámetros de selección de características  
 En los algoritmos que admiten la selección de características se puede controlar cuándo se encuentra activada dicha selección usando los parámetros siguientes. Cada algoritmo tiene un valor predeterminado para el número de entradas permitidas, pero se puede invalidar este valor y especificar el número de atributos. En esta sección se enumeran los parámetros que se proporcionan para administrar la selección de características.  
  
#### <a name="maximum_input_attributes"></a>MAXIMUM_INPUT_ATTRIBUTES  
 Si un modelo contiene más columnas que el número especificado en el parámetro *MAXIMUM_INPUT_ATTRIBUTES* , el algoritmo pasa por alto cualquier columna que determina como no interesante.  
  
#### <a name="maximum_output_attributes"></a>MAXIMUM_OUTPUT_ATTRIBUTES  
 De forma similar, si un modelo contiene más columnas de predicción que el número especificado en el parámetro *MAXIMUM_OUTPUT_ATTRIBUTES* , el algoritmo pasa por alto cualquier columna que determina como no interesante.  
  
#### <a name="maximum_states"></a>MAXIMUM_STATES  
 Si un modelo contiene más casos de los especificados en el parámetro *MAXIMUM_STATES* , los estados con menor popularidad se agrupan y se tratan como estados que faltan. Si alguno de estos parámetros se establece en 0, la selección de características se desactiva. Esto afecta al tiempo de procesamiento y al rendimiento.  
  
 Además de estos métodos para la selección de características, es posible mejorar la capacidad del algoritmo para identificar o promover atributos significativos estableciendo *marcas de modelado* en el modelo o *marcas de distribución* en la estructura. Para más información sobre estos conceptos, vea [Marcas de modelado &#40;minería de datos&#41;](modeling-flags-data-mining.md) y [Distribuciones de columnas &#40;minería de datos&#41;](column-distributions-data-mining.md).  
  
## <a name="see-also"></a>Consulte también  
 [Personalizar la estructura y los modelos de minería de datos](customize-mining-models-and-structure.md)  
  
  
