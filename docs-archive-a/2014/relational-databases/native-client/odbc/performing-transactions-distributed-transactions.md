---
title: Realización de transacciones distribuidas | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MS DTC, performing distributed transactions
- SQL Server Native Client ODBC driver, transactions
- distributed transactions [ODBC]
- transactions [ODBC]
- ODBC, transactions
ms.assetid: 2c17fba0-7a3c-453c-91b7-f801e7b39ccb
author: rothja
ms.author: jroth
ms.openlocfilehash: 9ec23fd1883749e35e67f888e26bdf031ccf7fb8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87670350"
---
# <a name="performing-distributed-transactions"></a>Realizar transacciones distribuidas
  Microsoft DTC (Coordinador de transacciones distribuidas) permite que las aplicaciones puedan extender las transacciones en dos o más instancias de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. También permite que las aplicaciones participen en transacciones administradas por administradores de transacciones que obedecen al estándar Open Group DTP XA.  
  
 Normalmente, todos los comandos de administración de transacción se envían a través del controlador ODBC de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client al servidor. La aplicación inicia una transacción mediante una llamada a [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) con el modo de confirmación automática desactivado. A continuación, la aplicación realiza las actualizaciones que componen la transacción y llama a [SQLEndTran](../../native-client-odbc-api/sqlendtran.md) con la opción SQL_COMMIT o SQL_ROLLBACK.  
  
 Sin embargo, cuando se utiliza MS DTC, MS DTC se convierte en el administrador de transacciones y la aplicación ya no usa **SQLEndTran**.  
  
 Cuando se da de alta en una transacción distribuida y después en una segunda transacción distribuida, el controlador ODBC de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client se da de baja de la transacción distribuida original y se da de alta en la transacción nueva. Para obtener más información, vea [Referencia del programador de DTC](https://msdn.microsoft.com/library/ms686108\(VS.85\).aspx).  
  
## <a name="see-also"></a>Consulte también  
 [Realizar transacciones &#40;&#41;ODBC](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
