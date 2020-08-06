---
title: Visor de conflictos de replicación de Microsoft (Replicación transaccional) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replconflictviewer.cvqueued.f1
ms.assetid: eec59d8e-cadb-4623-a31f-9f42ec09c97f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8cc3f2ea3d1d2b29fba9c9d9121e23bf4bcd88bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661946"
---
# <a name="microsoft-replication-conflict-viewer-transactional-replication"></a>Visor de conflictos de replicación de Microsoft (Replicación transaccional)
  El Visor de conflictos de replicación permite ver los conflictos surgidos durante la sincronización de la replicación transaccional punto a punto y la replicación transaccional con suscripciones de actualización en cola. Para obtener más información, vea [Ver conflictos de datos para publicaciones transaccionales &#40;SQL Server Management Studio&#41;](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md).  
  
> [!NOTE]  
>  El Visor de conflictos de replicación muestra los conflictos que se producen durante la replicación de mezcla y la replicación transaccional. Para la replicación transaccional, puede utilizarse el Visor de conflictos de replicación para ver los datos de los conflictos, pero no puede elegir una resolución distinta para el conflicto.  
  
## <a name="options"></a>Opciones  
 El Visor de conflictos de replicación está dividido en dos secciones. La sección superior del cuadro de diálogo muestra la lista de conflictos de la tabla seleccionada. Si hace clic en un elemento de la lista de conflictos, se mostrarán los detalles del conflicto en la sección inferior del cuadro de diálogo.  
  
 Los datos del conflicto de la sección inferior se muestran en las dos columnas correspondientes (**Ganador del conflicto** y **Perdedor del conflicto**). Si el conflicto se produce entre datos actualizados y eliminados, es posible que no haya datos que mostrar en el lado eliminado del conflicto. En este caso, el Visor de conflictos de replicación muestra un mensaje en una de las columnas en el que indica que se eliminó la fila en una ubicación y se actualizó en otra. También indica la resolución recomendada.  
  
 **Base de datos**  
 Elija una base de datos que contenga publicaciones con conflictos.  
  
 **Publicación**  
 Elija una publicación que contenga tablas con conflictos.  
  
 **Tabla**  
 Elija una tabla que contenga conflictos.  
  
 **Definir filtro**  
 Haga clic para abrir el cuadro de diálogo **Definir filtros** .  
  
 **Aplicar o quitar filtro**  
 Haga clic para aplicar o quitar un filtro definido en el cuadro de diálogo **Definir filtros** .  
  
 **Seleccionar todo**  
 Haga clic para seleccionar todos los conflictos mostrados en la cuadrícula.  
  
 **Seleccione ninguno**  
 Haga clic para anular la selección de todos los conflictos mostrados en la cuadrícula.  
  
 **Remove**  
 Haga clic en esta opción para quitar los conflictos seleccionados del visor y los metadatos asociados de las tablas del sistema de replicación.  
  
 **Mostrar todas las columnas**  
 Seleccione esta opción para mostrar todas las columnas de la tabla.  
  
 **Mostrar las primeras cinco columnas y el resto de las columnas con datos en conflicto**  
 Seleccione esta opción para mostrar las cinco primeras columnas y otras columnas con conflictos. Resulta útil si las tablas presentan un número elevado de columnas y solo desea ver las columnas más importantes para solucionar el conflicto. Las cinco primeras columnas se incluyen en esta vista, como campos que identifican una fila, como la clave principal o campos de nombre, que con frecuencia se encuentran entre las cinco primeras columnas de la tabla.  
  
 **Mostrar información de columna** (**...**)  
 Haga clic para ver la información de la columna: **Nombre de tabla**, **Nombre de columna**, **Tipo de datos**y **Valor de columna**.  
  
 **Registrar los detalles de este conflicto**  
 Active esta casilla para registrar los detalles del conflicto en un archivo. Para especificar la ubicación del archivo, señale el menú **Ver** y haga clic en **Opciones**. Escriba un valor o haga clic en el botón de búsqueda (**...**) y navegue hasta encontrar el archivo adecuado. Haga clic en **Aceptar** para salir del cuadro de diálogo **Opciones** .  
  
## <a name="see-also"></a>Consulte también  
 [Detección de conflictos en la replicación punto a punto](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)   
 [Ver conflictos de datos para publicaciones transaccionales &#40;SQL Server Management Studio&#41;](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)  
  
  
