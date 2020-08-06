---
title: Tarea Reducir base de datos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.shrinkdatabasetask.f1
helpviewer_keywords:
- Shrink Database task
- database shrinking [Integration Services]
- shrinking databases
ms.assetid: e66286f8-97b1-4e5a-86b4-e56f1932b7d5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 587777928e362e87e4b691e3c46167c1239984cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676123"
---
# <a name="shrink-database-task"></a>Reducir base de datos, tarea
  La tarea Reducir base de datos reduce el tamaño de los datos y los archivos de registro de bases de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Un paquete puede utilizar la tarea Reducir base de datos para reducir los archivos de una o varias bases de datos.  
  
 La reducción de los archivos de datos permite recuperar espacio moviendo páginas de datos del final del archivo a espacio desocupado próximo al principio del archivo. Cuando se crea suficiente espacio disponible al final del archivo, las páginas de datos situadas al final del mismo se pueden desasignar y devolver al sistema de archivos.  
  
> [!WARNING]  
>  Los datos que se mueven para reducir un archivo se pueden dispersar en cualquier ubicación disponible en el archivo. Esto produce la fragmentación de índices y puede reducir el rendimiento de las consultas que buscan un intervalo del índice. Para eliminar la fragmentación, considere la posibilidad de volver a generar los índices en el archivo después de la reducción.  
  
## <a name="commands"></a>Comandos:  
 La tarea Reducir base de datos encapsula un comando DBCC SHRINKDATABASE, que incluye los siguientes argumentos y opciones:  
  
-   *database_name*  
  
-   *target_percent*  
  
-   NOTRUNCATE o TRUNCATEONLY.  
  
 Si la tarea Reducir base de datos reduce varias bases de datos, la tarea ejecuta varios comandos SHRINKDATABASE, uno para cada una de las bases de datos. Todas las instancias del comando SHRINKDATABASE usan los mismos valores para los argumentos, excepto para el argumento *database_name* . Para obtener más información, vea [DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql).  
  
## <a name="configuration-of-the-shrink-database-task"></a>Configuración de la tarea Reducir base de datos  
 Puede establecer propiedades a través del Diseñador [!INCLUDE[ssIS](../../../includes/ssis-md.md)] . Esta tarea se encuentra en la sección **Tareas del plan de mantenimiento** del **Cuadro de herramientas** , en el Diseñador [!INCLUDE[ssIS](../../../includes/ssis-md.md)] .  
  
 Para obtener más información acerca de las propiedades que puede establecer en el Diseñador [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , haga clic en el tema siguiente:  
  
-   [Tarea Reducir base de datos &#40;Plan de mantenimiento&#41;](../../relational-databases/maintenance-plans/shrink-database-task-maintenance-plan.md)  
  
 Para obtener más información sobre cómo configurar estas propiedades en el Diseñador [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , haga clic en el tema siguiente:  
  
-   [Establecer las propiedades de tareas o contenedores](../set-the-properties-of-a-task-or-container.md)  
  
  
