---
title: Ejecutar directamente una instrucción (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statement execution
ms.assetid: b690f9de-66e1-4ee5-ab6a-121346fb5f85
author: rothja
ms.author: jroth
ms.openlocfilehash: 2aeada906a925cff93455ffd92e7c17822a80124
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661986"
---
# <a name="execute-a-statement-directly-odbc"></a>Ejecutar directamente una instrucción (ODBC)
    
### <a name="to-execute-a-statement-directly-and-one-time-only"></a>Para ejecutar directamente y solo una vez una instrucción  
  
1.  Si la instrucción tiene marcadores de parámetro, utilice [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) para enlazar cada parámetro a una variable de programa. Llene las variables de programa de valores de datos y, a continuación, prepare los parámetros de datos en ejecución.  
  
2.  Llame a [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) para ejecutar la instrucción.  
  
3.  Si se usan parámetros de entrada de datos en ejecución, [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) devuelve SQL_NEED_DATA. Envíe los datos en fragmentos utilizyo [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) y [SQLPutData](../../native-client-odbc-api/sqlputdata.md).  
  
### <a name="to-execute-a-statement-multiple-times-by-using-column-wise-parameter-binding"></a>Para ejecutar varias veces una instrucción utilizando el enlace de parámetro de modo de columna  
  
1.  Llame a [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) para establecer los atributos siguientes:  
  
     Establezca SQL_ATTR_PARAMSET_SIZE en el número de conjuntos (S) de parámetros.  
  
     Establezca SQL_ATTR_PARAM_BIND_TYPE en SQL_PARAMETER_BIND_BY_COLUMN.  
  
     Establezca el atributo SQL_ATTR_PARAMS_PROCESSED_PTR para que señale a una variable SQLUINTEGER que incluya el número de parámetros procesados.  
  
     Establezca SQL_ATTR_PARAMS_STATUS_PTR para que señale a una matriz[S] de variables SQLUSSMALLINT que incluya los indicadores de estado de parámetros.  
  
2.  Para cada marcador de parámetro:  
  
     Asigne una matriz de S búferes de parámetros donde almacenar los valores de datos.  
  
     Asigne una matriz de S búferes de parámetros donde almacenar las longitudes de datos.  
  
     Llame a [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) para enlazar el valor de datos de parámetro y las matrices de longitud de datos al parámetro de instrucción.  
  
     Prepare los parámetros de texto o imagen de datos en ejecución.  
  
     Coloque S valores de datos y S longitudes de datos en las matrices de parámetros enlazadas.  
  
3.  Llame a [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) para ejecutar la instrucción. El controlador ejecuta eficazmente la instrucción S veces, una vez para cada conjunto de parámetros.  
  
4.  Si se usan parámetros de entrada de datos en ejecución, [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) devuelve SQL_NEED_DATA. Envíe los datos en fragmentos utilizyo [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) y [SQLPutData](../../native-client-odbc-api/sqlputdata.md).  
  
### <a name="to-execute-a-statement-multiple-times-by-using-row-wise-parameter-binding"></a>Para ejecutar varias veces una instrucción utilizando el enlace de parámetro de modo de fila  
  
1.  Asigne una matriz[S] de estructuras, donde S es el número de conjuntos de parámetros. La estructura tiene un elemento para cada parámetro y cada elemento tiene dos partes:  
  
     La primera parte es una variable del tipo de datos adecuado donde almacenar los datos de parámetros.  
  
     La segunda parte es una variable SQLINTEGER donde almacenar el indicador de estado.  
  
2.  Llame a [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) para establecer los atributos siguientes:  
  
     Establezca SQL_ATTR_PARAMSET_SIZE en el número de conjuntos (S) de parámetros.  
  
     Establezca SQL_ATTR_PARAM_BIND_TYPE en el tamaño de la estructura asignada en el paso 1.  
  
     Establezca el atributo SQL_ATTR_PARAMS_PROCESSED_PTR para que señale a una variable SQLUINTEGER que incluya el número de parámetros procesados.  
  
     Establezca SQL_ATTR_PARAMS_STATUS_PTR para que señale a una matriz[S] de variables SQLUSSMALLINT que incluya los indicadores de estado de parámetros.  
  
3.  Para cada marcador de parámetro, llame a [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) para que el valor de datos de parámetro y el puntero de longitud de datos señalen a sus variables en el primer elemento de la matriz de estructuras asignada en el paso 1. Si el parámetro es un parámetro de datos en ejecución, configúrelo.  
  
4.  Rellene la matriz de búferes de parámetros enlazados con valores de datos.  
  
5.  Llame a [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) para ejecutar la instrucción. El controlador ejecuta eficazmente la instrucción S veces, una vez para cada conjunto de parámetros.  
  
6.  Si se usan parámetros de entrada de datos en ejecución, [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) devuelve SQL_NEED_DATA. Envíe los datos en fragmentos utilizyo [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) y [SQLPutData](../../native-client-odbc-api/sqlputdata.md).  
  
 **Nota** Los enlaces de modo de columna y de modo de fila se usan con mayor frecuencia con [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360) y [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) que con [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399).  
  
## <a name="see-also"></a>Consulte también  
 [Temas de procedimientos de ejecución de consultas &#40;ODBC&#41;](executing-queries-how-to-topics-odbc.md)  
  
  
