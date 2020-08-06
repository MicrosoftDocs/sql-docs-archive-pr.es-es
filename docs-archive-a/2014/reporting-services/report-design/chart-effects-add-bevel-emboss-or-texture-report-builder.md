---
title: Agregar estilos con bisel, relieve y textura a un gráfico (Generador de informes y SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 737cfc80-b39e-497c-817b-b46693deb58f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 92c5d4af47b7889b9ba5ec421706848f8822075b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676365"
---
# <a name="add-bevel-emboss-and-texture-styles-to-a-chart-report-builder-and-ssrs"></a>Agregar estilos con bisel, relieve y textura a un gráfico (Generador de informes y SSRS)
  Cuando use determinados tipos de gráficos, puede especificar efectos de dibujo que aumenten el impacto visual del gráfico. Estos efectos de dibujo solamente se aplican a las series del gráfico. No afectan a ningún otro elemento del gráfico.  
  
 Cuando use cualquier variante de un gráfico circular o de anillos, puede especificar un estilo de dibujo de borde suave o cóncavo, similar a los efectos de bisel o de relieve que se pueden aplicar a una imagen.  
  
 Cuando use cualquier variante de un gráfico de barras o de columnas, puede aplicar estilos de textura, como cilindros, cuñas y degradados a barras o columnas individuales.  
  
 Además de estos estilos de dibujo, puede agregar bordes y sombras a muchos elementos del gráfico para crear una sensación de profundidad. Para más información sobre otras maneras de dar formato al gráfico, vea [Aplicar formato a un gráfico &#40;Generador de informes y SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-bevel-or-emboss-styles-to-a-pie-or-doughnut-chart"></a>Para agregar estilos de bisel y de relieve a un gráfico circular o de anillos  
  
1.  En la pestaña **Vista** , seleccione **Propiedades** para abrir el panel Propiedades.  
  
2.  Seleccione el gráfico circular o de anillos que desea mejorar. Seleccione un campo de datos en el gráfico, no en el gráfico entero.  
  
3.  En el panel de propiedades, expanda el nodo **CustomAttributes** .  
  
4.  Para PieDrawingStyle, seleccione un estilo en la lista desplegable.  
  
> [!NOTE]  
>  No puede tener estilos de relieve o bisel, y 3D en el mismo gráfico. Si ha habilitado 3D para el gráfico, no verá la propiedad PieDrawingStyle.  
  
 ![Gráfico circular con estilo de dibujo cóncavo](../media/rs-piedrawingeffects-concave.gif "Gráfico circular con estilo de dibujo cóncavo")  
  
### <a name="to-add-texture-styles-to-a-bar-or-column-chart"></a>Para agregar estilos de textura a un gráfico de barras o de columnas  
  
1.  Seleccione el gráfico de barras o de columnas que desea mejorar. Seleccione un campo de datos en el gráfico, no en el gráfico entero.  
  
2.  Abra el panel de propiedades.  
  
3.  Expanda el nodo **CustomAttributes** .  
  
4.  Para DrawingStyle, seleccione un estilo en la lista desplegable.  
  
> [!NOTE]  
>  No puede tener estilos de relieve o bisel, y 3D en el mismo gráfico. Si ha habilitado 3D para el gráfico, no verá la propiedad PieDrawingStyle.  
  
 ![Gráfico de barras con efecto de dibujo LightToDark](../media/rs-bardrawingeffects-lighttodark.gif "Gráfico de barras con efecto de dibujo LightToDark")  
  
## <a name="see-also"></a>Consulte también  
 [Gráficos de barras &#40;Generador de informes y SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Gráficos de columnas &#40;Generador de informes y SSRS&#41;](column-charts-report-builder-and-ssrs.md)   
 [Gráficos circulares &#40;Generador de informes y SSRS&#41;](pie-charts-report-builder-and-ssrs.md)   
 [Aplicar formato a un gráfico &#40;Generador de informes y SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)  
  
  
