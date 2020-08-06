---
title: Configuración de la información del dispositivo de imagen | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- images [Reporting Services], rendering
- device information settings [Reporting Services], IMAGE rendering
ms.assetid: edad9498-69f7-4726-8699-fa615f704dff
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4a177b114e331a817427fbd2ce703afa21390a9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751894"
---
# <a name="image-device-information-settings"></a>Configuración de la información del dispositivo de imagen
  En la tabla siguiente se muestra la configuración de la información de los dispositivos para la representación en formato IMAGE.  
  
|Configuración|Value|  
|-------------|-----------|  
|**Columnas**|Número de columnas que se van a establecer para el informe. Este valor invalida la configuración original del informe.|  
|**ColumnSpacing**|Espacio entre las columnas que se va a establecer para el informe. Este valor invalida la configuración original del informe.|  
|`DpiX`|Resolución horizontal de la imagen de salida. El valor predeterminado es **96**. Se aplica a los `BMP` `GIF` formatos de salida,, `PNG` y `TIFF` .|  
|`DpiY`|Resolución vertical de la imagen de salida. El valor predeterminado es **96**. Se aplica a los `BMP` `GIF` formatos de salida,, `PNG` y `TIFF` .|  
|**EndPage**|Última página del informe que se va a representar. El valor predeterminado es el de `StartPage`.|  
|**MarginBottom**|Valor del margen inferior, en pulgadas, que se va a establecer para el informe. Debe incluir un valor entero o un valor decimal seguido de "in" (por ejemplo, `1in`). Este valor invalida la configuración original del informe.|  
|**MarginLeft**|El valor del margen izquierdo, en pulgadas, que se va a establecer para el informe. Debe incluir un valor entero o un valor decimal seguido de "in" (por ejemplo, `1in`). Este valor invalida la configuración original del informe.|  
|**MarginRight**|El valor del margen derecho, en pulgadas, que se va a establecer para el informe. Debe incluir un valor entero o un valor decimal seguido de "in" (por ejemplo, `1in`). Este valor invalida la configuración original del informe.|  
|**MarginTop**|El valor del margen superior, en pulgadas, que se va a establecer para el informe. Debe incluir un valor entero o un valor decimal seguido de "in" (por ejemplo, `1in`). Este valor invalida la configuración original del informe.|  
|**OutputFormat**|Uno de los formatos de salida admitidos por [!INCLUDE[ndptecgdiexpanded](../includes/ndptecgdiexpanded-md.md)] ([!INCLUDE[ndptecgdi](../includes/ndptecgdi-md.md)]): `BMP`, `EMF`, `GIF`, `JPEG`, `PNG` o `TIFF`.|  
|**PageHeight**|El alto de la página, en pulgadas, que se va a establecer para el informe. Debe incluir un valor entero o un valor decimal seguido de "in" (por ejemplo, `11in`). Este valor invalida la configuración original del informe.|  
|**PageWidth**|El ancho de la página, en pulgadas, que se va a establecer para el informe. Debe incluir un valor entero o un valor decimal seguido de "in" (por ejemplo, `8.5in`). Este valor invalida la configuración original del informe.|  
|**PrintDpiX**|Resolución horizontal de la imagen de salida. El valor predeterminado es `300`. Se aplica al formato de salida de metarchivo mejorado ( `EMF` ).|  
|**PrintDpiY**|Resolución vertical de la imagen de salida. El valor predeterminado es `300`. Se aplica al formato de salida de metarchivo mejorado ( `EMF` ).|  
|`StartPage`|Primera página del informe que se va a representar. El valor `0` indica que se representan todas las páginas. El valor predeterminado es `1`.|  
  
## <a name="see-also"></a>Consulte también  
 [Pasar la configuración de información de dispositivo a las extensiones de representación](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personalizar los parámetros de extensión de representación en RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Referencia técnica &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
