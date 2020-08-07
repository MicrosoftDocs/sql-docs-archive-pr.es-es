---
title: Supervisión y solución de problemas de objetos de base de datos administrados | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], performance
- monitoring [CLR integration]
- performance [CLR integration]
ms.assetid: a7b589ac-104d-4b68-b4aa-9f5fc192b13d
author: rothja
ms.author: jroth
ms.openlocfilehash: a7efbc045fc5f152f98ba7dbf2dfc686ff5e86a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87747034"
---
# <a name="monitoring-and-troubleshooting-managed-database-objects"></a>Supervisar y solucionar problemas de objetos de base de datos administrados
  En este tema se proporciona información sobre las herramientas que se pueden utilizar para supervisar y solucionar problemas de los objetos de base de datos administrados y ensamblados que se ejecutan en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="profiler-trace-events"></a>Eventos de seguimiento del Analizador  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] incluye Seguimiento de SQL y notificaciones de evento para supervisar los eventos que se generan en el motor de base de datos. Al registrar los eventos especificados, Seguimiento de SQL ayuda a solucionar los problemas de rendimiento, auditar la actividad de la base de datos, obtener datos de muestra para un entorno de prueba, depurar instrucciones y procedimientos almacenados de [!INCLUDE[tsql](../../../includes/tsql-md.md)] y recopilar datos para las herramientas de análisis del rendimiento. Para obtener más información, vea [seguimiento de SQL](../sql-trace/sql-trace.md) y [eventos extendidos](../extended-events/extended-events.md).  
  
|Evento|Descripción|  
|-----------|-----------------|  
|[Assembly Load (clase de eventos)](../../database-engine/assembly-load-event-class.md)|Se utiliza para supervisar las solicitudes de carga de ensamblados (correctas y no realizadas).|  
|[SQL: BatchStarting (clase de eventos](../event-classes/sql-batchstarting-event-class.md)), [SQL: BatchCompleted (clase de eventos](../event-classes/sql-batchcompleted-event-class.md) )|Proporciona información sobre los lotes de [!INCLUDE[tsql](../../../includes/tsql-md.md)] que se han iniciado o completado.|  
|[SP: Starting (clase de eventos](../event-classes/sp-starting-event-class.md)), [SP: Completed (clase de eventos](../event-classes/sp-completed-event-class.md) )|Se utiliza para supervisar la ejecución de procedimientos almacenados de [!INCLUDE[tsql](../../../includes/tsql-md.md)].|  
|[SQL: StmtStarting, clase de eventos](../event-classes/sql-stmtstarting-event-class.md), [SQL: StmtCompleted (clase de eventos](../event-classes/sql-stmtcompleted-event-class.md) )|Se utiliza para supervisar la ejecución de rutinas de CLR y [!INCLUDE[tsql](../../../includes/tsql-md.md)].|  
  
## <a name="performance-counters"></a>Contadores de rendimiento  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] incluye objetos y contadores que puede utilizar el Monitor de sistema para supervisar la actividad de los equipos en los que se ejecute una instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Un objeto es cualquier recurso de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], como un bloqueo de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] o un proceso de Windows. Cada objeto contiene uno o más contadores que determinan diversos aspectos de los objetos que se van a supervisar. Para obtener más información, vea [Usar objetos de SQL Server](../performance-monitor/use-sql-server-objects.md).  
  
|Object|Descripción|  
|------------|-----------------|  
|[CLR (objeto de SQL Server)](../performance-monitor/sql-server-clr-object.md)|Tiempo total de la ejecución en CLR.|  
  
## <a name="windows-system-monitor-perfmonexe-counters"></a>Contadores de Monitor de sistema (PERFMON.EXE) de Windows  
 La herramienta Monitor de sistema (PERFMON.EXE) de Windows tiene varios contadores de rendimiento que se pueden utilizar para supervisar las aplicaciones de integración CLR. El nombre de proceso "sqlservr" puede filtrar los contadores de rendimiento de .NET CLR para realizar el seguimiento de las aplicaciones de integración CLR que se están ejecutando actualmente.  
  
