---
title: Metadatos de parámetros con valores de tabla para instrucciones preparadas | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), metadata for prepared statements
ms.assetid: fd2fc705-2e98-4011-9822-c7e6cca4a535
author: rothja
ms.author: jroth
ms.openlocfilehash: ad1394bd5e5bedc69a98308ba67a98434559c146
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750842"
---
# <a name="table-valued-parameter-metadata-for-prepared-statements"></a>Metadatos de parámetros con valores de tabla para instrucciones preparadas
  Una aplicación puede obtener metadatos para una llamada a procedimiento preparada a través de SQLNumParams y SQLDescribeParam. En el caso de los parámetros con valores de tabla, *DataTypePtr* se establece en SQL_SS_TABLE. Los metadatos adicionales están disponibles a través de SQLGetDescField para SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME y SQL_CA_SS_SCHEMA_NAME.  
  
 SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME y SQL_CA_SS_SCHEMA_NAME se pueden usar con SQLColumns para obtener los metadatos de columna para los tipos de tabla asociados a los parámetros con valores de tabla. En este caso, SQL_SOPT_SS_NAME_SCOPE debe establecerse en SQL_SS_NAME_SCOPE_TABLE_TYPE antes de que se llame a SQLColumns. A continuación, SQL_SOPT_SS_NAME_SCOPE se debe volver a establecer en el valor predeterminado, SQL_SS_NAME_SCOPE_TABLE, cuando la aplicación haya terminado de recuperar los metadatos de columnas de parámetros con valores de tabla.  
  
 SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME y SQL_CA_SS_SCHEMA_NAME se pueden usar también con parámetros de tipos definidos por el usuario de CLR.  
  
 No puede obtener metadatos de parámetros con valores de tabla para instrucciones preparadas que no sean llamadas a procedimientos almacenados. Si lo intenta, la aplicación devuelve SQL_ERROR con SQLSTATE 42000 y el mensaje "error de sintaxis o infracción de acceso".  
  
## <a name="see-also"></a>Consulte también  
 [Parámetros con valores de tabla &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  
