---
title: Tipo de conexión de Hyperion Essbase (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 108a00b6-799f-4066-b796-da59e95c09fd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 90292b91f74eac90ff5d1199e929c0685142d424
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663922"
---
# <a name="hyperion-essbase-connection-type-ssrs"></a>Tipo de conexión de Hyperion Essbase (SSRS)
  Para incluir los datos de un origen de datos externo de [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] en su informe, deberá tener un conjunto de datos basado en un origen de datos de informe de tipo [!INCLUDE[extEssbase](../../includes/extessbase-md.md)]. Este tipo de origen de datos integrado se basa en la extensión de datos de [!INCLUDE[extEssbase](../../includes/extessbase-md.md)], que permite recuperar los datos multidimensionales de un origen de datos externo de [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] .  
  
 Utilice la información de este tema para crear un origen de datos. Para obtener instrucciones paso a paso, vea [Agregar y comprobar una conexión de datos o un origen de datos &#40;generador de informes y SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="connection-string"></a><a name="Connection"></a> Cadena de conexión  
 En el siguiente ejemplo de cadena de conexión se especifica un origen de datos de [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] en un servidor que usa el puerto 13080 y XML para [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (XMLA) en Internet con el protocolo SOAP y una conexión a un catálogo de ejemplo:  
  
```  
Data Source=http://localhost:13080/aps/XMLA; Initial Catalog=Sample  
```  
  
 Para más información sobre ejemplos de cadenas de conexión, vea [Conexiones de datos, orígenes de datos y cadenas de conexión en el Generador de informes](../data-connections-data-sources-and-connection-strings-in-report-builder.md).  
  
  
##  <a name="credentials"></a><a name="Credentials"></a> Credenciales  
 Se necesitan credenciales para ejecutar consultas y obtener una vista previa del informe localmente y desde el servidor de informes.  
  
 Después de publicar el informe, es posible que necesite cambiar las credenciales para el origen de datos de tal forma que, cuando el informe se ejecute en el servidor de informes, los permisos para recuperar los datos sean válidos.  
  
 Para obtener más información, vea [conexiones de datos, orígenes de datos y cadenas de conexión en Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) o [Especifique las credenciales en generador de informes](../specify-credentials-in-report-builder.md).  
  
  
##  <a name="queries"></a><a name="Query"></a> Consultas  
 Puede especificar una consulta de varias maneras:  
  
-   Generar una consulta interactivamente. Utilice el diseñador gráfico de consultas en modo de diseño o de consulta para examinar los metadatos del origen de datos externo y generar una consulta con la sintaxis de Expresiones multidimensionales (MDX).  
  
    -   **Vista de diseño** : para crear una consulta MDX, se pueden arrastrar dimensiones, miembros, propiedades de miembros, medidas y KPI desde el explorador de metadatos hasta el panel **Datos** . Para definir más campos de conjunto de datos, se pueden arrastrar miembros calculados desde el panel Miembros calculados hasta el panel de datos.  
  
    -   **Vista de consulta** : para crear una consulta MDX, se pueden arrastrar dimensiones, miembros, propiedades de miembros, medidas y KPI desde el explorador de metadatos hasta el panel Consulta. El texto MDX se puede editar directamente en el panel de consulta. Para definir más campos de conjunto de datos, se pueden arrastrar miembros calculados desde el panel Miembros calculados hasta el panel de consulta.  
  
     Para más información, vea [Interfaz de usuario del Diseñador de consultas de Hyperion Essbase &#40;Generador de informes&#41;](../hyperion-essbase-query-designer-user-interface-report-builder.md).  
  
-   Importar una consulta MDX existente desde un informe. Utilice el botón **Importar consulta** para ir a un archivo .rdl e importar una consulta. Puede importar una consulta desde un informe que contenga un conjunto de datos incrustado que se base en un origen de datos de [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] . No se admite la importación directa de una consulta MDX desde un archivo .mdx.  
  
 Durante el diseño, ejecute la consulta para ver un conjunto de resultados. Después de crear la consulta, vea la colección de campos del conjunto de datos generada a partir de los metadatos en el panel Datos de informe. Cuando el informe se ejecuta, los datos reales se devuelven desde el origen de datos externo.  
  
 La extensión de procesamiento de datos de [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] admite propiedades de campo de conjunto de datos extendidas. Éstos son valores disponibles del origen de datos externo, pero no aparecen en el panel Datos de informe. Para obtener más información, vea [Propiedades de campo extendidas](#Extended) más adelante en este tema.  
  
  
##  <a name="parameters"></a><a name="Parameters"></a> Parámetros  
 Para incluir parámetros de consulta, cree un filtro en el área de filtro del diseñador de consultas y marque el filtro como un parámetro. Para cada filtro, se crea automáticamente un conjunto de datos para proporcionar los valores disponibles. De forma predeterminada, estos conjuntos de datos no aparecen en el panel Datos de informe. Para obtener más información, vea [Mostrar conjuntos de datos ocultos para los valores de parámetro de datos multidimensionales &#40;Generador de informes y SSRS&#41;](show-hidden-datasets-for-parameter-values-multidimensional-data.md).  
  
 De forma predeterminada, cada parámetro de informe tiene el tipo de datos **Text**. Una vez creados los parámetros de informe, podría suceder que tenga que cambiar los valores predeterminados. Para más información, vea [Parámetros de informe &#40;Generador de informes y Diseñador de informes&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).  
  
  
##  <a name="extended-field-properties"></a><a name="Extended"></a> Propiedades de campo extendidas  
 La extensión de procesamiento de datos de [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] admite propiedades de campo extendidas. Las propiedades de campo extendidas son propiedades (además de `Value` e `IsMissing`) que la extensión de procesamiento de datos define para un campo de conjunto de datos. Las propiedades extendidas incluyen propiedades predefinidas y propiedades personalizadas. Las propiedades predefinidas son propiedades comunes para varios orígenes de datos. Las propiedades personalizadas son únicas para cada origen de datos.  
  
 Las propiedades de campo extendidas no aparecen en el panel Datos de informe como elementos que se puedan arrastrar al diseño del informe. En su lugar, se arrastra al informe el campo primario de la propiedad y, después, se cambia la propiedad predeterminada de `Value` a la propiedad que se desee utilizar.  
  
 El nombre de la propiedad de campo extendida aparecerá en la información sobre herramientas al situar el puntero del mouse sobre un campo del panel Metadatos del diseñador de consultas. Para obtener más información acerca del diseñador de consultas que se puede usar para explorar los datos subyacentes, vea [Hyperion Essbase Query Designer User Interface](hyperion-essbase-query-designer-user-interface.md).  
  
> [!NOTE]  
>  Solo existirán valores para las propiedades de campo extendidas si se incluyen en la expresión MDX y si el origen de datos ofrece estos valores cuando el informe se ejecuta y recupera los datos para sus conjuntos de datos. En ese caso, podrá hacer referencia a esos valores de la propiedad `Field` desde cualquier expresión mediante la sintaxis descrita en la sección siguiente. No obstante, dado que estos campos son específicos de este proveedor de datos y no son parte del lenguaje RDL (Report Definition Language), los cambios que se realicen en estos valores no se guardarán con la definición de informe.  
  
  
### <a name="predefined-field-properties"></a>Propiedades de campo predefinidas  
 Propiedades de campo predefinidas admitidas generalmente por varios proveedores de datos y que aparecen en la consulta MDX subyacente para un conjunto de datos de informe. Por ejemplo, la propiedad de dimensión MDX MEMBER_UNIQUE_NAME se asigna a la propiedad de campo de conjunto de datos de informe predefinida `UniqueName`. Para incluir el valor de nombre único en un cuadro de texto, use la expresión `=Fields!` *\<FieldName>* `.UniqueName` .  
  
 En la tabla siguiente, se ofrece una lista de las propiedades de campo predefinidas que se pueden usar para un origen de datos de [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] .  
  
|**Propiedad**|**Tipo**|**Descripción o valor esperado**|  
|------------------|--------------|---------------------------------------|  
|`Value`|`Object`|Especifica el valor de los datos del campo.<br /><br /> Para una propiedad de dimensión, se asigna a MEMBER_CAPTION. Para una medida, se asigna al valor de datos.|  
|`IsMissing`|`Boolean`|Indica si se ha encontrado el campo en el conjunto de datos resultante.|  
|`FormattedValue`|`String`|Devuelve un valor con formato para una cifra clave.<br /><br /> Se asigna desde FORMATTED_VALUE en la expresión MDX.|  
|`BackgroundColor`|`String`|Devuelve el color de fondo del campo, definido en la base de datos.<br /><br /> Se asigna desde BACK_COLOR en la expresión MDX.|  
|`Color`|`String`|Devuelve el color de primer plano del elemento, definido en la base de datos.<br /><br /> Se asigna desde FORE_COLOR en la expresión MDX.|  
|`UniqueName`|`String`|Devuelve el nombre completo de un nivel.<br /><br /> Se asigna desde MEMBER_UNIQUE_NAME en la expresión MDX.|  
  
 Para más información sobre el uso de campos y propiedades de campo en una expresión, vea [Colecciones integradas en expresiones &#40;Generador de informes y SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).  
  
  
### <a name="custom-properties"></a>Propiedades personalizadas  
 Propiedades de campo personalizadas admitidas por un proveedor de datos y que aparecen en la consulta MDX subyacente para un conjunto de datos de informe, pero no aparecen en el panel de conjuntos de datos de informe como campos del conjunto de datos. Por ejemplo, **Long Names** es una propiedad de miembro definida para un nivel de dimensión. Para incluir el valor en un cuadro de texto, use la expresión `=Fields!` *\<FieldName>* `("Long Names")` . En los nombres de campos de la expresión se distinguen mayúsculas de minúsculas.  
  
 Para hacer referencia a propiedades extendidas personalizadas en una expresión, se utiliza la sintaxis siguiente:  
  
-   *Ámbitos! FieldName ("PropertyName")*  
  
 En la tabla siguiente, se muestra la propiedad de campo personalizada que se puede usar para un origen de datos de [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] .  
  
|**Property**|**Type**|**Descripción o valor esperado**|  
|------------------|--------------|---------------------------------------|  
|`FORMAT_STRING`|`String`|Se define en una medida y es `FormattedValue`, disponible como un tipo String.|  
  
  
##  <a name="remarks"></a><a name="Remarks"></a> Comentarios  
 Este proveedor de datos no admite todos los modos de entrega de informes. No se admite la entrega de informes a través de suscripciones controladas por datos para esta extensión de procesamiento de datos. Para más información, vea [Usar un origen de datos externo para obtener información de los suscriptores &#40;suscripción controlada por datos&#41;](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md) en la documentación de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en Libros en pantalla[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [ de ](https://go.microsoft.com/fwlink/?linkid=121312).  
  
 Para obtener más información, vea [Using SQL Server 2005 Reporting Services with Hyperion Essbase](https://go.microsoft.com/fwlink/?LinkId=81970).  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a>Temas de procedimientos  
 Esta sección contiene instrucciones paso a paso para trabajar con conexiones de datos, orígenes de datos y conjuntos de datos.  
  
 [Agregar y comprobar una conexión de datos o un origen de datos &#40;Generador de informes y SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [Crear un conjunto de datos compartido o un conjunto de datos incrustado &#40;Generador de informes y SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [Agregar un filtro a un conjunto de datos &#40;Generador de informes y SSRS&#41;](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
##  <a name="related-sections"></a><a name="Related"></a> Secciones relacionadas  
 Estas secciones de la documentación proporcionan información conceptual detallada sobre los datos de informe, así como información de procedimientos acerca de cómo definir, personalizar y usar las partes de un informe que están relacionadas con datos.  
  
 [Agregar datos a un informe &#40;Generador de informes y SSRS&#41;](report-datasets-ssrs.md)  
 Proporciona información general sobre cómo obtener acceso a los datos del informe.  
  
 [Conexiones de datos, orígenes de datos y cadenas de conexión en el Generador de informes](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 Proporciona información sobre las conexiones de datos y los orígenes de datos.  
  
 [Conjuntos de datos incrustados y compartidos de informe &#40;Generador de informes y SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 Proporciona información sobre conjuntos de datos compartidos e incrustados.  
  
 [Colección Campos del conjunto de datos &#40;Generador de informes y SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)  
 Proporciona información sobre la colección de campos que genera la consulta del conjunto de datos.  
  
 [Orígenes de datos admitidos por Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) en la documentación relativa a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en los [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Libros en pantalla](https://go.microsoft.com/fwlink/?linkid=121312) de .  
 Proporciona información detallada sobre la compatibilidad de versiones y plataformas para cada extensión de datos.  
  
 [Using SQL Server 2005 Reporting Services with Hyperion Essbase](https://go.microsoft.com/fwlink/?LinkId=81970)  
 Proporciona información detallada sobre cómo trabajar con esta extensión de datos.  
  
  
## <a name="see-also"></a>Consulte también  
 [Parámetros de informe &#40;Generador de informes y Diseñador de informes&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [Filtrar, agrupar y ordenar datos &#40;Generador de informes y SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Expresiones &#40;Generador de informes y SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
