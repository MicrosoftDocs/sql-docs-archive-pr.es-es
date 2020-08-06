---
title: Agregar efectos 3D a un gráfico (Generador de informes y SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ab9625d8-6557-4a4d-8123-eefa7c066ff5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f4fcd90452e32b760bc446ac5d085ed00520a2f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676368"
---
# <a name="add-3d-effects-to-a-chart-report-builder-and-ssrs"></a>Agregar efectos 3D a un gráfico (Generador de informes y SSRS)
  Se pueden usar efectos tridimensionales (3D) para dar profundidad y agregar impacto visual a un gráfico. Por ejemplo, si desea resaltar un sector específico de un gráfico circular seccionado, puede girar y cambiar la perspectiva del gráfico para que los usuarios se fijen primero en dicho sector. Cuando se aplican efectos 3D al gráfico, se deshabilitan todos los colores de degradado y los estilos de sombreado.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-apply-3d-effects-to-a-range-area-line-scatter-or-polar-chart"></a>Para aplicar efectos 3D a un gráfico de intervalos, áreas, líneas, dispersión o polar  
  
1.  Haga clic con el botón derecho en cualquier parte dentro del área del gráfico y seleccione **Efectos 3D**. Aparecerá el cuadro de diálogo **Propiedades del área de gráfico** .  
  
2.  En **Opciones 3D**, seleccione la opción **Habilitar 3D** .  
  
3.  (Opcional) En **Opciones 3D**, puede establecer diversas propiedades relacionadas con opciones de ángulos y escenas 3D. Para obtener más información sobre estas propiedades, vea [Aplicar 3D, bisel y otros efectos a un gráfico &#40;Generador de informes y SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md).  
  
4.  Haga clic en **OK**.  
  
### <a name="to-apply-3d-effects-to-a-funnel-chart"></a>Para aplicar efectos 3D a un gráfico de embudo  
  
1.  Haga clic con el botón derecho en cualquier parte dentro del área del gráfico y seleccione **Efectos 3D**. Aparecerá el cuadro de diálogo **Propiedades del área de gráfico** .  
  
2.  En **Opciones 3D**, seleccione la opción **Habilitar 3D** . Haga clic en **OK**.  
  
3.  (Opcional) Para personalizar el aspecto visual del gráfico de embudo, puede ir al panel Propiedades y cambiar propiedades específicas para ese tipo de gráfico.  
  
    1.  Abra el panel de propiedades.  
  
    2.  En la superficie de diseño, haga clic en cualquier parte del gráfico de embudo. Se muestran las propiedades de las series del gráfico de embudo en el panel de propiedades.  
  
    3.  En la sección **General** , expanda el nodo **CustomAttributes** .  
  
    4.  Para la propiedad **Funnel3DDrawingStyle** , seleccione si el embudo se mostrará como circular o cuadrado.  
  
    5.  Para la propiedad **Funnel3DRotationAngle** , establezca un valor entre -10 y 10. Esto determinará el grado de inclinación que se mostrará en el gráfico de embudo 3D.  
  
### <a name="to-apply-3d-effects-to-a-pie-chart"></a>Para aplicar efectos 3D a un gráfico circular  
  
1.  Haga clic con el botón secundario en cualquier parte dentro del área del gráfico y seleccione Efectos 3D. Aparecerá el cuadro de diálogo **Propiedades del área de gráfico** .  
  
2.  En **Opciones 3D**, seleccione la opción **Habilitar 3D** . Haga clic en **OK**.  
  
3.  (Opcional) En **Giro**, escriba un valor entero que represente el giro horizontal del gráfico circular.  
  
4.  (Opcional) En **Inclinación**, escriba un valor entero que represente el giro de inclinación vertical del gráfico circular.  
  
5.  Haga clic en **OK**.  
  
### <a name="to-apply-3d-effects-to-a-bar-or-column-chart"></a>Para aplicar efectos 3D a un gráfico de barras o de columnas  
  
1.  Haga clic con el botón derecho en cualquier parte dentro del área del gráfico y seleccione **Efectos 3D**. Aparecerá el cuadro de diálogo **Propiedades del área de gráfico** .  
  
2.  Seleccione la opción **Habilitar 3D** . Haga clic en **OK**.  
  
3.  (Opcional) Seleccione la opción **Habilitar agrupación en clústeres** . Si el gráfico contiene varias series de gráficos de barras o de columnas, esta opción mostrará las series agrupadas en clústeres. De forma predeterminada, cuando hay varias series de barras o de columnas se muestran unas al lado de otras.  
  
4.  Haga clic en **OK**.  
  
5.  (Opcional) Para agregar efectos de cilindro a un gráfico de barras o de columnas, siga estos pasos:  
  
    1.  Abra el panel de propiedades.  
  
    2.  En la superficie de diseño, haga clic en cualquiera de las barras en la serie. Las propiedades de la serie se muestran en el panel de propiedades.  
  
    3.  En la sección **General** , expanda el nodo **CustomAttributes** .  
  
    4.  Para la propiedad **DrawingStyle** , especifique el valor **Cylinder** .  
  
## <a name="see-also"></a>Consulte también  
 [Aplicar 3D, bisel y otros efectos a un gráfico &#40;Generador de informes y SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md)   
 [Aplicar formato a un gráfico &#40;Generador de informes y SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [Gráficos &#40;Generador de informes y SSRS&#41;](charts-report-builder-and-ssrs.md)  
  
  
