---
title: Elegir y asignar los datos de prueba del modelo | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- columns [data mining], mining accuracy charts
- Mining Accuracy Chart [Analysis Services], column mappings
- input column mapping [Analysis Services]
- mapping input columns [Analysis Services]
ms.assetid: be0d9f20-40c3-4dac-81da-281cfe724126
author: minewiskan
ms.author: owend
ms.openlocfilehash: 84f1d01c40070069d610bb028ab003223c5afbcd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87671840"
---
# <a name="choose-and-map-model-testing-data"></a>Elegir y asignar datos de prueba para el modelo
  Para crear un gráfico de precisión en [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], debe elegir los datos que se utilizarán para probar el modelo y asignar dichos datos al modelo.  
  
 De forma predeterminada, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilizará los datos de prueba del modelo de minería de datos, siempre que se haya creado un conjunto de datos de exclusión al generar la estructura. La manera más fácil de probar los modelos basados en la misma estructura de minería de datos consiste en crear un conjunto de pruebas de exclusión, ya que los nombres de las columnas y los tipos de datos siempre coincidirán con el modelo y podrá estar casi seguro de que la distribución de los datos es similar. Además, el diseñador creará automáticamente las relaciones entre la columnas de entrada y las del modelo.  
  
 Otra alternativa es especificar un origen de datos externo. Para los datos externos, hay algunos requisitos adicionales:  
  
-   El conjunto de datos externos se debe definir como una vista del origen de datos en una instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
-   El conjunto de datos externos debe contener al menos una columna que se pueda asignar a la columna de predicción en el modelo de minería de datos. Puede optar por omitir algunas columnas.  
  
-   No puede agregar columnas nuevas ni asignar columnas en una vista del origen de datos diferente. La vista del origen de datos que seleccione debe contener todas las columnas que necesite para la consulta de predicción.  
  
-   Si los nombres de las columnas externas coinciden exactamente con los del modelo, el diseñador los asignará automáticamente. Si las asignaciones son erróneas, podrá cambiarlas, o eliminarlas y crear unas nuevas para las columnas existentes.  
  
-   Si utiliza un origen de datos externos, podrá aplicar filtros para restringir los datos de prueba a un subconjunto de casos que sea relevante.  
  
