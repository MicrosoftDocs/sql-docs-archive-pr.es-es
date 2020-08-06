---
title: Asistente para optimización basada en el uso (ayuda F1) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.usagebasedoptimizationwizard.f1
helpviewer_keywords:
- Usage-Based Optimization Wizard
ms.assetid: e5f5a938-ae7c-4f4e-9416-a7f94ac82763
author: minewiskan
ms.author: owend
ms.openlocfilehash: 517c122f79421294e1dfa562665948c4dc7bf95f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87747730"
---
# <a name="usage-based-optimization-wizard-f1-help"></a>Asistente para optimización basada en el uso (Ayuda F1)
  El Asistente para optimización basada en el uso es parecido en su resultado al Asistente para diseñar agregaciones, y se utiliza para diseñar agregaciones para una partición. No obstante, el Asistente para optimización basada en el uso diseña agregaciones en función de patrones de uso específicos de consultas registradas en un registro de consultas de una instancia de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Las agregaciones proporcionan mejoras de rendimiento al permitir [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] que recupere los totales calculados previamente directamente desde el almacenamiento de cubos en lugar de tener que volver a calcular los datos de un origen de datos subyacente para cada consulta.  
  
 Para abrir el Asistente para optimización basada en el uso desde [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] , abra el diseñador de cubos para un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] proyecto de y, a continuación, haga clic en la pestaña **agregaciones** . Haga clic en el botón **optimización basada** en el uso en la barra de herramientas.  
  
 Para abrir el Asistente para optimización basada en el uso desde dentro de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], conéctese a una base de datos [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] y, después, abra la carpeta **Cubos** . Seleccione un cubo y, a continuación, abra la carpeta **Grupos de medida** y expanda el grupo de medida que desea modificar. Haga clic con el botón derecho en la carpeta **Particiones** y, después, seleccione **Optimización basada en el uso**.  
  
 Para diseñar estas agregaciones, puede utilizar el Asistente para diseñar agregaciones. Este asistente le guía por los siguientes pasos:  
  
-   Seleccionar una configuración estándar o personalizada para las opciones de almacenamiento y almacenamiento en caché de una partición, grupo de medida o cubo.  
  
-   Proporcionar recuentos estimados o reales de los objetos a los que hace referencia la partición, el grupo de medida o el cubo.  
  
-   Especificar opciones y límites de agregación para optimizar el rendimiento de almacenamiento y de consulta de las agregaciones diseñadas.  
  
-   Guardar y, opcionalmente, procesar la partición, el grupo de medida o el cubo para generar las agregaciones definidas.  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] proporciona el Asistente para diseñar agregaciones para diseñar agregaciones basadas en el análisis estadístico de la estructura de la partición y ofrecer, de este modo, un diseño de agregaciones que pueda limitarse según el tamaño de almacenamiento o la ganancia de rendimiento estimada. Puede utilizar el Asistente para diseñar agregaciones para mejorar el rendimiento global de una partición, pero el diseño de la agregación no va destinado a las necesidades específicas de los usuarios de empresa. El Asistente para optimización basada en el uso puede proporcionar un diseño de agregaciones destinado a estas necesidades específicas, pero el asistente solo puede hacerlo si el registro de consultas para la instancia de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] contiene suficiente información para construir dichas consultas.  
  
 Generalmente, ambos asistentes se utilizan conjuntamente para mejorar el rendimiento durante la implementación y a lo largo del tiempo. El Asistente para diseñar agregaciones debe utilizarse en primer lugar, cuando se implementa inicialmente la partición (o el cubo o grupo de medida que contiene la partición), para proporcionar beneficios sobre el rendimiento general. Tras un período de tiempo durante el que habrá registrado las consultas de los usuarios de empresa para la partición en el registro de consultas, puede utilizar el Asistente para optimización basada en el uso para centrar la agregación en el diseño con el fin de optimizar el rendimiento y satisfacer los requisitos de las consultas de los usuarios de empresa.  
  
> [!NOTE]  
>  Para más información sobre cómo configurar el registro de consultas, vea [Configuring the Analysis Services Query Log (Configuración del registro de consultas de Analysis Services)](instances/log-operations-in-analysis-services.md?view=sql-server-2014#bkmk_querylog).  
  
## <a name="in-this-section"></a>En esta sección  
  
-   [Seleccione las particiones para modificar &#40;Asistente para optimización basada en el uso&#41;](select-partitions-to-modify-usage-based-optimization-wizard.md)  
  
-   [Especificar criterios de consulta &#40;Asistente para optimización basada en el uso&#41;](specify-query-criteria-usage-based-optimization-wizard.md)  
  
-   [Revise las consultas que se optimizarán &#40;Asistente para optimización basada en el uso&#41;](review-the-queries-that-will-be-optimized-usage-based-optimization-wizard.md)  
  
-   [Revise el uso de agregaciones &#40;Asistente para optimización basado en el uso&#41;](review-aggregation-usage-usage-based-optimiation-wizard.md)  
  
-   [Especificar recuentos de objetos &#40;Asistente para optimización basada en el uso&#41;](specify-object-counts-usage-based-optimization-wizard.md)  
  
-   [Establezca las opciones de agregación &#40;Asistente para optimización basada en el uso&#41;](set-aggregation-options-usage-based-optimization-wizard.md)  
  
-   [Finalización del asistente &#40;Asistente para optimización basada en el uso&#41;](completing-the-wizard-usage-based-optimization-wizard.md)  
  
## <a name="see-also"></a>Consulte también  
 [Agregaciones y diseños de agregaciones](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)   
 [Cubos en modelos multidimensionales](multidimensional-models/cubes-in-multidimensional-models.md)   
 [Asistente para diseñar agregaciones (ayuda F1)](aggregation-design-wizard-f1-help.md)   
 [Analysis Services asistentes &#40;datos multidimensionales&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  
