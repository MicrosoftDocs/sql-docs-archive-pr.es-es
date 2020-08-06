---
title: Explorar la flexibilidad de una región de datos Tablix (Generador de informes y SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fef19359-a618-4d21-a7e4-e391cdefd4eb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c30a5b75732bd0729ecff39fea5efde21a45607a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743978"
---
# <a name="exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs"></a>Explorar la flexibilidad de una región de datos Tablix (Generador de informes y SSRS)
  Cuando agrega una región de datos de lista, tabla o matriz desde la pestaña Insertar en la cinta de opciones, empieza por una plantilla inicial para una región de datos Tablix, pero no está limitado por esa plantilla. Puede seguir definiendo cómo se muestran los datos agregando o quitando características de la región de datos Tablix tales como grupos, filas y columnas.  
  
 Al eliminar una grupo de filas o de columnas, tiene la opción de eliminar las filas y columnas que se usan para mostrar los valores de grupo. También puede agregar o quitar filas y columnas de forma manual. Para entender cómo se usan las filas y las columnas al mostrar datos detallados y de grupo, vea [Región de datos Tablix &#40;Generador de informes y SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md).  
  
 Una vez modificada la estructura de la región de datos Tablix, puede establecer propiedades para ayudar a controlar la manera en la que el informe representa la región de datos; por ejemplo, puede repetir los encabezados de columna en la parte superior de cada página, o mantener un encabezado de grupo con el grupo. Para más información, vea [Controlar la presentación de la región de datos Tablix en una página de informe &#40;Generador de informes y SSRS&#41;](controlling-the-tablix-data-region-display-on-a-report-page.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="changing-a-table-to-a-matrix"></a>Convertir una tabla en una matriz  
 De forma predeterminada, una tabla tiene filas de detalles que muestran los valores del conjunto de datos de informe. Normalmente, una tabla incluye grupos de filas que organizan los datos detallados por grupo y, a continuación, incluye valores agregados basados en cada uno de los grupos. Para convertir la tabla en una matriz, agregue grupos de columnas. Normalmente, se quitará el grupo de detalles cuando la región de datos tenga grupos de filas y de columnas con el fin de mostrar solo los valores de resumen para los grupos. Para obtener más información, vea [Agregar o eliminar un grupo en una región de datos &#40;generador de informes y SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md).  
  
 Por definición, cuando se crea una matriz, se agrega una celda de la esquina del Tablix. Puede combinar las celdas de esta área y agregar una etiqueta. Para más información, vea [Combinar celdas en una región de datos &#40;Generador de informes y SSRS&#41;](merge-cells-in-a-data-region-report-builder-and-ssrs.md).  
  
## <a name="changing-a-matrix-to-a-table"></a>Convertir una matriz en una tabla  
 De forma predeterminada, una matriz tiene grupos de filas y de columnas, pero ningún grupo de detalles. Para convertir una matriz en una tabla, quite los grupos de columnas y agregue un grupo de detalles para que aparezca en la fila de detalles. Para más información, vea [Agregar o eliminar un grupo en una región de datos &#40;Generador de informes y SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) y [Agregar un grupo de detalles &#40;Generador de informes y SSRS&#41;](add-a-details-group-report-builder-and-ssrs.md).  
  
## <a name="changing-a-default-list-to-a-grouped-list"></a>Convertir una lista predeterminada en una lista agrupada  
 De forma predeterminada, una lista tiene filas de detalles, pero ningún grupo. Para modificar la lista de tal forma que use una fila de grupo, cambie el nombre del grupo de detalles y especifique una expresión de grupo. Para más información, vea [Agregar o eliminar un grupo en una región de datos &#40;Generador de informes y SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md).  
  
## <a name="creating-stepped-displays"></a>Crear visualizaciones escalonadas  
 De forma predeterminada, cuando se agregan grupos a una región de datos Tablix, las celdas del área de encabezado del grupo de filas muestran valores de grupo en la columna. Si dispone de varios grupos anidados, cada uno de ellos se muestra en una columna independiente. Para crear una presentación escalonada, quite todas las columnas de grupo excepto una y dé formato a la columna restante para que muestre la jerarquía de grupos como una presentación de texto con sangría. Para más información, vea [Crear un informe escalonado &#40;Generador de informes y SSRS&#41;](create-a-stepped-report-report-builder-and-ssrs.md).  
  
## <a name="adding-an-adjacent-details-group"></a>Agregar un grupo de detalles adyacente  
 De forma predeterminada, el grupo de detalles es el grupo secundario más interior de una jerarquía de grupos. No se puede anidar un grupo debajo del grupo de detalles. Puede crear grupos de detalles adyacentes adicionales; por ejemplo, para mostrar los 5 productos más vendidos y los 5 menos vendidos. Dado que puede agregar expresiones de filtro y de ordenación en cada grupo, puede mostrar dos vistas de datos detallados del mismo conjunto de datos en una región de datos Tablix. Para más información, vea [Descripción de los grupos &#40;Generador de informes y SSRS&#41;](understanding-groups-report-builder-and-ssrs.md), [Agregar o eliminar un grupo en una región de datos &#40;Generador de informes y SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) y [Agregar un filtro a un conjunto de datos &#40;Generador de informes y SSRS&#41;](../report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Consulte también  
 [&#40;de la región de datos Tablix Generador de informes y SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [Enumera &#40;Generador de informes y SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Tablas &#40;Generador de informes y SSRS&#41;](tables-report-builder-and-ssrs.md)   
 [Matrices &#40;Generador de informes y SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)   
 [Listas &#40;Generador de informes y SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
  