-   Incluso aunque utilice el conjunto de pruebas de exclusión, deberá tener en cuenta que los filtros pueden producir diferencias entre los datos de prueba asociados con una estructura de minería de datos y los casos de prueba del modelo de minería de datos.  
  
 En este tema se describe cómo elegir y asignar los datos de prueba:  
  
 [Seleccionar tablas de entrada para probar la precisión de un modelo de minería de datos](#bkmk_SelectInputs)  
  
 [Asignar columnas del modelo a las columnas de los datos de prueba](#bkmk_MapColumns)  
  
 [Cambiar la forma en la que las columnas de los datos de prueba se asignan al modelo](#bkmk_ChangeMappings)  
  
##  <a name="to-select-input-tables-to-test-the-accuracy-of-a-mining-model"></a><a name="bkmk_SelectInputs"></a> Para seleccionar tablas de entrada para probar la precisión de un modelo de minería de datos  
  
1.  En el Diseñador de minería de datos de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], haga doble clic en la estructura de minería de datos que contiene los modelos de los que desea crear un gráfico.  
  
2.  Seleccione la pestaña **Gráfico de precisión de minería de datos** .  
  
3.  En la pestaña **Selección de entrada** de la vista **Gráfico de precisión de minería de datos** , seleccione una de las opciones siguientes:  
  
     **Usar casos de prueba de modelo de minería de datos**  
  
     **Usar casos de prueba de estructura de minería de datos**  
  
     **Especificar otro conjunto de datos**  
  
4.  Si ha seleccionado **Especificar otro conjunto de datos**, puede hacer clic en **Abrir editor de filtros** para crear condiciones de filtro en el conjunto de datos de entrada. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
5.  Haga clic en la pestaña **Gráfico de elevación** o la pestaña **Matriz de clasificación** para generar automáticamente el gráfico utilizando los datos de prueba que especificó.  
  
##  <a name="to-map-model-columns-to-the-columns-in-the-testing-data"></a><a name="bkmk_MapColumns"></a> Para asignar columnas del modelo a las columnas de los datos de prueba  
  
1.  Haga doble clic en la estructura de minería de datos que contiene los modelos de los que desea crear un gráfico para abrir la estructura y los modelos en el Diseñador de minería de datos.  
  
2.  Seleccione la pestaña **Gráfico de precisión de minería de datos** y luego seleccione la pestaña **Selección de entrada** .  
  
3.  En la pestaña **Selección de entrada** , en **Seleccionar un conjunto de datos para usarlo en un gráfico de precisión**, seleccione la opción **Especificar otro conjunto de datos**.  
  
4.  Haga clic en el botón examinar **(...)** para abrir un cuadro de diálogo y generar la definición del conjunto de datos externo.  
  
5.  En el cuadro de diálogo **Seleccionar estructura de minería de datos** , seleccione la estructura que contenga los modelos con los que desea trabajar y, después, haga clic en **Aceptar**.  
  
6.  En la tabla **Seleccionar tabla(s) de entrada** de la pestaña **Gráfico de precisión de minería de datos** , haga clic en **Seleccionar tabla de casos** para abrir el cuadro de diálogo **Seleccionar tabla** .  
  
7.  En el cuadro de diálogo **Seleccionar tablas** , seleccione un origen de datos de la lista **Origen de datos** . Elija una tabla con los datos que desee usar en las consultas de predicción para determinar la precisión de los modelos.  
  
8.  En el cuadro **Nombre de tabla o vista** , seleccione la tabla que contiene los datos que quiere usar para probar los modelos.  
  
9. Modifique las asignaciones, si es necesario. Las columnas de la estructura de minería de datos se asignan automáticamente a las columnas que tengan el mismo nombre en la tabla de entrada. Para crear asignaciones manualmente, haga clic en una columna en la tabla **Seleccionar tabla(s) de entrada** y arrástrela a la columna correspondiente en la tabla **Estructura de minería de datos** . Para eliminar una asignación, haga clic en la línea que vincula la columna de la tabla **Estructura de minería de datos** con la columna asignada de la tabla **Seleccionar tabla(s) de entrada** y, después, presione Suprimir.  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="to-modify-the-way-input-data-is-mapped-to-the-model"></a><a name="bkmk_ChangeMappings"></a>Para modificar la forma en que los datos de entrada se asignan al modelo  
  
1.  En el Diseñador de minería de datos, haga doble clic en la estructura que contiene los modelos que quiere incluir en un gráfico.  
  
2.  Seleccione la pestaña **Gráfico de precisión de minería de datos** .  
  
3.  Haga clic en la pestaña **Selección de entrada** .  
  
4.  En **seleccionar el conjunto de datos que se va a usar para el gráfico de precisión**, seleccione la opción **especificar un conjunto de datos diferente**.  
  
5.  Haga clic en el botón examinar **(...)** para abrir un cuadro de diálogo y generar la definición del origen de datos externo.  
  
6.  En el cuadro de diálogo **Especificar asignación de columnas** , haga clic en **Seleccionar tabla de casos**.  
  
7.  En el cuadro de diálogo Seleccionar tabla, seleccione una vista del origen de datos en la lista y la tabla que contiene los datos del caso. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  Si las tablas que necesita no están disponibles, cierre el cuadro de diálogo y cree una nueva vista del origen de datos que contenga la tabla. Para obtener información sobre cómo crear una vista del origen de datos, vea [Definir una vista del origen de datos &#40;Analysis Services&#41;](../multidimensional-models/defining-a-data-source-view-analysis-services.md).  
  
9. Si el modelo de minería de datos contiene una tabla anidada, haga clic en **Seleccionar tabla anidada**y seleccione la tabla anidada en la lista de tablas de la vista del origen de datos. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. Seleccione la línea de combinación de la asignación que desea modificar y seleccione **Modificar conexiones**.  
  
     Se abre el cuadro de diálogo **Modificar asignación** . En la tabla de este cuadro de diálogo, **Columna de la estructura de minería de datos** incluye todas las columnas que contiene la estructura de minería de datos selecciona y **Columna de la tabla** incluye las columnas de las tablas de entrada que están asignadas a columnas en la estructura de minería de datos.  
  
11. En **Columna de la tabla**, seleccione la fila que corresponda a la fila bajo **Columna de la estructura de minería de datos** para la que desee modificar una relación. Seleccione una columna nueva en la lista o seleccione la entrada vacía en la lista para eliminar la columna.  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     Las nuevas asignaciones de columna se muestran en el cuadro de diálogo **Especificar asignación de columnas** . Puede quitar una asignación seleccionando la línea entre las columnas y presionando la tecla Supr. Para crear una conexión, seleccione una columna de la tabla **Estructura de minería de datos** y arrástrela hasta la columna correspondiente de la tabla **Seleccionar tabla(s) de entrada** .  
  
## <a name="see-also"></a>Consulte también  
 [Tareas y procedimientos de prueba y validación &#40;minería de datos&#41;](testing-and-validation-tasks-and-how-tos-data-mining.md)  
  
  
