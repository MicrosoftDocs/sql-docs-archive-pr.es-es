---
title: 'Tutorial: Agregar un minigráfico a un informe (Generador de informes) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 18c90a36-48bf-4805-a960-2d1e8f00c2dc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fb1bf83810b6c743b977e399864ce2edd514f572
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87747931"
---
# <a name="tutorial-add-a-sparkline-to-your-report-report-builder"></a>Tutorial: Agregar un minigráfico a un informe (Generador de informes)
  En este tutorial, crea un informe de la tabla básico basado en datos de ventas de ejemplo y, a continuación, agrega un minigráfico a una celda de la tabla.  
  
 Una versión mejorada del informe que creará en este tutorial está disponible como informe de ejemplo del Generador de informes de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Para obtener más información acerca de cómo descargar este informe de ejemplo y otros, vea [generador de informes informes de ejemplo](https://go.microsoft.com/fwlink/?LinkId=184851). La siguiente ilustración muestra un informe de ejemplo similar al que creará.  
  
 ![rs_SparklineMatrixTutorial](../../2014/tutorials/media/rs-sparklinematrixtutorial.gif "rs_SparklineMatrixTutorial")  
  
 En el vídeo [Cómo: crear un minigráfico en una tabla (generador de informes vídeo)](https://technet.microsoft.com/bi/ff871942.aspx) se muestra cómo crear un informe similar con minigráficos.  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a>Qué aprenderá  
 En este tutorial, aprenderá a realizar las siguientes tareas:  
  
 1. [Crear un informe con una tabla](#CreateTable)  
  
 2. [Crear una consulta en el Asistente para tablas o matrices](#Query)  
  
 3. [Agregar un minigráfico a la tabla](#Sparkline)  
  
 4. [Alinear los minigráficos vertical y horizontalmente](#AlignSparklines)  
  
### <a name="other-optional-steps"></a>Otros pasos opcionales  
 5. [Dar formato a los datos como moneda](#FormatCurrency)  
  
 6. [Dar formato a los datos como datos](#FormatDates)  
  
 7. [Cambiar el ancho de columna](#Width)  
  
 8. [Agregar un título de informe](#Title)  
  
 9. [Guardar el informe](#Save)  
  
 Tiempo estimado para completar este tutorial: 30 minutos.  
  
## <a name="requirements"></a>Requisitos  
 Para obtener más información sobre los requisitos, consulte [Requisitos previos para los tutoriales &#40;Generador de informes&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="1-create-a-report-with-a-table"></a><a name="CreateTable"></a>1. crear un informe con una tabla  
  
#### <a name="to-create-a-report"></a>Para crear un informe  
  
1.  Haga clic en **Inicio**, seleccione **Programas**, **Generador de informes de Microsoft SQL Server 2012**y, a continuación, haga clic en **Generador de informes**.  
  
     Se abre el cuadro de diálogo **Introducción**.  
  
    > [!NOTE]  
    >  Si el cuadro de diálogo **Introducción** no aparece, en el botón **generador de informes** , haga clic en **nuevo**.  
  
2.  En el panel de la izquierda, compruebe que está seleccionada la opción **Nuevo informe** .  
  
3.  En el panel de la derecha, haga clic en **Asistente para tabla o matriz**.  
  
4.  En la página **Elegir un conjunto de datos** , seleccione **Crear un conjunto de datos**y, después, haga clic en **Siguiente**. Se abre la página **Elegir una conexión a un origen de datos** .  
  
    > [!NOTE]  
    >  Este tutorial no necesita datos concretos; solo necesita una conexión a una base de datos de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] . Si ya tiene una conexión de origen de datos enumerada en **Conexiones de origen de datos**, puede seleccionarla e ir al paso 10. Para obtener más información, consulte [Maneras alternativas de obtener una conexión de datos &#40;Generador de informes&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).  
  
5.  Haga clic en **Nueva**. Se abre el cuadro de diálogo **Propiedades del origen de datos** .  
  
6.  En **Nombre**, escriba **Ventas de producto**como nombre del origen de datos.  
  
7.  En **Seleccionar un tipo de conexión**, compruebe que está seleccionado **Microsoft SQL Server** .  
  
8.  En **Cadena de conexión**, escriba el texto siguiente:  
  
     **Origen de datos =\<servername>**  
  
     La expresión \<servername>, por ejemplo Report001, especifica un equipo en el que se ha instalado una instancia del motor de SQL Server Database. Dado que los datos del informe no se extraen de una base de datos de SQL Server, no necesita incluir el nombre de una base de datos. Para analizar la consulta se utiliza la base de datos predeterminada en el servidor especificado.  
  
9. Haga clic en **Credenciales**. Escriba las credenciales necesarias para tener acceso al origen de datos externo.  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     Volverá a encontrarse en la página **Elegir una conexión a un origen de datos** .  
  
11. Para comprobar que se puede conectar al origen de datos, haga clic en **Probar conexión**.  
  
     Aparece un mensaje que indica que la conexión se ha creado correctamente.  
  
12. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
13. Haga clic en **Next**.  
  
##  <a name="2-create-a-query-in-the-table-wizard"></a><a name="Query"></a>2. crear una consulta en el Asistente para tablas  
 En un informe puede usar un conjunto de datos compartido que tenga una consulta predefinida o crear un conjunto de datos incrustado para usarlo exclusivamente en ese informe. En este tutorial, creará un conjunto de datos incrustado.  
  
> [!NOTE]  
>  En este tutorial, la consulta contiene los valores de datos, de forma que no necesita un origen de datos externo. Esto hace que la consulta requiera bastante tiempo. En un entorno empresarial, la consulta no contendría los datos. Esto es solo con fines de aprendizaje.  
  
#### <a name="to-create-a-query"></a>Para crear una consulta  
  
1.  En la página **Diseñar una consulta** , el diseñador de consultas relacionales está abierto. En este tutorial, usará el diseñador de consultas basado en texto.  
  
2.  Haga clic en **Editar como texto**. El diseñador de consultas basado en texto muestra un panel de consulta y un panel de resultados.  
  
3.  Pegue la siguiente consulta [!INCLUDE[tsql](../includes/tsql-md.md)] en el cuadro **Consulta** .  
  
    ```  
    SELECT CAST('2010-01-04' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2010-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Carrying Case' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2010-01-10' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Carrying Case' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2010-01-04' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Budget Movie-Maker' as Product, CAST(1056.00 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2010-01-05' AS date) as SalesDate,  'Accessories' as Subcategory,  
       'Slim Digital' as Product, CAST(1380.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2010-01-05' AS date) as SalesDate,'Accessories' as Subcategory,    
       'Budget Movie-Maker' as Product, CAST(780.00 AS money) AS Sales, 26 as Quantity  
    UNION SELECT CAST('2010-01-07' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(3798.00 AS money) AS Sales, 9 as Quantity  
    UNION SELECT CAST('2010-01-08' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(10400.00 AS money) AS Sales, 13 as Quantity  
    UNION SELECT CAST('2010-01-09' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(3000.00 AS money) AS Sales, 60 as Quantity  
    UNION SELECT CAST('2010-01-10' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(7234.50 AS money) AS Sales, 39 as Quantity  
    UNION SELECT CAST('2010-01-06' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Carrying Case' as Product, CAST(10836.00 AS money) AS Sales, 84 as Quantity  
    UNION SELECT CAST('2010-01-07' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Slim Digital' as Product, CAST(2550.00 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2010-01-04' AS date) as SalesDate, 'Digital' as Subcategory,   
       'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2010-01-08' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'Slim Digital' as Product, CAST(18530.00 AS money) AS Sales, 34 as Quantity  
    UNION SELECT CAST('2010-01-06' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'Slim Digital' as Product, CAST(26576.00 AS money) AS Sales, 88 as Quantity  
    ```  
  
4.  En la barra de herramientas del diseñador de consultas, haga clic en Ejecutar (**!**).  
  
     La consulta se ejecuta y muestra el conjunto de resultados para los campos **SalesDate**, **Subcategory**, **Product**, **Sales**y **Quantity**.  
  
5.  Haga clic en **Next**.  
  
6.  En la página **Organizar campos** , arrastre **Sales** hasta **Valores**.  
  
     La función Sum agrega**Sales** . El valor es [Sum(Sales)].  
  
7.  Arrastre **Product** hasta **Grupos de filas**.  
  
8.  Arrastre **SalesDate** hasta **Grupos de columnas**.  
  
9. Haga clic en **Next**.  
  
10. En la página **Elegir el diseño** , en **Opciones**, compruebe que esté seleccionada la opción **Mostrar subtotales y totales generales** .  
  
     El panel Vista previa del asistente muestra una tabla con tres filas. Al ejecutar el informe, cada fila se mostrará de la siguiente forma:  
  
    1.  La primera fila aparecerá una vez en la tabla para mostrar los encabezados de columna.  
  
    2.  La segunda fila se repetirá una vez en cada producto y mostrará el nombre del producto, el total por día y el total de línea.  
  
    3.  La tercera fila aparecerá una vez en la tabla para mostrar los totales generales.  
  
11. Haga clic en **Next**.  
  
12. En la página **Elegir un estilo** , en el panel **Estilos** , seleccione **Pizarra**.  
  
     El panel Vista previa muestra un ejemplo de la tabla con ese estilo.  
  
13. Haga clic en **Finalizar**  
  
14. La tabla se agrega a la superficie de diseño. La tabla tiene tres columnas y tres filas.  
  
     Busque en el panel Agrupación. Si no ve el panel Agrupación, en el menú **Vista** , haga clic en **Agrupación**. El panel Grupos de filas muestra un grupo de filas: **Product**. El panel Grupos de columnas muestra un grupo de columnas: **SalesDate**. Los datos detallados son todos los datos recuperados por la consulta del conjunto de datos.  
  
15. Haga clic en **Ejecutar** para obtener la vista previa del informe.  
  
##  <a name="3-add-a-sparkline"></a><a name="Sparkline"></a>3. agregar un minigráfico  
  
#### <a name="to-add-a-sparkline-chart-to-a-table"></a>Para agregar un minigráfico a una tabla  
  
1.  Haga clic en **Diseño** para volver a la vista de diseño.  
  
2.  Seleccione la columna Total en su tabla.  
  
3.  Haga clic con el botón derecho, señale **Insertar columna**y, después, haga clic en **Izquierda**.  
  
4.  En la nueva columna, haga clic con el botón secundario en la fila [product], seleccione la pestaña **Insertar** de la cinta de opciones y, a continuación, haga clic en **minigráfico**.  
  
5.  Asegúrese de que el primer minigráfico de la fila de **columna** está seleccionado y, a continuación, haga clic en **Aceptar**.  
  
6.  Haga clic en el minigráfico para mostrar el panel Datos del gráfico.  
  
7.  Haga clic en el signo más (+) en el cuadro valores y, a continuación, haga clic en **ventas**.  
  
     Los valores del campo **Sales** son ahora los valores para el minigráfico.  
  
8.  Haga clic en el signo más (+) en el cuadro grupos de categorías y, a continuación, haga clic en **fechaventa**.  
  
9. Haga clic en **Ejecutar** para obtener una vista previa del informe.  
  
     Tenga en cuenta que hay minigráficos en cada fila de la tabla, pero no son correctos. Las barras de los gráficos no están alineadas entre sí. Solo hay cuatro barras en la segunda fila de datos, por lo que las barras son más anchas que las de la primera fila, que tiene seis. No puede comparar los valores para cada producto por día. Tienen que estar alineados entre sí.  
  
     Además, observe que para cada fila, la barra más alta de esa fila es el alto de la fila. Esto también es engañoso, porque los valores más grandes de cada fila no son iguales: el valor más grande de Budget Movie-Maker es $10.400, pero el valor más grande para digital delgada es $26.576-más de dos veces más grande. Además, las barras más grandes de esas dos filas tienen aproximadamente el mismo alto. También es necesario realizar esto para ajustarse a los demás minigráficos.  
  
     ![rs_SprklineMtrxUnaligndBars](../../2014/tutorials/media/rs-sprklinemtrxunaligndbars.gif "rs_SprklineMtrxUnaligndBars")  
  
##  <a name="4-align-the-sparklines-vertically-and-horizontally"></a><a name="AlignSparklines"></a>4. alinear los minigráficos vertical y horizontalmente  
 Los minigráficos son difíciles de leer cuando no todos usan las mismas medidas. Los ejes horizontal y vertical de cada uno tienen que coincidir con el resto.  
  
#### <a name="to-set-alignment-for-the-sparklines-in-the-table"></a>Para establecer la alineación de los minigráficos en la tabla  
  
1.  Haga clic en **Diseño** para volver a la vista de diseño.  
  
2.  Haga clic con el botón derecho en el minigráfico y, después, haga clic en **Propiedades del eje vertical**.  
  
3.  Active la casilla **Alinear ejes en** .  
  
     Tablix1 aparecerá en la lista. Es la única opción. Establece el alto de las barras en cada minigráfico con respecto a los demás.  
  
4.  Haga clic en **OK**.  
  
5.  Haga clic con el botón derecho en el minigráfico y, después, haga clic en **Propiedades del eje horizontal**.  
  
6.  Active la casilla **Alinear ejes en** .  
  
     Tablix1 aparecerá en la lista. Es la única opción. Establece el ancho de las barras en cada minigráfico con respecto a los demás. Si algunos minigráficos tienen menos barras que otros, dichos minigráficos tendrán espacios en blanco correspondientes a los datos que faltan.  
  
7.  Haga clic en **OK**.  
  
8.  Para volver a obtener una vista previa de un informe, haga clic en **Ejecutar** .  
  
 Observe que todas las barras están ahora alineadas con las barras de las demás filas.  
  
##  <a name="5-optional-format-data-as-currency"></a><a name="FormatCurrency"></a>5. (opcional) dar formato a los datos como moneda  
 De forma predeterminada, los datos de resumen del campo **sales** muestran un número general. Aplíquele el formato adecuado para mostrar el número como moneda. Alterne **Estilos de marcador de posición** para mostrar los cuadros de texto con formato y el texto de marcador de posición como valores de ejemplo.  
  
#### <a name="to-format-a-currency-field"></a>Para dar formato a un campo de moneda  
  
1.  Haga clic en **Diseño** para cambiar a la vista de diseño.  
  
2.  Haga clic en la celda de la segunda fila (bajo la fila de encabezados de columna) en la columna **fechaventa** y arrastre para seleccionar todas las celdas que contienen `[Sum(Sales)]` .  
  
3.  En la pestaña **Inicio** , en el grupo **Número** , haga clic en el botón **Moneda** . Las celdas cambian para mostrar la moneda con formato.  
  
     Si la configuración regional es Inglés (Estados Unidos), el texto de ejemplo predeterminado es [**$12,345.00**]. Si no ve un valor de moneda de ejemplo, haga clic en **estilos de marcador de posición** en el grupo **números** y, a continuación, haga clic en **valores de ejemplo**.  
  
4.  Haga clic en **Ejecutar** para obtener una vista previa del informe.  
  
 Los valores de Resumen de **sales** se muestran como moneda.  
  
##  <a name="6-optional-format-data-as-dates"></a><a name="FormatDates"></a>6. (opcional) dar formato a los datos como fechas  
 De forma predeterminada, el campo **fechaventa** muestra información de fecha y hora. Puede darle formato para mostrar solo la fecha.  
  
#### <a name="to-format-a-date-field-as-the-default-format"></a>Para dar formato a un campo de fecha como el formato predeterminado  
  
1.  Haga clic en **Diseño** para volver a la vista de diseño.  
  
2.  Haga clic en la celda que contiene `[SalesDate]`.  
  
3.  En la cinta de opciones, en la pestaña **Inicio** , en el grupo **número** , en la lista desplegable, seleccione **fecha**.  
  
     La celda muestra la fecha de ejemplo **[1/31/2000]**. Si no ve un valor de fecha de ejemplo, haga clic en **Estilos de marcador de posición** en el grupo **Números** y, después, haga clic en **Valores de ejemplo**.  
  
4.  Haga clic en **Ejecutar** para obtener la vista previa del informe.  
  
 Los valores de **fechaventa** se muestran en el formato de fecha predeterminado.  
  
##  <a name="7-optional-change-column-widths"></a><a name="Width"></a>7. (opcional) cambiar el ancho de las columnas  
 De forma predeterminada, cada celda de una tabla contiene un cuadro de texto. Un cuadro de texto se expande verticalmente para alojar el texto cuando se representa la página. En el informe representado, cada fila se expande hasta el alto del cuadro de texto más alto representado de la fila. El alto de la fila en la superficie de diseño no tiene efecto alguno en el alto de la fila en el informe representado.  
  
 Para reducir la cantidad de espacio vertical que ocupa cada fila, expanda el ancho de columna para dar cabida en una línea al contenido previsto de los cuadros de texto de la columna.  
  
#### <a name="to-change-the-width-of-columns"></a>Para cambiar el ancho de las columnas  
  
1.  Haga clic en **Diseño** para volver a la vista de diseño.  
  
2.  Haga clic en la tabla para que los identificadores de columna y de fila aparezcan encima y al lado de la tabla.  
  
     Las barras grises situadas en la parte superior y en el lado de la tabla son los identificadores de fila y de columna.  
  
3.  Sitúe el cursor en la línea que hay entre los controladores de columna para que cambie a una flecha doble. Arrastre las columnas hasta que tengan el tamaño deseado. Por ejemplo, expanda la columna de **Product** para que el nombre de producto se muestre en una línea.  
  
4.  Haga clic en **Ejecutar** para obtener una vista previa del informe.  
  
##  <a name="8-optional-add-a-report-title"></a><a name="Title"></a>8. (opcional) agregar un título de informe  
 Los títulos de informe aparecen en la parte superior. Puede situar el título del informe en un encabezado de informe o, si el informe no lo utiliza, en un cuadro de texto en la parte superior del cuerpo del informe. En este tutorial, deberá utilizar el cuadro de texto que se coloca automáticamente en la parte superior del cuerpo del informe.  
  
 El texto se puede mejorar aún más aplicando estilos de fuente, tamaños y colores diferentes a las frases y caracteres individuales. Para obtener más información, vea [Dar formato al texto en un cuadro de texto &#40;Generador de informes y SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md).  
  
#### <a name="to-add-a-report-title"></a>Para agregar un título de informe  
  
1.  En la superficie de diseño, haga clic en **Haga clic para agregar título**.  
  
2.  Escriba **Ventas del producto**y después haga clic fuera del cuadro de texto.  
  
3.  Haga clic con el botón secundario en el cuadro de texto que contiene **Ventas del producto** y haga clic en **Propiedades de cuadro de texto**.  
  
4.  En el cuadro de diálogo **Propiedades de cuadro de texto** , haga clic en **Fuente**.  
  
5.  En la lista **Tamaño** , seleccione **18 pt**.  
  
6.  En la lista **color** , seleccione **granate**.  
  
7.  Seleccione **Negrita**.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="9-save-the-report"></a><a name="Save"></a>9. guardar el informe  
 Guarde el informe un servidor de informes o en su equipo. Si no guarda el informe en el servidor de informes, varias características de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , como los elementos de informe y los subinformes, no estarán disponibles.  
  
#### <a name="to-save-the-report-on-a-report-server"></a>Para guardar el informe en un servidor de informes  
  
1.  En el botón **Generador de informes** , haga clic en **Guardar como**.  
  
2.  Haga clic en **Sitios y servidores recientes**.  
  
3.  Seleccione o escriba el nombre del servidor de informes donde tiene el permiso para guardar los informes.  
  
     Aparecerá el mensaje "Conectando con el servidor de informes". Una vez completada la conexión, se mostrará el contenido de la carpeta de informes que el administrador del servidor de informes especificó como ubicación predeterminada para los informes.  
  
4.  En **Nombre**, reemplace el nombre predeterminado por **Ventas de producto**.  
  
5.  Haga clic en **Save**(Guardar).  
  
 El informe se guarda en el servidor de informes. El nombre del servidor de informes al que está conectado aparecerá en la barra de estado en la parte inferior de la ventana.  
  
#### <a name="to-save-the-report-on-your-computer"></a>Para guardar el informe en el equipo  
  
1.  En el botón **Generador de informes** , haga clic en **Guardar como**.  
  
2.  Haga clic en **Escritorio**, **Mis documentos**o **Mi PC**y vaya a la carpeta donde quiere guardar el informe.  
  
3.  En **Nombre**, reemplace el nombre predeterminado por **Ventas de producto**.  
  
4.  Haga clic en **Save**(Guardar).  
  
## <a name="next-steps"></a>Pasos siguientes  
 Esto concluye el tutorial para crear un informe de tabla con minigráficos. Para obtener más información sobre minigráficos, vea [Minigráficos y barras de datos &#40;Generador de informes y SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Consulte también  
 [Tutoriales &#40;Generador de informes&#41;](report-builder-tutorials.md)   
 [Generador de informes en SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
