---
title: Configurar propiedades de informes para informes de Power View | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0ffc5f44-17d3-42d4-bc2c-baf3b4485e2d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7776d9af8b2eb98533ac9ff2e7b1b8a760b92565
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748276"
---
# <a name="configure-reporting-properties-for-power-view-reports"></a>Configurar las propiedades de notificación para informes de Power View
  En esta lección complementaria, verá las propiedades de informes del proyecto Adventure Works Internet Sales Model. Las propiedades de informe facilitan a los usuarios finales la selección y presentación de datos del modelo en Power View. También establecerá las propiedades para ocultar ciertas columnas y tablas, y creará nuevos datos para usar en gráficos.  
  
 Tras completar esta lección y volver a implementar el modelo para una instancia de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] integrada con SharePoint y [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], puede crear un origen de datos, especificar la información de conexión de datos, iniciar Power View y diseñar informes con el modelo.  
  
 En esta lección no se describe cómo crear y usar los informes de Power View. Esta lección pretende proporcionar a los autores de modelos tabulares una introducción aquellas propiedades y opciones que afectan al modo en que los datos del modelo aparecerán en Power View. Para obtener información sobre cómo crear informes de Power View, vea [Tutorial: Crear un informe de ejemplo en Power View](https://go.microsoft.com/fwlink/?LinkId=221204).  
  
 Tiempo estimado para completar esta lección: **30 minutos**  
  
## <a name="prerequisites"></a>Requisitos previos  
 Este tema de la lección complementaria forma parte de un tutorial de creación de modelos tabulares, que se debe completar de forma ordenada. Antes de realizar las tareas de esta lección complementaria, debe haber completado todas las lecciones anteriores.  
  
 Para completar esta lección complementaria concreta, también debe tener lo siguiente:  
  
-   El Adventure Works Internet Sales Model (completado a través de este tutorial) listo para implementarse o ya implementado en una instancia de Analysis Services que se ejecuta en modo Tabular.  
  
-   Un sitio de SharePoint integrado con [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] ejecutándose en modo Tabular y [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)], configurado para admitir informes de Power View.  
  
-   Debe tener permisos suficientes para crear una conexión de datos en el sitio de SharePoint que señale al Adventure Works Internet Sales Model.  
  
## <a name="model-properties-that-affect-reporting"></a>Propiedades de modelo que afectan a los informes  
 Al crear un modelo tabular, hay ciertas propiedades que puede establecer en tablas y columnas individuales para mejorar la experiencia de informes del usuario final en Power View. Además, puede crear datos de modelo adicionales para permitir la visualización de datos y otras características específicas del cliente de informes. Para el Adventure Works Internet Sales Model de ejemplo, aquí se enumeran algunos de los cambios que hará:  
  
-   **Agregar nuevos datos** : al agregar datos nuevos en una columna calculada mediante una fórmula Dax, se crea información de fecha en un formato más fácil de mostrar en los gráficos.  
  
-   **Ocultar las tablas y las columnas que no son útiles para el usuario final** : la propiedad **Hidden** controla si las tablas y las columnas de tabla se muestran en el cliente de informes. Los elementos que están ocultos siguen siendo parte del modelo y permanecen disponibles para las consultas y los cálculos.  
  
-   **Habilitar tablas de un clic** : de forma predeterminada, no se produce ninguna acción si un usuario final hace clic en una tabla de la lista de campos. Para cambiar este comportamiento de modo que al hacer clic en la tabla, se agregue al informe, establecerá Conjunto de campos predeterminado en cada columna que desee incluir en la tabla. Esta propiedad se establece en las columnas de tabla que los usuarios finales es probable que deseen usar.  
  
-   **Establecer agrupación cuando sea necesario** : la propiedad **Mantener filas únicas** determina si los valores de la columna se deben agrupar por valores en un campo diferente, como un campo identificador. En las columnas que contienen valores duplicados, como Customer Name (por ejemplo, varios clientes denominados John Smith), es importante agrupar (mantener filas únicas) en el campo **Identificador de fila** para proporcionar a los usuarios finales los resultados correctos.  
  
-   **Establecer tipos de datos y formatos de datos** : de manera predeterminada, Power View aplica las reglas según el tipo de datos de columna a fin de determinar si el campo puede usarse como una medida. Dado que cada visualización de datos en Power View también tiene reglas sobre dónde se pueden colocar las medidas y las no medidas, es importante establecer el tipo de datos en el modelo o invalidar el predeterminado para lograr el comportamiento que quiera para el usuario final.  
  
