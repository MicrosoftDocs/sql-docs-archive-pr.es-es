---
title: Editor de destinos de ADO NET (página Administrador de conexiones) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetdest.connection.f1
ms.assetid: a3b11286-32c8-40e1-8ae7-090e2590345a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 78851d5bbad18d2d1076eaa87200dd73e6962a90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662217"
---
# <a name="ado-net-destination-editor-connection-manager-page"></a><span data-ttu-id="73e26-102">Editor de destinos de ADO NET (página Administrador de conexiones)</span><span class="sxs-lookup"><span data-stu-id="73e26-102">ADO NET Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="73e26-103">Utilice la página **Administrador de conexiones** del cuadro de diálogo **Editor de destinos de ADO NET** para seleccionar la conexión [!INCLUDE[vstecado](../includes/vstecado-md.md)] del destino.</span><span class="sxs-lookup"><span data-stu-id="73e26-103">Use the **Connection Manager** page of the **ADO NET Destination Editor** dialog box to select the [!INCLUDE[vstecado](../includes/vstecado-md.md)] connection for the destination.</span></span> <span data-ttu-id="73e26-104">Esta página también permite seleccionar una tabla o vista de la base de datos.</span><span class="sxs-lookup"><span data-stu-id="73e26-104">This page also lets you select a table or view from the database.</span></span>  
  
 <span data-ttu-id="73e26-105">Para obtener más información acerca del destino de ADO NET, vea [ADO NET Destination](data-flow/ado-net-destination.md).</span><span class="sxs-lookup"><span data-stu-id="73e26-105">To learn more about the ADO NET destination, see [ADO NET Destination](data-flow/ado-net-destination.md).</span></span>  
  
 <span data-ttu-id="73e26-106">**Para abrir la página Administrador de conexiones**</span><span class="sxs-lookup"><span data-stu-id="73e26-106">**To open the Connection Manager page**</span></span>  
  
1.  <span data-ttu-id="73e26-107">En [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], abra el paquete [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] que tiene el destino de ADO NET.</span><span class="sxs-lookup"><span data-stu-id="73e26-107">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET destination.</span></span>  
  
2.  <span data-ttu-id="73e26-108">En la pestaña **Flujo de datos** , haga doble clic en el destino de ADO NET.</span><span class="sxs-lookup"><span data-stu-id="73e26-108">On the **Data Flow** tab, double-click the ADO NET destination.</span></span>  
  
