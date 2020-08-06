---
title: Establecer opciones de cursor (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], options
ms.assetid: 0e72b48a-fc5a-4656-8cf5-39f57d8c1565
author: rothja
ms.author: jroth
ms.openlocfilehash: 877c2596c87ce50295a15912493661c6dd4e0305
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87749285"
---
# <a name="set-cursor-options-odbc"></a>Establecer las opciones del cursor (ODBC)
  Para establecer las opciones de cursor, llame a [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) para establecer o [SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md) para obtener las opciones de la instrucción que controlan el comportamiento del cursor.  
  
|*Attribute*|Especifica|  
|-----------------|---------------|  
|SQL_ATTR_CURSOR_TYPE|Tipo de cursor de solo avance, estático, dinámico o controlado por conjunto de claves|  
|SQL_ATTR_CONCURRENCY|Opción de control de simultaneidad de solo lectura, bloqueo, marcas de tiempo de uso optimista o valores de uso optimista|  
|SQL_ATTR_ROW_ARRAY_SIZE|Número de filas obtenido en cada captura|  
|SQL_ATTR_CURSOR_SENSITIVITY|Cursor que puede mostrar o no las actualizaciones realizadas por otras conexiones en las filas del cursor|  
|SQL_ATTR_CURSOR_SCROLLABLE|Cursor que puede desplazarse hacia delante y hacia atrás|  
  
 Los valores predeterminados de estos atributos (solo avance, solo lectura, tamaño del conjunto de filas igual a 1) no usan los cursores del servidor. Para usar los cursores del servidor, al menos uno de estos atributos debe establecerse en un valor distinto del predeterminado y la instrucción en ejecución debe ser una instrucción SELECT única o un procedimiento almacenado que contenga una instrucción SELECT única. Cuando se utilizan los cursores del servidor, las instrucciones SELECT no pueden utilizar cláusulas que no sean compatibles con los cursores del servidor: COMPUTE, COMPUTE BY, FOR BROWSE e INTO.  
  
 Puede controlar el tipo de cursor utilizando estableciendo SQL_ATTR_CURSOR_TYPE y SQL_ATTR_CONCURRENCY o estableciendo SQL_ATTR_CURSOR_SENSITIVITY y SQL_ATTR_CURSOR_SCROLLABLE. No debe mezclar los dos métodos que se utilizan para especificar el comportamiento del cursor.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se asigna un identificador de instrucción, se establece un tipo de cursor dinámico con simultaneidad optimista de versiones de fila y, a continuación, se ejecuta una instrucción SELECT.  
  
```  
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER)SQL_CURSOR_DYNAMIC, SQL_IS_INTEGER);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CONCURRENCY, SQLPOINTER)SQL_CONCUR_ROWVER, SQL_IS_INTEGER);  
retcode = SQLExecDirect(hstmt1, SELECT au_lname FROM authors", SQL_NTS);  
```  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se asigna un identificador de instrucción, se establece un cursor desplazable de tipo SENSITIVE y, a continuación, se ejecuta una instrucción SELECT  
  
```  
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
  
// Set the cursor options and execute the statement.  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_SCROLLABLE, SQLPOINTER)SQL_SCROLLABLE, SQL_IS_INTEGER);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_SENSITIVITY, SQLPOINTER)SQL_INSENSITIVE, SQL_IS_INTEGER);  
retcode = SQLExecDirect(hstmt1, select au_lname from authors", SQL_NTS);  
```  
  
## <a name="see-also"></a>Consulte también  
 [Temas de procedimientos de ejecución de consultas &#40;ODBC&#41;](executing-queries-how-to-topics-odbc.md)  
  
  
