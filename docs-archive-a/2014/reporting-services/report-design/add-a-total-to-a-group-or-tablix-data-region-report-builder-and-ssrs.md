---
title: Agregar un total a un grupo o a una región de datos Tablix (Generador de informes y SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: cf1b96c3-7f0f-4c94-ad08-5239c77ccfe4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f626621a37a327ae32664ab9444e72ce4931ac0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662555"
---
# <a name="add-a-total-to-a-group-or-tablix-data-region-report-builder-and-ssrs"></a>Agregar un total a un grupo o a una región de datos Tablix (Generador de informes y SSRS)
  Puede agregar totales en una región de datos Tablix solo para un grupo o para toda la región de datos. De forma predeterminada, un total es la suma de los datos numéricos no NULL de un grupo o de la región de datos, una vez aplicados los filtros. Para agregar totales a un grupo, haga clic en **Agregar total** en el menú contextual del grupo en el panel Agrupación. Para agregar totales a una celda individual en el área del cuerpo Tablix, haga clic en **Agregar total** en el menú contextual de la celda. El comando **Agregar total** es contextual y solo está habilitado para los campos numéricos. En función de la celda de Tablix seleccionada, puede agregar un total para una única celda, seleccionando una celda en el área del cuerpo de Tablix, o para el grupo completo, seleccionando una celda en el área del grupo de filas o del grupo de columnas de Tablix. Para obtener más información sobre las áreas de Tablix, vea [Región de datos Tablix &#40;Generador de informes y SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md).  
  
 Después de agregar un total, puede cambiar la función Sum predeterminada por una función de agregado diferente de la lista de funciones de informe integradas. Para obtener más información, vea [referencia a las funciones de agregado &#40;generador de informes y SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).[!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-total-for-an-individual-value-in-the-tablix-body-area"></a>Para agregar un total a un valor individual en el área del cuerpo de Tablix  
  
-   En el área del cuerpo de la región de datos Tablix, haga clic con el botón secundario en la celda donde desea agregar el total. La celda debe contener un campo numérico. Seleccione **Agregar total**y, a continuación, haga clic en **Fila** o **Columna**.  
  
     Se agrega a la región de datos una nueva fila o columna fuera del grupo actual, con un total predeterminado para el campo de la celda en la que hizo clic.  
  
     Si la región de datos Tablix es una tabla, automáticamente se agrega una fila.  
  
### <a name="to-add-totals-for-a-row-group"></a>Para agregar totales a un grupo de filas  
  
-   En el área de grupo de filas de la región de datos Tablix, haga clic con el botón derecho en una celda del área de grupo de filas cuyos totales quiere calcular, seleccione **Agregar total**y, luego, haga clic en **Antes** o **Después**.  
  
     Se agrega a la región de datos una nueva fila fuera del grupo actual y, a continuación, se agrega un total predeterminado para cada campo numérico de la fila.  
  
### <a name="to-add-totals-for-a-column-group"></a>Para agregar totales a un grupo de columnas  
  
-   En el área de grupo de filas de la región de datos Tablix, haga clic con el botón derecho en la celda del área de grupo de columnas cuyos totales quiere calcular, seleccione **Agregar total**y, luego, haga clic en **Antes** o **Después**.  
  
     Se agrega a la región de datos una nueva columna fuera del grupo actual y, a continuación, se agrega un total predeterminado para cada campo numérico de la columna.  
  
## <a name="see-also"></a>Consulte también  
 [Ámbito de expresión para los totales, agregados y colecciones integradas &#40;Generador de informes y SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)   
 [&#40;de la región de datos Tablix Generador de informes y SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [Tablas &#40;Generador de informes y SSRS&#41;](tables-report-builder-and-ssrs.md)   
 [Matrices &#40;Generador de informes y SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)   
 [Enumera &#40;Generador de informes y SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Tablas, matrices y listas &#40;Generador de informes y SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
