---
title: Cuadro de diálogo de la expresión de restricción CHECK (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.checkconstraintexpression
ms.assetid: beb6ce43-3913-4d66-8826-8e885335b790
author: stevestein
ms.author: sstein
ms.openlocfilehash: 38268d4e49a9c674c100bc22c0782e3e61477967
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661759"
---
# <a name="check-constraint-expression-dialog-box-visual-database-tools"></a>Expresión de restricción CHECK (cuadro de diálogo, Visual Database Tools)
  Cuando asocie una restricción CHECK a una tabla o columna, debe incluir una expresión SQL. Escriba la expresión de restricción CHECK en el cuadro correspondiente.  
  
## <a name="ui-element-list"></a>Lista de elementos de la interfaz de usuario  
 Expression  
 Escriba la expresión.  
  
 Puede crear una expresión de restricción sencilla para comprobar una condición sencilla en los datos o puede crear una expresión compleja mediante operadores booleanos para comprobar varias condiciones en los datos. Por ejemplo, supongamos que la tabla authors tiene una columna zip que requiere una cadena de caracteres de 5 dígitos. Esta expresión de restricción de ejemplo garantiza que solo se permitan números de 5 dígitos:  
  
```  
zip LIKE '[0-9][0-9][0-9][0-9][0-9]'  
```  
  
 O bien, supongamos que la tabla sales tiene una columna llamada qty que requiere un valor mayor que 0. Esta restricción de muestra garantiza que solo se permitan los valores positivos:  
  
```  
qty > 0  
```  
  
 Supongamos también que la tabla orders limita el tipo de tarjetas de crédito admitidas para todos los pedidos de tarjeta de crédito. Esta restricción de ejemplo garantiza que si el pedido se realiza con una tarjeta de crédito, solo se aceptará Visa, MasterCard o American Express:  
  
```  
NOT (payment_method = 'credit card') OR  
   (card_type IN ('VISA', 'MASTERCARD', 'AMERICAN EXPRESS'))  
```  
  
## <a name="to-define-a-constraint-expression"></a>Para definir una expresión de restricción  
 En la pestaña Restricciones CHECK de las páginas de propiedades, escriba una expresión en el cuadro de diálogo Expresión de restricción CHECK utilizando la sintaxis siguiente:  
  
 `{constant | column_name | function | (subquery)}`  
  
 `[{operator | AND | OR | NOT}`  
  
 `{constant | column_name | function | (subquery)}...]`  
  
 La sintaxis de SQL está formada por los siguientes parámetros:  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|constant|Valor literal, como un valor numérico o una cadena de caracteres. Los datos de caracteres deben escribirse entre comillas sencillas (').|  
|column_name|Especifica una columna.|  
|function|Función integrada.|  
|operator|Operadores aritméticos, bit a bit, de comparación o de cadena.|  
|y|Se utiliza en expresiones booleanas para conectar dos expresiones. Se devuelven resultados cuando las dos expresiones son verdaderas.<br /><br /> Cuando se utilizan los operadores AND y OR en una instrucción, se procesará primero el operador AND. Puede cambiar el orden de ejecución utilizando paréntesis.|  
|O BIEN|Se utiliza en expresiones booleanas para conectar dos o más condiciones. Se devuelven resultados cuando al menos una de las condiciones sea verdadera.<br /><br /> Cuando se utilizan los operadores AND y OR en una instrucción, OR se evaluará después de AND. Puede cambiar el orden de ejecución utilizando paréntesis.|  
|NOT|Niega cualquier expresión booleana (que puede incluir palabras clave como LIKE, NULL, BETWEEN, IN y EXISTS).<br /><br /> Cuando se utiliza más de un operador lógico en una instrucción, se procesará primero el operador NOT. Puede cambiar el orden de ejecución utilizando paréntesis.|  
  
## <a name="see-also"></a>Consulte también  
 [Restricciones UNIQUE y restricciones check](../../relational-databases/tables/unique-constraints-and-check-constraints.md)   
 [Crear restricciones UNIQUE](../../relational-databases/tables/create-unique-constraints.md)  
  
  
