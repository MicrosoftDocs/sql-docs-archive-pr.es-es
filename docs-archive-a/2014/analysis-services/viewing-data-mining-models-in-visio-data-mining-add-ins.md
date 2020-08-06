---
title: Ver modelos de minería de datos en Visio (complementos de minería de datos) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- diagram, modifying
- templates [Visio]
- shapes, data mining
- diagram
ms.assetid: 5841adea-6650-4fae-8526-26af33edbede
author: minewiskan
ms.author: owend
ms.openlocfilehash: f3c1e63c058295b93e2562c64a6df90a30273a10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87671190"
---
# <a name="viewing-data-mining-models-in-visio-data-mining-add-ins"></a>Ver los modelos de minería de datos en Visio (Complementos de minería de datos)
  Las formas de Visio para minería de datos le permiten conectarse a un servidor y crear un diagrama que represente un modelo de minería de datos existente. Posteriormente, se pueden personalizar los diagramas mediante los controles de Visio, pero también puede explorar en profundidad datos, exponer algunas de las estadísticas subyacentes y trabajar con el modelo subyacente.  
  
## <a name="building-a-model-diagram"></a>Crear un diagrama del modelo  
 Al abrir el archivo que contiene las formas de Visio para la minería de datos, el panel **formas** muestra las formas siguientes.  
  
 Si no ve las formas de minería de datos al abrir Visio, abra el archivo de plantilla desde la carpeta de instalación.  
  
 ![DM](media/dm-stencil.gif "DM")  
  
 Para usar una forma, arrástrela hasta la página. Cada forma abre un asistente diferente que ayuda a seleccionar datos de origen, establecer opciones específicas del tipo de diagrama y especificar sombreado y otras opciones de presentación.  
  
 En la tabla siguiente se muestran los tipos de modelos que se pueden usar con cada tipo de diagrama.  
  
|Forma de Visio|Modelos admitidos|  
|-----------------|----------------------|  
|Árbol de decisión|Esta forma se usa para modelos basados en los algoritmos de árboles de decisión o de regresión linear.|  
|Red de dependencias|Esta forma se usa para modelos basados en cualquiera de los algoritmos siguientes: Bayes naive, Árboles de decisión o Reglas de asociación.|  
|Clúster|Esta forma se usa para modelos basados en algoritmos de clústeres.|  
  
 El asistente puede ofrecer distintas opciones en función del tipo de datos del modelo de minería de datos. Por ejemplo, las columnas que contienen números continuos se visualizan de forma diferente que las variables de categorías.  
  
## <a name="working-with-completed-shapes"></a>Trabajar con formas completadas  
 Una vez haya completado el diagrama, puede utilizarlo para examinar el modelo de minería de datos o para mejorara el diagrama e incluirlo en presentaciones.  
  
### <a name="visio-menus"></a>Menús de Visio  
 Visio proporciona una variedad de controles de representación, temas y menús contextuales para ayudarle a mejorar los diagramas.  
  
-   Los temas de Visio se usan para modificar los colores del diagrama.  
  
-   Cambie los conectores o el diseño del diagrama.  
  
### <a name="data-mining-menus"></a>Menús de minería de datos  
 Estas barras de herramientas y elementos de menú los proporcionan los complementos específicos de cada forma o tipo de modelo  
  
-   Cada tipo de diagrama tiene un menú contextual para la forma que permite tener acceso a opciones especiales. Aunque muchas de las opciones de este menú son comunes para todas las formas de Visio, algunas son exclusivas de las plantillas de minería de datos  
  
     Por ejemplo, en un diagrama de árbol de decisión, puede hacer clic en un nodo y, después, contraer los nodos secundarios para que el diagrama sea más sencillo, o trasladar los nodos secundarios a otra página distinta.  
  
-   Dado que la forma está vinculada a los datos del modelo, también se puede realizar cierto nivel de exploración con el diagrama:  
  
     Filtrar los nodos que se muestran, o cambiar el nivel del árbol o la profundidad del gráfico.  
  
     Acercar secciones específicas, buscar nodos que contengan un determinado atributo o filtrar un gráfico de dependencias por sus bordes (probabilidad).  
  
## <a name="walkthroughs"></a>Tutoriales  
 Para obtener ejemplos de cómo trabajar con un diagrama completado y cómo interpretarlo, vea los temas siguientes:  
  
 [Tutorial del diagrama del clúster](cluster-diagram-walkthrough-data-mining-add-ins.md)  
  
 [Tutorial del diagrama de red de dependencias](dependency-network-diagram-walkthrough-data-mining-add-ins.md)  
  
 [Tutorial del diagrama de árbol de decisión](decision-tree-diagram-walkthrough-data-mining-add-ins.md)  
  
## <a name="see-also"></a>Consulte también  
 [Examinar modelos en Excel &#40;SQL Server complementos de minería de datos&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
