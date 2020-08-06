---
title: Suscribirse a publicaciones | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.conc.subtopubs.f1
helpviewer_keywords:
- subscriptions [SQL Server replication], about subscriptions
- pull subscriptions [SQL Server replication]
- subscriptions [SQL Server replication]
- push subscriptions [SQL Server replication], about push subscriptions
- merge replication subscribing [SQL Server replication]
- merge replication subscribing [SQL Server replication], about subscribing
- publications [SQL Server replication], subscribing
- push subscriptions [SQL Server replication]
- pull subscriptions [SQL Server replication], about pull subscriptions
- snapshot replication [SQL Server], subscribing
- transactional replication, subscribing
ms.assetid: 088ee30a-05ab-47c4-92ed-316b93e12445
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c565aae26c6d549eb67043168797d5fb059c8e2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662775"
---
# <a name="subscribe-to-publications"></a>Suscribirse a publicaciones
  Una suscripción es una solicitud de copia de datos y objetos de base de datos en una publicación. Una suscripción define qué publicación se recibirá, dónde y cuándo. Al planear suscripciones, tenga en cuenta dónde se realizará el proceso del agente. El tipo de suscripción que elige controla dónde se ejecuta el agente. Con una suscripción de inserción, el Agente de mezcla o el Agente de distribución se ejecutan en el distribuidor, mientras que en una suscripción de extracción los agentes se ejecutan en los suscriptores. Después de crear una suscripción, no se puede cambiar de un tipo a otro.  
  
|Suscripción|Características|Se utiliza si|  
|------------------|---------------------|--------------|  
|Suscripción de inserción|Con una suscripción de inserción, el publicador propaga los cambios al suscriptor sin que éste lo solicite. Los cambios pueden insertarse en los suscriptores a petición, de manera continua o según una programación. De forma predeterminada, el Agente de distribución o el Agente de mezcla se ejecutan en el distribuidor.|Normalmente, los datos se sincronizarán de forma continua o con una frecuencia determinada.<br /><br /> Las publicaciones requieren que el movimiento de datos sea casi en tiempo real.<br /><br /> La sobrecarga del procesador en el distribuidor no afecta al rendimiento.<br /><br /> Se utiliza frecuentemente en la replicación de instantáneas y transaccional.|  
|Suscripción de extracción|En una suscripción de extracción, el suscriptor solicita los cambios efectuados en el publicador. Las suscripciones de extracción permiten al usuario del suscriptor determinar cuándo se sincronizan los cambios en los datos. El Agente de distribución o el Agente de mezcla se ejecutan en el suscriptor.|Los datos se sincronizarán, generalmente, a petición o en función de una programación, en lugar de hacerlo de forma continuada.<br /><br /> La publicación dispone de un gran número de suscriptores y/o la ejecución de todos los agentes en el distribuidor supone un uso demasiado intensivo de recursos.<br /><br /> Los suscriptores son autónomos, están desconectados o se desplazan. Los suscriptores determinan cuándo se conectarán y sincronizarán los cambios.<br /><br /> Se utiliza frecuentemente en la replicación de mezcla.|  
  
## <a name="merge-replication-subscription-types"></a>Tipos de suscripción de replicación de mezcla  
 Todos los tipos de replicación permiten suscripciones de inserción y extracción. La replicación de mezcla utiliza dos términos adicionales para distinguir las suscripciones: suscripciones de cliente y suscripciones de servidor. Ambos tipos de suscripción se pueden utilizar con suscripciones de inserción o extracción. Las suscripciones de cliente son adecuadas para la mayoría de suscriptores, mientras que las suscripciones de servidor se utilizan normalmente en suscriptores que vuelven a publicar datos en otros suscriptores. La elección de la suscripción también afecta a la resolución de conflictos.  
  
## <a name="non-sql-server-subscribers"></a>suscriptores que no son de SQL Server  
 Oracle e IBM DB2 pueden suscribirse a publicaciones de instantáneas y transaccionales con suscripciones de inserción. Para más información, consulte [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md).  
  
## <a name="creating-subscriptions"></a>Crear suscripciones  
 Para crear una suscripción, proporcione la siguiente información:  
  
-   Nombre de la publicación.  
  
-   El nombre del suscriptor y la base de datos de suscripciones.  
  
-   Si el Agente de distribución o el Agente de mezcla se ejecutan en el distribuidor o en el suscriptor.  
  
-   Si el Agente de distribución o el Agente de mezcla se ejecutan de forma continua, programada o solamente a petición.  
  
-   Si el Agente de instantáneas debe crear una instantánea inicial para la suscripción y si el Agente de distribución o el Agente de mezcla debe aplicar esa instantánea en el suscriptor.  
  
-   Las cuentas con la que se ejecutará el Agente de distribución o el Agente de mezcla.  
  
-   En la replicación de mezcla, el tipo de suscripción: servidor o cliente.  
  
 **Para crear una suscripción de inserción**  
  
 [Create a Push Subscription](create-a-push-subscription.md) (Creación de una suscripción de inserción)  
  
 **Para ver o modificar las propiedades de una suscripción de inserción**  
  
 [Ver y modificar las propiedades de una suscripción de inserción](view-and-modify-push-subscription-properties.md)  
  
 **Para eliminar una suscripción de inserción**  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Eliminar una suscripción de inserción](delete-a-push-subscription.md)  
  
> [!NOTE]  
>  Al eliminar una suscripción no se quitan los objetos publicados del suscriptor.  
  
 **Para crear una suscripción de extracción**  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Crear una suscripción de extracción](create-a-pull-subscription.md)  
  
 **Para ver o modificar las propiedades de una suscripción de extracción**  
  
 [Ver y modificar las propiedades de una suscripción de extracción](view-and-modify-pull-subscription-properties.md)  
  
 **Para eliminar una suscripción de extracción**  
  
 [Eliminar una suscripción de extracción](delete-a-pull-subscription.md)  
  
## <a name="see-also"></a>Consulte también  
 [Proteger el suscriptor](security/secure-the-subscriber.md)   
 [Desactivación y expiración de la suscripción](subscription-expiration-and-deactivation.md)  
  
  
