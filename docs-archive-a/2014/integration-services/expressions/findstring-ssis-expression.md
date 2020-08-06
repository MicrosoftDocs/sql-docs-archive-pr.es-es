---
title: FINDSTRING (expresión de SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- FINDSTRING function
ms.assetid: c83cb1b1-3c52-4496-b518-4c9253b9336d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 72f2ff21cb179ce565e60c6550b8ecc2618a5adb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672197"
---
# <a name="findstring-ssis-expression"></a>FINDSTRING (expresión de SSIS)
  Devuelve la ubicación de la repetición especificada de una cadena en una expresión de caracteres. El resultado devuelto es el índice de base uno de la repetición. El parámetro string debe devolver una expresión de caracteres y el parámetro occurrence debe devolver un entero. Si no se encuentra la cadena, el valor devuelto es 0. Si la cadena aparece menos veces de las que especifica el argumento de repetición, el valor devuelto es 0.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
FINDSTRING(character_expression, searchstring, occurrence)  
```  
  
## <a name="arguments"></a>Argumentos  
 *character_expression*  
 Cadena de caracteres en la que se va a buscar.  
  
 *searchstring*  
 Cadena de caracteres que se va a buscar.  
  
 *occurrence*  
 Entero con o sin signo que especifica la repetición de *searchstring* que se debe notificar.  
  
## <a name="result-types"></a>Tipos de resultado  
 DT_I4  
  
## <a name="remarks"></a>Observaciones  
 FINDSTRING solo funciona con el tipo de datos DT_WSTR.  Los argumentos*character_expression* y *searchstring* , que son literales de cadena o columnas de datos con el tipo de datos DT_STR, se convierten implícitamente al tipo de datos DT_WSTR antes de que FINDSTRING realice su operación. Los otros tipos de datos deben convertirse explícitamente al tipo de datos DT_WSTR. Para obtener más información, vea [Tipos de datos de Integration Services](../data-flow/integration-services-data-types.md) y [Conversión &#40;expresión de SSIS&#41;](cast-ssis-expression.md).  
  
 FINDSTRING devuelve NULL si el valor de *character_expression* o *searchstring* es NULL.  
  
 Para obtener el índice de la primera repetición, use el valor 1 para el argumento *occurrence* , use 2 para obtener el índice de la segunda repetición, etc.  
  
 El valor de *occurrence* debe ser un entero con un valor mayor que 0.  
  
## <a name="expression-examples"></a>Ejemplos de expresiones  
 Este ejemplo usa un literal de cadena. Devuelve el valor 11.  
  
```  
FINDSTRING("New York, NY, NY", "NY", 1)   
```  
  
 Este ejemplo usa un literal de cadena. Dado que la cadena "NY" solo aparece dos veces, el resultado devuelto es 0.  
  
```  
FINDSTRING("New York, NY, NY", "NY", 3)   
```  
  
 Este ejemplo usa la columna **Name** . Devuelve la ubicación del valor n en la columna **Name** . El resultado devuelto varía en función del valor de **Name**. Si **Name** contiene Anderson, la función devuelve 8.  
  
```  
FINDSTRING(Name,"n", 2)   
```  
  
 En este ejemplo se utilizan las columnas **Name** y **Size** . Devuelve la ubicación del primer carácter por la izquierda del valor **Size** de la columna **Name** . El resultado devuelto varía en función de los valores de columna. Si **Name** contiene Mountain,500Red,42 y **Size** contiene 42, el resultado devuelto es 17.  
  
```  
FINDSTRING(Name,Size,1)   
```  
  
## <a name="see-also"></a>Consulte también  
 [REPLACE &#40;expresión de SSIS&#41;](replace-ssis-expression.md)   
 [Funciones &#40;expresión de SSIS&#41;](functions-ssis-expression.md)  
  
  
