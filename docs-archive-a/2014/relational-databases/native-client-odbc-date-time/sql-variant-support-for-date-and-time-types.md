---
title: Compatibilidad sql_variant con tipos de fecha y hora | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- sql_variant data type
ms.assetid: 12ff1ea6-e2cc-40e6-910c-3126974a90b3
author: rothja
ms.author: jroth
ms.openlocfilehash: 0818f0ccee72264ea7cab69b90e18418179031ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748774"
---
# <a name="sql_variant-support-for-date-and-time-types"></a>Compatibilidad con sql_variant para tipos de fecha y hora
  En este tema se describe la forma en que el tipo de datos `sql_variant` admite una funcionalidad de fecha y hora mejorada.  
  
 El atributo de columna SQL_CA_SS_VARIANT_TYPE se usa para devolver el tipo C de una columna de resultados variant. [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] introduce un atributo adicional, SQL_CA_SS_VARIANT_SQL_TYPE, que establece el tipo SQL de una columna de resultados variant en el descriptor de filas de implementación (IRD). SQL_CA_SS_VARIANT_SQL_TYPE también puede usarse en el descriptor de parámetros de implementación (IPD) para especificar el tipo SQL de un parámetro SQL_SS_TIME2 o SQL_SS_TIMESTAMPOFFSET que tiene un tipo SQL_C_BINARY de C enlazado al tipo SQL_SS_VARIANT.  
  
 Los nuevos tipos SQL_SS_TIME2 y SQL_SS_TIMESTAMPOFFSET pueden establecerse mediante SQLColAttribute. SQLGetDescField puede devolver SQL_CA_SS_VARIANT_SQL_TYPE.  
  
 Para las columnas de resultados, el controlador convertirá el tipo variant en un tipo de fecha y hora. Para obtener más información, vea [conversiones de SQL a C](datetime-data-type-conversions-from-sql-to-c.md). Al enlazar a SQL_C_BINARY, la longitud del búfer debe ser lo suficientemente grande como para recibir el struct correspondiente al tipo SQL.  
  
 Para los parámetros SQL_SS_TIME2 y SQL_SS_TIMESTAMPOFFSET, el controlador convertirá los valores de C en valores `sql_variant`, tal y como describe a continuación en la tabla. Si un parámetro se enlaza como SQL_C_BINARY y el tipo de servidor es SQL_SS_VARIANT, se considerará como un valor binario a menos que la aplicación haya establecido SQL_CA_SS_VARIANT_SQL_TYPE en un otro tipo SQL. En este caso, SQL_CA_SS_VARIANT_SQL_TYPE tiene prioridad; es decir, si se establece SQL_CA_SS_VARIANT_SQL_TYPE, invalida el comportamiento predeterminado de deducir el tipo variant de SQL a partir del tipo de C.  
  
|Tipo de C|Tipo de servidor|Comentarios|  
|------------|-----------------|--------------|  
|SQL_C_CHAR|varchar|Se omite SQL_CA_SS_VARIANT_SQL_TYPE.|  
|SQL_C_WCHAR|nvarcar|Se omite SQL_CA_SS_VARIANT_SQL_TYPE.|  
|SQL_C_TINYINT|SMALLINT|Se omite SQL_CA_SS_VARIANT_SQL_TYPE.|  
|SQL_C_STINYINT|SMALLINT|Se omite SQL_CA_SS_VARIANT_SQL_TYPE.|  
|SQL_C_SHORT|SMALLINT|Se omite SQL_CA_SS_VARIANT_SQL_TYPE.|  
|SQL_C_SSHORT|SMALLINT|Se omite SQL_CA_SS_VARIANT_SQL_TYPE.|  
|SQL_C_USHORT|int|Se omite SQL_CA_SS_VARIANT_SQL_TYPE.|  
|SQL_C_LONG|int|Se omite SQL_CA_SS_VARIANT_SQL_TYPE.|  
|SQL_C_SLONG|int|Se omite SQL_CA_SS_VARIANT_SQL_TYPE.|  
|SQL_C_ULONG|bigint|Se omite SQL_CA_SS_VARIANT_SQL_TYPE.|  
|SQL_C_SBIGINT|bigint|Se omite SQL_CA_SS_VARIANT_SQL_TYPE.|  
|SQL_C_FLOAT|real|Se omite SQL_CA_SS_VARIANT_SQL_TYPE.|  
|SQL_C_DOUBLE|FLOAT|Se omite SQL_CA_SS_VARIANT_SQL_TYPE.|  
|SQL_C_BIT|bit|Se omite SQL_CA_SS_VARIANT_SQL_TYPE.|  
|SQL_C_UTINYINT|TINYINT|Se omite SQL_CA_SS_VARIANT_SQL_TYPE.|  
|SQL_C_BINARY|varbinary|No se establece SQL_CA_SS_VARIANT_SQL_TYPE.|  
|SQL_C_BINARY|time|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIME2<br /><br /> Scale se establece en SQL_DESC_PRECISION (el parámetro *ColumnSize* de `SQLBindParameter` ).|  
|SQL_C_BINARY|datetimeoffset|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIMESTAMPOFFSET<br /><br /> Scale se establece en SQL_DESC_PRECISION (el parámetro *ColumnSize* de `SQLBindParameter` ).|  
|SQL_C_TYPE_DATE|date|Se omite SQL_CA_SS_VARIANT_SQL_TYPE.|  
|SQL_C_TYPE_TIME|time(0)|Se omite SQL_CA_SS_VARIANT_SQL_TYPE.|  
|SQL_C_TYPE_TIMESTAMP|datetime2|Scale se establece en SQL_DESC_PRECISION (el parámetro *ColumnSize* de `SQLBindParameter` ).|  
|SQL_C_NUMERIC|Decimal|La precisión se establece en SQL_DESC_PRECISION (el parámetro *columnas* de `SQLBindParameter` ).<br /><br /> Conjunto de escalado a SQL_DESC_SCALE (el parámetro *ColumnSize* de SQLBindParameter).|  
|SQL_C_SS_TIME2|time|Se ignora SQL_CA_SS_VARIANT_SQL_TYPE.|  
|SQL_C_SS_TIMESTAMPOFFSET|datetimeoffset|Se ignora SQL_CA_SS_VARIANT_SQL_TYPE.|  
  
## <a name="see-also"></a>Consulte también  
 [Mejoras de fecha y hora &#40;ODBC&#41;](date-and-time-improvements-odbc.md)  
  
  
