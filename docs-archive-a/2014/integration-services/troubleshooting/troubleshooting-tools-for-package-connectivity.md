---
title: Solución de problemas de conectividad de paquetes de herramientas | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Integration Services packages, troubleshooting
- SSIS packages, troubleshooting
- Integration Services, troubleshooting
- connectivity [Integration Services], troubleshooting
- errors [Integration Services], troubleshooting
- packages [Integration Services], troubleshooting
ms.assetid: 08a019f5-8ba7-4527-97c1-e9846d4022ff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1baac9af5a30fdc0f5b15e8ac56eb5badacc0edb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745895"
---
# <a name="troubleshooting-tools-package-connectivity"></a>Herramientas para solucionar problemas de conectividad entre paquetes
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] incluye características y herramientas que pueden usarse para solucionar problemas de conectividad entre los paquetes y los orígenes de datos desde los que los paquetes extraen y cargan los datos.  
  
## <a name="troubleshooting-issues-with-external-data-providers"></a>Solucionar problemas de proveedores de datos externos  
 Muchos de los errores de los paquetes se producen durante la interacción con proveedores de datos externos. Sin embargo, los mensajes que dichos proveedores devuelven a [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] no suelen proporcionar suficiente información como para comenzar a solucionar los problemas de interacción. Para cubrir esta necesidad de solucionar problemas, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] incluye mensajes de registro que puede utilizar para solucionar problemas relacionados con la interacción de un paquete con orígenes de datos externos.  
  
-   **Habilitar el registro de paquetes y seleccionar el evento Diagnostic del paquete para ver los mensajes de solución de problemas**. Los siguientes componentes de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] son capaces de escribir un mensaje en el registro antes y después de cada llamada a un proveedor de datos externo:  
  
    -   Administrador de conexiones OLE DB, origen de OLE DB y destino de OLE DB  
  
    -   Administrador de conexiones [!INCLUDE[vstecado](../../includes/vstecado-md.md)] y origen de ADO NET  
  
    -   Tarea Ejecutar SQL  
  
    -   Transformación Búsqueda, transformación Comando de OLE DB y transformación Dimensión variable lenta  
  
     Los mensajes de registro incluyen el nombre del método al que se llama. Por ejemplo, estos mensajes de registro podrían incluir el método `Open` de un objeto `Connection` de OLE DB o el método `ExecuteNonQuery` de un objeto `Command`. Los mensajes tienen el formato siguiente, donde '%1!s!' es un marcador de posición para la información de método:  
  
    ```  
    ExternalRequest_pre: The object is ready to make the following external request: '%1!s!'.  
    ExternalRequest_post: '%1!s!'. The external request has completed.  
    ```  
  
     Para solucionar los problemas de interacción con el proveedor de datos externos, revise el registro para comprobar si cada mensaje "anterior" (`ExternalRequest_pre`) tiene un mensaje "posterior" correspondiente (`ExternalRequest_post`). Si no hay un mensaje "posterior" correspondiente, podrá saber que el proveedor de datos externo no respondió tal y como se esperaba.  
  
     En el siguiente ejemplo se muestran algunas filas de ejemplo de un registro que incluye estos mensajes de registro:  
  
    ```  
    ExternalRequest_pre: The object is ready to make the following external request: 'ITransactionJoin::JoinTransaction'.  
    ExternalRequest_post: 'ITransactionJoin::JoinTransaction succeeded'. The external request has completed.  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbConnection.Open'.  
    ExternalRequest_post: 'IDbConnection.Open succeeded'. The external request has completed.  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbConnection.CreateCommand'.  
    ExternalRequest_post: 'IDbConnection.CreateCommand finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbCommand.ExecuteReader'.  
    ExternalRequest_post: 'IDbCommand.ExecuteReader finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDataReader.GetSchemaTable'.  
    ExternalRequest_post: 'IDataReader.GetSchemaTable finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDataReader.Close'.  
    ExternalRequest_post: 'IDataReader.Close finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbConnection.Close'.  
    ExternalRequest_post: 'IDbConnection.Close finished'. The external request has completed."  
    ```  
  
## <a name="see-also"></a>Consulte también  
 [Herramientas para solucionar problemas con el desarrollo de paquetes](troubleshooting-tools-for-package-development.md)   
 [Herramientas para solucionar problemas de la ejecución de paquetes](troubleshooting-tools-for-package-execution.md)  
  
  