|Objeto de rendimiento|Descripción|  
|------------------------|-----------------|  
|SqlServer:CLR|Proporciona las estadísticas de CPU del servidor.|  
|Excepciones de .NET CLR|Realiza el seguimiento del número de excepciones por segundo.|  
|Carga de .NET CLR|Proporciona información sobre los ensamblados y AppDomain cargados en el servidor.|  
|Memoria de .NET CLR|Proporciona información sobre el uso de memoria de CLR. Este objeto se puede utilizar para marcar alertas si el uso de memoria aumenta en exceso.|  
|Proveedor de datos de .NET para SQL Server|Realiza el seguimiento del número de conexiones y desconexiones por segundo. Este objeto se puede utilizar para supervisar el nivel de actividad de base de datos.|  
  
## <a name="catalog-views"></a>Vistas de catálogo  
 Las vistas de catálogo devuelven información que utiliza el motor de base de datos de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Se recomienda utilizar las vistas de catálogo porque son la interfaz más general para los metadatos del catálogo y proporcionan el método más eficaz para obtener, transformar y presentar formas personalizadas de esta información. Todos los metadatos del catálogo disponibles para el usuario se exponen mediante las vistas de catálogo. Para obtener más información, vea [Vistas de catálogo &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql).  
  
|Datos del catálogo|Descripción|  
|------------------|-----------------|  
|[Sys. Assemblies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assemblies-transact-sql)|Devuelve información sobre los ensamblados registrados en una base de datos.|  
|[Sys. assembly_references &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-references-transact-sql)|Identifica ensamblados que hacen referencia a otros ensamblados.|  
|[sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql)|Devuelve información sobre cada función, procedimiento almacenado y desencadenador definidos en un ensamblado.|  
|[Sys. assembly_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-files-transact-sql)|Devuelve información sobre los archivos de ensamblado registrados en la base de datos.|  
|[Sys. assembly_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-types-transact-sql)|Identifica los tipos definidos por el usuario (UDT) definidos por un ensamblado.|  
|[Sys. module_assembly_usages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-module-assembly-usages-transact-sql)|Identifica los ensamblados donde se definen los módulos CLR.|  
|[sys.parameter_type_usages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-parameter-type-usages-transact-sql)|Devuelve información sobre los parámetros que son tipos definidos por el usuario.|  
|[sys.server_assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql)|Identifica el ensamblado donde se define un desencadenador CLR.|  
|[sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql)|Identifica los desencadenadores DDL en el nivel de servidor de un servidor, incluidos los desencadenadores CLR.|  
|[Sys. type_assembly_usages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-type-assembly-usages-transact-sql)|Identifica los ensamblados donde se definen los tipos definidos por el usuario.|  
|[sys.types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-types-transact-sql)|Devuelve los tipos definidos por el usuario y de sistema registrados en la base de datos.|  
  
## <a name="dynamic-management-views"></a>Vistas de administración dinámica  
 Las funciones y vistas de administración dinámica devuelven información sobre el estado del servidor que se puede utilizar para controlar el estado de una instancia del servidor, para diagnosticar problemas y para optimizar el rendimiento. Para obtener más información, vea [funciones y vistas de administración dinámica &#40;Transact-SQL&#41;](../views/views.md).  
  
|DMV|Descripción|  
|---------|-----------------|  
|[sys.dm_clr_appdomains &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql)|Proporciona información sobre cada dominio de aplicación del servidor.|  
|[sys.dm_clr_loaded_assemblies &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql)|Identifica cada ensamblado administrado registrado en el servidor.|  
|[sys.dm_clr_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-clr-properties-transact-sql)|Devuelve información acerca del entorno CLR hospedado.|  
|[sys.dm_clr_tasks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-clr-tasks-transact-sql)|Identifica todas las tareas CLR que se están ejecutando actualmente.|  
|[sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql)|Devuelve información sobre los planes de ejecución de consultas almacenados en memoria caché por [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] para una ejecución más rápida de las consultas.|  
|[sys.dm_exec_query_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql)|Devuelve estadísticas de rendimiento de agregado para planes de consulta en caché.|  
|[sys.dm_exec_requests &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql)|Devuelve información acerca de cada solicitud que se está ejecutando en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[sys.dm_os_memory_clerks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql)|Devuelve todos los distribuidores de memoria activos actualmente en la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], incluidos los distribuidores de memoria CLR.|  
  
## <a name="see-also"></a>Consulte también  
 [Conceptos de programación en el ámbito de la integración de Common Language Runtime &#40;CLR&#41;](../../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  
