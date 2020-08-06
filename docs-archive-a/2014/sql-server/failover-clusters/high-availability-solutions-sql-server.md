---
title: Soluciones de alta disponibilidad (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- high availability [SQL Server], solutions
- Database Engine [SQL Server], availability
- database availability [SQL Server]
- availability [SQL Server]
- server availability [SQL Server]
ms.assetid: b2eda634-0f8e-4703-801b-7ba895544ff5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 83e7dde423fadcc0cd7d4d34dd4fd05b460cf453
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672593"
---
# <a name="high-availability-solutions-sql-server"></a>Soluciones de alta disponibilidad (SQL Server)
  En este tema se presentan varias soluciones de alta disponibilidad de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que mejoran la disponibilidad de los servidores o las bases de datos. Una solución de alta disponibilidad enmascara los efectos de un error de hardware o software y mantiene la disponibilidad de las aplicaciones a fin de minimizar el tiempo de inactividad que perciben los usuarios.  
  
> [!NOTE]  
>  Para más información sobre qué ediciones de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] admiten una solución de alta disponibilidad determinada, vea la sección sobre alta disponibilidad AlwaysOn de [Características compatibles con las ediciones de SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
(#RecommendedSolutions)  
  
##  <a name="overview-of-sql-server-high-availability-solutions"></a><a name="TermsAndDefinitions"></a> Información general de las soluciones de alta disponibilidad de SQL Server  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ofrece varias opciones para crear alta disponibilidad para un servidor o una base de datos. Entre las opciones de alta disponibilidad figuran las siguientes:  
  
 Instancias de clúster de conmutación por error de AlwaysOn  
 Como parte de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oferta de AlwaysOn, las instancias de clúster de conmutación por error de AlwaysOn aprovechan la funcionalidad de clústeres de conmutación por error de Windows Server (WSFC) para proporcionar alta disponibilidad local mediante redundancia en el nivel de instancia de servidor, una *instancia de clúster de conmutación por error* (FCI). Una FCI es una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que se instala a través de los nodos de Clústeres de conmutación por error de Windows Server (WSFC) y, posiblemente, a través de varias subredes. En la red, una FCI aparece como una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que se ejecuta en un equipo individual, pero proporciona la conmutación por error entre nodos de WSFC si el nodo actual deja de estar disponible.  
  
 Para obtener más información, vea [Always On Failover Cluster Instances (SQL Server)](windows/always-on-failover-cluster-instances-sql-server.md) (Instancias de clúster de conmutación por error de Always On [SQL Server]).  
  
 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]  
 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] es una solución de alta disponibilidad y recuperación ante desastres de nivel empresarial presentada en [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] que permite maximizar la disponibilidad para una o varias bases de datos de usuario. [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] necesita que las instancias de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se encuentren en nodos de Clústeres de conmutación por error de Windows Server (WSFC). Para obtener más información, consulte [Grupos de disponibilidad AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md).  
  
> [!NOTE]  
>  Una FCI puede aprovechar las ventajas de [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] para proporcionar recuperación remota ante desastres en la base de datos. Para más información, vea [Clúster de conmutación por error y grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md).  
  
 Creación de reflejo de la base de datos  
 > [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Se recomienda utilizar [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] en su lugar.  
  
 La creación de reflejo de la base de datos es una solución para aumentar la disponibilidad de la base de datos mediante una conmutación por error casi inmediata. La creación de reflejo de la base de datos puede utilizarse para mantener una sola base de datos en estado de espera, o *base de datos reflejada*, para una base de datos de producción correspondiente a la que se conoce como *base de datos principal*. Para obtener más información, vea [Creación de reflejo de la base de datos &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
 Trasvase de registros  
 Al igual que [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] y la creación de reflejo de la base de datos, el trasvase de registros se aplica en la base de datos. Puede usar el trasvase de registros para mantener una o varias bases de datos en estado de espera activa (denominadas *bases de datos secundarias*) para una sola base de datos de producción denominada *base de datos principal*. Para obtener más información sobre el trasvase de registros, vea [Acerca del trasvase de registros &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).  
  
##  <a name="recommended-solutions-for-using-sql-server-to-protect-data"></a><a name="RecommendedSolutions"></a> Soluciones recomendadas para utilizar SQL Server para proteger datos  
 Esta es nuestra recomendación para proporcionar protección de datos en el entorno de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   Para la protección de datos en una solución de disco compartido de otro fabricante (una SAN), se recomienda utilizar las instancias de clúster de conmutación por error de AlwaysOn.  
  
-   Para la protección de datos en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], se recomienda utilizar [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].  
  
    > [!NOTE]  
    >  Si ejecuta una edición de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que no admite [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], se recomienda el trasvase de registros. Para más información sobre qué ediciones de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] admiten [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], vea la sección sobre alta disponibilidad AlwaysOn de [Características compatibles con las ediciones de SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="see-also"></a>Consulte también  
 [Clústeres de conmutación por error de Windows Server &#40;WSFC&#41; con SQL Server](windows/windows-server-failover-clustering-wsfc-with-sql-server.md)   
 [Creación de reflejo de la base de datos: interoperabilidad y coexistencia &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-interoperability-and-coexistence-sql-server.md)   
 [Características desusadas del motor de base de datos de SQL Server 2014](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)  
  
  
