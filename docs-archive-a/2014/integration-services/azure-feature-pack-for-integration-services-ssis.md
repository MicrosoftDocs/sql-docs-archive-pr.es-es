---
title: Feature Pack de Azure | Microsoft Docs
ms.custom: ''
ms.date: 08/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL11.SSIS.AZURE.F1
- SQL12.SSIS.AZURE.F1
ms.assetid: 31de555f-ae62-4f2f-a6a6-77fea1fa8189
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8bca2b4d3ce91f6010fbe01da836efd8a67ca6bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744285"
---
# <a name="azure-feature-pack"></a>Feature Pack de Azure
Feature Pack de SQL Server Integration Services (SSIS) para Azure es una extensión que proporciona los componentes que se muestran en esta página para que SSIS se conecte a los servicios de Azure, para transferir datos entre Azure y orígenes de datos locales, y para procesar los datos almacenados en Azure.

## <a name="components-in-the-feature-pack"></a>Componentes de Feature Pack
  
-   Administradores de conexión  
  
    -   [Administrador de conexiones de Azure Storage](connection-manager/azure-storage-connection-manager.md)  
  
    -   [Administrador de conexiones de suscripción de Azure](connection-manager/azure-subscription-connection-manager.md)  
    
    -   [Administrador de conexiones de Azure Data Lake Store](../../2014/integration-services/azure-data-lake-store-connection-manager.md)
    
    -   [Administrador de conexiones de Azure Resource Manager](../../2014/integration-services/azure-resource-manager-connection-manager.md)
    
    -   [Administrador de conexiones de Azure HDInsight](../../2014/integration-services/azure-hdinsight-connection-manager.md)
  
-   Tareas  
  
    -   [Tarea de carga de blobs de Azure](control-flow/azure-blob-upload-task.md)  
  
    -   [Tarea de descarga de blobs de Azure](control-flow/azure-blob-download-task.md)  
  
    -   [Tarea de Hive de Azure HDInsight](control-flow/azure-hdinsight-hive-task.md)  
  
    -   [Tarea de Pig de Azure HDInsight](https://msdn.microsoft.com/library/mt146781(v=sql.120).aspx)
  
    -   [Tarea de creación de clúster de HDInsight de Azure](control-flow/azure-hdinsight-create-cluster-task.md)  
  
    -   [Tarea de eliminación de clúster de HDInsight de Azure](control-flow/azure-hdinsight-delete-cluster-task.md)
    
    -   [Tarea de carga de Azure SQL DW](../../2014/integration-services/azure-sql-dw-upload-task.md)    
    
    -   [Tarea Sistema de archivos de Azure Data Lake Store](control-flow/file-system-task.md)    
  
-   Componentes de flujo de datos  
  
    -   [Origen de blobs de Azure](https://msdn.microsoft.com/library/mt146775(v=sql.120).aspx)  
  
    -   [Destino de blobs de Azure](data-flow/azure-blob-destination.md)  
    
    -   [Origen de Azure Data Lake Store](../../2014/integration-services/azure-data-lake-store-source.md)
    
    -   [Destino de Azure Data Lake Store](../../2014/integration-services/azure-data-lake-store-destination.md)
  
-   Enumerador de blobs de Azure & enumerador de archivos ADLS. Vea [contenedor de bucles foreach](control-flow/foreach-loop-container.md).  
  
 
## <a name="download-the-feature-pack"></a>Descarga del Feature Pack  
Descargue Feature Pack de SQL Server Integration Services (SSIS) para Azure.  
  
-   [Feature Pack de Microsoft SQL Server 2014 Integration Services para Azure](https://www.microsoft.com/download/details.aspx?id=47366)  

## <a name="prerequisites"></a>Requisitos previos  
Necesita instalar los siguientes requisitos previos antes de instalar este Feature Pack.  
  
-   SQL Server Integration Services  
-   .Net Framework 4.5  
  
## <a name="scenarios"></a>Escenarios  
  
### <a name="big-data-processing"></a>Procesamiento de macrodatos  
 Use el Conector Azure para completar el trabajo de procesamiento de macrodatos siguiente:  
  
1.  Utilice la tarea de carga de blobs de Azure para cargar datos de entrada en el almacenamiento de blobs de Azure.  
  
2.  Utilice la tarea de creación de clúster de HDInsight de Azure para crear un clúster de HDInsight de Azure. Este paso es opcional si quiere utilizar su propio clúster.  
  
3.  Utilice la tarea de Hive de HDInsight de Azure o la tarea de Pig de HDInsight de Azure para invocar un trabajo de Pig o Hive en el clúster de HDInsight de Azure.  
  
4.  Utilice la tarea de eliminación de clúster de HDInsight de Azure para eliminar el clúster de HDInsight tras su uso si creó un clúster de HDInsight a petición en el paso 2.  
  
5.  Utilice la tarea de descarga de blobs de HDInsight de Azure para descargar los datos de salida de Pig o Hive del almacenamiento de blobs de Azure.  
  
 ![SSIS-AzureConnector-BigDataScenario](media/ssis-azureconnector-bigdatascenario.png "SSIS-AzureConnector-BigDataScenario")  
  
### <a name="cloud-data-archiving"></a>Archivado de datos en la nube  
 Use el destino de blobs de Azure en un paquete de SSIS para escribir los datos de salida en un almacenamiento de blobs de Azure o para utilizar el origen de blobs de Azure para leer datos desde un almacenamiento de blobs de Azure.  
  
 ![SSIS-AzureConnector-CloudArchive-1](media/ssis-azureconnector-cloudarchive-1.png "SSIS-AzureConnector-CloudArchive-1")  
  
 ![SSIS-AzureConnector-CloudArchive-2](media/ssis-azureconnector-cloudarchive-2.png "SSIS-AzureConnector-CloudArchive-2")  
  
 Y utilice el contenedor de bucles Foreach con el enumerador de blobs de Azure para procesar los datos de varios archivos de blob.  
  
 ![SSIS-AzureConnector-CloudArchive-3](media/ssis-azureconnector-cloudarchive-3.png "SSIS-AzureConnector-CloudArchive-3")  
  
  
