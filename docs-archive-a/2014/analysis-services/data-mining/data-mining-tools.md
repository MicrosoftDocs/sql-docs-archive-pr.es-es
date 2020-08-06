---
title: Herramientas de minería de datos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- tools [Analysis Services]
- mining models [Analysis Services], tools
- data mining [Analysis Services], tools
- data mining [Analysis Services], development
ms.assetid: 003ada6a-0bcd-4f16-8c34-1a9ffc75cd2c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4be2f343f0fb7969f76b63ec1eb1677c1c9e589f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87677957"
---
# <a name="data-mining-tools"></a>Herramientas de minería de datos
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] proporciona las siguientes herramientas que puede utilizar para crear soluciones de minería de datos:  
  
-   El **Asistente para minería de datos** de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] facilita la creación de estructuras y de modelos de minería de datos, usando orígenes de datos relacionales o datos multidimensionales en cubos.  
  
     En el asistente, elija los datos que desee utilizar y, a continuación, aplique técnicas de minería de datos específicas, como agrupación en clústeres, redes neurales o modelado de series temporales.  
  
-   **y** disponen de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] visores de modelos [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]para explorar los modelos de minería de datos una vez creados.  Puede examinar los modelos mediante visores adaptados a cada algoritmo o analizar con mayor profundidad utilizando el visor de contenido del modelo.  
  
-   El **Generador de consultas de predicción** se proporciona en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] y [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] para ayudarle a crear consultas de predicción. También puede probar la exactitud de los modelos respecto a un conjunto de datos de exclusión o datos externos, o utilizar validación cruzada para evaluar la calidad del conjunto de datos.  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] es la interfaz en la que administra las soluciones de minería de datos implementadas en una instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Puede volver a procesar las estructuras y modelos para actualizar los datos que contienen.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]contiene herramientas que puede utilizar para limpiar datos, automatizar tareas como la creación de predicciones y la actualización de modelos, y para crear soluciones de minería de texto.  
  
 Las siguientes secciones proporcionan más información sobre las herramientas de minería de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="data-mining-wizard"></a>Asistente para minería de datos  
 Utilice el Asistente para minería de datos para empezar a crear soluciones de minería de datos. El asistente es rápido y sencillo, y le guía en el proceso de creación de una estructura de minería de datos y un modelo inicial de minería de datos relacionado. Asimismo, incluye las tareas necesarias para seleccionar un tipo de algoritmo y un origen de datos, y para definir los datos del caso usados para el análisis.  
  
 **Para más información:** [Asistente para minería de datos &#40;Analysis Services - Minería de datos&#41;](data-mining-wizard-analysis-services-data-mining.md).  
  
## <a name="data-mining-designer"></a>Data Mining Designer  
 Después de crear una estructura y modelo de minería de datos mediante el Asistente para minería de datos, puede utilizar el Diseñador de minería de datos desde [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] para trabajar con las estructuras y modelos de minería de datos existentes.  
  
 El diseñador incluye herramientas para estas tareas:  
  
-   Modificar las propiedades de las estructuras de minería de datos, agregar columnas y crear alias de columna, cambiar el método de discretización o la distribución de valores esperada.  
  
-   Agregar nuevos modelos a una estructura existente; copiar modelos, cambiar las propiedades o metadatos del modelo o definir filtros en un modelo de minería de datos.  
  
-   Examinar los patrones y reglas que incluye el modelo; explorar asociaciones o árboles de decisión. Obtener estadísticas detalladas sobre  
  
     Se proporcionan visores personalizados para cada tiempo del modelo, para ayudarle a analizar sus datos y explorar los patrones que revela la minería de datos.  
  
-   Validar modelos creando gráficos de elevación o analizando la curva de ganancia de los modelos. Comparar modelos utilizando matrices de clasificación, o validar un conjunto de datos y sus modelos utilizando la validación cruzada.  
  
-   Crear predicciones y consultas de contenido en los modelos de minería de datos existentes. Compilar consultas únicas, o configurar consultas para generar predicciones para tablas de datos externos completas.  
  
 **Para obtener más información:** [Diseñador de minería de datos](data-mining-designer.md)  
  
## <a name="sql-server-management-studio"></a>SQL Server Management Studio  
 Después de crear e implementar los modelos de minería de datos en un servidor, puede utilizar [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] para administrar la base de datos [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] que hospeda los objetos de minería de datos. También puede seguir realizando tareas que utilizan el modelo, como explorar modelos, procesar nuevos datos y crear predicciones.  
  
 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] también contiene editores de consultas que puede usar para diseñar y ejecutar consultas de extensiones de minería de datos (DMX) o trabajar con objetos de minería de datos con XMLA.  
  
## <a name="integration-services-data-mining-tasks-and-transformations"></a>Transformaciones y tareas de minería de datos en Integration Services  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]proporciona muchos componentes que admiten la minería de datos.  
  
 Algunas herramientas de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] están diseñadas para ayudar a automatizar tareas de datos comunes, incluida la predicción, la compilación de modelos y el procesamiento. Por ejemplo:  
  
-   Crear un paquete de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] que actualice automáticamente el modelo cada vez que el conjunto de datos se actualice con nuevos clientes  
  
-   Realizar una segmentación personalizada o un muestreo personalizado de los registros del caso.  
  
-   Generar automáticamente modelos pasados en parámetros.  
  
 Sin embargo, también puede utilizar la minería de datos en un flujo de trabajo de paquetes, como una entrada a otros procesos. Por ejemplo:  
  
-   Usar valores de probabilidad generados por el modelo para ponderar las puntuaciones de la minería de texto u otras tareas de clasificación.  
  
-   Generar automáticamente predicciones basadas en datos anteriores y utilizar esos valores para evaluar la validez de nuevos datos.  
  
-   Usar la regresión logística para segmentar los clientes de entrada por riesgo.  
  
 **Para más información:** [Proyectos relacionados para soluciones de minería de datos](data-mining-solutions.md)  
  
## <a name="see-also"></a>Consulte también  
 [Referencia de extensiones de minería de datos &#40;DMX&#41;](/sql/dmx/data-mining-extensions-dmx-reference)   
 [Tareas y procedimientos del modelo de minería de datos](mining-model-tasks-and-how-tos.md)   
 [Tareas y procedimientos del visor de modelos de minería de datos](mining-model-viewer-tasks-and-how-tos.md)   
 [Soluciones de minería de datos](data-mining-solutions.md)  
  
  
