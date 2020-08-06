---
title: Combinar una base de datos secundaria con un grupo de disponibilidad (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.joindbs.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- secondary databases [SQL Server]
- Availability Groups [SQL Server], joining
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: fd7efe79-c1f9-497d-bfe7-b2a2b2321cf5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b0d79325bcde33d13688003de079a42a9601cc41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672263"
---
# <a name="join-a-secondary-database-to-an-availability-group-sql-server"></a>Combinar una base de datos secundaria con un grupo de disponibilidad (SQL Server)
  En este tema se explica cómo combinar una base de datos secundaria con un grupo de disponibilidad de AlwaysOn mediante [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]o PowerShell en [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Después de preparar una base de datos secundaria para una réplica de disponibilidad secundaria, debe combinar la base de datos con el grupo de disponibilidad lo antes posible. Se iniciará el movimiento de datos de la base de datos principal correspondiente a la base de datos secundaria.  
  
-   **Antes de empezar:**  
  
     [Requisitos previos](#Prerequisites)  
  
     [Seguridad](#Security)  
  
-   **Para preparar una base de datos secundaria, utilizando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
> [!NOTE]  
>  Para obtener información acerca de lo que sucede después de que una base de datos secundaria se une al grupo, consulte [información general de Grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Requisitos previos  
  
-   Debe estar conectado a la instancia del servidor que hospeda la réplica secundaria.  
  
-   La réplica secundaria ya debe estar unida al grupo de disponibilidad. Para obtener más información, vea [Combinar una réplica secundaria con un grupo de disponibilidad &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
-   La base de datos secundaria debe haberse preparado recientemente. Para obtener más información, vea [Preparar manualmente una base de datos secundaria para un grupo de disponibilidad &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
###  <a name="security"></a><a name="Security"></a> Seguridad  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permisos  
 Se requiere el permiso ALTER AVAILABILITY GROUP en el grupo de disponibilidad, el permiso CONTROL AVAILABILITY GROUP, el permiso ALTER ANY AVAILABILITY GROUP o el permiso CONTROL SERVER.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Uso de SQL Server Management Studio  
 **Para combinar una base de datos secundaria con un grupo de disponibilidad**  
  
1.  En el Explorador de objetos, conéctese a la instancia del servidor que hospeda la réplica secundaria y expanda el árbol de servidores.  
  
2.  Expanda los nodos **Alta disponibilidad de AlwaysOn** y **Grupos de disponibilidad** .  
  
3.  Expanda el grupo de disponibilidad que desea cambiar y expanda el nodo **Bases de datos de disponibilidad** .  
  
4.  Haga clic con el botón derecho en la base de datos y haga clic en **Combinar con grupo de disponibilidad**.  
  
5.  Se abrirá el cuadro de diálogo **Combinar bases de datos con el grupo de disponibilidad** . Compruebe el nombre del grupo de disponibilidad, que se muestra en la barra de título, y el nombre o nombres de base de datos mostrados en la cuadrícula, y haga clic en **Aceptar**o en **Cancelar**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Usar Transact-SQL  
 **Para combinar una base de datos secundaria con un grupo de disponibilidad**  
  
1.  Conéctese a la instancia del servidor que hospeda la réplica secundaria.  
  
2.  Utilice la cláusula [SET HADR de la instrucción ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) del siguiente modo:  
  
     ALTER DATABASE *nombre_baseDeDatos* SET HADR AVAILABILITY GROUP = *nombre_grupo*  
  
     donde *nombre_BaseDeDatos* es el nombre de la base de datos que se va a unir y *nombre_grupo* es el nombre del grupo de disponibilidad.  
  
     En el ejemplo siguiente se une la base de datos secundaria `Db1` a la réplica secundaria local del grupo de disponibilidad `MyAG`.  
  
    ```sql
    ALTER DATABASE Db1 SET HADR AVAILABILITY GROUP = MyAG;  
    ```  
  
    > [!NOTE]  
    >  Para ver esta instrucción [!INCLUDE[tsql](../../../includes/tsql-md.md)] usada en contexto, vea [Crear un grupo de disponibilidad &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md).  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Con PowerShell  
 **Para combinar una base de datos secundaria con un grupo de disponibilidad**  
  
1.  Cambie el directorio (`cd`) a la instancia del servidor que hospeda la réplica secundaria.  
  
2.  Utilice el cmdlet `Add-SqlAvailabilityDatabase` para unir una o más bases de datos secundarias al grupo de disponibilidad.  
  
     Por ejemplo, el comando siguiente une una base de datos secundaria `Db1`al grupo de disponibilidad `MyAG` en una de las instancias de servidor que hospeda una réplica secundaria.  
  
    ```powershell
    Add-SqlAvailabilityDatabase -Path SQLSERVER:\SQL\SecondaryServer\InstanceName\AvailabilityGroups\MyAG -Database "Db1"  
    ```  
  
    > [!NOTE]  
    >  Para ver la sintaxis de un cmdlet, use el cmdlet `Get-Help` en el entorno de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Para más información, consulte [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Para configurar y usar el proveedor de SQL Server PowerShell**  
  
-   [Proveedor de SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tareas relacionadas  
  
-   [Combinar una réplica secundaria con un grupo de disponibilidad &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Preparar manualmente una base de datos secundaria para un grupo de disponibilidad &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a>Consulte también  
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql)   
 [Información general de Grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Solucionar problemas de Grupos de disponibilidad AlwaysOn &#40;de configuración de SQL Server&#41;eliminado](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
