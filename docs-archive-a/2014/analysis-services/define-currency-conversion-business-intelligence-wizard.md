---
title: Definir la conversión de moneda (Asistente de Business Intelligence) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.existingscriptpage.f1
ms.assetid: 37dd65b7-9d8d-44ad-b316-96a92c622472
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1c60b6ad6964060164e273004f59604fef6574a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662336"
---
# <a name="define-currency-conversion-business-intelligence-wizard"></a>Definir la conversión de moneda (Asistente de Business Intelligence)
  Use la página **Definir la conversión de moneda** para revisar el script MDX (Expresiones multidimensionales) que contiene la funcionalidad de conversión de moneda generada por el Asistente de Business Intelligence. A continuación, puede utilizar el script MDX generado por este asistente para sobrescribir o agregar la funcionalidad de conversión de moneda definida previamente en el script MDX del cubo.  
  
> [!NOTE]  
>  Esta página solo aparecerá si el Asistente de Business Intelligence detecta como mínimo una conversión de moneda definida previamente en el script MDX del cubo. En el script MDX del cubo, las conversiones de moneda se encuadran con los siguientes comentarios:  
>   
>  `//<Currency conversion>`  
>   
>  `...`  
>   
>  `[MDX statements for the currency conversion]`  
>   
>  `...`  
>   
>  `//</Currency conversion>`  
>   
>  Si cambia o quita estos comentarios, el Asistente de Business Intelligence quizás no pueda detectar una conversión de moneda definida previamente.  
  
## <a name="options"></a>Opciones  
 **Nuevo script de conversión de moneda**  
 Muestra el script MDX generado por la sesión actual del Asistente de Business Intelligence.  
  
 **Sobrescribir el script de conversión de moneda existente**  
 Seleccione esta opción para sobrescribir el script MDX mostrado en **Script de conversión de moneda existente** con el script MDX mostrado en **Nuevo script de conversión de moneda**.  
  
 **Anexar después de**  
 Seleccione esta opción para anexar el script MDX mostrado en **Nuevo script de conversión de moneda** al final del script MDX mostrado en **Script de conversión de moneda existente**. El script anexado aparece como una sección nueva.  
  
 **Script de conversión de moneda existente**  
 Seleccione la sección del script MDX existente que contiene la funcionalidad de conversión de moneda definida previamente que se sobrescribirá o anexará.  
  
## <a name="see-also"></a>Consulte también  
 [Asistente de Business Intelligence (ayuda F1)](business-intelligence-wizard-f1-help.md)   
 [Diseñador de cubos &#40;Analysis Services de datos multidimensionales&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Diseñador de dimensiones &#40;Analysis Services de datos multidimensionales&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
