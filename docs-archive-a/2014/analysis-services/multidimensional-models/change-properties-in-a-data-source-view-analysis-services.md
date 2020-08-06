---
title: Cambiar las propiedades de una vista del origen de datos (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- friendly names [Analysis Services]
- names [Analysis Services], data source views
- viewing tables
- displaying tables
- data source views [Analysis Services], tables
- tables [Analysis Services], data source views
ms.assetid: 4ccdabea-9c4d-460d-ba78-d23068143696
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5637186d079d08590f9f6080825f1376c94c20b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748380"
---
# <a name="change-properties-in-a-data-source-view-analysis-services"></a>Cambiar las propiedades de una vista del origen de datos (Analysis Services)
  Una vez que haya definido una vista del origen de datos mediante el Asistente para vistas del origen de datos y le haya agregado tablas, vistas, cálculos con nombre y consultas con nombre, podría interesarle cambiar las propiedades relativas a:  
  
-   Criterios de coincidencia de vistas del origen de datos  
  
-   Opciones avanzadas de vistas del origen de datos  
  
-   Nombres de objetos  
  
-   Metadatos de objetos  
  
 También puede ver los metadatos de objetos recuperados del origen de datos y que no se pueden modificar.  
  
## <a name="viewing-or-changing-data-source-view-properties"></a>Ver o cambiar las propiedades de las vistas del origen de datos  
 Las propiedades de las vistas del origen de datos, excepto una descripción de la vista del origen de datos, son establecidas por el Asistente para vistas del origen de datos la primera vez que se define la vista del origen de datos. En la siguiente tabla se muestran y describen las propiedades de una vista del origen de datos.  
  
> [!NOTE]  
>  El panel de propiedades muestra las propiedades del archivo .dsv y del objeto DSV. Para ver las propiedades del objeto, haga doble clic en él en el Explorador de soluciones. El panel de propiedades se actualizará para reflejar las propiedades que aparecen en la tabla siguiente.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|Origen de datos|Especifica el origen de datos de la vista del origen de datos cuyas propiedades está viendo.|  
|Descripción|Especifica la descripción de la vista del origen de datos.|  
|Nombre|Especifica el nombre de la vista del origen de datos que aparece en el Explorador de soluciones o la base de datos de Analysis Services. Puede cambiar el nombre de la vista del origen de datos aquí o en el Explorador de soluciones.|  
|NameMatchingCriteria|Criterios de coincidencia de nombres del origen de datos. No hay valor predeterminado si el Asistente para vistas del origen de datos detecta relaciones entre claves principales y claves externas. Independientemente de que el Asistente para vistas del origen de datos haya establecido esta propiedad o no, aquí puede especificar un valor. Si hay relaciones de base de datos y especifica criterios de coincidencia de nombres, se usarán ambas cosas para deducir relaciones entre las tablas existentes y las que se agreguen.|  
|RetrieveRelationships|Especifica si se recuperan relaciones de la base de datos. El valor predeterminado es True.|  
|SchemaRestriction|Especifica las restricciones, si las hay, de los esquemas recuperados de un origen de datos. De manera predeterminada, no hay restricciones de esquema.|  
  
## <a name="viewing-or-changing-datatable-properties"></a>Ver o cambiar las propiedades DataTable  
 Las propiedades**DataTable** son las propiedades de tablas, vistas y consultas con nombre de una vista del origen de datos. Estas propiedades se establecen cuando se agrega cualquiera de estos objetos a la vista del origen de datos. En la siguiente tabla se muestran y describen las propiedades de los objetos **DataTable** de una vista del origen de datos.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|AllowChangesDuringGeneration|Especifica si el Asistente para generar esquemas tiene permiso para sobrescribir una tabla de la vista del origen de datos cuando se vuelve a generar. Está propiedad solo está presente en las tablas generadas inicialmente por el Asistente para generar esquemas. Para obtener más información, vea [Descripción de la generación incremental](understanding-incremental-generation.md).|  
|DataSource|Especifica el origen de datos para el objeto. Esta propiedad no se puede editar.|  
|Descripción|Especifica la descripción de la tabla, vista o consulta con nombre. Si la tabla o vista de la base de datos subyacente tenía una descripción almacenada como propiedad extendida, se muestra este valor. Esta propiedad se puede editar.|  
|FriendlyName|Especifica un nombre para la tabla o vista que es significativo para los usuarios o tiene relación con el asunto. De manera predeterminada, la propiedad **FriendlyName** de una tabla o vista es igual que la propiedad **Name** de la misma. La propiedad **FriendlyName** es utilizada por los objetos de minería de datos y OLAP al definir nombres de objeto basados en tablas o vistas. Esta propiedad se puede editar.|  
|Nombre|Especifica el nombre de la tabla o vista subyacente, o el nombre de la consulta con nombre. La propiedad **Name** es utilizada por los objetos de minería de datos y OLAP al definir nombres de objeto basados en consultas con nombre. Esta propiedad solo se puede editar para las consultas con nombre.|  
|QueryDefinition|Especifica la definición de la consulta con nombre. Esta propiedad solo se puede aplicar a las consultas con nombre y no se puede editar directamente. Para editar esta propiedad, se edita la propia consulta con nombre.|  
|Schema|Especifica el esquema de la base de datos aplicable a la tabla, vista o consulta con nombre. Esta propiedad no se puede editar.|  
|TableType|Especifica el tipo de tabla de la tabla, vista o consulta con nombre. Esta propiedad no se puede editar.|  
  
## <a name="viewing-or-changing-datacolumn-properties"></a>Ver o cambiar las propiedades DataColumn  
 Las propiedades**DataColumn** son las propiedades de las columnas de las tablas, vistas y consultas con nombre de una vista del origen de datos. Estas propiedades se establecen cuando se agrega cualquiera de estos objetos a la vista del origen de datos, ya sea desde la tabla o vista subyacente, desde una consulta con nombre o tal como las define un cálculo con nombre. En la siguiente tabla se muestran y describen las propiedades de los objetos **DataColumn** de una vista del origen de datos.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|AllowNull|Especifica la propiedad de nulabilidad de la columna en función de la columna de la tabla subyacente, el valor o la consulta con nombre. Esta propiedad no se puede editar.|  
|DataType|Especifica el tipo de datos de la columna en función de la columna de la tabla subyacente, el valor o la consulta con nombre. Esta propiedad no se puede editar directamente. Sin embargo, si tiene que cambiar el tipo de datos de una columna de una tabla o vista, reemplace la tabla por una consulta con nombre que convierta la columna al tipo de datos deseado.|  
|DateTimeMode|Especifica el formato de serialización de fechas para las columnas **DateTime** . El valor predeterminado es **UnspecifiedLocal**. Esta propiedad se puede editar.|  
|Descripción|Especifica la descripción de la columna. Si la columna de la base de datos subyacente tenía una descripción almacenada como propiedad extendida, se muestra este valor. Esta propiedad se puede editar.|  
|FriendlyName|Especifica el nombre para una columna de una tabla o vista que es significativo para los usuarios o tiene relación con el asunto. De manera predeterminada, la propiedad **FriendlyName** de una columna de una tabla o vista es igual que la propiedad **Name** de la columna. La propiedad **FriendlyName** es utilizada por los objetos de minería de datos y OLAP al definir atributos basados en columnas de tablas o vistas. Esta propiedad se puede editar.|  
|Length|Especifica la longitud máxima de la columna, en función de los datos de la columna de la tabla o vista subyacente.|  
|Nombre|Especifica el nombre de la columna subyacente, o el nombre del cálculo con nombre. La propiedad **Name** la usan los objetos de minería de datos y OLAP al definir atributos basados en cálculos con nombre. Esta propiedad solo se puede editar para los cálculos con nombre.|  
  
## <a name="see-also"></a>Consulte también  
 [Vistas del origen de datos en modelos multidimensionales](data-source-views-in-multidimensional-models.md)   
 [Trabajar con diagramas en el Diseñador de vistas del origen de datos &#40;Analysis Services&#41;](work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  
