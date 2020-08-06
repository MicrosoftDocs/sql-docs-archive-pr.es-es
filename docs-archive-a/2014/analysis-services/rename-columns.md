---
title: 'Lección 3: cambiar el nombre de las columnas | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5fc8ba1a-2b30-4775-9b3b-c09dee711b3e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 59904f1110455b65679b3d19e6e8b7c731465ee9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662263"
---
# <a name="lesson-3-rename-columns"></a><span data-ttu-id="e0a9c-102">Lección 3: Cambiar el nombre de las columnas</span><span class="sxs-lookup"><span data-stu-id="e0a9c-102">Lesson 3: Rename Columns</span></span>
  <span data-ttu-id="e0a9c-103">En esta lección, cambiará el nombre de muchas de las columnas de cada tabla que ha importado.</span><span class="sxs-lookup"><span data-stu-id="e0a9c-103">In this lesson, you will rename many of the columns in each table you imported.</span></span> <span data-ttu-id="e0a9c-104">El cambio de nombre permite navegar de forma más sencilla por el diseñador de modelos y facilita la selección de campos de los usuarios en una aplicación cliente.</span><span class="sxs-lookup"><span data-stu-id="e0a9c-104">Renaming makes columns more identifiable and easier to navigate in both the model designer as well by users selecting fields in a client application.</span></span> <span data-ttu-id="e0a9c-105">Para obtener más información, consulte [Cambiar el nombre de una tabla o una columna &#40;SSAS tabular&#41;](tabular-models/rename-a-table-or-column-ssas-tabular.md).</span><span class="sxs-lookup"><span data-stu-id="e0a9c-105">To learn more, see [Rename a Table or Column &#40;SSAS Tabular&#41;](tabular-models/rename-a-table-or-column-ssas-tabular.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e0a9c-106">El cambio de nombre de las columnas no es necesario para completar este tutorial; sin embargo, las lecciones restantes, especialmente en las que hay que crear relaciones, así como crear columnas calculadas y medidas mediante fórmulas DAX, hacen referencia a los nombres descriptivos que se indican en esta lección.</span><span class="sxs-lookup"><span data-stu-id="e0a9c-106">Renaming columns is not necessary to complete this tutorial; however, remaining lessons, in particular those that include creating relationships and creating calculated columns and measures using DAX formulas, refer to the column friendly names described in this lesson.</span></span> <span data-ttu-id="e0a9c-107">Si decide no cambiar el nombre de las columnas, tendrá que editar las fórmulas DAX en las lecciones 5, 6 y 7 para utilizar los nombres de las columnas de origen originales proporcionados en esta lección.</span><span class="sxs-lookup"><span data-stu-id="e0a9c-107">If you choose not to rename columns, you will have to edit the DAX formulas in lessons 5, 6, and 7 to use the original source column names provided in this lesson.</span></span>  
  
 <span data-ttu-id="e0a9c-108">Tiempo estimado para completar esta lección: **20 minutos**</span><span class="sxs-lookup"><span data-stu-id="e0a9c-108">Estimated time to complete this lesson: **20 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e0a9c-109">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="e0a9c-109">Prerequisites</span></span>  
 <span data-ttu-id="e0a9c-110">Este tema forma parte de un tutorial de modelado tabular, que se debe completar en orden.</span><span class="sxs-lookup"><span data-stu-id="e0a9c-110">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="e0a9c-111">Antes de realizar las tareas de esta lección, debe haber completado la lección anterior: [Lección 2: Agregar datos](lesson-2-add-data.md).</span><span class="sxs-lookup"><span data-stu-id="e0a9c-111">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 2: Add Data](lesson-2-add-data.md).</span></span>  
  
## <a name="rename-columns"></a><span data-ttu-id="e0a9c-112">Cambiar el nombre de las columnas</span><span class="sxs-lookup"><span data-stu-id="e0a9c-112">Rename Columns</span></span>  
  
#### <a name="to-rename-columns"></a><span data-ttu-id="e0a9c-113">Para cambiar el nombre de las columnas</span><span class="sxs-lookup"><span data-stu-id="e0a9c-113">To rename columns</span></span>  
  
1.  <span data-ttu-id="e0a9c-114">En el diseñador de modelos, haga clic en la pestaña de la tabla **Customer** .</span><span class="sxs-lookup"><span data-stu-id="e0a9c-114">In the model designer, click the **Customer** table (tab).</span></span>  
  
     <span data-ttu-id="e0a9c-115">Al hacer clic en una pestaña, la tabla se activa en la ventana del diseñador de modelos.</span><span class="sxs-lookup"><span data-stu-id="e0a9c-115">When you click a tab, that table becomes active in the model designer window.</span></span>  
  
2.  <span data-ttu-id="e0a9c-116">Haga doble clic en el nombre de la columna **CustomerKey** , escriba `Customer  Id` y, a continuación, presione Entrar.</span><span class="sxs-lookup"><span data-stu-id="e0a9c-116">Double click the **CustomerKey** column name, then type `Customer  Id`, and then press ENTER.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="e0a9c-117">También puede cambiar el nombre de una columna en la propiedad **nombre de columna** en la ventana **propiedades** de la columna o en la vista de diagrama.</span><span class="sxs-lookup"><span data-stu-id="e0a9c-117">You can also rename a column in the **Column Name** property in the column's **Properties** window, or in Diagram View.</span></span>  
  