3.  <span data-ttu-id="73e26-109">En el **Editor de destinos de ADO NET**, haga clic en **Administrador de conexiones**.</span><span class="sxs-lookup"><span data-stu-id="73e26-109">In the **ADO NET Destination Editor**, click **Connection Manager**.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="73e26-110">Opciones estáticas</span><span class="sxs-lookup"><span data-stu-id="73e26-110">Static Options</span></span>  
 <span data-ttu-id="73e26-111">**Connection manager**</span><span class="sxs-lookup"><span data-stu-id="73e26-111">**Connection manager**</span></span>  
 <span data-ttu-id="73e26-112">Seleccione un administrador de conexiones de la lista o cree una conexión haciendo clic en **Nuevo**.</span><span class="sxs-lookup"><span data-stu-id="73e26-112">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="73e26-113">**Nuevo**</span><span class="sxs-lookup"><span data-stu-id="73e26-113">**New**</span></span>  
 <span data-ttu-id="73e26-114">Cree un administrador de conexiones mediante el cuadro de diálogo **Configurar el administrador de conexiones ADO.NET** .</span><span class="sxs-lookup"><span data-stu-id="73e26-114">Create a new connection manager by using the **Configure ADO.NET Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="73e26-115">**Usar una tabla o una vista**</span><span class="sxs-lookup"><span data-stu-id="73e26-115">**Use a table or view**</span></span>  
 <span data-ttu-id="73e26-116">Seleccione una tabla o vista de la lista o cree una tabla haciendo clic en **Nueva**.</span><span class="sxs-lookup"><span data-stu-id="73e26-116">Select an existing table or view from the list, or create a new table by clicking **New**..</span></span>  
  
 <span data-ttu-id="73e26-117">**Nuevo**</span><span class="sxs-lookup"><span data-stu-id="73e26-117">**New**</span></span>  
 <span data-ttu-id="73e26-118">Cree un tabla o una vista mediante el cuadro de diálogo **Crear tabla** .</span><span class="sxs-lookup"><span data-stu-id="73e26-118">Create a new table or view by using the **Create Table** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="73e26-119">Al hacer clic en **Nueva**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] genera una instrucción predeterminada CREATE TABLE basada en el origen de datos conectado.</span><span class="sxs-lookup"><span data-stu-id="73e26-119">When you click **New**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="73e26-120">La instrucción predeterminada CREATE TABLE no incluirá el atributo FILESTREAM, aunque la tabla de origen tenga una columna con el atributo FILESTREAM declarado.</span><span class="sxs-lookup"><span data-stu-id="73e26-120">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="73e26-121">Para ejecutar un componente [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] con el atributo FILESTREAM, implemente en primer lugar el almacenamiento de FILESTREAM en la base de datos de destino.</span><span class="sxs-lookup"><span data-stu-id="73e26-121">To run an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="73e26-122">A continuación, agregue el atributo FILESTREAM a la instrucción CREATE TABLE en el cuadro de diálogo **Crear tabla** .</span><span class="sxs-lookup"><span data-stu-id="73e26-122">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="73e26-123">Para más información, vea [Datos de objeto binario grande &#40;Blob&#41; &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span><span class="sxs-lookup"><span data-stu-id="73e26-123">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="73e26-124">**Versión preliminar**</span><span class="sxs-lookup"><span data-stu-id="73e26-124">**Preview**</span></span>  
 <span data-ttu-id="73e26-125">Obtenga una vista previa de los resultados mediante el cuadro de diálogo **Vista previa de los resultados de la consulta** .</span><span class="sxs-lookup"><span data-stu-id="73e26-125">Preview results by using the **Preview Query Results** dialog box.</span></span> <span data-ttu-id="73e26-126">La vista previa puede mostrar hasta 200 filas.</span><span class="sxs-lookup"><span data-stu-id="73e26-126">Preview can display up to 200 rows.</span></span>  
  
 <span data-ttu-id="73e26-127">**Usar inserción masiva cuando esté disponible**</span><span class="sxs-lookup"><span data-stu-id="73e26-127">**Use bulk insert when available**</span></span>  
 <span data-ttu-id="73e26-128">Especifique si se debe usar la interfaz <xref:System.Data.SqlClient.SqlBulkCopy> para mejorar el rendimiento de las operaciones de inserción masiva.</span><span class="sxs-lookup"><span data-stu-id="73e26-128">Specify whether to use the <xref:System.Data.SqlClient.SqlBulkCopy> interface to improve the performance of bulk insert operations.</span></span>  
  
 <span data-ttu-id="73e26-129">Solamente los proveedores ADO.NET que devuelven un objeto <xref:System.Data.SqlClient.SqlConnection> admiten el uso de la interfaz <xref:System.Data.SqlClient.SqlBulkCopy> .</span><span class="sxs-lookup"><span data-stu-id="73e26-129">Only ADO.NET providers that return a <xref:System.Data.SqlClient.SqlConnection> object support the use of the <xref:System.Data.SqlClient.SqlBulkCopy> interface.</span></span> <span data-ttu-id="73e26-130">El Proveedor de datos .NET para SQL Server (SqlClient) devuelve un objeto <xref:System.Data.SqlClient.SqlConnection> y, por otra parte, un proveedor personalizado puede devolver un objeto <xref:System.Data.SqlClient.SqlConnection> .</span><span class="sxs-lookup"><span data-stu-id="73e26-130">The .NET Data Provider for SQL Server (SqlClient) returns a <xref:System.Data.SqlClient.SqlConnection> object, and a custom provider may return a <xref:System.Data.SqlClient.SqlConnection> object.</span></span>  
  
 <span data-ttu-id="73e26-131">Puede usar el proveedor de datos .NET para SQL Server (SqlClient) para conectarse a [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)].</span><span class="sxs-lookup"><span data-stu-id="73e26-131">You can use the .NET Data Provider for SQL Server (SqlClient) to connect to [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)].</span></span>  
  
 <span data-ttu-id="73e26-132">Si selecciona **Use bulk insert when available**(Usar la inserción masiva cuando esté disponible) y establece la opción **Error** en **Redirect the row**(Redirigir la fila), el lote de datos que el destino redirige a la salida de error puede incluir filas correctas. Para obtener más información sobre cómo administrar errores en operaciones masivas, vea [Control de errores en los datos](data-flow/error-handling-in-data.md).</span><span class="sxs-lookup"><span data-stu-id="73e26-132">If you select **Use bulk insert when available**, and set the **Error** option to **Redirect the row**, the batch of data that the destination redirects to the error output may include good rows.For more information about handling errors in bulk operations, see [Error Handling in Data](data-flow/error-handling-in-data.md).</span></span> <span data-ttu-id="73e26-133">Para obtener más información sobre la opción **Error** , vea [Editor de destinos de ADO NET &#40;página Salida de error&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md).</span><span class="sxs-lookup"><span data-stu-id="73e26-133">For more information about the **Error** option, see [ADO NET Destination Editor &#40;Error Output Page&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="73e26-134">Si una tabla de origen de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] o de Sybase incluye una columna de identidad, es necesario que use las tareas Ejecutar SQL para ejecutar una instrucción SET IDENTITY_INSERT antes y después del destino de ADO NET.</span><span class="sxs-lookup"><span data-stu-id="73e26-134">If a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or Sybase source table includes an identity column, you must use Execute SQL tasks to run a SET IDENTITY_INSERT statement before and after the ADO NET destination.</span></span> <span data-ttu-id="73e26-135">La propiedad de la columna de identidad especifica un valor incremental de la columna.</span><span class="sxs-lookup"><span data-stu-id="73e26-135">The identity column property specifies an incremental value for the column.</span></span> <span data-ttu-id="73e26-136">La instrucción SET IDENTITY_INSERT permite insertar valores explícitos en la columna de identidad.</span><span class="sxs-lookup"><span data-stu-id="73e26-136">The SET IDENTITY_INSERT statement enables explicit values to be inserted into the identity column.</span></span> <span data-ttu-id="73e26-137">Para ejecutar las instrucciones CREATE TABLE y SET IDENTITY en la misma conexión de bases de datos, establezca en `RetainSameConnection` la propiedad `True` del administrador de conexiones [!INCLUDE[vstecado](../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="73e26-137">To run the CREATE TABLE and SET IDENTITY statements on the same database connection, set the `RetainSameConnection` property of the [!INCLUDE[vstecado](../includes/vstecado-md.md)] connection manager to `True`.</span></span> <span data-ttu-id="73e26-138">Asimismo, use el mismo administrador de conexiones [!INCLUDE[vstecado](../includes/vstecado-md.md)] para las tareas Ejecutar SQL y el destino de ADO NET.</span><span class="sxs-lookup"><span data-stu-id="73e26-138">Also, use the same [!INCLUDE[vstecado](../includes/vstecado-md.md)] connection manager for the Execute SQL tasks and the ADO NET destination.</span></span>  
>   
>  <span data-ttu-id="73e26-139">Para obtener más información, vea [SET IDENTITY_INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-identity-insert-transact-sql) y [IDENTITY &#40;propiedad de Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql-identity-property).</span><span class="sxs-lookup"><span data-stu-id="73e26-139">For more information, see [SET IDENTITY_INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-identity-insert-transact-sql) and [IDENTITY &#40;Property&#41; &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql-identity-property).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="73e26-140">Recursos externos</span><span class="sxs-lookup"><span data-stu-id="73e26-140">External Resources</span></span>  
 <span data-ttu-id="73e26-141">Artículo técnico sobre cómo [cargar datos en Azure SQL Database de la forma más rápida](https://go.microsoft.com/fwlink/?LinkId=244333), en sqlcat.com</span><span class="sxs-lookup"><span data-stu-id="73e26-141">Technical article, [Loading data to Azure SQL Database the fast way](https://go.microsoft.com/fwlink/?LinkId=244333), on sqlcat.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73e26-142">Consulte también</span><span class="sxs-lookup"><span data-stu-id="73e26-142">See Also</span></span>  
 <span data-ttu-id="73e26-143">[Editor de destinos de ADO NET &#40;página asignaciones&#41;](../../2014/integration-services/ado-net-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="73e26-143">[ADO NET Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/ado-net-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="73e26-144">[Editor de destinos de ADO NET &#40;página salida de error&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="73e26-144">[ADO NET Destination Editor &#40;Error Output Page&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="73e26-145">[Administrador de conexiones de ADO.NET](connection-manager/ado-net-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="73e26-145">[ADO.NET Connection Manager](connection-manager/ado-net-connection-manager.md) </span></span>  
 [<span data-ttu-id="73e26-146">Tarea Ejecutar SQL</span><span class="sxs-lookup"><span data-stu-id="73e26-146">Execute SQL Task</span></span>](control-flow/execute-sql-task.md)  
  
  