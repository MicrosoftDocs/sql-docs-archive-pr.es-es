---
title: Herramientas de cálculo (pestaña KPI, diseñador de cubos) (Analysis Services-datos multidimensionales) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.kpisview.calculationtoolspane.f1
ms.assetid: c030c725-7763-4c23-9988-4b274a88fc31
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7bb8470173b0a413795fb7b5e3213bb50aa8ee43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87670074"
---
# <a name="calculation-tools-kpis-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="7b3ad-102">Herramientas de cálculo (pestaña KPI, Diseñador de cubos) (Analysis Services - Datos multidimensionales)</span><span class="sxs-lookup"><span data-stu-id="7b3ad-102">Calculation Tools (KPIs Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="7b3ad-103">Use el panel **Herramientas de cálculo** en la pestaña **KPI** del Diseñador de cubos para explorar metadatos, funciones y plantillas disponibles para usarlas en indicadores clave de rendimiento (KPI).</span><span class="sxs-lookup"><span data-stu-id="7b3ad-103">Use the **Calculation Tools** pane on the **KPIs** tab in Cube Designer to explore metadata, functions, and templates available for use in Key Performance Indicators (KPIs).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b3ad-104">Este panel solo se muestra en la vista de formulario.</span><span class="sxs-lookup"><span data-stu-id="7b3ad-104">This pane is displayed only in form view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7b3ad-105">Opciones</span><span class="sxs-lookup"><span data-stu-id="7b3ad-105">Options</span></span>  
 <span data-ttu-id="7b3ad-106">**Metadata**</span><span class="sxs-lookup"><span data-stu-id="7b3ad-106">**Metadata**</span></span>  
 <span data-ttu-id="7b3ad-107">Muestra los metadatos del cubo seleccionado.</span><span class="sxs-lookup"><span data-stu-id="7b3ad-107">Displays the metadata for the selected cube.</span></span>  
  
 <span data-ttu-id="7b3ad-108">Arrastre el elemento seleccionado al panel **Editor de Formulario de KPI** para incluir la sintaxis de Expresiones multidimensionales (MDX) para dicho elemento en la ubicación seleccionada del panel.</span><span class="sxs-lookup"><span data-stu-id="7b3ad-108">Drag a selected element to the **KPI Form Editor** pane to include the Multidimensional Expressions (MDX) syntax for that element at the selected location in the pane.</span></span>  
  
 <span data-ttu-id="7b3ad-109">**Funciones**</span><span class="sxs-lookup"><span data-stu-id="7b3ad-109">**Functions**</span></span>  
 <span data-ttu-id="7b3ad-110">Muestra las funciones disponibles para las expresiones y condiciones.</span><span class="sxs-lookup"><span data-stu-id="7b3ad-110">Displays the functions available for expressions and conditions.</span></span>  
  
 <span data-ttu-id="7b3ad-111">Arrastre el elemento seleccionado al panel **Editor de Formulario de KPI** para incluir la sintaxis MDX para dicho elemento en la ubicación seleccionada del panel.</span><span class="sxs-lookup"><span data-stu-id="7b3ad-111">Drag a selected element to the **KPI Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b3ad-112">En el modo de proyecto, el cuadro de diálogo **Herramientas de cálculo** lee la información de esta opción desde un archivo XML con el nombre MDXFunctions.xml, incluido en [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b3ad-112">In project mode, the **Calculation Tools** dialog box reads information for this option from an XML file named MDXFunctions.xml, included with [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="7b3ad-113">En el modo en línea, la información de esta opción se recupera del conjunto de filas del esquema MDSCHEMA_FUNCTIONS para la instancia.</span><span class="sxs-lookup"><span data-stu-id="7b3ad-113">In online mode, information for this option is retrieved from the MDSCHEMA_FUNCTIONS schema rowset for the instance.</span></span>  
  
 <span data-ttu-id="7b3ad-114">**Templates** (Plantillas [C++])</span><span class="sxs-lookup"><span data-stu-id="7b3ad-114">**Templates**</span></span>  
 <span data-ttu-id="7b3ad-115">Muestra las plantillas predeterminadas disponibles para los KPI.</span><span class="sxs-lookup"><span data-stu-id="7b3ad-115">Displays the predefined templates available for KPIs.</span></span>  
  
 <span data-ttu-id="7b3ad-116">Arrastre el elemento seleccionado al panel **Editor de Formulario de KPI** para incluir la sintaxis MDX para dicho elemento en la ubicación seleccionada del panel.</span><span class="sxs-lookup"><span data-stu-id="7b3ad-116">Drag a selected element to the **KPI Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="7b3ad-117">Menú contextual</span><span class="sxs-lookup"><span data-stu-id="7b3ad-117">Context Menu</span></span>  
 <span data-ttu-id="7b3ad-118">Las siguientes opciones están disponibles en el menú contextual que se muestra al hacer clic con el botón derecho en un elemento del panel **Herramientas de cálculo** :</span><span class="sxs-lookup"><span data-stu-id="7b3ad-118">The following options are available in the context menu displayed by right-clicking an element in the **Calculation Tools** pane:</span></span>  
  
 <span data-ttu-id="7b3ad-119">**Copiar**</span><span class="sxs-lookup"><span data-stu-id="7b3ad-119">**Copy**</span></span>  
 <span data-ttu-id="7b3ad-120">Seleccione esta opción para copiar el elemento seleccionado en **Metadatos** o **Funciones** en el Portapapeles.</span><span class="sxs-lookup"><span data-stu-id="7b3ad-120">Select to copy the selected element in **Metadata** or **Functions** to the Clipboard.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b3ad-121"> No se mostrará esta opción si se selecciona **Plantillas** .</span><span class="sxs-lookup"><span data-stu-id="7b3ad-121">This option is not displayed if **Templates** is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b3ad-122"> Se deshabilitará esta opción si no es posible copiar el miembro seleccionado, al igual que la carpeta **Conjuntos** de una dimensión mostrada en **Metadatos** o la carpeta del grupo de función para una función mostrada en **Funciones**.</span><span class="sxs-lookup"><span data-stu-id="7b3ad-122">This option is disabled if the selected member cannot be copied, such as the **Sets** folder of a dimension displayed in **Metadata** or the function group folder for a function displayed in **Functions**.</span></span>  
  
 <span data-ttu-id="7b3ad-123">**Filtrar miembros**</span><span class="sxs-lookup"><span data-stu-id="7b3ad-123">**Filter Members**</span></span>  
 <span data-ttu-id="7b3ad-124">Seleccione esta opción para mostrar el cuadro de diálogo **Filtrar miembros** y filtrar los miembros del elemento seleccionado en **Metadatos**.</span><span class="sxs-lookup"><span data-stu-id="7b3ad-124">Select to display the **Filter Members** dialog box and filter members displayed for the selected element in **Metadata**.</span></span> <span data-ttu-id="7b3ad-125">Para más información sobre el cuadro de diálogo **Filtrar miembros**, vea [Cuadro de diálogo Filtrar miembros &#40;Analysis Services - Datos multidimensionales&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).</span><span class="sxs-lookup"><span data-stu-id="7b3ad-125">For more information about the **Filter Members** dialog box, see [Filter Members Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b3ad-126"> Solo se mostrará esta opción si se selecciona **Metadatos** .</span><span class="sxs-lookup"><span data-stu-id="7b3ad-126">This option is displayed only if **Metadata** is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b3ad-127"> Solo se habilitará esta opción si se selecciona un nivel para un atributo en **Metadatos**.</span><span class="sxs-lookup"><span data-stu-id="7b3ad-127">This option is enabled only if a level for an attribute is selected in **Metadata**.</span></span>  
  
 <span data-ttu-id="7b3ad-128">**Agregar plantilla**</span><span class="sxs-lookup"><span data-stu-id="7b3ad-128">**Add Template**</span></span>  
 <span data-ttu-id="7b3ad-129">Seleccione esta opción para agregar un nuevo miembro calculado, un conjunto con nombre o un comando de un script en la plantilla seleccionada al script del cubo y mostrar el **Editor de Formulario de KPI** en la vista de formulario.</span><span class="sxs-lookup"><span data-stu-id="7b3ad-129">Select to add a new calculated member, named set, or script command based on the selected template to the cube script and display the **KPI Form Editor** in form view.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b3ad-130"> Solo se mostrará esta opción si se selecciona **Metadatos** .</span><span class="sxs-lookup"><span data-stu-id="7b3ad-130">This option is displayed only if **Metadata** is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b3ad-131">Consulte también</span><span class="sxs-lookup"><span data-stu-id="7b3ad-131">See Also</span></span>  
 <span data-ttu-id="7b3ad-132">[Diseñador de cubos &#40;Analysis Services de datos multidimensionales&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7b3ad-132">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="7b3ad-133">[KPI &#40;diseñador de cubos&#41; &#40;Analysis Services de datos multidimensionales&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7b3ad-133">[KPIs &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="7b3ad-134">[Barra de herramientas &#40;pestaña KPI, diseñador de cubos&#41; &#40;Analysis Services de datos multidimensionales&#41;](toolbar-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7b3ad-134">[Toolbar &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="7b3ad-135">[Organizador de KPI &#40;pestaña KPI, diseñador de cubos&#41; &#40;Analysis Services de datos multidimensionales&#41;](kpi-organizer-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7b3ad-135">[KPI Organizer &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](kpi-organizer-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="7b3ad-136">[Editor de formulario de KPI &#40;pestaña KPI, diseñador de cubos&#41; &#40;Analysis Services de datos multidimensionales&#41;](kpi-form-editor-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7b3ad-136">[KPI Form Editor &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](kpi-form-editor-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="7b3ad-137">Explorador de KPI &#40;pestaña KPI, diseñador de cubos&#41; &#40;Analysis Services de datos multidimensionales&#41;</span><span class="sxs-lookup"><span data-stu-id="7b3ad-137">KPI Browser &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](kpi-browser-kpis-tab-cube-designer-analysis-services-multidimensional-data.md)  
  
  