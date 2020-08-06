---
title: Origen de ADO NET | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetsource.f1
helpviewer_keywords:
- ADO.NET source
- sources [Integration Services], ADO.NET
- sources [Integration Services], DataReader
- .NET Framework [Integration Services]
- DataReader source
ms.assetid: 2a2f1750-2cda-4dda-9dca-623a96a6b3c0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eb50a6171ed29fc5328663d8ce9992e0462e02f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748851"
---
# <a name="ado-net-source"></a>Origen de ADO NET
  El origen de ADO NET consume datos de un proveedor .NET y hace que los datos estén disponibles para el flujo de datos.  
  
 Puede usar el origen de ADO NET para conectarse a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. No se admite la conexión a [!INCLUDE[ssSDS](../../includes/sssds-md.md)] mediante OLE DB. Para más información sobre [!INCLUDE[ssSDS](../../includes/sssds-md.md)], consulte [Instrucciones y limitaciones generales (Azure SQL Database)](https://go.microsoft.com/fwlink/?LinkId=248228).  
  
## <a name="data-type-support"></a>Compatibilidad con tipos de datos  
 El origen convierte cualquier tipo de datos que no se asigna a un tipo de datos de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] específico en el tipo de datos de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] DT_NTEXT. Esta conversión se produce aunque el tipo de datos sea `System.Object`.  
  
 Puede cambiar el tipo de datos DT_NTEXT a DT_WSTR, o el tipo de datos DT_WSTR a DT_NTEXT. Para cambiar los tipos de datos, establezca la propiedad **DataType** en el cuadro de diálogo **Editor avanzado** del origen de ADO NET. Para más información, consulte [Common Properties](../common-properties.md).  
  
 El tipo de datos DT_NTEXT también se puede convertir en el tipo de datos DT_BYTES o DT_STR utilizando una transformación de conversión de datos después del origen de ADO NET. Para más información, consulte [Data Conversion Transformation](transformations/data-conversion-transformation.md).  
  
 En [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], los tipos de datos de fecha, DT_DBDATE, DT_DBTIME2, DT_DBTIMESTAMP2 y DT_DBTIMESTAMPOFFSET, se asignan a ciertos tipos de datos de fecha de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Puede configurar el origen de ADO NET de modo que se conviertan los tipos de datos de fecha de los datos que utiliza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en los que usa [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Para configurar el origen de ADO NET de modo que se conviertan estos tipos de datos de fecha, establezca la propiedad **Type System Version** del administrador de conexiones de [!INCLUDE[vstecado](../../includes/vstecado-md.md)] en **Latest**. (La propiedad **Type System Version** está en la página **Todo** del cuadro de diálogo **Administrador de conexiones** . Para abrir el cuadro de diálogo **Administrador de conexiones** , haga clic con el botón derecho en el administrador de conexiones de [!INCLUDE[vstecado](../../includes/vstecado-md.md)] y, después, elija **Editar**).  
  
> [!NOTE]  
>  Si la propiedad **Type System Version** del administrador de conexiones de [!INCLUDE[vstecado](../../includes/vstecado-md.md)] se establece en **SQL Server 2005**, el sistema convierte los tipos de datos de fecha de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en DT_WSTR.  
  
 El sistema convierte los tipos de datos definidos por el usuario (UDT) en objetos binarios grandes (BLOB) de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] cuando el administrador de conexiones de [!INCLUDE[vstecado](../../includes/vstecado-md.md)] especifica el proveedor como Proveedor de datos .NET para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient). El sistema aplica las reglas siguientes cuando convierte el tipo de datos UDT:  
  
-   Si los datos son de un tipo UDT que no es grande, el sistema los convierte en DT_BYTES.  
  
-   Si los datos son de un tipo UDT que no es grande y la propiedad **Length** de la columna de la base de datos se establece en -1 o en un valor mayor que 8000 bytes, el sistema convierte los datos en DT_IMAGE.  
  
