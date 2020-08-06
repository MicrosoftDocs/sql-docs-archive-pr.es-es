---
title: MSSQL_REPL027183 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_REPL027183 error
ms.assetid: 52c271ac-1a0e-43d5-85d4-35886d1efd32
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4484318cd6ec6ff4f0b201be69dc9b7544dd2c2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750693"
---
# <a name="mssql_repl027183"></a>MSSQL_REPL027183
    
## <a name="message-details"></a>Detalles del mensaje  
  
|||  
|-|-|  
|Nombre de producto|SQL Server|  
|Id. de evento|27183|  
|Origen de eventos|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nombre simbólico||  
|Texto del mensaje|El proceso de mezcla no pudo enumerar los cambios en los artículos con filtros de fila con parámetros. Si el error persiste, aumente el tiempo de espera de consulta, reduzca el período de retención de la publicación y mejore los índices en las tablas publicadas.|  
  
## <a name="explanation"></a>Explicación  
 Este error se genera si se agota el tiempo de espera del Agente de mezcla durante el procesamiento de cambios en una publicación filtrada. Este tiempo de espera puede estar causado por uno de los siguientes problemas:  
  
-   No utilizar la optimización de particiones precalculadas.  
  
-   Fragmentar índices en las columnas empleadas para filtrar.  
  
-   Tablas de metadatos de mezcla de gran tamaño, como **MSmerge_tombstone**, **MSmerge_contents**y **MSmerge_genhistory**.  
  
-   Tablas filtradas que no están combinadas en una clave única y filtros de combinación que incluyen un gran número de tablas.  
  
## <a name="user-action"></a>Acción del usuario  
 Para resolver el problema:  
  
-   Aumente el valor del parámetro **-QueryTimeOut** para que el agente de mezcla permita que el procesamiento continúe mientras soluciona los problemas causantes del error. Los parámetros del agente se pueden especificar en los perfiles del agente y en la línea de comandos. Para más información, consulte:  
  
    -   [Trabajar con perfiles del Agente de replicación](agents/replication-agent-profiles.md)  
  
    -   [Ver y modificar parámetros del símbolo del sistema de los agentes de replicación &#40;SQL Server Management Studio&#41;](agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   [Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).  
  
-   Si es posible, utilice la optimización de particiones precalculadas. Esta optimización se utiliza de forma predeterminada si se cumplen una serie de requisitos de publicación. Para obtener más información sobre estos requisitos, vea [Optimizar el rendimiento de los filtros con parámetros con particiones calculadas previamente](merge/parameterized-filters-optimize-for-precomputed-partitions.md). Si la publicación no reúne dichos requisitos, considere la posibilidad de volver a diseñar la publicación.  
  
-   Especifique el valor más bajo posible para el período de retención de la publicación, ya que la replicación no puede limpiar los metadatos de las bases de datos de suscripciones y publicaciones hasta que se alcance el período de retención. Para más información, consulte [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).  
  
-   Como parte del mantenimiento de la replicación de mezcla, compruebe ocasionalmente el crecimiento de las tablas del sistema asociadas con la replicación de mezcla: **MSmerge_contents**, **MSmerge_genhistory**, **MSmerge_tombstone**, **MSmerge_current_partition_mappings**y **MSmerge_past_partition_mappings**. Vuelva a indizar estas tablas periódicamente. Para obtener más información, vea [Reorganizar y volver a generar índices](../indexes/indexes.md).  
  
-   Asegúrese de que las columnas utilizadas para filtrar están correctamente indizadas y vuelva a generar dichos índices en caso necesario. Para obtener más información, vea [Reorganizar y volver a generar índices](../indexes/indexes.md).  
  
-   Establezca la propiedad **join_unique_key** para los filtros combinados basados en columnas únicas. Para obtener más información, consulte [Join Filters](merge/join-filters.md).  
  
-   Limite el número de tablas de la jerarquía del filtro de combinación. Si va a generar filtros de combinación de cinco tablas o más, considere otras soluciones, como no filtrar tablas pequeñas, que no estén sometidas a cambios o que sean principalmente tablas de búsqueda. Utilice filtros combinados solo entre tablas que deben particionarse entre las suscripciones.  
  
-   Realice un número reducido de cambios en las tablas filtradas entre sincronizaciones o ejecute el Agente de mezcla con mayor frecuencia. Para obtener más información acerca de la configuración de las programaciones de sincronización, vea [Specify Synchronization Schedules](specify-synchronization-schedules.md).  
  
## <a name="see-also"></a>Consulte también  
 [Referencia de errores y eventos &#40;replicación&#41;](errors-and-events-reference-replication.md)  
  
  
