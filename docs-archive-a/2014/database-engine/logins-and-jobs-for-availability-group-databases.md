---
title: Administración de inicios de sesión y trabajos para las bases de datos de un grupo de disponibilidad (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], failover
- failover [SQL Server], AlwaysOn Availability Groups
ms.assetid: d7da14d3-848c-44d4-8e49-d536a1158a61
author: rothja
ms.author: jroth
ms.openlocfilehash: 457f3ef946b5cfaf86a4a19774af63c5d7635882
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87677819"
---
# <a name="management-of-logins-and-jobs-for-the-databases-of-an-availability-group-sql-server"></a>Administración de inicios de sesión y de trabajos para las bases de datos de un grupo de disponibilidad (SQL Server)
  Debe mantener de forma sistemática el mismo conjunto de inicios de sesión de usuario y de trabajos del Agente [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] en cada base de datos principal de un grupo de disponibilidad AlwaysOn y sus correspondientes bases de datos secundarias. Los inicios de sesión y los trabajos se deben reproducir en cada instancia de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] que hospede una réplica de disponibilidad para el grupo de disponibilidad.  
  
-   **[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Trabajos del agente**  
  
     Debe copiar manualmente los trabajos pertinentes de la instancia de servidor que hospeda la réplica principal original a las instancias de servidor que hospedan las réplicas secundarias originales. Para todas las bases de datos, debe agregar lógica al principio de cada trabajo importante para que el trabajo solo se ejecute en la base de datos principal; es decir, solo cuando la réplica local sea la réplica principal de la base de datos.  
  
     Las instancias de servidor que hospedan las réplicas de disponibilidad de un grupo de disponibilidad se pueden configurar de forma diferente, con letras de unidad de cinta distintas, etc. Los trabajos para cada réplica de disponibilidad deben permitir tales diferencias.  
  
     Cabe mencionar que los trabajos de copia de seguridad pueden usar la función [sys.fn_hadr_is_preferred_backup_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) para identificar si la réplica local es la preferida para las copias de seguridad, según las preferencias de copia de seguridad del grupo de disponibilidad. Los trabajos de copia de seguridad creados mediante el [Asistente para planes de mantenimiento](../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md) usan esta función de forma nativa. Para otros trabajos de copia de seguridad, se recomienda usar esta función como condición de los trabajos de copia de seguridad, de forma que solo se ejecuten en la réplica preferida. Para obtener más información, vea [secundarias activas: copia de seguridad en las réplicas secundarias (grupos de disponibilidad AlwaysOn)](availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).  
  
-   **Inicios de sesión**  
  
     Si usa bases de datos independientes, puede configurar usuarios independientes en las bases de datos, y para estos usuarios no es necesario crear inicios de sesión en las instancias de servidor que hospedan una réplica secundaria. En el caso de una base de datos de disponibilidad dependiente, deberá crear usuarios para los inicios de sesión en las instancias de servidor que hospedan las réplicas de disponibilidad. Para obtener más información, vea [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).  
  
     Si ninguna de las aplicaciones usa la autenticación [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] o un inicio de sesión local de Windows, vea [Inicios de sesión de aplicaciones que usan la autenticación de SQL Server o un inicio de sesión local de Windows](../../2014/database-engine/logins-and-jobs-for-availability-group-databases.md#SSauthentication), más adelante en este tema.  
  
    > [!NOTE]  
    >  Un usuario de base de datos cuyo inicio de sesión de SQL Server está sin definir o se ha definido de forma incorrecta en una instancia de servidor no podrá iniciar una sesión en la instancia. Es lo que se denomina un *usuario huérfano* de la base de datos en esa instancia de servidor. Si un usuario está huérfano en una instancia de servidor determinada, puede configurar los inicios de sesión de usuario en cualquier momento. Para obtener más información, vea [Solucionar problemas de usuarios huérfanos &#40;SQL Server&#41;](../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md).  
  
-   **Metadatos adicionales**  
  
     Los inicios de sesión y los trabajos no son la única información que es necesario volver a crear en cada instancia de servidor que hospeda una réplica secundaria para un grupo de disponibilidad determinado. Por ejemplo, quizás necesite volver a crear la configuración del servidor, las credenciales, los datos cifrados, los permisos, la configuración de replicación, las aplicaciones de Service Broker, los desencadenadores (en el nivel de servidor), etc. Para obtener más información, vea [Administrar los metadatos cuando una base de datos pasa a estar disponible en otra instancia del servidor &#40;SQL Server&#41;](../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md).  
  
##  <a name="logins-of-applications-that-use-sql-server-authentication-or-a-local-windows-login"></a><a name="SSauthentication"></a> Inicios de sesión de aplicaciones que usan la autenticación de SQL Server o un inicio de sesión local de Windows  
 Si una aplicación usa la Autenticación de SQL Server o un inicio de sesión local de Windows, los SID que no coinciden pueden impedir que el inicio de sesión de la aplicación se resuelva en una instancia remota de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Los SID que no coincidan harán que el inicio de sesión sea un usuario huérfano en la instancia del servidor remoto. Este problema puede producirse cuando una aplicación se conecta con una base de datos reflejada o de trasvase de registros después de una conmutación por error o con una base de datos Suscriptor de replicación que se inicializó desde una copia de seguridad.  
  
 Para evitar que se produzca este problema, se recomienda tomar medidas preventivas al configurar una aplicación de este tipo para que utilice una base de datos hospedada por una instancia remota de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. La prevención implica la transferencia de los inicios de sesión y las contraseñas de la instancia local de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a la instancia remota de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Para obtener más información acerca de cómo evitar este problema, vea el artículo de KB 918992:[Cómo transferir los inicios de sesión y las contraseñas entre instancias de SQL Server](https://support.microsoft.com/kb/918992/)).  
  
> [!NOTE]  
>  Este problema afecta a las cuentas locales de Windows en distintos equipos. Sin embargo, este problema no ocurre en las cuentas de dominio debido a que el SID es el mismo en todos los equipos.  
  
 Para obtener más información, vea [Usuarios huérfanos con creación de reflejo de la base de datos y trasvase de registros](https://blogs.msdn.com/b/sqlserverfaq/archive/2009/04/13/orphaned-users-with-database-mirroring-and-log-shipping.aspx) (un blog del motor de base de datos).  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tareas relacionadas  
  
-   [Crear un inicio de sesión](../relational-databases/security/authentication-access/create-a-login.md)  
  
-   [Cree un usuario de base de datos](../relational-databases/security/authentication-access/create-a-database-user.md).  
  
-   [Crear un trabajo](../ssms/agent/create-a-job.md)  
  
-   [Administrar los metadatos cuando una base de datos pasa a estar disponible en otra instancia del servidor &#40;SQL Server&#41;](../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)  
  
## <a name="see-also"></a>Consulte también  
 [Información general de Grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Bases de datos independientes](../relational-databases/databases/contained-databases.md)   
 [Crear trabajos](../ssms/agent/create-jobs.md)  
  
  
