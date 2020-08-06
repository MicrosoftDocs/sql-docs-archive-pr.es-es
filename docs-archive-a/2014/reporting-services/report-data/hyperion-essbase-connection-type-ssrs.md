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
# <a name="hyperion-essbase-connection-type-ssrs"></a><span data-ttu-id="ed7c7-102">Tipo de conexión de Hyperion Essbase (SSRS)</span><span class="sxs-lookup"><span data-stu-id="ed7c7-102">Hyperion Essbase Connection Type (SSRS)</span></span>
  <span data-ttu-id="ed7c7-103">Para incluir los datos de un origen de datos externo de [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] en su informe, deberá tener un conjunto de datos basado en un origen de datos de informe de tipo [!INCLUDE[extEssbase](../../includes/extessbase-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ed7c7-103">To include data from a [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] external data source in your report, you must have a dataset that is based on a report data source of type [!INCLUDE[extEssbase](../../includes/extessbase-md.md)].</span></span> <span data-ttu-id="ed7c7-104">Este tipo de origen de datos integrado se basa en la extensión de datos de [!INCLUDE[extEssbase](../../includes/extessbase-md.md)], que permite recuperar los datos multidimensionales de un origen de datos externo de [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ed7c7-104">This built-in data source type is based on the data extension for [!INCLUDE[extEssbase](../../includes/extessbase-md.md)], which enables you to retrieve multidimensional data from a [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] external data source.</span></span>  
  
 <span data-ttu-id="ed7c7-105">Utilice la información de este tema para crear un origen de datos.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-105">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="ed7c7-106">Para obtener instrucciones paso a paso, vea [Agregar y comprobar una conexión de datos o un origen de datos &#40;generador de informes y SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span><span class="sxs-lookup"><span data-stu-id="ed7c7-106">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a> <span data-ttu-id="ed7c7-107">Cadena de conexión</span><span class="sxs-lookup"><span data-stu-id="ed7c7-107">Connection String</span></span>  
 <span data-ttu-id="ed7c7-108">En el siguiente ejemplo de cadena de conexión se especifica un origen de datos de [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] en un servidor que usa el puerto 13080 y XML para [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (XMLA) en Internet con el protocolo SOAP y una conexión a un catálogo de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="ed7c7-108">The following connection string example specifies a [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] data source on a server that uses port 13080 and XML for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (XMLA) over the Internet using SOAP, connecting to a sample catalog:</span></span>  
  
```  
Data Source=http://localhost:13080/aps/XMLA; Initial Catalog=Sample  
```  
  
 <span data-ttu-id="ed7c7-109">Para más información sobre ejemplos de cadenas de conexión, vea [Conexiones de datos, orígenes de datos y cadenas de conexión en el Generador de informes](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span><span class="sxs-lookup"><span data-stu-id="ed7c7-109">For more information about connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
  
##  <a name="credentials"></a><a name="Credentials"></a> <span data-ttu-id="ed7c7-110">Credenciales</span><span class="sxs-lookup"><span data-stu-id="ed7c7-110">Credentials</span></span>  
 <span data-ttu-id="ed7c7-111">Se necesitan credenciales para ejecutar consultas y obtener una vista previa del informe localmente y desde el servidor de informes.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-111">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="ed7c7-112">Después de publicar el informe, es posible que necesite cambiar las credenciales para el origen de datos de tal forma que, cuando el informe se ejecute en el servidor de informes, los permisos para recuperar los datos sean válidos.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-112">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="ed7c7-113">Para obtener más información, vea [conexiones de datos, orígenes de datos y cadenas de conexión en Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) o [Especifique las credenciales en generador de informes](../specify-credentials-in-report-builder.md).</span><span class="sxs-lookup"><span data-stu-id="ed7c7-113">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
  
##  <a name="queries"></a><a name="Query"></a> <span data-ttu-id="ed7c7-114">Consultas</span><span class="sxs-lookup"><span data-stu-id="ed7c7-114">Queries</span></span>  
 <span data-ttu-id="ed7c7-115">Puede especificar una consulta de varias maneras:</span><span class="sxs-lookup"><span data-stu-id="ed7c7-115">You can specify a query in the following ways:</span></span>  
  
-   <span data-ttu-id="ed7c7-116">Generar una consulta interactivamente.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-116">Build a query interactively.</span></span> <span data-ttu-id="ed7c7-117">Utilice el diseñador gráfico de consultas en modo de diseño o de consulta para examinar los metadatos del origen de datos externo y generar una consulta con la sintaxis de Expresiones multidimensionales (MDX).</span><span class="sxs-lookup"><span data-stu-id="ed7c7-117">Use the graphical query designer in Design or Query mode to browse the metadata on the external data source and generate a query in Multidimensional Expression (MDX) syntax.</span></span>  
  
    -   <span data-ttu-id="ed7c7-118">**Vista de diseño** : para crear una consulta MDX, se pueden arrastrar dimensiones, miembros, propiedades de miembros, medidas y KPI desde el explorador de metadatos hasta el panel **Datos** .</span><span class="sxs-lookup"><span data-stu-id="ed7c7-118">**Design View** Drag dimensions, members, member properties, measures, and KPIs from the metadata browser to the **Data** pane to build an MDX query.</span></span> <span data-ttu-id="ed7c7-119">Para definir más campos de conjunto de datos, se pueden arrastrar miembros calculados desde el panel Miembros calculados hasta el panel de datos.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-119">Drag calculated members from the CalculatedMembers pane to the Data pane to define additional dataset fields.</span></span>  
  
    -   <span data-ttu-id="ed7c7-120">**Vista de consulta** : para crear una consulta MDX, se pueden arrastrar dimensiones, miembros, propiedades de miembros, medidas y KPI desde el explorador de metadatos hasta el panel Consulta.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-120">**Query View** Drag dimensions, members, member properties, measures, and KPIs from the metadata browser to the Query pane to build an MDX query.</span></span> <span data-ttu-id="ed7c7-121">El texto MDX se puede editar directamente en el panel de consulta.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-121">You can edit MDX text directly in the Query pane.</span></span> <span data-ttu-id="ed7c7-122">Para definir más campos de conjunto de datos, se pueden arrastrar miembros calculados desde el panel Miembros calculados hasta el panel de consulta.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-122">Drag calculated members from the CalculatedMembers pane to the Query pane to define additional dataset fields.</span></span>  
  
     <span data-ttu-id="ed7c7-123">Para más información, vea [Interfaz de usuario del Diseñador de consultas de Hyperion Essbase &#40;Generador de informes&#41;](../hyperion-essbase-query-designer-user-interface-report-builder.md).</span><span class="sxs-lookup"><span data-stu-id="ed7c7-123">For more information, see [Hyperion Essbase Query Designer User Interface &#40;Report Builder&#41;](../hyperion-essbase-query-designer-user-interface-report-builder.md).</span></span>  
  
-   <span data-ttu-id="ed7c7-124">Importar una consulta MDX existente desde un informe.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-124">Import an existing MDX query from a report.</span></span> <span data-ttu-id="ed7c7-125">Utilice el botón **Importar consulta** para ir a un archivo .rdl e importar una consulta.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-125">Use the **Import** query button to browse to an .rdl file and import a query.</span></span> <span data-ttu-id="ed7c7-126">Puede importar una consulta desde un informe que contenga un conjunto de datos incrustado que se base en un origen de datos de [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ed7c7-126">You can import a query from a report that contains an embedded dataset that is based on a [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] data source.</span></span> <span data-ttu-id="ed7c7-127">No se admite la importación directa de una consulta MDX desde un archivo .mdx.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-127">Importing an MDX query directly from an .mdx file is not supported.</span></span>  
  
 <span data-ttu-id="ed7c7-128">Durante el diseño, ejecute la consulta para ver un conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-128">At design time, run the query to view a result set.</span></span> <span data-ttu-id="ed7c7-129">Después de crear la consulta, vea la colección de campos del conjunto de datos generada a partir de los metadatos en el panel Datos de informe.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-129">After you build the query, view the dataset field collection that is generated from the metadata in the Report Data pane.</span></span> <span data-ttu-id="ed7c7-130">Cuando el informe se ejecuta, los datos reales se devuelven desde el origen de datos externo.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-130">When the report runs, the actual data is returned from the external data source.</span></span>  
  
 <span data-ttu-id="ed7c7-131">La extensión de procesamiento de datos de [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] admite propiedades de campo de conjunto de datos extendidas.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-131">The [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] data processing extension supports extended dataset field properties.</span></span> <span data-ttu-id="ed7c7-132">Éstos son valores disponibles del origen de datos externo, pero no aparecen en el panel Datos de informe.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-132">These are values that are available from the external data source but that do not appear in the Report Data pane.</span></span> <span data-ttu-id="ed7c7-133">Para obtener más información, vea [Propiedades de campo extendidas](#Extended) más adelante en este tema.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-133">For more information, see [Extended Field Properties](#Extended) later in this topic.</span></span>  
  
  
##  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="ed7c7-134">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ed7c7-134">Parameters</span></span>  
 <span data-ttu-id="ed7c7-135">Para incluir parámetros de consulta, cree un filtro en el área de filtro del diseñador de consultas y marque el filtro como un parámetro.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-135">To include query parameters, create a filter in the filter area in the query designer, and mark the filter as a parameter.</span></span> <span data-ttu-id="ed7c7-136">Para cada filtro, se crea automáticamente un conjunto de datos para proporcionar los valores disponibles.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-136">For each filter, a dataset is automatically created to provide the available values.</span></span> <span data-ttu-id="ed7c7-137">De forma predeterminada, estos conjuntos de datos no aparecen en el panel Datos de informe.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-137">By default, these datasets do not appear in the Report Data pane.</span></span> <span data-ttu-id="ed7c7-138">Para obtener más información, vea [Mostrar conjuntos de datos ocultos para los valores de parámetro de datos multidimensionales &#40;Generador de informes y SSRS&#41;](show-hidden-datasets-for-parameter-values-multidimensional-data.md).</span><span class="sxs-lookup"><span data-stu-id="ed7c7-138">For more information, see [Show Hidden Datasets for Parameter Values for Multidimensional Data &#40;Report Builder and SSRS&#41;](show-hidden-datasets-for-parameter-values-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="ed7c7-139">De forma predeterminada, cada parámetro de informe tiene el tipo de datos **Text**.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-139">By default, each report parameter has data type **Text**.</span></span> <span data-ttu-id="ed7c7-140">Una vez creados los parámetros de informe, podría suceder que tenga que cambiar los valores predeterminados.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-140">After the report parameters are created, you might have to change default values.</span></span> <span data-ttu-id="ed7c7-141">Para más información, vea [Parámetros de informe &#40;Generador de informes y Diseñador de informes&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span><span class="sxs-lookup"><span data-stu-id="ed7c7-141">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  
  
##  <a name="extended-field-properties"></a><a name="Extended"></a> <span data-ttu-id="ed7c7-142">Propiedades de campo extendidas</span><span class="sxs-lookup"><span data-stu-id="ed7c7-142">Extended Field Properties</span></span>  
 <span data-ttu-id="ed7c7-143">La extensión de procesamiento de datos de [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] admite propiedades de campo extendidas.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-143">The [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] data processing extension supports extended field properties.</span></span> <span data-ttu-id="ed7c7-144">Las propiedades de campo extendidas son propiedades (además de `Value` e `IsMissing`) que la extensión de procesamiento de datos define para un campo de conjunto de datos.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-144">Extended field properties are properties in addition to `Value` and `IsMissing` that are defined for a dataset field by the data processing extension.</span></span> <span data-ttu-id="ed7c7-145">Las propiedades extendidas incluyen propiedades predefinidas y propiedades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-145">Extended properties include predefined properties and custom properties.</span></span> <span data-ttu-id="ed7c7-146">Las propiedades predefinidas son propiedades comunes para varios orígenes de datos.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-146">Predefined properties are properties common to multiple data sources.</span></span> <span data-ttu-id="ed7c7-147">Las propiedades personalizadas son únicas para cada origen de datos.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-147">Custom properties are unique to each data source.</span></span>  
  
 <span data-ttu-id="ed7c7-148">Las propiedades de campo extendidas no aparecen en el panel Datos de informe como elementos que se puedan arrastrar al diseño del informe.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-148">Extended field properties do not appear in the Report Data pane as items that you can drag onto your report layout.</span></span> <span data-ttu-id="ed7c7-149">En su lugar, se arrastra al informe el campo primario de la propiedad y, después, se cambia la propiedad predeterminada de `Value` a la propiedad que se desee utilizar.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-149">Instead, you drag the parent field of the property onto the report and then change the default property from `Value` to the property you want to use.</span></span>  
  
 <span data-ttu-id="ed7c7-150">El nombre de la propiedad de campo extendida aparecerá en la información sobre herramientas al situar el puntero del mouse sobre un campo del panel Metadatos del diseñador de consultas.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-150">The name for an extended field property appears in the ToolTip when you rest the mouse on a field in the Metadata pane in the query designer.</span></span> <span data-ttu-id="ed7c7-151">Para obtener más información acerca del diseñador de consultas que se puede usar para explorar los datos subyacentes, vea [Hyperion Essbase Query Designer User Interface](hyperion-essbase-query-designer-user-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ed7c7-151">For more information about the query designer you can use to explore the underlying data, see [Hyperion Essbase Query Designer User Interface](hyperion-essbase-query-designer-user-interface.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ed7c7-152">Solo existirán valores para las propiedades de campo extendidas si se incluyen en la expresión MDX y si el origen de datos ofrece estos valores cuando el informe se ejecuta y recupera los datos para sus conjuntos de datos.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-152">Values exist for extended field properties only if they are included in the MDX expression and the data source provides these values when your report runs and retrieves the data for its datasets.</span></span> <span data-ttu-id="ed7c7-153">En ese caso, podrá hacer referencia a esos valores de la propiedad `Field` desde cualquier expresión mediante la sintaxis descrita en la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-153">You can then refer to those `Field` property values from any expression using the syntax described in the following section.</span></span> <span data-ttu-id="ed7c7-154">No obstante, dado que estos campos son específicos de este proveedor de datos y no son parte del lenguaje RDL (Report Definition Language), los cambios que se realicen en estos valores no se guardarán con la definición de informe.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-154">However, because these fields are specific to this data provider and not part of the report definition language, changes that you make to these values are not saved with the report definition.</span></span>  
  
  
### <a name="predefined-field-properties"></a><span data-ttu-id="ed7c7-155">Propiedades de campo predefinidas</span><span class="sxs-lookup"><span data-stu-id="ed7c7-155">Predefined Field Properties</span></span>  
 <span data-ttu-id="ed7c7-156">Propiedades de campo predefinidas admitidas generalmente por varios proveedores de datos y que aparecen en la consulta MDX subyacente para un conjunto de datos de informe.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-156">Predefined field properties that are typically supported by multiple data providers and that appear in the underlying MDX query for a report dataset.</span></span> <span data-ttu-id="ed7c7-157">Por ejemplo, la propiedad de dimensión MDX MEMBER_UNIQUE_NAME se asigna a la propiedad de campo de conjunto de datos de informe predefinida `UniqueName`.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-157">For example, the MDX dimension property MEMBER_UNIQUE_NAME is mapped to the predefined report dataset field property `UniqueName`.</span></span> <span data-ttu-id="ed7c7-158">Para incluir el valor de nombre único en un cuadro de texto, use la expresión `=Fields!` *\<FieldName>* `.UniqueName` .</span><span class="sxs-lookup"><span data-stu-id="ed7c7-158">To include the unique name value in a text box, use the expression `=Fields!`*\<FieldName>*`.UniqueName`.</span></span>  
  
 <span data-ttu-id="ed7c7-159">En la tabla siguiente, se ofrece una lista de las propiedades de campo predefinidas que se pueden usar para un origen de datos de [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ed7c7-159">The following table provides a list of predefined field properties that you can use for a [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] data source.</span></span>  
  
|<span data-ttu-id="ed7c7-160">**Propiedad**</span><span class="sxs-lookup"><span data-stu-id="ed7c7-160">**Property**</span></span>|<span data-ttu-id="ed7c7-161">**Tipo**</span><span class="sxs-lookup"><span data-stu-id="ed7c7-161">**Type**</span></span>|<span data-ttu-id="ed7c7-162">**Descripción o valor esperado**</span><span class="sxs-lookup"><span data-stu-id="ed7c7-162">**Description or expected value**</span></span>|  
|------------------|--------------|---------------------------------------|  
|`Value`|`Object`|<span data-ttu-id="ed7c7-163">Especifica el valor de los datos del campo.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-163">Specifies the data value of the field.</span></span><br /><br /> <span data-ttu-id="ed7c7-164">Para una propiedad de dimensión, se asigna a MEMBER_CAPTION.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-164">For a dimension property, this is mapped to MEMBER_CAPTION.</span></span> <span data-ttu-id="ed7c7-165">Para una medida, se asigna al valor de datos.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-165">For a measure, this is mapped to the data value.</span></span>|  
|`IsMissing`|`Boolean`|<span data-ttu-id="ed7c7-166">Indica si se ha encontrado el campo en el conjunto de datos resultante.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-166">Indicates whether the field was found in the resulting data set.</span></span>|  
|`FormattedValue`|`String`|<span data-ttu-id="ed7c7-167">Devuelve un valor con formato para una cifra clave.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-167">Returns a formatted value for a key figure.</span></span><br /><br /> <span data-ttu-id="ed7c7-168">Se asigna desde FORMATTED_VALUE en la expresión MDX.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-168">Mapped from FORMATTED_VALUE in the MDX expression.</span></span>|  
|`BackgroundColor`|`String`|<span data-ttu-id="ed7c7-169">Devuelve el color de fondo del campo, definido en la base de datos.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-169">Returns the background color defined in the database for the field.</span></span><br /><br /> <span data-ttu-id="ed7c7-170">Se asigna desde BACK_COLOR en la expresión MDX.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-170">Mapped from BACK_COLOR in the MDX expression.</span></span>|  
|`Color`|`String`|<span data-ttu-id="ed7c7-171">Devuelve el color de primer plano del elemento, definido en la base de datos.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-171">Returns the foreground color defined in the database for the item.</span></span><br /><br /> <span data-ttu-id="ed7c7-172">Se asigna desde FORE_COLOR en la expresión MDX.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-172">Mapped from FORE_COLOR in the MDX expression.</span></span>|  
|`UniqueName`|`String`|<span data-ttu-id="ed7c7-173">Devuelve el nombre completo de un nivel.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-173">Returns the fully qualified name of a level.</span></span><br /><br /> <span data-ttu-id="ed7c7-174">Se asigna desde MEMBER_UNIQUE_NAME en la expresión MDX.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-174">Mapped from MEMBER_UNIQUE_NAME in the MDX expression.</span></span>|  
  
 <span data-ttu-id="ed7c7-175">Para más información sobre el uso de campos y propiedades de campo en una expresión, vea [Colecciones integradas en expresiones &#40;Generador de informes y SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span><span class="sxs-lookup"><span data-stu-id="ed7c7-175">For more information about how to use fields and field properties in an expression, see [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
  
### <a name="custom-properties"></a><span data-ttu-id="ed7c7-176">Propiedades personalizadas</span><span class="sxs-lookup"><span data-stu-id="ed7c7-176">Custom Properties</span></span>  
 <span data-ttu-id="ed7c7-177">Propiedades de campo personalizadas admitidas por un proveedor de datos y que aparecen en la consulta MDX subyacente para un conjunto de datos de informe, pero no aparecen en el panel de conjuntos de datos de informe como campos del conjunto de datos.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-177">Custom field properties that are supported by a data provider and that appear in the underlying MDX query for a report dataset, but do not appear in the report Datasets pane as fields under that dataset.</span></span> <span data-ttu-id="ed7c7-178">Por ejemplo, **Long Names** es una propiedad de miembro definida para un nivel de dimensión.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-178">For example, **Long Names** is a member property defined for a dimension level.</span></span> <span data-ttu-id="ed7c7-179">Para incluir el valor en un cuadro de texto, use la expresión `=Fields!` *\<FieldName>* `("Long Names")` .</span><span class="sxs-lookup"><span data-stu-id="ed7c7-179">To include the value in a text box, you use the expression `=Fields!`*\<FieldName>*`("Long Names")`.</span></span> <span data-ttu-id="ed7c7-180">En los nombres de campos de la expresión se distinguen mayúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-180">Field names in the expression are case-sensitive.</span></span>  
  
 <span data-ttu-id="ed7c7-181">Para hacer referencia a propiedades extendidas personalizadas en una expresión, se utiliza la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="ed7c7-181">Use the following syntax to refer to custom extended properties in an expression:</span></span>  
  
-   <span data-ttu-id="ed7c7-182">*Ámbitos! FieldName ("PropertyName")*</span><span class="sxs-lookup"><span data-stu-id="ed7c7-182">*Fields!FieldName("PropertyName")*</span></span>  
  
 <span data-ttu-id="ed7c7-183">En la tabla siguiente, se muestra la propiedad de campo personalizada que se puede usar para un origen de datos de [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ed7c7-183">The following table shows the custom field property that you can use for a [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] data source.</span></span>  
  
|<span data-ttu-id="ed7c7-184">**Property**</span><span class="sxs-lookup"><span data-stu-id="ed7c7-184">**Property**</span></span>|<span data-ttu-id="ed7c7-185">**Type**</span><span class="sxs-lookup"><span data-stu-id="ed7c7-185">**Type**</span></span>|<span data-ttu-id="ed7c7-186">**Descripción o valor esperado**</span><span class="sxs-lookup"><span data-stu-id="ed7c7-186">**Description or expected value**</span></span>|  
|------------------|--------------|---------------------------------------|  
|`FORMAT_STRING`|`String`|<span data-ttu-id="ed7c7-187">Se define en una medida y es `FormattedValue`, disponible como un tipo String.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-187">Defined on a measure, this is the `FormattedValue` available as a String type.</span></span>|  
  
  
##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="ed7c7-188">Comentarios</span><span class="sxs-lookup"><span data-stu-id="ed7c7-188">Remarks</span></span>  
 <span data-ttu-id="ed7c7-189">Este proveedor de datos no admite todos los modos de entrega de informes.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-189">Not all report delivery modes are supported by this data provider.</span></span> <span data-ttu-id="ed7c7-190">No se admite la entrega de informes a través de suscripciones controladas por datos para esta extensión de procesamiento de datos.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-190">Delivering reports through data-driven subscriptions is not supported for this data processing extension.</span></span> <span data-ttu-id="ed7c7-191">Para más información, vea [Usar un origen de datos externo para obtener información de los suscriptores &#40;suscripción controlada por datos&#41;](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md) en la documentación de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en Libros en pantalla[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [ de ](https://go.microsoft.com/fwlink/?linkid=121312).</span><span class="sxs-lookup"><span data-stu-id="ed7c7-191">For more information, see [Use an External Data Source for Subscriber Data &#40;Data-Driven Subscription&#41;](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
 <span data-ttu-id="ed7c7-192">Para obtener más información, vea [Using SQL Server 2005 Reporting Services with Hyperion Essbase](https://go.microsoft.com/fwlink/?LinkId=81970).</span><span class="sxs-lookup"><span data-stu-id="ed7c7-192">For more information, see [Using SQL Server 2005 Reporting Services with Hyperion Essbase](https://go.microsoft.com/fwlink/?LinkId=81970).</span></span>  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="ed7c7-193">Temas de procedimientos</span><span class="sxs-lookup"><span data-stu-id="ed7c7-193">How-To Topics</span></span>  
 <span data-ttu-id="ed7c7-194">Esta sección contiene instrucciones paso a paso para trabajar con conexiones de datos, orígenes de datos y conjuntos de datos.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-194">This section contains step-by-step instructions for working with data connections, data sources, and datasets:</span></span>  
  
 [<span data-ttu-id="ed7c7-195">Agregar y comprobar una conexión de datos o un origen de datos &#40;Generador de informes y SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ed7c7-195">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="ed7c7-196">Crear un conjunto de datos compartido o un conjunto de datos incrustado &#40;Generador de informes y SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ed7c7-196">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="ed7c7-197">Agregar un filtro a un conjunto de datos &#40;Generador de informes y SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ed7c7-197">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="ed7c7-198">Secciones relacionadas</span><span class="sxs-lookup"><span data-stu-id="ed7c7-198">Related Sections</span></span>  
 <span data-ttu-id="ed7c7-199">Estas secciones de la documentación proporcionan información conceptual detallada sobre los datos de informe, así como información de procedimientos acerca de cómo definir, personalizar y usar las partes de un informe que están relacionadas con datos.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-199">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="ed7c7-200">Agregar datos a un informe &#40;Generador de informes y SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ed7c7-200">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="ed7c7-201">Proporciona información general sobre cómo obtener acceso a los datos del informe.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-201">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="ed7c7-202">Conexiones de datos, orígenes de datos y cadenas de conexión en el Generador de informes</span><span class="sxs-lookup"><span data-stu-id="ed7c7-202">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="ed7c7-203">Proporciona información sobre las conexiones de datos y los orígenes de datos.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-203">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="ed7c7-204">Conjuntos de datos incrustados y compartidos de informe &#40;Generador de informes y SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ed7c7-204">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="ed7c7-205">Proporciona información sobre conjuntos de datos compartidos e incrustados.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-205">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="ed7c7-206">Colección Campos del conjunto de datos &#40;Generador de informes y SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ed7c7-206">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="ed7c7-207">Proporciona información sobre la colección de campos que genera la consulta del conjunto de datos.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-207">Provides information about the field collection that is generated by the dataset query.</span></span>  
  
 <span data-ttu-id="ed7c7-208">[Orígenes de datos admitidos por Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) en la documentación relativa a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en los [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Libros en pantalla](https://go.microsoft.com/fwlink/?linkid=121312) de .</span><span class="sxs-lookup"><span data-stu-id="ed7c7-208">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="ed7c7-209">Proporciona información detallada sobre la compatibilidad de versiones y plataformas para cada extensión de datos.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-209">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
 [<span data-ttu-id="ed7c7-210">Using SQL Server 2005 Reporting Services with Hyperion Essbase</span><span class="sxs-lookup"><span data-stu-id="ed7c7-210">Using SQL Server 2005 Reporting Services with Hyperion Essbase</span></span>](https://go.microsoft.com/fwlink/?LinkId=81970)  
 <span data-ttu-id="ed7c7-211">Proporciona información detallada sobre cómo trabajar con esta extensión de datos.</span><span class="sxs-lookup"><span data-stu-id="ed7c7-211">Provides detailed information about working with this data extension.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="ed7c7-212">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ed7c7-212">See Also</span></span>  
 <span data-ttu-id="ed7c7-213">[Parámetros de informe &#40;Generador de informes y Diseñador de informes&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="ed7c7-213">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="ed7c7-214">[Filtrar, agrupar y ordenar datos &#40;Generador de informes y SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ed7c7-214">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ed7c7-215">Expresiones &#40;Generador de informes y SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ed7c7-215">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  