---
title: Restricciones de precedencia | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- tasks [Integration Services], precedence constraints
- control flow [Integration Services], precedence constraints
- precedence constraints [Integration Services]
- constraints [Integration Services]
- sequence execution options [Integration Services]
- containers [Integration Services], precedence constraints
ms.assetid: c5ce5435-fd89-4156-a11f-68470a69aa9f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7a08fd1d66e43ede4c54284518bab191be8997a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674255"
---
# <a name="precedence-constraints"></a><span data-ttu-id="5617c-102">Restricciones de precedencia</span><span class="sxs-lookup"><span data-stu-id="5617c-102">Precedence Constraints</span></span>
  <span data-ttu-id="5617c-103">Las restricciones de precedencia vinculan ejecutables, contenedores y tareas de paquetes en un flujo de control, y especifican condiciones que determinan si se ejecutan los ejecutables.</span><span class="sxs-lookup"><span data-stu-id="5617c-103">Precedence constraints link executables, containers, and tasks in packages in a control flow, and specify conditions that determine whether executables run.</span></span> <span data-ttu-id="5617c-104">Un ejecutable puede ser un contenedor de bucles For, de bucles Foreach o de secuencia, o bien una tarea o un controlador de eventos.</span><span class="sxs-lookup"><span data-stu-id="5617c-104">An executable can be a For Loop, Foreach Loop, or Sequence container; a task; or an event handler.</span></span> <span data-ttu-id="5617c-105">Los controladores de eventos usan las restricciones de precedencia para vincular sus ejecutables en un flujo de control.</span><span class="sxs-lookup"><span data-stu-id="5617c-105">Event handlers also use precedence constraints to link their executables into a control flow.</span></span>

 <span data-ttu-id="5617c-106">Una restricción de precedencia vincula dos ejecutables: el ejecutable de precedencia y el ejecutable restringido.</span><span class="sxs-lookup"><span data-stu-id="5617c-106">A precedence constraint links two executables: the precedence executable and the constrained executable.</span></span> <span data-ttu-id="5617c-107">El ejecutable de precedencia se ejecuta antes del ejecutable restringido y el resultado de la ejecución del ejecutable de precedencia puede determinar si se ejecuta el ejecutable restringido.</span><span class="sxs-lookup"><span data-stu-id="5617c-107">The precedence executable runs before the constrained executable, and the execution result of the precedence executable may determine whether the constrained executable runs.</span></span> <span data-ttu-id="5617c-108">El siguiente diagrama muestra dos ejecutables vinculados por una restricción de precedencia.</span><span class="sxs-lookup"><span data-stu-id="5617c-108">The following diagram shows two executables linked by a precedence constraint.</span></span>

 <span data-ttu-id="5617c-109">![Ejecutables conectados mediante una restricción de precedencia](../media/ssis-pcsimple.gif "Ejecutables conectados mediante una restricción de precedencia")</span><span class="sxs-lookup"><span data-stu-id="5617c-109">![Executables connected by a precedence constraint](../media/ssis-pcsimple.gif "Executables connected by a precedence constraint")</span></span>

 <span data-ttu-id="5617c-110">En un flujo de control lineal, es decir, un flujo sin bifurcaciones, las restricciones de precedencia controlan ellas mismas la secuencia en que se ejecutan las tareas.</span><span class="sxs-lookup"><span data-stu-id="5617c-110">In a linear control flow, that is, one without branching, precedence constraints alone govern the sequence in which tasks run.</span></span> <span data-ttu-id="5617c-111">Si un flujo de control se bifurca, el motor de tiempo de ejecución de [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] determina el orden de ejecución entre las tareas y contenedores que siguen inmediatamente la bifurcación.</span><span class="sxs-lookup"><span data-stu-id="5617c-111">If a control flow branches, the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] run-time engine determines the execution order among the tasks and containers that immediately follow the branching.</span></span> <span data-ttu-id="5617c-112">El motor de tiempo de ejecución también determina el orden de ejecución entre los flujos de trabajo no conectados en un flujo de control.</span><span class="sxs-lookup"><span data-stu-id="5617c-112">The run-time engine also determines execution order among unconnected workflows in a control flow.</span></span>

 <span data-ttu-id="5617c-113">La arquitectura de contenedor anidado de [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] habilita todos los contenedores, salvo el contenedor del host de la tarea que encapsula una sola tarea, para incluir otros contenedores, cada uno de los cuales tiene su propio flujo de control.</span><span class="sxs-lookup"><span data-stu-id="5617c-113">The nested-container architecture of [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] enables all containers, except for the task host container that encapsulates only a single task, to include other containers, each with its own control flow.</span></span> <span data-ttu-id="5617c-114">Los contenedores de bucles For, de bucles Foreach y de secuencia pueden incluir varias tareas y otros contenedores, que a su vez pueden incluir varias tareas y contenedores.</span><span class="sxs-lookup"><span data-stu-id="5617c-114">The For Loop, Foreach Loop, and Sequence containers can include multiple tasks and other containers, which in turn can include multiple tasks and containers.</span></span> <span data-ttu-id="5617c-115">Por ejemplo, un paquete con una tarea Script y un contenedor de secuencias tiene una restricción de precedencia que vincula la tarea Script y el contenedor de secuencias.</span><span class="sxs-lookup"><span data-stu-id="5617c-115">For example, a package with a Script task and a Sequence container has a precedence constraint that links the Script task and the Sequence container.</span></span> <span data-ttu-id="5617c-116">El contenedor de secuencias incluye tres tareas Script y las restricciones de precedencia vinculan las tres tareas Script en un flujo de control.</span><span class="sxs-lookup"><span data-stu-id="5617c-116">The Sequence container includes three Script tasks, and its precedence constraints link the three Script tasks into a control flow.</span></span> <span data-ttu-id="5617c-117">El siguiente diagrama muestra las restricciones de precedencia en un paquete con dos niveles de anidamiento.</span><span class="sxs-lookup"><span data-stu-id="5617c-117">The following diagram shows the precedence constraints in a package with two levels of nesting.</span></span>

 <span data-ttu-id="5617c-118">![Restricciones de precedencia en un paquete](../media/mw-dts-12.gif "Restricciones de precedencia en un paquete")</span><span class="sxs-lookup"><span data-stu-id="5617c-118">![Precedence contraints in a package](../media/mw-dts-12.gif "Precedence contraints in a package")</span></span>

 <span data-ttu-id="5617c-119">Dado que el paquete se encuentra en la parte superior de la jerarquía de contenedores de [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , no se pueden vincular varios paquetes mediante restricciones de precedencia. Sin embargo, puede agregar una tarea Ejecutar paquete a un paquete y vincular indirectamente otro paquete en el flujo de control.</span><span class="sxs-lookup"><span data-stu-id="5617c-119">Because the package is at the top of the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] container hierarchy, multiple packages cannot be linked by precedence constraints; however, you can add an Execute Package task to a package and indirectly link another package into the control flow.</span></span>

 <span data-ttu-id="5617c-120">Puede configurar las restricciones de precedencia de las siguientes maneras:</span><span class="sxs-lookup"><span data-stu-id="5617c-120">You can configure precedence constraints in the following ways:</span></span>

