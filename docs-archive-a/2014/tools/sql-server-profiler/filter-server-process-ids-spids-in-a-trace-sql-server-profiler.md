---
title: Filtrar los Id. de proceso de servidor (SPID) en un seguimiento (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], traces
- filters [SQL Server], SPIDs
- traces [SQL Server], filters
ms.assetid: f5945c39-be6b-4632-91cb-92066c80e188
author: stevestein
ms.author: sstein
ms.openlocfilehash: 99ae7eac6f19bd942a04f97b0a7da580eadc9dbf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87749003"
---
# <a name="filter-server-process-ids-spids-in-a-trace-sql-server-profiler"></a>Filtrar los Id. de proceso de servidor (SPID) en un seguimiento (SQL Server Profiler)
  En este tema se describe cómo filtrar identificadores de proceso de servidor (SPID) en un seguimiento mediante el [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-filter-system-ids-in-a-trace"></a>Para filtrar identificadores de sistema en un seguimiento  
  
1.  En el menú **Archivo** , haga clic en **Nuevo seguimiento**y, a continuación, conéctese a una instancia de SQL Server.  
  
     Aparecerá el cuadro de diálogo **Propiedades de seguimiento**.  
  
    > [!NOTE]  
    >  Si está seleccionada la opción **iniciar el seguimiento inmediatamente después de establecer la conexión**, el cuadro de diálogo Propiedades de **seguimiento**no aparecerá y, en su lugar, se iniciará el seguimiento. Para desactivar esta configuración, en el menú **Herramientas**, haga clic en **Opciones**y desactive la casilla **Iniciar el seguimiento inmediatamente tras realizar la conexión** .  
  
2.  En el cuadro **Nombre de seguimiento** , escriba un nombre para el seguimiento.  
  
3.  En el cuadro **Use the template**(Usar la plantilla), seleccione una plantilla de seguimiento.  
  
4.  Opcionalmente, especifique una tabla o un archivo de destino donde guardar los resultados del seguimiento.  
  
5.  En el menú **Selección de eventos**, haga clic en el encabezado de la columna **SPID**para mostrar el cuadro de diálogo **Editar filtro** . También puede hacer clic con el botón derecho en el encabezado de la columna y seleccionar **Editar filtro de columna**. Si no aparece la columna **SPID** , active la casilla **Mostrar todas las columnas** .  
  
6.  En el cuadro de diálogo **Editar filtro** , expanda el operador de comparación adecuado y especifique un SPID como valor para la comparación.  
  
## <a name="see-also"></a>Consulte también  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
