---
title: Insertar o eliminar una columna (Generador de informes y SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e9db79e2-7e7d-4359-a706-cb746c94182a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9a6f782dbb6cc1024583926aafe4bab1cfe2d042
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87749097"
---
# <a name="insert-or-delete-a-column-report-builder-and-ssrs"></a>Insertar o eliminar una columna (Generador de informes y SSRS)
  Puede agregar o eliminar columnas en una región de datos Tablix. La región de datos Tablix puede ser una tabla, una matriz o una lista. Los procedimientos siguientes no se aplican a las regiones de datos Gráfico y Medidor.  
  
 En una región de datos Tablix, puede agregar columnas que están asociadas a un grupo (dentro de un grupo) o que no están asociadas a un grupo (fuera de un grupo). Una columna que está dentro de un grupo se repite una vez para cada valor de grupo único. Por ejemplo, una columna dentro de un grupo que está basada en el valor de una columna de datos que contiene nombres de colores se repite una vez para cada nombre de color. Para los grupos anidados, una columna puede estar fuera del grupo secundario, pero dentro del grupo primario. En este caso, la fila se repite una vez para cada valor único del grupo primario.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-select-a-data-region-so-that-the-row-and-column-handles-appear"></a>Para seleccionar una región de datos con objeto de que aparezcan los identificadores de columna y de fila  
  
-   En la vista Diseño, haga clic en la esquina superior izquierda de la región de datos Tablix para que los identificadores de columna y de fila aparezcan por encima y junto a ella.  
  
     Para obtener más información sobre las áreas de la región de datos, vea [listas &#40;generador de informes y SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md).  
  
### <a name="to-insert-a-column-in-a-selected-data-region"></a>Para insertar una columna en una región de datos seleccionada  
  
-   Haga clic con el botón derecho en el identificador de columna donde quiera insertar una columna, seleccione **Insertar columna**y, después, haga clic en **Izquierda** o **Derecha**.  
  
     -- o --  
  
-   Haga clic con el botón derecho en una celda de la región de datos donde quiera insertar una fila, seleccione **Insertar columna**y, después, haga clic en **Izquierda** o **Derecha**.  
  
### <a name="to-delete-a-column-from-a-selected-data-region"></a>Para eliminar una columna de una región de datos seleccionada  
  
-   Seleccione las columnas que quiera eliminar, haga clic con el botón derecho en el identificador de una de las columnas seleccionadas y, después, haga clic en **Eliminar columnas**.  
  
     -- o --  
  
-   Haga clic con el botón derecho en una celda de la región de datos de la que quiere eliminar una columna y, después, haga clic en **Eliminar columnas**.  
  
### <a name="to-insert-a-column-in-a-group-in-a-selected-data-region"></a>Para insertar una columna en un grupo de una región de datos seleccionada  
  
-   Haga clic con el botón derecho en una celda de grupo de columnas en el área de grupo de columnas de la región de datos Tablix donde quiera insertar una columna, seleccione **Insertar columna**y, después, haga clic en **Fuera del grupo - Izquierda**, **Dentro del grupo - Izquierda**, **Dentro del grupo - Derecha**o **Fuera del grupo - Derecha**.  
  
     Una vez hecho esto, se agrega una columna dentro o fuera del grupo representado por la celda de grupo de columnas sobre la que ha hecho clic.  
  
### <a name="to-delete-a-column-from-a-group-in-a-selected-data-region"></a>Para eliminar una columna de un grupo en una región de datos seleccionada  
  
-   Haga clic con el botón derecho en una celda de grupo de columnas en el área de grupo de columnas de la región de datos Tablix de la que quiera eliminar una columna y, después, haga clic en **Eliminar columnas**.  
  
## <a name="see-also"></a>Consulte también  
 [Descripción de los grupos &#40;Generador de informes y SSRS&#41;](understanding-groups-report-builder-and-ssrs.md)   
 [Región de datos Tablix &#40;Generador de informes y SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [Tablas &#40;Generador de informes y SSRS&#41;](tables-report-builder-and-ssrs.md)   
 [Matrices &#40;Generador de informes y SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)   
 [Listas &#40;Generador de informes y SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Listas &#40;Generador de informes y SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
