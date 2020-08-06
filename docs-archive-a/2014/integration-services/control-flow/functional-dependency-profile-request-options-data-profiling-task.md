---
title: Opciones de Solicitud de perfil de dependencia funcional (tarea de generación de perfiles de datos) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 6eb853aa-8016-490c-be4f-06ab8d7f5021
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b6b8446b03bc0d51ad7fbb57526a642e844cc324
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662203"
---
# <a name="functional-dependency-profile-request-options-data-profiling-task"></a><span data-ttu-id="a27e4-102">Opciones de Solicitud de perfil de dependencia funcional (tarea de generación de perfiles de datos)</span><span class="sxs-lookup"><span data-stu-id="a27e4-102">Functional Dependency Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="a27e4-103">Utilice el panel **Propiedades de la solicitud** de la página **Solicitudes de perfil** para establecer las opciones de **Solicitud de perfil de dependencia funcional** seleccionadas en el panel de solicitudes.</span><span class="sxs-lookup"><span data-stu-id="a27e4-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Functional Dependency Profile Request** selected in the requests pane.</span></span> <span data-ttu-id="a27e4-104">Un perfil de dependencia funcional informa de hasta qué punto los valores de una columna (la columna dependiente) dependen de los valores de otra columna o de un conjunto de columnas (la columna determinante).</span><span class="sxs-lookup"><span data-stu-id="a27e4-104">A Functional Dependency profile reports the extent to which the values in one column (the dependent column) depend on the values in another column or set of columns (the determinant column).</span></span> <span data-ttu-id="a27e4-105">Este perfil también puede ayudarle a identificar problemas de los datos, por ejemplo valores que no sean válidos.</span><span class="sxs-lookup"><span data-stu-id="a27e4-105">This profile can also help you identify problems in your data such as invalid values.</span></span> <span data-ttu-id="a27e4-106">Por ejemplo, imagine que genera un perfil de la dependencia entre una columna de código postal y una columna de estados de Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="a27e4-106">For example, you profile the dependency between a Zip Code/Postal Code column and a United States state column.</span></span> <span data-ttu-id="a27e4-107">En este perfil, el mismo código postal debería tener siempre el mismo estado, pero el perfil detecta infracciones de la dependencia.</span><span class="sxs-lookup"><span data-stu-id="a27e4-107">In this profile, the same Zip Code should always have the same state, but the profile discovers violations of the dependency.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a27e4-108">Las opciones que se describen en este tema aparecen en la página **Solicitudes de perfil** del **Editor de tareas de generación de perfiles de datos**.</span><span class="sxs-lookup"><span data-stu-id="a27e4-108">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="a27e4-109">Para obtener más información sobre esta página del editor, vea [Editor de tareas de generación de perfiles de datos &#40;página Solicitudes de perfil&#41;](data-profiling-task-editor-profile-requests-page.md).</span><span class="sxs-lookup"><span data-stu-id="a27e4-109">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="a27e4-110">Para más información sobre cómo usar la tarea de generación de perfiles de datos, vea [Configuración de la Tarea de generación de perfiles de datos](data-profiling-task.md).</span><span class="sxs-lookup"><span data-stu-id="a27e4-110">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="a27e4-111">Para obtener más información sobre cómo usar el Visor de perfil de datos para analizar la salida de la tarea de generación de perfiles de datos, vea [Visor de perfil de datos](data-profile-viewer.md).</span><span class="sxs-lookup"><span data-stu-id="a27e4-111">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="understanding-the-selection-of-determinant-and-dependent-columns"></a><span data-ttu-id="a27e4-112">Selección de las columnas determinante y dependiente</span><span class="sxs-lookup"><span data-stu-id="a27e4-112">Understanding the Selection of Determinant and Dependent Columns</span></span>  
 <span data-ttu-id="a27e4-113">Una **Solicitud de perfil de dependencia funcional** calcula el grado en que la columna o conjunto de columnas del lado determinante (especificadas en la propiedad **DeterminantColumns** ) determina el valor de la columna del lado dependiente (que se especifica en la propiedad **DependentColumn** ).</span><span class="sxs-lookup"><span data-stu-id="a27e4-113">A **Functional Dependency Profile Request** computes the degree to which the determinant side column or set of columns (specified in the **DeterminantColumns** property) determines the value of the dependent side column (specified in the **DependentColumn** property).</span></span> <span data-ttu-id="a27e4-114">Por ejemplo, una columna de estados de Estados Unidos debería ser funcionalmente dependiente de una columna de códigos postales de Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="a27e4-114">For example, a United States state column should be functionally dependent on a United States Zip Code column.</span></span> <span data-ttu-id="a27e4-115">Es decir, si el código postal (columna determinante) es 98052, el estado (columna dependiente) siempre debería ser Washington.</span><span class="sxs-lookup"><span data-stu-id="a27e4-115">That is, if the Zip Code (determinant column) is 98052, the state (dependent column) should always be Washington.</span></span>  
  
 <span data-ttu-id="a27e4-116">Para el lado determinante, puede especificar una columna o un conjunto de columnas en la propiedad **DeterminantColumns** .</span><span class="sxs-lookup"><span data-stu-id="a27e4-116">For the determinant side, you can specify a column or a set of columns in the **DeterminantColumns** property.</span></span> <span data-ttu-id="a27e4-117">Por ejemplo, considere una tabla de ejemplo que contenga las columnas A, B y C. Puede hacer las selecciones siguientes para la propiedad **DeterminantColumns** :</span><span class="sxs-lookup"><span data-stu-id="a27e4-117">For example, consider a sample table that contains columns A, B, and C. You make the following selections for the **DeterminantColumns** property:</span></span>  
  
