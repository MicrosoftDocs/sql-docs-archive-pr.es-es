---
title: Guardar gráficos de interbloqueo (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- deadlocks [SQL Server], saving deadlock graphs
- graphs [SQL Server]
- saving deadlock graphs
ms.assetid: bf1fc906-abd6-4a89-842e-da0d66b2defe
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cdd0bd808ba4b934e5b2d91c9079909acf6e3997
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674769"
---
# <a name="save-deadlock-graphs-sql-server-profiler"></a>Guardar gráficos de interbloqueo (SQL Server Profiler)
  En este tema se explica cómo guardar un gráfico de interbloqueo mediante el [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Los gráficos de interbloqueo se guardan como archivos XML.  
  
### <a name="to-save-deadlock-graph-events-separately"></a>Para guardar eventos deadlock graph por separado  
  
1.  En el menú **Archivo** , haga clic en **Nuevo seguimiento**y, a continuación, conéctese a una instancia de SQL Server.  
  
     Aparecerá el cuadro de diálogo **Propiedades de seguimiento**.  
  
    > [!NOTE]  
    >  Si se selecciona **Iniciar el seguimiento inmediatamente tras realizar la conexión** , el cuadro de diálogo **Propiedades de seguimiento**no aparecerá y, en su lugar, se iniciará el seguimiento. Para desactivar esta configuración, en el menú **Herramientas**, haga clic en **Opciones**y desactive la casilla **Iniciar el seguimiento inmediatamente tras realizar la conexión** .  
  
2.  En el cuadro de diálogo Propiedades de seguimiento, en el cuadro**Nombre de seguimiento** , escriba un nombre para el seguimiento.  
  
3.  En la lista **Usar la plantilla** , seleccione la plantilla de seguimiento que desea utilizar para el seguimiento o seleccione la opción **En blanco** si no desea utilizar ninguna plantilla.  
  
4.  Lleve a cabo una de las siguientes acciones:  
  
    -   Active la casilla**Guardar en archivo** para capturar el seguimiento en un archivo. Especifique un valor en **Establecer el tamaño máximo de archivo (MB)** .  
  
         Si lo desea, seleccione **Habilitar sustitución incremental de archivos** y **El servidor procesa los datos de seguimiento**.  
  
    -   Active la casilla **Guardar en tabla** para capturar el seguimiento en una tabla de base de datos.  
  
         Opcionalmente, haga clic en **establecer número máximo de filas**y especifique un valor.  
  
5.  Opcionalmente, active la casilla **Habilitar hora de detención de seguimiento** para especificar una fecha y hora de detención.  
  
6.  Haga clic en la pestaña **Selección de eventos**.  
  
7.  En el cuadro de diálogo **Eventos**, expanda la categoría de evento **Bloqueos**y, luego, active la casilla **Deadlock graph**. Si la categoría de eventos Bloqueos no está disponible, seleccione la opción **Mostrar todos los eventos** para mostrarla.  
  
     Aparecerá el cuadro de diálogo **Configuración de extracción de eventos**se agrega al cuadro de diálogo **Propiedades de seguimiento**.  
  
8.  En el menú **Configuración de extracción de eventos**, haga clic en **Guardar eventos XML de interbloqueo por separado**.  
  
9. En el cuadro de diálogo **Guardar como** , escriba el nombre del archivo donde desee almacenar los eventos deadlock graph.  
  
10. Haga clic en **Todos los lotes XML de interbloqueo en un solo archivo** para guardar todos los eventos deadlock graph en un solo archivo XML, o bien haga clic en **Cada lote XML de interbloqueo en un archivo independiente**para crear un nuevo archivo XML para cada evento deadlock graph.  
  
 Una vez guardado el archivo de interbloqueo, puede abrir el archivo en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Para obtener más información, vea [abrir, ver e imprimir un archivo de Interbloqueo &#40;SQL Server Management Studio&#41;](open-view-and-print-a-deadlock-file-sql-server-management-studio.md).  
  
## <a name="see-also"></a>Consulte también  
 [Analizar interbloqueos con SQL Server Profiler](../../tools/sql-server-profiler/analyze-deadlocks-with-sql-server-profiler.md)  
  
  
