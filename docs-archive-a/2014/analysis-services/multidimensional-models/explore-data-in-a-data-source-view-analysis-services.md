---
title: Explorar datos en una vista del origen de datos (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- exploring data [Analysis Services]
- data source views [Analysis Services], exploring data
- viewing source data
ms.assetid: 2c922c35-fbcb-45b2-96b1-c7a846d8b419
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6adf9edecd807158ba1d0de3287cccd6fa8dd787
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87677902"
---
# <a name="explore-data-in-a-data-source-view-analysis-services"></a>Explorar datos en una vista del origen de datos (Analysis Services)
  Puede usar el cuadro de diálogo **Explorar datos** del Diseñador de vistas del origen de datos de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] para explorar los datos de una tabla, vista o consulta con nombre en una vista del origen de datos (DSV). Al explorar los datos en el Diseñador de vistas del origen de datos, puede ver el contenido de cada columna de datos de una tabla, vista o consulta con nombre seleccionada. Observar el contenido real le puede ayudar a determinar si todas las columnas son necesarias, si se necesitan cálculos con nombre para mejorar la facilidad de uso, y si los cálculos o consultas con nombre devuelven los valores previstos.  
  
 Para ver datos, debe tener una conexión activa con el origen u orígenes de datos del objeto seleccionado en la DSV. En la consulta también se envían todos los cálculos con nombre de la tabla.  
  
 Los datos se devuelven en formato tabular, y pueden ordenarse y copiarse. Haga clic en los encabezados de columna para reordenar las filas por esa columna. También puede resaltar datos en la cuadrícula y presionar Ctrl+C para copiar la selección en el portapapeles.  
  
 Asimismo, puede controlar el método de muestreo y el número de muestras. De forma predeterminada, se devuelven las 5000 principales filas.  
  
## <a name="to-browse-data-or-change-sampling-options"></a>Para examinar los datos o cambiar las opciones de muestreo  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], abra el proyecto o conéctese a la base de datos que contiene la vista del origen de datos en que desea examinar los datos.  
  
2.  En el Explorador de soluciones, expanda la carpeta **Vistas del origen de datos** y, después, haga doble clic en la vista del origen de datos.  
  
3.  Haga clic con el botón derecho en la tabla, vista o consulta con nombre que contiene los datos que quiere ver y, después, haga clic en **Explorar datos**.  
  
     El origen de datos subyacente de la tabla, vista o consulta con nombre de la vista del origen de datos es consultas y los resultados aparecen en la pestaña **explorar \<object name> tabla** .  
  
4.  En la barra de herramientas **explorar \<object name> tabla** , haga clic en el icono **Opciones de muestreo** .  
  
     Se abrirá el cuadro de diálogo **Opciones de exploración de datos** . En este cuadro de diálogo puede especificar el método de muestreo (más o menos registros que el tamaño de muestreo predeterminado de 5000 filas) o el número de muestras.  
  
5.  Haga clic en **Aceptar** o en **Cancelar** , según corresponda.  
  
6.  Para volver a muestrear los datos, haga clic en volver a **muestrear datos** en la barra de herramientas **explorar \<object name> tabla** .  
  
## <a name="see-also"></a>Consulte también  
 [Vistas del origen de datos en modelos multidimensionales](data-source-views-in-multidimensional-models.md)  
  
  
