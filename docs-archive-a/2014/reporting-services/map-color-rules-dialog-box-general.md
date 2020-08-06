---
title: Cuadro de diálogo reglas de color de mapa, general | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10541"
- sql12.rtp.rptdesigner.shared.mapcolorrulesgeneral.f1
ms.assetid: 14ff5fc1-4cf8-4a45-9d98-47a1bf1c52c4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0dffc6c0b31400cb4eb9cecbbada1a52f8f41443
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676862"
---
# <a name="map-color-rules-dialog-box-general"></a>Cuadro de diálogo de Reglas de color de mapa, General
  Seleccione **General** en el cuadro de diálogo **Propiedades de reglas de color** para definir las opciones de color de los elementos de mapa en esta capa. Entre los elementos de mapa se incluyen los polígonos, líneas y puntos. Las reglas de color se pueden aplicar cuando se haya creado una relación entre los elementos de mapa basada en los datos espaciales y los datos analíticos desde un campo de conjunto de datos o desde un campo de origen de datos espaciales.  
  
 Para mostrar todos los elementos de mapa en una capa especificando un degradado decorativo con colores primarios y secundarios diferentes, utilice la página **Relleno** del cuadro de diálogo Propiedades de polígono de mapa. Las reglas de color tienen prioridad sobre las propiedades de presentación de una capa. Para más información, vea [Personalizar los datos y la presentación de un mapa o una capa de mapa &#40;Generador de informes y SSRS&#41;](report-design/customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md).  
  
## <a name="options"></a>Opciones  
 **Aplicar estilo de plantilla**  
 Seleccione esta opción para utilizar un color basado en el tema que se eligió en el asistente o establecido en las propiedades de capa de polígono, línea o punto. Un tema establece las opciones predeterminadas del color, fuente y bordes del mapa. Para esta opción, no se aplica ninguna regla para asignar los colores a cada elemento de mapa.  
  
 **Visualizar datos mediante el uso de la paleta de colores**  
 Seleccione esta opción para visualizar los datos analíticos utilizando los colores de una paleta de colores concreta.  
  
 **Visualizar datos mediante el uso de rangos de colores**  
 Seleccione esta opción para visualizar los datos analíticos utilizando una gama de colores para cada elemento de mapa. Por ejemplo, al especificar rojo como color inicial, amarillo como color medio y verde como color final, los valores del rango inferior son rojos, los valores del rango intermedio son amarillos y los valores en el rango superior son verdes.  
  
 **Visualizar datos mediante el uso de colores personalizados**  
 Seleccione esta opción para visualizar los datos analíticos especificando su propia lista de colores.  
  
 **Campo de datos**  
 Esta opción aparece al seleccionar una de las opciones de **Visualizar datos** .  
  
 Seleccione el campo de datos analíticos que se usará en la lista desplegable. Según el origen de datos espaciales, la lista muestra los campos del origen de datos espaciales y de un conjunto de datos de informe que tiene una relación entre los datos espaciales y los datos analíticos. Para crear este tipo de relación, establezca las opciones de datos en la página Datos analíticos de la capa de mapa seleccionada.  
  
 **Índ**  
 Escriba o seleccione el nombre de la paleta de colores.  
  
 **Color inicial**  
 Especifique el color que se usará para los datos en el extremo final del rango de datos.  
  
 **Color intermedio**  
 Especifique el color que se utilizará para los datos en el intermedio del rango de datos. Seleccione **Ningún color** para quitar este rango.  
  
 **Color final**  
 Especifique el color que se usará para los datos en el extremo más alto del rango de datos.  
  
 **Add**  
 Haga clic en **Agregar** para especificar sus propios colores para la regla de color.  
  
## <a name="see-also"></a>Consulte también  
 [Mapas &#40;Generador de informes y SSRS&#41;](report-design/maps-report-builder-and-ssrs.md)   
 [Cambiar leyendas de mapa, escala de colores y reglas asociadas &#40;Generador de informes y SSRS&#41;](report-design/change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs.md)  
  
  
