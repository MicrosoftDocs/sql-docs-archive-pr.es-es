---
title: Duración de las transacciones | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- lifetimes [SQL Server]
- Transact-SQL vs. managed code
ms.assetid: cb076fda-6488-4959-a6a4-7adaccf3f25c
author: rothja
ms.author: jroth
ms.openlocfilehash: 8c00050ee323cade7493d44c4c296ba4ce6811e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751193"
---
# <a name="transaction-lifetimes"></a>Período de duración de las transacciones
  Hay una diferencia importante entre las transacciones iniciadas en procedimientos almacenados [!INCLUDE[tsql](../../includes/tsql-md.md)] y las iniciadas en código administrado: el código de Common Language Runtime (CLR) no puede desequilibrar el estado de la transacción al entrar o salir de una invocación CLR. Tenga en cuenta las implicaciones siguientes de esta diferencia:  
  
-   Una transacción iniciada dentro de un marco CLR se debe confirmar o revertir; de otro modo, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] genera un error cuando se sale del marco.  
  
-   Una transacción exterior no se puede confirmar o revertir dentro del código CLR.  
  
-   Un intento para confirmar una transacción no iniciada en el mismo procedimiento produce un error en tiempo de ejecución.  
  
-   Un intento de revertir una transacción no iniciada en el mismo procedimiento hace que la transacción deje de responder (lo que impide que se produzca cualquier otra operación con efectos secundarios). La transacción se interrumpe hasta que el código CLR se sale del ámbito. Tenga en cuenta que esto puede resultar útil cuando detecta un error dentro de su procedimiento y desea asegurarse de que toda la transacción finaliza.  
  
## <a name="see-also"></a>Consulte también  
 [Integración CLR y transacciones](../native-client-ole-db-transactions/transactions.md)  
  
  
