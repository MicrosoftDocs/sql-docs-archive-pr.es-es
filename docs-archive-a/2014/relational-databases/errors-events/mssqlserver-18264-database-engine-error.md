---
title: MSSQLSERVER_18264 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18264 (Database Engine error)
ms.assetid: 3050fc56-2be5-43cf-916b-50a3ac5f89aa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3edfeb82601e254c02df87cc4a978b9ab5e653e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674139"
---
# <a name="mssqlserver_18264"></a>MSSQLSERVER_18264
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre de producto|Microsoft SQL Server|  
|Id. de evento|18264|  
|Origen de eventos|MSSQLENGINE|  
|Componente|SQLEngine|  
|Nombre simbólico|STRMIO_DBDUMP|  
|Texto del mensaje|Se ha realizado una copia de seguridad de la base de datos. Base de datos: %s, fecha de creación (tiempo): %s(%s), páginas volcadas: %d, primer LSN: %s, último LSN: %s, número de dispositivos de volcado: %d, información del dispositivo: (%s). Esto es solo un mensaje informativo. No se requiere ninguna acción del usuario.|  
  
## <a name="explanation"></a>Explicación  
 De forma predeterminada, cada copia de seguridad correcta agrega este mensaje informativo al registro de errores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y al registro de eventos del sistema. Si hace una copia de seguridad del registro de transacciones con frecuencia, estos mensajes pueden acumularse rápidamente y crear registros de errores muy grandes, que pueden dificultar la búsqueda de otros mensajes.  
  
## <a name="user-action"></a>Acción del usuario  
 Puede suprimir estas entradas de registro usando la marca de seguimiento de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**3226**. Habilitar esta marca de seguimiento es útil si ejecuta frecuentemente copias de seguridad de los registros y ninguno de los scripts depende de esas entradas.  
  
 Para obtener información sobre cómo usar marcas de seguimiento, vea los Libros en pantalla de SQL Server.  
  
## <a name="see-also"></a>Consulte también  
 [Marcas de seguimiento &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)  
  
  
