---
title: Definir una relación de hechos y propiedades de la relación de hechos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- fact dimensions [Analysis Services]
ms.assetid: d8e41724-da77-4ac1-bc42-956b5d91ea5d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 15f67a4bdf699bbc6443fc76ce54bcfb35831827
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745443"
---
# <a name="define-a-fact-relationship-and-fact-relationship-properties"></a>Definir relaciones de hechos y propiedades de las relaciones de hechos
  Al definir una nueva dimensión de cubo o un nuevo grupo de medida, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] intentará detectar si existe una relación de dimensión de hechos y, a continuación, establecerá la configuración de uso de la dimensión en `Fact`. Puede ver o modificar una relación de dimensión de hechos en la pestaña **Uso de dimensiones** del Diseñador de cubos. La relación de hechos entre una dimensión y un grupo de medida presenta las siguientes restricciones:  
  
-   Una dimensión de cubo solamente puede tener una relación de hechos para un determinado grupo de medida.  
  
-   Una dimensión de cubo puede tener relaciones de hechos independientes con varios grupos de medida.  
  
-   El atributo de granularidad de la relación debe ser el atributo clave (como Transaction Number) de la dimensión. De este modo se crea una relación de uno a uno entre la dimensión y los hechos de la tabla de hechos.  
  
  
