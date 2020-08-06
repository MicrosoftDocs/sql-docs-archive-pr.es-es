---
title: Aplicar formato de fecha o de moneda a las etiquetas de los ejes (Generador de informes y SSRS)| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e9a01a74-2f51-4b35-be3a-a6138568f6cf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ffe9d903a2271db95d4b1c2ef6201d2b0f3edab3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87671381"
---
# <a name="format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs"></a>Aplicar formato de fecha o de moneda a las etiquetas de los ejes (Generador de informes y SSRS)
  Cuando se muestren valores DateTime con el formato correcto en un eje, un gráfico mostrará automáticamente dichos valores como días. Para especificar un intervalo de fechas u horas para el eje X, como un intervalo de meses o de horas, debe dar formato a las etiquetas del eje y establecer el tipo de intervalo de éste en un intervalo de fechas u horas válido.  
  
> [!NOTE]  
>  En gráficos de columnas y de dispersión, el eje horizontal, o eje X, es el eje de categorías. En los gráficos de barras, el vertical, o eje Y, es el eje de categoría.  
  
 Para dar el formato correcto a los intervalos de tiempo, los valores mostrados en el eje X se deben evaluar como un tipo de datos <xref:System.DateTime> . Si el campo tiene un tipo de datos <xref:System.String>, el gráfico no calculará los intervalos como fechas u horas. Para más información, vea [Gráficos &#40;Generador de informes y SSRS&#41;](charts-report-builder-and-ssrs.md).  
  
 Cuando se agrega un valor numérico al eje Y, de forma predeterminada, el gráfico no da formato al número antes de mostrarlo. Si el campo numérico es una cifra de ventas, considere la posibilidad de dar formato de moneda a los números para aumentar la legibilidad del gráfico.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-format-x-axis-labels-as-monthly-intervals"></a>Para dar formato de intervalo mensual a las etiquetas del eje X  
  
1.  Haga clic con el botón derecho en el eje horizontal, o X, del gráfico y, después, seleccione **Propiedades del eje horizontal**.  
  
2.  En el cuadro de diálogo **Propiedades del eje horizontal** , seleccione **Número**.  
  
3.  En la lista **Categoría** , seleccione **Fecha**. En la lista **Tipo** , seleccione un formato de fecha para aplicarlo a las etiquetas del eje X.  
  
4.  Seleccione **Opciones del eje**.  
  
5.  En **Intervalo**, escriba **1**. En la propiedad **Tipo de intervalo** , seleccione **Meses**.  
  
    > [!NOTE]  
    >  Si no especifica un tipo de intervalo, el gráfico calculará los intervalos en días.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-format-y-axis-labels-using-a-currency-format"></a>Para dar formato de moneda a las etiquetas del eje Y  
  
1.  Haga clic con el botón derecho en el eje vertical, o Y, del gráfico y, después, haga clic en **Propiedades del eje vertical**.  
  
2.  En el cuadro de diálogo **Propiedades del eje vertical** , seleccione **Número**.  
  
3.  En la lista **Categoría** , seleccione **Moneda**. En la lista **Símbolo** , seleccione un formato de moneda para aplicarlo a las etiquetas del eje Y.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Consulte también  
 [Aplicar formato a las etiquetas de los ejes de un gráfico &#40;Generador de informes y SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Aplicar formato a un gráfico &#40;Generador de informes y SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [Especificar una escala logarítmica &#40;Generador de informes y SSRS&#41;](specify-a-logarithmic-scale-report-builder-and-ssrs.md)   
 [Especificar un intervalo de eje &#40;Generador de informes y SSRS&#41;](specify-an-axis-interval-report-builder-and-ssrs.md)  
  
  
