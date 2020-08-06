---
title: Tarea Consulta de minería de datos| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingquerytask.f1
helpviewer_keywords:
- prediction queries [Integration Services]
- Data Mining Query task [Integration Services]
ms.assetid: f489348c-2008-4f66-8c2c-c07c3029439a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6bb3cea630401f92395e2ca4416c03bcd870c881
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673850"
---
# <a name="data-mining-query-task"></a><span data-ttu-id="079d1-102">Data Mining Query Task</span><span class="sxs-lookup"><span data-stu-id="079d1-102">Data Mining Query Task</span></span>
  <span data-ttu-id="079d1-103">La tarea Consulta de minería de datos ejecuta consultas de predicción basadas en modelos de minería de datos integrados en [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="079d1-103">The Data Mining Query task runs prediction queries based on data mining models built in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="079d1-104">La consulta de predicción crea una predicción para datos nuevos a partir de modelos de minería de datos.</span><span class="sxs-lookup"><span data-stu-id="079d1-104">The prediction query creates a prediction for new data by using mining models.</span></span> <span data-ttu-id="079d1-105">Por ejemplo, una consulta de predicción puede predecir cuántos barcos de vela es probable vender durante los meses de verano, así como generar una lista de clientes que podrían estar interesados en comprar uno.</span><span class="sxs-lookup"><span data-stu-id="079d1-105">For example, a prediction query can predict how many sailboats are likely to sell during the summer months or generate a list of prospective customers who are likely to buy a sailboat.</span></span>  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="079d1-106">proporciona tareas que realizan otras operaciones de Business Intelligence, como ejecutar instrucciones del lenguaje de definición de datos (DDL) y procesar objetos de análisis.</span><span class="sxs-lookup"><span data-stu-id="079d1-106">provides tasks that perform other business intelligence operations, such as running Data Definition Language (DDL) statements and processing analytic objects.</span></span>  
  
 <span data-ttu-id="079d1-107">Para obtener más información sobre otras tareas de Business Intelligence, haga clic en uno de los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="079d1-107">For more information about other business intelligence tasks, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="079d1-108">Tarea Ejecutar DDL de Analysis Services</span><span class="sxs-lookup"><span data-stu-id="079d1-108">Analysis Services Execute DDL Task</span></span>](analysis-services-execute-ddl-task.md)  
  
-   [<span data-ttu-id="079d1-109">Tarea de procesamiento de Analysis Services</span><span class="sxs-lookup"><span data-stu-id="079d1-109">Analysis Services Processing Task</span></span>](analysis-services-processing-task.md)  
  
