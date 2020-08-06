---
title: Administrador de conexiones ADO | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], ADO
- connection managers [Integration Services], ADO
- ADO connection manager [Integration Services]
ms.assetid: 490418bc-5ef1-41b8-a9c8-de38aa96e0f6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fb4b667733f81eebbaf2b6a2ab9b205c09fe2c66
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676141"
---
# <a name="ado-connection-manager"></a>Administrador de conexiones ADO
  Un administrador de conexiones ADO permite a un paquete conectarse con Objetos de datos ActiveX (ADO), como un conjunto de registros. Este administrador de conexiones se usa normalmente en tareas personalizadas escritas en una versión anterior de un lenguaje, como por ejemplo, Microsoft Visual Basic 6.0 o en tareas personalizadas que forman parte de una aplicación existente que usa ADO para conectarse a un origen de datos.  
  
 Cuando se agrega un administrador de conexiones ADO a un paquete, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crea un administrador de conexiones que se resuelve en una conexión ADO en tiempo de ejecución, establece las propiedades del administrador de conexiones y agrega el administrador de conexiones a la `Connections` colección del paquete. La propiedad `ConnectionManagerType` del administrador de conexiones se establece en `ADO`.  
  
## <a name="troubleshooting-the-ado-connection-manager"></a>Solución de problemas del administrador de conexiones ADO  
 Al ser leídos por un administrador de conexiones ADO, los datos de determinados tipos de datos de fecha de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generarán los resultados que se muestran en la tabla siguiente.  
  
|Tipo de datos de SQL Server|Resultado|  
|--------------------------|------------|  
|`time`, `datetimeoffset`|Se produce un error en el paquete a menos que el paquete utilice comandos SQL parametrizados. Para utilizar comandos SQL parametrizados, utilice la tarea Ejecute SQL en el paquete. Para más información, vea [Tarea Ejecutar SQL](../control-flow/execute-sql-task.md) y [Parámetros y códigos de retorno en la tarea Ejecutar SQL](../parameters-and-return-codes-in-the-execute-sql-task.md).|  
|`datetime2`|El administrador de conexiones ADO trunca el valor de milisegundos.|  
  
> [!NOTE]  
>  Para más información sobre los tipos de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y cómo se asignan a los tipos de datos de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vea [Tipos de datos &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) y [Tipos de datos de Integration Services](../data-flow/integration-services-data-types.md).  
  
## <a name="configuring-the-ado-connection-manager"></a>Configurar el Administrador de conexiones ADO  
 Puede configurar el administrador de conexiones ADO de las maneras siguientes:  
  
-   Proporcionar una cadena de conexión específica configurada para cumplir con los requisitos del proveedor seleccionado.  
  
-   Según el proveedor, incluir el nombre del origen de datos al cual conectarse.  
  
-   Proporcionar credenciales de seguridad según resulte apropiado para el proveedor seleccionado.  
  
-   Indicar si la conexión creada desde el administrador de conexiones se conserva en el tiempo de ejecución.  
  
 Puede establecer propiedades a través del Diseñador de [!INCLUDE[ssIS](../../../includes/ssis-md.md)] o mediante programación.  
  
 Para obtener más información acerca de las propiedades que puede establecer en el Diseñador [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , haga clic en el tema siguiente:  
  
-   [Configurar el administrador de conexiones OLE DB](ole-db-connection-manager.md)  
  
 Para obtener información sobre la configuración de un administrador de conexiones mediante programación, vea <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> y [Agregar conexiones mediante programación](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>Consulte también  
 [Conexiones de Integration Services &#40;SSIS&#41;](integration-services-ssis-connections.md)  
  
  
