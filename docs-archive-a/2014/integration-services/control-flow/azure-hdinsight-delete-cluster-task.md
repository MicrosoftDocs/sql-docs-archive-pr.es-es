---
title: Tarea de eliminación de clúster de Azure HDInsight | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpdelcltask.f1
- sql11.dts.designer.afpdelcltask.f1
ms.assetid: e298776e-d18a-4393-a8e6-65ee3d555749
author: chugugrace
ms.author: chugu
ms.openlocfilehash: db0a15aaea37c6d18c1d3c2136e0fd0c94eb7506
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676128"
---
# <a name="azure-hdinsight-delete-cluster-task"></a>Tarea de eliminación de clúster de HDInsight de Azure
La **tarea de eliminación de clúster de Azure HDInsight** permite que un paquete SSIS elimine un clúster de Azure HDInsight del grupo de recursos y la suscripción de Azure especificados.
  
> [!NOTE]
> La eliminación de un clúster de HDInsight puede tardar entre 10 y 20 minutos.  
  
Para agregar una **tarea de eliminación de clúster de HDInsight de Azure**, arrástrela y suéltela en el Diseñador SSIS y haga doble clic o haga clic con el botón derecho y luego haga clic en **Editar** para ver el siguiente cuadro de diálogo: **Azure HDInsight Delete Cluster Task Editor** (Editor de tareas de eliminación de clúster de HDInsight de Azure).  
  
En la tabla siguiente se proporciona una descripción de los campos del cuadro de diálogo.  
  
|||  
|-|-|  
|**Campo**|**Descripción**|  
|AzureResourceManagerConnection|Seleccione un administrador de conexiones de Azure Resource Manager existente o cree uno nuevo que se usará para eliminar el clúster de HDInsight.|
|SubscriptionId|Especifique el identificador de la suscripción en la que se encuentra el clúster de HDInsight.|
|ResourceGroup|Especifique el grupo de recursos de Azure en el que se encuentra el clúster de HDInsight.|
|ClusterName|Especifique el nombre del clúster que se va a eliminar.|  
|FailIfNotExists|Especifique si la tarea debe generar un error si no existe el clúster.|
