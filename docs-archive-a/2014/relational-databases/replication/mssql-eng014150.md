---
title: MSSQL_ENG014150 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014150 error
ms.assetid: c3dd3109-abf3-4b38-a4e9-ef48d0235656
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4c926d05be9613ff559f119484fa5e238d71d861
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662828"
---
# <a name="mssql_eng014150"></a>MSSQL_ENG014150
    
## <a name="message-details"></a>Detalles del mensaje  
  
|||  
|-|-|  
|Nombre de producto|SQL Server|  
|Id. de evento|14150|  
|Origen de eventos|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nombre simbólico||  
|Texto del mensaje|Replicación-%s: el agente %s se ejecutó correctamente. %s|  
  
## <a name="explanation"></a>Explicación  
 Este mensaje indica que un agente de replicación ha finalizado la ejecución correctamente. La replicación usa los siguientes agentes:  
  
-   Agente de instantáneas. Todas las publicaciones usan este agente.  
  
-   Agente de registro del LOG. Todas las publicaciones transaccionales usan este agente.  
  
-   Agente de lectura de cola. Todas las publicaciones transaccionales habilitadas para las suscripciones de actualización en cola usan este agente.  
  
-   Agente de distribución. Este agente sincroniza las suscripciones a publicaciones transaccionales y publicaciones de instantáneas.  
  
-   Agente de mezcla. Este agente sincroniza las suscripciones a publicaciones de combinación.  
  
-   Trabajos de mantenimiento de la replicación.  
  
## <a name="user-action"></a>Acción del usuario  
 El Agente de registro del LOG, el Agente de lectura de cola y el Agente de distribución se ejecutan normalmente de forma continua, mientras que el resto de agentes se ejecutan normalmente a petición o en función de una programación. Si no espera que un agente haya completado una ejecución, compruebe el estado del agente. Para más información, consulte [Monitor Replication Agents](agents/replication-agents-overview.md).  
  
## <a name="see-also"></a>Consulte también  
 [Administración del Agente de replicación](agents/replication-agent-administration.md)   
 [Referencia de errores y eventos &#40;replicación&#41;](errors-and-events-reference-replication.md)   
 [Replication Distribution Agent](agents/replication-distribution-agent.md)   
 [Replication Log Reader Agent](agents/replication-log-reader-agent.md)   
 [Replication Merge Agent](agents/replication-merge-agent.md)   
 [Agente de lectura de cola de replicación](agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](agents/replication-snapshot-agent.md)  
  
  
