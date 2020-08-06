---
title: Liberar un identificador de instrucción | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- reusing statement handles
- freeing statement handles
- statements [ODBC], statement handles
- SQLFreeStmt function
- ODBC applications, statements
- statement handles [ODBC]
ms.assetid: 96fdff84-0ca7-460a-a240-94ee826ea41c
author: rothja
ms.author: jroth
ms.openlocfilehash: 8d7a1e93d222e2b87058bc878f7eca85313b4108
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662866"
---
# <a name="freeing-a-statement-handle"></a>Liberar un identificador de instrucción
  Es más eficaz volver a utilizar los identificadores de instrucciones que quitarlos y asignar unos nuevos. Antes de ejecutar una nueva instrucción SQL en un identificador de instrucciones, las aplicaciones deberían comprobar que la configuración de instrucción actual es correcta. Éstos incluyen atributos de instrucción, enlaces de parámetros y enlaces de conjunto de resultados. Por lo general, los parámetros y conjuntos de resultados de la instrucción SQL anterior deben estar desenlazados mediante una llamada a [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) con las opciones SQL_RESET_PARAMS y SQL_UNBIND y, después, volver a enlazarse a la nueva instrucción SQL.  
  
 Cuando la aplicación ha terminado de usar la instrucción, llama a [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) para liberar la instrucción. Tenga en cuenta que **SQLDisconnect** libera automáticamente todas las instrucciones de una conexión.  
  
## <a name="see-also"></a>Consulte también  
 [Ejecutar consultas &#40;&#41;ODBC](executing-queries-odbc.md)  
  
  
