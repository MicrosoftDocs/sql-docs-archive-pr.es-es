---
title: Restringir la consulta con ejes de consulta y segmentador (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], axes
- queries [MDX], axes
- axes [MDX]
- MDX [Analysis Services], axes
ms.assetid: a64b8172-cd73-42f9-8847-52e967b9697a
author: minewiskan
ms.author: owend
ms.openlocfilehash: ed4d50aa40d2915c60f887e64cdc3ef8a6d52c5c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87747201"
---
# <a name="restricting-the-query-with-query-and-slicer-axes-mdx"></a>Restringir la consulta con ejes de consulta y segmentador (MDX)
  Cuando se formula una instrucción SELECT de Expresiones multidimensionales (MDX), una aplicación normalmente examina un cubo y divide el conjunto de jerarquías en dos subconjuntos:  
  
-   **Ejes de consulta**: conjunto de jerarquías a partir del cual se recuperan los datos de varios miembros. Para obtener más información sobre los ejes de consulta, vea [Especificar el contenido de un eje de consulta &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).  
  
-   **Eje segmentador**: conjunto de jerarquías a partir del cual se recuperan los datos para un solo miembro. Para obtener más información sobre el eje segmentador, vea [Especificar el contenido de un eje de división en sectores &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md).  
  
 Como los ejes de consulta y segmentador pueden construirse a partir de varias jerarquías del cubo que se va a consultar, estos términos se utilizan para diferenciar las jerarquías que emplea el cubo que se va a consultar de las jerarquías creadas en el cubo que devuelve una consulta de MDX.  
  
 Para ver un sencillo ejemplo del uso de los ejes de consulta y segmentador, consulte [Usar los ejes de consulta y segmentador en un ejemplo simple &#40;MDX&#41;](mdx-query-and-slicer-axes-using-axes-in-a-simple-example.md).  
  
## <a name="see-also"></a>Consulte también  
 [Trabajar con miembros, tuplas y conjuntos &#40;&#41;MDX](working-with-members-tuples-and-sets-mdx.md)   
 [Aspectos básicos de las consultas MDX &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
