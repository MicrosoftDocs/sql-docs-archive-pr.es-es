---
title: Herramientas de supervisión y optimización del rendimiento | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- tools [SQL Server], monitoring performance
- monitoring server performance [SQL Server], tools
- monitoring performance [SQL Server], tools
- database performance [SQL Server], tools
- tuning databases [SQL Server], tools
- database monitoring [SQL Server], tools
- performance [SQL Server], monitoring tools
- server performance [SQL Server], tools
ms.assetid: 31529dfe-68e7-49f7-b3c2-39fcecf33a95
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c9a1f262493b54c06e2bb9eb3d4d6d44bf60d52f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674782"
---
# <a name="performance-monitoring-and-tuning-tools"></a>Herramientas de supervisión y optimización del rendimiento
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proporciona un completo conjunto de herramientas para supervisar los eventos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y para optimizar el diseño de la base de datos física. La elección de la herramienta depende del tipo de supervisión u optimización que se realice y de los eventos particulares que se supervisen.  
  
 A continuación se describen las herramientas de supervisión y optimización de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
|Herramienta|Descripción|  
|----------|-----------------|  
|[sp_trace_setfilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql)|[!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] realiza un seguimiento de los eventos de procesos del motor, como el inicio de un lote o una transacción, lo que permite supervisar la actividad del servidor y de la base de datos (por ejemplo, interbloqueos, errores irrecuperables o actividad de inicio de sesión). Puede capturar datos de [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] en un archivo o una tabla de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para su análisis posterior y también puede reproducir paso a paso los eventos capturados en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para ver qué sucedió exactamente.|  
|[SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay puede usar varios equipos para reproducir los datos de seguimiento, simulando una carga de trabajo crítica.|  
|[Supervisar el uso de recursos&#40;Monitor de sistema&#41;](../performance-monitor/monitor-resource-usage-system-monitor.md)|La función principal del Monitor de sistema es hacer un seguimiento del uso de los recursos, como el número de solicitudes de página del administrador de búfer activas, que permite supervisar el rendimiento y la actividad del servidor mediante el uso de objetos y contadores predefinidos o contadores definidos por el usuario para supervisar eventos. El Monitor de sistema (Monitor de rendimiento en Microsoft Windows NT 4.0) recopila contadores y porcentajes en lugar de datos acerca de los eventos (por ejemplo, uso de la memoria, número de transacciones activas, número de bloqueos bloqueados o actividad de la CPU). Puede establecer umbrales en contadores específicos para generar alertas que notifiquen a los operadores.<br /><br /> El Monitor de sistema funciona en los sistemas operativos Microsoft Windows Server y Windows. Puede supervisar (remota o localmente) una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en Windows NT 4.0 o posterior.<br /><br /> La diferencia clave entre el [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] y el Monitor de sistema es que el [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] supervisa los eventos del motor de base de datos, mientras que el Monitor de sistema supervisa el uso de los recursos asociado con los procesos del servidor.|  
|[Abrir el Monitor de actividad &#40;SQL Server Management Studio&#41;](../performance-monitor/open-activity-monitor-sql-server-management-studio.md)|El Monitor de actividad de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] es útil para obtener vistas ad hoc de la actividad actual y muestra gráficamente información sobre:<br /><br /> Los procesos que se ejecutan en una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Los procesos bloqueados.<br /><br /> Bloqueos.<br /><br /> La actividad de los usuarios.|  
|[Seguimiento de SQL](../sql-trace/sql-trace.md)|[!INCLUDE[tsql](../../../includes/tsql-md.md)] que crean, filtran y definen trazas:<br /><br /> [sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)<br /><br /> [sp_trace_generateevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql)<br /><br /> [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)<br /><br /> [sp_trace_setfilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql)<br /><br /> [sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)|  
|Registros de errores|El registro de eventos de aplicación de Windows proporciona una imagen global de los eventos que ocurren en todos los sistemas operativos Windows Server y Windows, así como de los eventos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y la búsqueda de texto completo. Contiene información acerca de los eventos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que no está disponible en ningún otro lugar. Puede utilizar la información del registro de errores para solucionar problemas relacionados con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)|Los siguientes procedimientos almacenados del sistema de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] suponen una alternativa muy eficaz para realizar muchas tareas de supervisión:<br /><br /> [sp_who &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql): <br />                    Notifica información de instantáneas acerca de los usuarios y procesos actuales de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , incluida la información sobre la instrucción que se ejecuta actualmente y si la instrucción está bloqueada.<br /><br /> [sp_lock &#40;&#41;de Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-lock-transact-sql): notifica información de instantáneas acerca de los bloqueos, incluido el ID. de objeto, el identificador de índice, el tipo de bloqueo y el tipo o recurso al que se aplica el bloqueo.<br /><br /> [sp_spaceused &#40;&#41;de Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql): muestra una estimación de la cantidad actual de espacio en disco que utiliza una tabla (o una base de datos completa).<br /><br /> [sp_monitor &#40;&#41;de Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-monitor-transact-sql): muestra las estadísticas, incluido el uso de la CPU, el uso de e/s y la cantidad de tiempo de inactividad desde la última vez que se ejecutó el **sp_monitor** .|  
|[DBCC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-transact-sql)|Las instrucciones DBCC (Comandos de consola de base de datos) permiten comprobar las estadísticas de rendimiento y la coherencia lógica y física de una base de datos.|  
|[Funciones integradas &#40;Transact-SQL&#41;](/sql/t-sql/functions/functions)|Las funciones integradas muestran estadísticas de instantáneas acerca de la actividad de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] desde el inicio del servidor; estas estadísticas se almacenan en contadores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] predefinidos. Por ejemplo, **@ @CPU_BUSY ** contiene la cantidad de tiempo que la CPU ha estado ejecutando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] código. **@@CONNECTIONS** contiene el número de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conexiones o intentos de conexión; **y @PACKET_ERRORS @** contiene el número de paquetes de red que se producen en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] las conexiones.|  
|[Marcas de seguimiento &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)|Las marcas de seguimiento muestran información acerca de una actividad específica en el servidor para diagnosticar problemas o causas de bajo rendimiento (por ejemplo, cadenas de interbloqueos).|  
|[Database Engine Tuning Advisor](database-engine-tuning-advisor.md)|El Asistente para la optimización de motor de base de datos analiza los efectos en el rendimiento de las instrucciones [!INCLUDE[tsql](../../../includes/tsql-md.md)] ejecutadas en las bases de datos que desea optimizar. El Asistente para la optimización de motor de base de datos proporciona recomendaciones para agregar, quitar o modificar índices, vistas indizadas y particiones.|  
  
## <a name="choosing-a-monitoring-tool"></a>Elegir una herramienta de supervisión  
 La elección de la herramienta de supervisión depende del evento o de la actividad que se va a supervisar.  
  
|Evento o actividad|SQL Server Profiler|Distributed Replay|Monitor de sistema|Monitor de actividad|Transact-SQL|Registros de error|  
|-----------------------|-------------------------|------------------------|--------------------|----------------------|-------------------|----------------|  
|Análisis de tendencias|Sí||Sí||||  
|Reproducción de los eventos capturados|Sí (desde un equipo único)|Sí (desde varios equipos)|||||  
|Supervisión ad hoc|Sí|||Sí|Sí|Sí|  
|Generación de alertas|||Sí||||  
|Interfaz gráfica|Sí||Sí|Sí||Sí|  
|Uso en aplicaciones personalizadas|Sí <sup>1</sup>||||Sí||  
  
 <sup>1</sup> uso de [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] procedimientos almacenados del sistema.  
  
## <a name="windows-monitoring-tools"></a>Herramientas de supervisión de Windows  
 Los sistemas operativos Windows y Windows Server 2003 proporcionan además estas herramientas de supervisión.  
  
|Herramienta|Descripción|  
|----------|-----------------|  
|Administrador de tareas|Muestra una sinopsis de los procesos y las aplicaciones que se ejecutan en el sistema.|  
|Agente de supervisión de red|Supervisa el tráfico de red.|  
  
 Para obtener más información acerca de las herramientas de los sistemas operativos Windows o Windows Server, vea la documentación de Windows.  
  
  
