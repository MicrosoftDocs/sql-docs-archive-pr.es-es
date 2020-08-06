---
title: Tarea Transferir objetos de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfersqlserverobjectstask.f1
helpviewer_keywords:
- Transfer SQL Server Objects task [Integration Services]
ms.assetid: fe86d6e5-e415-406c-88f3-dc3ef71bd5f0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 281acb189e8f4dcfde9dc7ad1d2a74525236d28d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662175"
---
# <a name="transfer-sql-server-objects-task"></a>Tarea Transferir objetos de SQL Server
  La tarea Transferir objetos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transfiere uno o varios tipos de objetos de una base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entre instancias de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Por ejemplo, la tarea puede copiar tablas y procedimientos almacenados. Dependiendo de la versión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que se utilice como origen, hay diferentes tipos de objetos disponibles para copiar. Por ejemplo, solo en una base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se incluyen esquemas y agregados definidos por el usuario.  
  
## <a name="objects-to-transfer"></a>Objetos que se transferirán  
 Se pueden copiar roles de servidor, roles y usuarios de la base de datos especificada, así como los permisos para los objetos transferidos. Si copia los usuarios, roles y permisos asociados junto con los objetos, puede hacer que los objetos transferidos se puedan utilizar de inmediato en el servidor de destino.  
  
 En la tabla siguiente se muestra el tipo de objetos que se pueden copiar.  
  
|Object|  
|------------|  
|Tablas|  
|Vistas|  
|Procedimientos almacenados|  
|Funciones definidas por el usuario|  
|Valores predeterminados|  
|Tipos de datos definidos por el usuario|  
|Funciones de partición|  
|Esquemas de partición|  
|Esquemas|  
|Ensamblados|  
|Funciones de agregado definidas por el usuario|  
|Tipos definidos por el usuario|  
|Colección de esquemas XML|  
  
 Los tipos definidos por el usuario (UDT) que se han creado en una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tienen dependencias en los ensamblados CLR (Common Language Runtime). Si utiliza la tarea Transferir objetos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para transferir UDT, también deberá configurar la tarea para transferir los objetos dependientes. Para transferir objetos dependientes, establezca la propiedad `IncludeDependentObjects` en `True`.  
  
### <a name="table-options"></a>Opciones de tabla  
 Al copiar tablas, puede indicar los tipos de elementos relacionados con la tabla que desee incluir en el proceso de copia. Puede copiar los siguientes tipos de elementos junto con la tabla relacionada:  
  
-   Índices  
  
-   Desencadenadores  
  
-   Índices de texto completo  
  
-   Claves principales  
  
-   Claves externas  
  
 También puede indicar si el script que genera la tarea está en formato Unicode.  
  
## <a name="destination-options"></a>Opciones de destino  
 Puede configurar la tarea Transferir objetos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para que incluya nombres de esquema, datos, propiedades extendidas de los objetos transferidos y objetos dependientes en la transferencia. Si copia datos, puede reemplazar o anexar los datos existentes.  
  
 Algunas opciones únicamente se aplican a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Por ejemplo, solo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] admite esquemas.  
  
## <a name="security-options"></a>Opciones de seguridad  
 La tarea Transferir objetos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] puede incluir usuarios de nivel de base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y roles del origen, inicios de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y los permisos para los objetos transferidos. Por ejemplo, la transferencia puede incluir los permisos en las tablas transferidas.  
  
