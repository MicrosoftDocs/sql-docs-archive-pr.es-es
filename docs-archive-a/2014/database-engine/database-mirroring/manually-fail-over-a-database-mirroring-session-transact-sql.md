---
title: Realizar una conmutación por error manualmente de una sesión de creación de reflejo de la base de datos (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover [SQL Server], database mirroring
- manual failover [SQL Server]
- database mirroring [SQL Server], failover
ms.assetid: 36218d61-b5f5-4194-905a-608e0e903db4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2c04ea4908ccbc4cfe4f6bb3606347dd444ef416
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663660"
---
# <a name="manually-fail-over-a-database-mirroring-session-transact-sql"></a>Realizar una conmutación por error manualmente de una sesión de creación de reflejo de la base de datos (Transact-SQL)
  Cuando la base de datos reflejada se sincroniza (es decir, cuando el estado de la base de datos es SYNCHRONIZED), el propietario de la base de datos puede iniciar una conmutación por error manual en el servidor reflejado. La conmutación por error manual solo se puede iniciar desde el servidor principal.  
  
### <a name="to-manually-fail-over-a-database-mirroring-session"></a>Para realizar una conmutación por error manual en una sesión de creación de reflejo de la base de datos  
  
1.  Conéctese al servidor principal.  
  
2.  Establezca el contexto de la base de datos en la base de datos **maestra** :  
  
     `USE master;`  
  
3.  Emita la siguiente instrucción en el servidor principal:  
  
     [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) *nombre_de_base_de_datos* SET PARTNER FAILOVER, donde *nombre_de_base_de_datos* es la base de datos reflejada.  
  
     Esto inicia una transición inmediata del servidor reflejado hacia el rol principal.  
  
 En el principal antiguo, los clientes se desconectan de la base de datos y las transacciones en curso se revierten.  
  
> [!NOTE]  
>  Las transacciones que se han preparado mediante el Coordinador de transacciones distribuidas de [!INCLUDE[msCoName](../../includes/msconame-md.md)] pero que aún no están confirmadas en el momento de la conmutación por error se consideran anuladas tras la conmutación por error de la base de datos.  
  
## <a name="see-also"></a>Consulte también  
 [Reflejo de la base de datos ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)   
 [Conmutar por error manualmente una sesión de creación de reflejo de la base de datos &#40;SQL Server Management Studio&#41;](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)   
 [Conmutación de roles durante una sesión de creación de reflejo de la base de datos &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)  
  
  
