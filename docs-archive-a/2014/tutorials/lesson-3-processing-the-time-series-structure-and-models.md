---
title: 'Lección 3: procesar la estructura y los modelos de serie temporal | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 16e27b57-eae1-47a7-a02c-47b6ed487d87
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 493d27c9836eb765c655eba5bbb004e4d48cde40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746642"
---
# <a name="lesson-3-processing-the-time-series-structure-and-models"></a>Lección 3: Procesamiento de la estructura de serie temporal y los modelos
  En esta lección, usará la instrucción [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) para procesar las estructuras de minería de datos de serie temporal y los modelos de minería de datos que ha creado.  
  
 Al procesar una estructura de minería de datos, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] lee los datos de origen y genera las estructuras que admiten los modelos de minería de datos. Siempre tiene que procesar un modelo y estructura de minería de datos después de crearlo. Si especifica una estructura de minería de datos con INSERT INTO, la instrucción procesa la estructura de minería de datos y todos sus modelos asociados.  
  
 Si agrega un modelo de minería de datos a una estructura de minería de datos que ya se ha procesado, puede usar la instrucción `INSERT INTO MINING MODEL` para procesar solo el nuevo modelo de minería de datos con los datos existentes.  
  
 Para obtener más información sobre el procesamiento de modelos de minería de datos, vea [requisitos y consideraciones de procesamiento &#40;minería de datos&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).  
  
## <a name="insert-into-statement"></a>Instrucción INSERT INTO  
 Para entrenar la estructura de minería de datos de serie temporal y todos sus modelos de minería de datos asociados, utilice la instrucción [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) . El código de la instrucción se puede dividir en las partes siguientes.  
  
-   Identificación de la estructura de minería de datos  
  
-   Visualización en una lista de las columnas de la estructura de minería de datos  
  
-   Definición de los datos de entrenamiento  
  
 A continuación, se incluye un ejemplo genérico de la instrucción `INSERT INTO`:  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
)  
OPENQUERY (<source data definition>)  
```  
  
 La primera línea del código identifica la estructura de minería de datos que se entrenará:  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 Las líneas siguientes del código especifican las columnas definidas por la estructura de minería de datos. Debe incluir en la lista cada una de las columnas de la estructura de minería de datos, y cada columna debe estar asignada a una columna incluida en los datos de la consulta de origen:  
  
```  
(  
   <mining structure columns>  
)  
```  
  
 Las últimas líneas del código definen los datos que se utilizarán para entrenar la estructura de minería de datos.  
  
```  
OPENQUERY (<source data definition>)  
```  
  
 En esta lección usará `OPENQUERY` para definir los datos de origen. Para obtener más información sobre otros métodos para definir una consulta en los datos de origen, vea [&#60;&#62;de consultas de datos de origen ](/sql/dmx/source-data-query).  
  
## <a name="lesson-tasks"></a>Tareas de la lección  
 En esta lección realizará la tarea siguiente:  
  
-   Procesar la estructura de minería de datos Forecasting_MIXED_Structure  
  
-   Procesar los modelos de minería de datos relacionados Forecasting_MIXED, Forecasting_ARIMA y Forecasting_ARTXP  
  
## <a name="processing-the-time-series-mining-structure"></a>Procesar la estructura de minería de datos de serie temporal  
  
#### <a name="to-process-the-mining-structure-and-related-mining-models-by-using-insert-into"></a>Para procesar la estructura de minería de datos y los modelos relacionados mediante INSERT INTO  
  
1.  En **Explorador de objetos**, haga clic con el botón secundario en la instancia de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , seleccione **nueva consulta**y, a continuación, haga clic en **DMX**.  
  
     Se abre el Editor de consultas, que contiene una consulta nueva en blanco.  
  
2.  Copie el ejemplo genérico de la instrucción INSERT INTO en la consulta en blanco.  
  
3.  Reemplace lo siguiente:  
  
    ```  
    [<mining structure>]  
    ```  
  
     por:  
  
    ```  
    Forecasting_MIXED_Structure  
    ```  
  
4.  Reemplace lo siguiente:  
  
    ```  
    <mining structure columns>  
    ```  
  
     por:  
  
    ```  
    [ReportingDate],  
    [ModelRegion]   
    ```  
  
5.  Reemplace lo siguiente:  
  
    ```  
    OPENQUERY(<source data definition>)  
    ```  
  
     por:  
  
    ```  
    OPENQUERY([Adventure Works DW 2008R2],'SELECT [ReportingDate], [ModelRegion], [Quantity], [Amount]  
    FROM vTimeSeries ORDER BY [ReportingDate]')  
    ```  
  
     La consulta de origen hace referencia al [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] origen de datos definido en el proyecto de ejemplo IntermediateTutorial. Utiliza este origen de datos para tener acceso a la vista vTimeSeries. Esta vista contiene los datos de origen que se utilizarán para entrenar el modelo de minería de datos. Si no está familiarizado con este proyecto o con estas vistas, vea[Lección 2: generar un escenario de previsión &#40;tutorial intermedio de minería de datos&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).  
  
     Ahora la apariencia de la instrucción completa debe ser como la siguiente:  
  
    ```  
    INSERT INTO MINING STRUCTURE [Forecasting_MIXED_Structure]  
    (  
       [ReportingDate],[ModelRegion],[Quantity],[Amount])  
    )  
    OPENQUERY(  
    [Adventure Works DW 2008R2],  
    'SELECT [ReportingDate],[ModelRegion],[Quantity],[Amount] FROM vTimeSeries ORDER BY [ReportingDate]'  
    )   
    ```  
  
6.  En el menú **archivo** , haga clic en **Guardar DMXQuery1. DMX como**.  
  
7.  En el cuadro de diálogo **Guardar como** , vaya a la carpeta correspondiente y asigne el nombre al archivo `ProcessForecastingAll.dmx` .  
  
8.  En la barra de herramientas, haga clic en el botón **Ejecutar** .  
  
 Cuando la consulta termine de ejecutarse, puede crear las predicciones mediante los modelos de minería de datos procesados. En la lección siguiente, creará varias predicciones basadas en los modelos de minería de datos que ha creado.  
  
## <a name="next-lesson"></a>Lección siguiente  
 [Lección 4: Creación de predicciones de serie temporal con DMX](../../2014/tutorials/lesson-4-creating-time-series-predictions-using-dmx.md)  
  
## <a name="see-also"></a>Consulte también  
 [Requisitos y consideraciones de procesamiento &#40;la minería de datos&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)   
 [&#60;consulta de datos de origen&#62;](/sql/dmx/source-data-query)   
 [OPENQUERY &#40;DMX&#41;](/sql/dmx/source-data-query-openquery)  
  
  
