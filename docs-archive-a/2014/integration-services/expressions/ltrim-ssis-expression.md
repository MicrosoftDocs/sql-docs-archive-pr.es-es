---
title: LTRIM (expresión de SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- leading blanks
- LTRIM function
ms.assetid: d082f42a-d7e7-49f5-a503-ac44ba630832
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 678d9d93eb1dcd7649d2085b651a08418bbcd6a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672193"
---
# <a name="ltrim-ssis-expression"></a>LTRIM (expresión de SSIS)
  Devuelve una expresión de caracteres tras quitar todos los espacios iniciales en blanco.  
  
> [!NOTE]  
>  LTRIM no quita los caracteres de espacio en blanco, como los caracteres de tabulación o de salto de línea. Unicode proporciona puntos de código para muchos tipos distintos de espacios, pero su función solo reconoce el punto de código Unicode 0x0020. Cuando se convierten cadenas del juego de caracteres de doble byte (DBCS) a Unicode, éstas pueden incluir caracteres de espacio distintos de 0x0020 y la función no puede eliminarlos. Para eliminar cualquier tipo de espacio, puede utilizar el método LTrim de Microsoft Visual Basic .NET en un script ejecutado desde el componente Script.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
LTRIM(character expression)  
```  
  
## <a name="arguments"></a>Argumentos  
 *character_expression*  
 Expresión de caracteres de la que puede quitar espacios.  
  
## <a name="result-types"></a>Tipos de resultado  
 DT_WSTR  
  
## <a name="remarks"></a>Observaciones  
 LTRIM solo funciona con el tipo de datos DT_WSTR. Un argumento *character_expression* que sea un literal de cadena o una columna de datos con el tipo de datos DT_STR se convertirá implícitamente al tipo de datos DT_WSTR antes de que LTRIM realice su operación. Los otros tipos de datos deben convertirse explícitamente al tipo de datos DT_WSTR. Para obtener más información, vea [Tipos de datos de Integration Services](../data-flow/integration-services-data-types.md) y [Conversión &#40;expresión de SSIS&#41;](cast-ssis-expression.md).  
  
 LTRIM devuelve un resultado NULL si el valor del argumento es NULL.  
  
## <a name="expression-examples"></a>Ejemplos de expresiones  
 Este ejemplo quita los espacios iniciales de un literal de cadena. El resultado devuelto es "Hello".  
  
```  
LTRIM("    Hello")  
```  
  
 Este ejemplo quita los espacios iniciales de los valores de la columna **FirstName** .  
  
```  
LTRIM(FirstName)  
```  
  
 Este ejemplo quita los espacios iniciales de los valores de la variable **FirstName** .  
  
```  
LTRIM(@FirstName)  
```  
  
## <a name="see-also"></a>Consulte también  
 [RTRIM &#40;expresión de SSIS&#41;](trim-ssis-expression.md)   
 [TRIM &#40;expresión de SSIS&#41;](trim-ssis-expression.md)   
 [Funciones &#40;expresión de SSIS&#41;](functions-ssis-expression.md)  
  
  
