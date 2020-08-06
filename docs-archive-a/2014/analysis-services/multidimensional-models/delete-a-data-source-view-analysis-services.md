---
title: Eliminar una vista del origen de datos (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- deleting data source views
- data source views [Analysis Services], deleting
- removing data source views
ms.assetid: ae3f5ca0-ecbf-4b52-8386-eb457719d854
author: minewiskan
ms.author: owend
ms.openlocfilehash: 24b587e8d8961161ea803915c31d117c11f7cf2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87677245"
---
# <a name="delete-a-data-source-view-analysis-services"></a>Eliminar una vista del origen de datos (Analysis Services)
  Si ha dejado de usar una vista del origen de datos (DSV) en un proyecto de OLAP, puede eliminarla del proyecto en [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].  
  
 La eliminación de una DSV es permanente. No es posible restaurar una DSV eliminada en un proyecto o base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 No se pueden eliminar las DSV de las que dependen otros objetos desde una base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] abierta por [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] en el modo en línea. Para eliminar una DSV desde un proyecto que está conectado a una base de datos que se ejecuta en un servidor, primero debe eliminar todos los objetos de la base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] que dependen de esa DSV antes de eliminar la DSV.  
  
 Si elimina una DSV, invalidará otros objetos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] que dependen de ella, de modo que, antes de eliminar la DSV, verá la lista de objetos que quedarían invalidados cuando se quite la DSV. Revise esta lista con atención para asegurarse de que no contiene objetos que todavía espera usar.  
  
 ![Eliminar objetos, cuadro de diálogo](../media/ssas-olapdsv-deleteobjects.gif "Eliminar objetos, cuadro de diálogo")  
  
## <a name="see-also"></a>Consulte también  
 [Vistas del origen de datos en modelos multidimensionales](data-source-views-in-multidimensional-models.md)   
 [Cambiar las propiedades de una vista del origen de datos &#40;Analysis Services&#41;](change-properties-in-a-data-source-view-analysis-services.md)  
  
  
