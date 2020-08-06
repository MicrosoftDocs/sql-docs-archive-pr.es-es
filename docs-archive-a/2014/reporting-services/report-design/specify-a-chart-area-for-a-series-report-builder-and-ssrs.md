---
title: Especificar un área de gráfico para una serie (Generador de informes y SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10157"
- sql12.rtp.rptdesigner.chartareaproperties.alignment.f1
ms.assetid: dc3c365b-c263-402a-bf6f-c2a7081db073
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 483bc6d2fa4aa079c95e9dbd03e18c71d7b13abf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662537"
---
# <a name="specify-a-chart-area-for-a-series-report-builder-and-ssrs"></a>Especificar un área de gráfico para una serie (Generador de informes y SSRS)
  El gráfico es el contenedor de nivel superior que incluye el borde exterior, el título del gráfico y la leyenda. De forma predeterminada, el gráfico contiene un área de gráfico predeterminada. El área de gráfico no está visible en la superficie del gráfico, pero puede imaginarla como un contenedor que incluye únicamente las etiquetas del eje, el título del eje y el área de trazado de una o más series. En la ilustración siguiente se muestra el concepto de áreas de gráfico dentro de un único gráfico.  
  
 ![Muestra un diagrama de un área de gráfico](../media/chartareasdiagram.gif "Muestra un diagrama de un área de gráfico")  
  
 De forma predeterminada, todas las series se agregan al área de gráfico predeterminada. Cuando se usan gráficos de áreas, de columnas, de líneas y de dispersión, cualquier combinación de estas series se puede mostrar en la misma área de gráfico. Si tiene varias series en la misma área de gráfico, se reducirá la legibilidad del gráfico. Es recomendable separar los tipos de gráfico en varias áreas de gráfico. El uso de varias áreas de gráfico aumentará la legibilidad, facilitando las comparaciones. Por ejemplo, los gráficos de cotizaciones de volumen y precios suelen tener intervalos de valores diferentes, pero se pueden realizar comparaciones entre los datos de volumen y de precio durante el mismo período de tiempo.  
  
 Las series de tipo barras, polar o de formas solo se pueden combinar con series de los mismos tipos de gráfico en la misma área de gráfico. Si usa un gráfico polar o de formas, considere la posibilidad de usar una región de datos independiente para cada campo que desee mostrar.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-associate-a-series-with-a-new-chart-area"></a>Para asociar una serie a una nueva área de gráfico  
  
1.  Haga clic con el botón derecho en cualquier lugar del gráfico y seleccione **Agregar una nueva área de gráfico**. Aparecerá una nueva área de gráfico en blanco en el gráfico.  
  
2.  Haga clic con el botón derecho en la serie del gráfico o en un campo de serie o de datos en la zona apropiada del panel Datos del gráfico y, después, haga clic en **Propiedades de la serie**.  
  
3.  En **Ejes y área del gráfico**, seleccione el área de gráfico en la que desea mostrar la serie.  
  
4.  (Opcional) Alinee verticalmente las áreas de gráfico. Para ello, haga clic con el botón derecho en el gráfico y seleccione **Propiedades del área de gráfico**. En **Alineación**, seleccione el área de gráfico con la que desea alinear el área de gráfico seleccionada.  
  
## <a name="see-also"></a>Consulte también  
 [Mostrar varias series en un gráfico &#40;Generador de informes y SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md)   
 [Aplicar formato a los puntos de datos de un gráfico &#40;Generador de informes y SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [Definir los colores de un gráfico mediante una paleta &#40;Generador de informes y SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md)   
 [Gráficos polares &#40;Generador de informes y SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Gráficos de formas &#40;Generador de informes y SSRS&#41;](shape-charts-report-builder-and-ssrs.md)   
 [Gráficos circulares &#40;Generador de informes y SSRS&#41;](pie-charts-report-builder-and-ssrs.md)  
  
  
