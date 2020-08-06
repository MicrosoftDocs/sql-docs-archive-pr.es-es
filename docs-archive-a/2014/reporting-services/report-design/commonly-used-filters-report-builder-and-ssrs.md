---
title: Filtros de uso frecuente (Generador de informes y SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- multivalued parameters [Reporting Services]
- single-valued parameters [Reporting Services]
- parameters [Reporting Services], multivalued
- valid values [Reporting Services]
ms.assetid: cb70d0cd-707b-4de5-b39f-e4eb57d316aa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 201cf83d431d1b61e0f20e9d039b2016ad4f13e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673492"
---
# <a name="commonly-used-filters-report-builder-and-ssrs"></a>Filtros de uso frecuente (Generador de informes y SSRS)
  Para crear un filtro, debe especificar una o varias ecuaciones de filtro. Una ecuación de filtro incluye una expresión, un tipo de datos, un operador y un valor. En este tema, se proporcionan ejemplos de filtros usados habitualmente.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="filter-examples"></a>Ejemplos de filtros  
 En la tabla siguiente, se muestran ejemplos de ecuaciones de filtro que usan tipos de datos y operadores diferentes. El elemento de informe para el que se define un filtro determina el ámbito de la comparación. Por ejemplo, para un filtro definido en un conjunto de datos, **TOP % 10** es el 10 por ciento de los valores más altos del conjunto de datos; para un filtro definido en un grupo, **TOP% 10** es el 10 por ciento de los valores más altos del grupo.  
  
|Expresión simple|Tipo de datos|Operator|Value|Descripción|  
|-----------------------|---------------|--------------|-----------|-----------------|  
|`[SUM(Quantity)]`|`Integer`|`>`|`7`|Incluye valores de datos que son mayores que 7.|  
|`[SUM(Quantity)]`|`Integer`|`TOP N`|`10`|Incluye los 10 valores de datos más altos.|  
|`[SUM(Quantity)]`|`Integer`|`TOP %`|`20`|Incluye el 20% de los valores de datos más altos.|  
|`[Sales]`|`Text`|`>`|`=CDec(100)`|Incluye todos los valores de tipo System.Decimal (tipos de datos "money" de SQL) mayores que $100.|  
|`[OrderDate]`|`DateTime`|`>`|`2088-01-01`|Incluye todas las fechas desde el 1 de enero de 2008 hasta la fecha actual.|  
|`[OrderDate]`|`DateTime`|`BETWEEN`|`2008-01-01`<br /><br /> `2008-02-01`|Incluye las fechas desde el 1 de enero de 2008 hasta el 1 de febrero de 2008, inclusive.|  
|`[Territory]`|`Text`|`LIKE`|`*east`|Todos los nombres de territorios que terminan en "east".|  
|`[Territory]`|`Text`|`LIKE`|`%o%th*`|Todos los nombres de territorios que incluyen North y South al principio del nombre.|  
|`=LEFT(Fields!Subcat.Value,1)`|`Text`|`IN`|`B, C, T`|Todos los valores de subcategoría que comienzan con las letras B, C o T.|  
  
## <a name="examples-with-report-parameters"></a>Ejemplos con parámetros de informe  
 En la tabla siguiente, se proporcionan ejemplos de expresiones de filtro que incluyen una referencia a un parámetro con un solo valor o con varios valores.  
  
|Tipo de parámetro|Expresión (Filtro)|Operador|Value|Tipo de datos|  
|--------------------|---------------------------|--------------|-----------|---------------|  
|Un solo valor|`[EmployeeID]`|=|`[@EmployeeID]`|Entero|  
|Varios valores|`[EmployeeID]`|IN|`[@EmployeeID]`|Entero|  
  
## <a name="see-also"></a>Consulte también  
 [Parámetros de informe &#40;Generador de informes y Diseñador de informes&#41;](report-parameters-report-builder-and-report-designer.md)   
 [Agregar filtros de conjunto de datos, filtros de región de datos y filtros de grupo &#40;Generador de informes y SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md)   
 [La expresión usa en los informes &#40;Generador de informes y SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Ejemplos de expresiones &#40;Generador de informes y SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Tipos de datos en expresiones &#40;Generador de informes y SSRS&#41;](expressions-report-builder-and-ssrs.md)  
  
  
