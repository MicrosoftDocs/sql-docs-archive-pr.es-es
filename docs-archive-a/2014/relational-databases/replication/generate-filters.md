---
title: Generar filtros | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.generatefilters.f1
ms.assetid: be28515c-5d6d-467b-b933-d7c8d97a45b4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b0e484c89c97d3f32f3e41197800202f796a25d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663355"
---
# <a name="generate-filters"></a><span data-ttu-id="03613-102">Generar filtros</span><span class="sxs-lookup"><span data-stu-id="03613-102">Generate Filters</span></span>
  <span data-ttu-id="03613-103">El cuadro de diálogo **Generar filtros** le permite definir un filtro de filas en una tabla de una publicación de combinación; la replicación extenderá automáticamente el filtro a otras tablas relacionadas con relaciones de clave externa.</span><span class="sxs-lookup"><span data-stu-id="03613-103">The **Generate Filters** dialog box allows you to define a row filter on one table in a merge publication; replication then automatically extends the filter to other tables that are related through foreign key relationships.</span></span> <span data-ttu-id="03613-104">Por ejemplo, si define un filtro en una tabla de clientes para que solo contenga datos de clientes franceses, la replicación extiende el filtro de forma que los pedidos y las tablas de detalles de pedidos relacionados solo contengan información relativa a los clientes franceses.</span><span class="sxs-lookup"><span data-stu-id="03613-104">For example, if you define a filter on a customer table so that it only contains data on French customers, replication extends that filter so that related orders and order details tables contain only information related to French customers.</span></span>  
  
## <a name="options"></a><span data-ttu-id="03613-105">Opciones</span><span class="sxs-lookup"><span data-stu-id="03613-105">Options</span></span>  
 <span data-ttu-id="03613-106">El cuadro de diálogo presenta un proceso de tres pasos para crear un filtro de fila en una tabla.</span><span class="sxs-lookup"><span data-stu-id="03613-106">This dialog box involves a three-step process to create a row filter on a table.</span></span> <span data-ttu-id="03613-107">A continuación, el filtro se extiende a las tablas relacionadas con la tabla filtrada mediante relaciones de clave principal y de clave externa.</span><span class="sxs-lookup"><span data-stu-id="03613-107">The filter is then extended to the tables related to the filtered table through primary key and foreign key relationships.</span></span> <span data-ttu-id="03613-108">Por ejemplo, dadas las tablas **Customer**, **SalesOrderHeader**y **SalesOrderDetail**, con una relación entre **Customer** y **SalesOrderHeader**y una relación entre **SalesOrderHeader** y **SalesOrderDetail**, al aplicar un filtro de filas a **Customer**, la replicación extenderá dicho filtro a **SalesOrderHeader** y **SalesOrderDetail**.</span><span class="sxs-lookup"><span data-stu-id="03613-108">For example, given the three tables **Customer**, **SalesOrderHeader**, and **SalesOrderDetail**, with a relationship between **Customer** and **SalesOrderHeader**, and a relationship between **SalesOrderHeader** and **SalesOrderDetail**, apply a row filter to **Customer**, and replication extends that filter to **SalesOrderHeader** and **SalesOrderDetail**.</span></span>  
  
1.  <span data-ttu-id="03613-109">**Seleccione la tabla que desea filtrar.**</span><span class="sxs-lookup"><span data-stu-id="03613-109">**Select the table to filter.**</span></span>  
  
     <span data-ttu-id="03613-110">Seleccione una tabla del cuadro de lista desplegable.</span><span class="sxs-lookup"><span data-stu-id="03613-110">Select a table from the drop-down list box.</span></span> <span data-ttu-id="03613-111">Las tablas solo se mostrarán en el cuadro de lista si se han seleccionado en la página **Artículos** .</span><span class="sxs-lookup"><span data-stu-id="03613-111">Tables appear in the list box only if they were selected on the **Articles** page.</span></span>  
  
