---
title: MSSQL_ENG021286 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021286 error
ms.assetid: b63620b7-1c6d-46f7-90ea-3a8e99af8de4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 592c788b563046e5949217c94006de2d4755f049
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745208"
---
# <a name="mssql_eng021286"></a>MSSQL_ENG021286
    
## <a name="message-details"></a>Detalles del mensaje  
  
|||  
|-|-|  
|Nombre de producto|SQL Server|  
|Id. de evento|21286|  
|Origen de eventos|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nombre simbólico||  
|Texto del mensaje|La tabla de conflictos '%1!' no existe.|  
  
## <a name="explanation"></a>Explicación  
 Este error se produce si la tabla de conflictos de un artículo mencionado en [sysmergearticles &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/sysmergearticles-transact-sql) no existe realmente. El error se puede producir al intentar agregar o quitar una columna de una tabla publicada para la replicación de mezcla.  
  
## <a name="user-action"></a>Acción del usuario  
 Ejecute [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) en la base de datos donde falta la tabla en conflicto para comprobar que no existen problemas de coherencia de datos.  
  
 Si la tabla de conflictos falta en un suscriptor, quite y vuelva a crear la suscripción. Si la tabla de conflictos falta en un publicador, quite todas las suscripciones, quite la publicación y vuelva a crear la publicación y todas las suscripciones. Para obtener más información sobre la creación de publicación, vea [Publicar datos y objetos de base de datos](publish/publish-data-and-database-objects.md) y [Suscribirse a publicaciones](subscribe-to-publications.md).  
  
## <a name="see-also"></a>Consulte también  
 [Referencia de errores y eventos &#40;replicación&#41;](errors-and-events-reference-replication.md)  
  
  
