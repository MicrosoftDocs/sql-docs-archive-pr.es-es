---
title: '|| (OR lógico) (expresión de SSIS) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- OR operator
- logical OR (||)
- '|| (logical OR)'
ms.assetid: a3c07c09-f121-4187-9617-b01adcf843c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 72d4a1c7b54856675f0faa7f5f58452cb8bca450
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744793"
---
# <a name="-logical-or-ssis-expression"></a>|| (OR lógico) (expresión de SSIS)
  Realiza una operación lógica OR. La expresión devuelve TRUE si una o ambas condiciones son TRUE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
boolean_expression1 || boolean_expression2  
```  
  
## <a name="arguments"></a>Argumentos  
 *boolean_expression1, boolean_expression2*  
 Cualquier expresión válida cuya evaluación devuelva TRUE, FALSE o NULL.  
  
## <a name="result-types"></a>Tipos de resultado  
 DT_BOOL  
  
## <a name="remarks"></a>Observaciones  
 En la siguiente tabla se muestra el resultado del operador ||.  
  
|Resultado|Expression|Expression|  
|------------|----------------|----------------|  
|TRUE|TRUE|TRUE|  
|TRUE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
|NULL|NULL|NULL|  
|TRUE|NULL|TRUE|  
|NULL|NULL|FALSE|  
  
## <a name="ssis-expression-examples"></a>Ejemplos de expresiones de SSIS  
 En este ejemplo se usan las columnas **StandardCost** y **ListPrice** . Este ejemplo devuelve TRUE si el valor de la columna **StandardCost** es menor que 300 o el valor de la columna **ListPrice** es mayor que 500.  
  
```  
StandardCost < 300 || ListPrice > 500  
```  
  
 En este ejemplo se utilizan las variables **SPrice** y **LPrice** en lugar de literales numéricos.  
  
```  
StandardCost < @SPrice || ListPrice > @LPrice  
```  
  
## <a name="see-also"></a>Consulte también  
 [&#124; &#40;OR inclusivo bit a bit&#41; &#40;expresión de SSIS&#41;](bitwise-inclusive-or-ssis-expression.md)   
 [^ &#40;OR exclusivo bit a bit&#41; &#40;expresión de SSIS&#41;](bitwise-exclusive-or-ssis-expression.md)   
 [Precedencia y capacidad de asociación de operadores](operator-precedence-and-associativity.md)   
 [Operadores &#40;expresión de SSIS&#41;](operators-ssis-expression.md)  
  
  