-   <span data-ttu-id="a27e4-118">Al seleccionar el carácter comodín **(\*)** , la tarea de generación de perfiles de datos prueba cada columna como lado determinante de la dependencia.</span><span class="sxs-lookup"><span data-stu-id="a27e4-118">When you select the **(\*)** wildcard, the Data Profiling task tests each column as the determinant side of the dependency.</span></span>  
  
-   <span data-ttu-id="a27e4-119">Al seleccionar el carácter comodín **(\*)** y otra columna o columnas, la tarea de generación de perfiles de datos prueba cada combinación de columnas como lado determinante de la dependencia.</span><span class="sxs-lookup"><span data-stu-id="a27e4-119">When you select the **(\*)** wildcard and another column or columns, the Data Profiling task tests each combination of columns as the determinant side of the dependency.</span></span> <span data-ttu-id="a27e4-120">Por ejemplo, considere una tabla de ejemplo que contiene las columnas A, B y C. Si especifica **(\*)** y la columna C como el valor de la propiedad **DeterminantColumns**, la tarea de generación de perfiles de datos prueba las combinaciones (A, C) y (B, C) como el lado determinante de la dependencia.</span><span class="sxs-lookup"><span data-stu-id="a27e4-120">For example, consider a sample table that contains columns A, B, and C. If you specify **(\*)** and column C as the value of the **DeterminantColumns** property, the Data Profiling task tests the combinations (A, C) and (B, C) as the determinant side of the dependency.</span></span>  
  
 <span data-ttu-id="a27e4-121">Para el lado dependiente, puede especificar una columna única o el carácter comodín **(\*)** en la propiedad **DependentColumn**.</span><span class="sxs-lookup"><span data-stu-id="a27e4-121">For the dependent side, you can specify a single column or the **(\*)** wildcard in the **DependentColumn** property.</span></span> <span data-ttu-id="a27e4-122">Al seleccionar **(\*)** , la tarea de generación de perfiles de datos prueba la columna o conjunto de columnas del lado determinante con cada columna.</span><span class="sxs-lookup"><span data-stu-id="a27e4-122">When you select **(\*)**, the Data Profiling task tests the determinant side column or set of columns against each column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a27e4-123">Si selecciona **(\*)** , esta opción podría provocar un gran número de cálculos y disminuir el rendimiento de la tarea.</span><span class="sxs-lookup"><span data-stu-id="a27e4-123">If you select **(\*)**, this option might result in a large number of computations and decrease the performance of the task.</span></span> <span data-ttu-id="a27e4-124">Sin embargo, si la tarea encuentra un subconjunto que satisface el umbral para una dependencia funcional, la tarea no analiza las combinaciones adicionales.</span><span class="sxs-lookup"><span data-stu-id="a27e4-124">However, if the task finds a subset that satisfies the threshold for a functional dependency, the task does not analyze additional combinations.</span></span> <span data-ttu-id="a27e4-125">Por ejemplo, en la tabla de ejemplo descrita anteriormente, si la tarea determina que la columna C es una columna determinante, no sigue analizando los candidatos compuestos.</span><span class="sxs-lookup"><span data-stu-id="a27e4-125">For example, in the sample table described above, if the task determines that column C is a determinant column, the task does not continue to analyze the composite candidates.</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="a27e4-126">Opciones de Propiedades de la solicitud</span><span class="sxs-lookup"><span data-stu-id="a27e4-126">Request Properties Options</span></span>  
 <span data-ttu-id="a27e4-127">Para cada **Solicitud de perfil de dependencia funcional**, el panel **Propiedades de la solicitud** muestra los grupos de opciones siguientes:</span><span class="sxs-lookup"><span data-stu-id="a27e4-127">For a **Functional Dependency Profile Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="a27e4-128">**Data**, que incluye las opciones **DeterminantColumns** y **DependentColumn** .</span><span class="sxs-lookup"><span data-stu-id="a27e4-128">**Data**, which includes the **DeterminantColumns** and **DependentColumn** options</span></span>  
  