-   <span data-ttu-id="5617c-121">Especificar una operación de evaluación.</span><span class="sxs-lookup"><span data-stu-id="5617c-121">Specify an evaluation operation.</span></span> <span data-ttu-id="5617c-122">La restricción de precedencia usa un valor de restricción, una expresión, ambas cosas o una de ellas para determinar si se ejecuta el ejecutable restringido.</span><span class="sxs-lookup"><span data-stu-id="5617c-122">The precedence constraint uses a constraint value, an expression, both, or either to determine whether the constrained executable runs.</span></span>

-   <span data-ttu-id="5617c-123">Si la restricción de precedencia usa un resultado de ejecución, puede especificar el resultado de ejecución para que sea correcto, error o conclusión.</span><span class="sxs-lookup"><span data-stu-id="5617c-123">If the precedence constraint uses an execution result, you can specify the execution result to be success, failure, or completion.</span></span>

-   <span data-ttu-id="5617c-124">Si la restricción de precedencia usa un resultado de evaluación, puede proporcionar una expresión que se evalúa como un valor booleano.</span><span class="sxs-lookup"><span data-stu-id="5617c-124">If the precedence constraint uses an evaluation result, you can provide an expression that evaluates to a Boolean.</span></span>

-   <span data-ttu-id="5617c-125">Especificar si la restricción de precedencia se evalúa individualmente o junto con otras restricciones que se aplican al ejecutable restringido.</span><span class="sxs-lookup"><span data-stu-id="5617c-125">Specify whether the precedence constraint is evaluated singly or together with other constraints that apply to the constrained executable.</span></span>

## <a name="evaluation-operations"></a><span data-ttu-id="5617c-126">Operaciones de evaluación</span><span class="sxs-lookup"><span data-stu-id="5617c-126">Evaluation Operations</span></span>
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="5617c-127">proporciona las siguientes operaciones de evaluación:</span><span class="sxs-lookup"><span data-stu-id="5617c-127">provides the following evaluation operations:</span></span>