3.  <span data-ttu-id="e0a9c-118">Cambie el nombre de las columnas restantes de la tabla **Customer** , así como el de las columnas de las demás tablas, y sustituya el nombre de origen por el nombre descriptivo:</span><span class="sxs-lookup"><span data-stu-id="e0a9c-118">Rename the remaining columns in the **Customer** table, as well as the columns in the remaining tables, replacing the source name with the friendly name:</span></span>  
  
     <span data-ttu-id="e0a9c-119">**Tabla Customer**</span><span class="sxs-lookup"><span data-stu-id="e0a9c-119">**Customer Table**</span></span>  
  
    |<span data-ttu-id="e0a9c-120">Nombre de origen</span><span class="sxs-lookup"><span data-stu-id="e0a9c-120">Source Name</span></span>|<span data-ttu-id="e0a9c-121">Nombre descriptivo</span><span class="sxs-lookup"><span data-stu-id="e0a9c-121">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="e0a9c-122">GeographyKey</span><span class="sxs-lookup"><span data-stu-id="e0a9c-122">GeographyKey</span></span>|<span data-ttu-id="e0a9c-123">Geography Id</span><span class="sxs-lookup"><span data-stu-id="e0a9c-123">Geography Id</span></span>|  
    |<span data-ttu-id="e0a9c-124">CustomerAlternateKey</span><span class="sxs-lookup"><span data-stu-id="e0a9c-124">CustomerAlternateKey</span></span>|<span data-ttu-id="e0a9c-125">Id. alternativo del cliente</span><span class="sxs-lookup"><span data-stu-id="e0a9c-125">Customer Alternate Id</span></span>|  
    |<span data-ttu-id="e0a9c-126">Nombre</span><span class="sxs-lookup"><span data-stu-id="e0a9c-126">FirstName</span></span>|<span data-ttu-id="e0a9c-127">Nombre</span><span class="sxs-lookup"><span data-stu-id="e0a9c-127">First Name</span></span>|  
    |<span data-ttu-id="e0a9c-128">MiddleName</span><span class="sxs-lookup"><span data-stu-id="e0a9c-128">MiddleName</span></span>|<span data-ttu-id="e0a9c-129">Segundo nombre</span><span class="sxs-lookup"><span data-stu-id="e0a9c-129">Middle Name</span></span>|  
    |<span data-ttu-id="e0a9c-130">Apellidos</span><span class="sxs-lookup"><span data-stu-id="e0a9c-130">LastName</span></span>|<span data-ttu-id="e0a9c-131">Apellido</span><span class="sxs-lookup"><span data-stu-id="e0a9c-131">Last Name</span></span>|  
    |<span data-ttu-id="e0a9c-132">NameStyle</span><span class="sxs-lookup"><span data-stu-id="e0a9c-132">NameStyle</span></span>|<span data-ttu-id="e0a9c-133">Estilo del nombre</span><span class="sxs-lookup"><span data-stu-id="e0a9c-133">Name Style</span></span>|  
    |<span data-ttu-id="e0a9c-134">BirthDate</span><span class="sxs-lookup"><span data-stu-id="e0a9c-134">BirthDate</span></span>|<span data-ttu-id="e0a9c-135">Birth Date</span><span class="sxs-lookup"><span data-stu-id="e0a9c-135">Birth Date</span></span>|  
    |<span data-ttu-id="e0a9c-136">MaritalStatus</span><span class="sxs-lookup"><span data-stu-id="e0a9c-136">MaritalStatus</span></span>|<span data-ttu-id="e0a9c-137">Marital Status</span><span class="sxs-lookup"><span data-stu-id="e0a9c-137">Marital Status</span></span>|  
    |<span data-ttu-id="e0a9c-138">EmailAddress</span><span class="sxs-lookup"><span data-stu-id="e0a9c-138">EmailAddress</span></span>|<span data-ttu-id="e0a9c-139">Dirección de correo electrónico</span><span class="sxs-lookup"><span data-stu-id="e0a9c-139">Email Address</span></span>|  
    |<span data-ttu-id="e0a9c-140">YearlyIncome</span><span class="sxs-lookup"><span data-stu-id="e0a9c-140">YearlyIncome</span></span>|<span data-ttu-id="e0a9c-141">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="e0a9c-141">Yearly Income</span></span>|  
    |<span data-ttu-id="e0a9c-142">TotalChildren</span><span class="sxs-lookup"><span data-stu-id="e0a9c-142">TotalChildren</span></span>|<span data-ttu-id="e0a9c-143">Total Children</span><span class="sxs-lookup"><span data-stu-id="e0a9c-143">Total Children</span></span>|  
    |<span data-ttu-id="e0a9c-144">NumberChildrenAtHome</span><span class="sxs-lookup"><span data-stu-id="e0a9c-144">NumberChildrenAtHome</span></span>|<span data-ttu-id="e0a9c-145">Hijos a su cuidado</span><span class="sxs-lookup"><span data-stu-id="e0a9c-145">Number of Children At Home</span></span>|  
    |<span data-ttu-id="e0a9c-146">EnglishEducation</span><span class="sxs-lookup"><span data-stu-id="e0a9c-146">EnglishEducation</span></span>|<span data-ttu-id="e0a9c-147">Education</span><span class="sxs-lookup"><span data-stu-id="e0a9c-147">Education</span></span>|  
    |<span data-ttu-id="e0a9c-148">EnglishOccupation</span><span class="sxs-lookup"><span data-stu-id="e0a9c-148">EnglishOccupation</span></span>|<span data-ttu-id="e0a9c-149">Occupation</span><span class="sxs-lookup"><span data-stu-id="e0a9c-149">Occupation</span></span>|  
    |<span data-ttu-id="e0a9c-150">HouseOwnerFlag</span><span class="sxs-lookup"><span data-stu-id="e0a9c-150">HouseOwnerFlag</span></span>|<span data-ttu-id="e0a9c-151">Propietario de una vivienda</span><span class="sxs-lookup"><span data-stu-id="e0a9c-151">Owns House</span></span>|  
    |<span data-ttu-id="e0a9c-152">NumberCarsOwned</span><span class="sxs-lookup"><span data-stu-id="e0a9c-152">NumberCarsOwned</span></span>|<span data-ttu-id="e0a9c-153">Número de vehículos en propiedad</span><span class="sxs-lookup"><span data-stu-id="e0a9c-153">Number of Cars Owned</span></span>|  
    |<span data-ttu-id="e0a9c-154">AddressLine1</span><span class="sxs-lookup"><span data-stu-id="e0a9c-154">AddressLine1</span></span>|<span data-ttu-id="e0a9c-155">Línea de dirección 1</span><span class="sxs-lookup"><span data-stu-id="e0a9c-155">Address Line 1</span></span>|  
    |<span data-ttu-id="e0a9c-156">AddressLine2</span><span class="sxs-lookup"><span data-stu-id="e0a9c-156">AddressLine2</span></span>|<span data-ttu-id="e0a9c-157">Línea de dirección 2</span><span class="sxs-lookup"><span data-stu-id="e0a9c-157">Address Line 2</span></span>|  
    |<span data-ttu-id="e0a9c-158">Teléfono</span><span class="sxs-lookup"><span data-stu-id="e0a9c-158">Phone</span></span>|<span data-ttu-id="e0a9c-159">Número de teléfono</span><span class="sxs-lookup"><span data-stu-id="e0a9c-159">Phone Number</span></span>|  
    |<span data-ttu-id="e0a9c-160">DateFirstPurchase</span><span class="sxs-lookup"><span data-stu-id="e0a9c-160">DateFirstPurchase</span></span>|<span data-ttu-id="e0a9c-161">Fecha de la primera compra</span><span class="sxs-lookup"><span data-stu-id="e0a9c-161">Date of First Purchase</span></span>|  
    |<span data-ttu-id="e0a9c-162">CommuteDistance</span><span class="sxs-lookup"><span data-stu-id="e0a9c-162">CommuteDistance</span></span>|<span data-ttu-id="e0a9c-163">Commute Distance</span><span class="sxs-lookup"><span data-stu-id="e0a9c-163">Commute Distance</span></span>|  
  
     <span data-ttu-id="e0a9c-164">**Date**</span><span class="sxs-lookup"><span data-stu-id="e0a9c-164">**Date**</span></span>  
  
    |<span data-ttu-id="e0a9c-165">Nombre de origen</span><span class="sxs-lookup"><span data-stu-id="e0a9c-165">Source Name</span></span>|<span data-ttu-id="e0a9c-166">Nombre descriptivo</span><span class="sxs-lookup"><span data-stu-id="e0a9c-166">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="e0a9c-167">FullDateAlternateKey</span><span class="sxs-lookup"><span data-stu-id="e0a9c-167">FullDateAlternateKey</span></span>|<span data-ttu-id="e0a9c-168">Date</span><span class="sxs-lookup"><span data-stu-id="e0a9c-168">Date</span></span>|  
    |<span data-ttu-id="e0a9c-169">DayNumberOfWeek</span><span class="sxs-lookup"><span data-stu-id="e0a9c-169">DayNumberOfWeek</span></span>|<span data-ttu-id="e0a9c-170">Día de la semana</span><span class="sxs-lookup"><span data-stu-id="e0a9c-170">Day Number of Week</span></span>|  
    |<span data-ttu-id="e0a9c-171">EnglishDayNameOfWeek</span><span class="sxs-lookup"><span data-stu-id="e0a9c-171">EnglishDayNameOfWeek</span></span>|<span data-ttu-id="e0a9c-172">Nombre del día</span><span class="sxs-lookup"><span data-stu-id="e0a9c-172">Day Name</span></span>|  
    |<span data-ttu-id="e0a9c-173">DayNumberOfMonth</span><span class="sxs-lookup"><span data-stu-id="e0a9c-173">DayNumberOfMonth</span></span>|<span data-ttu-id="e0a9c-174">Día del mes</span><span class="sxs-lookup"><span data-stu-id="e0a9c-174">Day of Month</span></span>|  
    |<span data-ttu-id="e0a9c-175">DayNumberOfYear</span><span class="sxs-lookup"><span data-stu-id="e0a9c-175">DayNumberOfYear</span></span>|<span data-ttu-id="e0a9c-176">Día del año</span><span class="sxs-lookup"><span data-stu-id="e0a9c-176">Day of Year</span></span>|  
    |<span data-ttu-id="e0a9c-177">WeekNumberOfYear</span><span class="sxs-lookup"><span data-stu-id="e0a9c-177">WeekNumberOfYear</span></span>|<span data-ttu-id="e0a9c-178">Número de semana del año</span><span class="sxs-lookup"><span data-stu-id="e0a9c-178">Week Number of Year</span></span>|  
    |<span data-ttu-id="e0a9c-179">EnglishMonthName</span><span class="sxs-lookup"><span data-stu-id="e0a9c-179">EnglishMonthName</span></span>|<span data-ttu-id="e0a9c-180">Nombre del mes</span><span class="sxs-lookup"><span data-stu-id="e0a9c-180">Month Name</span></span>|  
    |<span data-ttu-id="e0a9c-181">MonthNumberOfYear</span><span class="sxs-lookup"><span data-stu-id="e0a9c-181">MonthNumberOfYear</span></span>|<span data-ttu-id="e0a9c-182">Month</span><span class="sxs-lookup"><span data-stu-id="e0a9c-182">Month</span></span>|  
    |<span data-ttu-id="e0a9c-183">CalendarQuarter</span><span class="sxs-lookup"><span data-stu-id="e0a9c-183">CalendarQuarter</span></span>|<span data-ttu-id="e0a9c-184">Trimestre del calendario</span><span class="sxs-lookup"><span data-stu-id="e0a9c-184">Calendar Quarter</span></span>|  
    |<span data-ttu-id="e0a9c-185">CalendarYear</span><span class="sxs-lookup"><span data-stu-id="e0a9c-185">CalendarYear</span></span>|<span data-ttu-id="e0a9c-186">Año del calendario</span><span class="sxs-lookup"><span data-stu-id="e0a9c-186">Calendar Year</span></span>|  
    |<span data-ttu-id="e0a9c-187">CalendarSemester</span><span class="sxs-lookup"><span data-stu-id="e0a9c-187">CalendarSemester</span></span>|<span data-ttu-id="e0a9c-188">Semestre del calendario</span><span class="sxs-lookup"><span data-stu-id="e0a9c-188">Calendar Semester</span></span>|  
    |<span data-ttu-id="e0a9c-189">FiscalQuarter</span><span class="sxs-lookup"><span data-stu-id="e0a9c-189">FiscalQuarter</span></span>|<span data-ttu-id="e0a9c-190">Trimestre fiscal</span><span class="sxs-lookup"><span data-stu-id="e0a9c-190">Fiscal Quarter</span></span>|  
    |<span data-ttu-id="e0a9c-191">FiscalYear</span><span class="sxs-lookup"><span data-stu-id="e0a9c-191">FiscalYear</span></span>|<span data-ttu-id="e0a9c-192">Año fiscal</span><span class="sxs-lookup"><span data-stu-id="e0a9c-192">Fiscal Year</span></span>|  
    |<span data-ttu-id="e0a9c-193">FiscalSemester</span><span class="sxs-lookup"><span data-stu-id="e0a9c-193">FiscalSemester</span></span>|<span data-ttu-id="e0a9c-194">Semestre fiscal</span><span class="sxs-lookup"><span data-stu-id="e0a9c-194">Fiscal Semester</span></span>|  
  
     <span data-ttu-id="e0a9c-195">**Geografía**</span><span class="sxs-lookup"><span data-stu-id="e0a9c-195">**Geography**</span></span>  
  
    |<span data-ttu-id="e0a9c-196">Nombre de origen</span><span class="sxs-lookup"><span data-stu-id="e0a9c-196">Source Name</span></span>|<span data-ttu-id="e0a9c-197">Nombre descriptivo</span><span class="sxs-lookup"><span data-stu-id="e0a9c-197">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="e0a9c-198">GeographyKey</span><span class="sxs-lookup"><span data-stu-id="e0a9c-198">GeographyKey</span></span>|<span data-ttu-id="e0a9c-199">Geography Id</span><span class="sxs-lookup"><span data-stu-id="e0a9c-199">Geography Id</span></span>|  
    |<span data-ttu-id="e0a9c-200">StateProvinceCode</span><span class="sxs-lookup"><span data-stu-id="e0a9c-200">StateProvinceCode</span></span>|<span data-ttu-id="e0a9c-201">Código de estado o provincia</span><span class="sxs-lookup"><span data-stu-id="e0a9c-201">State Province Code</span></span>|  
    |<span data-ttu-id="e0a9c-202">StateProvinceName</span><span class="sxs-lookup"><span data-stu-id="e0a9c-202">StateProvinceName</span></span>|<span data-ttu-id="e0a9c-203">Nombre de estado o provincia</span><span class="sxs-lookup"><span data-stu-id="e0a9c-203">State Province Name</span></span>|  
    |<span data-ttu-id="e0a9c-204">CountryRegionCode</span><span class="sxs-lookup"><span data-stu-id="e0a9c-204">CountryRegionCode</span></span>|<span data-ttu-id="e0a9c-205">Código de país o región</span><span class="sxs-lookup"><span data-stu-id="e0a9c-205">Country Region Code</span></span>|  
    |<span data-ttu-id="e0a9c-206">EnglishCountryRegionName</span><span class="sxs-lookup"><span data-stu-id="e0a9c-206">EnglishCountryRegionName</span></span>|<span data-ttu-id="e0a9c-207">Nombre de país o región</span><span class="sxs-lookup"><span data-stu-id="e0a9c-207">Country Region Name</span></span>|  
    |<span data-ttu-id="e0a9c-208">Código postal</span><span class="sxs-lookup"><span data-stu-id="e0a9c-208">PostalCode</span></span>|<span data-ttu-id="e0a9c-209">Código postal</span><span class="sxs-lookup"><span data-stu-id="e0a9c-209">Postal Code</span></span>|  
    |<span data-ttu-id="e0a9c-210">SalesTerritoryKey</span><span class="sxs-lookup"><span data-stu-id="e0a9c-210">SalesTerritoryKey</span></span>|<span data-ttu-id="e0a9c-211">Sales Territory Id</span><span class="sxs-lookup"><span data-stu-id="e0a9c-211">Sales Territory Id</span></span>|  
  
     <span data-ttu-id="e0a9c-212">**Producto**</span><span class="sxs-lookup"><span data-stu-id="e0a9c-212">**Product**</span></span>  
  
    |<span data-ttu-id="e0a9c-213">Nombre de origen</span><span class="sxs-lookup"><span data-stu-id="e0a9c-213">Source Name</span></span>|<span data-ttu-id="e0a9c-214">Nombre descriptivo</span><span class="sxs-lookup"><span data-stu-id="e0a9c-214">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="e0a9c-215">ProductKey</span><span class="sxs-lookup"><span data-stu-id="e0a9c-215">ProductKey</span></span>|<span data-ttu-id="e0a9c-216">Product Id</span><span class="sxs-lookup"><span data-stu-id="e0a9c-216">Product Id</span></span>|  
    |<span data-ttu-id="e0a9c-217">ProductAlternateKey</span><span class="sxs-lookup"><span data-stu-id="e0a9c-217">ProductAlternateKey</span></span>|<span data-ttu-id="e0a9c-218">Product Alternate Id</span><span class="sxs-lookup"><span data-stu-id="e0a9c-218">Product Alternate Id</span></span>|  
    |<span data-ttu-id="e0a9c-219">ProductSubcategoryKey</span><span class="sxs-lookup"><span data-stu-id="e0a9c-219">ProductSubcategoryKey</span></span>|<span data-ttu-id="e0a9c-220">Id. de subcategoría del producto</span><span class="sxs-lookup"><span data-stu-id="e0a9c-220">Product Subcategory Id</span></span>|  
    |<span data-ttu-id="e0a9c-221">WeightUnitMeasureCode</span><span class="sxs-lookup"><span data-stu-id="e0a9c-221">WeightUnitMeasureCode</span></span>|<span data-ttu-id="e0a9c-222">Código de unidad de peso</span><span class="sxs-lookup"><span data-stu-id="e0a9c-222">Weight Unit Code</span></span>|  
    |<span data-ttu-id="e0a9c-223">SizeUnitMeasureCode</span><span class="sxs-lookup"><span data-stu-id="e0a9c-223">SizeUnitMeasureCode</span></span>|<span data-ttu-id="e0a9c-224">Código de unidad de tamaño</span><span class="sxs-lookup"><span data-stu-id="e0a9c-224">Size Unit Code</span></span>|  
    |<span data-ttu-id="e0a9c-225">EnglishProductName</span><span class="sxs-lookup"><span data-stu-id="e0a9c-225">EnglishProductName</span></span>|<span data-ttu-id="e0a9c-226">Nombre de producto</span><span class="sxs-lookup"><span data-stu-id="e0a9c-226">Product Name</span></span>|  
    |<span data-ttu-id="e0a9c-227">StandardCost</span><span class="sxs-lookup"><span data-stu-id="e0a9c-227">StandardCost</span></span>|<span data-ttu-id="e0a9c-228">Standard Cost</span><span class="sxs-lookup"><span data-stu-id="e0a9c-228">Standard Cost</span></span>|  
    |<span data-ttu-id="e0a9c-229">FinishedGoodsFlag</span><span class="sxs-lookup"><span data-stu-id="e0a9c-229">FinishedGoodsFlag</span></span>|<span data-ttu-id="e0a9c-230">Es producto final</span><span class="sxs-lookup"><span data-stu-id="e0a9c-230">Is Finished Product</span></span>|  
    |<span data-ttu-id="e0a9c-231">SafetyStockLevel</span><span class="sxs-lookup"><span data-stu-id="e0a9c-231">SafetyStockLevel</span></span>|<span data-ttu-id="e0a9c-232">Safety Stock Level</span><span class="sxs-lookup"><span data-stu-id="e0a9c-232">Safety Stock Level</span></span>|  
    |<span data-ttu-id="e0a9c-233">ReorderPoint</span><span class="sxs-lookup"><span data-stu-id="e0a9c-233">ReorderPoint</span></span>|<span data-ttu-id="e0a9c-234">Reorder Point</span><span class="sxs-lookup"><span data-stu-id="e0a9c-234">Reorder Point</span></span>|  
    |<span data-ttu-id="e0a9c-235">ListPrice</span><span class="sxs-lookup"><span data-stu-id="e0a9c-235">ListPrice</span></span>|<span data-ttu-id="e0a9c-236">List Price</span><span class="sxs-lookup"><span data-stu-id="e0a9c-236">List Price</span></span>|  
    |<span data-ttu-id="e0a9c-237">SizeRange</span><span class="sxs-lookup"><span data-stu-id="e0a9c-237">SizeRange</span></span>|<span data-ttu-id="e0a9c-238">Size Range</span><span class="sxs-lookup"><span data-stu-id="e0a9c-238">Size Range</span></span>|  
    |<span data-ttu-id="e0a9c-239">DaysToManufacture</span><span class="sxs-lookup"><span data-stu-id="e0a9c-239">DaysToManufacture</span></span>|<span data-ttu-id="e0a9c-240">Días hasta fabricación</span><span class="sxs-lookup"><span data-stu-id="e0a9c-240">Days to Manufacture</span></span>|  
    |<span data-ttu-id="e0a9c-241">ProductLine</span><span class="sxs-lookup"><span data-stu-id="e0a9c-241">ProductLine</span></span>|<span data-ttu-id="e0a9c-242">Línea de productos</span><span class="sxs-lookup"><span data-stu-id="e0a9c-242">Product Line</span></span>|  
    |<span data-ttu-id="e0a9c-243">Dealer Price</span><span class="sxs-lookup"><span data-stu-id="e0a9c-243">Dealer Price</span></span>|<span data-ttu-id="e0a9c-244">Dealer Price</span><span class="sxs-lookup"><span data-stu-id="e0a9c-244">Dealer Price</span></span>|  
    |<span data-ttu-id="e0a9c-245">ModelName</span><span class="sxs-lookup"><span data-stu-id="e0a9c-245">ModelName</span></span>|<span data-ttu-id="e0a9c-246">Nombre del modelo</span><span class="sxs-lookup"><span data-stu-id="e0a9c-246">Model Name</span></span>|  
    |<span data-ttu-id="e0a9c-247">LargePhoto</span><span class="sxs-lookup"><span data-stu-id="e0a9c-247">LargePhoto</span></span>|<span data-ttu-id="e0a9c-248">Foto grande</span><span class="sxs-lookup"><span data-stu-id="e0a9c-248">Large Photo</span></span>|  
    |<span data-ttu-id="e0a9c-249">EnglishDescription</span><span class="sxs-lookup"><span data-stu-id="e0a9c-249">EnglishDescription</span></span>|<span data-ttu-id="e0a9c-250">Descripción</span><span class="sxs-lookup"><span data-stu-id="e0a9c-250">Description</span></span>|  
    |<span data-ttu-id="e0a9c-251">StartDate</span><span class="sxs-lookup"><span data-stu-id="e0a9c-251">StartDate</span></span>|<span data-ttu-id="e0a9c-252">Fecha de inicio del producto</span><span class="sxs-lookup"><span data-stu-id="e0a9c-252">Product Start Date</span></span>|  
    |<span data-ttu-id="e0a9c-253">EndDate</span><span class="sxs-lookup"><span data-stu-id="e0a9c-253">EndDate</span></span>|<span data-ttu-id="e0a9c-254">Fecha de finalización del producto</span><span class="sxs-lookup"><span data-stu-id="e0a9c-254">Product End Date</span></span>|  
    |<span data-ttu-id="e0a9c-255">Estado</span><span class="sxs-lookup"><span data-stu-id="e0a9c-255">Status</span></span>|<span data-ttu-id="e0a9c-256">Estado del producto</span><span class="sxs-lookup"><span data-stu-id="e0a9c-256">Product Status</span></span>|  
  
     <span data-ttu-id="e0a9c-257">**Categoría de productos**</span><span class="sxs-lookup"><span data-stu-id="e0a9c-257">**Product Category**</span></span>  
  
    |<span data-ttu-id="e0a9c-258">Nombre de origen</span><span class="sxs-lookup"><span data-stu-id="e0a9c-258">Source Name</span></span>|<span data-ttu-id="e0a9c-259">Nombre descriptivo</span><span class="sxs-lookup"><span data-stu-id="e0a9c-259">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="e0a9c-260">ProductCategoryKey</span><span class="sxs-lookup"><span data-stu-id="e0a9c-260">ProductCategoryKey</span></span>|<span data-ttu-id="e0a9c-261">Id. de categoría del producto</span><span class="sxs-lookup"><span data-stu-id="e0a9c-261">Product Category Id</span></span>|  
    |<span data-ttu-id="e0a9c-262">ProductCategoryAlternateKey</span><span class="sxs-lookup"><span data-stu-id="e0a9c-262">ProductCategoryAlternateKey</span></span>|<span data-ttu-id="e0a9c-263">Id. alternativo de categoría del producto</span><span class="sxs-lookup"><span data-stu-id="e0a9c-263">Product Category Alternate Id</span></span>|  
    |<span data-ttu-id="e0a9c-264">EnglishProductCategoryName</span><span class="sxs-lookup"><span data-stu-id="e0a9c-264">EnglishProductCategoryName</span></span>|<span data-ttu-id="e0a9c-265">Nombre de categoría del producto</span><span class="sxs-lookup"><span data-stu-id="e0a9c-265">Product Category Name</span></span>|  
  
     <span data-ttu-id="e0a9c-266">**Product Subcategory**</span><span class="sxs-lookup"><span data-stu-id="e0a9c-266">**Product Subcategory**</span></span>  
  
    |<span data-ttu-id="e0a9c-267">Nombre de origen</span><span class="sxs-lookup"><span data-stu-id="e0a9c-267">Source Name</span></span>|<span data-ttu-id="e0a9c-268">Nombre descriptivo</span><span class="sxs-lookup"><span data-stu-id="e0a9c-268">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="e0a9c-269">ProductSubcategoryKey</span><span class="sxs-lookup"><span data-stu-id="e0a9c-269">ProductSubcategoryKey</span></span>|<span data-ttu-id="e0a9c-270">Id. de subcategoría del producto</span><span class="sxs-lookup"><span data-stu-id="e0a9c-270">Product Subcategory Id</span></span>|  
    |<span data-ttu-id="e0a9c-271">ProductSubcategoryAlternateKey</span><span class="sxs-lookup"><span data-stu-id="e0a9c-271">ProductSubcategoryAlternateKey</span></span>|<span data-ttu-id="e0a9c-272">Id. alternativo de subcategoría del producto</span><span class="sxs-lookup"><span data-stu-id="e0a9c-272">Product Subcategory Alternate Id</span></span>|  
    |<span data-ttu-id="e0a9c-273">EnglishProductSubcategoryName</span><span class="sxs-lookup"><span data-stu-id="e0a9c-273">EnglishProductSubcategoryName</span></span>|<span data-ttu-id="e0a9c-274">Nombre de subcategoría del producto</span><span class="sxs-lookup"><span data-stu-id="e0a9c-274">Product Subcategory Name</span></span>|  
    |<span data-ttu-id="e0a9c-275">ProductCategoryKey</span><span class="sxs-lookup"><span data-stu-id="e0a9c-275">ProductCategoryKey</span></span>|<span data-ttu-id="e0a9c-276">Id. de categoría del producto</span><span class="sxs-lookup"><span data-stu-id="e0a9c-276">Product Category Id</span></span>|  
  
     <span data-ttu-id="e0a9c-277">**Internet Sales**</span><span class="sxs-lookup"><span data-stu-id="e0a9c-277">**Internet Sales**</span></span>  
  
    |<span data-ttu-id="e0a9c-278">Nombre de origen</span><span class="sxs-lookup"><span data-stu-id="e0a9c-278">Source Name</span></span>|<span data-ttu-id="e0a9c-279">Nombre descriptivo</span><span class="sxs-lookup"><span data-stu-id="e0a9c-279">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="e0a9c-280">ProductKey</span><span class="sxs-lookup"><span data-stu-id="e0a9c-280">ProductKey</span></span>|<span data-ttu-id="e0a9c-281">Product Id</span><span class="sxs-lookup"><span data-stu-id="e0a9c-281">Product Id</span></span>|  
    |<span data-ttu-id="e0a9c-282">CustomerKey</span><span class="sxs-lookup"><span data-stu-id="e0a9c-282">CustomerKey</span></span>|<span data-ttu-id="e0a9c-283">Customer Id</span><span class="sxs-lookup"><span data-stu-id="e0a9c-283">Customer Id</span></span>|  
    |<span data-ttu-id="e0a9c-284">PromotionKey</span><span class="sxs-lookup"><span data-stu-id="e0a9c-284">PromotionKey</span></span>|<span data-ttu-id="e0a9c-285">Id. de promoción</span><span class="sxs-lookup"><span data-stu-id="e0a9c-285">Promotion Id</span></span>|  
    |<span data-ttu-id="e0a9c-286">CurrencyKey</span><span class="sxs-lookup"><span data-stu-id="e0a9c-286">CurrencyKey</span></span>|<span data-ttu-id="e0a9c-287">Id. de moneda</span><span class="sxs-lookup"><span data-stu-id="e0a9c-287">Currency Id</span></span>|  
    |<span data-ttu-id="e0a9c-288">SalesTerritoryKey</span><span class="sxs-lookup"><span data-stu-id="e0a9c-288">SalesTerritoryKey</span></span>|<span data-ttu-id="e0a9c-289">Sales Territory Id</span><span class="sxs-lookup"><span data-stu-id="e0a9c-289">Sales Territory Id</span></span>|  
    |<span data-ttu-id="e0a9c-290">SalesOrderNumber</span><span class="sxs-lookup"><span data-stu-id="e0a9c-290">SalesOrderNumber</span></span>|<span data-ttu-id="e0a9c-291">Número de pedido de ventas</span><span class="sxs-lookup"><span data-stu-id="e0a9c-291">Sales Order Number</span></span>|  
    |<span data-ttu-id="e0a9c-292">SalesOrderLineNumber</span><span class="sxs-lookup"><span data-stu-id="e0a9c-292">SalesOrderLineNumber</span></span>|<span data-ttu-id="e0a9c-293">Número de líneas del pedido de venta</span><span class="sxs-lookup"><span data-stu-id="e0a9c-293">Sales Order Line Number</span></span>|  
    |<span data-ttu-id="e0a9c-294">RevisionNumber</span><span class="sxs-lookup"><span data-stu-id="e0a9c-294">RevisionNumber</span></span>|<span data-ttu-id="e0a9c-295">Revision Number</span><span class="sxs-lookup"><span data-stu-id="e0a9c-295">Revision Number</span></span>|  
    |<span data-ttu-id="e0a9c-296">OrderQuantity</span><span class="sxs-lookup"><span data-stu-id="e0a9c-296">OrderQuantity</span></span>|<span data-ttu-id="e0a9c-297">Cantidad del pedido</span><span class="sxs-lookup"><span data-stu-id="e0a9c-297">Order Quantity</span></span>|  
    |<span data-ttu-id="e0a9c-298">UnitPrice</span><span class="sxs-lookup"><span data-stu-id="e0a9c-298">UnitPrice</span></span>|<span data-ttu-id="e0a9c-299">Unit Price</span><span class="sxs-lookup"><span data-stu-id="e0a9c-299">Unit Price</span></span>|  
    |<span data-ttu-id="e0a9c-300">ExtendedAmount</span><span class="sxs-lookup"><span data-stu-id="e0a9c-300">ExtendedAmount</span></span>|<span data-ttu-id="e0a9c-301">Extended Amount</span><span class="sxs-lookup"><span data-stu-id="e0a9c-301">Extended Amount</span></span>|  
    |<span data-ttu-id="e0a9c-302">UnitPriceDiscountPct</span><span class="sxs-lookup"><span data-stu-id="e0a9c-302">UnitPriceDiscountPct</span></span>|<span data-ttu-id="e0a9c-303">Porcentaje de descuento del precio por unidad</span><span class="sxs-lookup"><span data-stu-id="e0a9c-303">Unit Price Discount Pct</span></span>|  
    |<span data-ttu-id="e0a9c-304">DiscountAmount</span><span class="sxs-lookup"><span data-stu-id="e0a9c-304">DiscountAmount</span></span>|<span data-ttu-id="e0a9c-305">Discount Amount</span><span class="sxs-lookup"><span data-stu-id="e0a9c-305">Discount Amount</span></span>|  
    |<span data-ttu-id="e0a9c-306">ProductStandardCost</span><span class="sxs-lookup"><span data-stu-id="e0a9c-306">ProductStandardCost</span></span>|<span data-ttu-id="e0a9c-307">Product Standard Cost</span><span class="sxs-lookup"><span data-stu-id="e0a9c-307">Product Standard Cost</span></span>|  
    |<span data-ttu-id="e0a9c-308">TotalProductCost</span><span class="sxs-lookup"><span data-stu-id="e0a9c-308">TotalProductCost</span></span>|<span data-ttu-id="e0a9c-309">Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="e0a9c-309">Total Product Cost</span></span>|  
    |<span data-ttu-id="e0a9c-310">ImporteVentas</span><span class="sxs-lookup"><span data-stu-id="e0a9c-310">SalesAmount</span></span>|<span data-ttu-id="e0a9c-311">Sales Amount</span><span class="sxs-lookup"><span data-stu-id="e0a9c-311">Sales Amount</span></span>|  
    |<span data-ttu-id="e0a9c-312">TaxAmt</span><span class="sxs-lookup"><span data-stu-id="e0a9c-312">TaxAmt</span></span>|<span data-ttu-id="e0a9c-313">Tax Amt</span><span class="sxs-lookup"><span data-stu-id="e0a9c-313">Tax Amt</span></span>|  
    |<span data-ttu-id="e0a9c-314">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="e0a9c-314">CarrierTrackingNumber</span></span>|<span data-ttu-id="e0a9c-315">Número de seguimiento del transportista</span><span class="sxs-lookup"><span data-stu-id="e0a9c-315">Carrier Tracking Number</span></span>|  
    |<span data-ttu-id="e0a9c-316">CustomerPONumber</span><span class="sxs-lookup"><span data-stu-id="e0a9c-316">CustomerPONumber</span></span>|<span data-ttu-id="e0a9c-317">Número de orden de compra del cliente</span><span class="sxs-lookup"><span data-stu-id="e0a9c-317">Customer PO Number</span></span>|  
    |<span data-ttu-id="e0a9c-318">OrderDate</span><span class="sxs-lookup"><span data-stu-id="e0a9c-318">OrderDate</span></span>|<span data-ttu-id="e0a9c-319">Order Date</span><span class="sxs-lookup"><span data-stu-id="e0a9c-319">Order Date</span></span>|  
    |<span data-ttu-id="e0a9c-320">DueDate</span><span class="sxs-lookup"><span data-stu-id="e0a9c-320">DueDate</span></span>|<span data-ttu-id="e0a9c-321">Due Date</span><span class="sxs-lookup"><span data-stu-id="e0a9c-321">Due Date</span></span>|  
    |<span data-ttu-id="e0a9c-322">ShipDate</span><span class="sxs-lookup"><span data-stu-id="e0a9c-322">ShipDate</span></span>|<span data-ttu-id="e0a9c-323">Ship Date</span><span class="sxs-lookup"><span data-stu-id="e0a9c-323">Ship Date</span></span>|  
  
## <a name="next-step"></a><span data-ttu-id="e0a9c-324">siguiente paso</span><span class="sxs-lookup"><span data-stu-id="e0a9c-324">Next Step</span></span>  
 <span data-ttu-id="e0a9c-325">Para continuar este tutorial, vaya a la lección siguiente: [Lección 4: Marcar como tabla de fechas](lesson-3-mark-as-date-table.md).</span><span class="sxs-lookup"><span data-stu-id="e0a9c-325">To continue this tutorial, go to the next lesson: [Lesson 4: Mark as Date Table](lesson-3-mark-as-date-table.md).</span></span>  
  
  