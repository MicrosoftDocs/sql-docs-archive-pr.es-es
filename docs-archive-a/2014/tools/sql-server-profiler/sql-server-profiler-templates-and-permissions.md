---
title: Plantillas y permisos de SQL Server Profiler | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], about SQL Server Profiler
- SQL Server Profiler, about SQL Server Profiler
ms.assetid: 6d00378a-5d74-463b-9ed6-a2685306a9d2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8f3e3bc180db4e59def5af7eae39d8f177c93268
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663877"
---
# <a name="sql-server-profiler-templates-and-permissions"></a>Plantillas y permisos de SQL Server Profiler
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] muestra el modo en que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resuelve las consultas internamente. Esto permite a los administradores ver exactamente las instrucciones [!INCLUDE[tsql](../../includes/tsql-md.md)] o las Expresiones multidimensionales que se envían al servidor y cómo el servidor tiene acceso a la base de datos o al cubo para devolver los conjuntos de resultados.  
  
 Mediante el [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]puede hacer lo siguiente:  
  
-   Crear un seguimiento que se base en una plantilla que se puede reutilizar  
  
-   Observar el resultado del seguimiento a medida que se ejecuta el seguimiento  
  
-   Almacenar el resultado de un seguimiento en una tabla  
  
-   Iniciar, detener, pausar y modificar el resultado del seguimiento según sea necesario  
  
-   Reproducir el resultado del seguimiento  
  
 Utilice el [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] para supervisar únicamente los eventos en los que está interesado. Si los seguimientos son demasiado grandes, puede filtrarlos a partir de la información que desea, de forma que solo se recopile un subconjunto de los datos del evento. Si se supervisan demasiados eventos, aumentará la sobrecarga del servidor y el proceso de supervisión, y podría hacer que el archivo o la tabla de seguimiento crezcan demasiado, especialmente cuando el proceso de supervisión se realiza durante un período prolongado de tiempo.  
  
> [!NOTE]  
>  Los valores de las columnas de seguimiento superiores a 1 GB devuelven un error y se truncan en la salida del seguimiento.  
  
## <a name="in-this-section"></a>En esta sección  
  
|Tema|Descripción|  
|-----------|-----------------|  
|[Plantillas de SQL Server Profiler](sql-server-profiler-templates.md)|Contiene información acerca de las plantillas de seguimiento predefinidas que se incluyen en el [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Permisos necesarios para ejecutar SQL Server Profiler](permissions-required-to-run-sql-server-profiler.md)|Contiene información acerca de los permisos necesarios para ejecutar el [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Guardar seguimientos y plantillas de seguimiento](save-traces-and-trace-templates.md)|Contiene información acerca de cómo guardar la salida del seguimiento y las definiciones de seguimiento en una plantilla.|  
|[Modificar plantillas de seguimiento](modify-trace-templates.md)|Contiene información acerca de cómo modificar plantillas de seguimiento mediante [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
|[Iniciar un seguimiento](start-a-trace.md)|Contiene información acerca de lo que ocurre cuando se inicia, pausa o detiene un seguimiento.|  
|[Correlacionar un seguimiento con los datos del registro de rendimiento de Windows](correlate-a-trace-with-windows-performance-log-data.md)|Contiene información acerca de la correlación de los datos del registro del rendimiento de Windows con un seguimiento mediante el Analizador de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Ver y analizar seguimientos con SQL Server Profiler](view-and-analyze-traces-with-sql-server-profiler.md)|Contiene información acerca del uso de seguimientos para solucionar problemas de datos, mostrando los nombres de los objetos de un seguimiento y localizando los eventos de un seguimiento.|  
|[Analizar interbloqueos con SQL Server Profiler](analyze-deadlocks-with-sql-server-profiler.md)|Contiene información acerca del uso del [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] para identificar la causa de un interbloqueo.|  
|[Analizar consultas con resultados de SHOWPLAN en SQL Server Profiler](analyze-queries-with-showplan-results-in-sql-server-profiler.md)|Contiene información acerca del uso del [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] para recopilar y mostrar el resultado del plan de presentación y de las estadísticas del plan de presentación.|  
|[Filtrar seguimientos con SQL Server Profiler](filter-traces-with-sql-server-profiler.md)|Contiene información acerca del establecimiento de filtros en columnas de datos para filtrar la salida del seguimiento mediante el [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Reproducir seguimientos](replay-traces.md)|Contiene información que explica lo que significa la reproducción de un seguimiento y qué es necesario para reproducir un seguimiento.|  
  
## <a name="see-also"></a>Consulte también  
 [SQL Server Profiler](sql-server-profiler.md)   
 [Iniciar SQL Server Profiler](start-sql-server-profiler.md)  
  
  
