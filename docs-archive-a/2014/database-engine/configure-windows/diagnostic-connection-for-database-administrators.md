---
title: Conexión de diagnóstico para administradores de bases de datos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- server management [SQL Server], connections
- administrator connections [SQL Server]
- ports [SQL Server], DAC
- DAC
- network connections [SQL Server], dedicated administrator
- diagnostic connections [SQL Server]
- connections [SQL Server], dedicated administrator
- ports [SQL Server]
- dedicated administrator connections [SQL Server]
ms.assetid: 993e0820-17f2-4c43-880c-d38290bf7abc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0d452ca155a5187136c910e81e8bd073e34cad56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673896"
---
# <a name="diagnostic-connection-for-database-administrators"></a><span data-ttu-id="66910-102">Conexión de diagnóstico para administradores de bases de datos</span><span class="sxs-lookup"><span data-stu-id="66910-102">Diagnostic Connection for Database Administrators</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="66910-103">proporciona una conexión de diagnóstico especial para los administradores cuando no son posibles las conexiones estándar con el servidor.</span><span class="sxs-lookup"><span data-stu-id="66910-103">provides a special diagnostic connection for administrators when standard connections to the server are not possible.</span></span> <span data-ttu-id="66910-104">La conexión de diagnóstico permite a un administrador tener acceso a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para ejecutar consultas de diagnóstico y solucionar problemas, incluso cuando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no responde a las solicitudes de conexión estándar.</span><span class="sxs-lookup"><span data-stu-id="66910-104">This diagnostic connection allows an administrator to access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to execute diagnostic queries and troubleshoot problems even when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not responding to standard connection requests.</span></span>  
  
 <span data-ttu-id="66910-105">Esta conexión de administrador dedicada (DAC) admite la característica de cifrado y otras características de seguridad de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="66910-105">This dedicated administrator connection (DAC) supports encryption and other security features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="66910-106">La DAC solo permite cambiar el contexto de usuario a otro usuario de administración.</span><span class="sxs-lookup"><span data-stu-id="66910-106">The DAC only allows changing the user context to another admin user.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="66910-107">hace lo posible para que la conexión de administrador dedicada (DAC) sea correcta, pero, en situaciones extremas, es posible que no lo logre.</span><span class="sxs-lookup"><span data-stu-id="66910-107">makes every attempt to make DAC connect successfully, but under extreme situations it may not be successful.</span></span>  
  
