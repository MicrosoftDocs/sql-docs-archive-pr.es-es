---
title: Cuadro de diálogo procesar (Analysis Services-datos multidimensionales) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.processdialog.f1
ms.assetid: c065248c-9001-4f0c-928f-9c59eccb618b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 369c121713894bba9b2ce6c40aa2869de49eaa72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750258"
---
# <a name="process-dialog-box-analysis-services---multidimensional-data"></a>Cuadro de diálogo Procesar (Analysis Services - Datos multidimensionales)
  Use el cuadro de diálogo **Proceso** de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] y [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] para procesar objetos de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Para mostrar el cuadro de diálogo **Procesar** de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] :  
  
-   Haga clic con el botón derecho en un proyecto, cubo, dimensión o estructura de minería de datos de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] en el **Explorador de soluciones** y seleccione **Procesar**.  
  
-   Seleccione **Procesar** en la barra de herramientas en todas las páginas del **Diseñador de cubos**, en todas las páginas del **Diseñador de dimensiones**o en las páginas de la **Estructura de minería de datos** y **Modelos de minería de datos** del **Diseñador de modelos de minería de datos**.  
  
-   Haga clic con el botón derecho en un modelo de minería de datos de la página **Modelos de minería de datos** del **Diseñador de modelos de minería de datos** y seleccione **Procesar estructura de minería de datos y todos los modelos** o **Procesar modelo**.  
  
 Para mostrar el cuadro de diálogo **Procesar** de **SQL Server Management Studio** :  
  
-   Haga clic con el botón derecho en una base de datos, cubo, grupo de medida, partición, dimensión, estructura de minería de datos o modelo de minería de datos de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] en el **Explorador de objetos** y seleccione **Procesar**.  
  
## <a name="options"></a>Opciones  
 **Lista de objetos**  
 Seleccione los objetos de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] que desea procesar, así como las opciones de proceso y la configuración que desea aplicar. La cuadrícula contiene las columnas siguientes:  
  
 **Nombre de objeto**  
 Muestra el nombre del objeto que se va a procesar. El icono que se muestra a la izquierda del nombre indica el tipo de objeto.  
  
 **Tipo**  
 Muestra el tipo de objeto que se va a procesar.  
  
 **Opciones de proceso**  
 Seleccione el tipo de procesamiento que desea realizar para el objeto seleccionado. Para obtener más información sobre las opciones de procesamiento disponibles, vea [procesamiento de objetos de modelo multidimensional](multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 **Configuración**  
 Muestra el hipervínculo **Configurar** si elige **Procesar incremental** en **Opciones de proceso** para cubos, grupos de medida o particiones. Haga clic en **Configurar** para abrir el cuadro de diálogo **Actualización incremental** . Para obtener más información sobre el cuadro de diálogo **Actualización incremental**, vea [Cuadro de diálogo Actualización incremental &#40;Analysis Services - Datos multidimensionales&#41;](incremental-update-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Remove**  
 Haga clic para quitar los elementos seleccionados de la **Lista de objetos**.  
  
 **Análisis de impacto**  
 Haga clic para abrir el cuadro de diálogo **Análisis de impacto** y mostrar los objetos a los que afectará la tarea de procesamiento. Para obtener más información sobre el cuadro de diálogo **Análisis de impacto**, vea [Cuadro de diálogo Análisis de impacto &#40;Analysis Services - Datos multidimensionales&#41;](impact-analysis-dialog-box-analysis-services-multidimensional-data.md).  
  
> [!NOTE]  
>   Esta opción se deshabilitará si se selecciona la opción **Objetos afectados por el proceso** en el cuadro de diálogo **Cambiar configuración** .  
  
 **Cambiar configuración**  
 Haga clic para abrir el cuadro de diálogo **Cambiar configuración** y cambiar la configuración que regirá el procesamiento de los objetos seleccionados, incluida la configuración de procesamiento por lotes, la configuración de reescritura y la configuración de errores de claves de dimensiones. Para obtener más información sobre el cuadro de diálogo **Cambiar configuración**, vea [Cuadro de diálogo Cambiar configuración &#40;Analysis Services - Datos multidimensionales&#41;](change-settings-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Ejecutar**  
 Haga clic para procesar los objetos.  
  
## <a name="see-also"></a>Consulte también  
 [Analysis Services diseñadores y cuadros de diálogo &#40;datos multidimensionales&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Cuadro de diálogo progreso del proceso &#40;Analysis Services de datos multidimensionales&#41;](process-progress-dialog-box-analysis-services-multidimensional-data.md)  
  
  
