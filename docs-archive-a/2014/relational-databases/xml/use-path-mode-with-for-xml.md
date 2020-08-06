---
title: Usar el modo PATH con FOR XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode
- characters [SQL Server], XML
- aliases [SQL Server], XML
- FOR XML clause, PATH mode
- FOR XML PATH mode
- column names [SQL Server]
- XPath queries [SQL Server]
ms.assetid: a685a9ad-3d28-4596-aa72-119202df3976
author: rothja
ms.author: jroth
ms.openlocfilehash: ce0cf811f1e610d14a94993b54c51ea079f613e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673553"
---
# <a name="use-path-mode-with-for-xml"></a>Usar el modo PATH con FOR XML
  Tal como se describe en [Generar XML mediante FOR XML](for-xml-sql-server.md), el modo PATH facilita la combinación de elementos y atributos. También facilita la especificación de anidación adicional para representar propiedades complejas. Puede utilizar consultas de modo FOR XML EXPLICIT para generar XML a partir de un conjunto de filas, pero el modo PATH supone una alternativa más sencilla a las consultas de modo EXPLICIT potencialmente complicadas. El modo PATH, junto con la posibilidad de escribir consultas FOR XML anidadas y la directiva TYPE para devolver instancias de tipo **xml** , permite escribir consultas de forma más fácil.  
  
 En el modo PATH, los nombres o alias de columna se tratan como expresiones XPath. Estas expresiones indican el modo en el que se asignan los valores a XML. Cada expresión XPath es una expresión relativa que proporciona el tipo de elemento, como el atributo, el elemento y el valor escalar, así como el nombre y la jerarquía del nodo que se generará en relación con el elemento de fila.  
  
 Esta sección describe las columnas de asignación en un conjunto de filas bajo varias condiciones y proporciona los ejemplos.  
  
## <a name="in-this-section"></a>En esta sección  
  
-   [Columnas sin nombre](columns-without-a-name.md)  
  
-   [Columnas con nombre](columns-with-a-name.md)  
  
-   [Columnas con un nombre especificado como carácter comodín](columns-with-a-name-specified-as-a-wildcard-character.md)  
  
-   [Columnas con el nombre de una prueba de nodo XPath](columns-with-the-name-of-an-xpath-node-test.md)  
  
-   [Nombres de columna con la ruta de acceso especificada como data&#40;&#41;](column-names-with-the-path-specified-as-data.md)  
  
-   [Columnas que incluyen un valor NULL de forma predeterminada](columns-that-contain-a-null-value-by-default.md)  
  
-   [Compatibilidad con elementos de espacio de nombres en el modo PATH](namespace-support-in-path-mode.md)  
  
-   [Ejemplos: Uso del modo PATH](examples-using-path-mode.md)  
  
## <a name="see-also"></a>Consulte también  
 [Agregar espacios de nombres a consultas con WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql)   
 [FOR XML &#40;SQL Server&#41;](for-xml-sql-server.md)  
  
  
