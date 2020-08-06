---
title: Consulta de datos espaciales para el vecino más próximo | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 7af4ad5d-484e-45b4-aa16-83c33b358bb6
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 644b3e5cfdaeff7457639bc2da77260b64011735
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676950"
---
# <a name="query-spatial-data-for-nearest-neighbor"></a>Consultar datos espaciales para el vecino más próximo
  Una consulta frecuente utilizada con datos espaciales es la de vecino más cercano. Las consultas de vecino más cercano se emplean para encontrar los objetos espaciales más cercanos a un objeto espacial concreto. Por ejemplo, un buscador de tiendas de un sitio web debe encontrar a menudo las ubicaciones de las tiendas más cercanas a la ubicación de un cliente.  
  
 Se puede escribir una consulta de vecino más cercano en distintos formatos de consulta válidos, pero para que dicha consulta use un índice espacial se debe emplear la siguiente sintaxis.  
  
## <a name="syntax"></a>Sintaxis  
  
```vb  
SELECT TOP ( number )  
        [ WITH TIES ]  
        [ * | expression ]   
        [, ...]  
    FROM spatial_table_reference, ...   
        [ WITH   
            (   
                [ INDEX ( index_ref ) ]   
                [ , SPATIAL_WINDOW_MAX_CELLS = <value>]   
                [ ,... ]   
            )   
        ]  
    WHERE   
        column_ref.STDistance ( @spatial_ object )   
            {   
                [ IS NOT NULL ] | [ < const ] | [ > const ]   
                | [ <= const ] | [ >= const ] | [ <> const ] ]   
            }  
            [ AND { other_predicate } ]   
    }  
    ORDER BY column_ref.STDistance ( @spatial_ object ) [ ,...n ]  
[ ; ]  
  
```  
  
## <a name="nearest-neighbor-query-and-spatial-indexes"></a>Consulta de vecino más cercano e índices espaciales  
 En [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], las cláusulas `TOP` y `ORDER BY` se usan para realizar una consulta de vecino más cercano en columnas de datos espaciales. La cláusula `ORDER BY` contiene una llamada al método `STDistance()` para el tipo de datos de columna espacial. La cláusula `TOP` indica el número de objetos que se va a devolver para la consulta.  
  
 Se deben cumplir los siguientes requisitos para que una consulta de vecino más cercano utilice un índice espacial:  
  
1.  Debe haber un índice espacial en una de las columnas espaciales y el método `STDistance()` debe utilizar esa columna en las cláusulas `WHERE` y `ORDER BY`.  
  
2.  La cláusula `TOP` no puede contener una instrucción `PERCENT`.  
  
3.  La cláusula `WHERE` debe contener un método `STDistance()`.  
  
4.  Si hay varios predicados en la cláusula `WHERE`, el predicado que contiene el método `STDistance()` debe estar conectado por una conjunción `AND` a los demás predicados. El método `STDistance()` no puede estar en una parte opcional de la cláusula `WHERE`.  
  
5.  La primera expresión de la cláusula `ORDER BY` debe utilizar el método `STDistance()`.  
  
6.  El criterio de ordenación para la primera expresión `STDistance()` de la cláusula `ORDER BY` debe ser `ASC`.  
  
7.  Todas las filas para las que `STDistance` devuelve `NULL` se deben filtrar.  
  
> [!WARNING]  
>  Los métodos que toman los tipos de datos `geography` o `geometry` como argumentos devolverán `NULL` si los SRID no son los mismos para los tipos.  
  
 Se recomienda utilizar las nuevas teselaciones de índice espacial para los índices empleados en las consultas de vecino más cercano. Para obtener más información sobre las teselaciones de índice espacial, vea [Datos espaciales &#40;SQL Server&#41;](spatial-data-sql-server.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra una consulta de vecino más cercano que puede utilizar un índice espacial. En el ejemplo se utiliza la tabla `Person.Address` de la base de datos `AdventureWorks2012` .  
  
```  
USE AdventureWorks2012  
GO  
DECLARE @g geography = 'POINT(-121.626 47.8315)';  
SELECT TOP(7) SpatialLocation.ToString(), City FROM Person.Address  
WHERE SpatialLocation.STDistance(@g) IS NOT NULL  
ORDER BY SpatialLocation.STDistance(@g);  
  
```  
  
 Cree un índice espacial en la columna SpatialLocation para ver cómo una consulta de vecino más cercano utiliza un índice espacial. Para obtener más información sobre cómo crear índices espaciales, vea [Create, Modify, and Drop Spatial Indexes](create-modify-and-drop-spatial-indexes.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra una consulta de vecino más cercano que no puede utilizar un índice espacial.  
  
```  
USE AdventureWorks2012  
GO  
DECLARE @g geography = 'POINT(-121.626 47.8315)';  
SELECT TOP(7) SpatialLocation.ToString(), City FROM Person.Address  
ORDER BY SpatialLocation.STDistance(@g);  
  
```  
  
 A la consulta le falta una cláusula `WHERE` que utilice `STDistance()` en un formato especificado en la sección de sintaxis, por lo que la consulta no puede utilizar un índice espacial.  
  
## <a name="see-also"></a>Consulte también  
 [Datos espaciales &#40;SQL Server&#41;](spatial-data-sql-server.md)  
  
  
