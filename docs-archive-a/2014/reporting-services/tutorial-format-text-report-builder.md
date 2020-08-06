---
title: 'Tutorial: Dar formato a texto (Generador de informes) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 67d8513e-8a70-464b-b87f-e91d010cfd82
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c96b500f8aa30b77c78f75ccd1342398fd44eb2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748598"
---
# <a name="tutorial-format-text-report-builder"></a>Tutorial: Dar formato a texto (Generador de informes)
  En este tutorial, puede practicar el proceso de dar formato al texto de varias maneras. Después de configurar el informe en blanco con el origen de datos y el conjunto de datos, puede escoger y elegir los pasos que desea explorar.  
  
 En la siguiente ilustración se muestra un informe similar al que creará.  
  
 ![rs_FormatTextFinal](../../2014/tutorials/media/rs-formattextfinal.gif "rs_FormatTextFinal")  
  
 En un paso puede cometer un error voluntario para ver por qué es un error. A continuación, corrija el error para lograr el efecto deseado.  
  
 Una versión mejorada del informe que creará en este tutorial está disponible como informe de ejemplo del Generador de informes de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Para obtener más información acerca de cómo descargar este informe de ejemplo y otros, vea [generador de informes informes de ejemplo](https://go.microsoft.com/fwlink/?LinkId=184851).  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a>Qué aprenderá  
  
### <a name="set-up-the-report"></a>Configurar el informe  
 1. [Crear un informe en blanco con un origen de datos y un conjunto de datos](#CreateReport)  
  
 2. [Agregar un campo a la superficie de diseño del informe(incorrectamente y, luego, correctamente)](#AddField)  
  
 3. [Agregar una tabla al informe Superficie de diseño](#AddTable)  
  
### <a name="pick-and-choose"></a>Escoger y elegir  
 [Agregar un hipervínculo al informe](#AddHyperlink)  
  
 [Girar texto en el informe](#RotateText)  
  
 [Mostrar texto con formato HTML](#FormatHTML)  
  
 [Formato de moneda](#FormatCurrency)  
  
 [Guardar el informe](#Save)  
  
 Tiempo estimado para completar este tutorial: 20 minutos.  
  
## <a name="requirements"></a>Requisitos  
 Para obtener más información sobre los requisitos, consulte [Requisitos previos para los tutoriales &#40;Generador de informes&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="create-a-blank-report-with-a-data-source-and-dataset"></a><a name="CreateReport"></a>Crear un informe en blanco con un origen de datos y un conjunto de datos  
  
#### <a name="to-create-a-blank-report"></a>Para crear un informe en blanco  
  
1.  Haga clic en **Inicio**, seleccione **Programas**, [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]**Generador de informes**y luego haga clic en **Generador de informes**.  
  
    > [!NOTE]  
    >  Debería aparecer el cuadro de diálogo **Introducción** . Si no hace, en el botón Generador de informes haga clic **Nuevo**.  
  
2.  En el panel izquierdo del cuadro de diálogo **Introducción** , compruebe que **Nuevo informe** está seleccionado.  
  
3.  En el panel derecho, haga clic en **Informe en blanco**.  
  
#### <a name="to-create-a-data-source"></a>Para crear un origen de datos  
  
1.  En el panel datos de informe, haga clic en **nuevo**y, a continuación, haga clic en **origen de datos**.  
  
2.  En el cuadro **Nombre** , escriba: **TextDataSource**  
  
3.  Haga clic en **Usar una conexión incrustada en mi informe**.  
  
4.  Compruebe que el tipo de conexión es Microsoft SQL Server y, a continuación, en el cuadro **cadena de conexión** , escriba: **origen de datos = \<servername> **  
  
    > [!NOTE]  
    >  La expresión \<servername>, por ejemplo Report001, especifica un equipo en el que se ha instalado una instancia del motor de SQL Server Database. Este tutorial no necesita datos concretos; solo necesita una conexión a una base de datos de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] . Si ya tiene una conexión a un origen de datos enumerada bajo **Conexiones de origen de datos**, puede seleccionarla e ir al procedimiento siguiente, "Para crear un conjunto de datos". Para obtener más información, consulte [Maneras alternativas de obtener una conexión de datos &#40;Generador de informes&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-create-a-dataset"></a>Para crear un conjunto de datos  
  
1.  En el panel Datos de informe, haga clic en **Nuevo**y, a continuación, haga clic en **Conjunto de datos**.  
  
2.  Compruebe que el origen de datos es **TextDataSource**.  
  
3.  En el cuadro **Nombre** , escriba: **TextDataset.**  
  
4.  Compruebe que el tipo de consulta **Texto** está seleccionado, y, a continuación, haga clic en **Diseñador de consultas**.  
  
5.  Haga clic en **Editar como texto**.  
  
6.  Pegue la siguiente consulta en el panel de consulta:  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13747.25 AS money) AS Sales, 55 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(9248.15 AS money) As Sales, 37 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1800.00 AS money) AS Sales, 24 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1125.00 AS money) AS Sales, 15 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,  'Lens Adapter' as Product, CAST(742.50 AS money) AS Sales, 11 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1417.50 AS money) AS Sales, 21 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13497.30 AS money) AS Sales, 54 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(11997.60 AS money) AS Sales, 48 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(10247.95 AS money) As Sales, 41 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Tripod' as Product, CAST(1200.00 AS money) AS Sales, 16 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(2025.00 AS money) AS Sales, 27 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1425.00 AS money) AS Sales, 19 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(887.50 AS money) AS Sales, 13 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Lens Adapter' as Product, CAST(607.50 AS money) AS Sales, 9 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1215.00 AS money) AS Sales, 18 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(10191.00 AS money) AS Sales, 79 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8772.00 AS money) AS Sales, 68 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(10578.00 AS money) AS Sales, 82 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(7218.10 AS money) AS Sales, 38 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory,'Digital' as Subcategory,'Slim Digital' as Product, CAST(9307.55 AS money) AS Sales, 49 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(3870.00 AS money) AS Sales, 30 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(5805.00 AS money) AS Sales, 45 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8643.00 AS money) AS Sales, 67 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(9877.40 AS money) AS Sales, 52 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(12536.70 AS money) AS Sales, 66 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(6648.25 AS money) AS Sales, 35 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    ```  
  
7.  Haga clic en Ejecutar (**!**) para ejecutar la consulta.  
  
     Los resultados de la consulta son los datos disponibles para mostrarse en su informe.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="add-a-field-to-the-report-design-surface"></a><a name="AddField"></a>Agregar un campo al informe Superficie de diseño  
 Si desea que un campo del conjunto de datos aparezca en un informe, su primer impulso puede ser arrastrarlo hasta la superficie de diseño directamente. En este ejercicio se describe por qué eso no funciona y lo que se ha de hacer en su lugar.  
  
#### <a name="to-add-a-field-to-the-report-and-get-the-wrong-result"></a>Para agregar un campo al informe (y obtener el resultado incorrecto)  
  
1.  Arrastre el campo **FullName** desde el panel Datos de informe hasta la superficie de diseño.  
  
     El Generador de informes crea un cuadro de texto con una expresión en él, representada como \<Expr>.  
  
2.  Haga clic en **Ejecutar**.  
  
     Tenga en cuenta que solo hay un registro, **Fernando Ross**, que es alfabéticamente el primer registro de la consulta. El campo no se repite para mostrar los otros registros de ese campo.  
  
3.  Haga clic en **Diseño** para volver a la vista de diseño.  
  
4.  Seleccione la expresión \<Expr> en el cuadro de texto.  
  
5.  En el panel Propiedades, para la propiedad **Value** verá lo siguiente (si no ve el panel Propiedades, en la pestaña **Ver** active **Propiedades**):  
  
    ```  
    =First(Fields!FullName.Value, "TextDataSet")  
    ```  
  
     La función `First` está diseñada para recuperar solo el primer valor de un campo y es lo que ha hecho.  
  
     Al arrastrar el campo hacia la superficie de diseño directamente, se creó un cuadro de texto. Por sí mismos, los cuadros de texto no son regiones de datos, de modo que no muestran datos de un conjunto de datos de informe. Los cuadros de texto de las regiones de datos, como tablas, matrices y listas, muestran datos.  
  
6.  Seleccione el cuadro de texto (si tiene la expresión seleccionada, presione ESC para seleccionarlo) y presione la tecla SUPRIMIR.  
  
#### <a name="to-add-a-field-to-the-report-and-get-the-right-result"></a>Para agregar un campo al informe (y obtener el resultado correcto)  
  
1.  En la pestaña **Insertar** de la cinta de opciones, en el área **Regiones de datos** , haga clic en **Lista**. Haga clic en la superficie de diseño y, a continuación, arrástrela para crear un cuadro que tenga aproximadamente dos pulgadas de ancho y una de alto.  
  
2.  Arrastre el campo **FullName** desde el panel Datos de informe hasta el cuadro de lista.  
  
     Esta vez el Generador de informes crea un cuadro de texto con la expresión `[FullName]` en él.  
  
3.  Haga clic en **Ejecutar**.  
  
     Tenga en cuenta que esta vez el cuadro se repite para mostrar todos los registros de la consulta.  
  
4.  Haga clic en **Diseño** para volver a la vista de diseño.  
  
5.  Seleccione la expresión en el cuadro de texto.  
  
6.  En el panel Propiedades, para la propiedad **Value** , ve lo siguiente:  
  
    ```  
    =Fields!FullName.Value  
    ```  
  
     Arrastrando el cuadro de texto hasta la región de datos de la lista, muestra los datos que hay en el conjunto de datos.  
  
7.  Seleccione el cuadro de lista y presione la tecla ELIMINAR.  
  
##  <a name="add-a-table-to-the-report-design-surface"></a><a name="AddTable"></a>Agregar una tabla al informe Superficie de diseño  
 Cree esta tabla para tener un lugar donde colocar los hipervínculos y el texto girado.  
  
#### <a name="to-add-a-table-to-the-report"></a>Para agregar una tabla al informe  
  
1.  En el menú **Insertar** , haga clic en **tabla**y, a continuación, haga clic en **Asistente para tablas**.  
  
2.  En la página **elegir un conjunto** de información del Asistente para nueva tabla o matriz, haga clic en **elegir un conjunto de los conjuntos de los existentes en este informe o en un conjunto de un conjunto**de los recursos, y haga clic en **TextDataset (en este informe)** y, a continuación, en **siguiente**.  
  
3.  En la página **organizar campos** , arrastre los **campos territorio**, **LinkText**y **Product** a **grupos de filas**, arrastre el campo **sales** hasta **valores**y, a continuación, haga clic en **siguiente**.  
  
4.  En la página **elegir el diseño** , desactive la casilla **expandir o contraer grupos** de modo que pueda ver toda la tabla y, a continuación, haga clic en **siguiente**.  
  
5.  En la página **elegir un estilo** , haga clic en **pizarra**y, a continuación, haga clic en **Finalizar**.  
  
6.  Arrastre la tabla para que esté bajo el bloque de títulos.  
  
7.  Haga clic en **Ejecutar**.  
  
     La tabla parece correcta, pero tiene dos filas con el título Total. El campo **LinkText** no necesita una fila total.  
  
8.  Haga clic en **Diseño** para volver a la vista de diseño.  
  
9. Haga clic con el botón secundario en el cuadro de texto que contiene `[LinkText]` y haga clic en **dividir celdas**.  
  
10. Seleccione la celda vacía situada debajo de la `[LinkText]` celda y, a continuación, mantenga presionada la tecla Mayús y seleccione las dos celdas hacia la derecha: la celda **total** de la columna **Product** y la `[Sum(Sales)]` celda de la columna **sales** .  
  
11. Con las tres celdas seleccionadas, haga clic con el botón secundario en una de esas celdas y haga clic en **Eliminar fila**.  
  
12. Haga clic en **Ejecutar**.  
  
##  <a name="add-a-hyperlink-to-the-report"></a><a name="AddHyperlink"></a>Agregar un hipervínculo al informe  
 En esta sección, agrega un hipervínculo al texto de la tabla desde la sección anterior.  
  
#### <a name="to-add-a-hyperlink-to-the-report"></a>Para agregar un hipervínculo al informe  
  
1.  Haga clic en **Diseño** para volver a la vista de diseño.  
  
2.  Haga clic con el botón secundario en la celda que contiene `[LinkText]`y haga clic en **Propiedades de cuadro de texto**.  
  
3.  En el cuadro **propiedades de cuadro de texto** , haga clic en **acción**.  
  
4.  Haga clic en **ir a dirección URL**.  
  
5.  En el cuadro **seleccionar dirección URL** , haga clic en **[URL]** y, a continuación, haga clic en **Aceptar**.  
  
6.  Observe que el texto no parece diferente. Necesita que se parezca al texto del vínculo.  
  
7.  Seleccione `[LinkText]`.  
  
8.  En la sección **fuente** de la pestaña **Inicio** , haga clic en el botón **subrayado** y, a continuación, haga clic en la flecha desplegable situada junto al botón **color** y haga clic en **azul**.  
  
9. Haga clic en **Ejecutar**.  
  
     Ahora el texto parece un vínculo.  
  
10. Haga clic en un vínculo. Si el equipo está conectado a Internet, un explorador abrirá a un tema de la Ayuda del Generador de informes.  
  
##  <a name="rotate-text-in-the-report"></a><a name="RotateText"></a>Girar texto en el informe  
 En esta sección, girará parte del texto de la tabla de las secciones anteriores.  
  
#### <a name="to-rotate-text"></a>Para girar el texto  
  
1.  Haga clic en **Diseño** para volver a la vista de diseño.  
  
2.  Haga clic en la celda que contiene `[Territory].`  
  
3.  En la pestaña **Inicio** , en la sección **Fuente** , haga clic en el botón **Negrita** .  
  
4.  Si el panel de propiedades no está abierto, en la pestaña **Ver** active la casilla **Propiedades** .  
  
5.  Busque la propiedad WritingMode en el panel de propiedades.  
  
    > [!NOTE]  
    >  Cuando las propiedades del panel de propiedades se organizan en categorías, WritingMode está en la categoría **Localización** . Asegúrese de haber seleccionado la celda y no el texto. WritingMode es una propiedad del cuadro de texto, no del texto.  
  
6.  En el cuadro de lista, haga clic en **Rotate270**.  
  
7.  En la pestaña **Inicio** de la sección **párrafo** , haga clic en los botones **central** y **central** para buscar el texto en el centro de la celda tanto vertical como horizontalmente.  
  
8.  Haga clic en Ejecutar (**!**).  
  
 Ahora el texto de la celda `[Territory]` está situado verticalmente desde la parte inferior a la parte superior de las celdas.  
  
##  <a name="displaying-text-with-html-formatting"></a><a name="FormatHTML"></a>Mostrar texto con formato HTML  
  
#### <a name="to-display-text-formatted-as-html"></a>Para mostrar texto con formato HTML  
  
1.  Haga clic en **Diseño** para cambiar a la vista de diseño.  
  
2.  En la pestaña **Insertar** , haga clic en **Cuadro de texto**y, después, en la superficie de diseño, haga clic y arrastre para crear un cuadro de texto bajo la tabla, aproximadamente de cuatro pulgadas de ancho y tres de alto.  
  
3.  Copie este texto y péguelo en el cuadro de texto:  
  
    ```  
    <h4>Limitations of cascading style sheet attributes</h4>  
          <p>Only a basic set of <b>cascading style sheet (CSS)</b> attributes are defined:</p>  
          <ul><li>  
              text-align, text-indent  
            </li><li>  
              font-family, font-size  
            </li><li>  
              color  
            </li><li>  
              padding, padding-bottom, padding-top, padding-right, padding-left  
            </li><li>  
              font-weight  
            </li></ul>  
    ```  
  
4.  Seleccione todo el texto del cuadro de texto.  
  
     Esta es una propiedad del texto, no del cuadro de texto, por lo que en un cuadro de texto puede tener una mezcla de texto sin formato y texto que usa etiquetas HTML como estilos.  
  
5.  Haga clic con el botón secundario en todo el texto seleccionado y, después, haga clic en **Propiedades del texto**.  
  
6.  En la página **General** , en **tipo de marcado**, haga clic en **HTML-interpretar etiquetas HTML como estilos**.  
  
7.  Haga clic en **OK**.  
  
8.  Haga clic en Ejecutar (**!**) para obtener la vista previa del informe.  
  
 El texto del cuadro de texto se muestra como un encabezado, párrafo y lista con viñetas.  
  
##  <a name="format-currency"></a><a name="FormatCurrency"></a>Formato de moneda  
  
#### <a name="to-format-numbers-as-currency"></a>Para dar formato a los números como moneda  
  
1.  Haga clic en **Diseño** para cambiar a la vista de diseño.  
  
2.  Haga clic en la celda de la tabla superior que contiene `[Sum(Sales)]`, mantenga presionada la tecla MAYÚS y haga clic en la celda de la tabla inferior que contiene `[Sum(Sales)]`.  
  
3.  En la pestaña **Inicio** , en el grupo **Número** , haga clic en el botón **Moneda** .  
  
4.  Opta En la pestaña **Inicio** , en el grupo **número** , haga clic en el botón estilos de marcador de **posición** y, a continuación, haga clic en valores de **ejemplo** para ver cómo se dará formato a los números.  
  
5.  (Opcional) En la pestaña **Inicio** , en el grupo **Número** , haga clic dos veces en el botón **Disminuir decimales** para mostrar las cifras en dólares sin centavos.  
  
6.  Haga clic en Ejecutar (**!**) para obtener la vista previa del informe.  
  
 El informe muestra ahora datos dados con formato y es más fácil de leer.  
  
##  <a name="save-the-report"></a><a name="Save"></a>Guardar el informe  
 Puede guardar los informes en un servidor de informes, en una biblioteca de SharePoint o en su equipo.  
  
 En este tutorial, guarde el informe en un servidor de informes. Si no tiene acceso a un servidor de informes, guarde el informe en su equipo.  
  
#### <a name="to-save-the-report-on-a-report-server"></a>Para guardar el informe en un servidor de informes  
  
1.  En el botón **Generador de informes** , haga clic en **Guardar como**.  
  
2.  Haga clic en **Sitios y servidores recientes**.  
  
3.  Seleccione o escriba el nombre del servidor de informes donde tiene el permiso para guardar los informes.  
  
     Aparecerá el mensaje "Conectando con el servidor de informes". Una vez completada la conexión, se mostrará el contenido de la carpeta de informes que el administrador del servidor de informes especificó como ubicación predeterminada para los informes.  
  
4.  En **Nombre**, reemplace el nombre predeterminado por un nombre de su elección.  
  
5.  Haga clic en **Save**(Guardar).  
  
 El informe se guarda en el servidor de informes. El nombre del servidor de informes al que está conectado aparecerá en la barra de estado en la parte inferior de la ventana.  
  
#### <a name="to-save-the-report-on-your-computer"></a>Para guardar el informe en el equipo  
  
1.  En el botón **Generador de informes** , haga clic en **Guardar como**.  
  
2.  Haga clic en **Escritorio**, **Mis documentos**o **Mi PC**y vaya a la carpeta donde desea guardar el informe.  
  
3.  En **Nombre**, reemplace el nombre predeterminado por un nombre de su elección.  
  
4.  Haga clic en **Save**(Guardar).  
  
## <a name="next-steps"></a>Pasos siguientes  
 Hay muchas maneras de dar formato al texto en Generador de informes [Tutorial: crear un informe de forma libre &#40;Generador de informes&#41;](../reporting-services/tutorial-creating-a-free-form-report-report-builder.md) contiene más ejemplos.  
  
## <a name="see-also"></a>Consulte también  
 [Tutoriales &#40;Generador de informes&#41;](report-builder-tutorials.md)   
 [Aplicar formato a los elementos de informe &#40;Generador de informes y SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md)   
 [Generador de informes en SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
