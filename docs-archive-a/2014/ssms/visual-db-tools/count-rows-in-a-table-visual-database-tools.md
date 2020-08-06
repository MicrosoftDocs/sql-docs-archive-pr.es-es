---
title: Contar las filas de una tabla (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- totals [SQL Server], row counts
- row counts [SQL Server]
- column values [SQL Server]
- number of rows
- number of values
- counting rows
ms.assetid: dda4296a-1d16-4e77-8d6f-e295f6dd4e87
author: stevestein
ms.author: sstein
ms.openlocfilehash: f6dca92fb955b776f56d9b51f28b1a486b89f18f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746066"
---
# <a name="count-rows-in-a-table-visual-database-tools"></a>Contar las filas de una tabla (Visual Database Tools)
  Puede contar las filas de una tabla para determinar:  
  
-   El número total de filas de una tabla, como por ejemplo, la suma de todos los libros de una tabla `titles` .  
  
-   El número de filas de una tabla que satisfacen una condición específica, como por ejemplo, el número de libros de una editorial en una tabla `titles` .  
  
-   El número de valores de una determinada columna.  
  
 Cuando se cuentan los valores de una columna, no se incluyen los valores NULL en el recuento. Por ejemplo, es posible que desee hacer el recuento del número de libros de una tabla `titles` que tiene valores en la columna `advance` . De forma predeterminada, el recuento incluirá todos los valores y no solo los valores únicos.  
  
 Los procedimientos para los tres tipos de recuentos son similares.  
  
### <a name="to-count-all-the-rows-in-a-table"></a>Para contar todas las filas de una tabla  
  
1.  Asegúrese de que la tabla que desea resumir ya esté presente en el panel Diagrama.  
  
2.  Haga clic con el botón derecho en el fondo del panel Diagrama y, a continuación, elija **Agregar grupo por** en el menú contextual. El [Diseñador de consultas y vistas](visual-database-tools.md) agrega una columna **Agrupar por** a la cuadrícula en el panel Criterios.  
  
3.  Seleccione ** \* (todas las columnas)** en el rectángulo que representa la tabla o el objeto con valores de tabla.  
  
     El Diseñador de consultas y vistas escribe automáticamente el término **Recuento** en la columna **Agrupar por** del panel Criterios y asigna un alias a la columna que se va a resumir. Puede sustituir este alias generado automáticamente por otro más significativo. Para más información, consulte [Crear alias de columna &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).  
  
4.  Ejecuta la consulta.  
  
### <a name="to-count-all-the-rows-that-meet-a-condition"></a>Para contar todas las filas que cumplen una condición  
  
1.  Asegúrese de que la tabla que desea resumir ya esté presente en el panel Diagrama.  
  
2.  Haga clic con el botón derecho en el fondo del panel Diagrama y, a continuación, elija **Agregar grupo por** en el menú contextual. El Diseñador de consultas y vistas agrega una columna **Agrupar por** a la cuadrícula en el panel Criterios.  
  
3.  Seleccione ** \* (todas las columnas)** en el rectángulo que representa la tabla o el objeto con estructura de tabla.  
  
     El Diseñador de consultas y vistas escribe automáticamente el término **Recuento** en la columna **Agrupar por** del panel Criterios y asigna un alias a la columna que se va a resumir. Para crear un encabezado de columna más útil en el resultado de la consulta, vea [Crear alias de columna &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).  
  
4.  Agregue la columna de datos que desea buscar y, a continuación, desactive la casilla de la columna **Resultados**.  
  
     El Diseñador de consultas y vistas incluye automáticamente el término **Agrupar por** en la columna **Agrupar por** de la cuadrícula.  
  
5.  Cambie **Agrupar por** en la columna **Agrupar por** por **Ubicación**.  
  
6.  En la columna **Filtro** de la columna de datos en la que va a realizar la búsqueda, especifique la condición de búsqueda.  
  
7.  Ejecuta la consulta.  
  
### <a name="to-count-the-values-in-a-column"></a>Para contar los valores de una columna  
  
1.  Asegúrese de que la tabla que desea resumir ya esté presente en el panel Diagrama.  
  
2.  Haga clic con el botón derecho en el fondo del panel Diagrama y, a continuación, elija **Agregar grupo por** en el menú contextual. El Diseñador de consultas y vistas agrega una columna **Agrupar por** a la cuadrícula en el panel Criterios.  
  
3.  Agregue la columna que desea contar al panel Criterios.  
  
     El Diseñador de consultas y vistas incluye automáticamente el término **Agrupar por** en la columna **Agrupar por** de la cuadrícula.  
  
4.  Cambie **Agrupar por** en la columna **Agrupar por** por **Recuento**.  
  
    > [!NOTE]  
    >  Para contar solo valores únicos, elija **Count Distinct**.  
  
5.  Ejecuta la consulta.  
  
## <a name="see-also"></a>Consulte también  
 [Ordenar y agrupar los resultados de una consulta &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md)   
 [Resumir los resultados de una consulta &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md)  
  
  
