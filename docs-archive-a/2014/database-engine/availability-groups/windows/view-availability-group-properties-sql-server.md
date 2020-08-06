---
title: Ver las propiedades del grupo de disponibilidad (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server]
ms.assetid: 61243c87-bd62-4510-863f-2a8f347caf1f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b7d1f57a9bd29b6c65160ec9a163bc77dfca48b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87671176"
---
# <a name="view-availability-group-properties-sql-server"></a><span data-ttu-id="a0965-102">Ver las propiedades del grupo de disponibilidad (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a0965-102">View Availability Group Properties (SQL Server)</span></span>
  <span data-ttu-id="a0965-103">En este tema se describe cómo pueden verse las propiedades de un grupo disponibilidad AlwaysOn con [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)] en [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a0965-103">This topic describes how to view the properties of an availability group for an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  

  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a0965-104">Uso de SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a0965-104">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="a0965-105">**Para ver y cambiar las propiedades de un grupo de disponibilidad**</span><span class="sxs-lookup"><span data-stu-id="a0965-105">**To view and change the properties an availability group**</span></span>  
  
1.  <span data-ttu-id="a0965-106">En el Explorador de objetos, conéctese a la instancia del servidor que hospeda la réplica principal y expanda el árbol.</span><span class="sxs-lookup"><span data-stu-id="a0965-106">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="a0965-107">Expanda los nodos **Alta disponibilidad de AlwaysOn** y **Grupos de disponibilidad** .</span><span class="sxs-lookup"><span data-stu-id="a0965-107">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="a0965-108">Haga clic con el botón derecho en el grupo de disponibilidad cuyas propiedades quiere ver y seleccione el comando **Propiedades** .</span><span class="sxs-lookup"><span data-stu-id="a0965-108">Right-click the availability group whose properties you want to view, and select the **Properties** command.</span></span>  
  
4.  <span data-ttu-id="a0965-109">En el cuadro de diálogo **Propiedades de grupo de disponibilidad**, use las páginas **General** y **Preferencias de copia de seguridad** para ver y, en algunos casos, cambiar las propiedades del grupo de disponibilidad seleccionado.</span><span class="sxs-lookup"><span data-stu-id="a0965-109">In the **Availability Group Properties** dialog box, use the **General** and **Backup Preferences** pages to view and, in some cases, change properties of the selected availability group.</span></span> <span data-ttu-id="a0965-110">Para más información, vea [Propiedades de grupo de disponibilidad y nuevo grupo de disponibilidad &#40;página General&#41;](availability-group-properties-new-availability-group-general-page.md) y [Propiedades de grupo de disponibilidad: Nuevo grupo de disponibilidad &#40;página Preferencias de copia de seguridad&#41;](availability-group-properties-new-availability-group-backup-preferences-page.md).</span><span class="sxs-lookup"><span data-stu-id="a0965-110">For more information, see [Availability Group Properties and New Availability Group &#40;General Page&#41;](availability-group-properties-new-availability-group-general-page.md) and [Availability Group Properties: New Availability Group &#40;Backup Preferences Page&#41;](availability-group-properties-new-availability-group-backup-preferences-page.md).</span></span>  
  
     <span data-ttu-id="a0965-111">Use la página de **Permisos** para ver los inicios de sesión, roles y permisos explícitos actuales asociados al grupo de disponibilidad.</span><span class="sxs-lookup"><span data-stu-id="a0965-111">Use the **Permissions** page to view the current logins, roles, and explicit permissions associated with the availability group.</span></span> <span data-ttu-id="a0965-112">Para más información, consulte [Permissions or Securables Page](../../../relational-databases/security/permissions-or-securables-page.md).</span><span class="sxs-lookup"><span data-stu-id="a0965-112">For more information, see [Permissions or Securables Page](../../../relational-databases/security/permissions-or-securables-page.md).</span></span>  
  

  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a0965-113">Usar Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a0965-113">Using Transact-SQL</span></span>  
 <span data-ttu-id="a0965-114">**Para ver las propiedades y el estado de un grupo de disponibilidad**</span><span class="sxs-lookup"><span data-stu-id="a0965-114">**To view the properties and state of an availability group**</span></span>  
  
 <span data-ttu-id="a0965-115">Para consultar las propiedades y los estados de los grupos de disponibilidad en los que la instancia de servidor hospeda una réplica de disponibilidad, use las vistas siguientes:</span><span class="sxs-lookup"><span data-stu-id="a0965-115">To query the properties and states of the availability groups for which the server instance hosts an availability replica, use the following views:</span></span>  
  
 [<span data-ttu-id="a0965-116">sys.availability_groups</span><span class="sxs-lookup"><span data-stu-id="a0965-116">sys.availability_groups</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)  
 <span data-ttu-id="a0965-117">Devuelve una fila para cada grupo de disponibilidad para el que la instancia local de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hospeda una réplica de disponibilidad.</span><span class="sxs-lookup"><span data-stu-id="a0965-117">Returns a row for each availability group for which the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hosts an availability replica.</span></span> <span data-ttu-id="a0965-118">Cada fila contiene una copia almacenada en caché de los metadatos del grupo de disponibilidad.</span><span class="sxs-lookup"><span data-stu-id="a0965-118">Each row contains a cached copy of the availability group metadata.</span></span>  
  
 <span data-ttu-id="a0965-119">**Nombres de columna:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference y automated_backup_preference_desc</span><span class="sxs-lookup"><span data-stu-id="a0965-119">**Column names:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc</span></span>  
  
 [<span data-ttu-id="a0965-120">sys.availability_groups_cluster</span><span class="sxs-lookup"><span data-stu-id="a0965-120">sys.availability_groups_cluster</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-cluster-transact-sql)  
 <span data-ttu-id="a0965-121">Devuelve una fila para cada grupo de disponibilidad del clúster de WSFC.</span><span class="sxs-lookup"><span data-stu-id="a0965-121">Returns a row for each availability group in the WSFC cluster.</span></span> <span data-ttu-id="a0965-122">Cada fila contiene los metadatos del grupo de disponibilidad procedentes del clúster de clústeres de conmutación por error de Windows Server (WSFC).</span><span class="sxs-lookup"><span data-stu-id="a0965-122">Each row contains the availability group metadata from the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="a0965-123">**Nombres de columna:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference y automated_backup_preference_desc</span><span class="sxs-lookup"><span data-stu-id="a0965-123">**Column names:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc</span></span>  
  
 [<span data-ttu-id="a0965-124">sys.dm_hadr_availability_group_states</span><span class="sxs-lookup"><span data-stu-id="a0965-124">sys.dm_hadr_availability_group_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql)  
 <span data-ttu-id="a0965-125">Devuelve una fila para cada grupo de disponibilidad que posee una réplica de disponibilidad en la instancia local de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a0965-125">Returns a row for each availability group that possesses an availability replica on the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a0965-126">Cada fila muestra los estados que definen el estado de un grupo de disponibilidad determinado.</span><span class="sxs-lookup"><span data-stu-id="a0965-126">Each row displays the states that define the health of a given availability group.</span></span>  
  
 <span data-ttu-id="a0965-127">**Nombres de columna:** group_id, primary_replica, primary_recovery_health, primary_recovery_health_desc, secondary_recovery_health, secondary_recovery_health_desc, synchronization_health y synchronization_health_desc</span><span class="sxs-lookup"><span data-stu-id="a0965-127">**Column names:** group_id, primary_replica, primary_recovery_health, primary_recovery_health_desc, secondary_recovery_health, secondary_recovery_health_desc, synchronization_health, synchronization_health_desc</span></span>  
  

  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="a0965-128">Tareas relacionadas</span><span class="sxs-lookup"><span data-stu-id="a0965-128">Related Tasks</span></span>  
 <span data-ttu-id="a0965-129">**Para obtener más información acerca de los grupos de disponibilidad**</span><span class="sxs-lookup"><span data-stu-id="a0965-129">**To view information about availability groups**</span></span>  
  
-   [<span data-ttu-id="a0965-130">Ver las propiedades de una réplica de disponibilidad &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a0965-130">View Availability Replica Properties &#40;SQL Server&#41;</span></span>](view-availability-replica-properties-sql-server.md)  
  
-   [<span data-ttu-id="a0965-131">Ver las propiedades del agente de escucha de grupo de disponibilidad &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a0965-131">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
-   [<span data-ttu-id="a0965-132">Directivas de AlwaysOn para problemas operativos con Grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a0965-132">AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](always-on-policies-for-operational-issues-always-on-availability.md)
  
-   [<span data-ttu-id="a0965-133">Usar el Panel de AlwaysOn &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a0965-133">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="a0965-134">Supervisar grupos de disponibilidad &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a0965-134">Monitor Availability Groups &#40;Transact-SQL&#41;</span></span>](monitor-availability-groups-transact-sql.md)  
  
 <span data-ttu-id="a0965-135">**Para configurar un grupo de disponibilidad existente**</span><span class="sxs-lookup"><span data-stu-id="a0965-135">**To configure an existing availability group**</span></span>  
  
-   [<span data-ttu-id="a0965-136">Agregar una réplica secundaria a un grupo de disponibilidad &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a0965-136">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="a0965-137">Quitar una réplica secundaria de un grupo de disponibilidad &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a0965-137">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="a0965-138">Agregar una base de datos a un grupo de disponibilidad &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a0965-138">Add a Database to an Availability Group &#40;SQL Server&#41;</span></span>](availability-group-add-a-database.md)  
  
-   [<span data-ttu-id="a0965-139">Quitar una base de datos secundaria de un grupo de disponibilidad &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a0965-139">Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="a0965-140">Crear o configurar un agente de escucha de grupo de disponibilidad &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a0965-140">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="a0965-141">Quitar un agente de escucha de grupo de disponibilidad &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a0965-141">Remove an Availability Group Listener &#40;SQL Server&#41;</span></span>](remove-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="a0965-142">Quitar una base de datos principal de un grupo de disponibilidad &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a0965-142">Remove a Primary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="a0965-143">Quitar un grupo de disponibilidad &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a0965-143">Remove an Availability Group &#40;SQL Server&#41;</span></span>](remove-an-availability-group-sql-server.md)  
  
 <span data-ttu-id="a0965-144">**Para realizar la conmutación por error manual de un grupo de disponibilidad**</span><span class="sxs-lookup"><span data-stu-id="a0965-144">**To manually fail over an availability group**</span></span>  
  
-   [<span data-ttu-id="a0965-145">Realizar una conmutación por error manual planeada de un grupo de disponibilidad &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a0965-145">Perform a Planned Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="a0965-146">Realizar una conmutación por error manual forzada de un grupo de disponibilidad &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a0965-146">Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="a0965-147">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a0965-147">See Also</span></span>  
 <span data-ttu-id="a0965-148">[Información general de Grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) supervisar grupos de disponibilidad &#40;directivas de AlwaysOn de [Transact-SQL&#41;](monitor-availability-groups-transact-sql.md) [para problemas operativos con grupos de disponibilidad AlwaysOn](always-on-policies-for-operational-issues-always-on-availability.md) &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a0965-148">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) [Monitor Availability Groups &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md) [AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md)</span></span> 
  
  
