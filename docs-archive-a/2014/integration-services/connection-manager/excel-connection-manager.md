---
title: Administrador de conexiones con Excel | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- files [Integration Services], connections
- connections [Integration Services], Excel
- Excel [Integration Services]
- connection managers [Integration Services], Excel
ms.assetid: 667419f2-74fb-4b50-b963-9197d1368cda
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7561361c6d4ab7e22282b25367906aa4b75e5bc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672234"
---
# <a name="excel-connection-manager"></a>Administrador de conexiones con Excel
  Un Administrador de conexiones con Excel permite a un paquete conectarse con un archivo de libro de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel existente. El origen de Excel y el destino de Excel que [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] incluye usan el administrador de conexiones con Excel.  
  
 Cuando agrega un Administrador de conexiones con Excel a un paquete, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crea un Administrador de conexiones que se resuelve como una conexión Excel en el tiempo de ejecución, establece las propiedades del Administrador de conexiones y agrega el Administrador de conexiones a la colección `Connections` del paquete.  
  
 La propiedad `ConnectionManagerType` del administrador de conexiones se establece en `EXCEL`.  
  
> [!NOTE]  
>  No puede conectar con un archivo de Excel protegido mediante contraseña.  
  
## <a name="configuration-of-the-excel-connection-manager"></a>Configuración del administrador de conexiones de Excel  
 Puede configurar el Administrador de conexiones con Excel de las maneras siguientes:  
  
-   Especificar la ruta del archivo de libro de Excel.  
  
-   Especificar la versión de Excel que se usó para crear el archivo.  
  
-   Indicar si la primera fila de datos a los que se tuvo acceso en las hojas de cálculo o los rangos seleccionados contiene nombres de columna.  
  
 Si un origen de Excel utiliza el Administrador de conexiones con Excel, los nombres de las columnas se incluyen con los datos extraídos. Si un destino de Excel utiliza el Administrador de conexiones con Excel, los nombres de las columnas se incluyen con los datos escritos.  
  
 El administrador de conexiones con Excel usa el [!INCLUDE[msCoName](../../includes/msconame-md.md)] proveedor de OLE DB para Jet 4,0 y el controlador ISAM (método de acceso secuencial indizado) de Excel compatible para conectar y leer y escribir datos en orígenes de datos de Excel. Para obtener más información sobre el comportamiento de este proveedor y controlador cuando se usa con orígenes de Excel y destinos de Excel, vea [Excel Source](../data-flow/excel-source.md) y [Excel Destination](../data-flow/excel-destination.md).  
  
 Puede establecer propiedades a través del Diseñador de [!INCLUDE[ssIS](../../includes/ssis-md.md)] o mediante programación.  
  
 Para más información sobre las propiedades que puede configurar en el Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] , vea [Editor de Administrador de conexiones con Excel](../excel-connection-manager-editor.md).  
  
 Para obtener información sobre la configuración de un administrador de conexiones mediante programación, vea <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> y [Agregar conexiones mediante programación](../building-packages-programmatically/adding-connections-programmatically.md).  
  
 Para más información sobre cómo crear bucles entre un grupo de archivos de Excel, vea [Crear bucles entre archivos y tablas de Excel usando un contenedor de bucles Foreach](../control-flow/foreach-loop-container.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Crear bucles entre archivos y tablas de Excel mediante un contenedor de bucles ForEach](../control-flow/foreach-loop-container.md)  
  
-   [Importación de datos desde Excel o exportación de datos a Excel con SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md)
  
  
