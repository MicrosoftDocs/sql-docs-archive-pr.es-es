---
title: Cuadro de diálogo plantilla de asignación de nombres de nivel (Analysis Services-datos multidimensionales) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.levelnamingtemplatedialog.f1
helpviewer_keywords:
- Level Naming Template dialog box
ms.assetid: 96cad715-213e-4eac-9003-130a2f5fc985
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4dd704e619e49f0dd1adb8fed8f1e743b61309af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87752473"
---
# <a name="level-naming-template-dialog-box-analysis-services---multidimensional-data"></a>Cuadro de diálogo Plantilla de asignación de nombres de nivel (Analysis Services - Datos multidimensionales)
  Use el cuadro de diálogo **Plantilla de asignación de nombres de nivel** de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] para crear la plantilla de asignación de nombres de nivel para un atributo primario de una dimensión. Para obtener más información sobre el nivel de nomenclatura de plantillas, vea [Elemento NamingTemplate &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/namingtemplate-element-assl). Para mostrar el cuadro de diálogo **plantilla de asignación de nombres de nivel** , haga clic en el botón de puntos suspensivos (**...**) del `NamingTemplate` valor de una traducción de un atributo en el panel **detalles de traducción** de la pestaña **traducciones** del **Diseñador de dimensiones**.  
  
## <a name="options"></a>Opciones  
  
|Término|Definición|  
|----------|----------------|  
|**Definir la plantilla de nivel**|Muestra una cuadrícula en la que se puede diseñar la jerarquía de niveles del atributo primario. La cuadrícula contiene las columnas siguientes:<br /><br /> **Nivel**: muestra la posición ordinal del nivel para el que se utiliza el nombre especificado en **nombre** . Para agregar una nueva plantilla de asignación de nombres de nivel, seleccione **Nombre** en la fila que contenga un asterisco (\*) en **Nivel**.<br /><br /> **Nombre**: contiene la plantilla de asignación de nombres usada para el nivel indicado en **nivel**. Si desea agregar un marcador de posición para la posición ordinal del nivel en la plantilla de asignación de nombres, agregue un asterisco (*). Para agregar un asterisco como parte del nombre creado por la plantilla de asignación de nombres, agregue dos asteriscos ( \* \* ).|  
|**Borrar todo**|Seleccione esta opción para borrar todas las filas de **Definir la plantilla de nivel**.|  
|**Resultado**|Muestra la plantilla de asignación de nombres de nivel generada en el cuadro de diálogo.|  
  
## <a name="see-also"></a>Consulte también  
 [Analysis Services diseñadores y cuadros de diálogo &#40;datos multidimensionales&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Traducciones &#40;diseñador de dimensiones&#41; &#40;Analysis Services de datos multidimensionales&#41;](translations-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