-   <span data-ttu-id="5617c-128">Una restricción que usa solamente el resultado de la ejecución del ejecutable de precedencia para determinar si el ejecutable restringido se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="5617c-128">A constraint that uses only the execution result of the precedence executable to determine whether the constrained executable runs.</span></span> <span data-ttu-id="5617c-129">El resultado de la ejecución del ejecutable de precedencia puede ser conclusión, correcto o error.</span><span class="sxs-lookup"><span data-stu-id="5617c-129">The execution result of the precedence executable can be completion, success, or failure.</span></span> <span data-ttu-id="5617c-130">Esta es la operación predeterminada.</span><span class="sxs-lookup"><span data-stu-id="5617c-130">This is the default operation.</span></span>

-   <span data-ttu-id="5617c-131">Una expresión que se evalúa para determinar si se ejecuta el ejecutable restringido.</span><span class="sxs-lookup"><span data-stu-id="5617c-131">An expression that is evaluated to determine whether the constrained executable runs.</span></span> <span data-ttu-id="5617c-132">Si la expresión se evalúa como TRUE, el ejecutable restringido se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="5617c-132">If the expression evaluates to true, the constrained executable runs.</span></span>

-   <span data-ttu-id="5617c-133">Una expresión y una restricción que combina los requisitos de los resultados de la ejecución del ejecutable de precedencia y los resultados de devolución de la evaluación de la expresión.</span><span class="sxs-lookup"><span data-stu-id="5617c-133">An expression and a constraint that combines the requirements of execution results of the precedence executable and the return results of evaluating the expression.</span></span>

