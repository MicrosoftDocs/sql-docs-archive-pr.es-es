---
title: Reconciliar los cambios realizados por varios usuarios (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- table modifications [SQL Server], multiple users
- reconciling changes made by multiple users
- modifications made by multiple users
ms.assetid: fc7ed4f2-ad3d-47fc-a3ef-51e5bb069ef0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 337d505fce474a33301c18313fe6137f6bc0ec1b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744944"
---
# <a name="reconcile-changes-made-by-multiple-users-visual-database-tools"></a>Reconciliar los cambios realizados por varios usuarios (Visual Database Tools)
  En un entorno multiusuario, varios usuarios pueden realizar cambios en el mismo objeto al mismo tiempo. Esto puede ocurrir cuando se trabaja en la estructura del objeto en los diseñadores de diagramas de base de datos o tablas, o con los valores de los resultados que devuelve el panel Resultados del Diseñador de consultas y vistas. Esto puede ocasionar conflictos que es necesario solucionar.  
  
## <a name="conflicts-in-the-table-or-database-diagram-designers"></a>Conflictos en los diseñadores de diagramas de base de datos o tablas  
 Por ejemplo, otro usuario podría eliminar o cambiar el nombre de una tabla mientras está trabajando con esa tabla o con una tabla relacionada en el Diseñador de tablas. Al intentar guardar la tabla, el [Cuadro de diálogo Se han detectado cambios en la base de datos &#40;Visual Database Tools&#41;](visual-database-tools.md) le informará que la base de datos se actualizó desde que se abrió la tabla.  
  
 Este cuadro de diálogo también muestra una lista de objetos de base de datos que se verán afectados como resultado de guardar la tabla. En este momento, puede realizar una de las siguientes acciones:  
  
-   Elija **Sí** para guardar la tabla y actualizar la base de datos con todos los cambios de la lista.  
  
     Esta acción puede afectar a las tablas que comparten los mismos objetos de base de datos. Por ejemplo, supongamos que edita la columna `au`_`id` de la tabla `titleauthors` mientras otro usuario trabaja con la tabla `authors` , que está relacionada con la tabla `titleauthors` mediante la columna `au`\_`id` . Si guarda la tabla, se verá afectada la tabla del otro usuario. De igual manera, supongamos que otro usuario ha definido una restricción CHECK para la columna `qty` de la tabla `sales` . Si elimina la columna `qty` y guarda la tabla `sales` , la restricción CHECK del otro usuario se verá afectada.  
  
-   Elija **No** para cancelar la acción de guardar.  
  
     A continuación, puede cerrar la tabla sin guardarla. Cuando vuelva a abrir la tabla, coincidirá con el contenido de la base de datos.  
  
-   Elija **Guardar archivo de texto** para guardar una lista de los cambios.  
  
     Puede guardar la lista de los cambios de la base de datos que se muestran en el cuadro de diálogo **Se han detectado cambios en la base de datos** en un archivo de texto para poder investigar la causa de los cambios de otros usuarios. Por ejemplo, si otro usuario ha editado una tabla que usted marcó para eliminar, es posible que desee comprobar si debe eliminarse la tabla antes de actualizar la base de datos.  
  
## <a name="conflicts-in-the-query-and-view-designer"></a>Conflictos en el Diseñador de consultas y vistas  
 Si ejecuta una consulta o devuelve los resultados de una vista, los datos se muestran en el [panel Resultados](results-pane-visual-database-tools.md). Varios usuarios pueden trabajar en el mismo conjunto de datos al mismo tiempo, lo cual puede ocasionar conflictos.  
  
 Por ejemplo, supongamos que usted y un colega ejecutan una consulta cada uno para mostrar todos los datos de la tabla `titleauthors` . Su colega cambia el nombre del primer registro devuelto de Barb a Barbara. En ese momento el valor que hay en ese campo de la base de datos es Barbara, aunque en su conjunto de resultados siga apareciendo Barb. A continuación, escribe Bárbara y hace clic fuera de de la fila. Recibirá un mensaje que le preguntará cómo desea solucionar el conflicto.  
  
-   Haga clic en **Sí** para actualizar la base de datos con los cambios.  
  
     Con ello, se reemplazarán los cambios de su colega.  
  
-   Haga clic en **No** para actualizar el conjunto de resultados de modo que coincida con lo que hay actualmente en la base de datos.  
  
     Con ello, se reemplazarán sus cambios por los de su colega.  
  
-   Haga clic en **Cancelar** para continuar la edición sin solucionar el conflicto.  
  
     En este caso, no podrá confirmar sus cambios en la base de datos.  
  
## <a name="see-also"></a>Consulte también  
 [Cuadro de diálogo Se han detectado cambios en la base de datos &#40;Visual Database Tools&#41;](visual-database-tools.md)  
  
  
