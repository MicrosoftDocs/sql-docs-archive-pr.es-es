---
title: Asignación de un identificador de entorno | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, environment handles
- ODBC applications, connections
- handles [SQL Server Native Client]
- environment handles [SQLNCLI]
ms.assetid: 15c1b428-ea6d-4672-894c-f0e289e2da3f
author: rothja
ms.author: jroth
ms.openlocfilehash: 1c655b5e9a406c3e1881c9dd199a92666377918f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674097"
---
# <a name="allocating-an-environment-handle"></a>Asignar un identificador de entorno
  Para que una aplicación pueda llamar a cualquier función ODBC, debe inicializar el entorno ODBC y asignar un identificador de entorno. Se trata del identificador de contexto global y marcador de posición del resto de los identificadores de ODBC. Para ello, debe llamar a **SQLAllocHandle** con el parámetro *HandleType* establecido en SQL_HANDLE_ENV y *InputHandle* establecido en SQL_NULL_HANDLE.  
  
 Después de asignar el identificador de entorno, la aplicación debe establecer atributos de entorno para indicar qué versión de las llamadas a funciones de ODBC va a utilizar. Para usar ODBC 3. funciones *x* , llame a [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) con el parámetro de *atributo* establecido en SQL_ATTR_ODBC_VERSION y *ValuePtr* establecido en SQL_OV_ODBC3.  
  
## <a name="see-also"></a>Consulte también  
 [Comunicarse con SQL Server &#40;ODBC&#41;](communicating-with-sql-server-odbc.md)  
  
  
