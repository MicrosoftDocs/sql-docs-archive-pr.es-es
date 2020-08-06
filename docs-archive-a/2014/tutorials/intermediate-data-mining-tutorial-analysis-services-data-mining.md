---
title: Tutorial intermedio de minería de datos (Analysis Services-minería de datos) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 404b31d5-27f4-4875-bd60-7b2b8613eb1b
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 090bcd8cc987da57a5c4bdf27e6782ae07b85719
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663871"
---
# <a name="intermediate-data-mining-tutorial-analysis-services---data-mining"></a>Tutorial intermedio de minería de datos (Analysis Services - Minería de datos)
  [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]proporciona un entorno integrado para crear y trabajar con modelos de minería de datos. Puede crear fácilmente enlaces con orígenes de datos, crear y probar varios modelos basados en los mismos datos e implementar los modelos para utilizarlos en análisis predictivos.  
  
 En el Tutorial básico de minería de datos, aprendió a utilizar [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] para crear una solución de minería de datos y generó tres modelos para una campaña de envío de correo directo con el fin de analizar el comportamiento de compra de los clientes e identificar a los compradores potenciales.  
  
 Este tutorial intermedio se basa en esa experiencia y presenta varios escenarios nuevos, incluidos algunos requisitos empresariales habituales, como el análisis de previsiones y de la cesta de la compra. Aprenderá a crear un modelo de serie temporal, un modelo de asociación y un modelo de agrupación en clústeres de secuencia. Por último, aprenderá a usar una red neuronal para explorar las correlaciones de los datos y a usar la regresión logística para las predicciones.  
  
 Las lecciones son independientes y se pueden completar por separado.  
  
 Para completar los siguientes tutoriales, debe estar familiarizado con las herramientas de minería de datos y los visores del modelo de minería de datos que se presentaron en el Tutorial básico de minería de datos.  
  
 En todos los escenarios se utiliza el origen de datos [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)], pero creará vistas del origen de datos diferentes para los distintos escenarios. Puede llevar a cabo las lecciones en cualquier orden siempre que cree primero el origen de datos.  
  
## <a name="lesson-scenarios"></a>Escenarios de las lecciones  
 Una vez finalizada correctamente la campaña de envío de correo directo, se le ha pedido que aplique sus conocimientos sobre minería de datos a fin de desarrollar modelos nuevos para los planes empresariales. Estos incluye las siguientes tareas:  
  
-   **Previsión:** Creará un modelo de *serie temporal* para pronosticar las ventas de productos en diferentes regiones de todo el mundo. Desarrollará modelos individuales para cada región y aprenderá a usar la *predicción cruzada*.  
  
-   Análisis de la cesta de la **compra:** Creará un *modelo de asociación*para analizar las agrupaciones de productos que se adquieren durante las visitas al [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] sitio de comercio electrónico. En función de este modelo de cesta de la compra, puede recomendar productos a los clientes.  
  
-   **Análisis de secuencias:** Cree un *modelo de agrupación en clústeres de secuencia*para analizar el orden en que los clientes compran productos. A partir de este modelo, puede planear cambios en el diseño del sitio web o en las ofertas de nuevos productos.  
  
-   **Análisis de factor:** Use un modelo de *red neuronal* para explorar las posibles causas de una calidad deficiente del servicio en los datos del centro de llamadas. Basándose en la información del modelo preliminar, creará un *modelo de regresión logística* para predecir las estrategias para mejorar la experiencia del cliente.  
  
## <a name="what-you-will-learn"></a>Aprendizaje  
 Este tutorial le enseñará a crear varios tipos de algoritmos de minería de datos y a trabajar con ellos. El tutorial está compuesto por las lecciones siguientes:  
  
 [Lección 1: crear la solución intermedia de minería de datos &#40;tutorial intermedio de minería de datos&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
 En esta lección creará un nuevo proyecto basado en la base de datos [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] que admite varias vistas del origen de datos nuevas y muchos más modelos de minería de datos.  
  
 [Lección 2: generar un escenario de previsión &#40;tutorial intermedio de minería de datos&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
 En esta lección aprenderá a crear un modelo de minería de datos que se pueda utilizar como parte de un escenario de previsión. Analizará también los modelos de minería de datos creados con el algoritmo de serie temporal de [!INCLUDE[msCoName](../includes/msconame-md.md)].  
  
 Creará modelos para regiones individuales y, a continuación, creará un modelo general que se pueda utilizar en la predicción cruzada.  
  
 [Lección 3: Generar un escenario de cesta de la compra &#40;Tutorial intermedio de minería de datos&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
 En esta lección agregará una nueva vista del origen de datos y aprenderá a trabajar con tablas anidadas y claves. A partir de estos datos, creará un modelo de minería de datos que se pueda utilizar como parte de un escenario de cesta de la compra. Analizará también los modelos de minería de datos creados con el algoritmo de asociación de [!INCLUDE[msCoName](../includes/msconame-md.md)].  
  
 [Lección 4: generar un escenario de agrupación en clústeres de secuencia &#40;tutorial intermedio de minería de datos&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
 En esta lección aprenderá a crear un modelo de minería de datos que se pueda utilizar como parte de un escenario de agrupación en clústeres de secuencia. Asimismo, aprenderá a explorar los modelos de minería de datos creados mediante el algoritmo de clústeres de secuencia de [!INCLUDE[msCoName](../includes/msconame-md.md)].  
  
 [Lección 5: Generar modelos de red neuronal y de regresión logística &#40;Tutorial intermedio de minería de datos&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
 En esta lección, creará varios modelos de minería de datos relacionados, utilizando los algoritmos de Red neural de Microsoft y de Regresión logística de Microsoft. También aprenderá a trabajar con vistas del origen de datos para explorar datos subyacentes de los modelos.  
  
## <a name="requirements"></a>Requisitos  
 Asegúrese de que los siguientes componentes estén instalados:  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] con la base de datos [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] .  
  
 Con el fin de mejorar la seguridad, las bases de datos de ejemplo no se instalan de forma predeterminada. Para instalar las bases de datos oficiales para [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , visite la página bases de datos de [ejemplo de Microsoft SQL](https://go.microsoft.com/fwlink/?LinkId=88417) y seleccione la versión adecuada de la base de datos de ejemplo.  
  
## <a name="see-also"></a>Consulte también  
 [Tutorial básico de minería de datos](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Tutorial DMX de Bike Buyer](../../2014/tutorials/bike-buyer-dmx-tutorial.md)   
 [Tutorial DMX de Market Basket](../../2014/tutorials/market-basket-dmx-tutorial.md)  
  
  
