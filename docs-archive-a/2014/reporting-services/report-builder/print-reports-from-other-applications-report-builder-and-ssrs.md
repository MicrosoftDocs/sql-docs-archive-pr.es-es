---
title: Imprimir informes desde otras aplicaciones (Generador de informes y SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a5560581-fd57-4a45-b7ea-43b21a8a7419
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 58fee2cf31601dc638eebd69a13727a805408ac0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746787"
---
# <a name="print-reports-from-other-applications-report-builder-and-ssrs"></a>Imprimir informes desde otras aplicaciones (Generador de informes y SSRS)
  El Generador de informes incluye una opción de exportación que le permite ver fácilmente un informe en otras aplicaciones. El comando `Export` está disponible en la barra de herramientas de informe que aparece en la parte superior de un informe cuando abre dicho informe en un explorador o una aplicación basada en web. Si exporta un informe, este se muestra en una aplicación diferente (por ejemplo, si se exporta un informe a Excel, se abre en [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]). Para la impresión, solo se recomienda exportar un informe si la aplicación dispone de unas características de impresión concretas que desea utilizar.  
  
 Para exportar un informe a otra aplicación, debe tener instalada esa aplicación. Por ejemplo, es imprescindible tener Adobe Acrobat Reader instalado en el equipo para realizar exportaciones al formato Acrobat (PDF). Si decide exportar un informe al formato TIFF, el servidor de informes colocará el informe en una aplicación de visualización asociada al tipo de archivo TIFF. Aunque la aplicación elegida depende de la versión de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows instalada, suele tratarse de la aplicación Visor de imágenes y fax de Windows. La resolución predeterminada corresponde a una resolución de pantalla de 96 puntos por pulgada (ppp). Puede aumentar la resolución a 300 o 600 ppp en la aplicación Visor de imágenes y fax de Windows para adaptarla a las características de su impresora. Para obtener más información sobre cómo ajustar la resolución, consulte la documentación del producto de Windows.  
  
 Si elige el formato de archivo web (también denominado MHTML), el informe se exporta al explorador predeterminado. Si imprime desde el explorador, es posible que la información de la ruta de acceso al informe se agregue en la parte inferior de cada página. En la mayoría de los casos existe la posibilidad de establecer opciones del explorador para que se omita la información de la ruta de acceso en las páginas impresas. Para obtener más información, consulte la información del producto del explorador que está utilizando.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a>Consulte también  
 [Imprimir un informe &#40;Generador de informes y SSRS&#41;](print-a-report-report-builder-and-ssrs.md)   
 [Imprimir informes desde un explorador con el control de impresión &#40;Generador de informes y SSRS&#41;](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md)   
 [Exportar informes &#40;Generador de informes y SSRS&#41;](export-reports-report-builder-and-ssrs.md)   
 [Exportar un informe como otro tipo de archivo &#40;Generador de informes y SSRS&#41;](../export-a-report-as-another-file-type-report-builder-and-ssrs.md)   
 [Buscar, ver y administrar informes &#40;Generador de informes y SSRS&#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
