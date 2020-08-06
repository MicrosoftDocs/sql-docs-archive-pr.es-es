---
title: Establecer y recuperar información de versión | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- historical information [SQL Server]
- source controls [SQL Server Management Studio], version information
- retrieving version information
- current file version information
- version control services [SQL Server], retrieving version information
- version control services [SQL Server], setting version information
- status information [SQL Server], source control files
- historical information [SQL Server], source control files
ms.assetid: c3f253c4-4e3d-48e8-8d90-bd6ee899faf7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: eff3d40ba9b663ba8611508c5b9f0c9961005b81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744291"
---
# <a name="set-and-retrieve-version-information"></a>Establecer y recuperar información de versión
  La información de versión incluye el historial y el estado actual de un archivo controlado por código fuente. [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe conserva un historial completo de cada archivo controlado por código fuente, lo que permite realizar un seguimiento de la evolución de uno o más archivos a lo largo del tiempo. Además, esta información se puede utilizar para recuperar una copia local de cualquier versión del archivo o para comparar dos versiones cualesquiera.  
  
 El historial de un archivo incluye:  
  
-   El número de versión, que identifica su secuencia entre otras versiones del mismo archivo.  
  
-   acción realizada. Las operaciones realizadas incluyen la creación del archivo, la protección y la eliminación.  
  
-   El nombre de usuario de la persona que realizó una acción con el archivo.  
  
-   La fecha y la hora en que se realizó la operación.  
  
 Visual SourceSafe también conserva información de estado actual sobre la solución cargada. Esta información proporciona una instantánea del estado actual del archivo, lo que incluye:  
  
-   La identidad del usuario que tiene desprotegido el archivo.  
  
-   El número de la última versión del archivo seleccionado.  
  
-   La fecha en la que se creó la versión.  
  
-   Los comentarios de usuario asociados a la versión.  
  
-   Las rutas de acceso a los proyectos que comparten el archivo.  
  
## <a name="in-this-section"></a>En esta sección  
  
-   [Ver el historial de un archivo](../../2014/database-engine/view-file-history.md)  
  
-   [Ver el historial del proyecto](../../2014/database-engine/view-project-history.md)  
  
-   [Ver el estado de archivo](../../2014/database-engine/view-file-status.md)  
  
-   [Recuperar archivos](../../2014/database-engine/retrieve-files.md)  
  
-   [Especificar una versión como última versión](../../2014/database-engine/specify-a-version-as-the-latest-version.md)  
  
-   [Comparar archivos](../../2014/database-engine/compare-files.md)  
  
-   [Compartir archivos](../../2014/database-engine/share-files.md)  
  
-   [Crear informes de historial y estado](../../2014/database-engine/create-history-and-status-reports.md)  
  
## <a name="see-also"></a>Consulte también  
 [Fundamentos del control de código fuente](../../2014/database-engine/source-control-basics.md)  
  
  