||  
|-|  
|<span data-ttu-id="66910-108">**Se aplica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ( [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] desde hasta la [versión actual](https://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="66910-108">**Applies to**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] through [current version](https://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].</span></span>|  
  
## <a name="connecting-with-dac"></a><span data-ttu-id="66910-109">Conectar con DAC</span><span class="sxs-lookup"><span data-stu-id="66910-109">Connecting with DAC</span></span>  
 <span data-ttu-id="66910-110">De forma predeterminada, solo se permite la conexión desde un cliente que se ejecute en el servidor.</span><span class="sxs-lookup"><span data-stu-id="66910-110">By default, the connection is only allowed from a client running on the server.</span></span> <span data-ttu-id="66910-111">Las conexiones de red no están permitidas, a menos que se configuren con el procedimiento almacenado sp_configure con la opción [remote admin connections](remote-admin-connections-server-configuration-option.md).</span><span class="sxs-lookup"><span data-stu-id="66910-111">Network connections are not permitted unless they are configured by using the sp_configure stored procedure with the [remote admin connections option](remote-admin-connections-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="66910-112">Solo los miembros del rol sysadmin de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pueden conectarse utilizando la DAC.</span><span class="sxs-lookup"><span data-stu-id="66910-112">Only members of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sysadmin role can connect using the DAC.</span></span>  
  
 <span data-ttu-id="66910-113">La DAC está disponible y se admite a través de la utilidad del símbolo del sistema **sqlcmd** a través de un modificador de administrador especial (**-A**).</span><span class="sxs-lookup"><span data-stu-id="66910-113">The DAC is available and supported through the **sqlcmd** command-prompt utility using a special administrator switch (**-A**).</span></span> <span data-ttu-id="66910-114">Para obtener más información sobre cómo usar **sqlcmd**, vea [Usar sqlcmd con variables de script](../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md).</span><span class="sxs-lookup"><span data-stu-id="66910-114">For more information about using **sqlcmd**, see [Use sqlcmd with Scripting Variables](../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md).</span></span> <span data-ttu-id="66910-115">También puede conectar el prefijo `admin:` al nombre de la instancia con el formato **sqlcmd-Sadmin:** _<instance_name>._</span><span class="sxs-lookup"><span data-stu-id="66910-115">You can also connect prefixing `admin:`to the instance name in the format **sqlcmd -Sadmin:**_<instance_name>._</span></span> <span data-ttu-id="66910-116">También puede iniciar una DAC desde un [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Editor de consultas mediante la conexión a `admin:` \<*instance_name*> .</span><span class="sxs-lookup"><span data-stu-id="66910-116">You can also initiate a DAC from a [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor by connecting to `admin:`\<*instance_name*>.</span></span>  
  
## <a name="restrictions"></a><span data-ttu-id="66910-117">Restricciones</span><span class="sxs-lookup"><span data-stu-id="66910-117">Restrictions</span></span>  
 <span data-ttu-id="66910-118">Dado que la DAC existe únicamente para el diagnóstico de problemas de servidor en raras circunstancias, hay algunas restricciones en la conexión:</span><span class="sxs-lookup"><span data-stu-id="66910-118">Because the DAC exists solely for diagnosing server problems in rare circumstances, there are some restrictions on the connection:</span></span>  
  
-   <span data-ttu-id="66910-119">Para asegurarse de que haya recursos disponibles para la conexión, solo se permite una DAC por cada instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="66910-119">To guarantee that there are resources available for the connection, only one DAC is allowed per instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="66910-120">Si ya hay una conexión DAC activa, cualquier solicitud nueva de conexión a través de la DAC se denegará con el error 17810.</span><span class="sxs-lookup"><span data-stu-id="66910-120">If a DAC connection is already active, any new request to connect through the DAC is denied with error 17810.</span></span>  
  
-   <span data-ttu-id="66910-121">Para ahorrar recursos, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] no escucha en el puerto DAC a menos que se inicie con la marca de seguimiento 7806.</span><span class="sxs-lookup"><span data-stu-id="66910-121">To conserve resources, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] does not listen on the DAC port unless started with a trace flag 7806.</span></span>  
  
-   <span data-ttu-id="66910-122">Inicialmente la DAC intenta conectarse a la base de datos predeterminada asociada al inicio de sesión.</span><span class="sxs-lookup"><span data-stu-id="66910-122">The DAC initially attempts to connect to the default database associated with the login.</span></span> <span data-ttu-id="66910-123">Una vez conectada correctamente, el usuario podrá conectarse a la base de datos maestra.</span><span class="sxs-lookup"><span data-stu-id="66910-123">After it is successfully connected, you can connect to the master database.</span></span> <span data-ttu-id="66910-124">Si la base de datos predeterminada está sin conexión o no disponible por la razón que sea, la conexión devolverá el error 4060.</span><span class="sxs-lookup"><span data-stu-id="66910-124">If the default database is offline or otherwise not available, the connection will return error 4060.</span></span> <span data-ttu-id="66910-125">Con todo, se realizará correctamente si invalida la base de datos predeterminada para conectarse a la base de datos maestra utilizando el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="66910-125">However, it will succeed if you override the default database to connect to the master database instead using the following command:</span></span>  
  
     <span data-ttu-id="66910-126">**Sqlcmd-A-d maestro**</span><span class="sxs-lookup"><span data-stu-id="66910-126">**sqlcmd -A -d master**</span></span>  
  
     <span data-ttu-id="66910-127">Se recomienda conectarse a la base de datos maestra con la DAC porque su disponibilidad está garantizada si se ha iniciado la instancia de [!INCLUDE[ssDE](../../includes/ssde-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="66910-127">We recommend that you connect to the master database with the DAC because master is guaranteed to be available if the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is started.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="66910-128">prohíbe la ejecución de comandos o consultas paralelas con la DAC.</span><span class="sxs-lookup"><span data-stu-id="66910-128">prohibits running parallel queries or commands with the DAC.</span></span> <span data-ttu-id="66910-129">Por ejemplo, se genera el error 3637 si se ejecuta una de las instrucciones siguientes con la DAC:</span><span class="sxs-lookup"><span data-stu-id="66910-129">For example, error 3637 is generated if you execute either of the following statements with the DAC:</span></span>  
  
    -   <span data-ttu-id="66910-130">RESTORE</span><span class="sxs-lookup"><span data-stu-id="66910-130">RESTORE</span></span>  
  
    -   <span data-ttu-id="66910-131">BACKUP</span><span class="sxs-lookup"><span data-stu-id="66910-131">BACKUP</span></span>  
  
-   <span data-ttu-id="66910-132">Con la DAC solo está garantizada la disponibilidad de recursos limitados.</span><span class="sxs-lookup"><span data-stu-id="66910-132">Only limited resources are guaranteed to be available with the DAC.</span></span> <span data-ttu-id="66910-133">No use la DAC para ejecutar consultas que consuman muchos recursos (por ejemplo,</span><span class="sxs-lookup"><span data-stu-id="66910-133">Do not use the DAC to run resource-intensive queries (for example.</span></span> <span data-ttu-id="66910-134">una combinación compleja en una tabla grande) o consultas que se puedan bloquear.</span><span class="sxs-lookup"><span data-stu-id="66910-134">a complex join on large table) or queries that may block.</span></span> <span data-ttu-id="66910-135">Así se evita que la DAC agrave cualquier problema de servidor ya existente.</span><span class="sxs-lookup"><span data-stu-id="66910-135">This helps prevent the DAC from compounding any existing server problems.</span></span> <span data-ttu-id="66910-136">Para evitar posibles escenarios de bloqueo, si debe ejecutar consultas que se pueden bloquear, ejecútelas con niveles de aislamiento basado en instantáneas siempre que sea posible; de lo contrario, establezca el nivel de aislamiento de transacción en READ UNCOMMITTED y establezca un valor pequeño, como 2000 milisegundos, para LOCK_TIMEOUT, o ambos.</span><span class="sxs-lookup"><span data-stu-id="66910-136">To avoid potential blocking scenarios, if you have to run queries that may block, run the query under snapshot-based isolation levels if possible; otherwise, set the transaction isolation level to READ UNCOMMITTED and set the LOCK_TIMEOUT value to a short value such as 2000 milliseconds, or both.</span></span> <span data-ttu-id="66910-137">Esto evitará que la sesión de la DAC se bloquee.</span><span class="sxs-lookup"><span data-stu-id="66910-137">This will prevent the DAC session from getting blocked.</span></span> <span data-ttu-id="66910-138">Sin embargo, dependiendo del estado en el que esté [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , puede ser que la sesión de la DAC se bloquee en un bloqueo temporal.</span><span class="sxs-lookup"><span data-stu-id="66910-138">However, depending on the state that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is in, the DAC session might get blocked on a latch.</span></span> <span data-ttu-id="66910-139">Es posible que pueda finalizar la sesión de la DAC mediante CTRL-C, pero esto no está garantizado.</span><span class="sxs-lookup"><span data-stu-id="66910-139">You might be able to terminate the DAC session using CNTRL-C but it is not guaranteed.</span></span> <span data-ttu-id="66910-140">En tal caso, la única alternativa puede ser reiniciar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="66910-140">In that case, your only option may be to restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="66910-141">Para asegurarse de la conectividad y la solución de problemas con la DAC, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] reserva recursos limitados para procesar los comandos ejecutados en la DAC.</span><span class="sxs-lookup"><span data-stu-id="66910-141">To guarantee connectivity and troubleshooting with the DAC, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] reserves limited resources to process commands run on the DAC.</span></span> <span data-ttu-id="66910-142">Estos recursos solo suelen ser suficientes para funciones sencillas de diagnóstico y solución de problemas, como las que se mencionan más adelante.</span><span class="sxs-lookup"><span data-stu-id="66910-142">These resources are typically only enough for simple diagnostic and troubleshooting functions, such as those listed below.</span></span>  
  
 <span data-ttu-id="66910-143">Aunque teóricamente es posible ejecutar cualquier instrucción [!INCLUDE[tsql](../../includes/tsql-md.md)] que no se tenga que ejecutar en paralelo en la DAC, se recomienda encarecidamente limitar el uso a los siguientes comandos de diagnóstico y solución de problemas:</span><span class="sxs-lookup"><span data-stu-id="66910-143">Although you can theoretically run any [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that does not have to execute in parallel on the DAC, we strongly recommend that you restrict usage to the following diagnostic and troubleshooting commands:</span></span>  
  
-   <span data-ttu-id="66910-144">Consultas en vistas de administración dinámica para diagnósticos básicos como sys.dm_tran_locks para el estado de bloqueo, sys.dm_os_memory_cache_counters para comprobar el estado de las cachés, y sys.dm_exec_requests y sys.dm_exec_sessions para solicitudes y sesiones activas.</span><span class="sxs-lookup"><span data-stu-id="66910-144">Querying dynamic management views for basic diagnostics such as sys.dm_tran_locks for the locking status, sys.dm_os_memory_cache_counters to check the health of caches, and sys.dm_exec_requests and sys.dm_exec_sessions for active sessions and requests.</span></span> <span data-ttu-id="66910-145">Evite las vistas de administración dinámica que consumen muchos recursos (por ejemplo, sys.dm_tran_version_store recorre el almacén de versiones completo y puede causar numerosas E/S) o que utilizan combinaciones complejas.</span><span class="sxs-lookup"><span data-stu-id="66910-145">Avoid dynamic management views that are resource intensive (for example, sys.dm_tran_version_store scans the full version store and can cause extensive I/O) or that use complex joins.</span></span> <span data-ttu-id="66910-146">Para obtener información acerca de las implicaciones para el rendimiento, vea la documentación específica para la [vista de administración dinámica](../../relational-databases/views/views.md).</span><span class="sxs-lookup"><span data-stu-id="66910-146">For information about performance implications, see the documentation for the specific [dynamic management view](../../relational-databases/views/views.md).</span></span>  
  
-   <span data-ttu-id="66910-147">Consultas en vistas de catálogo.</span><span class="sxs-lookup"><span data-stu-id="66910-147">Querying catalog views.</span></span>  
  
-   <span data-ttu-id="66910-148">Comandos DBCC básicos como DBCC FREEPROCCACHE, DBCC FREESYSTEMCACHE, DBCC DROPCLEANBUFFERS`,` y DBCC SQLPERF.</span><span class="sxs-lookup"><span data-stu-id="66910-148">Basic DBCC commands such as DBCC FREEPROCCACHE, DBCC FREESYSTEMCACHE, DBCC DROPCLEANBUFFERS`,` and DBCC SQLPERF.</span></span> <span data-ttu-id="66910-149">No ejecute comandos que consumen muchos recursos, como **DBCC** CHECKDB, DBCC DBREINDEX o DBCC SHRINKDATABASE.</span><span class="sxs-lookup"><span data-stu-id="66910-149">Do not run resource-intensive commands such as **DBCC** CHECKDB, DBCC DBREINDEX, or DBCC SHRINKDATABASE.</span></span>  
  
-   <span data-ttu-id="66910-150">Comando [!INCLUDE[tsql](../../includes/tsql-md.md)] KILL *\<spid>* .</span><span class="sxs-lookup"><span data-stu-id="66910-150">[!INCLUDE[tsql](../../includes/tsql-md.md)] KILL*\<spid>* command.</span></span> <span data-ttu-id="66910-151">Dependiendo del estado de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], es posible que el comando KILL no siempre se ejecute correctamente; en tal caso, la única opción puede ser reiniciar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="66910-151">Depending on the state of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the KILL command might not always succeed; then the only option may be to restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="66910-152">Éstas son algunas directrices generales:</span><span class="sxs-lookup"><span data-stu-id="66910-152">The following are some general guidelines:</span></span>  
  
    -   <span data-ttu-id="66910-153">Compruebe que realmente se ha eliminado el SPID con la consulta `SELECT * FROM sys.dm_exec_sessions WHERE session_id = <spid>`.</span><span class="sxs-lookup"><span data-stu-id="66910-153">Verify that the SPID was actually killed by querying `SELECT * FROM sys.dm_exec_sessions WHERE session_id = <spid>`.</span></span> <span data-ttu-id="66910-154">Si no devuelve ninguna fila, significa que la sesión se ha eliminado.</span><span class="sxs-lookup"><span data-stu-id="66910-154">If it returns no rows, it means the session was killed.</span></span>  
  
    -   <span data-ttu-id="66910-155">Si la sesión todavía existe, compruebe si hay tareas asignadas a esta sesión ejecutando la consulta `SELECT * FROM sys.dm_os_tasks WHERE session_id = <spid>`.</span><span class="sxs-lookup"><span data-stu-id="66910-155">If the session is still there, verify whether there are tasks assigned to this session by running the query `SELECT * FROM sys.dm_os_tasks WHERE session_id = <spid>`.</span></span> <span data-ttu-id="66910-156">Si ve la tarea, lo más probable es que se esté eliminando la sesión ahora.</span><span class="sxs-lookup"><span data-stu-id="66910-156">If you see the task there, most likely your session is currently being killed.</span></span> <span data-ttu-id="66910-157">Tenga en cuenta que es posible que esto tarde bastante tiempo y que no salga correctamente.</span><span class="sxs-lookup"><span data-stu-id="66910-157">Note that this may take considerable amount of time and may not succeed at all.</span></span>  
  
    -   <span data-ttu-id="66910-158">Si no hay ninguna tarea en sys.dm_os_tasks asociada a esta sesión, pero la sesión permanece en sys.dm_exec_sessions tras ejecutar el comando KILL, significa que no tiene ningún trabajo disponible.</span><span class="sxs-lookup"><span data-stu-id="66910-158">If there are no tasks in the sys.dm_os_tasks associated with this session, but the session remains in sys.dm_exec_sessions after executing the KILL command, it means that you do not have a worker available.</span></span> <span data-ttu-id="66910-159">Seleccione una de las tareas que se están ejecutando (una tarea que aparece en la vista sys.dm_os_tasks con `sessions_id <> NULL`), y elimine la sesión que tiene asociada para liberar el trabajo.</span><span class="sxs-lookup"><span data-stu-id="66910-159">Select one of the currently running tasks (a task listed in the sys.dm_os_tasks view with a `sessions_id <> NULL`), and kill the session associated with it to free up the worker.</span></span> <span data-ttu-id="66910-160">Tenga en cuenta que es posible que no sea suficiente eliminar una sola sesión: posiblemente tendrá que eliminar varias.</span><span class="sxs-lookup"><span data-stu-id="66910-160">Note that it may not be enough to kill a single session: you may have to kill multiple ones.</span></span>  
  
## <a name="dac-port"></a><span data-ttu-id="66910-161">Puerto de la DAC</span><span class="sxs-lookup"><span data-stu-id="66910-161">DAC Port</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="66910-162">escucha la DAC en el puerto TCP 1434 si está disponible o en un puerto asignado dinámicamente en el inicio de [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span><span class="sxs-lookup"><span data-stu-id="66910-162">listens for the DAC on TCP port 1434 if available or a TCP port dynamically assigned upon [!INCLUDE[ssDE](../../includes/ssde-md.md)] startup.</span></span> <span data-ttu-id="66910-163">El registro de errores contiene el número de puerto en el que escucha la DAC.</span><span class="sxs-lookup"><span data-stu-id="66910-163">The error log contains the port number the DAC is listening on.</span></span> <span data-ttu-id="66910-164">De forma predeterminada, la escucha de la DAC solo acepta la conexión en el puerto local.</span><span class="sxs-lookup"><span data-stu-id="66910-164">By default the DAC listener accepts connection on only the local port.</span></span> <span data-ttu-id="66910-165">Para ver un ejemplo de código en el que se activan conexiones de administración remota, vea [remote admin connections (opción de configuración del servidor)](remote-admin-connections-server-configuration-option.md).</span><span class="sxs-lookup"><span data-stu-id="66910-165">For a code sample that activates remote administration connections, see [remote admin connections Server Configuration Option](remote-admin-connections-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="66910-166">Una vez configurada la conexión de administración remota, la escucha de la DAC se habilita sin necesidad de reiniciar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y se puede conectar un cliente a la DAC de forma remota.</span><span class="sxs-lookup"><span data-stu-id="66910-166">After the remote administration connection is configured, the DAC listener is enabled without requiring a restart of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and a client can now connect to the DAC remotely.</span></span> <span data-ttu-id="66910-167">Puede habilitar la escucha de la DAC para que acepte las conexiones remotamente incluso si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no responde conectándose primero a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mediante la DAC de forma local y, a continuación, ejecutando el procedimiento almacenado sp_configure para aceptar la conexión desde conexiones remotas.</span><span class="sxs-lookup"><span data-stu-id="66910-167">You can enable the DAC listener to accept connections remotely even if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is unresponsive by first connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the DAC locally, and then executing the sp_configure stored procedure to accept connection from remote connections.</span></span>  
  
 <span data-ttu-id="66910-168">En las configuraciones de clúster, la DAC estará desactivada de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="66910-168">On cluster configurations, the DAC will be off by default.</span></span> <span data-ttu-id="66910-169">Los usuarios pueden ejecutar la opción remote admin connection de sp_configure para habilitar la escucha de la DAC para tener acceso a una conexión remota.</span><span class="sxs-lookup"><span data-stu-id="66910-169">Users can execute the remote admin connection option of sp_configure to enable the DAC listener to access a remote connection.</span></span> <span data-ttu-id="66910-170">Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no responde y la escucha de la DAC no está habilitada, es posible que tenga que reiniciar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para conectarse a la DAC.</span><span class="sxs-lookup"><span data-stu-id="66910-170">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is unresponsive and the DAC listener is not enabled, you might have to restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to connect with the DAC.</span></span> <span data-ttu-id="66910-171">Por esta razón, es recomendable que habilite la opción de configuración remote admin connections en los sistemas en clúster.</span><span class="sxs-lookup"><span data-stu-id="66910-171">Therefore, we recommend that you enable the remote admin connections configuration option on clustered systems.</span></span>  
  
 <span data-ttu-id="66910-172">Durante el inicio, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] asigna dinámicamente el puerto de la DAC.</span><span class="sxs-lookup"><span data-stu-id="66910-172">The DAC port is assigned dynamically by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] during startup.</span></span> <span data-ttu-id="66910-173">Mientras se establece la conexión a la instancia predeterminada, la DAC evita el uso de una solicitud del protocolo de resolución de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SSRP) al servicio SQL Server Browser.</span><span class="sxs-lookup"><span data-stu-id="66910-173">When connecting to the default instance, the DAC avoids using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resolution Protocol (SSRP) request to the SQL Server Browser Service when connecting.</span></span> <span data-ttu-id="66910-174">Primero se conecta a través del puerto TCP 1434.</span><span class="sxs-lookup"><span data-stu-id="66910-174">It first connects over TCP port 1434.</span></span> <span data-ttu-id="66910-175">Si se produce un error, realiza una llamada SSRP para obtener el puerto.</span><span class="sxs-lookup"><span data-stu-id="66910-175">If that fails, it makes an SSRP call to get the port.</span></span> <span data-ttu-id="66910-176">Si el Explorador de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no escucha las solicitudes SSRP, la solicitud de conexión devolverá un error.</span><span class="sxs-lookup"><span data-stu-id="66910-176">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser is not listening for SSRP requests, the connection request returns an error.</span></span> <span data-ttu-id="66910-177">Consulte el registro de errores para ver en qué número de puerto escucha la DAC.</span><span class="sxs-lookup"><span data-stu-id="66910-177">Refer to the error log to find the port number DAC is listening on.</span></span> <span data-ttu-id="66910-178">Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] está configurado para aceptar conexiones de administración remotas, la DAC debe iniciarse con un número de puerto explícito:</span><span class="sxs-lookup"><span data-stu-id="66910-178">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured to accept remote administration connections, the DAC must be initiated with an explicit port number:</span></span>  
  
 <span data-ttu-id="66910-179">**sqlcmd-STCP:** _ \<server> , \<port> _</span><span class="sxs-lookup"><span data-stu-id="66910-179">**sqlcmd-Stcp:** _\<server>,\<port>_</span></span>  
  
 <span data-ttu-id="66910-180">El registro de errores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muestra el número de puerto de la DAC, que es 1434 de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="66910-180">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log lists the port number for the DAC, which is 1434 by default.</span></span> <span data-ttu-id="66910-181">Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] está configurado para aceptar solo conexiones DAC locales, conéctese mediante el adaptador de bucles invertidos con el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="66910-181">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured to accept local DAC connections only, connect using the loopback adapter using the following command:</span></span>  
  
 <span data-ttu-id="66910-182">**sqlcmd-s 127.0.0.1**,`1434`</span><span class="sxs-lookup"><span data-stu-id="66910-182">**sqlcmd-S127.0.0.1**,`1434`</span></span>  
  
