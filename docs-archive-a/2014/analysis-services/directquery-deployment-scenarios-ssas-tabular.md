---
title: Escenarios de implementación de DirectQuery (SSAS tabular) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2aaf5cb8-294b-4031-94b3-fe605d7fc4c7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2c90d90b40686b5953e26853ed9f53dcfd157f0f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87677279"
---
# <a name="directquery-deployment-scenarios-ssas-tabular"></a><span data-ttu-id="2c270-102">Escenarios de implementación de DirectQuery (SSAS tabular)</span><span class="sxs-lookup"><span data-stu-id="2c270-102">DirectQuery Deployment Scenarios (SSAS Tabular)</span></span>
  <span data-ttu-id="2c270-103">Este tema proporciona un tutorial del proceso de diseño e implementación para los modelos de DirectQuery.</span><span class="sxs-lookup"><span data-stu-id="2c270-103">This topic provides a walkthrough of the design and deployment process for DirectQuery models.</span></span> <span data-ttu-id="2c270-104">Puede configurar DirectQuery para utilizar solo datos relacionales (solo DirectQuery), o puede configurar el modelo para cambiar entre usar solo datos en caché o solo datos relacionales (modo híbrido).</span><span class="sxs-lookup"><span data-stu-id="2c270-104">You can configure DirectQuery to use relational data only (DirectQuery only), or you can configure the model to switch between using cached data only or relational data only (hybrid mode).</span></span> <span data-ttu-id="2c270-105">En este tema se describe el proceso de implementación para ambos modos, y describe diferencias posibles en los resultados de la consulta dependiendo del modo y configuración de seguridad.</span><span class="sxs-lookup"><span data-stu-id="2c270-105">This topic explains the implementation process for both modes, and describes possible differences in query results depending on the mode and the security configuration.</span></span>  
  
 [<span data-ttu-id="2c270-106">Pasos de diseño e implementación</span><span class="sxs-lookup"><span data-stu-id="2c270-106">Design and Deployment Steps</span></span>](#bkmk_DQProcedure)  
  
 [<span data-ttu-id="2c270-107">Comparar las configuraciones de DirectQuery</span><span class="sxs-lookup"><span data-stu-id="2c270-107">Comparing DirectQuery Configurations</span></span>](#bkmk_Configurations)  
  
##  <a name="design-and-deployment-steps"></a><a name="bkmk_DQProcedure"></a><span data-ttu-id="2c270-108">Pasos de diseño e implementación</span><span class="sxs-lookup"><span data-stu-id="2c270-108">Design and Deployment Steps</span></span>  
 <span data-ttu-id="2c270-109">**Paso 1. Crear la solución**</span><span class="sxs-lookup"><span data-stu-id="2c270-109">**Step 1. Create the solution**</span></span>  
  
 <span data-ttu-id="2c270-110">Independientemente del modo que utilizará, debe revisar la información que describe las limitaciones en los datos que se pueden utilizar en los modelos de DirectQuery.</span><span class="sxs-lookup"><span data-stu-id="2c270-110">Regardless of which mode you will use, you must review the information that describes limitations on the data that can be used in DirectQuery models.</span></span> <span data-ttu-id="2c270-111">Por ejemplo, todos los datos usados en el modelo y los informes deben proceder de una sola base de datos de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2c270-111">For example, all the data used in your model and reports must come from a single SQL Server database.</span></span> <span data-ttu-id="2c270-112">Para más información, vea [Modo DirectQuery &#40;SSAS tabular&#41;](tabular-models/directquery-mode-ssas-tabular.md).</span><span class="sxs-lookup"><span data-stu-id="2c270-112">For more information, see [DirectQuery Mode &#40;SSAS Tabular&#41;](tabular-models/directquery-mode-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="2c270-113">Además, revise las limitaciones de las medidas y columnas calculadas, y determine si las fórmulas que piensa utilizar son compatibles con el modo de DirectQuery.</span><span class="sxs-lookup"><span data-stu-id="2c270-113">Also, review the limitations on measures and calculated columns, and determine whether the formulas you intend to use are compatible with DirectQuery mode.</span></span> <span data-ttu-id="2c270-114">Podría necesitar quitar o modificar los siguientes elementos:</span><span class="sxs-lookup"><span data-stu-id="2c270-114">You might need to remove or modify the following elements:</span></span>  
  
-   <span data-ttu-id="2c270-115">Las columnas calculadas no se admiten.</span><span class="sxs-lookup"><span data-stu-id="2c270-115">Calculated columns are not supported.</span></span>  
  
-   <span data-ttu-id="2c270-116">Los datos copiados-pegados no se pueden utilizar.</span><span class="sxs-lookup"><span data-stu-id="2c270-116">Copy-pasted data cannot be used.</span></span> <span data-ttu-id="2c270-117">Si importa un modelo de PowerPivot para iniciar la solución, asegúrese de eliminar las tablas vinculadas antes de importar la solución, ya que estos datos no se pueden eliminar y bloquearán la validación de DirectQuery.</span><span class="sxs-lookup"><span data-stu-id="2c270-117">If you import a PowerPivot model to jumpstart your solution, be sure to delete linked tables before importing the solution, as this data cannot be deleted and will block DirectQuery validation.</span></span>  
  
 <span data-ttu-id="2c270-118">**Paso 2. Habilitar el modo DirectQuery en el diseñador de modelos**</span><span class="sxs-lookup"><span data-stu-id="2c270-118">**Step 2. Enable DirectQuery mode in the model designer**</span></span>  
  
 <span data-ttu-id="2c270-119">De forma predeterminada, DirectQuery está deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="2c270-119">By default, DirectQuery is disabled.</span></span> <span data-ttu-id="2c270-120">Por tanto, debe configurar el entorno de diseño para admitir el modo de DirectQuery.</span><span class="sxs-lookup"><span data-stu-id="2c270-120">Therefore, you must configure the design environment to support DirectQuery mode.</span></span>  
  
 <span data-ttu-id="2c270-121">Haga clic con el botón secundario en el nodo **Model. BIM** en explorador de soluciones y establezca la propiedad, **modo DirectQuery**, en `On` .</span><span class="sxs-lookup"><span data-stu-id="2c270-121">Right-click the **Model.bim** node in Solution Explorer and set the property, **DirectQuery Mode**, to `On`.</span></span>  
  
 <span data-ttu-id="2c270-122">Puede activar DirectQuery en cualquier momento; sin embargo, para asegurarse de que no crea columnas o fórmulas incompatibles con el modo DirectQuery, se recomienda habilitar el modo DirectQuery desde el principio.</span><span class="sxs-lookup"><span data-stu-id="2c270-122">You can turn on DirectQuery at any time; however, to ensure that you do not create columns or formulas that are incompatible with DirectQuery mode, we recommend that you enable DirectQuery mode right from the beginning.</span></span>  
  
 <span data-ttu-id="2c270-123">Inicialmente, incluso los modelos de DirectQuery se crean siempre en memoria.</span><span class="sxs-lookup"><span data-stu-id="2c270-123">Initially, even DirectQuery models are always created in memory.</span></span> <span data-ttu-id="2c270-124">El modo de consulta predeterminado para la base de datos del área de trabajo también se establece en **DirectQuery con In-Memory**.</span><span class="sxs-lookup"><span data-stu-id="2c270-124">The default query mode for the workspace database is also set to **DirectQuery with In-Memory**.</span></span> <span data-ttu-id="2c270-125">Este modo de funcionamiento híbrido permite utilizar la memoria caché de los datos importados para mejorar el rendimiento durante el proceso de diseño de modelos mientras se valida el modelo con los requisitos de DirectQuery.</span><span class="sxs-lookup"><span data-stu-id="2c270-125">This hybrid working mode lets you use the cache of imported data for improved performance during the model design process, while validating the model against DirectQuery requirements.</span></span>  
  
 <span data-ttu-id="2c270-126">**Paso 3. Resolver errores de validación**</span><span class="sxs-lookup"><span data-stu-id="2c270-126">**Step 3. Resolve validation errors**</span></span>  
  
 <span data-ttu-id="2c270-127">Si obtiene errores de validación al activar DirectQuery, o al agregar nuevos datos o nuevas fórmulas, abra la **Lista de errores**de Visual Studio y tome las medidas necesarias.</span><span class="sxs-lookup"><span data-stu-id="2c270-127">If you get validation errors when you turn DirectQuery on, or when you add new data or formulas, open the Visual Studio **Error List**, and then take the required actions.</span></span>  
  
-   <span data-ttu-id="2c270-128">Cambie los valores de las propiedades requeridos para el modo DirectQuery, tal como se describe en los mensajes de error.</span><span class="sxs-lookup"><span data-stu-id="2c270-128">Change any required property settings for DirectQuery mode, as described in the error messages.</span></span>  
  
-   <span data-ttu-id="2c270-129">Quite las columnas calculadas.</span><span class="sxs-lookup"><span data-stu-id="2c270-129">Remove calculated columns.</span></span> <span data-ttu-id="2c270-130">Si necesita una columna calculada para una medida determinada, siempre puede crear la columna mediante el diseñador de [consultas relacionales &#40;SSAS&#41;](relational-query-designer-ssas.md) proporcionado en el Asistente para la importación de tablas.</span><span class="sxs-lookup"><span data-stu-id="2c270-130">If you require a calculated column for a particular measure, you can always create the column by using the [Relational Query Designer &#40;SSAS&#41;](relational-query-designer-ssas.md) provided in the Table Import wizard.</span></span>  
  
-   <span data-ttu-id="2c270-131">Modifique o quite las fórmulas incompatibles con el modo DirectQuery.</span><span class="sxs-lookup"><span data-stu-id="2c270-131">Modify or remove formulas that are incompatible with DirectQuery mode.</span></span> <span data-ttu-id="2c270-132">Si necesita una determinada función para un cálculo, considere las posibles formas de proporcionar un equivalente usando Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="2c270-132">If you require a particular function for a calculation, consider ways that you could provide an equivalent by using Transact-SQL.</span></span>  
  
-   <span data-ttu-id="2c270-133">Agregue datos según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="2c270-133">Add data as needed.</span></span>  <span data-ttu-id="2c270-134">Si el modelo utilizaba anteriormente datos de copiar y pegar o datos de proveedores distintos de SQL Server, puede crear nuevas vistas y columnas derivadas dentro de la conexión existente, o utilizar consultas distribuidas.</span><span class="sxs-lookup"><span data-stu-id="2c270-134">If your model previously used copy-paste data or data from providers other than SQL Server, you can create new views and derived columns within the existing connection, or use distributed queries.</span></span>  <span data-ttu-id="2c270-135">Todos los datos utilizados en un modelo de DirectQuery deben ser accesibles a través de un único origen de datos de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2c270-135">All data used in a DirectQuery model must be accessible via a single SQL Server data source.</span></span>  
  
 <span data-ttu-id="2c270-136">**Paso 4. Establecer el método preferido para responder a las consultas en el modelo**</span><span class="sxs-lookup"><span data-stu-id="2c270-136">**Step 4. Set the preferred method for answering queries on the model**</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2c270-137">**Solo DirectQuery**</span><span class="sxs-lookup"><span data-stu-id="2c270-137">**DirectQuery only**</span></span>|<span data-ttu-id="2c270-138">Establezca la propiedad en **DirectQuery**.</span><span class="sxs-lookup"><span data-stu-id="2c270-138">Set the property to **DirectQuery**.</span></span>|  
|<span data-ttu-id="2c270-139">**Modo híbrido**</span><span class="sxs-lookup"><span data-stu-id="2c270-139">**Hybrid mode**</span></span>|<span data-ttu-id="2c270-140">Establezca la propiedad en **In-Memory con DirectQuery** o en **DirectQuery con In-Memory**.</span><span class="sxs-lookup"><span data-stu-id="2c270-140">Set the property to **In-Memory With DirectQuery** or **DirectQuery With In-Memory**.</span></span><br /><br /> <span data-ttu-id="2c270-141">Este valor se puede modificar posteriormente para utilizar otra preferencia.</span><span class="sxs-lookup"><span data-stu-id="2c270-141">You can change this value later to use a different preference.</span></span><br /><br /> <span data-ttu-id="2c270-142">Observe que los clientes pueden invalidar el método preferido en la cadena de conexión.</span><span class="sxs-lookup"><span data-stu-id="2c270-142">Note that clients can override the preferred method in the connection string.</span></span>|  
  
 <span data-ttu-id="2c270-143">**Paso 5. Especificar la partición DirectQuery**</span><span class="sxs-lookup"><span data-stu-id="2c270-143">**Step 5. Specify the DirectQuery partition**</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2c270-144">**Solo DirectQuery**</span><span class="sxs-lookup"><span data-stu-id="2c270-144">**DirectQuery only**</span></span>|<span data-ttu-id="2c270-145">Opcional.</span><span class="sxs-lookup"><span data-stu-id="2c270-145">Optional.</span></span> <span data-ttu-id="2c270-146">Un modelo de solo DirectQuery no necesita ninguna partición.</span><span class="sxs-lookup"><span data-stu-id="2c270-146">A DirectQuery only model has no need for a partition.</span></span><br /><br /> <span data-ttu-id="2c270-147">Sin embargo, si ha creado particiones en el modelo durante la fase de diseño, recuerde que solo se puede utilizar una partición como origen de datos.</span><span class="sxs-lookup"><span data-stu-id="2c270-147">However, if you created partitions in the model during the design phase, remember that only one partition can be used as the data source.</span></span> <span data-ttu-id="2c270-148">De forma predeterminada, la primera partición que creó se utilizará como la partición de DirectQuery.</span><span class="sxs-lookup"><span data-stu-id="2c270-148">By default the first partition you created will be used as the DirectQuery partition.</span></span><br /><br /> <span data-ttu-id="2c270-149">Para asegurarse de que todos los datos que necesita el modelo están disponibles en la partición de DirectQuery, elija una partición de DirectQuery y modifique la instrucción SQL para obtener el conjunto de datos completo.</span><span class="sxs-lookup"><span data-stu-id="2c270-149">To ensure that all the data required by the model is available from the DirectQuery partition, choose a DirectQuery partition and edit the SQL statement to get the entire data set.</span></span>|  
|<span data-ttu-id="2c270-150">**Modo híbrido**</span><span class="sxs-lookup"><span data-stu-id="2c270-150">**Hybrid mode**</span></span>|<span data-ttu-id="2c270-151">Si alguna tabla del modelo tiene varias particiones, debe elegir una sola partición como *partición de DirectQuery*.</span><span class="sxs-lookup"><span data-stu-id="2c270-151">If any table in your model has multiple partitions, you must choose a single partition as the *DirectQuery partition*.</span></span> <span data-ttu-id="2c270-152">Si no asigna una partición, la primera partición creada se utilizará, de forma predeterminada, como la partición de DirectQuery.</span><span class="sxs-lookup"><span data-stu-id="2c270-152">If you do not assign a partition, by default, the first partition that was created will be used as the DirectQuery partition.</span></span><br /><br /> <span data-ttu-id="2c270-153">Establezca opciones de procesamiento en todas las particiones salvo en la de DirectQuery.</span><span class="sxs-lookup"><span data-stu-id="2c270-153">Set processing options on all partitions except the DirectQuery.</span></span> <span data-ttu-id="2c270-154">Normalmente, la partición de DirectQuery nunca se procesa, porque los datos se pasan a través del origen relacional.</span><span class="sxs-lookup"><span data-stu-id="2c270-154">Typically the DirectQuery partition is never processed, because the data is passed through from the relational source.</span></span><br /><br /> <span data-ttu-id="2c270-155">Para obtener más información, vea [particiones y el modo DirectQuery &#40;&#41;tabular de SSAS ](tabular-models/define-partitions-in-directquery-models-ssas-tabular.md).</span><span class="sxs-lookup"><span data-stu-id="2c270-155">For more information, see [Partitions and DirectQuery Mode &#40;SSAS Tabular&#41;](tabular-models/define-partitions-in-directquery-models-ssas-tabular.md).</span></span>|  
  
 <span data-ttu-id="2c270-156">**Paso 6. Configurar la suplantación**</span><span class="sxs-lookup"><span data-stu-id="2c270-156">**Step 6. Configure impersonation**</span></span>  
  
 <span data-ttu-id="2c270-157">La suplantación solo se admite en los modelos DirectQuery.</span><span class="sxs-lookup"><span data-stu-id="2c270-157">Impersonation is supported only for DirectQuery models.</span></span> <span data-ttu-id="2c270-158">La opción de suplantación **Configuración de suplantación**define las credenciales que se utilizan al ver los datos del origen de datos de SQL Server especificado.</span><span class="sxs-lookup"><span data-stu-id="2c270-158">The impersonation option, **Impersonation Settings**, defines the credentials that are used when viewing data from the specified SQL Server data source.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2c270-159">**Solo DirectQuery**</span><span class="sxs-lookup"><span data-stu-id="2c270-159">**DirectQuery only**</span></span>|<span data-ttu-id="2c270-160">En la propiedad  **Configuración de suplantación** , especifique la cuenta que se utilizará para conectar con el origen de datos de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2c270-160">For the  **Impersonation Settings** property, specify the account that will be used to connect to the SQL Server data source.</span></span><br /><br /> <span data-ttu-id="2c270-161">Si utiliza el valor **ImpersonateCurrentUser**, la instancia de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] que hospeda el modelo pasará las credenciales del usuario actual del modelo a la base de datos de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2c270-161">If you use the value, **ImpersonateCurrentUser**, the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that hosts the model will pass the credentials of the current user of the model to the SQL Server database.</span></span>|  
|<span data-ttu-id="2c270-162">**Modo híbrido**</span><span class="sxs-lookup"><span data-stu-id="2c270-162">**Hybrid mode**</span></span>|<span data-ttu-id="2c270-163">En la propiedad **Configuración de suplantación** , especifique la cuenta que se utilizará para acceder a los datos del origen de datos de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2c270-163">For the **Impersonation Settings** property, specify the account that will be used to access the data in the SQL Server data source.</span></span><br /><br /> <span data-ttu-id="2c270-164">Esta configuración no afecta a las credenciales utilizadas para procesar la memoria caché usada por el modelo.</span><span class="sxs-lookup"><span data-stu-id="2c270-164">This setting does not affect the credentials that are used to process the cache used by the model.</span></span>|  
  
 <span data-ttu-id="2c270-165">**Paso 7. Implementar el modelo**</span><span class="sxs-lookup"><span data-stu-id="2c270-165">**Step 7. Deploy the model**</span></span>  
  
 <span data-ttu-id="2c270-166">Cuando esté listo para implementar el modelo, abra el menú **proyecto** de Visual Studio y seleccione **propiedades**.</span><span class="sxs-lookup"><span data-stu-id="2c270-166">When you are ready to deploy the model, open the **Project** menu of Visual Studio, and select **Properties**.</span></span> <span data-ttu-id="2c270-167">Establezca la propiedad de **QueryMode** en uno de los valores descritos en la siguiente tabla:</span><span class="sxs-lookup"><span data-stu-id="2c270-167">Set the **QueryMode** property to one of the values described in the following table:</span></span>  
  
 <span data-ttu-id="2c270-168">Para obtener más información, vea [implementar desde SQL Server Data Tools &#40;&#41;tabular de SSAS ](tabular-models/deploy-from-sql-server-data-tools-ssas-tabular.md).</span><span class="sxs-lookup"><span data-stu-id="2c270-168">For more information, see [Deploy From SQL Server Data Tools &#40;SSAS Tabular&#41;](tabular-models/deploy-from-sql-server-data-tools-ssas-tabular.md).</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2c270-169">**Solo DirectQuery**</span><span class="sxs-lookup"><span data-stu-id="2c270-169">**DirectQuery only**</span></span>|<span data-ttu-id="2c270-170">**DirectQueryOnly**</span><span class="sxs-lookup"><span data-stu-id="2c270-170">**DirectQueryOnly**</span></span><br /><br /> <span data-ttu-id="2c270-171">Dado que ha especificado solo Direct Query, los metadatos del modelo se implementarán en el servidor, pero no se procesará el modelo.</span><span class="sxs-lookup"><span data-stu-id="2c270-171">Because you have specified Direct Query only, the metadata of the model is deployed to the server, but the model is not processed.</span></span><br /><br /> <span data-ttu-id="2c270-172">Tenga en cuenta que la memoria caché utilizada por la base de datos del área de trabajo no se eliminará automáticamente.</span><span class="sxs-lookup"><span data-stu-id="2c270-172">Note that the cache that was used by the workspace database is not automatically deleted.</span></span> <span data-ttu-id="2c270-173">Si desea asegurarse de que los usuarios no puedan ver los datos de la memoria caché, borre la caché de tiempo de diseño.</span><span class="sxs-lookup"><span data-stu-id="2c270-173">If you want to ensure that users are not able to see the cached data, you might wish to clear the design-time cache.</span></span> <span data-ttu-id="2c270-174">Para obtener más información, vea [borrar las cachés de Analysis Services](instances/clear-the-analysis-services-caches.md).</span><span class="sxs-lookup"><span data-stu-id="2c270-174">For more information, see [Clear the Analysis Services Caches](instances/clear-the-analysis-services-caches.md).</span></span>|  
|<span data-ttu-id="2c270-175">**Modo híbrido**</span><span class="sxs-lookup"><span data-stu-id="2c270-175">**Hybrid mode**</span></span>|<span data-ttu-id="2c270-176">**DirectQuery con In-Memory**</span><span class="sxs-lookup"><span data-stu-id="2c270-176">**DirectQuery with In-Memory**</span></span><br /><br /> <span data-ttu-id="2c270-177">**In-memory con DirectQuery**</span><span class="sxs-lookup"><span data-stu-id="2c270-177">**In-Memory with DirectQuery**</span></span><br /><br /> <span data-ttu-id="2c270-178">Ambos valores le permiten utilizar la memoria caché o el origen de datos relacional según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="2c270-178">Both of these values allow you to use either the cache or the relational data source as necessary.</span></span> <span data-ttu-id="2c270-179">El orden define el origen de datos que se utiliza de forma predeterminada al responder a las consultas realizadas en el modelo.</span><span class="sxs-lookup"><span data-stu-id="2c270-179">The order defines which data source is used by default when answering queries against the model.</span></span><br /><br /> <span data-ttu-id="2c270-180">En un modo híbrido, la memoria caché se debe procesar al mismo tiempo que los metadatos del modelo se implementan en el servidor.</span><span class="sxs-lookup"><span data-stu-id="2c270-180">In a hybrid mode, the cache must be processed at the same time that the model metadata is deployed to the server.</span></span><br /><br /> <span data-ttu-id="2c270-181">Puede cambiar este valor una vez realizada la implementación.</span><span class="sxs-lookup"><span data-stu-id="2c270-181">You can change this setting after deployment.</span></span>|  
  
 <span data-ttu-id="2c270-182">**Paso 8. Comprobar el modelo implementado**</span><span class="sxs-lookup"><span data-stu-id="2c270-182">**Step 8. Verify deployed model**</span></span>  
  
 <span data-ttu-id="2c270-183">En [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], abra la instancia de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] en la que implementó el modelo.</span><span class="sxs-lookup"><span data-stu-id="2c270-183">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], open the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] where you deployed the model.</span></span> <span data-ttu-id="2c270-184">Haga clic con el botón secundario en el nombre de la base de datos y seleccione **Propiedades**.</span><span class="sxs-lookup"><span data-stu-id="2c270-184">Right-click the name of the database and select **Properties**.</span></span>  
  
-   <span data-ttu-id="2c270-185">La propiedad **DirectQueryMode**se estableció al definir las propiedades de implementación.</span><span class="sxs-lookup"><span data-stu-id="2c270-185">The property, **DirectQueryMode**, was set when you defined the deployment properties.</span></span>  
  
-   <span data-ttu-id="2c270-186">La propiedad **Información de suplantación de origen de datos**se estableció al definir las opciones de suplantación de usuarios.</span><span class="sxs-lookup"><span data-stu-id="2c270-186">The property, **Data Source Impersonation Info**, was set when you defined the user impersonation options.</span></span> <span data-ttu-id="2c270-187">Para más información, vea [Establezca las opciones de suplantación &#40;SSAS - multidimensional&#41;](multidimensional-models/set-impersonation-options-ssas-multidimensional.md).</span><span class="sxs-lookup"><span data-stu-id="2c270-187">For more information, see [Set Impersonation Options &#40;SSAS - Multidimensional&#41;](multidimensional-models/set-impersonation-options-ssas-multidimensional.md).</span></span>  
  
-   <span data-ttu-id="2c270-188">Una vez implementado el modelo, puede cambiar estas propiedades en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="2c270-188">You can change these properties any time after the model has been deployed.</span></span>  
  
##  <a name="comparing-directquery-options"></a><a name="bkmk_Configurations"></a><span data-ttu-id="2c270-189">Comparar las opciones de DirectQuery</span><span class="sxs-lookup"><span data-stu-id="2c270-189">Comparing DirectQuery Options</span></span>  
 <span data-ttu-id="2c270-190">**Solo DirectQuery**</span><span class="sxs-lookup"><span data-stu-id="2c270-190">**DirectQuery Only**</span></span>  
 <span data-ttu-id="2c270-191">Es preferible utilizar esta opción si se desea garantizar un único origen de datos, o si los datos no caben en la memoria.</span><span class="sxs-lookup"><span data-stu-id="2c270-191">This option is preferred when you want to guarantee a single source of data, or when your data is too large to fit in memory.</span></span> <span data-ttu-id="2c270-192">Si trabaja con un origen de datos relacional muy grande, durante el tiempo de diseño puede crear el modelo utilizando un subconjunto de los datos.</span><span class="sxs-lookup"><span data-stu-id="2c270-192">If you are working with a very large relational data source, during design time you can create the model by using some subset of the data.</span></span> <span data-ttu-id="2c270-193">Al implementar el modelo en el modo Solo DirectQuery, puede modificar la definición del origen de datos para incluir todos los datos necesarios.</span><span class="sxs-lookup"><span data-stu-id="2c270-193">When you deploy the model in DirectQuery only mode, you can edit the data source definition to include all the required data.</span></span>  
  
 <span data-ttu-id="2c270-194">También es preferible utilizar esta opción si se desea utilizar la seguridad proporcionada por el origen de datos relacional para controlar el acceso de los usuarios a los datos.</span><span class="sxs-lookup"><span data-stu-id="2c270-194">This option is also preferred if you want to use the security provided by the relational data source to control user access to data.</span></span> <span data-ttu-id="2c270-195">En los modelos tabulares almacenados en caché, también es posible utilizar los roles de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] para controlar el acceso a los datos, pero los datos almacenados en la caché también deben protegerse.</span><span class="sxs-lookup"><span data-stu-id="2c270-195">With cached tabular models, you can also use [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] roles to control data access, but the data stored in the cache must also be secured.</span></span> <span data-ttu-id="2c270-196">Debe utilizar siempre esta opción si el contexto de seguridad requiere que los datos no se almacenen nunca en la memoria caché.</span><span class="sxs-lookup"><span data-stu-id="2c270-196">You should always use this option if your security context requires that data should never be cached.</span></span>  
  
 <span data-ttu-id="2c270-197">En la tabla siguiente se describen los posibles resultados de implementación para el modo Solo DirectQuery:</span><span class="sxs-lookup"><span data-stu-id="2c270-197">The following table describes the possible deployment outcomes for DirectQuery only mode:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2c270-198">**DirectQuery sin caché**</span><span class="sxs-lookup"><span data-stu-id="2c270-198">**DirectQuery with no cache**</span></span>|<span data-ttu-id="2c270-199">No se carga ningún dato en la memoria caché.</span><span class="sxs-lookup"><span data-stu-id="2c270-199">No data is loaded into the cache.</span></span> <span data-ttu-id="2c270-200">El modelo no se podrá procesar nunca.</span><span class="sxs-lookup"><span data-stu-id="2c270-200">The model can never be processed.</span></span><br /><br /> <span data-ttu-id="2c270-201">Solo se podrán realizar consultas en el modelo utilizando clientes compatibles con las consultas DAX.</span><span class="sxs-lookup"><span data-stu-id="2c270-201">The model can only be queried by using clients that support DAX queries.</span></span> <span data-ttu-id="2c270-202">Los resultados de la consulta siempre se devolverán desde el origen de datos original.</span><span class="sxs-lookup"><span data-stu-id="2c270-202">Query results are always returned from the original data source.</span></span><br /><br /> <span data-ttu-id="2c270-203">**DirectQueryMode** = `On`</span><span class="sxs-lookup"><span data-stu-id="2c270-203">**DirectQueryMode** = `On`</span></span><br /><br /> <span data-ttu-id="2c270-204">**QueryMode**  =  **DirectQuery**</span><span class="sxs-lookup"><span data-stu-id="2c270-204">**QueryMode** = **DirectQuery**</span></span>|  
|<span data-ttu-id="2c270-205">**DirectQuery con consultas a la caché únicamente**</span><span class="sxs-lookup"><span data-stu-id="2c270-205">**DirectQuery with queries against cache only**</span></span>|<span data-ttu-id="2c270-206">Se produce un error en la implementación.</span><span class="sxs-lookup"><span data-stu-id="2c270-206">Deployment fails.</span></span> <span data-ttu-id="2c270-207">Esta configuración no se admite.</span><span class="sxs-lookup"><span data-stu-id="2c270-207">This configuration is not supported.</span></span><br /><br /> <span data-ttu-id="2c270-208">**DirectQueryMode** = `On`</span><span class="sxs-lookup"><span data-stu-id="2c270-208">**DirectQueryMode** = `On`</span></span><br /><br /> <span data-ttu-id="2c270-209">**QueryMode**  =  **En memoria**</span><span class="sxs-lookup"><span data-stu-id="2c270-209">**QueryMode** = **In-Memory**</span></span>|  
  
 <span data-ttu-id="2c270-210">**Modo híbrido**</span><span class="sxs-lookup"><span data-stu-id="2c270-210">**Hybrid mode**</span></span>  
 <span data-ttu-id="2c270-211">La implementación del modelo en un modo híbrido tiene muchas ventajas: permite conseguir datos actualizados del origen de datos de SQL Server si es necesario, pero la conservación de la memoria caché le ofrece la posibilidad de trabajar con datos en memoria mientras diseña informes o prueba el modelo, obteniendo un mejor rendimiento.</span><span class="sxs-lookup"><span data-stu-id="2c270-211">Deploying your model in a hybrid mode has many advantages: you can get up-to-date data from the SQL Server data source if needed, but preserving the cache gives you the ability to work with data in memory for faster performance while designing reports or testing the model.</span></span>  
  
 <span data-ttu-id="2c270-212">Un modo híbrido de DirectQuery también es útil si el modelo es muy grande.</span><span class="sxs-lookup"><span data-stu-id="2c270-212">A DirectQuery hybrid mode is also useful if your model is very large.</span></span> <span data-ttu-id="2c270-213">Para evitar que los usuarios obtengan datos obsoletos o que no se pueda utilizar el modelo mientras se procesa la memoria caché, puede cambiar el modelo al modo DirectQuery mientras se realiza el procesamiento.</span><span class="sxs-lookup"><span data-stu-id="2c270-213">Rather than have users get stale data or have the model be unavailable while the cache is processed, you can switch the model to DirectQuery mode while processing is in progress.</span></span> <span data-ttu-id="2c270-214">Es posible que los usuarios experimenten un rendimiento ligeramente inferior, pero podrán conseguir los datos directamente del almacén relacional, evitando así resultados obsoletos.</span><span class="sxs-lookup"><span data-stu-id="2c270-214">Users might experience slightly slower performance but they would be able to get data directly from the relational store, ensuring that results were up-to-date.</span></span>  
  
 <span data-ttu-id="2c270-215">La tabla siguiente compara el resultado de la implementación en cada una de las combinaciones de opciones de DirectQuery.</span><span class="sxs-lookup"><span data-stu-id="2c270-215">The following table compares the deployment outcome in each of the combinations of DirectQuery options.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2c270-216">**Modo híbrido con caché preferida**</span><span class="sxs-lookup"><span data-stu-id="2c270-216">**Hybrid mode with cache preferred**</span></span>|<span data-ttu-id="2c270-217">El modelo se puede procesar y los datos se pueden cargar en la memoria caché.</span><span class="sxs-lookup"><span data-stu-id="2c270-217">The model can be processed and data can be loaded into the cache.</span></span> <span data-ttu-id="2c270-218">Las consultas utilizan la memoria caché de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="2c270-218">Queries use the cache by default.</span></span>  <span data-ttu-id="2c270-219">Si un cliente desea utilizar el origen de datos DirectQuery, se debe insertar un parámetro en la cadena de conexión.</span><span class="sxs-lookup"><span data-stu-id="2c270-219">If a client wants to use the DirectQuery source, a parameter must be inserted in the connection string.</span></span><br /><br /> <span data-ttu-id="2c270-220">**DirectQueryMode** = `On`</span><span class="sxs-lookup"><span data-stu-id="2c270-220">**DirectQueryMode** = `On`</span></span><br /><br /> <span data-ttu-id="2c270-221">**QueryMode**  =  **In-memory con DirectQuery**</span><span class="sxs-lookup"><span data-stu-id="2c270-221">**QueryMode** = **In-Memory with DirectQuery**</span></span>|  
|<span data-ttu-id="2c270-222">**Modo híbrido con DirectQuery preferido**</span><span class="sxs-lookup"><span data-stu-id="2c270-222">**Hybrid mode with DirectQuery preferred**</span></span>|<span data-ttu-id="2c270-223">El modelo se procesa y los datos se pueden cargar en la memoria caché.</span><span class="sxs-lookup"><span data-stu-id="2c270-223">The model is processed and data can be loaded into the cache.</span></span> <span data-ttu-id="2c270-224">Sin embargo, las consultas utilizan DirectQuery de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="2c270-224">However, queries use DirectQuery by default.</span></span> <span data-ttu-id="2c270-225">Si un cliente desea utilizar los datos en caché, se debe insertar un parámetro en la cadena de conexión.</span><span class="sxs-lookup"><span data-stu-id="2c270-225">If a client wants to use the cached data, a parameter must be inserted in the connection string.</span></span> <span data-ttu-id="2c270-226">Si las tablas del modelo se dividen en particiones, la partición principal de la memoria caché también se establece en **In-Memory con DirectQuery**.</span><span class="sxs-lookup"><span data-stu-id="2c270-226">If the tables in the model are partitioned, the principal partition of the cache is also set to **In-Memory with DirectQuery**.</span></span><br /><br /> <span data-ttu-id="2c270-227">**DirectQueryMode** = `On`</span><span class="sxs-lookup"><span data-stu-id="2c270-227">**DirectQueryMode** = `On`</span></span><br /><br /> <span data-ttu-id="2c270-228">**QueryMode**  =  **DirectQuery con in-memory**</span><span class="sxs-lookup"><span data-stu-id="2c270-228">**QueryMode** = **DirectQuery with In-Memory**</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2c270-229">Consulte también</span><span class="sxs-lookup"><span data-stu-id="2c270-229">See Also</span></span>  
 <span data-ttu-id="2c270-230">[Modo DirectQuery &#40;&#41;tabular de SSAS](tabular-models/directquery-mode-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="2c270-230">[DirectQuery Mode &#40;SSAS Tabular&#41;](tabular-models/directquery-mode-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="2c270-231">Acceso a datos de modelos tabulares</span><span class="sxs-lookup"><span data-stu-id="2c270-231">Tabular Model Data Access</span></span>](tabular-models/tabular-model-data-access.md)  
  
  