-   <span data-ttu-id="a27e4-129">**General**</span><span class="sxs-lookup"><span data-stu-id="a27e4-129">**General**</span></span>  
  
-   <span data-ttu-id="a27e4-130">**Opciones**</span><span class="sxs-lookup"><span data-stu-id="a27e4-130">**Options**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="a27e4-131">Opciones de Data</span><span class="sxs-lookup"><span data-stu-id="a27e4-131">Data Options</span></span>  
 <span data-ttu-id="a27e4-132">**ConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="a27e4-132">**ConnectionManager**</span></span>  
 <span data-ttu-id="a27e4-133">Seleccione el administrador de conexiones de [!INCLUDE[vstecado](../../includes/vstecado-md.md)] existente que usa el proveedor de datos .NET para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) para conectarse a la base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que contiene la tabla o la vista con la que se generará el perfil.</span><span class="sxs-lookup"><span data-stu-id="a27e4-133">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="a27e4-134">**TableOrView**</span><span class="sxs-lookup"><span data-stu-id="a27e4-134">**TableOrView**</span></span>  
 <span data-ttu-id="a27e4-135">Seleccione la tabla o vista cuyo perfil se va a generar.</span><span class="sxs-lookup"><span data-stu-id="a27e4-135">Select the existing table or view to be profiled.</span></span>  
  
 <span data-ttu-id="a27e4-136">**DeterminantColumns**</span><span class="sxs-lookup"><span data-stu-id="a27e4-136">**DeterminantColumns**</span></span>  
 <span data-ttu-id="a27e4-137">Seleccione la columna o conjunto de columnas determinantes.</span><span class="sxs-lookup"><span data-stu-id="a27e4-137">Select the determinant column or set of columns.</span></span> <span data-ttu-id="a27e4-138">Es decir, seleccione la columna o conjunto de columnas cuyos valores determinan el valor de la columna dependiente.</span><span class="sxs-lookup"><span data-stu-id="a27e4-138">That is, select the column or set of columns whose values determine the value of the dependent column.</span></span>  
  
 <span data-ttu-id="a27e4-139">Para obtener más información, vea las secciones, "Selección de las columnas determinante y dependiente" y "Opciones DeterminantColumns y DependentColumn", en este tema.</span><span class="sxs-lookup"><span data-stu-id="a27e4-139">For more information, see the sections, "Understanding the Selection of Determinant and Dependent Columns" and "DeterminantColumns and DependentColumn Options," in this topic.</span></span>  
  
 <span data-ttu-id="a27e4-140">**DependentColumn**</span><span class="sxs-lookup"><span data-stu-id="a27e4-140">**DependentColumn**</span></span>  
 <span data-ttu-id="a27e4-141">Seleccione la columna dependiente.</span><span class="sxs-lookup"><span data-stu-id="a27e4-141">Select the dependent column.</span></span> <span data-ttu-id="a27e4-142">Es decir, seleccione la columna cuyo valor se determina mediante el valor de la columna o conjunto de columnas del lado determinante.</span><span class="sxs-lookup"><span data-stu-id="a27e4-142">That is, select the column whose value is determined by the value of the determinant side column or set of columns.</span></span>  
  
 <span data-ttu-id="a27e4-143">Para obtener más información, vea las secciones, "Selección de las columnas determinante y dependiente" y "Opciones DeterminantColumns y DependentColumn", en este tema.</span><span class="sxs-lookup"><span data-stu-id="a27e4-143">For more information, see the sections, "Understanding the Selection of Determinant and Dependent Columns" and "DeterminantColumns and DependentColumn Options," in this topic.</span></span>  
  
