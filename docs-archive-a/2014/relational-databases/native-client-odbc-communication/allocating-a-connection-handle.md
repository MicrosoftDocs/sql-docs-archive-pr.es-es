---
title: Asignando un identificador de conexión | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, passwords
- ODBC applications, connections
- handles [SQL Server Native Client]
- expiration [SQL Server Native Client]
- passwords [SQL Server], modifying
- SQL Server Native Client ODBC driver, connection handles
- connection handles [SQL Server Native Client]
- modifying passwords
- SQLAllocHandle function
ms.assetid: 471d8a31-199c-4f92-bb10-004fc7733b35
author: rothja
ms.author: jroth
ms.openlocfilehash: d3cf84e541f114d527d9a00cd19bce705a09af30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750933"
---
# <a name="allocating-a-connection-handle"></a>Asignar un identificador de conexión
  Antes de que la aplicación se pueda conectar a un origen de datos o controlador, debe asignar un identificador de conexión. Esto se hace llamando a **SQLAllocHandle** con el parámetro *HandleType* establecido en SQL_HANDLE_DBC y *InputHandle* que apunta a un identificador de entorno inicializado.  
  
 Las características de la conexión se controlan estableciendo los atributos de conexión. Por ejemplo, dado que las transacciones se producen en el nivel de conexión, el nivel de aislamiento de transacción es un atributo de conexión. De igual forma, el tiempo de espera del inicio de sesión, o número de segundos que se espera mientras se intenta conectar antes de agotar el tiempo, es un atributo de conexión.  
  
 Los atributos de conexión se establecen con [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)y su configuración actual se recupera con [SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md). Si se llama a **SQLSetConnectAttr** antes de que se intente una conexión, el administrador de controladores ODBC almacena los atributos en su estructura de conexión y los establece en el controlador como parte del proceso de conexión. Algunos atributos de conexión se deben establecer antes de la aplicación intente conectar; otros se pueden establecer después de que la conexión se haya completado. Por ejemplo, SQL_ATTR_ODBC_CURSORS se debe establecer antes de que se realice una conexión, pero SQL_ATTR_AUTOCOMMIT se puede establecer después de conectar.  
  
 En ocasiones, las aplicaciones que se ejecutan en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versión 7.0 o versiones posteriores pueden mejorar su rendimiento si restablecen el tamaño de paquete de red del flujo TDS. El tamaño de paquete predeterminado se establece en el servidor, en 4 KB. Un tamaño de paquete entre 4 y 8 KB generalmente proporciona el máximo rendimiento. Si las pruebas muestran que el rendimiento es mejor con un tamaño de paquete diferente, la aplicación puede restablecer el tamaño de paquete. Las aplicaciones ODBC pueden hacerlo antes de la conexión mediante una llamada a **SQLSetConnectAttr** con la opción SQL_ATTR_PACKET_SIZE. Algunas aplicaciones presentan un mejor rendimiento con un tamaño de paquete mayor, pero las mejoras de rendimiento suelen ser mínimas en tamaños de paquete mayores que 8 KB.  
  
 El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] controlador ODBC de Native Client tiene una serie de atributos de conexión extendidos que una aplicación puede utilizar para aumentar su funcionalidad. Algunos de estos atributos controlan las mismas opciones que se pueden especificar en orígenes de datos y se utilizan para invalidar las opciones establecidas en un origen de datos. Por ejemplo, si una aplicación utiliza identificadores entrecomillados, puede establecer el atributo SQL_COPT_SS_QUOTED_IDENT específico de controlador en SQL_QI_ON para asegurarse de que esta opción siempre se establece sin tener en cuenta el valor en cualquier origen de datos.  
  
## <a name="see-also"></a>Consulte también  
 [Comunicarse con SQL Server &#40;ODBC&#41;](communicating-with-sql-server-odbc.md)  
  
  
