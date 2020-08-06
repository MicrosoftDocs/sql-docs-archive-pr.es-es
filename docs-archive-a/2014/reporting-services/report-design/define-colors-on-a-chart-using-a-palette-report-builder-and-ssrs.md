---
title: Definir los colores de un gráfico mediante una paleta (Generador de informes y SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d95efc22-5a32-43d4-9bd2-12753e7fd395
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7db137ed87b0c84e43577dcf2936a6287abd8e36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672737"
---
# <a name="define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs"></a>Definir los colores de un gráfico mediante una paleta (Generador de informes y SSRS)
  Para cambiar la paleta de colores de un gráfico, puede seleccionar una paleta predefinida o definir una paleta personalizada. Las paletas personalizadas son específicas de cada informe.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-colors-on-the-chart-using-a-built-in-color-palette"></a>Para cambiar los colores del gráfico mediante una paleta de colores integrada  
  
1.  Abra el panel de propiedades.  
  
2.  En la superficie de diseño, haga clic en el gráfico. Las propiedades del objeto de gráfico se muestran en el panel de propiedades.  
  
     El nombre del objeto (de forma predeterminada,**Chart1** ) aparece en la lista desplegable de la parte superior del panel de propiedades.  
  
3.  En la sección **Gráfico** , para la propiedad Palette, seleccione una nueva paleta en la lista desplegable.  
  
    > [!NOTE]  
    >  No puede cambiar los colores ni su orden en una paleta predefinida.  
  
### <a name="to-define-your-own-colors-on-the-chart-using-a-custom-color-palette"></a>Para definir sus propios colores para el gráfico utilizando una paleta de colores personalizada  
  
1.  Abra el panel de propiedades.  
  
2.  En la superficie de diseño, haga clic en el gráfico. Las propiedades del objeto de gráfico se muestran en el panel de propiedades.  
  
3.  En la sección **gráfico** , para la `Palette` propiedad, seleccione **personalizado**.  
  
4.  En la propiedad CustomPaletteColors, haga clic en el botón Editar colección ( **...** ). Se abre el **Editor de la colección ReportColorExpression** .  
  
5.  Haga clic **Agregar** para agregar un color. Seleccione un color de la lista desplegable o seleccione Expresión y especifique un valor hexadecimal para un color específico, como ff6600 para "Anaranjado".  
  
     Para obtener más información sobre los valores hexadecimales, vea [Color Table](https://go.microsoft.com/fwlink/?linkid=9258) en MSDN.  
  
6.  Haga clic **Agregar** para agregar más colores a la paleta.  
  
7.  Cuando termine, haga clic en **Aceptar**.  
  
 Si está utilizando una paleta personalizada, puede cambiar el orden de los colores para cambiar el color de las distintas series del gráfico.  
  
## <a name="see-also"></a>Consulte también  
 [Aplicar formato a los colores de serie de un gráfico &#40;Generador de informes y SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [Gráficos &#40;Generador de informes y SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Especificar colores coherentes en varios gráficos de formas &#40;Generador de informes y SSRS&#41;](shape-charts-report-builder-and-ssrs.md)  
  
  