#### <a name="determinantcolumns-and-dependentcolumn-options"></a><span data-ttu-id="a27e4-144">Opciones DeterminantColumns y DependentColumn</span><span class="sxs-lookup"><span data-stu-id="a27e4-144">DeterminantColumns and DependentColumn Options</span></span>  
 <span data-ttu-id="a27e4-145">Las opciones siguientes se presentan para cada columna seleccionada para generar un perfil en **DeterminantColumns** y **DependentColumn**.</span><span class="sxs-lookup"><span data-stu-id="a27e4-145">The following options are presented for each column selected for profiling in **DeterminantColumns** and in **DependentColumn**.</span></span>  
  
 <span data-ttu-id="a27e4-146">Para obtener más información, vea la sección "Selección de las columnas determinante y dependiente" anteriormente en este tema.</span><span class="sxs-lookup"><span data-stu-id="a27e4-146">For more information, see the section, "Understanding the Selection of Determinant and Dependent Columns," earlier in this topic.</span></span>  
  
 <span data-ttu-id="a27e4-147">**IsWildCard**</span><span class="sxs-lookup"><span data-stu-id="a27e4-147">**IsWildCard**</span></span>  
 <span data-ttu-id="a27e4-148">Especifica si se ha seleccionado el carácter comodín **(\*)** .</span><span class="sxs-lookup"><span data-stu-id="a27e4-148">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="a27e4-149">Esta opción está establecida en **True** si ha seleccionado **(\*)** para generar un perfil de todas las columnas.</span><span class="sxs-lookup"><span data-stu-id="a27e4-149">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="a27e4-150">Es **False** si ha seleccionado una columna individual para la que generar un perfil.</span><span class="sxs-lookup"><span data-stu-id="a27e4-150">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="a27e4-151">Esta opción es de solo lectura.</span><span class="sxs-lookup"><span data-stu-id="a27e4-151">This option is read-only.</span></span>  
  
 <span data-ttu-id="a27e4-152">**ColumnName**</span><span class="sxs-lookup"><span data-stu-id="a27e4-152">**ColumnName**</span></span>  
 <span data-ttu-id="a27e4-153">Muestra el nombre de la columna seleccionada.</span><span class="sxs-lookup"><span data-stu-id="a27e4-153">Displays the name of the selected column.</span></span> <span data-ttu-id="a27e4-154">Esta opción está en blanco si ha seleccionado **(\*)** para generar un perfil de todas las columnas.</span><span class="sxs-lookup"><span data-stu-id="a27e4-154">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="a27e4-155">Esta opción es de solo lectura.</span><span class="sxs-lookup"><span data-stu-id="a27e4-155">This option is read-only.</span></span>  
  
 <span data-ttu-id="a27e4-156">**StringCompareOptions**</span><span class="sxs-lookup"><span data-stu-id="a27e4-156">**StringCompareOptions**</span></span>  
 <span data-ttu-id="a27e4-157">Seleccione las opciones para comparar los valores de cadena.</span><span class="sxs-lookup"><span data-stu-id="a27e4-157">Select options for comparing string values.</span></span> <span data-ttu-id="a27e4-158">Esta propiedad presenta las opciones indicadas en la siguiente tabla.</span><span class="sxs-lookup"><span data-stu-id="a27e4-158">This property has the options listed in the following table.</span></span> <span data-ttu-id="a27e4-159">El valor predeterminado de esta opción es **Default**.</span><span class="sxs-lookup"><span data-stu-id="a27e4-159">The default value of this option is **Default**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a27e4-160">Cuando use el carácter comodín **(\*)** para **ColumnName**, **CompareOptions** es de solo lectura y se establece en el valor **Default**.</span><span class="sxs-lookup"><span data-stu-id="a27e4-160">When you use the **(\*)** wildcard for **ColumnName**, **CompareOptions** is read-only and is set to the **Default** setting.</span></span>  
  
