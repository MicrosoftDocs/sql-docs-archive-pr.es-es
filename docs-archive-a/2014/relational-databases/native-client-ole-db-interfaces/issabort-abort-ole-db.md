---
title: ISSAbort::Abort (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAbort::Abort (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Abort method
ms.assetid: a5bca169-694b-4895-84ac-e8fba491e479
author: rothja
ms.author: jroth
ms.openlocfilehash: 3daad53087c876af8dc46bccc9c4bf7952976067
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746985"
---
# <a name="issabortabort-ole-db"></a>ISSAbort::Abort (OLE DB)
  Cancela el conjunto de filas actual y los comandos en lotes asociados al comando actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
HRESULT Abort(void);  
```  
  
## <a name="remarks"></a>Observaciones  
 Si el comando que se anula se encuentra en un procedimiento almacenado, terminará la ejecución del procedimiento almacenado (y cualquier procedimiento que haya llamado a este procedimiento) así como del lote de comandos que contiene la llamada al procedimiento almacenado. Si el servidor está en proceso de transferir un conjunto de resultados al cliente, se detendrá. Si el cliente no desea consumir un conjunto de resultados, la llamada a **ISSAbort::Abort** antes de liberar el conjunto de filas acelerará la liberación del conjunto de filas, pero si hay una transacción abierta y XACT_ABORT está establecido en ON, la transacción se revertirá al llamar a **ISSAbort::Abort** .  
  
 Después de que **ISSAbort::Abort** devuelva S_OK, la interfaz **IMultipleResults** asociada inicia un estado inutilizable y devuelve DB_E_CANCELED a todas las llamadas a método (excepto en los métodos que define la interfaz **IUNKNOWN** ) hasta que se libera. Si se ha obtenido una interfaz **IRowset** de **IMultipleResults** antes de una llamada a **Anular**, también inicia un estado inutilizable y devuelve DB_E_CANCELED a todas las llamadas a método (excepto en los métodos que define la interfaz **IUNKNOWN** e **IRowset::ReleaseRows**) hasta que se libera después de una llamada correcta a **ISSAbort::Abort**.  
  
> [!NOTE]  
>  A partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], si el estado de servidor XACT_ABORT está establecido en ON, la ejecución de **ISSAbort::Abort** finalizará y revertirá cualquier transacción implícita o explícita actual al conectarse a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Las versiones anteriores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no anularán la transacción actual.  
  
## <a name="arguments"></a>Argumentos  
 Ninguno.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 S_OK  
 El método **ISSAbort::Abort** devuelve S_OK si el lote se ha cancelado y DB_E_CANTCANCEL de lo contrario. Si el lote ya se había cancelado, se devuelve DB_E_CANCELED.  
  
 DB_E_CANCELED  
 El lote ya se ha cancelado.  
  
 DB_E_CANTCANCEL  
 El lote no se ha cancelado.  
  
 E_FAIL  
 Se produjo un error específico del proveedor. para obtener información detallada, use la interfaz [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) .  
  
 E_UNEXPECTED  
 No se esperaba la llamada al método. Por ejemplo, el objeto está en un estado zombi porque ya se ha llamado a **ISSAbort::Abort** .  
  
 E_OUTOFMEMORY  
 Error de memoria insuficiente.  
  
## <a name="see-also"></a>Consulte también  
 [ISSAbort &#40;OLE DB&#41;](../../database-engine/dev-guide/issabort-ole-db.md)  
  
  
