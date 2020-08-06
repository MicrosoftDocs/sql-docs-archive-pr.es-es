---
title: Examinar un modelo usando el visor Bayes Naive de Microsoft | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- discrimination [Analysis Services]
- naive bayes model [Analysis Services]
- Bayesian classifiers
- mining model content, viewing
- predictive modeling [Analysis Services]
- Naive Bayes Viewer [Analysis Services]
- data mining [Analysis Services], predictive modeling
- Microsoft Naive Bayes Viewer
- histograms [Analysis Services]
- mining models [Analysis Services], predictive modeling
- dependencies [Analysis Services]
ms.assetid: 19743095-63c1-4486-8c1d-2efc143243be
author: minewiskan
ms.author: owend
ms.openlocfilehash: 03469e73d82a389426f91d8757630f50fe78fc55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87677979"
---
# <a name="browse-a-model-using-the-microsoft-naive-bayes-viewer"></a>Examinar un modelo usando el visor Bayes naive de Microsoft
  El [!INCLUDE[msCoName](../../includes/msconame-md.md)] visor Bayes Naive de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] muestra los modelos de minería de datos que se generan con el [!INCLUDE[msCoName](../../includes/msconame-md.md)] algoritmo Bayes Naive de. El algoritmo Bayes naive de [!INCLUDE[msCoName](../../includes/msconame-md.md)] es un algoritmo de clasificación que se adapta muy bien a las tareas de modelado de predicción. Para obtener más información acerca de este algoritmo, vea [Microsoft Naive Bayes Algorithm](microsoft-naive-bayes-algorithm.md).  
  
 Como uno de los principales propósitos de un modelo Bayes naive es ofrecer una manera rápida de explorar los datos de un conjunto de datos, el Visor Bayes naive de [!INCLUDE[msCoName](../../includes/msconame-md.md)] proporciona varios métodos para mostrar la interacción entre los atributos de predicción y los atributos de entrada.  
  
> [!NOTE]  
>  Si desea ver información detallada acerca de las ecuaciones que se usan en el modelo y los patrones detectados, puede cambiar al Visor de árbol de contenido genérico de [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Para obtener más información, vea [Examinar un modelo usando el Visor de árbol de contenido genérico de Microsoft](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) o [Visor de árbol de contenido genérico de Microsoft &#40;Minería de datos&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).  
  
##  <a name="viewer-tabs"></a><a name="BKMK_ViewerTabs"></a>Pestañas del visor  
 Cuando se explora un modelo de minería de datos en [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], el modelo aparece en la pestaña **Visor de modelos de minería de datos** del visor del diseñador de minería de datos apropiado para el modelo. El Visor Bayes naive de [!INCLUDE[msCoName](../../includes/msconame-md.md)] dispone de las siguientes pestañas para explorar datos:  
  
-   [Red de dependencias](#BKMK_Dependency)  
  
-   [Perfiles del atributo](#BKMK_Profiles)  
  
-   [Características del atributo](#BKMK_Characteristics)  
  
-   [Distinción del atributo](#BKMK_Discrimination)  
  
##  <a name="dependency-network"></a><a name="BKMK_Dependency"></a>Red de dependencias  
 La pestaña **Red de dependencias** muestra las dependencias entre los atributos de entrada y los atributos de predicción de un modelo. El control deslizante de la izquierda del visor se comporta como un filtro que está asociado a la importancia de las dependencias. Si desplaza el control deslizante hacia abajo, sólo se verán los vínculos más similares.  
  
 Cuando se selecciona un nodo, el visor resalta las dependencias específicas de dicho nodo. Por ejemplo, si elige un nodo de predicción, el visor también resalta cada uno de los nodos que ayudan a predecir el nodo de predicción.  
  
 La leyenda de la parte inferior del visor vincula códigos de color con el tipo de dependencia en el gráfico. Por ejemplo, cuando selecciona un nodo de predicción, este nodo se sombrea en color turquesa y los nodos que predicen el nodo seleccionado aparecen sombreados en color naranja.  
  
 [Volver al principio](#BKMK_ViewerTabs)  
  
##  <a name="attribute-profiles"></a><a name="BKMK_Profiles"></a>Perfiles de atributo  
 La pestaña **Perfiles del atributo** muestra histogramas en una cuadrícula. Puede utilizar esta cuadrícula para comparar el atributo de predicción seleccionado en el cuadro **De predicción** con los demás atributos del modelo. Cada columna de la pestaña representa un estado del atributo de predicción. Si el atributo de predicción tiene muchos estados, puede cambiar el número de estados que aparecen en el histograma ajustando las **Barras de histograma**. Si el número que elige es menor que el número total de estados del atributo, los estados se enumerarán en orden de compatibilidad, con los estados restantes recopilados en un único depósito deshabilitado.  
  
 Para mostrar una leyenda de minería de datos que relaciona los colores del histograma con los estados de un atributo, active la casilla **Mostrar leyenda** . La Leyenda de minería de datos también muestra la distribución de casos para cada par de atributo-valor que seleccione.  
  
 Para copiar el contenido de la cuadrícula en el Portapapeles como una tabla HTML, haga clic con el botón derecho en la pestaña **Perfiles del atributo** y seleccione **Copiar**.  
  
 [Volver al principio](#BKMK_ViewerTabs)  
  
##  <a name="attribute-characteristics"></a><a name="BKMK_Characteristics"></a>Características del atributo  
 Para usar la pestaña **Características del atributo** , seleccione un atributo de predicción en la lista **Atributo** y elija un estado del atributo seleccionado en la lista **Valor** . Al establecer estas variables, la pestaña **Características del atributo** muestra los estados de los atributos que están asociados con el caso seleccionado del atributo seleccionado. Los atributos se ordenan por importancia.  
  
 [Volver al principio](#BKMK_ViewerTabs)  
  
##  <a name="attribute-discrimination"></a><a name="BKMK_Discrimination"></a>Distinción de atributos  
 Para usar la pestaña **Distinción del atributo** , seleccione un atributo de predicción y dos de sus estados en las listas **Atributo**, **Valor 1**y **Valor 2** . La cuadrícula de la pestaña **Distinción del atributo** mostrará entonces la siguiente información en columnas:  
  
 **Attribute**  
 Muestra otros atributos del conjunto de datos que contienen un estado que favorece claramente un estado del atributo de predicción.  
  
 **Valores**  
 Muestra el valor del atributo en la columna **Atributo**.  
  
 **Favorece\<value 1>**  
 Muestra una barra coloreada que indica la intensidad con la que el valor de atributo favorece el valor de atributo predecible mostrado en **Valor 1**.  
  
 **Favorece\<value 2>**  
 Muestra una barra coloreada que indica la intensidad con la que el valor de atributo favorece el valor de atributo predecible mostrado en **Valor 2**.  
  
 [Volver al principio](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a>Consulte también  
 [Algoritmo Bayes Naive de Microsoft](microsoft-naive-bayes-algorithm.md)   
 [Tareas y procedimientos del visor de modelos de minería de datos](mining-model-viewer-tasks-and-how-tos.md)   
 [Herramientas de minería de datos](data-mining-tools.md)   
 [Visores de modelos de minería de datos](data-mining-model-viewers.md)  
  
  
