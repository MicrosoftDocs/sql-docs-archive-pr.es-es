---
title: MSSQLSERVER_41301 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41301 (Database Engine error)
ms.assetid: c6127e1e-2846-4ee9-bc42-2d896ea9730e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d4fa78b334f32033f96df002aeaf039994b396cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674142"
---
# <a name="mssqlserver_41301"></a>MSSQLSERVER_41301
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre de producto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Id. de evento|41301|  
|Origen de eventos|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|COMMIT_DEPENDENCY_FAILURE|  
|Texto del mensaje|Una transacción anterior a la transacción actual realizada en una dependencia se ha anulado y la transacción actual ya no puede confirmarse.|  
  
## <a name="explanation"></a>Explicación  
 La transacción encontró un error de dependencia y ahora está condenada.  
  
 Este error también puede producirse si hay demasiadas transacciones dependientes. Las transacciones de escritura pueden tener un número limitado de transacciones dependientes. Por ejemplo, este error puede producirse si muchas transacciones de lectura intentan depender de la transacción de actualización.  
  
## <a name="user-action"></a>Acción del usuario  
 No haga ningún trabajo en la transacción. Llame a ROLLBACK TRAN para revertir la transacción. Para obtener más información, vea [OLTP en memoria &#40;optimización en memoria&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Consulte también  
 [Habilitar y deshabilitar grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)  
  
  
