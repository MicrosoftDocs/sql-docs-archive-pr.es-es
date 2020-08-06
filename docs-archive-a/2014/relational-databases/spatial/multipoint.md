---
title: MultiPoint | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiPoint geometry subtype [SQL Server]
ms.assetid: 2aaab211-3aba-4dbd-90b7-095d997b1f62
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: b741071b7986aceea4e49d4fde8293ef2c96fc2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676957"
---
# <a name="multipoint"></a>MultiPoint
  Un `MultiPoint` es una colección de cero o más puntos. El límite de una instancia de `MultiPoint` está vacío.  
  
## <a name="examples"></a>Ejemplos  
 El ejemplo siguiente crea una instancia de `geometry MultiPoint` con SRID 23 y dos puntos: un punto con las coordenadas (2, 3), un punto con las coordenadas (7, 8) y un valor de Z de 9,5.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 Esta instancia de `MultiPoint` también se puede expresar usando `STMPointFromText()` como se muestra a continuación.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STMPointFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 El ejemplo siguiente usa el método `STGeometryN()` para recuperar una descripción del primer punto de la colección.  
  
```  
SELECT @g.STGeometryN(1).STAsText();  
```  
  
## <a name="see-also"></a>Consulte también  
 [Elija](point.md)   
 [Datos espaciales &#40;SQL Server&#41;](spatial-data-sql-server.md)  
  
  
