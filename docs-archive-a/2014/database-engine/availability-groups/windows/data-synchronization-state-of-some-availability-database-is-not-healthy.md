---
title: El estado de sincronización de datos de alguna base de datos de disponibilidad no es correcto | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.drp3datasynchealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 89f95d15-33c6-4768-bccd-9dbf8c4f49a9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 221f25a1ee7e4a8719acc133372c742ca4a79303
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87752334"
---
# <a name="data-synchronization-state-of-some-availability-database-is-not-healthy"></a>El estado de sincronización de datos de alguna base de datos de disponibilidad no está en buen estado
    
## <a name="introduction"></a>Introducción  
  
|||  
|-|-|  
|**Nombre de directiva**|Estado de sincronización de datos de las réplicas de disponibilidad|  
|**Problema**|El estado de sincronización de datos de alguna base de datos de disponibilidad no es correcto.|  
|**Categoría**|**Warning (ADVERTENCIA)**|  
|**Faceta**|réplica de disponibilidad|  
  
## <a name="description"></a>Descripción  
 Esta directiva comprueba el estado de sincronización de datos de la base de datos de disponibilidad (también denominada “réplica de base de datos”). La directiva está en mal estado cuando el estado de sincronización de datos es NOT SYNCHRONIZING o cuando no es SYNCHRONIZED para la réplica de base de datos de confirmación sincrónica.  
  
> [!NOTE]  
>  Para esta versión de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], la información sobre las posibles causas y soluciones se encuentra en [El estado de sincronización de datos de la base de datos de disponibilidad no es correcto](https://go.microsoft.com/fwlink/p/?LinkId=220863) en la wiki de TechNet.  
  
## <a name="possible-causes"></a>Causas posibles  
 Al menos una base de datos de disponibilidad en la réplica tiene un estado incorrecto de sincronización de datos. Si se trata de una réplica de disponibilidad de confirmación asincrónica, todas las bases de datos de disponibilidad deben estar en el estado SYNCHRONIZING. Si se trata de una réplica de disponibilidad de confirmación sincrónica, todas las bases de datos de disponibilidad deben estar en el estado SYNCHRONIZED. Este problema puede deberse a lo siguiente:  
  
-   La réplica de disponibilidad puede estar desconectada.  
  
-   El movimiento de datos puede haberse suspendido.  
  
-   La base de datos no está accesible.  
  
-   Puede haber un problema de retraso temporal debido a la latencia de red o a la carga en la réplica principal o secundaria.  
  
## <a name="possible-solution"></a>Solución posible  
 Resuelva cualquier problema de suspensión de conexión o de movimiento de datos. Compruebe los eventos correspondientes a este problema mediante SQL Server Management Studio y busque el error de la base de datos. Realice los siguientes pasos para solucionar problemas del error concreto.  
  
## <a name="see-also"></a>Consulte también  
 [Información general de Grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Usar el Panel de AlwaysOn &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