2.  <span data-ttu-id="03613-112">**Complete la instrucción de filtro para identificar las filas de la tabla que recibirán los suscriptores.**</span><span class="sxs-lookup"><span data-stu-id="03613-112">**Complete the filter statement to identify which table rows Subscribers will receive.**</span></span>  
  
     <span data-ttu-id="03613-113">Defina una nueva instrucción de filtro.</span><span class="sxs-lookup"><span data-stu-id="03613-113">Define a new filter statement.</span></span> <span data-ttu-id="03613-114">El cuadro de lista **Columnas** muestra todas las columnas que va a publicar en la tabla seleccionada en **Seleccione la tabla que desea filtrar**.</span><span class="sxs-lookup"><span data-stu-id="03613-114">The **Columns** list box lists all the columns that you are publishing from the table you selected in **Select the table to filter**.</span></span> <span data-ttu-id="03613-115">El área de texto **Instrucción de filtro** incluye el texto predeterminado, que tiene este formato:</span><span class="sxs-lookup"><span data-stu-id="03613-115">The **Filter statement** text area includes the default text, which is in the form of:</span></span>  
  
     `SELECT <published_columns> FROM [tableowner].[tablename] WHERE`  
  
     <span data-ttu-id="03613-116">No se puede cambiar este texto; escriba la cláusula de filtro después de la palabra clave WHERE utilizando sintaxis estándar [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="03613-116">This text cannot be changed; type the filter clause after the WHERE keyword using standard [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="03613-117">Por motivos de rendimiento, se recomienda que no aplique funciones a nombres de columnas en las cláusulas de los filtros de fila con parámetros, como `LEFT([MyColumn]) = SUSER_SNAME()`.</span><span class="sxs-lookup"><span data-stu-id="03613-117">For performance reasons, we recommended that you not apply functions to column names in parameterized row filter clauses, such as `LEFT([MyColumn]) = SUSER_SNAME()`.</span></span> <span data-ttu-id="03613-118">Si utiliza HOST_NAME en una cláusula de filtro y reemplaza el valor HOST_NAME, puede que sea necesario convertir los tipos de datos utilizando CONVERT.</span><span class="sxs-lookup"><span data-stu-id="03613-118">If you use HOST_NAME in a filter clause and override the HOST_NAME value, it might be necessary to convert data types using CONVERT.</span></span> <span data-ttu-id="03613-119">Para obtener más información acerca de las prácticas recomendadas para este caso, vea la sección "Reemplazar el valor de HOST_NAME()" del tema [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).</span><span class="sxs-lookup"><span data-stu-id="03613-119">For more information about best practices for this case, see the section "Overriding the HOST_NAME() Value" in the topic [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
3.  <span data-ttu-id="03613-120">**Especifique cuántas suscripciones recibirán datos de esta tabla.**</span><span class="sxs-lookup"><span data-stu-id="03613-120">**Specify how many subscriptions will receive data from this table.**</span></span>  
  
     <span data-ttu-id="03613-121">Solo para [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="03613-121">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="03613-122">La replicación de mezcla le permite especificar el tipo de partición más adecuado para sus datos y aplicación.</span><span class="sxs-lookup"><span data-stu-id="03613-122">Merge replication allows you to specify the type of partitions that are best suited to your data and application.</span></span> <span data-ttu-id="03613-123">Si selecciona **Una fila de esta tabla irá a una sola suscripción**, la replicación de mezcla establece la opción de particiones no superpuestas.</span><span class="sxs-lookup"><span data-stu-id="03613-123">If you select **A row from this table will go to only one subscription**, merge replication sets the nonoverlapping partitions option.</span></span> <span data-ttu-id="03613-124">Las particiones no superpuestas funcionan junto con las particiones precalculadas para aumentar el rendimiento: la finalidad de las particiones no superpuestas es minimizar el costo de carga asociado a las particiones precalculadas.</span><span class="sxs-lookup"><span data-stu-id="03613-124">Nonoverlapping partitions work in conjunction with precomputed partitions to improve performance, with nonoverlapping partitions minimizing the upload cost associated with precomputed partitions.</span></span> <span data-ttu-id="03613-125">La ventaja en el rendimiento de las particiones no superpuestas es más evidente cuando los filtros con parámetros y de combinación utilizados son más complejos.</span><span class="sxs-lookup"><span data-stu-id="03613-125">The performance benefit of nonoverlapping partitions is more noticeable when the parameterized filters and join filters used are more complex.</span></span> <span data-ttu-id="03613-126">Si selecciona esta opción, debe asegurarse de que los datos se dividen en particiones de forma que una fila no se pueda replicar en más de un suscriptor.</span><span class="sxs-lookup"><span data-stu-id="03613-126">If you select this option, you must ensure that the data is partitioned in such a way that a row cannot be replicated to more than one Subscriber.</span></span> <span data-ttu-id="03613-127">Para obtener más información, vea la sección sobre cómo configurar opciones de partición en el tema [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).</span><span class="sxs-lookup"><span data-stu-id="03613-127">For more information, see the section "Setting 'partition options'" in the topic [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 <span data-ttu-id="03613-128">Una vez agregado un filtro, haga clic en **Aceptar** para salir y cerrar el cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="03613-128">After you have added a filter, click **OK** to exit and close the dialog box.</span></span> <span data-ttu-id="03613-129">El filtro que ha especificado se analiza y se ejecuta según la tabla de la cláusula SELECT.</span><span class="sxs-lookup"><span data-stu-id="03613-129">The filter you specified is parsed and run against the table in the SELECT clause.</span></span> <span data-ttu-id="03613-130">Si la instrucción de filtro contiene errores de sintaxis u otros problemas, se le notificará y podrá modificar dicha instrucción.</span><span class="sxs-lookup"><span data-stu-id="03613-130">If the filter statement contains syntax errors or other problems, you will be notified and will be able to edit the filter statement.</span></span>  
  
 <span data-ttu-id="03613-131">Una vez analizada la instrucción, la replicación crea los filtros de combinación necesarios.</span><span class="sxs-lookup"><span data-stu-id="03613-131">After the statement is parsed, replication creates the necessary join filters.</span></span> <span data-ttu-id="03613-132">Si todavía no ha configurado el distribuidor del publicador en el que se ejecuta este asistente, se le pedirá que lo configure.</span><span class="sxs-lookup"><span data-stu-id="03613-132">If you have not yet configured the Distributor for the Publisher against which this wizard is running, you are prompted to configure it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03613-133">Consulte también</span><span class="sxs-lookup"><span data-stu-id="03613-133">See Also</span></span>  
 <span data-ttu-id="03613-134">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="03613-134">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="03613-135">[Ver y modificar propiedades de publicación](publish/view-and-modify-publication-properties.md) </span><span class="sxs-lookup"><span data-stu-id="03613-135">[View and Modify Publication Properties](publish/view-and-modify-publication-properties.md) </span></span>  
 <span data-ttu-id="03613-136">[Filtrar datos publicados](publish/filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="03613-136">[Filter Published Data](publish/filter-published-data.md) </span></span>  
 <span data-ttu-id="03613-137">[Join Filters](merge/join-filters.md) </span><span class="sxs-lookup"><span data-stu-id="03613-137">[Join Filters](merge/join-filters.md) </span></span>  
 <span data-ttu-id="03613-138">[Filtros de fila con parámetros](merge/parameterized-filters-parameterized-row-filters.md) </span><span class="sxs-lookup"><span data-stu-id="03613-138">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span></span>  
 [<span data-ttu-id="03613-139">Publicar datos y objetos de base de datos</span><span class="sxs-lookup"><span data-stu-id="03613-139">Publish Data and Database Objects</span></span>](publish/publish-data-and-database-objects.md)  
  
  