-   <span data-ttu-id="5617c-134">Una expresión o una restricción que usa los resultados de la ejecución del ejecutable de precedencia o los resultados de devolución de la evaluación de la expresión.</span><span class="sxs-lookup"><span data-stu-id="5617c-134">An expression or a constraint that uses either the execution results of the precedence executable or the return results of evaluating the expression.</span></span>

 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] <span data-ttu-id="5617c-135">usa colores para identificar el tipo de restricción de precedencia.</span><span class="sxs-lookup"><span data-stu-id="5617c-135">Designer uses color to identify the type of precedence constraint.</span></span> <span data-ttu-id="5617c-136">La restricción de operación realizada correctamente es verde, la de error es roja y la de conclusión es azul.</span><span class="sxs-lookup"><span data-stu-id="5617c-136">The Success constraint is green, the Failure constraint is red, and the Completion constraint is blue.</span></span> <span data-ttu-id="5617c-137">Para mostrar etiquetas de texto en el Diseñador [!INCLUDE[ssIS](../../../includes/ssis-md.md)] que muestran el tipo de la restricción, debe configurar las características de accesibilidad del Diseñador [!INCLUDE[ssIS](../../../includes/ssis-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5617c-137">To display text labels in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] designer that show the type of the constraint, you must configure the accessibility features of [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>

 <span data-ttu-id="5617c-138">La expresión debe ser una expresión de [!INCLUDE[ssIS](../../../includes/ssis-md.md)] válida y puede incluir funciones, operadores y variables del sistema y personalizadas.</span><span class="sxs-lookup"><span data-stu-id="5617c-138">The expression must be a valid [!INCLUDE[ssIS](../../../includes/ssis-md.md)] expression, and it can include functions, operators, and system and custom variables.</span></span> <span data-ttu-id="5617c-139">Para obtener más información, vea [Expresiones de Integration Services &#40;SSIS&#41;](../expressions/integration-services-ssis-expressions.md) y [Variables de Integration Services &#40;SSIS&#41;](../integration-services-ssis-variables.md).</span><span class="sxs-lookup"><span data-stu-id="5617c-139">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md) and [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>

## <a name="execution-results"></a><span data-ttu-id="5617c-140">Resultados de la ejecución</span><span class="sxs-lookup"><span data-stu-id="5617c-140">Execution Results</span></span>
 <span data-ttu-id="5617c-141">La restricción de precedencia puede usar los siguientes resultados de ejecución individualmente o combinados con una expresión.</span><span class="sxs-lookup"><span data-stu-id="5617c-141">The precedence constraint can use the following execution results alone or in combination with an expression.</span></span>

-   <span data-ttu-id="5617c-142">La conclusión requiere solamente que el ejecutable de precedencia se haya completado, sin importar su resultado, para que el ejecutable restringido se pueda ejecutar.</span><span class="sxs-lookup"><span data-stu-id="5617c-142">Completion requires only that the precedence executable has completed, without regard to outcome, in order for the constrained executable to run.</span></span>

-   <span data-ttu-id="5617c-143">El resultado correcto requiere que el ejecutable de precedencia se complete correctamente para que pueda ejecutarse el ejecutable restringido.</span><span class="sxs-lookup"><span data-stu-id="5617c-143">Success requires that the precedence executable must complete successfully for the constrained executable to run.</span></span>

-   <span data-ttu-id="5617c-144">El resultado de error requiere que el ejecutable de precedencia genere un error para que pueda ejecutarse el ejecutable restringido.</span><span class="sxs-lookup"><span data-stu-id="5617c-144">Failure requires that the precedence executable fail for the constrained executable to run.</span></span>

> [!NOTE]
>  <span data-ttu-id="5617c-145">Solo las restricciones de precedencia que son miembros de la misma colección `Precedence Constraint` se pueden agrupar en una condición lógica AND.</span><span class="sxs-lookup"><span data-stu-id="5617c-145">Only precedence constraints that are members of the same `Precedence Constraint` collection can be grouped in a logical AND condition.</span></span> <span data-ttu-id="5617c-146">Por ejemplo, no se pueden combinar restricciones de precedencia de dos contenedores de bucles Foreach.</span><span class="sxs-lookup"><span data-stu-id="5617c-146">For example, you cannot combine precedence constraints from two Foreach Loop containers.</span></span>

## <a name="configuration-of-the-precedence-constraint"></a><span data-ttu-id="5617c-147">Configuración de la restricción de precedencia</span><span class="sxs-lookup"><span data-stu-id="5617c-147">Configuration of the Precedence Constraint</span></span>
 <span data-ttu-id="5617c-148">Puede establecer propiedades a través del Diseñador de [!INCLUDE[ssIS](../../../includes/ssis-md.md)] o mediante programación.</span><span class="sxs-lookup"><span data-stu-id="5617c-148">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>

 <span data-ttu-id="5617c-149">Para obtener información sobre las propiedades que se pueden configurar en el Diseñador de [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , vea [Editor de restricciones de precedencia](../precedence-constraint-editor.md).</span><span class="sxs-lookup"><span data-stu-id="5617c-149">For information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, see [Precedence Constraint Editor](../precedence-constraint-editor.md).</span></span>

 <span data-ttu-id="5617c-150">Para obtener información sobre cómo establecer mediante programación estas propiedades, vea <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>.</span><span class="sxs-lookup"><span data-stu-id="5617c-150">For information about programmatically setting these properties, see <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="5617c-151">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="5617c-151">Related Tasks</span></span>
 <span data-ttu-id="5617c-152">Para obtener información detallada sobre cómo establecer estas propiedades en el Diseñador [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , haga clic en uno de los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="5617c-152">For details about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>

-   [<span data-ttu-id="5617c-153">Establecer las propiedades de una restricción de precedencia</span><span class="sxs-lookup"><span data-stu-id="5617c-153">Set the Properties of a Precedence Constraint</span></span>](../set-the-properties-of-a-precedence-constraint.md)

-   [<span data-ttu-id="5617c-154">Establecer el valor de una restricción de precedencia mediante el menú contextual</span><span class="sxs-lookup"><span data-stu-id="5617c-154">Set the Value of a Precedence Constraint by Using the Shortcut Menu</span></span>](../set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md)

-   [<span data-ttu-id="5617c-155">Conectar tareas y contenedores mediante una restricción de precedencia predeterminada</span><span class="sxs-lookup"><span data-stu-id="5617c-155">Connect Tasks and Containers by Using a Default Precedence Constraint</span></span>](../connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)

     <span data-ttu-id="5617c-156">En este tema se ofrece información sobre cómo se configura el comportamiento predeterminado para las restricciones de precedencia y cómo se conectan los ejecutables mediante las restricciones de precedencia predeterminadas.</span><span class="sxs-lookup"><span data-stu-id="5617c-156">This topic provides information on how to set the default behavior for precedence constraints, and how to connect executables using the default precedence constraints, see.</span></span>

## <a name="related-content"></a><span data-ttu-id="5617c-157">Contenido relacionado</span><span class="sxs-lookup"><span data-stu-id="5617c-157">Related Content</span></span>
 <span data-ttu-id="5617c-158">Artículo técnico, sobre [ejemplos de expresiones SSIS](https://go.microsoft.com/fwlink/?LinkId=220761), en social.technet.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="5617c-158">Technical article, [SSIS Expression Examples](https://go.microsoft.com/fwlink/?LinkId=220761), on social.technet.microsoft.com</span></span>

## <a name="see-also"></a><span data-ttu-id="5617c-159">Consulte también</span><span class="sxs-lookup"><span data-stu-id="5617c-159">See Also</span></span>
 <span data-ttu-id="5617c-160">[Agregar expresiones a las restricciones de precedencia](../add-expressions-to-precedence-constraints.md) [varias restricciones de precedencia](../multiple-precedence-constraints.md)</span><span class="sxs-lookup"><span data-stu-id="5617c-160">[Add Expressions to Precedence Constraints](../add-expressions-to-precedence-constraints.md) [Multiple Precedence Constraints](../multiple-precedence-constraints.md)</span></span>

