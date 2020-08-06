---
title: Probar un modelo filtrado (tutorial básico de minería de datos) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f0d74f8c-600d-4df5-a742-695e6947a071
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a97b5ca3523d1fc73405baba52b179a9bef04767
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662394"
---
# <a name="testing-a-filtered-model-basic-data-mining-tutorial"></a>Probar un modelo filtrado (Tutorial básico de minería de datos)
  Ahora que ha determinado que el `TM_Decision_Tree` modelo es el más preciso, personalizará el modelo para satisfacer mejor las necesidades de la campaña de [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] correo directo. Concretamente, el departamento de marketing desea saber si hay alguna diferencia entre los clientes masculinos y femeninos. Esta información puede ayudarles a decidir qué revistas utilizar para los anuncios y qué productos ofrecer en sus campañas.  
  
## <a name="using-filters"></a>Usar filtros  
 El filtrado permite crear con facilidad modelos basados en subconjuntos de datos. El filtro se aplica solo al modelo y no cambia el origen de datos subyacente.  
  
 En esta lección, creará un modelo filtrado por género para predecir las características que más influyen en el comportamiento de compra de los hombres y las mujeres.  
  
 En primer lugar, realizará una copia del `TM_Decision_Tree` modelo.  
  
#### <a name="to-copy-the-decision-tree-model"></a>Para copiar el modelo del árbol de decisión  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], en el Explorador de soluciones, seleccione **BasicDataMining**.  
  
2.  Haga clic en la pestaña **Modelos de minería de datos** .  
  
3.  Haga clic con el botón secundario en el `TM_Decision_Tree` modelo y seleccione **nuevo modelo de minería de datos.**  
  
4.  En el campo **nombre del modelo** , escriba `TM_Decision_Tree_Male` .  
  
5.  Haga clic en **OK**.  
  
 Luego, cree un filtro para seleccionar los clientes para el modelo basados en su género.  
  
#### <a name="to-create-a-case-filter-on-a-mining-model"></a>Para crear un filtro de casos en un modelo de minería de datos  
  
1.  Haga clic con el botón secundario en el `TM_Decision_Tree_Male` modelo de minería de datos para abrir el menú contextual.  
  
     -- o --  
  
     Seleccione el modelo. En el menú **Minería de datos** , seleccione **Establecer filtro de modelos**.  
  
2.  En el cuadro de diálogo **Filtro del modelo** , haga clic en la fila superior de la cuadrícula en el cuadro de texto **Columna de la estructura de minería de datos** .  
  
     La lista desplegable muestra solo los nombres de las columnas de esa tabla.  
  
3.  En el cuadro de texto Columna de la estructura de minería de datos, seleccione **Gender**.  
  
     El icono en la parte izquierda del cuadro de texto cambia para indicar que el elemento seleccionado es una tabla o una columna.  
  
4.  Haga clic en el cuadro de texto **Operador** y seleccione el operador igual (=) en la lista.  
  
5.  Haga clic en el cuadro de texto **Valor** y escriba **M**.  
  
6.  Haga clic en la siguiente fila de la cuadrícula.  
  
7.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Filtro del modelo** .  
  
     El filtro se muestra en la ventana **Propiedades** . Como alternativa, puede iniciar el cuadro de diálogo **Filtro del modelo** en la ventana **Propiedades** .  
  
8.  Repita los pasos anteriores, pero esta vez asigne un nombre al modelo `TM_Decision_Tree_Female` y escriba **F** en el cuadro de texto **valor** .  
  
