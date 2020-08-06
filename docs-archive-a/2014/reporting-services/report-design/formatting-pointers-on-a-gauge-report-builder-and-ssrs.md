---
title: Aplicar formato a los punteros de un medidor (Generador de informes y SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2fdf670a-5237-48fe-813d-97657c5c77d2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c74cb4d4c61c18d25069dab062bf09804f5935b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743965"
---
# <a name="formatting-pointers-on-a-gauge-report-builder-and-ssrs"></a>Aplicar formato a los punteros de un medidor (Generador de informes y SSRS)
  El puntero de un medidor indica el valor actual del medidor. De forma predeterminada, cuando se agrega un campo, los valores contenidos en él se agregan a un valor mostrado por el puntero en el medidor. Puede agregar varios punteros al medidor para que apunten a varios valores en la misma escala o agregar varias escalas y un puntero para cada una. Después de agregar un campo a un medidor, debe establecer los valores máximo y mínimo en la escala correspondiente para dar contexto al valor del puntero. También tiene la opción de establecer los valores mínimo y máximo en un intervalo, que muestra un área crítica en la escala.  
  
 Puede establecer las propiedades de aspecto en el puntero haciendo clic con el botón derecho en el puntero y seleccionando **Propiedades del puntero radial** o **Propiedades del puntero lineal**. Cada puntero del medidor contiene el mismo conjunto de propiedades. Hay también propiedades de aspecto correspondientes exclusivas de cada tipo de medidor:  
  
-   En un medidor radial, puede especificar un puntero de aguja y un extremo de aguja.  
  
-   En un medidor lineal, puede especificar un puntero de termómetro, que es una variación del puntero de barra. El puntero de termómetro le permite especificar la forma de la cubeta.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="how-the-pointer-is-connected-to-data"></a><a name="HowPointer"></a> Cómo se conecta el puntero a los datos  
 De forma predeterminada, cuando se agrega un medidor, este contiene un puntero sin ningún campo asociado. Esto se conoce como puntero vacío. Este puntero indicará cero hasta que se agregue un campo al panel de datos. Al agregar un campo al panel de datos, el puntero se conecta a ese campo. Si se elimina un campo desde el panel de datos, también se elimina el puntero asociado a dicho campo.  
  
 Una vez agregados los datos, al hacer clic con el botón derecho en el puntero, obtendrá las opciones **Borrar valor de puntero** y **Eliminar puntero** . La opción **Borrar valor de puntero** quitará el campo adjuntado al medidor, pero el puntero seguirá apareciendo en el medidor. La opción **Eliminar puntero** quitará el campo del medidor y hará que el puntero deje de verse. Si vuelve a agregar un campo al medidor, reaparecerá el puntero predeterminado. Cuando se establece la propiedad **Hidden** del puntero en `True` , el puntero no se oculta en la superficie de diseño, sino que se oculta en tiempo de ejecución.  
  
  
##  <a name="displaying-multiple-pointers-on-the-gauge"></a><a name="DisplayingMultiple"></a> Mostrar varios punteros en el medidor  
 Puede agregar varios punteros al medidor para que apunten a varios valores en la misma escala. Esto puede ser útil para mostrar un valor alto y un valor bajo al mismo tiempo. Para especificar más de un puntero en el medidor para la misma escala, haga clic con el botón derecho en cualquier lugar dentro del medidor y haga clic en **Agregar puntero** en el menú contextual. O bien, puede agregar una escala haciendo clic con el botón derecho en cualquier lugar del medidor y, después, haciendo clic en **Agregar escala**. A continuación, podrá agregar un nuevo puntero que se asociará automáticamente a la última escala.  
  
 Cuando se superponen los punteros, el orden en el que se dibujan está determinado por el orden en el que se agregan al medidor. No es posible reorganizar el orden en el que se dibujan los punteros cambiando el orden de los campos en el panel de datos. Para cambiar el orden de dibujo de varios punteros, abra el panel Propiedades y haga clic en **Punteros (...)** . A continuación, cambie el orden de los punteros en la colección Puntero.  
  
  
##  <a name="setting-gradients-on-a-needle-cap"></a><a name="SettingGradients"></a> Establecer degradados en un extremo de aguja  
 Puede especificar un extremo de aguja que se puede dibujar encima o debajo del puntero únicamente en un medidor radial. Todos los estilos de extremos de aguja se dibujan utilizando degradados integrados que no se pueden modificar. La excepción es el estilo `RoundedDark`, donde puede especificar un color y un estilo de degradado.  
  
  
##  <a name="setting-a-snapping-interval"></a><a name="SettingSnappingInterval"></a> Establecer un intervalo de ajuste  
 Un intervalo de ajuste define el múltiplo al que se redondean los valores. De forma predeterminada, el medidor señala el valor exacto del campo que se ha especificado en el panel de datos. Sin embargo, puede ser que le interese redondear el valor exacto al alza o a la baja para que el puntero se ajuste a un intervalo preestablecido. Por ejemplo, si el valor del medidor es de 34,2 y especifica un intervalo de ajuste de 5, el puntero del medidor señalará 3,5. Si el valor del medidor es de 31,2 y especifica un intervalo de ajuste de 5, el puntero del medidor señalará 30. Para obtener más información, vea [establecer un intervalo de ajuste en un medidor &#40;generador de informes y SSRS&#41;](../set-a-snapping-interval-on-a-gauge-report-builder-and-ssrs.md).  
  
  
##  <a name="specifying-an-image-as-a-pointer-on-a-radial-gauge"></a><a name="SpecifyingImage"></a> Especificar una imagen como puntero en un medidor radial  
 Además de la lista integrada de estilos de puntero, puede especificar una imagen como puntero. Esto es muy eficaz cuando se usa una imagen para reemplazar un estilo de puntero de aguja existente. La imagen se superpone en el puntero, pero toda la funcionalidad de éste sigue intacta. Las opciones de color y degradado no son aplicables cuando se usa una imagen para el puntero.  
  
 Si la imagen del puntero tiene forma irregular, debe definir el color como transparente para ocultar las áreas de la imagen que no deben aparecer en el medidor. Al definir un color transparente, el medidor transpone la imagen encima del puntero existente y la recorta para que solo aparezca la forma del puntero. El medidor cambia la escala de la imagen para que se ajuste al tamaño del puntero. Al especificar una imagen para un puntero, cualquier puntero que se agregue posteriormente encima del medidor se dibujará debajo la imagen. Por este motivo, se recomienda no especificar una imagen para el puntero si hay varios punteros en el medidor. Para obtener más información, vea [especificar una imagen como puntero en un medidor &#40;generador de informes y SSRS&#41;](../specify-an-image-as-a-pointer-on-a-gauge-report-builder-and-ssrs.md).  
  
  
## <a name="see-also"></a>Consulte también  
 [Aplicar formato a las escalas de un medidor &#40;Generador de informes y SSRS&#41;](formatting-scales-on-a-gauge-report-builder-and-ssrs.md)   
 [Aplicar formato a los rangos de un medidor &#40;Generador de informes y SSRS&#41;](formatting-ranges-on-a-gauge-report-builder-and-ssrs.md)   
 [Medidores &#40;Generador de informes y SSRS&#41;](gauges-report-builder-and-ssrs.md)  
  
  
