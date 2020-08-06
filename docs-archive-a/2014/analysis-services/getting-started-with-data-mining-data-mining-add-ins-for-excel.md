---
title: Introducción con minería de datos (complementos de minería de datos para Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: cbe10a19-e194-408e-a65b-5fdf3fb1e880
author: minewiskan
ms.author: owend
ms.openlocfilehash: 066fc72fa0570d56376cc73478a68e42d20ffbc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669962"
---
# <a name="getting-started-with-data-mining-data-mining-add-ins-for-excel"></a><span data-ttu-id="b4882-102">Introducción a la minería de datos (Complementos de minería de datos para Excel)</span><span class="sxs-lookup"><span data-stu-id="b4882-102">Getting Started with Data Mining (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="b4882-103">La minería de datos es el proceso de detectar patrones significativos en los datos.</span><span class="sxs-lookup"><span data-stu-id="b4882-103">Data mining is the process of discovering meaningful patterns in data.</span></span> <span data-ttu-id="b4882-104">La minería de datos es un complemento natural al proceso de explorar y entender los datos a través de BI tradicional.</span><span class="sxs-lookup"><span data-stu-id="b4882-104">Data mining is a natural complement to the process of exploring and understanding your data through traditional BI.</span></span> <span data-ttu-id="b4882-105">Los algoritmos automáticos pueden procesar cantidades de datos muy grandes y detectar patrones y tendencias que, de lo contrario, estarían ocultos.</span><span class="sxs-lookup"><span data-stu-id="b4882-105">Machine algorithms can process very large amounts of data and discover patterns and trends that would otherwise be hidden.</span></span>  
  
 <span data-ttu-id="b4882-106">Para realizar la minería de datos, puede recopilar datos relevantes para una pregunta específica, como "¿quiénes son mis clientes?".</span><span class="sxs-lookup"><span data-stu-id="b4882-106">To do data mining, you collect data that is relevant to a specific question, such as "Who are my customers?"</span></span> <span data-ttu-id="b4882-107">o "¿Qué productos se compraron?"</span><span class="sxs-lookup"><span data-stu-id="b4882-107">or "what products were purchased?"</span></span> <span data-ttu-id="b4882-108">y, a continuación, aplique un algoritmo para buscar correlaciones estadísticas en los datos.</span><span class="sxs-lookup"><span data-stu-id="b4882-108">and then apply an algorithm to find statistical correlations in the data.</span></span> <span data-ttu-id="b4882-109">Los patrones y las tendencias que se detectan en el análisis se almacenan en forma de modelo de minería de datos.</span><span class="sxs-lookup"><span data-stu-id="b4882-109">The patterns and trends found through analysis are stored as a mining model.</span></span> <span data-ttu-id="b4882-110">Después puede aplicar el modelo de minería de datos a nuevos datos en escenarios empresariales como los siguientes:</span><span class="sxs-lookup"><span data-stu-id="b4882-110">You can then apply the mining model to new data, in business scenarios such as these:</span></span>  
  
-   <span data-ttu-id="b4882-111">Usar tendencias anteriores para predecir las ventas del siguiente trimestre, los requisitos de inventario o la satisfacción de los clientes.</span><span class="sxs-lookup"><span data-stu-id="b4882-111">Use past trends to forecast sales for the next quarter, inventory requirements, or customer satisfaction.</span></span>  
  
-   <span data-ttu-id="b4882-112">Aplicar el conocimiento de los clientes actuales para generar perfiles de nuevos clientes y recomendar nuevos productos o oportunidades.</span><span class="sxs-lookup"><span data-stu-id="b4882-112">Apply knowledge of current customers to profile new customers and recommend new products or opportunities.</span></span>  
  
-   <span data-ttu-id="b4882-113">Buscar correlaciones entre eventos pasados para predecir los errores o el tiempo de inactividad del servidor.</span><span class="sxs-lookup"><span data-stu-id="b4882-113">Find correlations among past events to predict server failures or downtime.</span></span>  
  
-   <span data-ttu-id="b4882-114">Analizar qué productos adquieren juntos los clientes y usar la información para recomendar paquetes o planear la posición de los productos.</span><span class="sxs-lookup"><span data-stu-id="b4882-114">Analyze which products customers purchase together and use the information to recommend bundles or plan product placement.</span></span>  
  
 <span data-ttu-id="b4882-115">El método de análisis que elija dependerá de los objetivos.</span><span class="sxs-lookup"><span data-stu-id="b4882-115">The method of analysis you choose depends on your goals.</span></span> <span data-ttu-id="b4882-116">Los Complementos de minería de datos admiten estos tipos de análisis:</span><span class="sxs-lookup"><span data-stu-id="b4882-116">The Data Mining Add-ins support these types of analysis:</span></span>  
  
-   <span data-ttu-id="b4882-117">Aprendizaje supervisado y no supervisado</span><span class="sxs-lookup"><span data-stu-id="b4882-117">Supervised and unsupervised learning</span></span>  
  
-   <span data-ttu-id="b4882-118">Agrupación en clústeres (segmentación)</span><span class="sxs-lookup"><span data-stu-id="b4882-118">Clustering (segmentation)</span></span>  
  
-   <span data-ttu-id="b4882-119">Análisis factorial, utilizando redes bayesianas y neuronales</span><span class="sxs-lookup"><span data-stu-id="b4882-119">Factor analysis, using Bayesian and neural networks</span></span>  
  
-   <span data-ttu-id="b4882-120">Análisis de series temporales</span><span class="sxs-lookup"><span data-stu-id="b4882-120">Time series analysis</span></span>  
  
-   <span data-ttu-id="b4882-121">Análisis de asociación, análisis de recomendaciones y análisis de la cesta de compras</span><span class="sxs-lookup"><span data-stu-id="b4882-121">Association analysis, recommendations, and shopping basket analysis</span></span>  
  
-   <span data-ttu-id="b4882-122">Resultados binarios de puntuación</span><span class="sxs-lookup"><span data-stu-id="b4882-122">Scoring binary outcomes</span></span>  
  
-   <span data-ttu-id="b4882-123">Regresión lineal</span><span class="sxs-lookup"><span data-stu-id="b4882-123">Linear regression</span></span>  
  
 <span data-ttu-id="b4882-124">Además, los complementos ayudan en la fase de preparación de datos: selección de datos, exploración y limpieza de datos.</span><span class="sxs-lookup"><span data-stu-id="b4882-124">In addition, the add-ins provide help the data preparation phase: data selection, exploration, and data cleansing.</span></span>  
  
## <a name="define-your-goal"></a><span data-ttu-id="b4882-125">Definir el objetivo</span><span class="sxs-lookup"><span data-stu-id="b4882-125">Define Your Goal</span></span>  
 <span data-ttu-id="b4882-126">Antes de empezar, dedique un par de minutos a considerar cuál es la pregunta a la que verdaderamente quiere dar una respuesta.</span><span class="sxs-lookup"><span data-stu-id="b4882-126">Before you get started, take a minute to consider the question you really want to answer.</span></span> <span data-ttu-id="b4882-127">La exploración en sí misma es reveladora, pero si desea aplicar sus hallazgos a nuevos datos, debe ser capaz de indicar claramente qué espera que genere el modelo y cómo medirá si el modelo logra los objetivos.</span><span class="sxs-lookup"><span data-stu-id="b4882-127">Exploration for its own sake is illuminating, but if you want to apply your findings to new data, you should be able to state clearly what you expect the model to produce, and how you will measure whether the model accomplishes your goals.</span></span>  
  
 <span data-ttu-id="b4882-128">Por ejemplo, en lugar de un objetivo de "buscar nuevos clientes", aclare su objetivo a algo más concreto, como "identificar los datos demográficos de los clientes que es probable que compren nuestro producto, con una probabilidad de al menos el 65%".</span><span class="sxs-lookup"><span data-stu-id="b4882-128">For example, rather than a goal of "finding new customers", clarify your objective to something more concrete, such as "identify the demographics of customers that are likely to buy our product, with a probability of at least 65%".</span></span>  
  
-   <span data-ttu-id="b4882-129">El conjunto de resultados debe contener al menos un atributo "result" que pueda usar para el entrenamiento y la predicción.</span><span class="sxs-lookup"><span data-stu-id="b4882-129">Your dataset should contain at least one "result" attribute that you can use for training and prediction.</span></span> <span data-ttu-id="b4882-130">Si no existe ese tipo de atributo, puede etiquetar manualmente algunos datos de entrenamiento o usar otras columnas para crear un proxy para el resultado.</span><span class="sxs-lookup"><span data-stu-id="b4882-130">If there is no such attribute, you can manually label some training data, or use other columns to create a proxy for the outcome.</span></span>  
  
     <span data-ttu-id="b4882-131">Por ejemplo, si desea predecir "las mejores perspectivas", debe aplicar alguna regla de negocios antes de etiquetar a los clientes existentes para que la minería de datos pueda aprender de los ejemplos proporcionados.</span><span class="sxs-lookup"><span data-stu-id="b4882-131">For example, if you want to predict "the best prospects", you should apply some business rule beforehand to label existing customers, so that data mining can learn from the examples you provide.</span></span>  
  
-   <span data-ttu-id="b4882-132">Si trabaja con un valor que cambia con el paso del tiempo y desea predecir las tendencias futuras, piense en cuál va a ser la granularidad de los resultados que necesita.</span><span class="sxs-lookup"><span data-stu-id="b4882-132">If you are working with a value that changes over time, and want to predict future trends, think about the granularity of the results you need.</span></span> <span data-ttu-id="b4882-133">¿Desea que las predicciones se realicen diaria, mensual o anualmente?</span><span class="sxs-lookup"><span data-stu-id="b4882-133">Do you want predictions for a month, day, or yearly basis?</span></span> <span data-ttu-id="b4882-134">Los datos tienen que analizarse con las mismas unidades que desea predecir.</span><span class="sxs-lookup"><span data-stu-id="b4882-134">Your data has to be analyzed using the same units that you want to predict.</span></span>  
  
     <span data-ttu-id="b4882-135">Con patrones cíclicos, si no obtiene buenos resultados con datos diarios, pruebe diferentes intervalos de tiempo o intente usar días de la semana, meses o incluso festivos.</span><span class="sxs-lookup"><span data-stu-id="b4882-135">With cyclical patterns, if you don't get good results with daily data, try different time slices, or try using week days, months, or even holidays.</span></span>  
  
-   <span data-ttu-id="b4882-136">Antes de iniciar un asistente para encontrar correlaciones nuevas en los datos, examine una vez más los datos y considere qué clase de relaciones existentes podría haber en el conjunto de datos.</span><span class="sxs-lookup"><span data-stu-id="b4882-136">Before you launch a wizard to find new correlations in your data, take one more look at your data and consider what sort of existing relationships might be present in the dataset.</span></span> <span data-ttu-id="b4882-137">¿Hay variables poco claras?</span><span class="sxs-lookup"><span data-stu-id="b4882-137">Are there confounding variables?</span></span> <span data-ttu-id="b4882-138">¿Hay duplicados o servidores proxy?</span><span class="sxs-lookup"><span data-stu-id="b4882-138">Are there duplicates or proxies?</span></span>  
  
-   <span data-ttu-id="b4882-139">¿Cuáles son las métricas por las que se evaluará el éxito del modelo?</span><span class="sxs-lookup"><span data-stu-id="b4882-139">What are the metrics by which the model's success will be evaluated?</span></span> <span data-ttu-id="b4882-140">¿Cómo sabrá que el modelo es "lo suficientemente bueno"?</span><span class="sxs-lookup"><span data-stu-id="b4882-140">How will you know that the model is "good enough"?</span></span>  
  
-   <span data-ttu-id="b4882-141">¿Desea realizar predicciones a partir del modelo de minería de datos o sólo buscar asociaciones y patrones interesantes?</span><span class="sxs-lookup"><span data-stu-id="b4882-141">Do you want to make predictions from the data mining model or just look for interesting patterns and associations?</span></span>  
  
## <a name="explore-your-data-and-explore-the-model"></a><span data-ttu-id="b4882-142">Explorar los datos y explorar el modelo</span><span class="sxs-lookup"><span data-stu-id="b4882-142">Explore Your Data and Explore the Model</span></span>  
 <span data-ttu-id="b4882-143">Quizás ya tenga un conocimiento profundo de los datos y el dominio.</span><span class="sxs-lookup"><span data-stu-id="b4882-143">Perhaps you already thoroughly understand the data and the domain.</span></span> <span data-ttu-id="b4882-144">Incluso aunque lo tenga, debe dedicar cierto tiempo a generar perfiles de los datos teniendo en cuenta el modelado.</span><span class="sxs-lookup"><span data-stu-id="b4882-144">Even if you do, you should take some time to profile your data with modeling in mind.</span></span>  
  
 <span data-ttu-id="b4882-145">Dedique un minuto a ver la distribución de valores e identificar posibles problemas como valores o marcadores de posición ausentes.</span><span class="sxs-lookup"><span data-stu-id="b4882-145">Take a minute to view the distribution of values, and identify potential problems such as missing values or placeholders.</span></span>  
  
 <span data-ttu-id="b4882-146">Si tiene previsto realizar la minería de datos en un conjunto de datos demasiado grande o complejo que no se pudo analizar con otros métodos, considere la posibilidad de usar el muestreo o la reducción de los datos.</span><span class="sxs-lookup"><span data-stu-id="b4882-146">If you are planning to perform data mining against a data set that was so large or complex that you couldn't analyze it with other methods, consider sampling or data reduction.</span></span>  
  
-   <span data-ttu-id="b4882-147">¿Cómo se distribuyen los datos?</span><span class="sxs-lookup"><span data-stu-id="b4882-147">How is the data distributed?</span></span>  
  
-   <span data-ttu-id="b4882-148">¿Cómo se relacionan las columnas? o en caso de haber varias tablas, ¿cómo se relacionan las tablas?</span><span class="sxs-lookup"><span data-stu-id="b4882-148">How are the columns related, or if there are multiple tables, how are the tables related?</span></span>  
  
-   <span data-ttu-id="b4882-149">¿Falta algún valor?</span><span class="sxs-lookup"><span data-stu-id="b4882-149">Are any values missing?</span></span> <span data-ttu-id="b4882-150">¿Hay valores que necesitan convertirse o procesarse previamente?</span><span class="sxs-lookup"><span data-stu-id="b4882-150">Are there values that need conversion or preprocessing?</span></span>  
  
-   <span data-ttu-id="b4882-151">¿Los datos son sobre todo texto, mayormente números o una combinación de texto y números?</span><span class="sxs-lookup"><span data-stu-id="b4882-151">Is the data mostly text, mostly numbers, or a mix?</span></span>  
  
-   <span data-ttu-id="b4882-152">¿Dispone de datos suficientes para analizar los resultados de destino?</span><span class="sxs-lookup"><span data-stu-id="b4882-152">Do you have enough data to support analysis of the targeted outcomes?</span></span> <span data-ttu-id="b4882-153">Si va a analizar asociaciones entre productos, seguramente necesite muchos datos más.</span><span class="sxs-lookup"><span data-stu-id="b4882-153">If you are analyzing associations among products, you might need lots more data.</span></span> <span data-ttu-id="b4882-154">Cuando se predicen resultados binarios, son necesarios muchos menos datos, siempre y cuando el conjunto de datos esté equilibrado.</span><span class="sxs-lookup"><span data-stu-id="b4882-154">If you are predicting a binary outcome, you can get by with much less, assuming the dataset is balanced.</span></span>  
  
 <span data-ttu-id="b4882-155">Una vez completado el modelo, dedique un tiempo a revisar los resultados e identifique maneras de modificar datos u obtener mejores resultados.</span><span class="sxs-lookup"><span data-stu-id="b4882-155">After your model is complete, take some time to review the results and identify ways to amend the data or get better results.</span></span> <span data-ttu-id="b4882-156">Es excepcionalmente raro que el primer modelo proporcione todas las respuestas.</span><span class="sxs-lookup"><span data-stu-id="b4882-156">It is exceedingly rare that your first model provides all the answers.</span></span> <span data-ttu-id="b4882-157">La minería de datos suele ser un proceso iterativo.</span><span class="sxs-lookup"><span data-stu-id="b4882-157">Data mining is typically an iterative process.</span></span>  
  
 <span data-ttu-id="b4882-158">Al intentar discretización los datos de distintas maneras o agregar nuevas columnas, recuerde usar el Asistente para **documentar modelo** para capturar una instantánea de los metadatos y los resultados de cada modelo.</span><span class="sxs-lookup"><span data-stu-id="b4882-158">As you try binning your data different ways, or adding new columns, remember to use the **Document Model** wizard to capture a snapshot of each model's metadata and results.</span></span> <span data-ttu-id="b4882-159">El hecho de tener un registro facilitará el seguimiento del progreso en la exploración.</span><span class="sxs-lookup"><span data-stu-id="b4882-159">Having a record will make it easier to track progress in your exploration.</span></span>  
  
 [<span data-ttu-id="b4882-160">Explorar y limpiar datos</span><span class="sxs-lookup"><span data-stu-id="b4882-160">Exploring and Cleaning Data</span></span>](exploring-and-cleaning-data.md)  
  
## <a name="validate-your-model"></a><span data-ttu-id="b4882-161">Validar el modelo</span><span class="sxs-lookup"><span data-stu-id="b4882-161">Validate Your Model</span></span>  
 <span data-ttu-id="b4882-162">A medida que se ejecuta cada asistente o herramienta, el algoritmo analiza el contenido de los datos y determina si existe un patrón estadísticamente válido.</span><span class="sxs-lookup"><span data-stu-id="b4882-162">As you run each wizard or tool, the algorithm analyzes the contents of the data and determines whether a statistically valid pattern exists.</span></span> <span data-ttu-id="b4882-163">Si el algoritmo no encuentra patrones válidos, aparecerá un mensaje de error.</span><span class="sxs-lookup"><span data-stu-id="b4882-163">If the algorithm cannot find valid patterns, you'll get an error message.</span></span> <span data-ttu-id="b4882-164">Sin embargo, aunque un modelo se haya creado correctamente, querrá probar el modelo para ver si valida sus suposiciones.</span><span class="sxs-lookup"><span data-stu-id="b4882-164">However, even if a model was successfully created, you'll want to test the model to see if it validates your assumptions.</span></span> <span data-ttu-id="b4882-165">Puede usar herramientas como el gráfico de [precisión &#40;SQL Server complementos de minería de datos&#41;](accuracy-chart-sql-server-data-mining-add-ins.md) o la [validación cruzada &#40;SQL Server](cross-validation-sql-server-data-mining-add-ins.md) complementos de minería de datos&#41;para generar medidas estadísticas de calidad del modelo.</span><span class="sxs-lookup"><span data-stu-id="b4882-165">You can use tools such as the [Accuracy Chart &#40;SQL Server Data Mining Add-ins&#41;](accuracy-chart-sql-server-data-mining-add-ins.md) or [Cross-Validation &#40;SQL Server Data Mining Add-ins&#41;](cross-validation-sql-server-data-mining-add-ins.md) to produce statistical measures of model quality.</span></span>  
  
 <span data-ttu-id="b4882-166">Cuando evalúe los resultados del primer modelo, hágase preguntas como estas:</span><span class="sxs-lookup"><span data-stu-id="b4882-166">As you assess the results of your first model, ask yourself questions such as these:</span></span>  
  
-   <span data-ttu-id="b4882-167">¿Qué tipos de patrones se han encontrado?</span><span class="sxs-lookup"><span data-stu-id="b4882-167">What kinds of patterns were found?</span></span> <span data-ttu-id="b4882-168">¿Cuáles son las probabilidades y los valores de compatibilidad?</span><span class="sxs-lookup"><span data-stu-id="b4882-168">What are the probabilities and support values?</span></span>  
  
-   <span data-ttu-id="b4882-169">¿Eran correctas las suposiciones acerca de las tendencias, o había correlaciones inesperadas?</span><span class="sxs-lookup"><span data-stu-id="b4882-169">Were our guesses about trends correct, or were there surprising correlations?</span></span>  
  
-   <span data-ttu-id="b4882-170">¿Recopilamos suficientes datos?</span><span class="sxs-lookup"><span data-stu-id="b4882-170">Did we collect enough data?</span></span> <span data-ttu-id="b4882-171">¿Produciría la discretización de los datos patrones más claros?</span><span class="sxs-lookup"><span data-stu-id="b4882-171">Would binning the data produce clearer patterns?</span></span>  
  
-   <span data-ttu-id="b4882-172">¿Está equilibrado el conjunto de datos?</span><span class="sxs-lookup"><span data-stu-id="b4882-172">Is the data set balanced?</span></span> <span data-ttu-id="b4882-173">La validación cruzada puede probar la representatividad de los datos.</span><span class="sxs-lookup"><span data-stu-id="b4882-173">Cross-validation can test the representativeness of your data.</span></span>  
  
 [<span data-ttu-id="b4882-174">Herramientas de análisis de tabla para Excel</span><span class="sxs-lookup"><span data-stu-id="b4882-174">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)  
  
 [<span data-ttu-id="b4882-175">Cliente de minería de datos para Excel &#40;SQL Server complementos de minería de datos&#41;</span><span class="sxs-lookup"><span data-stu-id="b4882-175">Data Mining Client for Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](data-mining-client-for-excel-sql-server-data-mining-add-ins.md)  
  
 [<span data-ttu-id="b4882-176">Elegir un modelo</span><span class="sxs-lookup"><span data-stu-id="b4882-176">Choosing a Model</span></span>](choosing-a-model.md)  
  
## <a name="explore-and-refine"></a><span data-ttu-id="b4882-177">Explorar y refinar</span><span class="sxs-lookup"><span data-stu-id="b4882-177">Explore and Refine</span></span>  
 <span data-ttu-id="b4882-178">Si el modelo parece ser válido, puede usarlo para realizar predicciones y recomendaciones, derivar percepciones o planear estrategias empresariales.</span><span class="sxs-lookup"><span data-stu-id="b4882-178">If the model appears to be valid, you can use the model for prediction, recommendation, deriving insights, or planning business strategies..</span></span>  
  
-   <span data-ttu-id="b4882-179">Use el explorador de minería de datos del Cliente de minería de datos para Excel con el fin de explorar e interactuar con el modelo.</span><span class="sxs-lookup"><span data-stu-id="b4882-179">Use the data mining browser in the Data Mining Client for Excel to explore and interact with the model.</span></span>  
  
-   <span data-ttu-id="b4882-180">Use Excel para reorganizar y filtrar los resultados.</span><span class="sxs-lookup"><span data-stu-id="b4882-180">Use Excel to rearrange and filter the results.</span></span>  
  
-   <span data-ttu-id="b4882-181">Use Visio para crear presentaciones y resaltar las relaciones que se encuentran en los datos.</span><span class="sxs-lookup"><span data-stu-id="b4882-181">Use Visio to create presentations and highlight the relationships found in the data.</span></span>  
  
 <span data-ttu-id="b4882-182">A menudo, el primer resultado del análisis es la percepción de que existen formas de mejorar el análisis o de que es necesario obtener nuevos y mejores datos.</span><span class="sxs-lookup"><span data-stu-id="b4882-182">Often, the first result of analysis is that you see ways to improve the analysis, or realize that you need to get new and better data.</span></span> <span data-ttu-id="b4882-183">Dado que los modelos que se crean con los Complementos de minería de datos para Excel se pueden guardar en una instancia de Analysis Service, es relativamente fácil actualizar el modelo con nuevos datos y continuar refinando y reutilizando modelos válidos.</span><span class="sxs-lookup"><span data-stu-id="b4882-183">Because the models that you create using the Data Mining Add-ins for Excel can be saved to an instance of Analysis Service, it is relatively easy to update the model with new data, and continue to refine and re-use successful models.</span></span>  
  
 <span data-ttu-id="b4882-184">Un uso importante de los modelos de minería de datos es la creación de predicciones y recomendaciones.</span><span class="sxs-lookup"><span data-stu-id="b4882-184">An important use of data mining models is to create predictions and recommendations.</span></span> <span data-ttu-id="b4882-185">Los Complementos de minería de datos para Excel incluyen herramientas que facilitan la generación de consultas de predicción complejas para convertir nuevas percepciones en resultados procesables.</span><span class="sxs-lookup"><span data-stu-id="b4882-185">The Data Mining Add-ins for Excel includes tools that make it easy to generate even complex prediction queries, for converting insights into actionable results.</span></span> <span data-ttu-id="b4882-186">Todas estas herramientas están totalmente integradas con Excel.</span><span class="sxs-lookup"><span data-stu-id="b4882-186">All of these tools are fully integrated with Excel.</span></span>  
  
 [<span data-ttu-id="b4882-187">Ver modelos &#40;complementos de minería de datos para Office&#41;</span><span class="sxs-lookup"><span data-stu-id="b4882-187">Viewing Models &#40;Data Mining Add-ins for Office&#41;</span></span>](viewing-models-data-mining-add-ins-for-office.md)  
  
 [<span data-ttu-id="b4882-188">Validar modelos y usar modelos para la predicción &#40;complementos de minería de datos para Excel&#41;</span><span class="sxs-lookup"><span data-stu-id="b4882-188">Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;</span></span>](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
## <a name="see-also"></a><span data-ttu-id="b4882-189">Consulte también</span><span class="sxs-lookup"><span data-stu-id="b4882-189">See Also</span></span>  
 <span data-ttu-id="b4882-190">[Qué se incluye en los complementos de minería de datos para Office](what-s-included-in-the-data-mining-add-ins-for-office.md) </span><span class="sxs-lookup"><span data-stu-id="b4882-190">[What's Included in the Data Mining Add-Ins for Office](what-s-included-in-the-data-mining-add-ins-for-office.md) </span></span>  
 [<span data-ttu-id="b4882-191">Referencia técnica &#40;complementos de minería de datos para Excel&#41;</span><span class="sxs-lookup"><span data-stu-id="b4882-191">Technical Reference &#40;Data Mining Add-ins for Excel&#41;</span></span>](technical-reference-data-mining-add-ins-for-excel.md)  
  
  