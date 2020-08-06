---
title: Parámetros de informe (Generador de informes y Diseñador de informes) | Microsoft Docs
ms.custom: ''
ms.date: 07/27/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.subreportproperties.parameters.f1
- sql12.rtp.rptdesigner.reportparameters.general.f1
- "10091"
- "10073"
- "10070"
- sql12.rtp.rptdesigner.reportparameters.advanced.f1
ms.assetid: 58b96555-d876-4f61-bff8-db5764b9f5f9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 15d8898a18e143c7954766b5a0bf9e7bb6d068eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672678"
---
# <a name="report-parameters-report-builder-and-report-designer"></a>Parámetros de informe (Generador de informes y Diseñador de informes)
  Este tema describe los usos habituales de los parámetros de informe de SSRS, las propiedades que puede establecer y muchas cosas más relativas a los parámetros. Los parámetros de informe le permiten controlar datos de informe, conectar informes relacionados y cambiar la presentación de los informes.  
  
[!INCLUDE[applies](../../includes/applies-md.md)]Modo de SharePoint y modo nativo
  
 Para consultar una demostración sobre cómo agregar un parámetro a un informe, vea [Tutorial: Agregar parámetros a un informe (SSRS)](https://technet.microsoft.com/library/aa337432\(v=SQL.105\).aspx)  

  
##  <a name="common-uses-for-parameters"></a><a name="bkmk_Common_Uses_for_Parameters"></a> Usos comunes de los parámetros  
 Estos son algunos de los usos más comunes de los parámetros.  
  
 **Controlar datos de informe**  
  
-   Filtre los datos del informe en el origen de datos escribiendo las consultas del conjunto de datos que incluyen variables.  
  
-   Filtrar datos desde un conjunto de datos compartido Cuando se agrega un conjunto de datos compartido a un informe, no se puede cambiar la consulta. En el informe, podrá agregar un filtro del conjunto de datos que incluya una referencia al parámetro de informe creado por usted.  
  
-   Permitir a los usuarios especificar valores para personalizar los datos de un informe. Por ejemplo, para proporcionar dos parámetros para la fecha de inicio y de finalización de los datos de ventas.  
  
 **Conectar informes relacionados**  
  
-   Use parámetros para relacionar informes principales con informes detallados, así como a subinformes e informes vinculados. Cuando se diseña un conjunto de informes, cada informe se puede diseñar de tal modo que responda a determinadas preguntas. Cada informe puede aportar un punto de vista o un nivel de detalle distinto sobre la información relacionada. Para ofrecer un conjunto de informes interrelacionados, cree parámetros para los datos relacionados en los informes de destino.  
  
     Para más información, vea [Informes detallados &#40;Generador de informes y SSRS&#41;](drillthrough-reports-report-builder-and-ssrs.md), [Subinformes &#40;Generador de informes y SSRS&#41;](subreports-report-builder-and-ssrs.md) y [Crear un informe vinculado](../reports/create-a-linked-report.md).  
  
-   Personalizar conjuntos de parámetros para varios usuarios. Crear dos informes vinculados basados en un informe de ventas en el servidor de informes. Uno utilizará valores de parámetro predefinidos para los vendedores y el otro, para los directores de ventas. Ambos informes utilizan la misma definición de informe.  
  
 **Cambiar la presentación de los informes**  
  
-   Envíe comandos a un servidor de informes a través de una solicitud URL, para personalizar la representación de un informe. Para más información, vea [Acceso URL &#40;SSRS&#41;](../url-access-ssrs.md) y [Pasar un parámetro de informe en una dirección URL](../pass-a-report-parameter-within-a-url.md).  
  
-   Permitir a los usuarios especificar valores para ayudarles a personalizar la apariencia de un informe. Por ejemplo, proporcionar un parámetro Boolean para indicar si se expandirán o contraerán todos los grupos de filas anidadas de una tabla.  
  
-   Permita a los usuarios personalizar los datos y apariencia de un informe mediante la incorporación de parámetros en una expresión.  
  
     Para más información, vea [Usar referencias a la colección de parámetros &#40;Generador de informes y SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md).  
  
##  <a name="parameter-pane"></a><a name="UserInterface"></a>Panel de parámetros  
 Cuando ve un informe, la barra de herramientas del Visor de informes muestra cada uno de los parámetros para que los usuarios puedan especificar valores de forma interactiva. En la ilustración siguiente se muestra el área de parámetros de un informe que tiene parámetros @StartDate ,, @EndDate @Subcategory y @ShowAllRows .  
  
 ![rs_ParameterStory](../media/rs-parameterstory.gif "rs_ParameterStory")  
  
1.  **Panel Parámetros** : la barra de herramientas del Visor de informes muestra un mensaje de petición de datos y un valor predeterminado para cada parámetro. Automáticamente se da formato al diseño de parámetro en la barra de herramientas. El orden viene determinado por el orden de aparición de los parámetros en el panel Datos de informe.  
  
2.  ** @StartDate y @EndDate Parameters** el parámetro @StartDate es del tipo de datos `DateTime` . El mensaje de petición de datos Start Date aparece junto al cuadro de texto. Para modificar la fecha, escriba una nueva en el cuadro de texto o utilice el control de calendario.  
  
     El parámetro @EndDate aparece junto a @StartDate .  
  
3.  ** @Subcategory parámetro** el parámetro @Subcategory es del tipo de datos `Text` . Dado @Subcategory que tiene una lista de valores disponibles, los valores válidos aparecen en una lista desplegable. Debe elegir los valores de esa lista. Dado @Subcategory que tiene varios valores, aparece la opción **seleccionar todo** , que le permite borrar todos los valores de la lista y seleccionarlos.  
  
4.  ** @ShowAllRows parámetro** el parámetro @ShowAllRows es del tipo de datos `Boolean` . Utilice los botones de radio para especificar `True` o `False`.  
  
5.  **Identificador Mostrar u ocultar área de parámetros** : en la barra de herramientas del Visor de informes, haga clic en esta flecha para mostrar u ocultar el panel de parámetros.  
  
6.  **Botón Parámetros** : en la vista previa del Generador de informes, en la Cinta de opciones, haga clic en el botón **Parámetros** para mostrar u ocultar el panel de parámetros.  
  
7.  **Botón Ver informe** : en la barra de herramientas del Visor de informes, haga clic en **Ver informe** para ejecutar el informe después de escribir los valores de parámetro. Si todos los parámetros poseen valores predeterminados, el informe se ejecuta automáticamente en la primera vista.  
  
##  <a name="creating-parameters"></a><a name="bkmk_Create_Parameters"></a> Crear parámetros  
 Puede crear parámetros de informe de las formas siguientes:  
  
-   Agregue una consulta de conjunto de datos que contenga variables o un procedimiento almacenado de conjunto de datos que contenga parámetros de entrada. Los parámetros de conjunto de datos se crean para cada variable o parámetro de entrada y los parámetros de informe se crean para cada parámetro de conjunto de datos.  
  
     La siguiente imagen del Generador de informes ilustra una consulta de conjunto de datos con una variable (1) y el parámetro de conjunto de datos (2) correspondiente y el parámetro de informe (3).  
  
     ![Cuadro de diálogo de propiedades de conjuntos de datos y panel de informes](../media/datasetquery-parameters.png "Cuadro de diálogo de propiedades de conjuntos de datos y panel de informes")  
  
    > **NOTA:** No todos los orígenes de datos son compatibles con los parámetros.  
  
     El conjunto de datos se puede incrustar o compartir. Cuando se agrega un conjunto de datos compartido a un informe, los parámetros de conjunto de datos que están marcados como internos no se pueden invalidar en el informe. Podrá invalidar parámetros de conjunto de datos que no estén marcados como internos.  
  
     Para obtener más información, vea [Consultas de conjunto de datos](#bkmk_Dataset_Parameters) en este tema.  
  
-   Cree un parámetro manualmente desde el panel Datos de informe.  
  
     Puede configurar parámetros de informe para que un usuario pueda especificar de forma interactiva valores que le permitan a personalizar el contenido o la apariencia de un informe. También puede configurar parámetros de informe para que un usuario no pueda cambiar los valores preconfigurados.  
  

  > **NOTA:** Puesto que los parámetros se administran de forma independiente en el servidor, al volver a publicar un informe principal con una nueva configuración de parámetros, no se sobrescribe la configuración de parámetros existente del informe.  
  
-   Agregue un elemento de informe que contenga referencias a un parámetro o a un conjunto de datos compartido que contenga variables.  
  
     Los elementos de informe se almacenan en el servidor de informes y están disponibles para que otros usuarios los utilicen en sus informes. Los elementos de informe que representan parámetros no se pueden administrar en el servidor de informes. Puede buscar los parámetros en la galería de elementos de informe y una vez agregados, configurarlos en su informe. Para más información, vea [Elementos de informe &#40;Generador de informes y SSRS&#41;](../report-parts-report-builder-and-ssrs.md).  
     
   > **NOTA:** Los parámetros se pueden publicar como elemento de informe independiente para las regiones de datos que tienen conjuntos de datos dependientes con parámetros. Aunque los parámetros se enumeren como elemento de informe, no puede agregar un parámetro de elemento de informe directamente a un informe. En lugar de ello, agregue el elemento de informe y los parámetros de informe necesarios se generan automáticamente a partir de las consultas de conjunto de datos que se encuentran en el elemento de informe, o a las que este hace referencia. Para más información sobre los elementos de informe, vea [Elementos de informe &#40;Generador de informes y SSRS&#41;](../report-parts-report-builder-and-ssrs.md) y [Elementos de informe en el Diseñador de informes &#40;SSRS&#41;](report-parts-in-report-designer-ssrs.md).  
  
### <a name="parameter-values"></a>Valores de parámetros  
 A continuación, se presentan las opciones para seleccionar valores de parámetro en el informe.  
  
-   Seleccione un único valor de parámetro de la lista desplegable.  
  
-   Seleccione varios valores de parámetro en la lista desplegable.  
  
-   Seleccione un valor de la lista desplegable para un parámetro, el cual determina los valores que están disponibles en la lista desplegable para otro parámetro. Se trata de parámetros en cascada. Los parámetros en cascada le permitirán filtrar sucesivamente los valores de parámetro para reducir los miles de valores posibles a un número más fácil de manejar.  
  
     Para más información, vea [Agregar parámetros en cascada a un informe &#40;Generador de informes y SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md).  
  
-   Ejecute el informe sin necesidad de seleccionar antes un valor de parámetro porque se ha creado un valor predeterminado para el parámetro.  
  
##  <a name="report-parameter-properties"></a><a name="bkmk_Report_Parameters"></a>Propiedades de los parámetros de informe  
 Puede cambiar las propiedades del parámetro de informe si usa el cuadro de diálogo Propiedades del informe. En la siguiente tabla se resumen las propiedades que se pueden establecer para cada parámetro:  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|Nombre|Escriba un nombre de parámetro con distinción de mayúsculas y minúsculas. El nombre debe comenzar por una letra y puede incluir letras, números y caracteres de subrayado (_). El nombre no puede contener espacios. En el caso de los parámetros generados automáticamente, el nombre coincide con el parámetro en la consulta de conjunto de datos. De forma predeterminada, los parámetros creados manualmente deben similares a ReportParameter1.|  
|Prompt|El texto que aparece junto al parámetro en la barra de herramientas del Visor de informes.|  
|Tipo de datos|Cuando se definen los valores disponibles para un parámetro, el usuario elige los valores en una lista desplegable, aunque el tipo de datos sea `DateTime` . Un parámetro de informes debe ser de uno de los siguientes tipos de datos:<br /><br /> `Boolean`. El usuario selecciona True o False en un botón de opción.<br /><br /> `DateTime`. El usuario selecciona una fecha en un control de calendario.<br /><br /> **Entero**. El usuario escribe valores en un cuadro de texto.<br /><br /> Valor **float**. El usuario escribe valores en un cuadro de texto.<br /><br /> `Text`. El usuario escribe valores en un cuadro de texto.<br /><br /> Para obtener más información acerca de los tipos de datos de informe, vea [RDL Data Types](../reports/report-definition-language-ssrs.md#bkmk_RDL_Data_Types).|  
|Permitir valor en blanco|Seleccione esta opción si el valor del parámetro puede ser una cadena vacía o estar en blanco.<br /><br /> Si especifica los valores válidos de un parámetro, y desea que el valor en blanco sea uno de ellos, deberá incluirlo como uno de los valores que especifique. La selección de esta opción no incluye automáticamente el espacio en blanco entre los valores disponibles.|  
|Permitir valor NULL|Seleccione esta opción si el valor del parámetro puede ser un valor NULL.<br /><br /> Si especifica los valores válidos de un parámetro, y desea que el valor NULL sea uno de ellos, deberá incluirlo como uno de los valores que especifique. La selección de esta opción no incluye automáticamente NULL entre los valores disponibles.|  
|Permitir varios valores|Proporcione los valores disponibles para crear una lista desplegable que permita realizar selecciones a los usuarios. Esta es una buena forma de asegurarse de que solo se enviarán valores válidos en una consulta de conjunto de datos.<br /><br /> Seleccione esta opción si el valor del parámetro puede ser varios valores que se muestran en una lista desplegable. No se admiten valores NULL. Cuando esta opción está seleccionada, se agregan casillas a la lista de valores disponibles en una lista desplegable de parámetros. La parte superior de la lista incluye una casilla para **Seleccionar todo**. Los usuarios pueden activar los valores que desean usar.<br /><br /> Si los datos que proporcionan valores cambian rápidamente, podría darse el caso de que la lista que ve el usuario no sea la más actualizada.|  
|Visible|Seleccione esta opción si desea mostrar el parámetro de informe en la parte superior del informe al ejecutarse éste. Esta opción permite a los usuarios seleccionar los valores de los parámetros en tiempo de ejecución.|  
|Hidden|Seleccione esta opción si desea ocultar el parámetro de informe en el informe publicado. Los valores del parámetro de informe pueden continuar estableciéndose en una dirección URL de informe, en una definición de suscripción o en el servidor de informes.|  
|Interno|Seleccione esta opción para ocultar el parámetro de informe. En el informe publicado, el parámetro de informe solamente podrá verse en la definición de informe.|  
|Valores disponibles|Si ha especificado los valores disponibles de un parámetro, los valores válidos aparecerán siempre como una lista desplegable. Por ejemplo, si proporciona los valores disponibles para un parámetro `DateTime`, aparecerá una lista desplegable para las fechas en el panel de parámetros en lugar de un control de calendario. Para asegurarse de que exista una lista de valores coherente entre un informe y los subinformes, puede establecer una opción en el origen de datos para utilizar una transacción única para todas las consultas de los conjuntos de datos que estén asociadas a un origen de datos.<br /><br /> Nota de seguridad en cualquier informe que incluya un parámetro de tipo de datos, asegúrese de usar una lista de valores disponibles (también conocida como lista de valores válidos) y asegúrese de que los usuarios que ejecuten el informe solo tengan los permisos necesarios para ver los datos del informe. ** \* \* \* \* ** `Text` Para más información, vea [Seguridad &#40;Generador de informes&#41;](../report-builder/security-report-builder.md).|  
|Valores predeterminados|Establezca los valores predeterminados a partir de una consulta o de una lista estática.<br /><br /> Los informes se ejecutan de forma automática en la primera vista cuando cada parámetro de informe tiene un valor predeterminado.|  
|Avanzado|Establecer el atributo de definición de informe `UsedInQuery`, un valor que indica si este parámetro afecta directa o indirectamente a los datos de un informe.<br /><br /> **Determinar automáticamente cuándo actualizar**<br /> Elija esta opción si desea que el procesador de informes determine una configuración para este valor. El valor es `True` si el procesador de informes detecta una consulta de conjunto de datos con una referencia directa o indirecta a este parámetro o si el informe tiene subinformes.<br /><br /> **Actualizar siempre**<br /> Elija esta opción cuando el parámetro de informes se utilice directa o indirectamente en una consulta de conjunto de datos o una expresión de parámetro. Esta opción establece `UsedInQuery` en True.<br /><br /> **No actualizar nunca**<br /> Elija esta opción cuando el parámetro de informes no se utilice directa o indirectamente en una consulta de conjunto de datos o una expresión de parámetro. Esta opción establece `UsedInQuery` en False.<br /><br /> ** \* \* PRECAUCIÓN \* use \* ** no **Actualizar nunca** con precaución. En el servidor de informes, `UsedInQuery` se utiliza para ayudar a controlar las opciones de memoria caché para los datos de los informes y para los informes representados, y opciones de parámetros para instantáneas de informe. Si establece **No actualizar nunca** de manera incorrecta podría provocar que los datos de informes o los informes incorrectos se almacenen en memoria caché o provocar que una instantánea de informe tenga datos incoherentes. Para más información, vea [Report Definition Language &#40;SSRS&#41;](../reports/report-definition-language-ssrs.md).|  
  
##  <a name="dataset-query"></a><a name="bkmk_Dataset_Parameters"></a> Consultas de conjunto de datos  
 Para filtrar los datos en la consulta de conjunto de datos, puede incluir una cláusula de restricción que limite los datos recuperados; para ello, deberá especificar los valores que se van a incluir o excluir del conjunto de resultados.  
  
 Use el diseñador de consultas para el origen de datos para generar una consulta con parámetros.  
  
-   En las consultas de [!INCLUDE[tsql](../../includes/tsql-md.md)] , cada origen de datos es compatible con una sintaxis para parámetros diferente. La compatibilidad varía para los parámetros que se identifican en la consulta por su posición o los que se identifican por su nombre. Para obtener más información, vea los temas sobre tipos de orígenes de datos externos específicos en [Agregar datos a un informe &#40;generador de informes y SSRS&#41;](../report-data/report-datasets-ssrs.md). En el diseñador de consultas relacional, debe seleccionar la opción de parámetro de un filtro para crear una consulta parametrizada. Para obtener más información, vea [Interfaz de usuario del Diseñador de consultas relacionales &#40;Generador de informes&#41;](../report-data/relational-query-designer-user-interface-report-builder.md).  
  
-   En las consultas basadas en un origen de datos multidimensionales, como Microsoft SQL Server Analysis Services, SAP NetWeaver BI o Hyperion Essbase, podrá especificar si desea crear un parámetro en función del filtro que haya especificado en el diseñador de consultas. Para más información, vea el tema sobre el Diseñador de consultas en [Diseñadores de consultas &#40;Generador de informes&#41;](../query-designers-report-builder.md) que se corresponda con la extensión de datos.  
  
##  <a name="parameter-management-for-a-published-report"></a><a name="bkmk_Manage_Parameters"></a> Administración de parámetros para un informe publicado  
 Cuando diseñe un informe, los parámetros de informe se guardarán en la definición de informe. Cuando diseñe un informe, los parámetros de informe se guardarán y administrarán por separado, no con la definición de informe.  
  
 En un informe publicado, puede usar lo siguiente:  
  
-   **Propiedades de los parámetros de informe.** Cambiar directamente los valores de los parámetros de informe en el servidor de informes independientemente de la definición de informe.  
  
-   **Informes almacenados en caché.** Para crear un plan de memoria caché para un informe, cada parámetro debe tener un valor predeterminado. Para más información, vea [Informes almacenados en caché &#40;SSRS&#41;](../report-server/caching-reports-ssrs.md).  
  
-   **Conjuntos de datos compartidos en caché.** Para crear un plan de memoria caché para un conjunto de datos compartido, cada parámetro debe tener un valor predeterminado. Para más información, vea [Informes almacenados en caché &#40;SSRS&#41;](../report-server/caching-reports-ssrs.md).  
  
-   **Informes vinculados.** Puede crear informes vinculados con valores de parámetro preestablecidos para filtrar datos para los distintos destinatarios. Para obtener más información, consulte [Crear un informe vinculado](../reports/create-a-linked-report.md).  
  
-   **Suscripciones a informes.** Puede especificar valores de parámetro para filtrar datos y entregar informes mediante suscripciones. Para obtener más información, vea [Suscripciones y entrega &#40;Reporting Services&#41;](../subscriptions/subscriptions-and-delivery-reporting-services.md).  
  
-   **Acceso URL.** Puede especificar valores de parámetro en una dirección URL a un informe. También puede ejecutar informes y especificar valores de parámetro mediante el acceso desde una dirección URL. Para más información, vea [Acceso URL &#40;SSRS&#41;](../url-access-ssrs.md).  
  
 Las propiedades de los parámetros para un informe publicado suelen conservarse al volver a publicar la definición del informe. Si se vuelve a publicar la definición del informe como el mismo informe y no se modifican los nombres de los parámetros ni los tipos de datos, se conserva la configuración de las propiedades. Si se agregan o eliminan parámetros de la definición del informe, o si se cambia el tipo de datos o el nombre de un parámetro existente, quizás resulte necesario cambiar las propiedades de los parámetros del informe publicado.  
  
 No todos los parámetros pueden modificarse siempre que se desea. Si un parámetro de informe obtiene un valor predeterminado de una consulta de conjunto de datos, ese valor no se podrá modificar para un informe publicado y tampoco en el servidor de informes. El valor que se utiliza en tiempo de ejecución se determina cuando se ejecuta la consulta o, en el caso de parámetros basados en una expresión, cuando se evalúa la expresión.  
  
 Las opciones de ejecución del informe pueden incidir en el modo en que se procesan los parámetros. Un informe que se ejecute como instantánea no puede utilizar parámetros obtenidos de una consulta excepto si la consulta incluye valores predeterminados para los parámetros.  
  
##  <a name="parameters-for-a-subscription"></a><a name="bkmk_Parameters_Subscription"></a> Parámetros de una suscripción  
 Puede definir una suscripción para un informe a petición o para una instantánea y especificar los valores de parámetro que se usarán durante el procesamiento de la suscripción.  
  
-   **Informe a petición.**  Para un informe a petición, puede especificar un valor de parámetro diferente que el valor publicado para cada parámetro indicado en el informe. Por ejemplo, supongamos que tiene un informe de llamadas de servicio que utiliza un parámetro *Período de tiempo* para devolver las solicitudes de atención al cliente para el día, la semana o el mes actual. Si el valor de parámetro predeterminado para el informe se establece en **hoy**, la suscripción puede usar un valor de parámetro diferente (como **semana** o **mes**) para producir un informe que contenga cifras semanales o mensuales.  
  
-   **Archivos.**  Para una instantánea, la suscripción debe usar los valores de parámetro definidos para la instantánea. La suscripción no puede reemplazar un valor de parámetro que se haya definido para una instantánea. Por ejemplo, supongamos que se va a suscribir a un informe de ventas para la región occidental que se ejecuta como instantánea de un informe, y la instantánea especifica **Occidental** como valor de parámetro regional. En este caso, si crea una suscripción a este informe, debe utilizar el valor de parámetro **Occidental** en la suscripción. Para proporcionar una indicación visual de que se omite el parámetro, los campos de parámetros de la página de suscripción se establecen en campos de solo lectura.  
  
     Las opciones de ejecución del informe pueden incidir en el modo en que se procesan los parámetros. Los informes con parámetros que se ejecuten como instantáneas de informes utilizan los valores de parámetro definidos para la instantánea de informes. Los valores de parámetro se definen en la página de propiedades de parámetros del informe. Un informe que se ejecute como instantánea no puede utilizar parámetros obtenidos de una consulta excepto si la consulta incluye valores predeterminados para los parámetros.  
  
     Si cambia un valor de parámetro en la instantánea de un informe después de que se haya definido la suscripción, el servidor de informes la desactiva. La desactivación de la suscripción indica que el informe se ha modificado. Para activarla, abra y guarde la suscripción.  
  
> [!NOTE]  
>  Las suscripciones controladas por datos pueden utilizar valores de parámetros que se obtienen a partir de un origen de datos de suscriptores. Para más información, vea [Usar un origen de datos externo para obtener información de los suscriptores &#40;suscripción controlada por datos&#41;](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md).  
  
 Para obtener más información, vea [Suscripciones y entrega &#40;Reporting Services&#41;](../subscriptions/subscriptions-and-delivery-reporting-services.md).  
  
##  <a name="parameters-and-securing-data"></a><a name="bkmk_Parameters_Security"></a> Parámetros y asegurar datos  
 Sea precavido cuando se distribuyan informes con parámetros que contengan información confidencial o delicada. Un usuario puede reemplazar fácilmente un parámetro de informe con un valor diferente y, sin pretenderlo, provocar la divulgación de la información.  
  
 Una alternativa segura al uso de parámetros para los datos de los empleados o el personal es seleccionar datos que se basen en expresiones que incluyan el campo **UserID** de la colección Users. La colección Users proporciona un método de obtener la identidad del usuario que ejecuta el informe y utiliza esa identidad para recuperar datos específicos de usuario.  
  
> [!IMPORTANT]  
>  En cualquier informe que incluya un parámetro de tipo `String`, asegúrese de utilizar una lista de valores disponibles (también conocida como lista de valores válidos) y de que los usuarios que ejecuten el informe solamente dispongan de los permisos necesarios para ver los datos del mismo. Cuando se define un parámetro de tipo `String`, el usuario ve un cuadro de texto que admite cualquier valor. Una lista de valores disponibles limita los valores que se pueden especificar. Si el parámetro de informe está asociado a un parámetro de conjunto de datos y no se utiliza una lista de valores disponibles, un usuario del informe podría escribir sintaxis SQL en el cuadro de texto y exponer el informe y el servidor a un ataque por inyección de código SQL. Si el usuario tiene permisos suficientes para ejecutar la nueva instrucción SQL, podría provocar resultados no deseados en el servidor.  
>   
>  Si un parámetro de informe no está asociado a un parámetro de conjunto de datos y los valores de parámetro están incluidos en el informe, un usuario del informe podría escribir sintaxis de expresiones o una dirección URL en el valor de parámetro y representar el informe en Excel o HTML. Si, posteriormente, otro usuario visualiza el informe y hace clic en el contenido del parámetro representado, el usuario podría ejecutar accidentalmente el script o el vínculo malintencionados.  
>   
>  Para reducir el riesgo de ejecución accidental de scripts malintencionados, abra los informes representados exclusivamente desde orígenes de confianza. Para obtener más información sobre cómo proteger informes, vea [Proteger informes y recursos](../security/secure-reports-and-resources.md).  
  
##  <a name="how-to-topics"></a><a name="bkmk_How_To_Topics"></a>Temas de procedimientos  
 En esta sección se enumeran procedimientos que muestran, paso a paso, cómo trabajar con los parámetros y los filtros.  
  
-   [Agregar, cambiar o eliminar parámetros de informe &#40;Generador de informes y SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md)  
  
-   [Agregar, cambiar o eliminar los valores disponibles para un parámetro de informe &#40;Generador de informes y SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md)  
  
-   [Agregar, cambiar o eliminar valores predeterminados para un parámetro de informe &#40;Generador de informes y SSRS&#41;](add-change-or-delete-default-values-for-a-report-parameter.md)  
  
-   [Cambiar el orden de un parámetro de informe &#40;Generador de informes y SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)  
  
-   [Agregar parámetros en cascada a un informe &#40;Generador de informes y SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)  
  
-   [Agregar un filtro a un conjunto de datos &#40;Generador de informes y SSRS&#41;](../report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
-   [Agregar un subinforme y parámetros &#40;Generador de informes y SSRS&#41;](add-a-subreport-and-parameters-report-builder-and-ssrs.md)  
  
-   [Informe de SSRS para procedimiento almacenado parametrizado](https://www.c-sharpcorner.com/UploadFile/7d3362/ssrs-report-for-parameterize-stored-procedure/)  
  
## <a name="did-this-article-help-you-were-listening"></a>¿Le ayudó este artículo? Estamos escuchando  
 ¿Qué información está buscando? ¿La encontró? Escuchamos sus comentarios para mejorar el contenido. Envíe sus comentarios a[sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Report%20Parameters%20page)  
  
##  <a name="related-content"></a><a name="bkmk_Related_Topics"></a> Contenido relacionado  
 [Configurar parámetros de informe de SSRS (cuestionario)](https://www.trenovision.com/quiz/sql-server-reporting-services-ssrs-quiz/)  
  
 [Tutorial: Agregar un parámetro a un informe &#40;Generador de informes&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md)  
  
 [Desvelar los misterios de InvalidReportParameterException en Reporting Services](https://go.microsoft.com/fwlink/p/?LinkId=393118)  
  
 [Ejemplos de informes (Generador de informes y SSRS)](https://go.microsoft.com/fwlink/?LinkId=198283)  
  
 [Usar expresiones en informes &#40;Generador de informes y SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)  
  
 [Expresiones &#40;Generador de informes y SSRS&#41;](expressions-report-builder-and-ssrs.md)  
  
 [Filtrar, agrupar y ordenar datos &#40;Generador de informes y SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
 [Seguridad &#40;Generador de informes&#41;](../report-builder/security-report-builder.md)  
  
 [Ordenación interactiva, mapas de documento y vínculos &#40;Generador de informes y SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md)  
  
 [Obtención de detalles, informes detallados, subinformes y regiones de datos anidadas &#40;Generador de informes y SSRS&#41;](drillthrough-drilldown-subreports-and-nested-data-regions.md)  
  
  
