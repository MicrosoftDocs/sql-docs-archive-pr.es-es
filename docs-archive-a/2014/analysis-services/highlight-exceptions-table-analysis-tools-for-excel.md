---
title: Resaltar excepciones (herramientas de análisis de tabla para Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- highlight exceptions
ms.assetid: d90a12f8-7bc3-4fdb-95a1-7c89058f0d9a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 97e8197fc76f431cf9740c5c6fbd7ac44d8204a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87749527"
---
# <a name="highlight-exceptions-table-analysis-tools-for-excel"></a>Resaltar excepciones (Herramientas de análisis de tabla para Excel)
  ![Botón Resaltar excepciones en cinta de opciones](media/tat-highlightex.gif "Botón Resaltar excepciones en cinta de opciones")  
  
 En ocasiones, los datos pueden contener valores peculiares. Por ejemplo, la lista de edades de propietarios de casas podría empezar en cinco años. Estos valores, que a menudo se denominan valores *atípicos*, pueden ser incorrectos debido a un error de entrada de datos o pueden indicar tendencias inusuales. De cualquier modo, las excepciones pueden afectar a la calidad del análisis. La herramienta **resaltar excepciones** le ayuda a encontrar estos valores y revisarlos para realizar otras acciones.  
  
 La herramienta **resaltar excepciones** puede trabajar con todo el rango de datos en una tabla de datos de Excel, o puede seleccionar solo algunas columnas. También es posible ajustar un umbral que controle la variabilidad de los datos para encontrar más o menos excepciones.  
  
 Al completar el análisis, la herramienta crea una hoja de cálculo nueva que contiene un informe de resumen sobre el número de valores atípicos que se encontraron en cada una de las columnas analizadas. La herramienta también resalta las excepciones en la tabla de datos original. Puesto que la herramienta analiza tendencias globales, quizás encuentre que la mayoría de los valores de una fila son normales y resalte sólo una celda de esa fila. En el ejemplo anterior de la vivienda, solo se podría resaltar la columna **Age** .  
  
 También puede cambiar el valor de **umbral de excepción** en el informe de **Resumen**. Este valor indica la probabilidad de que una celda determinada contenga un valor atípico. Por tanto, si aumenta el valor, se resaltarán menos valores como valores atípicos. Por el contrario, cuando el valor se disminuye, se verán más celdas resaltadas.  
  
## <a name="using-the-highlight-exceptions-tool"></a>Usar la herramienta Resaltar excepciones  
  
1.  Abra una tabla de Excel y haga clic en **resaltar excepciones**.  
  
2.  Especifique las columnas que desea analizar.  
  
3.  Haga clic en **Ejecutar**.  
  
4.  Abra la hoja de cálculo titulada \<table name> valores atípicos para ver un resumen de los valores atípicos encontrados.  
  
5.  Para cambiar el número de resaltados, haga clic en las flechas arriba y abajo de la fila **umbral de excepción** del **Informe resaltar excepciones**.  
  
### <a name="requirements"></a>Requisitos  
 Puede incluir columnas que no contengan valores erróneos si éstos contienen información que podría ser útil en la predicción de otras filas. No obstante, debe anular la selección de las columnas que tengan muchos valores cero o valores ausentes.  
  
 Dado que todas las columnas seleccionadas se utilizan para crear un patrón general, debería evitar usar columnas de entrada que sabe que tienen información no relevante, como las siguientes:  
  
-   Columnas que contienen valores únicos como los identificadores.  
  
-   Columnas que contienen un alto porcentaje de valores erróneos.  
  
-   Columnas con muchos valores ausentes.  
  
     Tenga en cuenta que hay algunos casos en los que resulta útil incluir columnas de entrada que tienen muchos valores ausentes. Por ejemplo, si siempre falta el valor del campo de dirección cuando el cliente compra a través de un minorista, el algoritmo de minería de datos pueden utilizar esta información para identificar otros clientes similares. Debe determinar caso por caso si los datos faltan por omisión o porque el estado Ausente es significativo.  
  
-   Columnas que probablemente no serán útiles para crear un patrón. Por ejemplo, una columna que tiene el mismo valor en todas las filas no agrega ninguna información de utilidad para generar patrones.  
  
## <a name="understanding-the-highlight-exceptions-report"></a>Descripción del Informe de excepciones resaltadas  
 Al hacer clic en **Ejecutar**, la herramienta hace tres cosas:  
  
-   Crea la estructura de minería de datos basándose en los datos actuales de la tabla.  
  
-   Crea un nuevo modelo de minería de datos usando el algoritmo de clústeres de [!INCLUDE[msCoName](../includes/msconame-md.md)].  
  
-   Crea una consulta de predicción basándose en los patrones para determinar si algún valor de la hoja de cálculo es improbable.  
  
 El valor inicial para el umbral de excepción siempre es 75, lo que significa que el algoritmo ha calculado que existe un 75% de posibilidad de que los datos resaltados sean erróneos. La herramienta establece automáticamente este umbral para la fase de análisis inicial, pero el valor puede cambiarse en el informe.  
  
 La herramienta **resaltar excepciones** resalta las celdas de la tabla de datos original que son sospechosas. El resaltado oscuro quiere decir que la fila necesita atención. El resaltado claro indica que el valor de esa celda en particular se identificó como sospechoso. Si cambia el umbral para las excepciones, los valores resaltados cambiarán según corresponda.  
  
 El gráfico de resumen muestra el número de celdas de cada columna que estaban por encima del umbral de excepción.  
  
## <a name="related-tools"></a>Herramientas relacionadas  
 Cuando esté limpiando o revisando datos como preparación para la minería de datos, también debería probar las características de exploración de datos del Cliente de minería de datos para Excel. Este complemento dispone de más herramientas avanzadas que le ayudarán a encontrar valores atípicos, cambiar etiquetas de datos o ver la distribución de datos. Para obtener más información acerca de las herramientas de exploración de datos en el cliente de minería de datos para Excel, vea [explorar y limpiar datos](exploring-and-cleaning-data.md).  
  
 La herramienta **resaltar excepciones** usa el [!INCLUDE[msCoName](../includes/msconame-md.md)] algoritmo de clústeres. Un modelo de clústeres detecta grupos de filas que comparten características similares. El cliente de minería de datos para Excel proporciona una ventana **examinar** que utiliza gráficos y perfiles característicos para permitir explorar los modelos de minería de datos creados por la agrupación en clústeres. Para obtener información acerca de cómo examinar el modelo de agrupación en clústeres creado por la herramienta **resaltar excepciones** , vea [examinar modelos (cliente de minería de datos para Excel)](highlight-exceptions-table-analysis-tools-for-excel.md).  
  
 Para obtener más información sobre el algoritmo de clústeres de [!INCLUDE[msCoName](../includes/msconame-md.md)], vea el tema "Algoritmo de clústeres de Microsoft" en los Libros en pantalla de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Consulte también  
 [Herramientas de análisis de tabla para Excel](table-analysis-tools-for-excel.md)  
  
  
