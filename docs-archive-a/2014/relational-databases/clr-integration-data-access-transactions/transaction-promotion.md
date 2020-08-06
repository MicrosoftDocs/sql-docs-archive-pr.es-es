---
title: Promoción de transacciones | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- distributed transactions [CLR integration]
- promoting transactions [CLR integration]
- Enlist keyword
- transaction promotion [CLR integration]
ms.assetid: 5bc7e26e-28ad-4198-a40d-8b2c648ba304
author: rothja
ms.author: jroth
ms.openlocfilehash: e78cbb3d2fc888e56c0b55780daf7b449fe6dc40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751186"
---
# <a name="transaction-promotion"></a>Promoción de transacciones
  La *promoción* de transacciones describe transacciones ligeras, locales que se pueden promover automáticamente a transacciones totalmente distribuibles, según sea necesario. Cuando se invoca un procedimiento almacenado administrado en una transacción de base de datos del servidor, se ejecuta el código de Common Language Runtime (CLR) en el contexto de una transacción local.  Si se abre una conexión a un servidor remoto en una transacción de base de datos, la conexión al servidor remoto se da de alta en la transacción distribuida y la transacción local se promueve automáticamente a una transacción distribuida. Por lo tanto, la promoción de transacciones minimiza la sobrecarga de las transacciones distribuidas difiriendo la creación de transacciones distribuidas hasta que se necesiten. La promoción de transacciones es automática, si se ha habilitado utilizando la palabra clave `Enlist` y no requiere la intervención del programador. El proveedor de datos de .NET Framework para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proporciona compatibilidad con la promoción de transacciones, administrada a través de las clases del espacio de nombres `System.Data.SqlClient` de .NET Framework.  
  
## <a name="the-enlist-keyword"></a>La palabra clave Enlist  
 La propiedad `ConnectionString` de un objeto `SqlConnection` admite la palabra clave `Enlist`, que indica si `System.Data.SqlClient` detecta los contextos transaccionales y da de alta automáticamente la conexión en una transacción distribuida. Si esta palabra clave está establecida en true (el valor predeterminado), la conexión se da de alta automáticamente en el contexto de transacción actual del subproceso de apertura. Si esta palabra clave está establecida en false, la conexión SqlClient no interactúa con una transacción distribuida. Si no se especifica `Enlist` en la cadena de conexión, la conexión se da de alta automáticamente en una transacción distribuida si se detecta una en el momento en que se abre la conexión.  
  
## <a name="distributed-transactions"></a>Transacciones distribuidas  
 Las transacciones distribuidas consumen normalmente recursos del sistema significativos. [!INCLUDE[msCoName](../../includes/msconame-md.md)] DTC (Coordinador de transacciones distribuidas) administra tales transacciones e integra todos los administradores de recursos a los que se obtiene acceso en estas transacciones. La promoción de transacciones, por otro lado, es una forma especial de una transacción `System.Transactions` que delega eficazmente el trabajo a una transacción [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] simple. `System.Transactions`, `System.Data.SqlClient` y [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] coordinan el trabajo relacionado con la administración de la transacción, promoviéndola a una transacción distribuida completa, según sea necesario.  
  
 La ventaja de utilizar la promoción de transacciones es que cuando se abre una conexión con una transacción `TransactionScope` activa y no hay abierta ninguna otra conexión, se confirma la transacción como una transacción ligera, en lugar de incurrir en la sobrecarga adicional de una transacción completa distribuida. Para obtener más información sobre `TransactionScope` , vea [usar System. Transactions](../native-client-ole-db-transactions/transactions.md).  
  
## <a name="see-also"></a>Consulte también  
 [Integración CLR y transacciones](clr-integration-and-transactions.md)  
  
  
