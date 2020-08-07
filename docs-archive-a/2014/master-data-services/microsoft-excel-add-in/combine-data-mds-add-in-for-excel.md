---
title: Combinar datos (Complemento MDS para Excel) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: a867dc15-5a0d-457c-8304-ac323bcf9377
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bc2d5bffb6d7a12164a8643e9a790b32538f8979
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745357"
---
# <a name="combine-data-mds-add-in-for-excel"></a>Combinar datos (Complemento MDS para Excel)
  En [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], combine los datos de dos hojas de cálculo si desea comparar los datos antes de publicarlos. En este procedimiento, se combinan los datos de dos hojas de cálculo en una. Puede realizar otras comparaciones y determinar qué datos publicar en el repositorio MDS.  
  
## <a name="prerequisites"></a>Requisitos previos  
  
-   Debe tener una hoja de cálculo activa que contenga los datos administrados por MDS. Para obtener más información, consulte [carga de datos de MDS en Excel](export-data-to-excel-from-master-data-services.md).  
  
-   Debe tener una hoja de cálculo que contenga los datos que desea combinar con los datos administrados por MDS. Esta hoja debe tener una fila de encabezado.  
  
### <a name="to-combine-non-managed-data-into-an-mds-managed-sheet"></a>Para combinar los datos no administrados en una hoja administrada por MDS  
  
1.  En la hoja que contiene los datos administrados por MDS, en el grupo **Publicar y validar** , haga clic en **Combinar datos**.  
  
2.  En el cuadro de diálogo **Combinar datos** , junto al cuadro de texto **Intervalo para combinar con los datos MDS** , haga clic en el icono. El cuadro de diálogo se contrae.  
  
3.  Haga clic en la hoja que contiene los datos que desea combinar.  
  
4.  Resalte todas las celdas de la hoja que desea combinar, incluida la fila de encabezado.  
  
5.  En el cuadro de diálogo **Combinar datos** , haga clic en el icono. El cuadro de diálogo se expande.  
  
6.  Para una columna enumerada para la entidad MDS, seleccione una columna debajo de **Columna correspondiente**. Ninguna columna MDS necesita las columnas correspondientes.  
  
7.  Haga clic en **Combinar**. Se muestra una columna **SOURCE** , que indica si los datos son de MDS o un origen externo.  
  
## <a name="next-steps"></a>Pasos siguientes  
  
-   Para buscar similitudes entre los datos administrados por MDS y los datos externos, vea [Coincidir datos similares &#40;Complemento MDS para Excel&#41;](match-similar-data-mds-add-in-for-excel.md).  
  
## <a name="see-also"></a>Consulte también  
 [Cargando datos &#40;Complemento MDS para Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Coincidencia de calidad de datos en el Complemento MDS para Excel](data-quality-matching-in-the-mds-add-in-for-excel.md)  
  
  
