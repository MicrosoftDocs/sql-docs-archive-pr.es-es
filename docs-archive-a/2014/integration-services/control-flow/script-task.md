---
title: Tarea Script | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scripttask.f1
helpviewer_keywords:
- scripts [Integration Services], tasks
- Script task [Integration Services], about Script task
- Script task [Integration Services]
ms.assetid: f6cce7df-4bd6-4b75-9f89-6c37b4bb5558
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 69c051994eb06cbab041db3db2683a487a6e1994
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662197"
---
# <a name="script-task"></a><span data-ttu-id="98afa-102">Tarea Script</span><span class="sxs-lookup"><span data-stu-id="98afa-102">Script Task</span></span>
  <span data-ttu-id="98afa-103">La tarea Script proporciona código para realizar funciones que no están disponibles en las tareas integradas ni en las transformaciones proporcionadas por [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="98afa-103">The Script task provides code to perform functions that are not available in the built-in tasks and transformations that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides.</span></span> <span data-ttu-id="98afa-104">La tarea Script también puede combinar funciones en un script, en lugar de usar múltiples tareas y transformaciones.</span><span class="sxs-lookup"><span data-stu-id="98afa-104">The Script task can also combine functions in one script instead of using multiple tasks and transformations.</span></span> <span data-ttu-id="98afa-105">La tarea Script sirve para trabajos que se deben realizar una sola vez en un paquete (o una vez por objeto enumerado), en lugar de una vez por fila de datos.</span><span class="sxs-lookup"><span data-stu-id="98afa-105">You use the Script task for work that must be done once in a package (or once per enumerated object), instead than once per data row.</span></span>  
  
 <span data-ttu-id="98afa-106">Puede usar la tarea Script para los siguientes fines:</span><span class="sxs-lookup"><span data-stu-id="98afa-106">You can use the Script task for the following purposes:</span></span>  
  
-   <span data-ttu-id="98afa-107">Tener acceso a datos mediante otras tecnologías incompatibles con los tipos de conexión integrados.</span><span class="sxs-lookup"><span data-stu-id="98afa-107">Access data by using other technologies that are not supported by built-in connection types.</span></span> <span data-ttu-id="98afa-108">Por ejemplo, un script puede usar interfaces del servicio Active Directory (ADSI) para tener acceso a los nombres de usuario de Active Directory y extraer dichos nombres.</span><span class="sxs-lookup"><span data-stu-id="98afa-108">For example, a script can use Active Directory Service Interfaces (ADSI) to access and extract user names from Active Directory.</span></span>  
  
-   <span data-ttu-id="98afa-109">Crear un contador de rendimiento específico del paquete.</span><span class="sxs-lookup"><span data-stu-id="98afa-109">Create a package-specific performance counter.</span></span> <span data-ttu-id="98afa-110">Por ejemplo, un script puede crear un contador de rendimiento que se actualiza mientras se ejecuta una tarea compleja o de bajo rendimiento.</span><span class="sxs-lookup"><span data-stu-id="98afa-110">For example, a script can create a performance counter that is updated while a complex or poorly performing task runs.</span></span>  
  
-   <span data-ttu-id="98afa-111">Identificar si archivos específicos están vacíos o cuántas filas contienen y luego, en función de esa información, afectar el flujo de control de un paquete.</span><span class="sxs-lookup"><span data-stu-id="98afa-111">Identify whether specified files are empty or how many rows they contain, and then based on that information affect the control flow in a package.</span></span> <span data-ttu-id="98afa-112">Por ejemplo, si un archivo contiene cero filas, el valor de una variable se establece en 0, y una restricción de precedencia que evalúa el valor impide que una tarea Sistema de archivos copie el archivo.</span><span class="sxs-lookup"><span data-stu-id="98afa-112">For example, if a file contains zero rows, the value of a variable set to 0, and a precedence constraint that evaluates the value prevents a File System task from copying the file.</span></span>  
  
 <span data-ttu-id="98afa-113">Si tiene que utilizar el script para hacer el mismo trabajo en cada fila de datos de un conjunto, utilice el componente de script de la tarea Script.</span><span class="sxs-lookup"><span data-stu-id="98afa-113">If you have to use the script to do the same work for each row of data in a set, you should use the Script component instead of the Script task.</span></span> <span data-ttu-id="98afa-114">Por ejemplo, si desea evaluar si un valor de franqueo es razonable y omitir filas de datos con valores extremadamente altos o bajos, utilice un componente de script.</span><span class="sxs-lookup"><span data-stu-id="98afa-114">For example, if you want to assess the reasonableness of a postage amount and skip data rows that have very high or low amounts, you would use a Script component.</span></span> <span data-ttu-id="98afa-115">Para más información, consulte [Script Component](../data-flow/transformations/script-component.md).</span><span class="sxs-lookup"><span data-stu-id="98afa-115">For more information, see [Script Component](../data-flow/transformations/script-component.md).</span></span>  
  
 <span data-ttu-id="98afa-116">Si varios paquetes usan el script, considere la posibilidad de escribir una tarea personalizada en lugar de usar la tarea Script.</span><span class="sxs-lookup"><span data-stu-id="98afa-116">If more than one package uses a script, consider writing a custom task instead of using the Script task.</span></span> <span data-ttu-id="98afa-117">Para más información, vea [Desarrollar una tarea personalizada](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span><span class="sxs-lookup"><span data-stu-id="98afa-117">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
 <span data-ttu-id="98afa-118">Una vez que haya decidido que la tarea Script es la opción adecuada para el paquete, tiene que desarrollar el script que la tarea utiliza y configurar la propia tarea.</span><span class="sxs-lookup"><span data-stu-id="98afa-118">After you decide that the Script task is the appropriate choice for your package, you have to both develop the script that the task uses and configure the task itself.</span></span>  
  
## <a name="writing-and-running-the-script-that-the-task-uses"></a><span data-ttu-id="98afa-119">Escribir y ejecutar el script que la tarea utiliza</span><span class="sxs-lookup"><span data-stu-id="98afa-119">Writing and Running the Script that the Task Uses</span></span>  
 <span data-ttu-id="98afa-120">La tarea Script usa [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools para Aplicaciones (VSTA) como entorno de escritura de los scripts y como motor que los ejecuta.</span><span class="sxs-lookup"><span data-stu-id="98afa-120">The Script task uses [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) as the environment in which you write the scripts and the engine that runs those scripts.</span></span>  
  
 <span data-ttu-id="98afa-121">VSTA proporciona todas las características estándar del entorno [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , como el editor de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] con códigos de color, IntelliSense y el **Explorador de objetos**.</span><span class="sxs-lookup"><span data-stu-id="98afa-121">VSTA provides all the standard features of the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] environment, such as the color-coded [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] editor, IntelliSense, and **Object Explorer**.</span></span> <span data-ttu-id="98afa-122">VSTA también utiliza el mismo depurador que usan otras herramientas de desarrollo de [!INCLUDE[msCoName](../../includes/msconame-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="98afa-122">VSTA also uses the same debugger that other [!INCLUDE[msCoName](../../includes/msconame-md.md)] development tools use.</span></span> <span data-ttu-id="98afa-123">Los puntos de interrupción del script funcionan a la perfección con los puntos de interrupción de las tareas y los contenedores de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="98afa-123">Breakpoints in the script work seamlessly with breakpoints on [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] tasks and containers.</span></span> <span data-ttu-id="98afa-124">VSTA es compatible con los lenguajes de programación [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic y [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.</span><span class="sxs-lookup"><span data-stu-id="98afa-124">VSTA supports both the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# programming languages.</span></span>  
  
 <span data-ttu-id="98afa-125">Para ejecutar un script, debe tener VSTA instalado en el equipo en que se ejecute el paquete.</span><span class="sxs-lookup"><span data-stu-id="98afa-125">To run a script, you must have VSTA installed on the computer where the package runs.</span></span> <span data-ttu-id="98afa-126">Al ejecutar el paquete, la tarea carga el motor de script y ejecuta el script.</span><span class="sxs-lookup"><span data-stu-id="98afa-126">When the package runs, the task loads the script engine and runs the script.</span></span> <span data-ttu-id="98afa-127">Puede tener acceso a ensamblados .NET externos en scripts; para ello, debe agregar referencias a dichos ensamblados en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="98afa-127">You can access external .NET assemblies in scripts by adding references to the assemblies in the project.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98afa-128">A diferencia de las versiones anteriores en las que podía indicar si se precompilaban los scripts, todos los scripts se precompilan en [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="98afa-128">Unlike earlier versions where you could indicate whether the scripts were precompiled, all scripts are precompiled in [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] and later versions.</span></span> <span data-ttu-id="98afa-129">Al precompilar el script, no se carga el motor del lenguaje en tiempo de ejecución, por lo que el paquete se ejecuta con mayor rapidez.</span><span class="sxs-lookup"><span data-stu-id="98afa-129">When a script is precompiled, the language engine is not loaded at run time and the package runs more quickly.</span></span> <span data-ttu-id="98afa-130">Sin embargo, los archivos binarios precompilados utilizan una cantidad considerable de espacio en disco.</span><span class="sxs-lookup"><span data-stu-id="98afa-130">However, precompiled binary files consume significant disk space.</span></span>  
  
## <a name="configuring-the-script-task"></a><span data-ttu-id="98afa-131">Configurar la tarea Script</span><span class="sxs-lookup"><span data-stu-id="98afa-131">Configuring the Script Task</span></span>  
 <span data-ttu-id="98afa-132">Puede configurar la tarea Script de las maneras siguientes:</span><span class="sxs-lookup"><span data-stu-id="98afa-132">You can configure the Script task in the following ways:</span></span>  
  
-   <span data-ttu-id="98afa-133">Proporcionar el script personalizado que ejecuta la tarea.</span><span class="sxs-lookup"><span data-stu-id="98afa-133">Provide the custom script that the task runs.</span></span>  
  
-   <span data-ttu-id="98afa-134">Especifique el método del proyecto de VSTA que el módulo de ejecución de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] llama como punto de entrada en el código de la tarea Script.</span><span class="sxs-lookup"><span data-stu-id="98afa-134">Specify the method in the VSTA project that the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] runtime calls as the entry point into the Script task code.</span></span>  
  
-   <span data-ttu-id="98afa-135">Especificar el lenguaje de script.</span><span class="sxs-lookup"><span data-stu-id="98afa-135">Specify the script language.</span></span>  
  
-   <span data-ttu-id="98afa-136">Opcionalmente, proporcionar listas de variables de solo lectura/lectura y escritura para su uso en el script.</span><span class="sxs-lookup"><span data-stu-id="98afa-136">Optionally, provide lists of read-only and read/write variables for use in the script.</span></span>  
  
 <span data-ttu-id="98afa-137">Puede establecer estas propiedades a través del Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] o mediante programación.</span><span class="sxs-lookup"><span data-stu-id="98afa-137">You can set these properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
### <a name="configuring-the-script-task-in-the-designer"></a><span data-ttu-id="98afa-138">Configurar la tarea Script en el Diseñador</span><span class="sxs-lookup"><span data-stu-id="98afa-138">Configuring the Script Task in the Designer</span></span>  
 <span data-ttu-id="98afa-139">En la tabla siguiente se describe el evento `ScriptTaskLogEntry` que se puede registrar para la tarea Script.</span><span class="sxs-lookup"><span data-stu-id="98afa-139">The following table describes the `ScriptTaskLogEntry` event that can be logged for Script task.</span></span> <span data-ttu-id="98afa-140">El `ScriptTaskLogEntry` evento se selecciona para el registro en la pestaña **detalles** del cuadro de diálogo **configurar registros de SSIS** .</span><span class="sxs-lookup"><span data-stu-id="98afa-140">The `ScriptTaskLogEntry` event is selected for logging on the **Details** tab of the **Configure SSIS Logs** dialog box.</span></span> <span data-ttu-id="98afa-141">Para obtener más información, vea [Registro de Integration Services &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md) y [Mensajes personalizados para registro](../custom-messages-for-logging.md).</span><span class="sxs-lookup"><span data-stu-id="98afa-141">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="98afa-142">Entrada del registro</span><span class="sxs-lookup"><span data-stu-id="98afa-142">Log entry</span></span>|<span data-ttu-id="98afa-143">Descripción</span><span class="sxs-lookup"><span data-stu-id="98afa-143">Description</span></span>|  
|---------------|-----------------|  
|`ScriptTaskLogEntry`|<span data-ttu-id="98afa-144">Informa sobre los resultados de la implementación del registro en el script.</span><span class="sxs-lookup"><span data-stu-id="98afa-144">Reports the results of implementing logging in the script.</span></span> <span data-ttu-id="98afa-145">La tarea escribe una entrada del registro para cada llamada al método `Log` del objeto `Dts`.</span><span class="sxs-lookup"><span data-stu-id="98afa-145">The task writes a log entry for each call to the `Log` method of the `Dts` object.</span></span> <span data-ttu-id="98afa-146">La tarea escribe estas entradas cuando se ejecuta el código.</span><span class="sxs-lookup"><span data-stu-id="98afa-146">The task writes these entries when the code is run.</span></span> <span data-ttu-id="98afa-147">Para más información, consulte [Logging in the Script Task](../extending-packages-scripting/task/logging-in-the-script-task.md).</span><span class="sxs-lookup"><span data-stu-id="98afa-147">For more information, see [Logging in the Script Task](../extending-packages-scripting/task/logging-in-the-script-task.md).</span></span>|  
  
 <span data-ttu-id="98afa-148">Para obtener más información acerca de las propiedades que puede establecer en el Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] , vea los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="98afa-148">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see the following topics:</span></span>  
  
-   [<span data-ttu-id="98afa-149">Editor de la tarea Script &#40;página General&#41;</span><span class="sxs-lookup"><span data-stu-id="98afa-149">Script Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="98afa-150">Editor de la tarea Script &#40;página Script&#41;</span><span class="sxs-lookup"><span data-stu-id="98afa-150">Script Task Editor &#40;Script Page&#41;</span></span>](../script-task-editor-script-page.md)  
  
-   [<span data-ttu-id="98afa-151">Página Expresiones</span><span class="sxs-lookup"><span data-stu-id="98afa-151">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="98afa-152">Para obtener más información sobre cómo establecer estas propiedades en el Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] , vea el siguiente tema:</span><span class="sxs-lookup"><span data-stu-id="98afa-152">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see the following topic:</span></span>  
  
-   [<span data-ttu-id="98afa-153">Establecer las propiedades de tareas o contenedores</span><span class="sxs-lookup"><span data-stu-id="98afa-153">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
### <a name="configuring-the-script-task-programmatically"></a><span data-ttu-id="98afa-154">Configurar la tarea Script mediante programación</span><span class="sxs-lookup"><span data-stu-id="98afa-154">Configuring the Script Task Programmatically</span></span>  
 <span data-ttu-id="98afa-155">Para obtener más información sobre cómo establecer estas propiedades mediante programación, vea el tema siguiente:</span><span class="sxs-lookup"><span data-stu-id="98afa-155">For more information about programmatically setting these properties, see the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask>  
  
## <a name="related-content"></a><span data-ttu-id="98afa-156">Contenido relacionado</span><span class="sxs-lookup"><span data-stu-id="98afa-156">Related Content</span></span>  
  
-   <span data-ttu-id="98afa-157">Artículo técnico [How to send email with delivery notification in C#](https://go.microsoft.com/fwlink/?LinkId=237625)(Enviar un mensaje de correo electrónico con una notificación de entrega en C#) en shareourideas.com</span><span class="sxs-lookup"><span data-stu-id="98afa-157">Technical article, [How to send email with delivery notification in C#](https://go.microsoft.com/fwlink/?LinkId=237625), on shareourideas.com</span></span>  
  
  