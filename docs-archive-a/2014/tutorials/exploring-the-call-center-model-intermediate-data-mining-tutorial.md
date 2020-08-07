---
title: Explorar el modelo de centro de llamadas (tutorial intermedio de minería de datos) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9095212c-9068-4dd8-85ce-17a467adeabb
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2aceec298ba78e29988571293f8422ab9e55aa97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87747320"
---
# <a name="exploring-the-call-center-model-intermediate-data-mining-tutorial"></a>Explorar el modelo de centro de llamadas (Tutorial intermedio de minería de datos)
  Ahora que ha creado el modelo de exploración, puede usarlo para obtener más información sobre los datos mediante las herramientas siguientes que se proporcionan en [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
-   [Visor de redes neuronal de Microsoft](#bkmk_NNviewer) **:** este visor está disponible en la pestaña **visor de modelos de minería** de datos del diseñador de minería de datos y está diseñado para ayudarle a experimentar con las interacciones de los datos.  
  
-   [Visor de árbol de contenido genérico de Microsoft](#bkmk_genviewer) **:** este visor estándar proporciona detalles detallados sobre los patrones y estadísticas que detecta el algoritmo al generar el modelo.  
  
##  <a name="microsoft-neural-network-viewer"></a><a name="bkmk_NNviewer"></a>Visor de redes neuronal de Microsoft  
 El visor tiene tres paneles: **entrada**, **salida**y **variables**.  
  
 Mediante el panel de **salida** , puede seleccionar valores diferentes para el atributo de predicción o la variable dependiente. Si el modelo contiene varios atributos de predicción, puede seleccionar el atributo en la lista **atributo de salida** .  
  
 En el panel **variables** se comparan los dos resultados elegidos en términos de atributos de contribución o variables. Las barras coloreadas representan visualmente en qué grado afecta la variable a los resultados buscados. También puede ver las puntuaciones de mejora respecto al modelo predictivo para las variables. Una puntuación de mejora respecto al modelo predictivo se calcula de forma diferente en función de qué tipo de modelo de minería de datos se usa, pero en general indica la mejora en el modelo cuando se usa este atributo para la predicción.  
  
 El panel **entrada** le permite agregar influenciadores al modelo para probar varios escenarios hipotéticos.  
  
### <a name="using-the-output-pane"></a>Usar el panel Salida  
 En este modelo inicial, le interesa ver cómo afectan varios factores al grado de servicio. Para ello, puede seleccionar el nivel de servicio en la lista de atributos de salida y, a continuación, comparar distintos niveles de servicio seleccionando intervalos en las listas desplegables para **valor 1** y **valor 2**.  
  
##### <a name="to-compare-lowest-and-highest-service-grades"></a>Para comparar los grados de servicio inferior y superior  
  
1.  En **valor 1**, seleccione el intervalo con los valores más bajos. Por ejemplo, el intervalo 0-0-0.7 representa las tasas menores de abandono y, por lo tanto, el mejor grado de servicio.  
  
    > [!NOTE]  
    >  Los valores exactos de este intervalo pueden variar según la configuración del modelo.  
  
2.  En **valor 2**, seleccione el intervalo con los valores más altos. Por ejemplo, el intervalo con el valor >= 0,12 representa las tasas mayores de abandono y, por lo tanto, el peor grado de servicio. En otras palabras, el 12% de los clientes que llamaron durante este turno colgaron antes de hablar con un agente.  
  
     El contenido del panel **variables** se actualiza para comparar los atributos que contribuyen a los valores de resultado. Por lo tanto, la columna de la izquierda muestra los atributos asociados al mejor grado de servicio y la columna de la derecha los atributos asociados al peor grado de servicio.  
  
### <a name="using-the-variables-pane"></a>Usar el panel Variables  
 En este modelo, parece que `Average Time Per Issue` es un factor importante. Esta variable indica el tiempo promedio que se tarda en responder una llamada, con independencia de su tipo.  
  
##### <a name="to-view-and-copy-probability-and-lift-scores-for-an-attribute"></a>Para ver y copiar las puntuaciones de mejora respecto al modelo predictivo y la probabilidad de un atributo  
  
1.  En el panel **variables** , coloque el mouse sobre la barra coloreada de la primera fila.  
  
     En esta barra de color se muestra cómo `Average Time Per Issue` contribuye a la calidad del servicio. La información sobre herramientas muestra una puntuación general, las probabilidades y las puntuaciones de mejora con respecto al modelo predictivo para cada combinación de variable y resultado de destino.  
  
2.  En el panel **variables** , haga clic con el botón secundario en cualquier barra coloreada y seleccione **copiar**.  
  
3.  En una hoja de cálculo de Excel, haga clic con el botón secundario en cualquier celda y seleccione **pegar**.  
  
     El informe se pega como una tabla HTML y solo muestra las puntuaciones de cada barra.  
  
4.  En otra hoja de cálculo de Excel, haga clic con el botón secundario en cualquier celda y seleccione **Pegar especial**.  
  
     El informe se pega en formato de texto e incluye las estadísticas relacionadas descritas en la sección siguiente.  
  
### <a name="using-the-input-pane"></a>Usar el panel Entrada  
 Suponga que le interesa observar el efecto de un factor determinado, como el turno o el número de operadores. Puede seleccionar una variable determinada mediante el panel **entrada** y el panel **variables** se actualiza automáticamente para comparar los dos grupos seleccionados anteriormente según la variable especificada.  
  
##### <a name="to-review-the-effect-on-service-grade-by-changing-input-attributes"></a>Para revisar el efecto en el grado de servicio cambiando los atributos de entrada  
  
1.  En el panel **entrada** , en **atributo**, seleccione Mayús.  
  
2.  En **valor**, seleccione **AM**.  
  
     El panel **variables** se actualiza para mostrar el efecto en el modelo cuando el turno es **AM**. Todas las demás selecciones siguen siendo las mismas: todavía está comparando los grados de servicio más bajos y más altos.  
  
3.  En **valor**, seleccione **PM1**.  
  
     El panel **variables** se actualiza para mostrar el efecto en el modelo cuando cambia el turno.  
  
4.  En el panel **entrada** , haga clic en la siguiente fila en blanco debajo de **atributo**y seleccione llamadas. En **valor**, seleccione el intervalo que indica el mayor número de llamadas.  
  
     Se agrega una condición de entrada nueva a la lista. El panel **variables** se actualiza para mostrar el efecto en el modelo para un turno determinado cuando el volumen de la llamada es el más alto.  
  
5.  Continúe cambiando los valores de Shift y Calls para encontrar correlaciones interesantes entre el turno, el volumen de llamadas y  el grado de servicio.  
  
    > [!NOTE]  
    >  Para borrar el panel de **entrada** de modo que pueda usar distintos atributos, haga clic en **actualizar contenido del visor**.  
  
### <a name="interpreting-the-statistics-provided-in-the-viewer"></a>Interpretar las estadísticas que se proporcionan en el visor  
 Los tiempos de espera más prolongados son un factor de predicción muy eficaz de una tasa de abandono elevada, lo que significa que el grado de servicio es deficiente. Esto puede parecer una conclusión obvia; sin embargo, el modelo de minería de datos proporciona datos estadísticos adicionales para ayudarle a interpretar estas tendencias.  
  
-   **Puntuación**: valor que indica la importancia global de esta variable para discriminar entre los resultados. Cuanto más alta es la puntuación, más intenso es el efecto que la variable tiene en el resultado.  
  
-   **Probabilidad del valor 1**: porcentaje que representa la probabilidad de este valor para este resultado.  
  
-   **Probabilidad del valor 2**: porcentaje que representa la probabilidad de este valor para este resultado.  
  
-   **Eleve el valor 1** y **eleve para el valor 2**: puntuaciones que representa el impacto de usar esta variable concreta para predecir el valor 1 y los resultados del valor 2. Cuanto más alta es la puntuación, mejor es la variable prediciendo los resultados.  
  
 La tabla siguiente contiene algunos valores de ejemplo para los influenciadores más importantes. Por ejemplo, la **probabilidad del valor 1** es 60,6% y la **probabilidad del valor 2** es 8,30%, lo que significa que cuando el promedio de tiempo por problema se encontraba en el intervalo de 44-70 minutos, el 60,6% de los casos estaban en el turno con los niveles de servicio más altos (valor 1) y el 8,30% de los casos estaban en el turno con los peores grados de  
  
 A partir de esta información puede sacar algunas conclusiones. Un menor tiempo de respuesta de las llamadas (el intervalo 44-70) influye en gran medida en un mejor grado de servicio (el intervalo 0.00-0.07). La puntuación (92,35) le indica que esta variable es muy importante.  
  
 Sin embargo, según se sigue mirando la lista de factores que influyen, se ven algunos otros factores con efectos que son más sutiles y más difíciles de interpretar. Por ejemplo, el turno parece influir en el servicio, pero las puntuaciones de mejora con respecto al modelo predictivo y las probabilidades relativas indican que no es un factor importante.  
  
|Atributo|Value|Favorece \< 0,07|Favorece >= 0,12|  
|---------------|-----------|--------------------|----------------------|  
|Average Time Per Issue|89,087-120,000||Puntuación: 100<br /><br /> Probabilidad de valor1:4,45%<br /><br /> Probabilidad de Valor2:51,94%<br /><br /> Elevación para Value1:0,19<br /><br /> Elevación para Valor2:1,94|  
|Average Time Per Issue|44,000-70,597|Puntuación: 92,35<br /><br /> Probabilidad de valor 1: 60,06 %<br /><br /> Probabilidad de valor 2: 8,30 %<br /><br /> Elevación de valor 1: 2,61<br /><br /> Elevación de valor 2: 0,31||  
  
 [Volver al principio](#bkmk_NNviewer)  
  
##  <a name="microsoft-generic-content-tree-viewer"></a><a name="bkmk_genviewer"></a>Visor de árbol de contenido genérico de Microsoft  
 Este visor se puede usar para ver información incluso más detallada creada por el algoritmo cuando se procesa el modelo. El **visor de árbol de contenido de MicrosoftGeneric** representa el modelo de minería de datos como una serie de nodos, donde cada nodo representa el conocimiento aprendido sobre los datos de entrenamiento. Este visor se puede utilizar con todos los modelos, pero el contenido de los nodos es diferente según el tipo de modelo.  
  
 En los modelos de red neuronal o de regresión logística, podría encontrar que el `marginal statistics node` es particularmente útil. Este nodo contiene estadísticas derivadas acerca de la distribución de los valores de los datos. Esta información puede ser de utilidad si desea obtener un resumen de los datos sin tener que escribir muchas consultas de T-SQL. El gráfico de los valores del tema anterior se derivó del nodo de estadísticas marginal.  
  
#### <a name="to-obtain-a-summary-of-data-values-from-the-mining-model"></a>Para obtener un resumen de los valores de datos del modelo de minería de datos  
  
1.  En el diseñador de minería de datos, en la pestaña **visor de modelos de minería** de datos, seleccione \<mining model name> .  
  
2.  En la lista **visor** , seleccione **visor de árbol de contenido genérico de Microsoft**.  
  
     La vista del modelo de minería de datos se actualiza para mostrar una jerarquía de nodos en el panel izquierdo y una tabla HTML en el panel derecho.  
  
3.  En el panel **título de nodo** , haga clic en el nodo que tenga el nombre 10000000000000000.  
  
     El nodo superior de cualquier modelo siempre es el nodo raíz. En un modelo de red neuronal o de regresión logística, el nodo que está inmediatamente por debajo es el nodo de estadísticas marginal.  
  
4.  En el panel **detalles del nodo** , desplácese hacia abajo hasta que encuentre la fila NODE_DISTRIBUTION.  
  
5.  Desplácese hacia abajo por la tabla NODE_DISTRIBUTION para ver la distribución de valores calculados por el algoritmo de red neuronal.  
  
 Para usar estos datos en un informe, podría seleccionar información de filas específicas y copiarla después, o puede usar la siguiente consulta de Extensiones de minería de datos (DMX) para extraer el contenido completo del nodo.  
  
```  
SELECT *   
FROM [Call Center EQ4].CONTENT  
WHERE NODE_NAME = '10000000000000000'  
```  
  
 También puede usar la jerarquía de nodos y los detalles de la tabla NODE_DISTRIBUTION para recorrer rutas individuales de la red neuronal y ver estadísticas del nivel oculto. Para obtener más información, vea [ejemplos de consultas del modelo de red neuronal](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md).  
  
 [Volver al principio](#bkmk_NNviewer)  
  
## <a name="next-task-in-lesson"></a>Siguiente tarea de la lección  
 [Agregar un modelo de regresión logística a la estructura del centro de llamadas &#40;tutorial intermedio de minería de datos&#41;](../../2014/tutorials/add-logistic-regression-model-to-call-center-intermediate-data-mining.md)  
  
## <a name="see-also"></a>Consulte también  
 [Contenido del modelo de minería de datos para los modelos de red neuronal &#40;Analysis Services-minería de datos&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md)   
 [Ejemplos de consultas de modelos de red neuronal](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md)   
 [Referencia técnica del algoritmo de red neuronal de Microsoft](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md)   
 [Cambiar la discretización de una columna en un modelo de minería de datos](../../2014/analysis-services/data-mining/change-the-discretization-of-a-column-in-a-mining-model.md)  
  
  
