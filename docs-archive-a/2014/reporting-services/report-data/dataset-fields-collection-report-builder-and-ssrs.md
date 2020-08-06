---
title: Colección de campos de conjunto de datos (Generador de informes y SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b3884576-1f7e-4d40-bb7d-168312333bb3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7850cb575ff50848c97fd4591835517853a0e2cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744508"
---
# <a name="dataset-fields-collection-report-builder-and-ssrs"></a>Colección Campos del conjunto de datos (Generador de informes y SSRS)
  Los campos de conjunto de datos representan los datos de una conexión de datos. Un campo puede representar datos numéricos o no numéricos. En los ejemplos se incluyen cantidades de ventas, ventas totales, nombres de cliente, identificadores de base de datos, direcciones URL, imágenes, datos espaciales y direcciones de correo electrónico. En la superficie de diseño, los campos aparecen como expresiones en los elementos de informe como los cuadros de texto, tablas y gráficos.  
  
 Un informe tiene tres tipos de campos y los muestra en el panel Datos de informe: campos de conjunto de datos, campos calculados del conjunto de datos y campos integrados.  
  
-   **Campos de conjunto de datos.** Los metadatos que representa la colección de campos que se devolverán cuando la consulta del conjunto de datos se ejecuta en el origen de datos.  
  
-   **Campos calculados de un conjunto de datos.** Campos adicionales que crea para el conjunto de datos. Cada campo calculado se crea evaluando una expresión que se define.  
  
-   **Campos integrados.** Metadatos que representan una colección de los campos que ofrece el Generador de informes y que proporcionan información como el nombre del informe o la hora en que se procesó. Para obtener más información, vea [Referencias a campos globales y de usuario integrados &#40;Generador de informes y SSRS&#41;](../report-design/built-in-collections-built-in-globals-and-users-references-report-builder.md).  
  
 Los nombres del campo de conjunto de datos se guardan como parte de la definición del conjunto de datos de informe. Para más información, vea [Conjuntos de datos incrustados y compartidos de informe &#40;Generador de informes y SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="dataset-fields-and-queries"></a><a name="Fields"></a> Campos y consultas de conjunto de datos  
 Los campos de los conjuntos de datos se especifican mediante un comando de consulta de conjunto de datos y mediante los campos calculados que se definan. La colección de campos que se ven en un informe depende del tipo de conjunto de datos que tenga:  
  
-   **Conjunto de datos compartidos.** La colección de campos es la lista de campos de la consulta en la definición del conjunto de datos compartido en el momento en que lo agregó directamente a un informe, o cuando agregó un elemento de informe que lo incluía. La colección de campos local no cambia cuando la definición del conjunto de datos compartida cambia en el servidor de informes. Debe actualizar la lista del conjunto de datos compartido local para actualizar la colección de campos local.  
  
-   **Conjunto de datos incrustado.** La colección de campos es la lista de campos que se devuelve al ejecutar la consulta actual con el origen de datos.  
  
 Para obtener más información, vea [Agregar, editar y actualizar campos en el panel Datos de informe &#40;Generador de informes y SSRS&#41;](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md).  
  

  
### <a name="calculated-fields"></a>Campos calculados  
 Un campo calculado se especifica manualmente creando una expresión. Los campos calculados se pueden usar para crear valores nuevos que no existen en el origen de datos. Por ejemplo, un campo calculado puede representar un valor nuevo, un criterio de ordenación personalizado para un conjunto de valores de campo, o un campo existente que se convierte a un tipo de datos diferente.  
  
 Los campos calculados son locales a un informe y no pueden guardarse como parte de un conjunto de datos compartido.  
  
 Para obtener más información, consulte [Agregar, editar y actualizar campos en el panel Datos de informe &#40;Generador de informes y SSRS&#41;](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md).  
  

  
### <a name="entities-and-entity-fields"></a>Entidades y campos de entidades  
 Si trabaja con un origen de datos de modelo de informe, especifique las entidades y sus campos como datos del informe. En el diseñador de consultas para un modelo de informe, puede explorar y seleccionar las entidades relacionadas interactivamente, además de elegir los campos que desea incluir en el conjunto de datos de informe. Cuando termine de diseñar la consulta, puede ver la colección de identificadores de entidad y campos de entidad en el panel Datos de informe. Los identificadores de entidad se generan automáticamente con el modelo de informe y por lo general no se muestran para el usuario final.  
  
### <a name="using-extended-field-properties"></a>Usar propiedades de campo extendidas  
 Los orígenes de datos que admiten consultas multidimensionales, como [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], admiten las propiedades de campo en los campos. Las propiedades de campo aparecen en el conjunto de resultados para una consulta, pero no están visibles en el panel **Datos de informe** . Sí que están disponibles para usarlas en el informe. Para hacer referencia a una propiedad de un campo, arrastre el campo al informe y cambie la propiedad predeterminada `Value` por el nombre de campo de la propiedad que desee. Por ejemplo, en un cubo de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , puede definir los formatos para los valores de las celdas del cubo. El valor con formato está disponible mediante la propiedad de campo `FormattedValue`. Para usar directamente el valor en lugar de usar un valor y establecer la propiedad de formato del cuadro de texto, arrastre el campo al cuadro de texto y cambie la expresión predeterminada `=Fields!FieldName.Value` a `=Fields!FieldName.FormattedValue`.  
  
> [!NOTE]  
>  No todas las propiedades `Field` pueden utilizarse para todos los orígenes de datos. Las propiedades `Value` y `IsMissing` se definen para todos los orígenes de datos. Otras propiedades predefinidas (como `Key`, `UniqueName` y `ParentUniqueName` para orígenes de datos multidimensionales) solo se admiten si el origen de datos las proporciona. Algunos proveedores de datos admiten las propiedades personalizadas. Para obtener más información, vea los temas sobre las propiedades de campo extendidas para cada tipo de origen de datos en [Conjuntos de datos incrustados y compartidos de informe &#40;Generador de informes y SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md). Por ejemplo, para un origen de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vea [Propiedades de campo extendidas para una base de datos de Analysis Services &#40;SSRS&#41;](extended-field-properties-for-an-analysis-services-database-ssrs.md).  
  

  
##  <a name="understanding-default-expressions-for-fields"></a><a name="Defaults"></a> Descripción de las expresiones predeterminadas para campos  
 Un cuadro de texto puede ser un elemento de informe de cuadro de texto en el cuerpo del informe o un cuadro de texto en una celda de una región de datos Tablix. Al vincular un campo con un cuadro de texto, la ubicación del cuadro de texto determina la expresión predeterminada para la referencia del campo. En el cuerpo del informe, una expresión de valor de cuadro de texto debe especificar un agregado y un conjunto de datos. Si solo existe un conjunto de datos en el informe, esta expresión predeterminada se crea automáticamente. Para un campo que representa un valor numérico, la función de agregado predeterminada es Sum. Para un campo que representa un valor no numérico, el agregado predeterminado es First.  
  
 En una región de datos Tablix, la expresión de campo predeterminada depende de la pertenencia a una fila o a un grupo del cuadro de texto al que se agrega el campo. La expresión de campo para el campo Sales, cuando se agrega a un cuadro de texto en la fila de detalles de una tabla, es `[Sales]`. Si agrega el mismo campo a un cuadro de texto de un encabezado de grupo, la expresión predeterminada es `(Sum[Sales])`, porque el encabezado de grupo muestra valores de resumen para el grupo, en lugar de valores detallados. Cuando se ejecuta el informe, el procesador de informes evalúa cada expresión y sustituye el resultado en el informe.  
  
 Para obtener más información sobre las expresiones, vea [Expresiones &#40;Generador de informes y SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md).  
  

  
##  <a name="field-data-types"></a><a name="DataTypes"></a> Tipos de datos de campo  
 Al crear un conjunto de datos, es posible que los tipos de datos de los campos del origen de datos no coincidan exactamente con los tipos de datos que se usan en un informe. Los tipos de datos pueden pasar por uno o dos niveles de asignación. La extensión de procesamiento de datos o el proveedor de datos pueden asignar los tipos de datos del origen de datos a tipos de datos de Common Language Runtime (CLR). Los tipos de datos devueltos por las extensiones de procesamiento de datos se asignan a un subconjunto de los tipos de datos de Common Language Runtime (CLR) de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
 En el origen de datos, los datos se almacenan en tipos de datos admitidos por el origen de datos. Por ejemplo, los datos de una base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deben ser de uno de los tipos de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] admitidos, como `nvarchar` o `datetime`. Cuando se recuperan datos del origen de datos, éstos pasan por la extensión de procesamiento de datos o por el proveedor de datos que está asociado al tipo de origen de datos. Dependiendo de la extensión de procesamiento de datos, los datos se pueden convertir desde los tipos de datos utilizados por el origen de datos en los tipos de datos admitidos por la extensión de procesamiento de datos. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] usa los tipos de datos admitidos por la versión de Common Language Runtime (CLR) instalada con [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. El proveedor de datos asigna cada columna del conjunto de resultados del tipo de datos nativo a un tipo de datos de CLR (Common Language Runtime) de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] .  
  
 En cada fase, los datos se representan mediante los tipos de datos descritos en la lista siguiente:  
  
-   **Origen de datos** : los tipos de datos admitidos por la versión del tipo de origen de datos con el que se está conectando.  
  
     Por ejemplo, para un origen de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], son típicos los tipos de datos `int`, `datetime` y `varchar`. Con [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], se han agregado los tipos de datos `date`, `time`, `datetimetz` y `datetime2`. Para obtener más información, vea [Tipos de datos (Transact-SQL)](https://go.microsoft.com/fwlink/?linkid=98362).  
  
-   **Proveedor de datos o extensión de procesamiento de datos** : los tipos de datos admitidos por la versión del proveedor de datos de la extensión de procesamiento de datos que se selecciona al conectar con el origen de datos. Los proveedores de datos basados en [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] usan tipos de datos admitidos por CLR. Para obtener más información sobre los tipos de datos de los proveedores de datos de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] , vea [Asignar tipos de datos en ADO.NET](https://go.microsoft.com/fwlink/?LinkId=112178) y [Trabajar con tipos base en .NET Framework](https://go.microsoft.com/fwlink/?LinkId=112177) en MSDN.  
  
     Por ejemplo, los tipos de datos típicos admitidos por [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] son `Int32` y `String`. La estructura `DateTime` admite las fechas y horas del calendario. En el Service Pack 1 de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 2.0 se introdujo la compatibilidad con la estructura `DateTimeOffset` para las fechas con un ajuste de zona horaria.  
  
    > [!NOTE]  
    >  El servidor de informes usa los proveedores de datos que se encuentran instalados y configurados en el mismo. En el modo de vista previa, los clientes de creación de informes usan las extensiones de procesamiento de datos instaladas y configuradas en el equipo cliente. Debe probar el informe en el entorno del cliente de informes y en el del servidor de informes.  
  
-   **Procesador de informes** : los tipos de datos se basan en la versión de CLR instalada cuando se instaló [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
     Por ejemplo, en la tabla siguiente, se muestran los tipos de datos que usa el procesador de informes para los nuevos tipos de fecha y hora introducidos en [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] :  
  
    |Tipo de datos de SQL|Tipo de datos de CLR|Descripción|  
    |-------------------|-------------------|-----------------|  
    |`Date`|`DateTime`|Solo fecha|  
    |`Time`|`TimeSpan`|Solo hora|  
    |`DateTimeTZ`|`DateTimeOffset`|Fecha y hora con ajuste de zona horaria|  
    |`DateTime2`|`DateTime`|Fecha y hora con fracciones de milisegundos|  
  
 Para obtener más información sobre los tipos de base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vea [Tipos de datos (motor de base de datos)](https://go.microsoft.com/fwlink/?linkid=98362) y [Tipos de datos y funciones de fecha y hora (Transact-SQL)](https://go.microsoft.com/fwlink/?linkid=98360).  
  
 Para obtener más información sobre cómo incluir referencias a un campo de conjunto de datos desde una expresión, vea [Tipos de datos en expresiones &#40;Generador de informes y SSRS&#41;](../report-design/data-types-in-expressions-report-builder-and-ssrs.md).  
  

  
##  <a name="detecting-missing-fields-at-run-time"></a><a name="MissingFields"></a> Detectar los campos que faltan en tiempo de ejecución  
 Cuando se procesa el informe, es posible que el conjunto de resultados para un conjunto de datos no contenga valores para todas las columnas especificadas porque éstas ya no existen en el origen de datos. Puede usar la propiedad de campo IsMissing para detectar si se devolvieron valores para un campo en tiempo de ejecución. Para obtener más información, vea [Referencias a la colección de campos de conjunto de datos &#40;Generador de informes y SSRS&#41;](../report-design/built-in-collections-dataset-fields-collection-references-report-builder.md).  
  

  
## <a name="see-also"></a>Consulte también  
 [Cuadro de diálogo Propiedades del conjunto de propiedades, campos &#40;Generador de informes&#41;](../dataset-properties-dialog-box-fields-report-builder.md)   
 [Elementos de informe y conjuntos de valores en Generador de informes](report-parts-and-datasets-in-report-builder.md)   
 [Conjuntos de datos incrustados y compartidos de informe &#40;Generador de informes y SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
