---
title: Desplazamiento y captura de filas | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- SQLFetchScroll function
- ODBC applications, cursors
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- fetching [ODBC]
- ODBC cursors, scrolling rows
ms.assetid: 9109f10d-326b-4a6d-8c97-831f60da8c4c
author: rothja
ms.author: jroth
ms.openlocfilehash: 97586f82ddddb79581b0f9c027aa60d7822b472c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87749296"
---
# <a name="scrolling-and-fetching-rows"></a>Desplazamiento y captura de filas
  Para utilizar un cursor desplazable, una aplicación ODBC debe:  
  
-   Establezca las capacidades del cursor mediante [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md).  
  
-   Abra el cursor con **SQLExecute** o **SQLExecDirect**.  
  
-   Desplazamiento y captura de filas con **SQLFetch** o [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md).  
  
 **SQLFetch** y **SQLFetchSroll** pueden capturar bloques de filas a la vez. El número de filas devueltas se especifica mediante **SQLSetStmtAttr** para establecer el parámetro SQL_ATTR_ROW_ARRAY_SIZE.  
  
 Las aplicaciones ODBC pueden usar **SQLFetch** para obtener un cursor de solo avance.  
  
 **SQLFetchScroll** se utiliza para desplazarse alrededor de un cursor. **SQLFetchScroll** admite la captura de los conjuntos de filas siguiente, anterior, primero y último, además de la captura relativa (capturar el conjunto de filas *n* filas desde el inicio del conjunto de filas actual) y la captura absoluta (capturar el conjunto de filas a partir de la fila *n*). Si *n* es negativo en una captura absoluta, las filas se cuentan desde el final del conjunto de resultados. Una captura absoluta de la fila -1 significa que se capturará el conjunto de filas que empieza con la última fila del conjunto de resultados.  
  
 Las aplicaciones que usan **SQLFetchScroll** solo para sus capacidades de cursor de bloque, como los informes, es probable que pasen por el conjunto de resultados una sola vez, usando solo la opción para capturar el siguiente conjunto de filas. Por otro lado, las aplicaciones basadas en pantalla pueden aprovechar todas las funcionalidades de **SQLFetchScroll**. Si la aplicación establece el tamaño del conjunto de filas en el número de filas que se muestra en la pantalla y enlaza los búferes de pantalla al conjunto de resultados, puede traducir las operaciones de la barra de desplazamiento directamente a las llamadas a **SQLFetchScroll**.  
  
|Funcionamiento de la barra de desplazamiento|Opción de desplazamiento de SQLFetchScroll|  
|--------------------------|-------------------------------------|  
|Re Pág|SQL_FETCH_PRIOR|  
|Av Pág|SQL_FETCH_NEXT|  
|Línea arriba|SQL_FETCH_RELATIVE con FetchOffset igual a-1|  
|Línea abajo|SQL_FETCH_RELATIVE con FetchOffset igual a 1|  
|Cuadro de desplazamiento hacia arriba|SQL_FETCH_FIRST|  
|Cuadro de desplazamiento hacia abajo|SQL_FETCH_LAST|  
|Posición del cuadro de desplazamiento aleatoria|SQL_FETCH_ABSOLUTE|  
  
## <a name="in-this-section"></a>En esta sección  
  
-   [Marcar filas en ODBC](scrolling-and-fetching-rows-bookmarking-rows-in-odbc.md)  
  
## <a name="see-also"></a>Consulte también  
 [Usar cursores &#40;&#41;ODBC](using-cursors-odbc.md)  
  
  
