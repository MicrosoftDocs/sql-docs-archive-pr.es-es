---
title: Definir un nuevo atributo automáticamente | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- automatic attribute creation
- attributes [Analysis Services], creating
ms.assetid: 208a050a-5e2f-470c-b645-8d835e123db7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 40f9ae1f00dd0a6520c6d1b06111864fba02e8f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750346"
---
# <a name="define-a-new-attribute-automatically"></a>Definir un nuevo atributo automáticamente
  Puede crear un atributo nuevo en una dimensión con la edición de tipo arrastrar y colocar del Diseñador de dimensiones.  
  
### <a name="to-create-a-new-attribute-automatically"></a>Para crear un nuevo atributo automáticamente  
  
1.  En el Diseñador de dimensiones, abra la dimensión en la que desea crear el atributo.  
  
2.  En la pestaña **Estructura de dimensión** , en el panel **Vista del origen de datos** , seleccione la columna dentro de la tabla a la que desee enlazar el atributo y arrástrela al panel **Atributos** .  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] crea el nuevo atributo con el mismo nombre que la columna con la que está enlazado. Si hay varios atributos que utilizan la misma columna, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] anexará un número al nombre de atributo.  
  
## <a name="see-also"></a>Consulte también  
 [Dimensiones en modelos multidimensionales](dimensions-in-multidimensional-models.md)   
 [Referencia de las propiedades de los atributos de dimensión](dimension-attribute-properties-reference.md)  
  
  
