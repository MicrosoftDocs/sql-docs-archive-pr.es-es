---
title: Herramientas de cálculo (pestaña acciones, diseñador de cubos) (Analysis Services-datos multidimensionales) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.actionsview.calculationtoolspane.f1
ms.assetid: a3370370-43cd-4cc2-bb9f-c0d988b96f05
author: minewiskan
ms.author: owend
ms.openlocfilehash: 123fa38ea2decb6af914e93fcefda4508f08545e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87670075"
---
# <a name="calculation-tools-actions-tab-cube-designer-analysis-services---multidimensional-data"></a>Herramientas de cálculo (pestaña Acciones, Diseñador de cubos) (Analysis Services - Datos multidimensionales)
  Use el panel **Herramientas de cálculo** en la pestaña **Acciones** del Diseñador de cubos para explorar metadatos, funciones y plantillas disponibles para utilizarlas en acciones, acciones de obtención de detalles y acciones de informe.  
  
## <a name="options"></a>Opciones  
 **Metadata**  
 Muestra los metadatos del cubo seleccionado.  
  
 Arrastre el elemento seleccionado al panel **Editor de Formulario de acción**, **Editor de Formulario de acción de obtención de detalles**o **Editor de Formulario de acción de informe** para incluir la sintaxis MDX (expresiones multidimensionales) del elemento en la ubicación seleccionada del panel.  
  
 **Funciones**  
 Muestra las funciones disponibles para las expresiones y condiciones.  
  
 Arrastre el elemento seleccionado al panel **Editor de Formulario de acción estándar**, **Editor de Formulario de acción de obtención de detalles**o **Editor de Formulario de acción de informe** para incluir la sintaxis MDX de dicho elemento en la ubicación seleccionada del panel.  
  
> [!NOTE]  
>  En el modo de proyecto, el cuadro de diálogo **Herramientas de cálculo** lee la información de esta opción desde un archivo XML con el nombre MDXFunctions.xml, incluido en [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. En el modo en línea, la información de esta opción se recupera del conjunto de filas del esquema MDSCHEMA_FUNCTIONS para la instancia.  
  
 **Templates** (Plantillas [C++])  
 Muestra las plantillas predeterminadas disponibles para las acciones.  
  
 Arrastre el elemento seleccionado al panel **Editor de Formulario de acción estándar**, **Editor de Formulario de acción de obtención de detalles**o **Editor de Formulario de acción de informe** para incluir la sintaxis MDX de dicho elemento en la ubicación seleccionada del panel.  
  
## <a name="context-menu"></a>Menú contextual  
 Las siguientes opciones están disponibles en el menú contextual que se muestra al hacer clic con el botón derecho en un elemento del panel **Herramientas de cálculo** :  
  
|Opción|Definición|  
|------------|----------------|  
|**Copiar**|Seleccione esta opción para copiar el elemento seleccionado en **Metadatos** o **Funciones** en el Portapapeles.<br /><br /> Tenga en cuenta que esta opción no se muestra si se selecciona **plantillas** . Tenga en cuenta también que esta opción está deshabilitada si no se puede copiar el miembro seleccionado, como la carpeta **sets** de una dimensión mostrada en **metadatos** o la carpeta del grupo de funciones para una función mostrada en **funciones**.|  
|**Filtrar miembros**|Seleccione esta opción para mostrar el cuadro de diálogo **Filtrar miembros** y filtrar los miembros del elemento seleccionado en **Metadatos**. Para más información sobre el cuadro de diálogo **Filtrar miembros**, vea [Cuadro de diálogo Filtrar miembros &#40;Analysis Services - Datos multidimensionales&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).<br /><br /> Tenga en cuenta que esta opción solo se muestra si se selecciona **metadatos** . Tenga en cuenta también que esta opción solo está habilitada si se selecciona un nivel para un atributo en los **metadatos**.|  
|**Agregar plantilla**|Seleccione esta opción para agregar al cubo una nueva acción, una acción de obtención de detalles o una acción de informe según la plantilla seleccionada y para mostrar, respectivamente, el **Editor de Formulario de acción estándar**, el **Editor de Formulario de acción de obtención de detalles**o el **Editor de Formulario de acción de informe**.<br /><br /> Nota: esta opción solo se muestra si se selecciona **metadatos** .|  
  
## <a name="see-also"></a>Consulte también  
 [Aspectos básicos de scripting de MDX &#40;Analysis Services&#41;](multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)   
 [Acciones &#40;diseñador de cubos&#41; &#40;Analysis Services de datos multidimensionales&#41;](actions-cube-designer-analysis-services-multidimensional-data.md)   
 [Barra de herramientas &#40;pestaña acciones, diseñador de cubos&#41; &#40;Analysis Services-datos multidimensionales&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Organizador de acciones &#40;pestaña acciones, diseñador de cubos&#41; &#40;Analysis Services de datos multidimensionales&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md)   
 [Editor de formulario de acción &#40;pestaña acciones, diseñador de cubos&#41; &#40;Analysis Services-datos multidimensionales&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md)   
 [Editor de formulario de acción de obtención de detalles &#40;pestaña acciones, diseñador de cubos&#41; &#40;Analysis Services-datos multidimensionales&#41;](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)   
 [Editor de formulario de acción de informe &#40;pestaña acciones, diseñador de cubos&#41; &#40;Analysis Services-datos multidimensionales&#41;](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)  
  
  
