---
title: Dividir (expresión de SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- / (divide)
- divide operator (/)
ms.assetid: 5bde9223-872d-443e-8a27-57735e1d8f3d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4541cd4601047770d1bf361077b1c474219e8833
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669756"
---
# <a name="divide-ssis-expression"></a>Divide (SSIS Expression)
  Divide la primera expresión numérica por la segunda.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dividend / divisor  
  
```  
  
## <a name="arguments"></a>Argumentos  
 *dividend*  
 Es la expresión numérica que se va a dividir. *dividend* puede ser cualquier expresión numérica. Para obtener más información, vea [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
 *divisor*  
 Es la expresión numérica entre la que se va a dividir el dividendo. *divisor* puede ser cualquier expresión numérica excepto cero.  
  
## <a name="result-types"></a>Tipos de resultado  
 Determinados por los tipos de datos de los dos argumentos. Para más información, consulte [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Observaciones  
 Si alguno de los operandos es NULL, el resultado será NULL.  
  
 No se permite dividir por cero. En función de cómo se evalúe la subexpresión *divisor* , se producirá uno de los siguientes errores:  
  
-   Si la subexpresión *divisor* que devuelve cero es una constante, el error aparecerá en tiempo de diseño y hará que no se valide la expresión.  
  
-   Si la subexpresión *divisor* que devuelve cero contiene variables pero no contiene columnas de entrada, el componente al que la expresión pertenece no superará la validación previa a la ejecución del paquete.  
  
-   Si la subexpresión *divisor* que se evalúa como cero contiene columnas de entrada, el error aparecerá en tiempo de ejecución y se controlará en función de las reglas de flujo de errores del componente de flujo de datos.  
  
## <a name="expression-examples"></a>Ejemplos de expresiones  
 Este ejemplo divide dos literales numéricos.  
  
```  
25 / 5  
```  
  
 Este ejemplo divide los valores de la columna **ListPrice** por los valores de la columna **StandardCost** .  
  
```  
ListPrice / StandardCost  
```  
  
## <a name="see-also"></a>Consulte también  
 [Precedencia y capacidad de asociación de operadores](operator-precedence-and-associativity.md)   
 [Operadores &#40;expresión de SSIS&#41;](operators-ssis-expression.md)  
  
  