-   **Establezca la propiedad ordenar por columna** : la propiedad **ordenar por columna** especifica si los valores de la columna se deben ordenar por valores en un campo diferente. Por ejemplo, en la columna Month Calendar que contiene el nombre de mes, ordene por la columna Month Number.  
  
## <a name="hide-tables-from-client-tools"></a>Ocultar las tablas de las herramientas de cliente  
 Dado que hay una columna calculada Product Category y otra Product Subcategory en la tabla calculated Product, no es necesario tener visibles las tablas Product Category y Product Subcategory para las aplicaciones cliente.  
  
#### <a name="to-hide-the-product-category-and-product-subcategory-tables"></a>Para ocultar las tablas Product Category y Product Subcategory  
  
1.  En el diseñador de modelos, haga clic con el botón derecho en la pestaña de la tabla **Product Category** y, después, haga clic en **Ocultar en herramientas cliente**.  
  
2.  Haga clic con el botón derecho en la pestaña de la tabla **Product Subcategory** y, después, haga clic en **Ocultar en herramientas cliente**.  
  
## <a name="create-new-data-for-charts"></a>Crear nuevos datos para gráficos  
 A veces puede ser necesario crear nuevos datos en el modelo mediante fórmulas DAX. En esta tarea, agregará dos columnas nuevas calculadas a la tabla Date. Estas columnas nuevas proporcionarán campos de fecha en un formato apropiado para usarse en gráficos.  
  
#### <a name="to-create-new-data-for-charts"></a>Para crear nuevos datos para gráficos  
  
1.  En la tabla **Date** , desplácese hasta la derecha y, después, haga clic en **Agregar columna**.  
  
2.  Agregue dos nuevas columnas calculadas con las fórmulas siguientes en la barra de fórmula:  
  
    |Nombre de columna|Fórmula|  
    |-----------------|-------------|  
    |Year Quarter|=[Calendar Year] & " Q" & [Calendar Quarter]|  
    |Year Month|=[Calendar Year] & FORMAT([Month],"#00")|  
  
