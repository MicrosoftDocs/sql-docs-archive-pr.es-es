---
title: NULL (expresión de SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- NULL function
- null values [Integration Services]
ms.assetid: df144237-3fbb-41ac-8624-efd92b6522b9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e14cd51b4e245ca6984a4c62eae2b9d5536ab1f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663024"
---
# <a name="null-ssis-expression"></a>NULL (expresión de SSIS)
  Devuelve un valor NULL asociado al tipo de datos solicitado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
NULL(typespec)  
```  
  
## <a name="arguments"></a>Argumentos  
 *typespec*  
 Tipo de datos válido. Para obtener más información, vea [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Tipos de resultado  
 Cualquier tipo de datos válido con valor NULL.  
  
## <a name="remarks"></a>Observaciones  
 NULL devuelve un resultado NULL si el valor del argumento es NULL.  
  
 Para solicitar un valor NULL para algunos tipos de datos es necesario utilizar parámetros. En la tabla siguiente se muestran estos tipos de datos y sus parámetros.  
  
|Tipo de datos|Parámetro|Ejemplo|  
|---------------|---------------|-------------|  
|DT_STR|*charcount*<br /><br /> *codepage*|(DT_STR,30,1252) convierte 30 caracteres al tipo de datos DT_STR con la página de códigos 1252.|  
|DT_WSTR|*charcount*|(DT_WSTR,20) convierte 20 caracteres al tipo de datos DT_WSTR.|  
|DT_BYTES|*bytecount*|(DT_BYTES,50) convierte 50 bytes al tipo de datos DT_BYTES.|  
|DT_DECIMAL|*scale*|(DT_DECIMAL,2) convierte un valor numérico al tipo de datos DT_DECIMAL con una escala de 2.|  
|DT_NUMERIC|*precisión*<br /><br /> *scale*|(DT_NUMERIC,10,3) convierte un valor numérico al tipo de datos DT_NUMERIC con una precisión de 10 decimales y una escala de 3.|  
|DT_TEXT|*codepage*|(DT_TEXT,1252) convierte un valor al tipo de datos DT_TEXT con la página de códigos 1252.|  
  
## <a name="expression-examples"></a>Ejemplos de expresiones  
 Estos ejemplos devuelven el valor NULL asociado a los tipos de datos DT_STR, DT_DATE y DT_BOOL.  
  
```  
NULL(DT_STR,10,1252)  
NULL(DT_DATE)  
NULL(DT_BOOL)  
```  
  
## <a name="see-also"></a>Consulte también  
 [ISNULL &#40;expresión de SSIS&#41;](null-ssis-expression.md)   
 [Funciones &#40;expresión de SSIS&#41;](functions-ssis-expression.md)  
  
  
