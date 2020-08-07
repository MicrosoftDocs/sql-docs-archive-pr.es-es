---
title: Filtrar datos antes de cargarlos (Complemento MDS para Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9e30eae0-776b-4a09-aac3-0c0249d92ca5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6d0ccf667f37763326e27dcd8d0cfc005627ebc2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745858"
---
# <a name="filter-data-before-loading-mds-add-in-for-excel"></a>Filtrar datos antes de cargarlos (complemento MDS para Excel)
  En [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] , filtre los datos si desea limitar el tamaño o el ámbito de los datos que va a cargar en Excel.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para realizar este procedimiento:  
  
-   Debe disponer de permiso de acceso al área funcional **Explorador** .  
  
### <a name="to-filter-data-before-loading"></a>Para filtrar datos antes de cargarlos  
  
1.  Abra Excel y, en la pestaña **Datos maestros** , conéctese a un repositorio MDS. Para obtener más información, consulte [Conectarse a un repositorio MDS &#40;complemento MDS para Excel&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md).  
  
2.  En el panel **Explorador de datos maestros** , seleccione un modelo y una versión. La lista de entidades se rellena.  
  
    -   Si el panel **Explorador de datos maestros** no está visible, en el grupo **Conectar y cargar** , haga clic en **Mostrar explorador**.  
  
    -   Si el panel **Explorador de datos maestros** está deshabilitado, se debe a que la hoja existente ya contiene datos administrados por MDS. Para habilitar el panel, abra una nueva hoja de cálculo.  
  
3.  En el panel **Explorador de datos maestros** , en la lista de entidades, haga clic en la entidad que desea filtrar.  
  
4.  En la cinta de opciones, en el grupo **Conectar y cargar** , haga clic en **Filtro**.  
  
5.  Para completar el cuadro de diálogo **Filtro** , seleccione los atributos (columnas) para mostrar, establecer el orden de las columnas y, si es necesario, filtrar los datos de modo que se devuelvan menos filas. Vea en el panel **Resumen** cuántos datos se devolverán. Para más información, vea [Cuadro de diálogo Filtrar &#40;Complemento MDS para Excel&#41;](filter-dialog-box-mds-add-in-for-excel.md).  
  
6.  Haga clic en **Cargar datos**. La hoja se rellena con datos administrados por MDS.  
  
    > [!NOTE]  
    >  -   Solo se carga en Excel el primer millón de miembros.  
    > -   En las columnas que son listas restringidas (atributos basados en dominio), solo se cargan los primeros 1000.  
  
## <a name="next-steps"></a>Pasos siguientes  
 [Publicar datos de Excel en MDS &#40;Complemento MDS para Excel&#41;](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>Consulte también  
 [Cargando datos &#40;Complemento MDS para Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Cuadro de diálogo filtrar &#40;Complemento MDS para Excel&#41;](filter-dialog-box-mds-add-in-for-excel.md)   
 [Reordenar columnas &#40;complemento MDS para Excel&#41;](reorder-columns-mds-add-in-for-excel.md)  
  
  