## <a name="default-field-set"></a>Conjunto de campos predeterminado  
 El conjunto de campos predeterminado es una lista predefinida de columnas y medidas para una tabla que se agregan automáticamente a un lienzo de informe Power View cuando se selecciona la tabla en la lista de campos de informes. Esencialmente, puede especificar la clasificación de los campos, las medidas y las columnas predeterminadas que los usuarios desearán ver cuando esta tabla se visualice en informes Power View.  Para el modelo Internet Sales, definirá un conjunto de campos predeterminado y un orden para las tablas Customer, Geography y Product. Se incluyen solo aquellas columnas más comunes que los usuarios desearán ver al analizar los datos de Adventure Works Internet Sales con informes Power View.  
  
 Para obtener información detallada sobre el conjunto de campos predeterminado, vea [Configurar un conjunto de campos predeterminado para informes de Power View &#40;SSAS tabular&#41;](tabular-models/power-view-configure-default-field-set-for-reports.md) en los Libros en pantalla de SQL Server.  
  
#### <a name="to-set-default-field-set-for-tables"></a>Para establecer el conjunto de campos predeterminado para las tablas  
  
1.  En el diseñador de modelos, haga clic en la pestaña de la tabla **Customer** .  
  
2.  En la ventana **Propiedades** , en **Propiedades de informe**, en la propiedad **Conjunto de campos predeterminado** , haga clic en **Haga clic para editar** para abrir el cuadro de diálogo **Conjunto de campos predeterminado** .  
  
3.  En el cuadro de diálogo **Conjunto de campos predeterminado** , en el cuadro de lista **Campos de la tabla** , presione CTRL y seleccione los campos siguientes; después, haga clic en **Agregar**.  
  
     **Birth Date**, **Customer Alternate Id**, **First Name**, **Last Name**.  
  
4.  En la ventana **Campos predeterminados, en orden** , use los botones Mover arriba y Mover abajo para poner el orden siguiente:  
  
     **Id. alternativo del cliente**  
  
     **Nombre**  
  
     **Last Name**  
  
     **Fecha de nacimiento**.  
  
5.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Conjunto de campos predeterminado** para la tabla **Customer** .  
  
6.  Realice estos mismos pasos para la tabla **Geography** , seleccionando los campos siguientes y poniéndolos en este orden.  
  
     **Ciudad**, **código de provincia de estado**, **código de región de estado**.  
  
7.  Finalmente, realice estos mismos pasos para la tabla **Product** , seleccionando los campos siguientes y poniéndolos en este orden.  
  
     **Product Alternate Id**, **Product Name**.  
  
## <a name="table-behavior"></a>Comportamiento de tabla  
 Con las propiedades de Comportamiento de tabla, puede cambiar el comportamiento predeterminado de los diferentes tipos de visualización y el comportamiento de agrupación para las tablas usadas en los informes de Power View. Esto permite una ubicación predeterminada más eficaz de la información de identificación como los nombres, imágenes o títulos en los diseños de mosaico, tarjeta y gráfico.  
  
 Para obtener más información sobre las propiedades de comportamiento de una tabla, vea [Configurar las propiedades de comportamiento de las tablas para informes de Power View &#40;SSAS tabular&#41;](tabular-models/power-view-configure-table-behavior-properties-for-reports.md) en los Libros en pantalla de SQL Server.  
  
#### <a name="to-set-table-behavior-for-tables"></a>Para establecer el comportamiento de tabla de las tablas  
  
1.  En el diseñador de modelos, haga clic en la pestaña de la tabla **Customer** .  
  
2.  En la ventana **Propiedades** , en la propiedad **Comportamiento de tabla** , haga clic en **Haga clic para editar**para abrir el cuadro de diálogo **Comportamiento de tabla** .  
  
3.  En el cuadro de diálogo **Comportamiento de tabla** , en el cuadro de lista desplegable **Identificador de fila** , seleccione la columna **Customer Id** .  
  
4.  En el cuadro de lista **Mantener filas únicas** , seleccione **First Name** y **Last Name**.  
  
     Esta configuración de propiedad especifica que estas columnas proporcionan valores que se deben tratar como únicos aunque estén duplicados, por ejemplo, para cuando dos o varios empleados compartan el mismo nombre.  
  
5.  En el cuadro de lista desplegable **Etiqueta predeterminada** , seleccione la columna **Last Name** .  
  
     Esta configuración de propiedad especifica esta columna proporciona un nombre para mostrar para representar datos de fila.  
  
6.  Repita estos pasos con la tabla **Geography** , seleccionando la columna **Geography Id** como el identificador de fila y la columna **City** en el cuadro de lista **Mantener filas únicas** . No necesita establecer una etiqueta predeterminada para esta tabla.  
  
7.  Repita estos pasos con la tabla **Product** , seleccionando la columna **Product Id** como identificador de fila y la columna **Product Name** en el cuadro de lista **Mantener filas únicas** . En **Etiqueta predeterminada**, seleccione **Product Alternate Id**.  
  
## <a name="reporting-properties-for-columns"></a>Propiedades de informe para las columnas  
 Hay varias propiedades de columna básicas y propiedades de informe específicos en las columnas que puede establecer para mejorar la experiencia de informes de modelo. Por ejemplo, puede no ser necesario que los usuarios vena cada columna de cada tabla. Al igual que ocultó las tablas Product Category y Product subcategory antes, mediante la propiedad Hidden de una columna puede ocultar columnas concretas de una tabla que, de otro modo, se muestra. Otras propiedades, como Data Format y Sort by Column, también pueden afectar al modo en que los datos de columna pueden aparecer en los informes. Establecerá algunas de esas columnas concretas ahora. Otras columnas no requieren ninguna acción y no se muestran a continuación.  
  
 Solo establecerá algunas propiedades de columna distintas aquí, pero hay muchas otras. Para obtener más información sobre las propiedades de informes de columna, vea [Pestaña Propiedades de columna &#40;SSAS tabular&#41;](tabular-models/properties-ssas-tabular.md) en los Libros en pantalla de SQL Server.  
  
#### <a name="to-set-properties-for-columns"></a>Para establecer las propiedades de las columnas  
  
1.  En el diseñador de modelos, haga clic en la pestaña de la tabla **Customer** .  
  
2.  Haga clic en la columna **Customer Id** para mostrar las propiedades de columna en la ventana **Propiedades** .  
  
3.  En la ventana **Propiedades** , establezca la propiedad **Hidden** en True. La columna **Customer Id** se atenúa en el diseñador de modelos.  
  
4.  Repita estos pasos, estableciendo la columna siguiente y las propiedades de informes para cada tabla especificada. Deje las demás propiedades con su configuración predeterminada.  
  
     **Customer**  
  
    |Columna|Propiedad|Value|  
    |------------|--------------|-----------|  
    |Geography Id|Hidden|True|  
    |Birth Date|Formato de datos|Short Date|  
  
     **Date**  
  
    > [!NOTE]  
    >  Dado que la tabla Date se seleccionó como la tabla de fechas de modelos con la opción Marcar como tabla de fechas, en la lección 7, Marcar como tabla de fechas, y la columna Date de la tabla Date como la columna que se usa como identificador único, la propiedad Identificador de fila de la columna Date se establecerá automáticamente en True y no se puede cambiar. Cuando se usan funciones de inteligencia temporal en fórmulas DAX, debe especificar una tabla de fechas. En este modelo, creó una serie de medidas con las funciones de inteligencia temporal para calcular los datos de ventas para varios periodos como los trimestres anteriores y actuales y también para usarse en KPI. Para obtener más información sobre cómo especificar una tabla de fechas, vea [Especificar Marcar como tabla de fechas con inteligencia de tiempo &#40;SSAS tabular&#41;](tabular-models/specify-mark-as-date-table-for-use-with-time-intelligence-ssas-tabular.md) en los Libros en pantalla de SQL Server.  
  
    |Columna|Propiedad|Value|  
    |------------|--------------|-----------|  
    |Date|Formato de datos|Short Date|  
    |Día de la semana|Hidden|True|  
    |Nombre del día|Sort By Column|Día de la semana|  
    |Día de la semana|Hidden|True|  
    |Día del mes|Hidden|True|  
    |Día del año|Hidden|True|  
    |Nombre del mes|Sort By Column|Mes|  
    |Mes|Hidden|True|  
    |Month Calendar|Hidden|True|  
    |Trimestre fiscal|Hidden|True|  
    |Año fiscal|Hidden|True|  
    |Semestre fiscal|Hidden|True|  
  
     **Geografía**  
  
    |Columna|Propiedad|Value|  
    |------------|--------------|-----------|  
    |Geography Id|Hidden|True|  
    |Sales Territory Id|Hidden|True|  
  
     **Producto**  
  
    |Columna|Propiedad|Value|  
    |------------|--------------|-----------|  
    |Product Id|Hidden|True|  
    |Product Alternate Id|Etiqueta predeterminada|True|  
    |Id. de subcategoría del producto|Hidden|True|  
    |Fecha de inicio del producto|Formato de datos|Short Date|  
    |Fecha de finalización del producto|Formato de datos|Short Date|  
    |Foto grande|Hidden|True|  
  
     **Internet Sales**  
  
    |Columna|Propiedad|Value|  
    |------------|--------------|-----------|  
    |Product Id|Hidden|True|  
    |Customer Id|Hidden|True|  
    |Id. de promoción|Hidden|True|  
    |Id. de moneda|Hidden|True|  
    |Sales Territory Id|Hidden|True|  
    |Cantidad del pedido|Tipo de datos<br /><br /> Formato de datos<br /><br /> Decimal Places|Decimal Number<br /><br /> Decimal Number<br /><br /> 0|  
    |Order Date|Tipo de datos|Short Date|  
    |Due Date|Tipo de datos|Short Date|  
    |Ship Date|Tipo de datos|Short Date|  
  
## <a name="redeploy-the-adventure-works-internet-sales-tabular-model"></a>Volver a implementar el MT Ventas AW  
 Dado que ha cambiado el modelo, debe volver a implementarlo. Básicamente, repetirá las tareas realizadas en [Lección 14: Implementar](lesson-13-deploy.md).  
  
#### <a name="to-redeploy-the-adventure-works-internet-sales-tabular-model"></a>Para volver a implementar el modelo tabular Ventas por Internet de Adventure Works  
  
-   En [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], haga clic en el menú **Generar** y, después, haga clic en **Implementar el modelo Ventas por Internet de Adventure Works**.  
  
     Aparece el cuadro de diálogo **implementar** y muestra el estado de implementación de los metadatos, así como las tablas incluidas en el modelo.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Ahora puede usar Power View para visualizar los datos del modelo. Asegúrese de que las cuentas de Analysis Services y Reporting Services en el sitio de SharePoint tienen permisos de lectura en la instancia de Analysis Services donde implementó el modelo.  
  
 Para crear un origen de datos de informe de Reporting Services que señale al modelo, vea [Crear un origen de datos compartido para un modelo de datos (SSRS)](https://msdn.microsoft.com/library/hh270317%28v=SQL.110%29.aspx).  
  
  
