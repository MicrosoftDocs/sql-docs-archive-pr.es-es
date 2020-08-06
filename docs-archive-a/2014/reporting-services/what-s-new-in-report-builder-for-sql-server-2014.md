---
title: Novedades de&#39;s en Generador de informes para SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8223c19b-4b0d-4b1d-a042-9a726c18e708
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0ce72af225130bc3f081a53008a303c5213db636
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674003"
---
# <a name="what39s-new-in-report-builder-for-sql-server-2014"></a>&#39;novedades de Generador de informes para SQL Server 2014
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] presenta diversas características de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
 Para obtener información acerca de las características de esta versión para otros [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] productos y tecnologías, consulte [novedades de SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).  
  
> [!TIP]  
>  Para obtener la información y los recursos más recientes con respecto a las nuevas características de esta versión, vea [Información adicional sobre las novedades de SQL Server Reporting Services (SSRS)](https://go.microsoft.com/fwlink/?LinkId=207147).  
  
##  <a name="excel-renderer-for-microsoft-excel-2007-2010-and-microsoft-excel-2003"></a><a name="ExcelRenderer"></a>Representador de Excel para Microsoft Excel 2007-2010 y Microsoft Excel 2003  
 La extensión de representación de Excel de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , nueva en [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], procesa un informe como un documento de Excel compatible con [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2007-2010, así como con [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2003, gracias al Paquete de compatibilidad de Microsoft Office para formatos de archivos de Word, Excel y PowerPoint instalado. El formato es Office Open XML y la extensión de los archivos es .xlsx.  
  
 Esta extensión de representación de Excel elimina las limitaciones de la versión anterior, compatible con Excel 2003. A continuación se indican las mejoras de la extensión de representación:  
  
-   Número máximo de filas por hoja de cálculo: 1.048.576.  
  
-   Número máximo de columnas por hoja de cálculo: 16.384.  
  
-   Número de colores permitido en una hoja de cálculo: aproximadamente 16 millones (color de 24 bits).  
  
-   La compresión ZIP proporciona archivos menores.  
  
 Para obtener más información, vea [Exportar a Microsoft Excel &#40;Generador de informes y SSRS&#41;](report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md).  
  
##  <a name="word-renderer-for-microsoft-word-2007-2010-and-microsoft-word-2003"></a><a name="WordRenderer"></a>Representador de Word para Microsoft Word 2007-2010 y Microsoft Word 2003  
 La extensión de representación de Word de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , nueva en [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], procesa un informe como un documento de Word compatible con [!INCLUDE[ofprword](../includes/ofprword-md.md)] 2007-2010, así como con [!INCLUDE[ofprword](../includes/ofprword-md.md)] 2003, gracias al Paquete de compatibilidad de [!INCLUDE[msCoName](../includes/msconame-md.md)] Office para formatos de archivos de Word, Excel y PowerPoint instalado. El formato es Office Open XML y la extensión de los archivos es .docx.  
  
 Además de hacer que las características nuevas de Word 2007-2010 estén disponibles en los informes exportados, los archivos *.docx de los informes exportados suelen ser menores. Los informes exportados mediante el representador de Word suelen ser mucho menores que los mismos informes exportados mediante el representador de Word 2003.  
  
 Para obtener más información, vea [Exportar a Microsoft Word &#40;Generador de informes y SSRS&#41;](report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Consulte también  
 [Generador de informes en SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
