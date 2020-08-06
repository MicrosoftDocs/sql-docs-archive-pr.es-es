---
title: Guardar de forma separada eventos Showplan XML Statistics Profile (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Showplan XML events
- saving Showplan XML events
- events [SQL Server], Showplan XML
ms.assetid: df393f13-d538-4d94-8155-9c2fdf5f755d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: be0c02f8396df81af803c365b9ede42610353ed3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746261"
---
# <a name="save-showplan-xml-statistics-profile-events-separately-sql-server-profiler"></a>Guardar de forma separada eventos Showplan XML Statistics Profile (SQL Server Profiler)
  En este tema se describe el modo de guardar eventos **Showplan XML Statistics Profile** capturados en seguimientos en archivos .SQLPlan diferentes mediante el uso del [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Puede abrir los archivos de eventos **Showplan XML Statistics Profile** en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], que le permite ver el plan de ejecución gráfico de cada evento.  
  
### <a name="to-save-showplan-xml-statistics-events-separately"></a>Para guardar eventos Showplan XML Statistics Profile por separado  
  
1.  En el menú **Archivo** , haga clic en **Nuevo seguimiento**y conéctese a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Aparecerá el cuadro de diálogo **Propiedades de seguimiento** .  
  
    > [!NOTE]  
    >  Si activa **Iniciar el seguimiento inmediatamente tras realizar la conexión**, no aparecerá el cuadro de diálogo **Propiedades de seguimiento**y, en su lugar, comenzará el seguimiento. Para desactivar esta configuración, en el menú **Herramientas**, haga clic en **Opciones**y desactive la casilla **Iniciar el seguimiento inmediatamente tras realizar la conexión** .  
  
2.  En el cuadro de diálogo **Propiedades de seguimiento** , en el cuadro **Nombre de seguimiento** , escriba un nombre para el seguimiento.  
  
3.  En la lista **Usar la plantilla** , seleccione una plantilla de seguimiento o elija **En blanco** si no desea utilizar ninguna plantilla.  
  
4.  Lleve a cabo una de las siguientes acciones:  
  
    -   Haga clic en**Guardar en el archivo**para capturar el seguimiento en un archivo. Especifique un valor en **Establecer el tamaño máximo de archivo (MB)** .  
  
         Opcionalmente, seleccione **Habilitar sustitución incremental de archivos** y el **servidor procesa los datos de seguimiento**.  
  
    -   Haga clic en**Guardar en la tabla** para capturar el seguimiento en una tabla de base de datos.  
  
         De forma opcional, haga clic en **Establecer número máximo de filas (en miles)** y especifique un valor.  
  
5.  Opcionalmente, active la casilla **Habilitar hora de detención de seguimiento** y especifique una fecha y hora de detención.  
  
6.  Haga clic en la pestaña **Selección de eventos**.  
  
7.  En el cuadro de diálogo **Eventos**, expanda la categoría de evento **Rendimiento**y, a continuación, active la casilla **Showplan XML Statistics Profile**. Si la categoría de evento **Rendimiento** no está disponible, active la casilla **Mostrar todos los eventos** para mostrarla.  
  
     Aparecerá el cuadro de diálogo **Configuración de extracción de eventos**se agrega al cuadro de diálogo **Propiedades de seguimiento**.  
  
8.  En el menú **Configuración de extracción de eventos**, haga clic en **Guardar eventos de plan de presentación XML por separado**.  
  
9. En el cuadro de diálogo **Guardar como** , especifique el nombre de archivo para guardar los eventos **Showplan XML Statistics Profile** .  
  
10. Haga clic en **Todos los lotes de plan de presentación en un solo archivo** para guardar todos los eventos **Showplan XML Statistics Profile** en un único archivo XML, o bien haga clic en **Cada lote de plan de presentación en un archivo independiente**para crear un archivo XML para cada evento **Showplan XML Statistics Profile** .  
  
11. Para ver el archivo del evento **Showplan XML Statistics Profile** en SQL Server Management Studio, en el menú **Archivo** , seleccione **Abrir**y haga clic en **Archivo**. Diríjase al directorio en que guardó el archivo o archivos de eventos **Showplan XML Statistics Profile** para seleccionar un archivo y abrirlo. Los archivos de eventos**Showplan XML Statistics Profile** tienen una extensión de archivo .SQLPlan.  
  
## <a name="see-also"></a>Consulte también  
 [Analizar consultas con resultados de SHOWPLAN en SQL Server Profiler](../../tools/sql-server-profiler/analyze-queries-with-showplan-results-in-sql-server-profiler.md)  
  
  
