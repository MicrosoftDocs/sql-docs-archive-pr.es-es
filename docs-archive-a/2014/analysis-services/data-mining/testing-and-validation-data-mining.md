---
title: Prueba y validación (minería de datos) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- testing data mining models
- comparing mining models
- continuous attribute charts
- data mining [Analysis Services], models
- charts [Analysis Services]
- predictive modeling [Analysis Services]
- mining models [Analysis Services], validating
- validating data mining models
- viewing mining accuracy
- confidence scores [data mining]
- displaying mining accuracy
- predictions [Analysis Services], comparing mining models
- scoring [data mining]
- lift charts [Analysis Services]
- classification matrix [Analysis Services]
- CRISP-DM
- accuracy testing [data mining]
ms.assetid: 197144f5-21ed-4009-b448-fe412fb3916c
author: minewiskan
ms.author: owend
ms.openlocfilehash: c12f0215daed0c3308c63f36df0ba323152ec8d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662345"
---
# <a name="testing-and-validation-data-mining"></a><span data-ttu-id="c98ce-102">Prueba y validación (minería de datos)</span><span class="sxs-lookup"><span data-stu-id="c98ce-102">Testing and Validation (Data Mining)</span></span>
  <span data-ttu-id="c98ce-103">La validación es el proceso de evaluar cuál sería el rendimiento de sus modelos de minería de datos con datos reales.</span><span class="sxs-lookup"><span data-stu-id="c98ce-103">Validation is the process of assessing how well your mining models perform against real data.</span></span> <span data-ttu-id="c98ce-104">Es importante que valide sus modelos de minería de datos entendiendo su calidad y sus características antes de implementarlos en un entorno de producción.</span><span class="sxs-lookup"><span data-stu-id="c98ce-104">It is important that you validate your mining models by understanding their quality and characteristics before you deploy them into a production environment.</span></span>  
  
 <span data-ttu-id="c98ce-105">En esta sección se presentan algunos conceptos básicos relacionados con la calidad de los modelos y se describen las estrategias para la validación de modelos que se proporcionan en [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c98ce-105">This section introduces some basic concepts related to model quality, and describes the strategies for model validation that are provided in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="c98ce-106">Para obtener información general sobre cómo la validación del modelo se adapta a procesos de minería de datos de mayor tamaño, vea [Soluciones de minería de datos](data-mining-solutions.md).</span><span class="sxs-lookup"><span data-stu-id="c98ce-106">For an overview of how model validation fits into the larger data mining process, see [Data Mining Solutions](data-mining-solutions.md).</span></span>  
  
## <a name="methods-for-testing-and-validation-of-data-mining-models"></a><span data-ttu-id="c98ce-107">Métodos de prueba y validación de los modelos de minería de datos</span><span class="sxs-lookup"><span data-stu-id="c98ce-107">Methods for Testing and Validation of Data Mining Models</span></span>  
 <span data-ttu-id="c98ce-108">Existen muchos enfoques a la hora de evaluar la calidad y las características de un modelo de minería de datos.</span><span class="sxs-lookup"><span data-stu-id="c98ce-108">There are many approaches for assessing the quality and characteristics of a data mining model.</span></span>  
  
-   <span data-ttu-id="c98ce-109">Use varias medidas de validez estadística para determinar si existen problemas en los datos o en el modelo.</span><span class="sxs-lookup"><span data-stu-id="c98ce-109">Use various measures of statistical validity to determine whether there are problems in the data or in the model.</span></span>  
  
-   <span data-ttu-id="c98ce-110">Separe los datos en conjuntos de entrenamiento y de prueba con el fin de probar la precisión de predicciones.</span><span class="sxs-lookup"><span data-stu-id="c98ce-110">Separate the data into training and testing sets to test the accuracy of predictions.</span></span>  
  
-   <span data-ttu-id="c98ce-111">Solicite a los expertos comerciales que revisen los resultados del modelo de minería de datos para determinar si los patrones detectados tienen sentido en un escenario empresarial concreto.</span><span class="sxs-lookup"><span data-stu-id="c98ce-111">Ask business experts to review the results of the data mining model to determine whether the discovered patterns have meaning in the targeted business scenario</span></span>  
  
 <span data-ttu-id="c98ce-112">Todos estos métodos son útiles para la metodología de minería de datos y se usan de forma iterativa a la hora de crear, probar y refinar modelos para responder a un problema concreto.</span><span class="sxs-lookup"><span data-stu-id="c98ce-112">All of these methods are useful in data mining methodology and are used iteratively as you create, test, and refine models to answer a specific problem.</span></span> <span data-ttu-id="c98ce-113">No hay ninguna regla completa única que pueda indicarle si un modelo es suficientemente bueno, o si cuenta con suficientes datos.</span><span class="sxs-lookup"><span data-stu-id="c98ce-113">No single comprehensive rule can tell you when a model is good enough, or when you have enough data.</span></span>  
  
## <a name="definition-of-criteria-for-validating-data-mining-models"></a><span data-ttu-id="c98ce-114">Definición de los criterios para validar los modelos de minería de datos</span><span class="sxs-lookup"><span data-stu-id="c98ce-114">Definition of Criteria for Validating Data Mining Models</span></span>  
 <span data-ttu-id="c98ce-115">Las medidas de minería de datos se suelen agrupar en las categorías de precisión, confiabilidad y utilidad.</span><span class="sxs-lookup"><span data-stu-id="c98ce-115">Measures of data mining generally fall into the categories of accuracy, reliability, and usefulness.</span></span>  
  
 <span data-ttu-id="c98ce-116">La*precisión* es una medida que indica hasta qué punto el modelo pone en correlación un resultado con los atributos de los datos que se han proporcionado.</span><span class="sxs-lookup"><span data-stu-id="c98ce-116">*Accuracy* is a measure of how well the model correlates an outcome with the attributes in the data that has been provided.</span></span> <span data-ttu-id="c98ce-117">Existen varias medidas de precisión, pero todas ellas dependen de los datos que se utilicen.</span><span class="sxs-lookup"><span data-stu-id="c98ce-117">There are various measures of accuracy, but all measures of accuracy are dependent on the data that is used.</span></span> <span data-ttu-id="c98ce-118">En realidad, podrían faltar valores o éstos ser aproximados, o incluso diferentes procesos podrían cambiar los datos.</span><span class="sxs-lookup"><span data-stu-id="c98ce-118">In reality, values might be missing or approximate, or the data might have been changed by multiple processes.</span></span> <span data-ttu-id="c98ce-119">En particular, en la fase de exploración y desarrollo, podría decidir aceptar una cierta cantidad de errores en los datos, sobre todo si éstos son suficientemente uniformes en sus características.</span><span class="sxs-lookup"><span data-stu-id="c98ce-119">Particularly in the phase of exploration and development, you might decide to accept a certain amount of error in the data, especially if the data is fairly uniform in its characteristics.</span></span> <span data-ttu-id="c98ce-120">Por ejemplo, un modelo que predice las ventas para un almacén determinado en base a las ventas pasadas puede estar muy correlacionado y ser muy preciso, incluso si ese almacén ha utilizado un método de contabilidad equivocado continuamente.</span><span class="sxs-lookup"><span data-stu-id="c98ce-120">For example, a model that predicts sales for a particular store based on past sales can be strongly correlated and very accurate, even if that store consistently used the wrong accounting method.</span></span> <span data-ttu-id="c98ce-121">Por tanto, es necesario equilibrar las mediciones de precisión mediante las valoraciones de confiabilidad.</span><span class="sxs-lookup"><span data-stu-id="c98ce-121">Therefore, measurements of accuracy must be balanced by assessments of reliability.</span></span>  
  
 <span data-ttu-id="c98ce-122">La*confiabilidad* evalúa la manera en la que se comporta un modelo de minería de datos en conjuntos de datos diferentes.</span><span class="sxs-lookup"><span data-stu-id="c98ce-122">*Reliability* assesses the way that a data mining model performs on different data sets.</span></span> <span data-ttu-id="c98ce-123">Un modelo de minería de datos es confiable si genera el mismo tipo de predicciones o encuentra los mismos tipos generales de patrones independientemente de los datos de prueba que se proporcionen.</span><span class="sxs-lookup"><span data-stu-id="c98ce-123">A data mining model is reliable if it generates the same type of predictions or finds the same general kinds of patterns regardless of the test data that is supplied.</span></span> <span data-ttu-id="c98ce-124">Por ejemplo, el modelo que ha generado para el almacén que utilizó un método de contabilidad equivocado no podría extrapolarse correctamente a otros almacenes, y por tanto, no sería confiable.</span><span class="sxs-lookup"><span data-stu-id="c98ce-124">For example, the model that you generate for the store that used the wrong accounting method would not generalize well to other stores, and therefore would not be reliable.</span></span>  
  
 <span data-ttu-id="c98ce-125">La*utilidad* incluye diferentes métricas que le indican si el modelo proporciona información útil.</span><span class="sxs-lookup"><span data-stu-id="c98ce-125">*Usefulness* includes various metrics that tell you whether the model provides useful information.</span></span> <span data-ttu-id="c98ce-126">Por ejemplo, un modelo de minería de datos que pone en correlación la ubicación del almacén con las ventas podría ser preciso y fiable, pero podría no ser útil, ya que no se podría generalizar ese resultado si se agregaran más almacenes en la misma ubicación.</span><span class="sxs-lookup"><span data-stu-id="c98ce-126">For example, a data mining model that correlates store location with sales might be both accurate and reliable, but might not be useful, because you cannot generalize that result by adding more stores at the same location.</span></span> <span data-ttu-id="c98ce-127">Es más, no responde a la pregunta comercial fundamental de porqué ciertas ubicaciones tienen más ventas que otras.</span><span class="sxs-lookup"><span data-stu-id="c98ce-127">Moreover, it does not answer the fundamental business question of why certain locations have more sales.</span></span> <span data-ttu-id="c98ce-128">También podría descubrir que un modelo que parece correcto, en realidad no tiene sentido porque está basado en correlaciones cruzadas de los datos.</span><span class="sxs-lookup"><span data-stu-id="c98ce-128">You might also find that a model that appears successful in fact is meaningless, because it is based on cross-correlations in the data.</span></span>  
  
## <a name="tools-for-testing-and-validation-of-mining-models"></a><span data-ttu-id="c98ce-129">Herramientas de prueba y validación de modelos de minería de datos</span><span class="sxs-lookup"><span data-stu-id="c98ce-129">Tools for Testing and Validation of Mining Models</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="c98ce-130">admite varios enfoques para la validación de soluciones de minería de datos, que abarcan todas las fases de la metodología de prueba de la minería de datos.</span><span class="sxs-lookup"><span data-stu-id="c98ce-130">supports multiple approaches to validation of data mining solutions, supporting all phases of the data mining test methodology.</span></span>  
  
-   <span data-ttu-id="c98ce-131">Crear particiones de los datos de los conjuntos de prueba y entrenamiento.</span><span class="sxs-lookup"><span data-stu-id="c98ce-131">Partitioning data into testing and training sets.</span></span>  
  
-   <span data-ttu-id="c98ce-132">Filtrar modelos para entrenar y probar combinaciones diferentes de los mismos datos de origen.</span><span class="sxs-lookup"><span data-stu-id="c98ce-132">Filtering models to train and test different combinations of the same source data.</span></span>  
  
-   <span data-ttu-id="c98ce-133">Medir la *mejora respecto al modelo predictivo* y la *ganancia*.</span><span class="sxs-lookup"><span data-stu-id="c98ce-133">Measuring *lift* and *gain*.</span></span> <span data-ttu-id="c98ce-134">Un *gráfico de mejora respecto al modelo predictivo* es un método para visualizar la mejora que obtendrá de usar un modelo de minería de datos, si lo compara con una estimación aleatoria.</span><span class="sxs-lookup"><span data-stu-id="c98ce-134">A *lift chart* is a method of visualizing the improvement that you get from using a data mining model, when you compare it to random guessing.</span></span>  
  
-   <span data-ttu-id="c98ce-135">Realizar una *validación cruzada* de los conjuntos de datos</span><span class="sxs-lookup"><span data-stu-id="c98ce-135">Performing *cross-validation* of data sets</span></span>  
  
-   <span data-ttu-id="c98ce-136">Generar *matrices de clasificación*.</span><span class="sxs-lookup"><span data-stu-id="c98ce-136">Generating *classification matrices*.</span></span> <span data-ttu-id="c98ce-137">Estos gráficos ordenan las estimaciones buenas y malas en una tabla, lo que permite analizar rápida y fácilmente con qué precisión predice el modelo el valor de destino.</span><span class="sxs-lookup"><span data-stu-id="c98ce-137">These charts sort good and bad guesses into a table so that you can quickly and easily gauge how accurately the model predicts the target value.</span></span>  
  
-   <span data-ttu-id="c98ce-138">Crear *gráficos de dispersión* para evaluar el ajuste de una fórmula de regresión.</span><span class="sxs-lookup"><span data-stu-id="c98ce-138">Creating *scatter plots* to assess the fit of a regression formula.</span></span>  
  
-   <span data-ttu-id="c98ce-139">Crear *gráficos de beneficios* que permiten asociar ganancias o costos financieros con el uso de cierto modelo de minería de datos, para poder evaluar el valor de las recomendaciones.</span><span class="sxs-lookup"><span data-stu-id="c98ce-139">Creating *profit charts* that associate financial gain or costs with the use of a mining model, so that you can assess the value of the recommendations.</span></span>  
  
 <span data-ttu-id="c98ce-140">Estas métricas no pretenden responder a la pregunta de si el modelo de minería de datos resuelve sus preguntas empresariales, sino que proporcionan medidas objetivas que puede usar para evaluar la confiabilidad de los datos para los análisis predictivos, y le ofrecen ayuda a la hora de decidir si debe usar una iteración determinada en el proceso de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="c98ce-140">These metrics do not aim to answer the question of whether the data mining model answers your business question; rather, these metrics provide objective measurements that you can use to assess the reliability of your data for predictive analytics, and to guide your decision of whether to use a particular iterate on the development process.</span></span>  
  
 <span data-ttu-id="c98ce-141">Los temas de esta sección proporcionan información general de cada método y le guían en el proceso de medir la exactitud de los modelos generados mediante la minería de datos de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c98ce-141">The topics in this section provide an overview of each method and walk you through the process of measuring the accuracy of models that you build using SQL Server Data Mining.</span></span>  
  
### <a name="related-topics"></a><span data-ttu-id="c98ce-142">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="c98ce-142">Related Topics</span></span>  
  
|<span data-ttu-id="c98ce-143">Temas</span><span class="sxs-lookup"><span data-stu-id="c98ce-143">Topics</span></span>|<span data-ttu-id="c98ce-144">Vínculos</span><span class="sxs-lookup"><span data-stu-id="c98ce-144">Links</span></span>|  
|------------|-----------|  
|<span data-ttu-id="c98ce-145">Obtenga información sobre cómo configurar un conjunto de datos de prueba mediante un asistente o mediante los comandos DMX</span><span class="sxs-lookup"><span data-stu-id="c98ce-145">Learn how to set up a testing data set using a wizard or DMX commands</span></span>|[<span data-ttu-id="c98ce-146">Conjuntos de datos de entrenamiento y de prueba</span><span class="sxs-lookup"><span data-stu-id="c98ce-146">Training and Testing Data Sets</span></span>](training-and-testing-data-sets.md)|  
|<span data-ttu-id="c98ce-147">Obtenga información sobre cómo probar la distribución y la representatividad de los datos de una estructura de minería de datos</span><span class="sxs-lookup"><span data-stu-id="c98ce-147">Learn how to test the distribution and representativeness of the data in a mining structure</span></span>|[<span data-ttu-id="c98ce-148">Validación cruzada &#40;Analysis Services - Minería de datos&#41;</span><span class="sxs-lookup"><span data-stu-id="c98ce-148">Cross-Validation &#40;Analysis Services - Data Mining&#41;</span></span>](cross-validation-analysis-services-data-mining.md)|  
|<span data-ttu-id="c98ce-149">Obtenga información sobre los tipos de gráficos de precisión proporcionados en [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c98ce-149">Learn about the accuracy chart types provided in [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)].</span></span>|[<span data-ttu-id="c98ce-150">Gráfico de mejora respecto al modelo predictivo &#40;Analysis Services - Minería de datos&#41;</span><span class="sxs-lookup"><span data-stu-id="c98ce-150">Lift Chart &#40;Analysis Services - Data Mining&#41;</span></span>](lift-chart-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="c98ce-151">Gráfico de beneficios &#40;Analysis Services - Minería de datos&#41;</span><span class="sxs-lookup"><span data-stu-id="c98ce-151">Profit Chart &#40;Analysis Services - Data Mining&#41;</span></span>](profit-chart-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="c98ce-152">Gráfico de dispersión &#40;Analysis Services - Minería de datos&#41;</span><span class="sxs-lookup"><span data-stu-id="c98ce-152">Scatter Plot &#40;Analysis Services - Data Mining&#41;</span></span>](scatter-plot-analysis-services-data-mining.md)|  
|<span data-ttu-id="c98ce-153">Aprenda a crear una matriz de clasificación, a veces denominada una matriz de confusión, para evaluar el número de verdaderos positivos, falsos positivos, verdaderos negativos y falsos negativos.</span><span class="sxs-lookup"><span data-stu-id="c98ce-153">Learn how to create a classification matrix, sometimes called a confusion matrix, for assessing the number of true and false positives and negatives.</span></span>|[<span data-ttu-id="c98ce-154">Matriz de clasificación &#40;Analysis Services - Minería de datos&#41;</span><span class="sxs-lookup"><span data-stu-id="c98ce-154">Classification Matrix &#40;Analysis Services - Data Mining&#41;</span></span>](classification-matrix-analysis-services-data-mining.md)|  
  
## <a name="see-also"></a><span data-ttu-id="c98ce-155">Consulte también</span><span class="sxs-lookup"><span data-stu-id="c98ce-155">See Also</span></span>  
 <span data-ttu-id="c98ce-156">[Herramientas de minería de datos](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="c98ce-156">[Data Mining Tools](data-mining-tools.md) </span></span>  
 <span data-ttu-id="c98ce-157">[Soluciones de minería de datos](data-mining-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="c98ce-157">[Data Mining Solutions](data-mining-solutions.md) </span></span>  
 [<span data-ttu-id="c98ce-158">Tareas y procedimientos de prueba y validación &#40;minería de datos&#41;</span><span class="sxs-lookup"><span data-stu-id="c98ce-158">Testing and Validation Tasks and How-tos &#40;Data Mining&#41;</span></span>](testing-and-validation-tasks-and-how-tos-data-mining.md)  
  
  