## <a name="example"></a><span data-ttu-id="66910-183">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="66910-183">Example</span></span>  
 <span data-ttu-id="66910-184">En este ejemplo, un administrador observa que el servidor `URAN123` no responde y desea diagnosticar el problema.</span><span class="sxs-lookup"><span data-stu-id="66910-184">In this example, an administrator notices that server `URAN123` is not responding and wants to diagnose the problem.</span></span> <span data-ttu-id="66910-185">Para ello, el usuario activa la utilidad del símbolo del sistema `sqlcmd` y se conecta al servidor `URAN123` mediante `-A` para indicar la DAC.</span><span class="sxs-lookup"><span data-stu-id="66910-185">To do this, the user activates the `sqlcmd` command prompt utility and connects to server `URAN123` using `-A` to indicate the DAC.</span></span>  
  
 `sqlcmd -S URAN123 -U sa -P <xxx> -A`  
  
 <span data-ttu-id="66910-186">Ahora el administrador puede ejecutar consultas para diagnosticar el problema y posiblemente finalizar las sesiones que no responden.</span><span class="sxs-lookup"><span data-stu-id="66910-186">The administrator can now execute queries to diagnose the problem and possibly terminate the unresponsive sessions.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="66910-187">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="66910-187">Related Tasks</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="66910-188">Contenido relacionado</span><span class="sxs-lookup"><span data-stu-id="66910-188">Related Content</span></span>  
 [<span data-ttu-id="66910-189">Usar sqlcmd con variables de script</span><span class="sxs-lookup"><span data-stu-id="66910-189">Use sqlcmd with Scripting Variables</span></span>](../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md)  
  
 [<span data-ttu-id="66910-190">Utilidad sqlcmd</span><span class="sxs-lookup"><span data-stu-id="66910-190">sqlcmd Utility</span></span>](../../tools/sqlcmd-utility.md)  
  
 [<span data-ttu-id="66910-191">SELECT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="66910-191">SELECT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/select-transact-sql)  
  
 [<span data-ttu-id="66910-192">sp_who &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="66910-192">sp_who &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql)  
  
 [<span data-ttu-id="66910-193">sp_lock &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="66910-193">sp_lock &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-lock-transact-sql)  
  
 [<span data-ttu-id="66910-194">KILL &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="66910-194">KILL &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/kill-transact-sql)  
  
 [<span data-ttu-id="66910-195">DBCC CHECKALLOC &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="66910-195">DBCC CHECKALLOC &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checkalloc-transact-sql)  
  
 [<span data-ttu-id="66910-196">DBCC CHECKDB &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="66910-196">DBCC CHECKDB &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
 [<span data-ttu-id="66910-197">DBCC OPENTRAN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="66910-197">DBCC OPENTRAN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-opentran-transact-sql)  
  
 [<span data-ttu-id="66910-198">DBCC INPUTBUFFER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="66910-198">DBCC INPUTBUFFER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-inputbuffer-transact-sql)  
  
 [<span data-ttu-id="66910-199">Opciones de configuración de servidor &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="66910-199">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
 [<span data-ttu-id="66910-200">Funciones y vistas de administración dinámica relacionadas con transacciones &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="66910-200">Transaction Related Dynamic Management Views and Functions &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql)  
  
 [<span data-ttu-id="66910-201">Marcas de seguimiento &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="66910-201">Trace Flags &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)  
  
  