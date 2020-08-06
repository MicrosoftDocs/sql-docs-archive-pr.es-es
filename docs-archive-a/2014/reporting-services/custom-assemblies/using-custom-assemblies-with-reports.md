---
title: Usar ensamblados personalizados con informes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom assemblies [Reporting Services]
- assemblies [Reporting Services], custom
- custom assemblies [Reporting Services], about custom assemblies
ms.assetid: 53d141d0-2185-466a-84dc-7b90d284da3d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f77b9da44ebb57617bd45e43d1e1e847e9074662
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745068"
---
# <a name="using-custom-assemblies-with-reports"></a>Usar ensamblados personalizados con informes
  En [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], puede escribir código personalizado para los valores de elementos de informe, estilos y formato. Por ejemplo, puede utilizar código personalizado para dar formato a las monedas según la configuración regional, marcar ciertos valores con formato especial o aplicar otras reglas de negocios en vigor en la compañía. Una manera de incluir este código en los informes es crear un ensamblado de código personalizado mediante al [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] que puede hacer referencia desde los archivos de definición de informe. El servidor llama a las funciones de los ensamblados personalizados cuando se ejecuta un informe. Los ensamblados personalizados se pueden utilizar para recuperar funciones especializadas que piensa utilizar en los informes.  
  
## <a name="in-this-section"></a>En esta sección  
 [Hacer referencia a ensamblados en un archivo RDL](referencing-assemblies-in-an-rdl-file.md)  
 Describe cómo hacer referencia a ensamblados personalizados en un archivo de lenguaje RDL (Report Definition Language).  
  
 [Implementación de un ensamblado personalizado](deploying-a-custom-assembly.md)  
 Describe cómo implementar un ensamblado personalizado en el Diseñador de informes y el servidor de informes.  
  
 [Usar ensamblados personalizados con nombre seguro](using-strong-named-custom-assemblies.md)  
 Describe cómo utilizar ensamblados personalizados con nombres seguros.  
  
 [Validar los permisos en ensamblados personalizados](asserting-permissions-in-custom-assemblies.md)  
 Describe cómo implementar los ensamblados personalizados con permisos limitados  concretos, y cómo validar esos permisos en el código.  
  
 [Acceso a los ensamblados personalizados a través de expresiones](accessing-custom-assemblies-through-expressions.md)  
 Describe cómo llamar a los métodos de ensamblado personalizados como expresiones de informe en las definiciones de informe.  
  
 [Inicializar objetos de ensamblados personalizados](initializing-custom-assembly-objects.md)  
 Describe cómo inicializar los valores para los objetos de ensamblado personalizados llamados desde un informe.  
  
 [Procedimientos: Depuración de ensamblados personalizados](how-to-debug-custom-assemblies.md)  
 Describe cómo depurar el código de ensamblado personalizado.  
  
## <a name="see-also"></a>Consulte también  
 [Lenguaje RDL (Report Definition Language) &#40;SSRS&#41;](../reports/report-definition-language-ssrs.md)  
  
  
