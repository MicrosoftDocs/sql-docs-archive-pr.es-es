---
title: MSSQL_ENG020598 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020598 error
ms.assetid: 1c3032f2-23d1-4ead-94ee-16ac4d75cd0c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8cef26001c353dea94ec9b658dfb38285231bc20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745213"
---
# <a name="mssql_eng020598"></a>MSSQL_ENG020598
    
## <a name="message-details"></a>Detalles del mensaje  
  
|||  
|-|-|  
|Nombre de producto|SQL Server|  
|Id. de evento|20598|  
|Origen de eventos|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nombre simbólico||  
|Texto del mensaje|No se encontró la fila en el suscriptor al aplicar el comando replicado.|  
  
## <a name="explanation"></a>Explicación  
 Este error se produce en la replicación transaccional si el Agente de distribución intenta actualizar una fila en el suscriptor, pero la fila se ha eliminado o se ha cambiado su clave principal. De forma predeterminada, los suscriptores de publicaciones transaccionales deben tratarse como de solo lectura, porque los cambios no se propagan de vuelta al publicador. En la replicación transaccional, los cambios de usuario deben realizarse solo en el suscriptor si se utilizan suscripciones actualizables o replicación del mismo nivel. Para obtener información acerca de estas opciones, vea [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md) y [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md).  
  
## <a name="user-action"></a>Acción del usuario  
 **Para resolver este problema:**  
  
1.  Si la replicación debe continuar mientras identifica el origen del error, especifique el parámetro **SkipErrors 20598** para el agente de distribución. Esto permite al agente omitir los cambios que provocan el error 20598, a la vez que permite que se repliquen otros cambios.  
  
2.  Identifique qué filas del suscriptor se han eliminado o tienen una clave principal distinta que las filas correspondientes en el publicador. Puede utilizar la [tablediff Utility](../../tools/tablediff-utility.md) para determinar qué filas de las bases de datos de publicaciones y suscripciones son diferentes. Para obtener información sobre el uso de esta utilidad con bases de datos replicadas, vea [Comparar tablas replicadas para buscar diferencias &#40;programación de la replicación&#41;](administration/compare-replicated-tables-for-differences-replication-programming.md).  
  
3.  Corrija las filas del suscriptor con la utilidad **tablediff** u otro método.  
  
4.  (Opcional) Quite el parámetro **- SkipErrors** .  
  
## <a name="see-also"></a>Consulte también  
 [Referencia de errores y eventos &#40;replicación&#41;](errors-and-events-reference-replication.md)  
  
  