## <a name="transfer-objects-between-instances-of-sql-server"></a>Transferencia de objetos entre instancias de SQL Server  
 La tarea Transferir objetos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] admite un origen y un destino que sea [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="events"></a>Eventos  
 La tarea emite un evento de información que indica el objeto transferido y un evento de advertencia cuando se sobrescribe un objeto. También se emite un evento de información para acciones como el truncamiento de tablas de una base de datos.  
  
 La tarea Transferir objetos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no indica el progreso incremental de la transferencia de objetos; solo indica 0% y 100%.  
  
## <a name="execution-value"></a>Valor de ejecución  
 El valor de ejecución, almacenado en la propiedad `ExecutionValue` de la tarea, devuelve el número de objetos transferidos. Si se asigna una variable definida por el usuario a la propiedad `ExecValueVariable` de la tarea Transferir objetos de SQL Server, se puede hacer que la información de la transferencia de objetos esté disponible para otros objetos del paquete. Para más información, vea [Variables de Integration Services &#40;SSIS&#41;](../integration-services-ssis-variables.md) y [Usar variables en paquetes](../use-variables-in-packages.md).  
  
## <a name="log-entries"></a>Entradas del registro  
 La tarea Transferir objetos de SQL Server incluye las siguientes entradas del registro personalizadas:  
  
-   TransferSqlServerObjectsTaskStartTransferringObjects   Esta entrada del registro indica que se ha iniciado la transferencia. La entrada del registro incluye la hora de inicio.  
  
-   TransferSqlServerObjectsTaskFinishedTransferringObjects    Esta entrada del registro indica que ha finalizado la transferencia. La entrada del registro incluye la hora de finalización.  
  
 Además, una entrada del registro para un evento `OnInformation` indica el número de objetos del tipo seleccionado para la transferencia, el número de objetos transferidos y acciones, como el truncamiento de tablas cuando se transfieren datos con tablas. Se escribe una entrada del registro para el evento `OnWarning` por cada objeto que se sobrescribe en el destino.  
  
## <a name="security-and-permissions"></a>Seguridad y permisos  
 El usuario debe tener permiso para examinar objetos en el servidor de origen, y para quitar y crear objetos en el servidor de destino; además, el usuario debe tener acceso a la base de datos especificada y a los objetos de la base de datos.  
  
## <a name="configuration-of-the-transfer-sql-server-objects-task"></a>Configuración de la tarea Transferir objetos de SQL Server  
 La tarea Transferir objetos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se puede configurar para que transfiera todos los objetos, todos los objetos de un tipo o solamente los objetos especificados de un tipo. Por ejemplo, puede copiar únicamente las tablas seleccionadas en la base de datos AdventureWorks.  
  
 Si la tarea Transferir objetos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transfiere tablas, puede especificar el tipo de objetos relacionados con las tablas que quiere copiar con las tablas. Por ejemplo, puede especificar que se copien las claves principales con las tablas.  
  
 Para mejorar aún más la funcionalidad de los objetos transferidos, puede configurar la tarea Transferir objetos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para que incluya nombres de esquema, datos, propiedades extendidas de los objetos transferidos y objetos dependientes en la transferencia. Al copiar los datos, puede especificar si desea reemplazar o anexar los datos existentes.  
  
 Durante la ejecución, la tarea Transferir objetos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se conecta con los servidores de origen y de destino utilizando dos administradores de conexión SMO. Los administradores de conexión SMO se configuran independientemente de la tarea Transferir objetos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y después se hace referencia a ellos en la tarea Transferir objetos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Los administradores de conexión SMO especifican el servidor y el modo de autenticación que se utilizará para tener acceso al servidor. Para más información, consulte [SMO Connection Manager](../connection-manager/smo-connection-manager.md).  
  
 Puede establecer propiedades a través del Diseñador de [!INCLUDE[ssIS](../../includes/ssis-md.md)] o mediante programación.  
  
 Para obtener más información acerca de las propiedades que puede establecer en el Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] , haga clic en uno de los temas siguientes:  
  
-   [Editor de la tarea Transferir objetos de SQL Server &#40;página General&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Editor de la tarea Transferir objetos de SQL Server &#40;página Objetos&#41;](../transfer-sql-server-objects-task-editor-objects-page.md)  
  
-   [Página Expresiones](../expressions/expressions-page.md)  
  
 Para obtener más información sobre cómo establecer estas propiedades en el Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] , haga clic en el siguiente tema:  
  
-   [Establecer las propiedades de tareas o contenedores](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-transfer-sql-server-objects-task"></a>Configuración mediante programación de la tarea Transferir objetos de SQL Server  
 Para obtener más información sobre cómo establecer estas propiedades mediante programación, haga clic en el tema siguiente:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferSqlServerObjectsTask.TransferSqlServerObjectsTask>  
  
  