|<span data-ttu-id="a27e4-161">Value</span><span class="sxs-lookup"><span data-stu-id="a27e4-161">Value</span></span>|<span data-ttu-id="a27e4-162">Descripción</span><span class="sxs-lookup"><span data-stu-id="a27e4-162">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a27e4-163">**Valor predeterminado**</span><span class="sxs-lookup"><span data-stu-id="a27e4-163">**Default**</span></span>|<span data-ttu-id="a27e4-164">Ordena y compara datos basados en la intercalación de la columna en la tabla de origen.</span><span class="sxs-lookup"><span data-stu-id="a27e4-164">Sorts and compares data based on the column's collation in the source table.</span></span>|  
|<span data-ttu-id="a27e4-165">**BinarySort**</span><span class="sxs-lookup"><span data-stu-id="a27e4-165">**BinarySort**</span></span>|<span data-ttu-id="a27e4-166">Ordena y compara los datos según los patrones de bits definidos para cada carácter.</span><span class="sxs-lookup"><span data-stu-id="a27e4-166">Sorts and compares data based on the bit patterns defined for each character.</span></span> <span data-ttu-id="a27e4-167">El orden binario utiliza la distinción de mayúsculas y minúsculas, y de acentos.</span><span class="sxs-lookup"><span data-stu-id="a27e4-167">Binary sort order is case sensitive and accent sensitive.</span></span> <span data-ttu-id="a27e4-168">El orden binario es también el más rápido.</span><span class="sxs-lookup"><span data-stu-id="a27e4-168">Binary is also the fastest sorting order.</span></span>|  
|<span data-ttu-id="a27e4-169">**DictionarySort**</span><span class="sxs-lookup"><span data-stu-id="a27e4-169">**DictionarySort**</span></span>|<span data-ttu-id="a27e4-170">Ordena y compara los datos según el orden y las reglas de comparación definidas en los diccionarios del idioma o alfabeto asociado.</span><span class="sxs-lookup"><span data-stu-id="a27e4-170">Sorts and compares data based on the sorting and comparison rules as defined in dictionaries for the associated language or alphabet.</span></span>|  
  
 <span data-ttu-id="a27e4-171">Si selecciona **DictionarySort**, también puede seleccionar cualquier combinación de las opciones enumeradas en la tabla siguiente.</span><span class="sxs-lookup"><span data-stu-id="a27e4-171">If you select **DictionarySort**, you can also select any combination of the options listed in the following table.</span></span> <span data-ttu-id="a27e4-172">De forma predeterminada, no se selecciona ninguna de estas opciones adicionales.</span><span class="sxs-lookup"><span data-stu-id="a27e4-172">By default, none of these additional options are selected.</span></span>  
  
