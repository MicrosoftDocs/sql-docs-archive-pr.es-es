---
title: Tarea de creación de clúster de Azure HDInsight | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpcreatecltask.f1
- sql11.dts.designer.afpcreatecltask.f1
ms.assetid: a8ec413a-38d3-45df-887e-6f5f4d9f8465
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e4029e3a01cbcfe04be5f2879a9b60866bfc867a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744813"
---
# <a name="azure-hdinsight-create-cluster-task"></a>Tarea de creación de clúster de HDInsight de Azure
La **tarea de creación de clúster de Azure HDInsight** permite que un paquete SSIS cree un clúster de Azure HDInsight en la suscripción de Azure y el grupo de recursos especificados.
  
> [!NOTE]  
> - La creación de un nuevo clúster de HDInsight puede tardar entre 10 y 20 minutos.  
> - Hay un costo asociado con la creación y ejecución de un clúster de Azure HDInsight. Vea el tema [Precios de HDInsight](https://azure.microsoft.com/pricing/details/hdinsight/) para más información.  
  
Para agregar una **tarea de creación de clúster de HDInsight de Azure**, arrástrela y colóquela en el Diseñador SSIS y haga doble clic (o haga clic con el botón derecho y, después, haga clic en **Editar** ) para ver el siguiente cuadro de diálogo del **Editor de la tarea de creación de clúster de HDInsight de Azure** .  
  
En la tabla siguiente se proporciona una descripción de los campos de este cuadro de diálogo.  
  
|||  
|-|-|  
|**Campo**|**Descripción**|  
|AzureResourceManagerConnection|Seleccione un administrador de conexiones de Azure Resource Manager o cree uno nuevo que se usará para crear el clúster de HDInsight.|  
|AzureStorageConnection|Seleccione un administrador de conexiones de almacenamiento de Azure existente o cree uno que haga referencia a una cuenta de almacenamiento de Azure que se asociará con el clúster de HDInsight.|
|SubscriptionId|Especifique el identificador de la suscripción en la que se creará el clúster de HDInsight.|
|ResourceGroup|Especifique el grupo de recursos de Azure en el que se creará el clúster de HDInsight.|
|Location|Especifique la ubicación del clúster de HDInsight. El clúster debe crearse en la misma ubicación que la cuenta de Azure Storage especificada.|  
|ClusterName|Especifique un nombre para el clúster de HDInsight que se va a crear.|  
|clusterSize|Especifique el número de nodos que quiere crear en el clúster.|  
|BlobContainer|Especifique el nombre del contenedor de almacenamiento predeterminado que quiere asociar con el clúster de HDInsight.|  
|UserName|Especifique el nombre de usuario que se usará para conectarse al clúster de HDInsight.|  
|Contraseña|Especifique la contraseña que se usará para conectarse al clúster de HDInsight.|
|SshUserName|Especifique el nombre de usuario que se usa para acceder de forma remota al clúster de HDInsight con SSH.|
|SshPassword|Especifique la contraseña usada para acceder de forma remota al clúster de HDInsight con SSH.|
|FailIfExists|Especifique si la tarea debe generar un error si el clúster ya existe.|  
  
> [!NOTE]  
> Las ubicaciones del clúster de HDInsight y de la cuenta de Azure Storage deben ser la misma.
