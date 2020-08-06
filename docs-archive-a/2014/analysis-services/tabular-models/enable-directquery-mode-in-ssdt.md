---
title: Habilitar el modo de diseño de DirectQuery (SSAS tabular) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 71fc7ebd-2e86-4a76-994b-66d3a57bcc9b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8ccd2dc88f447e78f6558565a89accc341eac37c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673912"
---
# <a name="enable-directquery-design-mode-ssas-tabular"></a>Habilitar el modo de diseño de DirectQuery (SSAS tabular)
  Para crear un modelo en el modo DirectQuery, primero debe cambiar el entorno de tiempo de diseño para que admita al usuario del modo DirectQuery. Al hacerlo, el diseñador también hará lo siguiente:  
  
-   Habilitará el uso de las propiedades de implementación de DirectQuery.  
  
-   Cambiará la base de datos del área de trabajo para que se ejecute en un modo híbrido que utilice la caché para el diseño. Cuando implemente definitivamente el modelo, el modo se cambiará de nuevo al valor especificado en las propiedades de implementación del proyecto.  
  
-   Deshabilitará las características de diseño que sean incompatibles con el modo DirectQuery.  
  
-   Validará el modelo existente.  
  
 Este procedimiento describe cómo habilitar el modo DirectQuery en el diseñador.  
  
### <a name="to-enable-use-of-directquery-in-a-model"></a>Para habilitar el uso de DirectQuery en un modelo  
  
1.  Abra el archivo de la solución en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  En el Explorador de objetos, haga doble clic en el archivo Model.bim.  
  
3.  En el panel **Propiedades** , cambie la propiedad **DirectQueryMode**a **On**.  
  
4.  Si hay errores, abra la **Lista de errores** en Visual Studio y solucione los problemas que impiden que el modelo se cambie al modo DirectQuery.  
  
## <a name="see-also"></a>Consulte también  
 [Modo DirectQuery &#40;SSAS tabular&#41;](directquery-mode-ssas-tabular.md)  
  
  
