---
title: Metadatos de parámetro y resultado | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- metadata [ODBC]
ms.assetid: 1518e6e5-a6a8-4489-b779-064c5624df53
author: rothja
ms.author: jroth
ms.openlocfilehash: 62cc3ef8121dd17a07874a805ae2c49587107829
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748782"
---
# <a name="parameter-and-result-metadata"></a>Metadatos de parámetros y resultados
  En este tema se describe la información que se devuelve en los campos descriptor de parámetros de implementación (IPD) y descriptor de filas de implementación (IRD) para los tipos de datos de fecha y hora.  
  
## <a name="information-returned-in-ipd-fields"></a>Información que se devuelve en los campos IPD  
 La siguiente información se devuelve en los campos IPD:  
  
|Tipo de parámetro|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|--------------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CONCISE_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_CODE_DATE|0|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|0|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|10|8, 10.. 16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_LENGTH|10|8, 10.. 16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_OCTET_LENGTH|6|12|4|8|16|20|  
|SQL_DESC_PRECISION|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SCALE|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_TYPE|SQL_TYPE_DATE|SQL_SS_TYPE_TIME2|SQL_DATETIME|SQL_DATETIME|SQL_DATETIME|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_TYPE_NAME|`date`|`time`|`smalldatetime` en IRD, `datetime2` en IPD|`datetime` en IRD, `datetime2` en IPD|`datetime2`|datetimeoffset|  
|SQL_CA_SS_VARIANT_TYPE|SQL_C_TYPE_DATE|SQL_C_TYPE_BINARY|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_BINARY|  
|SQL_CA_SS_VARIANT_SQL_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_CA_SS_SERVER_TYPE|N/D|N/D|SQL_SS_TYPE_SMALLDATETIME|SQL_SS_TYPE_DATETIME|SQL_SS_TYPE_DEFAULT|N/D|  
  
 A veces, hay discontinuidades en los intervalos de valores. Por ejemplo, en el intervalo 8,10..16 falta el valor 9. Esto se debe a la adición de un separador decimal cuando la precisión fraccionaria es mayor que cero.  
  
 `datetime2` se devuelve como nombre de tipo para `smalldatetime` y `datetime` porque el controlador lo utiliza como un tipo común para transmitir al servidor todos los valores `SQL_TYPE_TIMESTAMP`.  
  
 SQL_CA_SS_VARIANT_SQL_TYPE es un nuevo campo descriptor. Este campo se agregó a IRD e IPD para permitir que las aplicaciones especificasen el tipo de valor asociado a las columnas y parámetros `sqlvariant` (SQL_SSVARIANT).  
  
 SQL_CA_SS_SERVER_TYPE es un nuevo campo solo IPD que permite a las aplicaciones controlar la forma en que se envían al servidor los valores para parámetros enlazados como SQL_TYPE_TYPETIMESTAMP (o como SQL_SS_VARIANT con un tipo C SQL_C_TYPE_TIMESTAMP). Si SQL_DESC_CONCISE_TYPE es SQL_TYPE_TIMESTAMP (o es SQL_SS_VARIANT y el tipo C es SQL_C_TYPE_TIMESTAMP) cuando se llama a SQLExecute o SQLExecDirect, el valor de SQL_CA_SS_SERVER_TYPE determina el tipo de flujo TDS del valor del parámetro, como se indica a continuación:  
  
|Valor de SQL_CA_SS_SERVER_TYPE|Valores válidos para SQL_DESC_PRECISION|Valores válidos para SQL_DESC_LENGTH|Tipo de TDS|  
|----------------------------------------|-------------------------------------------|----------------------------------------|--------------|  
|SQL_SS_TYPE_DEFAULT|0..7|19, 21..27|`datetime2`|  
|SQL_SS_TYPE_SMALLDATETIME|0|19|`smalldatetime`|  
|SQL_SS_TYPE_DATETIME|3|23|`datetime`|  
  
 La configuración predeterminada de SQL_CA_SS_SERVER_TYPE es SQL_SS_TYPE_DEFAULT. Los valores de SQL_DESC_PRECISION y SQL_DESC_LENGTH se validan con el valor de SQL_CA_SS_SERVER_TYPE, tal y como se describía en la tabla anterior. Si se produce un error en esta validación, se devuelve SQL_ERROR y se registra un error de diagnóstico con SQLState 07006 y el mensaje "Infracción del atributo de tipo de datos restringido". También se devuelve este error si SQL_CA_SS_SERVER_TYPE se establece en un valor distinto de SQL_SS_TYPE DEFAULT y DESC_CONCISE_TYPE no es SQL_TYPE_TIMESTAMP. Estas validaciones se realizan cuando se lleva a cabo la validación de coherencia de descriptor; por ejemplo:  
  
-   Cuando se modifica SQL_DESC_DATA_PTR.  
  
-   En tiempo de preparación o ejecución (cuando se llama a SQLExecute, SQLExecDirect, SQLSetPos o SQLBulkOperations).  
  
-   Cuando una aplicación fuerza una preparación no aplazada llamando a SQLPrepare con la preparación diferida deshabilitada o llamando a SQLNumResultCols, SQLDescribeCol o SQLDescribeParam para una instrucción preparada pero no ejecutada.  
  
 Cuando SQL_CA_SS_SERVER_TYPE se establece mediante una llamada a SQLSetDescField, su valor debe ser SQL_SS_TYPE_DEFAULT, SQL_SS_TYPE_SMALLDATETIME o SQL_SS_TYPE_DATETIME. En caso contrario, se devuelve SQL_ERROR y se registra un error de diagnóstico con SQLState HY092 y el mensaje "Identificador de opción o atributo o no válido".  
  
 El atributo SQL_CA_SS_SERVER_TYPE pueden utilizarlo las aplicaciones que dependen de la funcionalidad compatible con `datetime` y `smalldatetime`, pero no con `datetime2`. Por ejemplo, `datetime2` requiere el uso de las `dateadd` funciones y **datediif** , mientras que `datetime` y `smalldatetime` también permiten operadores aritméticos. La mayoría de las aplicaciones no necesitarán usar este atributo, y debe evitarse su uso.  
  
## <a name="information-returned-in-ird-fields"></a>Información que se devuelve en los campos IRD  
 La siguiente información se devuelve en los campos IRD:  
  
|Tipo de columna|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|-----------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CONCISE_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_CODE_DATE|0|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|0|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|10|8, 10.. 16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_DISPLAY_SIZE|10|8, 10.. 16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_LENGTH|10|8, 10.. 16|16|2|19, 21..27|26, 28..34|  
|SQL_DESC_LITERAL_PREFIX|'|'|'|'|'|'|  
|SQL_DESC_LITERAL_SUFFIX|'|'|'|'|'|'|  
|SQL_DESC_LOCAL_TYPE_NAME|`date`|`time`|`smalldatetime`|`datetime`|`datetime2`|datetimeoffset|  
|SQL_DESC_OCTET_LENGTH|6|12|4|8|16|20|  
|SQL_DESC_PRECISION|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SCALE|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|  
|SQL_DESC_TYPE|SQL_DATETIME|SQL_SS_TIME2|SQL_DATETIME|SQL_DATETIME|SQL_DATETIME|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_TYPE_NAME|`date`|`time`|`smalldatetime`|`datetime`|`datetime2`|datetimeoffset|  
|SQL_DESC_UNSIGNED|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|  
  
## <a name="see-also"></a>Consulte también  
 [Metadatos &#40;&#41;ODBC](../../database-engine/dev-guide/metadata-odbc.md)  
  
  
