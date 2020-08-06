---
title: Destino de procesamiento de particiones | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partitionprocessingdest.f1
helpviewer_keywords:
- partitions [Analysis Services], processing
- Partition Processing destination [Integration Services]
- destinations [Integration Services], Partition Processing
ms.assetid: 36c592ff-3f78-4a58-b496-31c1c8eee131
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d32306328f7a0575e55397d5209b4767d0cf1bd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87670467"
---
# <a name="partition-processing-destination"></a>Destino de procesamiento de particiones
  El destino de procesamiento de particiones carga y procesa una partición de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Para más información sobre particiones, vea [Particiones &#40;Analysis Services - Datos multidimensionales&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data).  
  
 El destino de procesamiento de particiones incluye las siguientes características:  
  
-   Opciones para ejecutar procesamiento incremental, completo o de actualización.  
  
-   Configuración de errores, para especificar si el procesamiento debe omitir los errores o detenerse después de una cantidad de errores especificada.  
  
-   Asignación de columnas de entrada para columnas de particiones.  
  
 Para más información sobre el procesamiento de objetos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vea [Opciones y valores de procesamiento &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-options-and-settings-analysis-services).  
  
> [!NOTE]  
>  Las tareas aquí descritas no se aplican a los modelos tabulares de Analysis Services.  No se pueden asignar las columnas de entrada a las de partición para los modelos tabulares. En su lugar puede usar la tarea Ejecutar DDL de Analysis Services [Analysis Services Execute DDL Task](../control-flow/analysis-services-execute-ddl-task.md) para procesar la partición.  
  
## <a name="configuration-of-the-partition-processing-destination"></a>Configuración del destino de procesamiento de particiones  
 El destino de procesamiento de particiones usa un administrador de conexiones de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] para conectarse al proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o la instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] que contiene los cubos y particiones que procesa el destino. Para más información, consulte [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).  
  
 Este destino tiene una entrada. No admite una salida de error.  
  
 Puede establecer propiedades a través del Diseñador de [!INCLUDE[ssIS](../../includes/ssis-md.md)] o mediante programación.  
  
 Para obtener más información sobre las propiedades que se pueden configurar en el cuadro de diálogo **Editor de destino de procesamiento de particiones** , haga clic en uno de los siguientes temas:  
  
-   [Editor de destino de procesamiento de particiones &#40;página Administrador de conexiones&#41;](../partition-processing-destination-editor-connection-manager-page.md)  
  
-   [Editor de destino de procesamiento de particiones &#40;página Asignaciones&#41;](../partition-processing-destination-editor-mappings-page.md)  
  
-   [Editor de destino de procesamiento de particiones &#40;página Avanzadas&#41;](../partition-processing-destination-editor-advanced-page.md)  
  
 El cuadro de diálogo **Editor avanzado** indica las propiedades que se pueden establecer mediante programación. Para obtener más información acerca de las propiedades que puede establecer a través del cuadro de diálogo **Editor avanzado** o mediante programación, haga clic en uno de los temas siguientes:  
  
-   [Common Properties](../common-properties.md)  
  
-   [Propiedades personalizadas del destino de procesamiento de particiones](partition-processing-destination-custom-properties.md)  
  
 Para más información sobre cómo establecer las propiedades, vea [Establecer las propiedades de un componente de flujo de datos](set-the-properties-of-a-data-flow-component.md).  
  
  