-   Si los datos son de un tipo UDT grande, el sistema los convierte en DT_IMAGE.  
  
    > [!NOTE]  
    >  Si el origen de ADO NET no está configurado para utilizar la salida de errores, el sistema pasa el flujo de datos a la columna DT_IMAGE en fragmentos de 8.000 bytes. Si el origen de ADO NET está configurado para utilizar la salida de errores, el sistema pasa la matriz entera de bytes a la columna DT_IMAGE. Para más información sobre cómo configurar los componentes para que se use la salida de errores, vea [Control de errores en los datos](error-handling-in-data.md).  
  
 Para más información sobre los tipos de datos de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , las conversiones de tipos de datos admitidas y la asignación de tipo de datos en bases de datos específicas (como [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), vea [Tipos de datos de Integration Services](integration-services-data-types.md).  
  
 Para más información sobre cómo asignar tipos de datos de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] a tipos de datos administrados, vea [Trabajar con tipos de datos del flujo de datos](../extending-packages-custom-objects/data-flow/working-with-data-types-in-the-data-flow.md).  
  
## <a name="ado-net-source-troubleshooting"></a>Solución de problemas del origen de ADO NET  
 Puede registrar las llamadas que el origen de ADO NET realiza a proveedores de datos externos. Puede utilizar esta capacidad de registro para solucionar los problemas relacionados con la carga de datos de orígenes de datos externos que realiza el origen de ADO NET. Para registrar las llamadas realizadas por el origen de ADO NET a proveedores de datos externos, habilite el registro de paquetes y seleccione el evento **Diagnostic** en el nivel de paquete. Para más información, vea [Herramientas para solucionar problemas con la ejecución de paquetes](../troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
## <a name="ado-net-source-configuration"></a>Configuración del origen de ADO NET  
 Para configurar el origen de ADO NET, debe proporcionar la instrucción SQL que define el conjunto de resultados. Por ejemplo, un origen de ADO NET que se conecta a la base de datos [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] y utiliza la instrucción SQL `SELECT * FROM Production.Product` extrae todas las filas de la tabla **Production.Product** y proporciona el conjunto de datos a un componente de nivel inferior.  
  
> [!NOTE]  
>  Cuando use una instrucción SQL para invocar un procedimiento almacenado que devuelve resultados de una tabla temporal, use la opción WITH RESULT SETS para definir los metadatos del conjunto de resultados.  
  
> [!NOTE]  
>  Si utiliza una instrucción SQL para ejecutar un procedimiento almacenado y el paquete genera el error siguiente, es posible que pueda resolver el error agregando la instrucción `SET FMTONLY OFF` antes de la instrucción EXEC.  
>   
>  **La columna <column_name> no se encuentra en el origen de datos.**  
  
 Este origen de ADO NET utiliza un administrador de conexiones [!INCLUDE[vstecado](../../includes/vstecado-md.md)] para conectarse a un origen de datos. El administrador de conexiones especifica el proveedor .NET. Para más información, consulte [ADO.NET Connection Manager](../connection-manager/ado-net-connection-manager.md).  
  
 El origen de ADO NET tiene una salida normal y una salida de errores.  
  
 Puede establecer propiedades a través del Diseñador de [!INCLUDE[ssIS](../../includes/ssis-md.md)] o mediante programación.  
  
 Para obtener más información acerca de las propiedades que puede establecer a través del cuadro de diálogo **Editor avanzado** o mediante programación, haga clic en uno de los temas siguientes:  
  
-   [Common Properties](../common-properties.md)  
  
-   [Propiedades personalizadas de ADO NET](ado-net-custom-properties.md)  
  
 Para más información sobre cómo establecer propiedades, vea [Establecer las propiedades de un componente de flujo de datos](set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Consulte también  
 [Destino de DataReader](datareader-destination.md)   
 [Destino de ADO NET](ado-net-destination.md)   
 [Flujo de datos](data-flow.md)  
  
  
