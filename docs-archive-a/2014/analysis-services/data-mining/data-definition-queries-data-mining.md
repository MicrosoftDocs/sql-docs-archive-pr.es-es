---
title: Consultas de definición de datos (minería de datos) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 49e02de1-4ffa-401c-8eee-471a9c25b86a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 153369979737dded52609843cd30cf914315e9cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87671269"
---
# <a name="data-definition-queries-data-mining"></a>Consultas de definición de datos (minería de datos)
  Para la minería de datos, la categoría *consulta de definición de datos* significa instrucciones DMX o comandos XMLA que hacen lo siguiente:  
  
-   Crear, modificar o manipular objetos de minería de datos, por ejemplo un modelo.  
  
-   Definir el origen de datos que se va a utilizar para entrenar o para la predicción.  
  
-   Exportar o importar modelos y estructuras de minería de datos.  
  
 [Crear consultas de definición de datos](#bkmk_Create)  
  
-   [Consultas de definición de datos en Herramientas de datos de SQL Server](#bkmk_ssdt)  
  
-   [Consultas de definición de datos en SQL Server Management Studio](#bkmk_SSMS)  
  
 [Generar script para instrucciones de definición de datos](#bkmk_Scripts)  
  
 [Generar script para instrucciones de definición de datos](#bkmk_Export)  
  
##  <a name="creating-data-definition-queries"></a><a name="bkmk_Create"></a>Crear consultas de definición de datos  
 Puede crear consultas de definición de datos (instrucciones) mediante el Generador de consultas de predicción en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] y [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], o mediante la ventana Consulta DMX en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Las instrucciones de definición de datos de DMX forman parte del lenguaje de definición de datos (DDL) de Analysis Services.  
  
 Para obtener información sobre la sintaxis de las instrucciones de definición de datos específicas, vea [Referencia de funciones de Extensiones de minería de datos &#40;DMX&#41;](/sql/dmx/data-mining-extensions-dmx-reference).  
  
###  <a name="data-definition-queries-in-sql-server-data-tools"></a><a name="bkmk_ssdt"></a>Consultas de definición de datos en SQL Server Data Tools  
 El Asistente para minería de datos es la herramienta preferida de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] para crear y modificar modelos y estructuras de minería de datos y para definir los orígenes de datos que se utilizan en las consultas de predicción y para entrenar.  
  
 Sin embargo, si desea conocer qué instrucciones envía el asistente al servidor para crear estructuras de datos o modelos de minería de datos, puede utilizar SQL Server Profiler para capturar instrucciones de definición de datos. Para más información, consulte [Use SQL Server Profiler to Monitor Analysis Services](../instances/use-sql-server-profiler-to-monitor-analysis-services.md).  
  
 Para ver las instrucciones utilizadas para definir los orígenes de datos utilizados para entrenar o la predicción, puede utilizar la **Vista SQL** en el Generador de consultas de predicción. A veces puede resultar útil compilar consultas básicas para entrenar y probar modelos utilizando el Generador de consultas de predicción, para establecer la sintaxis correcta. A continuación, puede pasar a la **Vista SQL** y editar manualmente la consulta. Para más información, consulte [Manually Edit a Prediction Query](manually-edit-a-prediction-query.md).  
  
###  <a name="data-definition-queries-in-sql-server-management-studio"></a><a name="bkmk_SSMS"></a>Consultas de definición de datos en SQL Server Management Studio  
 Para los objetos de minería de datos, puede utilizar consultas de definición de datos para realizar las siguientes acciones:  
  
-   Crear tipos de modelos específicos, como un modelo de agrupación en clústeres o modelo de árbol de decisión, mediante [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx).  
  
-   Modificar una estructura de minería de datos existente agregando un modelo o cambiando las columnas mediante [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx). Tenga en cuenta que no puede modificar un modelo de minería de datos mediante DMX; solo agregar nuevos modelos a una estructura existente.  
  
-   Realizar una copia de un modelo de minería de datos y, después, modificarlo mediante [SELECT INTO &#40;DMX&#41;](/sql/dmx/select-into-dmx).  
  
-   Definir el conjunto de datos usado para entrenar un modelo mediante [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) junto con una consulta de origen de datos como OPENROWSET.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] proporciona plantillas de consulta que pueden ayudarle a crear consultas de definición de datos. Para más información, consulte [Use Analysis Services Templates in SQL Server Management Studio](../instances/use-analysis-services-templates-in-sql-server-management-studio.md).  
  
 En general, las plantillas proporcionadas para [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] solo contienen la definición de la sintaxis general, que debe personalizar, escribiendo en la ventana **Consulta** , o utilizando el cuadro de diálogo proporcionado para especificar parámetros.  
  
 Para obtener un ejemplo de cómo especificar parámetros mediante la interfaz, vea [Crear una consulta de predicción singleton desde una plantilla](create-a-singleton-prediction-query-from-a-template.md).  
  
###  <a name="scripting-data-definition-statements"></a><a name="bkmk_Scripts"></a>Scripting de instrucciones de definición de datos  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] proporciona varios lenguajes de scripting y programación que puede utilizar para crear o modificar objetos de minería de datos, o definir orígenes de datos.  Aunque DMX está diseñado para acelerar las tareas de minería de datos, también puede utilizar XMLA y AMO para manipular objetos en scripts o en código personalizado.  
  
 El Complemento de minería de datos para Excel también incluye muchas plantillas de consulta y proporciona el **Editor de consultas avanzadas**, que le ayuda a crear instrucciones DMX complejas. Puede compilar una consulta interactivamente y, a continuación, cambiar a la Vista SQL para capturar la instrucción DMX.  
  
##  <a name="exporting-and-importing-models"></a><a name="bkmk_Export"></a>Exportar e importar modelos  
 Puede utilizar instrucciones de definición de datos en DMX para exportar la definición de un modelo y su estructura y orígenes de datos necesarios y, a continuación, importar la definición en un servidor diferente. La importación y exportación es la manera más rápida y fácil de mover modelos y estructuras de minería de datos entre las instancias de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Para obtener más información, vea [Administración de soluciones y objetos de minería de datos](management-of-data-mining-solutions-and-objects.md).  
  
> [!WARNING]  
>  Si su modelo se basa en datos de un origen de datos de cubo, no podrá utilizar DMX para exportar el modelo y deberá utilizar la copia de seguridad y restaurarlo en su lugar.  
  
##  <a name="related-tasks"></a><a name="bkmk_Tasks"></a> Tareas relacionadas  
 En la siguiente tabla se proporcionan vínculos a tareas relacionadas con consultas de definición de datos.  
  
|||  
|-|-|  
|Trabajar con plantillas para consultas DMX.|[Uso de las plantillas de Analysis Services en SQL Server Management Studio](../instances/use-analysis-services-templates-in-sql-server-management-studio.md)|  
|Diseñar consultas de todo tipo, utilizando el Generador de consultas de predicción.|[Crear una consulta de predicción con el Generador de consultas de predicción](create-a-prediction-query-using-the-prediction-query-builder.md)|  
|Capturar definiciones de consultas utilizando SQL Server Profiler y utilizar seguimientos para supervisar [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|[Usar SQL Server Profiler para supervisar Analysis Services](../instances/use-sql-server-profiler-to-monitor-analysis-services.md)|  
|Obtener más información sobre los lenguajes de scripting y lenguajes de programación proporcionados por [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|[Referencia XML for Analysis &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference)<br /><br /> [Desarrollar con Objetos de administración de análisis &#40;AMO&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)|  
|Obtener información sobre la administración de modelos en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] y [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].|[Exportar e importar objetos de minería de datos](export-and-import-data-mining-objects.md)<br /><br /> [EXPORT &#40;DMX&#41;](/sql/dmx/export-dmx)<br /><br /> [IMPORT &#40;DMX&#41;](/sql/dmx/import-dmx)|  
|Obtener más información sobre OPENROWSET y otras maneras de consultar datos externos.|[&#60;source data query&#62;](/sql/dmx/source-data-query).|  
  
## <a name="see-also"></a>Consulte también  
 [Asistente para minería de datos &#40;Analysis Services - Minería de datos&#41;](data-mining-wizard-analysis-services-data-mining.md)  
  
  
