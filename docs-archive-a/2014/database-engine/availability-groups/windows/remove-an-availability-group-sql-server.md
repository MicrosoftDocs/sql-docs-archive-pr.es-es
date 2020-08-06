---
title: Quitar un grupo de disponibilidad (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.deleteag.f1
helpviewer_keywords:
- Availability Groups [SQL Server], removing
- Availability Groups [SQL Server], dropping
ms.assetid: 4b7f7f62-43a3-49db-a72e-22d4d7c2ddbb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c17b7d5b362d8b4030d66ebf7ba0e425495410e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87670593"
---
# <a name="remove-an-availability-group-sql-server"></a>Quitar un grupo de disponibilidad (SQL Server)
  En este tema se describe cómo eliminar (quitar) un grupo de disponibilidad de AlwaysOn mediante [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]o PowerShell en [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Si una instancia del servidor que hospeda una de las réplicas de disponibilidad está sin conexión al eliminar un grupo de disponibilidad, después de ponerse en línea, la instancia del servidor quitará la réplica de disponibilidad local. Quitar una disponibilidad del grupo elimina cualquier escucha de grupo de disponibilidad asociada.  
  
 Observe que, si es necesario, puede quitar un grupo de disponibilidad de cualquier nodo de clústeres de conmutación por error de Windows Server (WSFC) que posea las credenciales de seguridad correctas para el grupo de disponibilidad. Esto permite eliminar un grupo de disponibilidad cuando ninguna de sus réplicas de disponibilidad permanece.  
  
> [!IMPORTANT]  
>  Si es posible, quite el grupo de disponibilidad solo mientras esté conectado a la instancia de servidor que hospeda la réplica principal. Cuando el grupo de disponibilidad se quita de la réplica principal, se permiten cambios en las bases de datos principales anteriores (sin protección de alta disponibilidad). Al eliminar un grupo de disponibilidad de una réplica secundaria, la réplica principal queda en el estado RESTORING y no se permiten cambios en las bases de datos.  
  
-   **Antes de empezar:**  
  
     [Limitaciones y recomendaciones](#Restrictions)  
  
     [Seguridad](#Security)  
  
-   **Para eliminar un grupo de disponibilidad, use:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   [Contenido relacionado](#RelatedContent)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="limitations-and-recommendations"></a><a name="Restrictions"></a>Limitaciones y recomendaciones  
  
-   Cuando el grupo de disponibilidad está en línea, su eliminación de una réplica secundaria hace que la réplica principal pase al estado RESTORING. Por lo tanto, si es posible, quite el grupo de disponibilidad solo de la instancia de servidor que hospeda la réplica principal.  
  
-   Si elimina un grupo de disponibilidad de un equipo que se ha quitado o desalojado del clúster de conmutación por error de WSFC, el grupo de disponibilidad se elimina solo localmente.  
  
-   Evite quitar un grupo de disponibilidad cuando el clúster de Clústeres de conmutación por error de Windows Server (WSFC) no tiene quórum. Si debe quitar un grupo de disponibilidad mientras el clúster no tiene quórum, el grupo de disponibilidad de metadatos que se almacena en el clúster no se quita. Cuando el clúster recupere el quórum, necesitará volver a quitar el grupo de disponibilidad para quitarlo del clúster de WSFC.  
  
-   En una réplica secundaria, DROP AVAILABILITY GROUP solo se debe usar en caso de emergencia. Esto se debe a que al quitar un grupo de disponibilidad este se queda sin conexión. Si quita el grupo de disponibilidad de una réplica secundaria, la réplica principal no puede determinar si el estado OFFLINE se debió a la pérdida del quórum, a una conmutación por error forzada o a un comando DROP AVAILABILITY GROUP. La réplica principal cambia al estado RESTORING para impedir una posible situación de división de cerebro. Para obtener más información, vea [How It Works: DROP AVAILABILITY GROUP Behaviors (Cómo funciona: comportamientos de DROP AVAILABILITY GROUP)](https://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) (blog de los ingenieros de SQL Server de CSS).  
  
###  <a name="security"></a><a name="Security"></a> Seguridad  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permisos  
 Se requiere el permiso ALTER AVAILABILITY GROUP en el grupo de disponibilidad, el permiso CONTROL AVAILABILITY GROUP, el permiso ALTER ANY AVAILABILITY GROUP o el permiso CONTROL SERVER. Para quitar un grupo de disponibilidad que no se encuentre hospedado en la instancia del servidor local se necesita el permiso CONTROL SERVER o el permiso CONTROL en ese grupo de disponibilidad.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Uso de SQL Server Management Studio  
 **Para eliminar un grupo de disponibilidad**  
  
1.  En el Explorador de objetos, conéctese a la instancia de servidor que hospeda la réplica principal, si es posible, o conéctese a otra instancia de servidor habilitada para los grupos de disponibilidad de AlwaysOn en un nodo de WSFC propietario de las credenciales de seguridad correctas para el grupo de disponibilidad. Expanda el árbol de servidores.  
  
2.  Expanda los nodos **Alta disponibilidad de AlwaysOn** y **Grupos de disponibilidad** .  
  
3.  Este paso depende de si desea eliminar varios grupos de disponibilidad o solo un grupo de disponibilidad, como se indica a continuación:  
  
    -   Para eliminar varios grupos de disponibilidad (cuyas réplicas principales están en la instancia de servidor conectada), use el panel **Detalles del Explorador de objetos** para ver y seleccionar todos los grupos de disponibilidad que quiera eliminar. Para obtener más información, vea [Usar los detalles del Explorador de objetos para supervisar los grupos de disponibilidad &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md).  
  
    -   Para eliminar un solo grupo de disponibilidad, selecciónelo en el panel **Explorador de objetos** o **Detalles del Explorador de objetos** .  
  
4.  Haga clic con el botón derecho en el grupo o grupos de disponibilidad seleccionados y seleccione el comando **Eliminar** .  
  
5.  En el cuadro de diálogo **Quitar grupo de disponibilidad** , para eliminar todos los grupos de disponibilidad de la lista, haga clic en **Aceptar**. Si no desea quitar todos los grupos de disponibilidad de la lista, haga clic en **Cancelar**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Usar Transact-SQL  
 **Para eliminar un grupo de disponibilidad**  
  
1.  Conéctese a la instancia de servidor que hospeda la réplica principal, si es posible, o conéctese a otra instancia de servidor habilitada para los grupos de disponibilidad de AlwaysOn en un nodo de WSFC propietario de las credenciales de seguridad correctas para el grupo de disponibilidad.  
  
2.  Use la instrucción [DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql) del siguiente modo  
  
     DROP AVAILABILITY GROUP *group_name*  
  
     donde *group_name* es el nombre del grupo de disponibilidad que se va a quitar.  
  
     En el ejemplo siguiente se elimina el grupo de disponibilidad `MyAG` .  
  
    ```sql
    DROP AVAILABILITY GROUP MyAG;  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Con PowerShell  
 **Para eliminar un grupo de disponibilidad**  
  
 En el proveedor de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell:  
  
1.  Cambie el directorio (`cd`) a la instancia de servidor que hospeda la réplica principal, si es posible, o conéctese a otra instancia de servidor habilitada para los grupos de disponibilidad de AlwaysOn en un nodo de WSFC propietario de las credenciales de seguridad correctas para el grupo de disponibilidad.  
  
2.  Use el cmdlet **Remove-SqlAvailabilityGroup** .  
  
     Por ejemplo, el comando siguiente quita el grupo de disponibilidad denominado `MyAg`. Este comando se puede ejecutar en cualquier instancia de servidor que hospede una réplica de disponibilidad para el grupo de disponibilidad.  
  
    ```powershell
    Remove-SqlAvailabilityGroup -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg  
    ```  
  
    > [!NOTE]  
    >  Para ver la sintaxis de un cmdlet, use el cmdlet `Get-Help` en el entorno de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Para más información, consulte [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Para configurar y usar el proveedor de SQL Server PowerShell**  
  
-   [Proveedor de SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Contenido relacionado  
  
-   [How It Works: DROP AVAILABILITY GROUP Behaviors (Cómo funciona: comportamientos de DROP AVAILABILITY GROUP)](https://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) (blog de los ingenieros de SQL Server de CSS)  
  
## <a name="see-also"></a>Consulte también  
 [Información general de Grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Creación y configuración de grupos de disponibilidad &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md)  
