---
title: Generar medidas en MDX | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f0347835-4983-4d26-acbb-6c8fae7992bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: ac49d37f11584bfbc5d372241056da39e7dd8c93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87671735"
---
# <a name="building-measures-in-mdx"></a>Generar medidas en MDX
  En las expresiones multidimensionales (MDX), una medida es una expresión DAX con nombre que se resuelve calculando la expresión para devolver un valor en un modelo tabular. Esta definición tan genérica tiene un alcance notable. La capacidad de construir y utilizar medias en una consulta MDX proporciona una gran solución para manipular datos tabulares.  
  
> [!WARNING]  
>  Las medidas solo pueden definirse en modelos tabulares; si la base de datos se establece en modo multidimensional, al crear una medida se generará un error.  
  
 Para crear una medida definida como parte de una consulta MDX, y en consecuencia con un ámbito limitado a la consulta, debe usar la palabra clave WITH. Puede usar la medida en una instrucción MDX SELECT. De esta manera, el miembro calculado creado con la palabra clave WITH se puede cambiar sin tener que tocar la instrucción SELECT. Sin embargo, en MDX se hace referencia a la medida de forma diferente que en las expresiones DAX; para hacer referencia a la medida que se denomina como miembro de la dimensión [Measures], vea el siguiente ejemplo MDX:  
  
```  
with measure  'Sales Territory'[Total Sales Amount] = SUM('Internet Sales'[Sales Amount]) + SUM('Reseller Sales'[Sales Amount])  
select measures.[Total Sales Amount] on columns  
     ,NON EMPTY [Date].[Calendar Year].children on rows  
from [Model]  
  
```  
  
 Devolverá los siguientes datos cuando se ejecute:  
  
||Total Sales Amount||  
|-|------------------------|-|  
|2001|11331808.96||  
|2002|30674773.18||  
|2003|41993729.72||  
|2004|25808962.34||  
  
## <a name="see-also"></a>Consulte también  
 [Instrucción CREATE MEMBER &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member)   
 [Referencia de funciones MDX &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)   
 [SELECT &#40;Instrucción, MDX&#41;](/sql/mdx/mdx-data-manipulation-select)  
  
  