## <a name="prediction-queries"></a><span data-ttu-id="079d1-110">Consultas de predicción</span><span class="sxs-lookup"><span data-stu-id="079d1-110">Prediction Queries</span></span>  
 <span data-ttu-id="079d1-111">La consulta es una instrucción de Extensiones de minería de datos (DMX).</span><span class="sxs-lookup"><span data-stu-id="079d1-111">The query is a Data Mining Extensions (DMX) statement.</span></span> <span data-ttu-id="079d1-112">El lenguaje DMX es una extensión del lenguaje SQL que permite trabajar con modelos de minería de datos.</span><span class="sxs-lookup"><span data-stu-id="079d1-112">The DMX language is an extension of the SQL language that provides support for working with mining models.</span></span> <span data-ttu-id="079d1-113">Para más información sobre cómo usar el lenguaje DMX, vea [Referencia de Extensiones de minería de datos &#40;DMX&#41;](/sql/dmx/data-mining-extensions-dmx-reference).</span><span class="sxs-lookup"><span data-stu-id="079d1-113">For more information about how to use the DMX language, see [Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference).</span></span>  
  
 <span data-ttu-id="079d1-114">La tarea puede consultar múltiples modelos de minería de datos generados a partir de la misma estructura de minería de datos.</span><span class="sxs-lookup"><span data-stu-id="079d1-114">The task can query multiple mining models that are built on the same mining structure.</span></span> <span data-ttu-id="079d1-115">Un modelo de minería de datos se construye mediante uno de los algoritmos de minería de datos proporcionados por [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="079d1-115">A mining model is built using one of the data mining algorithms that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides.</span></span> <span data-ttu-id="079d1-116">La estructura de minería de datos a la que hace referencia la tarea Consulta de minería de datos puede incluir múltiples modelos de minería de datos generados con algoritmos diferentes.</span><span class="sxs-lookup"><span data-stu-id="079d1-116">The mining structure that the Data Mining Query task references can include multiple mining models, built using different algorithms.</span></span> <span data-ttu-id="079d1-117">Para más información, vea [Estructuras de minería de datos &#40;Analysis Services - Minería de datos&#41;](https://docs.microsoft.com/analysis-services/data-mining/mining-structures-analysis-services-data-mining) y [Algoritmos de minería de datos &#40;Analysis Services: Minería de datos&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining).</span><span class="sxs-lookup"><span data-stu-id="079d1-117">For more information, see [Mining Structures &#40;Analysis Services - Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/mining-structures-analysis-services-data-mining) and [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining).</span></span>  
  
 <span data-ttu-id="079d1-118">La consulta de predicción ejecutada por la tarea Consulta de minería de datos devuelve como resultado una única fila o un conjunto de datos.</span><span class="sxs-lookup"><span data-stu-id="079d1-118">The prediction query that the Data Mining Query task runs returns a result that is a single row or a data set.</span></span> <span data-ttu-id="079d1-119">Una consulta que devuelve una sola fila se denomina consulta de singleton. Por ejemplo, la consulta que predice cuántos barcos de vela se venderán en los meses de verano produce como resultado un número.</span><span class="sxs-lookup"><span data-stu-id="079d1-119">A query that returns a single row is called a singleton query: for example, the query that predicts how many sailboats will be sold during the summer months returns a number.</span></span> <span data-ttu-id="079d1-120">Para obtener más información acerca de las consultas de predicción que devuelven una única fila, vea [interfaces de consulta de minería de datos](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools).</span><span class="sxs-lookup"><span data-stu-id="079d1-120">For more information about prediction queries that return a single row, see [Data Mining Query Interfaces](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools).</span></span>  
  
 <span data-ttu-id="079d1-121">Los resultados de la consulta se almacenan en tablas.</span><span class="sxs-lookup"><span data-stu-id="079d1-121">The query results are saved to tables.</span></span> <span data-ttu-id="079d1-122">Si ya existe una tabla con el nombre especificado en la tarea Consulta de minería de datos, la tarea puede crear la nueva tabla anexando un número al nombre o sobrescribir el contenido de la tabla existente.</span><span class="sxs-lookup"><span data-stu-id="079d1-122">If a table with the name that the Data Mining Query task specifies already exists, the task can create a new table, using the same name with a number appended, or it can overwrite the table content.</span></span>  
  
 <span data-ttu-id="079d1-123">Si los resultados incluyen anidamientos, se quita información de estructura jerárquica de los resultados antes de guardarlos.</span><span class="sxs-lookup"><span data-stu-id="079d1-123">If the results include nesting, the result is flattened before it is saved.</span></span> <span data-ttu-id="079d1-124">La eliminación de información de estructura jerárquica de los resultados convierte un conjunto de resultados anidados en una tabla.</span><span class="sxs-lookup"><span data-stu-id="079d1-124">Flattening a result changes a nested result set to a table.</span></span> <span data-ttu-id="079d1-125">Por ejemplo, al quitar información de estructura jerárquica de un resultado anidado con una columna **Customer** y una columna anidada **Product** , se agregan filas a la columna **Customer** para crear una tabla que incluya los datos de productos de cada cliente.</span><span class="sxs-lookup"><span data-stu-id="079d1-125">For example, flattening a nested result with a **Customer** column and a nested **Product** column adds rows to the **Customer** column to make a table that includes product data for each customer.</span></span> <span data-ttu-id="079d1-126">Así, por ejemplo, un cliente con tres productos diferentes se convierte en una tabla con tres filas; y cada fila incluirá los datos del cliente y uno de los productos.</span><span class="sxs-lookup"><span data-stu-id="079d1-126">For example, a customer with three different products becomes a table with three rows, repeating the customer in each row and including a different product in each row.</span></span> <span data-ttu-id="079d1-127">Si se omite la palabra clave FLATTENED, la tabla solo contendrá la columna **Customer** y una única fila por cliente.</span><span class="sxs-lookup"><span data-stu-id="079d1-127">If the FLATTENED keyword is omitted, the table contains only the **Customer** column and only one row per customer.</span></span> <span data-ttu-id="079d1-128">Para más información, vea [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx).</span><span class="sxs-lookup"><span data-stu-id="079d1-128">For more information, see [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx).</span></span>  
  
## <a name="configuration-of-the-data-mining-query-task"></a><span data-ttu-id="079d1-129">Configuración de la tarea Consulta de minería de datos</span><span class="sxs-lookup"><span data-stu-id="079d1-129">Configuration of the Data Mining Query Task</span></span>  
 <span data-ttu-id="079d1-130">La tarea Consulta de minería de datos requiere dos conexiones.</span><span class="sxs-lookup"><span data-stu-id="079d1-130">The Data Mining Query task requires two connections.</span></span> <span data-ttu-id="079d1-131">La primera conexión es un administrador de conexiones de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] que se conecta a una instancia de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o a un proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] que contiene la estructura de minería de datos y el modelo de minería de datos.</span><span class="sxs-lookup"><span data-stu-id="079d1-131">The first connection is an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager that connects either to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] or to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project that contains the mining structure and the mining model.</span></span> <span data-ttu-id="079d1-132">La segunda conexión es un administrador de conexiones OLE DB que se conecta a la base de datos de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que contiene la tabla en la que escribe la tarea.</span><span class="sxs-lookup"><span data-stu-id="079d1-132">The second connection is an OLE DB connection manager that connects to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database that contains the table to which the task writes.</span></span> <span data-ttu-id="079d1-133">Para obtener más información, consulte [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md) y [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span><span class="sxs-lookup"><span data-stu-id="079d1-133">For more information, see [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md) and [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="079d1-134">Puede establecer propiedades a través del Diseñador de [!INCLUDE[ssIS](../../../includes/ssis-md.md)] o mediante programación.</span><span class="sxs-lookup"><span data-stu-id="079d1-134">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="079d1-135">Para obtener más información acerca de las propiedades que puede establecer en el Diseñador [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , haga clic en uno de los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="079d1-135">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="079d1-136">Editor de la tarea Consulta de minería de datos &#40;pestaña Modelo de minería de datos&#41;</span><span class="sxs-lookup"><span data-stu-id="079d1-136">Data Mining Query Task Editor &#40;Mining Model Tab&#41;</span></span>](../data-mining-query-task-editor-mining-model-tab.md)  
  
-   [<span data-ttu-id="079d1-137">Editor de la tarea Consulta de minería de datos &#40;pestaña Consulta&#41;</span><span class="sxs-lookup"><span data-stu-id="079d1-137">Data Mining Query Task Editor &#40;Query Tab&#41;</span></span>](../data-mining-query-task-editor-query-tab.md)  
  
-   [<span data-ttu-id="079d1-138">Editor de la tarea Consulta de minería de datos &#40;pestaña Salida&#41;</span><span class="sxs-lookup"><span data-stu-id="079d1-138">Data Mining Query Task Editor &#40;Output Tab&#41;</span></span>](../data-mining-query-task-editor-output-tab.md)  
  
> [!NOTE]  
>  <span data-ttu-id="079d1-139">El Editor de la tarea Consulta de minería de datos no tiene página Expresiones.</span><span class="sxs-lookup"><span data-stu-id="079d1-139">The Data Mining Query Editor has no Expressions page.</span></span> <span data-ttu-id="079d1-140">Utilice en su lugar la ventana **Propiedades** para tener acceso a las herramientas de creación y administración de expresiones de propiedades para las propiedades de la tarea Consulta de minería de datos.</span><span class="sxs-lookup"><span data-stu-id="079d1-140">Instead, use the **Properties** window to access the tools for creating and managing property expressions for properties of the Data Mining Query task.</span></span>  
  
 <span data-ttu-id="079d1-141">Para obtener más información sobre cómo establecer estas propiedades en el Diseñador [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , haga clic en el siguiente tema:</span><span class="sxs-lookup"><span data-stu-id="079d1-141">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="079d1-142">Establecer las propiedades de tareas o contenedores</span><span class="sxs-lookup"><span data-stu-id="079d1-142">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-data-mining-query-task"></a><span data-ttu-id="079d1-143">Configuración mediante programación de la tarea Consulta de minería de datos</span><span class="sxs-lookup"><span data-stu-id="079d1-143">Programmatic Configuration of Data Mining Query Task</span></span>  
 <span data-ttu-id="079d1-144">Para obtener más información sobre cómo establecer estas propiedades mediante programación, haga clic en uno de los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="079d1-144">For more information about programmatically setting these properties, click one of the following topics:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.DMQueryTask.DMQueryTask>  
  
  