|<span data-ttu-id="a27e4-173">Value</span><span class="sxs-lookup"><span data-stu-id="a27e4-173">Value</span></span>|<span data-ttu-id="a27e4-174">Descripción</span><span class="sxs-lookup"><span data-stu-id="a27e4-174">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a27e4-175">**IgnoreCase**</span><span class="sxs-lookup"><span data-stu-id="a27e4-175">**IgnoreCase**</span></span>|<span data-ttu-id="a27e4-176">Especifica si la comparación distingue entre mayúsculas y minúsculas.</span><span class="sxs-lookup"><span data-stu-id="a27e4-176">Specifies whether the comparison distinguishes between uppercase and lowercase letters.</span></span> <span data-ttu-id="a27e4-177">Si se establece esta opción, la comparación de las cadenas omite la distinción entre mayúsculas y minúsculas.</span><span class="sxs-lookup"><span data-stu-id="a27e4-177">If this option is set, the string comparison ignores case.</span></span> <span data-ttu-id="a27e4-178">Por ejemplo, "ABC" se interpreta igual que "abc".</span><span class="sxs-lookup"><span data-stu-id="a27e4-178">For example, "ABC" becomes the same as "abc".</span></span>|  
|<span data-ttu-id="a27e4-179">**IgnoreNonSpace**</span><span class="sxs-lookup"><span data-stu-id="a27e4-179">**IgnoreNonSpace**</span></span>|<span data-ttu-id="a27e4-180">Especifica si la comparación distingue entre caracteres con espacio y signos diacríticos.</span><span class="sxs-lookup"><span data-stu-id="a27e4-180">Specifies whether the comparison distinguishes between spacing characters and diacritics.</span></span> <span data-ttu-id="a27e4-181">Si se establece esta opción, la comparación omite los signos diacríticos.</span><span class="sxs-lookup"><span data-stu-id="a27e4-181">If this option is set, the comparison ignores diacritics.</span></span> <span data-ttu-id="a27e4-182">Por ejemplo, "å" se considera igual que "a".</span><span class="sxs-lookup"><span data-stu-id="a27e4-182">For example, "å" is equal to "a".</span></span>|  
|<span data-ttu-id="a27e4-183">**IgnoreKanaType**</span><span class="sxs-lookup"><span data-stu-id="a27e4-183">**IgnoreKanaType**</span></span>|<span data-ttu-id="a27e4-184">Especifica si la comparación distingue entre los dos tipos de caracteres kana japoneses: hiragana y katakana.</span><span class="sxs-lookup"><span data-stu-id="a27e4-184">Specifies whether the comparison distinguishes between the two types of Japanese kana characters: hiragana and katakana.</span></span> <span data-ttu-id="a27e4-185">Si se establece esta opción, la comparación de las cadenas omite los tipos de caracteres kana.</span><span class="sxs-lookup"><span data-stu-id="a27e4-185">If this option is set, the string comparison ignores kana type.</span></span>|  
|<span data-ttu-id="a27e4-186">**IgnoreWidth**</span><span class="sxs-lookup"><span data-stu-id="a27e4-186">**IgnoreWidth**</span></span>|<span data-ttu-id="a27e4-187">Especifica si la comparación distingue entre un carácter de un solo byte y el mismo carácter cuando se representa con un carácter de doble byte.</span><span class="sxs-lookup"><span data-stu-id="a27e4-187">Specifies whether the comparison distinguishes between a single-byte character and the same character when it is represented as a double-byte character.</span></span> <span data-ttu-id="a27e4-188">Si se establece esta opción, la comparación de las cadenas trata las representaciones de un solo byte y de doble byte del mismo carácter como idénticas.</span><span class="sxs-lookup"><span data-stu-id="a27e4-188">If this option is set, the string comparison treats single-byte and double-byte representations of the same character as identical.</span></span>|  
  
### <a name="general-options"></a><span data-ttu-id="a27e4-189">Opciones generales</span><span class="sxs-lookup"><span data-stu-id="a27e4-189">General Options</span></span>  
 <span data-ttu-id="a27e4-190">**IdSolicitud**</span><span class="sxs-lookup"><span data-stu-id="a27e4-190">**RequestID**</span></span>  
 <span data-ttu-id="a27e4-191">Escriba un nombre descriptivo para identificar esta solicitud de perfil.</span><span class="sxs-lookup"><span data-stu-id="a27e4-191">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="a27e4-192">Generalmente, no tiene que cambiar el valor generado automáticamente.</span><span class="sxs-lookup"><span data-stu-id="a27e4-192">Typically, you do not have to change the autogenerated value.</span></span>  
  
### <a name="options"></a><span data-ttu-id="a27e4-193">Opciones</span><span class="sxs-lookup"><span data-stu-id="a27e4-193">Options</span></span>  
 <span data-ttu-id="a27e4-194">**ThresholdSetting**</span><span class="sxs-lookup"><span data-stu-id="a27e4-194">**ThresholdSetting**</span></span>  
 <span data-ttu-id="a27e4-195">Especifique el valor de umbral.</span><span class="sxs-lookup"><span data-stu-id="a27e4-195">Specify the threshold setting.</span></span> <span data-ttu-id="a27e4-196">El valor predeterminado de esta propiedad es **Specified**.</span><span class="sxs-lookup"><span data-stu-id="a27e4-196">The default value of this property is **Specified**.</span></span>  
  
