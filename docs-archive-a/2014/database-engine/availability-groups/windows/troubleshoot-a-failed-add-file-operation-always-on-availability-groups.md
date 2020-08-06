---
title: Solucionar problemas de una operación de agregar archivos con error (Grupos de disponibilidad AlwaysOn) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- secondary databases [SQL Server], Availability Groups
- Availability Groups [SQL Server], troubleshooting
ms.assetid: 31ceaebf-864b-4dd0-9112-0d047b0316ad
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2551080c214f18473caa71a3e17797c34fcc943a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750169"
---
# <a name="troubleshoot-a-failed-add-file-operation-alwayson-availability-groups"></a>Solucionar problemas relativos a una operación de agregar archivos con error (grupos de disponibilidad AlwaysOn)
  En algunas implementaciones de grupos de disponibilidad AlwaysOn, las rutas de acceso difieren entre el sistema que hospeda la réplica principal y los sistemas que hospedan una réplica secundaria. Si la ruta de acceso a un archivo de una operación add-file no existe en una replicación secundaria, la operación add-file se realizará correctamente en la base de datos principal. Pero la operación add-file ocasionará la suspensión de la base de datos secundaria. Esto, a su vez, hace que la réplica secundaria entre en el estado NOT SYNCHRONIZING.  
  
> [!NOTE]  
>  Se recomienda que, si es posible, la ruta de acceso de archivo (incluida la letra de unidad) de una base de datos secundaria determinada sea idéntica a la de la base de datos principal correspondiente.  
  
## <a name="problem-resolution"></a>Resolución de problemas  
 Para resolver este problema, el propietario debe completar los siguientes pasos:  
  
1.  Quitar la base de datos secundaria del grupo de disponibilidad. Para obtener más información, vea [Quitar una base de datos secundaria de un grupo de disponibilidad &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md).  
  
2.  En la base de datos secundaria existente, restaurar una copia de seguridad completa del grupo de archivos que contenga el archivo agregado a la base de datos secundaria, mediante WITH NORECOVERY y WITH MOVE (que especifica la ruta de acceso en la instancia del servidor que hospeda la réplica secundaria). Para obtener más información, vea [Restaurar una base de datos a una nueva ubicación &#40;SQL Server&#41;](../../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md).  
  
3.  Realizar una copia de seguridad del registro de transacciones que contenga la operación de agregar archivos en la base de datos principal, y restaurar manualmente la copia de seguridad de registros en la base de datos secundaria mediante WITH NORECOVERY y WITH MOVE.  
  
4.  Preparar la base de datos secundaria para volver a unirse al grupo de disponibilidad, restaurando, WITH NO RECOVERY, cualquier otra copia de seguridad de registros pendiente de la base de datos principal.  
  
5.  Volver a unir la base de datos secundaria al grupo de disponibilidad. Para obtener más información, vea [Combinar una base de datos secundaria con un grupo de disponibilidad &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).  
  
## <a name="see-also"></a>Consulte también  
 [Información general de Grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Preparar manualmente una base de datos secundaria para un grupo de disponibilidad &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)   
 [Solucionar problemas de usuarios huérfanos &#40;SQL Server&#41;](../../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md)   
 [Solucionar problemas de Grupos de disponibilidad AlwaysOn &#40;de configuración de SQL Server&#41;eliminado](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
  