## <a name="process-the-filtered-models"></a>Procesar los modelos filtrados  
 Los modelos no se pueden utilizar hasta que se hayan implementado y procesado. Para obtener más información sobre los modelos de procesamiento, vea [procesar modelos en la estructura de distribución de correo directo &#40;tutorial básico de minería de datos&#41;](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md).  
  
#### <a name="to-process-the-filtered-model"></a>Para procesar el modelo filtrado  
  
1.  Haga clic con el botón secundario en el `TM_Decision_Tree_Male` modelo y seleccione **procesar estructura de minería de datos y todos los modelos**.  
  
2.  Haga clic en **Ejecutar** para procesar los nuevos modelos.  
  
3.  Una vez completado el procesamiento, haga clic en **Cerrar** en ambas ventanas de procesamiento.  
  
     Ahora tiene dos modelos nuevos que se muestran en la pestaña **Modelos de minería de datos** .  
  
## <a name="evaluate-the-results"></a>Evaluar los resultados  
 Vea los resultados y evalúe la exactitud de los modelos filtrados de la misma manera que hizo con los tres modelos anteriores. Para más información, consulte:  
  
 [Explorar el modelo de árbol de decisión &#40;tutorial básico de minería de datos&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
 [Probar la exactitud con gráficos de mejora respecto al modelo predictivo &#40;Tutorial básico de minería de datos&#41;](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
#### <a name="to-explore-the-filtered-models"></a>Para explorar los modelos filtrados  
  
1.  Seleccione la pestaña **Visor de modelo de minería de datos** en **Diseñador de minería de datos**.  
  
2.  En el cuadro modelo de minería de datos, seleccione `TM_Decision_Tree_Male` .  
  
3.  **Nivel** de presentación en `3` .  
  
4.  Cambie el valor de **fondo** a `1` .  
  
5.  Coloque el cursor sobre el nodo con la etiqueta **Todos** para ver el número de compradores de bicicleta con respecto a los no compradores.  
  
6.  Repita los pasos 1-5 para `TM_Decision_Tree_Female` .  
  
7.  Explore los resultados de `TM_Decision_Tree` y los modelos filtrados por sexo. Si se comparan todos los compradores de bicicletas, los compradores masculinos y femeninos comparten algunas de las mismas características de los compradores de bicicletas sin filtrar, pero los tres también presentan diferencias interesantes. Ésta es información útil que [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] puede utilizar para desarrollar su campaña de marketing.  
  
#### <a name="to-test-the-lift-of-the-filtered-models"></a>Para probar la mejora en la predicción de los modelos filtrados  
  
1.  Cambie a la pestaña **Gráfico de precisión de minería de datos** del Diseñador de minería de datos de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] y seleccione la pestaña **Selección de entrada** .  
  
2.  En el cuadro de grupo **Seleccionar un conjunto de datos para usarlo en un gráfico de precisión** , seleccione **Usar casos de prueba de estructura de minería de datos**.  
  
3.  En la pestaña **Selección de entrada** del Diseñador de minería de datos, en **Seleccione las columnas del modelo de minería de datos de predicción que se mostrarán en el gráfico de elevación**, active la casilla correspondiente a **Sincronizar valores y columnas de predicción**.  
  
4.  En la columna **Nombre de columna de predicción** , compruebe que **Bike Buyer** está seleccionado para cada modelo.  
  
5.  En la columna **Mostrar** , seleccione cada uno de los modelos.  
  
6.  En la columna **valor de predicción** , seleccione `1` .  
  
7.  Seleccione la pestaña **Gráfico de mejora respecto al modelo predictivo** para mostrar el gráfico de mejora.  
  
     Observará ahora que los tres modelos de Árbol de decisión proporcionan una mejora significativa con respecto al modelo de estimación aleatoria, además de superar a los modelos de agrupación en clústeres y Bayes naive.  
  
## <a name="related-tasks"></a>Related Tasks  
 Para obtener más información sobre los filtros, vea [filtros para modelos de minería de datos &#40;Analysis Services-Data Mining&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md).  
  
 Para obtener un ejemplo de cómo aplicar filtros a tablas anidadas, vea [tutorial intermedio de minería de datos &#40;Analysis Services-&#41;de minería de datos ](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md).  
  
## <a name="previous-task-in-lesson"></a>Tarea anterior de la lección  
 [Probar la exactitud con gráficos de mejora respecto al modelo predictivo &#40;Tutorial básico de minería de datos&#41;](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Lección siguiente  
 [Lección 6: Crear y trabajar con predicciones &#40;Tutorial básico de minería de datos&#41;](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Consulte también  
 [Tutorial intermedio de minería de datos &#40;Analysis Services:&#41;de minería de datos](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [Tareas y procedimientos del modelo de minería de datos](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Eliminar un filtro de un modelo de minería de datos](../../2014/analysis-services/data-mining/delete-a-filter-from-a-mining-model.md)   
 [Filtros para modelos de minería &#40;Analysis Services - Minería de datos&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  