|<span data-ttu-id="a27e4-197">Value</span><span class="sxs-lookup"><span data-stu-id="a27e4-197">Value</span></span>|<span data-ttu-id="a27e4-198">Descripción</span><span class="sxs-lookup"><span data-stu-id="a27e4-198">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a27e4-199">**None**</span><span class="sxs-lookup"><span data-stu-id="a27e4-199">**None**</span></span>|<span data-ttu-id="a27e4-200">No especifica un umbral.</span><span class="sxs-lookup"><span data-stu-id="a27e4-200">Does not specify a threshold.</span></span> <span data-ttu-id="a27e4-201">El nivel de dependencia funcional se indica independientemente de su valor.</span><span class="sxs-lookup"><span data-stu-id="a27e4-201">The functional dependency strength is reported regardless of its value.</span></span>|  
|<span data-ttu-id="a27e4-202">**Specified**</span><span class="sxs-lookup"><span data-stu-id="a27e4-202">**Specified**</span></span>|<span data-ttu-id="a27e4-203">Utilice el umbral que se especifica en **FDStrengthThreshold**.</span><span class="sxs-lookup"><span data-stu-id="a27e4-203">Use the threshold that is specified in **FDStrengthThreshold**.</span></span> <span data-ttu-id="a27e4-204">Solo se indica el nivel de dependencia funcional si es mayor que el umbral.</span><span class="sxs-lookup"><span data-stu-id="a27e4-204">The functional dependency strength is reported only if it is greater than the threshold.</span></span>|  
|<span data-ttu-id="a27e4-205">**Exact**</span><span class="sxs-lookup"><span data-stu-id="a27e4-205">**Exact**</span></span>|<span data-ttu-id="a27e4-206">No especifica un umbral.</span><span class="sxs-lookup"><span data-stu-id="a27e4-206">Does not specify a threshold.</span></span> <span data-ttu-id="a27e4-207">El nivel de dependencia funcional solo se indica si la dependencia funcional entre las columnas seleccionadas es exacta.</span><span class="sxs-lookup"><span data-stu-id="a27e4-207">The functional dependency strength is reported only if the functional dependency between the selected columns is exact.</span></span>|  
  
 <span data-ttu-id="a27e4-208">**FDStrengthThreshold**</span><span class="sxs-lookup"><span data-stu-id="a27e4-208">**FDStrengthThreshold**</span></span>  
 <span data-ttu-id="a27e4-209">Especifique el umbral (con un valor entre 0 y 1) por encima del que se debería notificar un nivel de dependencia funcional.</span><span class="sxs-lookup"><span data-stu-id="a27e4-209">Specify the threshold (by using a value between 0 and 1) above which the functional dependency strength should be reported.</span></span> <span data-ttu-id="a27e4-210">El valor predeterminado de esta propiedad es 0,95.</span><span class="sxs-lookup"><span data-stu-id="a27e4-210">The default value of this property is 0.95.</span></span> <span data-ttu-id="a27e4-211">Esta opción solo se habilita cuando la opción **Specified** se selecciona como **ThresholdSetting**.</span><span class="sxs-lookup"><span data-stu-id="a27e4-211">This option is enabled only when **Specified** is selected as the **ThresholdSetting**.</span></span>  
  
 <span data-ttu-id="a27e4-212">**MaxNumberOfViolations**</span><span class="sxs-lookup"><span data-stu-id="a27e4-212">**MaxNumberOfViolations**</span></span>  
 <span data-ttu-id="a27e4-213">Especifique el número máximo de infracciones de la dependencia funcional que va a notificarse en la salida.</span><span class="sxs-lookup"><span data-stu-id="a27e4-213">Specify the maximum number of functional dependency violations to report in the output.</span></span> <span data-ttu-id="a27e4-214">El valor predeterminado de esta propiedad es 100.</span><span class="sxs-lookup"><span data-stu-id="a27e4-214">The default value of this property is 100.</span></span> <span data-ttu-id="a27e4-215">Esta opción se deshabilita cuando la opción **Exact** se selecciona como **ThresholdSetting**.</span><span class="sxs-lookup"><span data-stu-id="a27e4-215">This option is disabled when **Exact** is selected as the **ThresholdSetting**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a27e4-216">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a27e4-216">See Also</span></span>  
 <span data-ttu-id="a27e4-217">[Editor de tareas de generación de perfiles de datos &#40;página General&#41;](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="a27e4-217">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="a27e4-218">Formulario de perfil rápido de tabla única &#40;tarea de generación de perfiles de datos&#41;</span><span class="sxs-lookup"><span data-stu-id="a27e4-218">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  