---
title: Compatibilidad con transacciones locales | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- autocommit mode
- transactions [OLE DB]
- ITransactionLocal interface
- SQL Server Native Client OLE DB provider, transactions
- local transactions [OLE DB]
ms.assetid: 78f2e5fc-b6fb-4eda-9f71-991a4d6c4902
author: rothja
ms.author: jroth
ms.openlocfilehash: a9bc11a038e56517aa42619117c371c1319b9ffe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87675819"
---
# <a name="supporting-local-transactions"></a>Compatibilidad con transacciones locales
  Una sesión delimita el ámbito de la transacción para una [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transacción local del proveedor de OLE DB de Native Client. Cuando, en la dirección de un consumidor, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client envía una solicitud a una instancia conectada de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , la solicitud constituye una unidad de trabajo para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] el proveedor de OLE DB de Native Client. Las transacciones locales siempre encapsulan una o más unidades de trabajo en una sola [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sesión de proveedor de OLE DB de Native Client.  
  
 Mediante el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] modo de confirmación automática del proveedor de OLE DB de Native Client predeterminado, una unidad de trabajo única se trata como el ámbito de una transacción local. Solo una unidad participa en la transacción local. Cuando se crea una sesión, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client inicia una transacción para la sesión. Cuando se completa correctamente una unidad de trabajo, el trabajo se confirma. En caso de error, cualquier trabajo comenzado se revierte y el error se notifica al consumidor. En cualquier caso, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client inicia una nueva transacción local para la sesión de modo que todo el trabajo se lleve a cabo dentro de una transacción.  
  
 El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consumidor del proveedor de OLE DB de Native Client puede dirigir un control más preciso sobre el ámbito de la transacción local mediante la interfaz **ITransactionLocal** . Cuando una sesión del consumidor inicia una transacción, todas las unidades de trabajo de la sesión entre el punto de inicio de la transacción y las posibles llamadas a los métodos **Commit** o **Abort** se tratan como una unidad atómica. El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client inicia implícitamente una transacción cuando el consumidor la dirige. Si el consumidor no solicita la retención, la sesión vuelve al comportamiento de nivel de transacción primaria, la mayoría de las veces en modo de confirmación automática.  
  
 El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client admite los parámetros **ITransactionLocal:: StartTransaction** como se indica a continuación.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|*isoLevel*[in]|Nivel de aislamiento que se va a utilizar con esta transacción. En las transacciones locales, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client admite lo siguiente:<br /><br /> -ISOLATIONLEVEL_UNSPECIFIED<br />-ISOLATIONLEVEL_CHAOS<br />-ISOLATIONLEVEL_READUNCOMMITTED<br />-ISOLATIONLEVEL_READCOMMITTED<br />-ISOLATIONLEVEL_REPEATABLEREAD<br />-ISOLATIONLEVEL_CURSORSTABILITY<br />-ISOLATIONLEVEL_REPEATABLEREAD<br />-ISOLATIONLEVEL_SERIALIZABLE<br />-ISOLATIONLEVEL_ISOLATED<br />-ISOLATIONLEVEL_SNAPSHOT **Nota:** a partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , ISOLATIONLEVEL_SNAPSHOT es válido para el argumento *isolevel* si el control de versiones está habilitado o no para la base de datos. Sin embargo, se producirá un error si el usuario intenta ejecutar una instrucción y no está habilitado el control de versiones, o si la base de datos no es de solo lectura. Además, si se especifica ISOLATIONLEVEL_SNAPSHOT como el valor de *isoLevel* al conectarse a una versión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anterior a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], se producirá el error XACT_E_ISOLATIONLEVEL.|  
|*isoFlags*[in]|El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client devuelve un error para cualquier valor distinto de cero.|  
|*pOtherOptions*[in]|Si no es NULL, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client solicita el objeto de opciones de la interfaz. El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client devuelve XACT_E_NOTIMEOUT si el miembro *ulTimeout* del objeto de opciones no es cero. El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client omite el valor del miembro *szDescription* .|  
|*pulTransactionLevel*[out]|Si no es NULL, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client devuelve el nivel anidado de la transacción.|  
  
 Para las transacciones locales, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client implementa los parámetros **ITransaction:: ABORT** como se indica a continuación.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|*pboidReason*[in]|Se omite si está establecido. Puede ser sin ningún riesgo NULL.|  
|*fRetaining*[in]|Si es TRUE, se inicia una nueva transacción de forma implícita para la sesión. La transacción debe ser confirmada o finalizada por el consumidor. Cuando es FALSE, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client vuelve al modo de confirmación automática para la sesión.|  
|*fAsync*[in]|El proveedor de OLE DB de Native Client no admite la anulación asincrónica [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client devuelve XACT_E_NOTSUPPORTED si el valor no es false.|  
  
 Para las transacciones locales, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client implementa los parámetros **ITransaction:: commit** como se indica a continuación.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|*fRetaining*[in]|Si es TRUE, se inicia una nueva transacción de forma implícita para la sesión. La transacción debe ser confirmada o finalizada por el consumidor. Cuando es FALSE, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client vuelve al modo de confirmación automática para la sesión.|  
|*grfTC*[in]|El proveedor de OLE DB de Native Client no admite las devoluciones asincrónicas y de fase uno [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client devuelve XACT_E_NOTSUPPORTED para cualquier valor distinto de XACTTC_SYNC.|  
|*grfRM*[in]|Debe ser 0.|  
  
 Los [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conjuntos de filas de proveedor de OLE DB de Native Client en la sesión se conservan en una operación de confirmación o anulación local basada en los valores de las propiedades del conjunto de filas DBPROP_ABORTPRESERVE y DBPROP_COMMITPRESERVE. De forma predeterminada, estas propiedades son VARIANT_FALSE y todos los [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conjuntos de filas del proveedor de OLE DB de Native Client de la sesión se pierden después de una operación de anulación o confirmación.  
  
 El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client no implementa la interfaz **ITransactionObject** . Si el consumidor intenta recuperar una referencia en la interfaz, obtiene E_NOINTERFACE.  
  
 En este ejemplo, se usa **ITransactionLocal**.  
  
```  
// Interfaces used in the example.  
IDBCreateSession*   pIDBCreateSession   = NULL;  
ITransaction*       pITransaction       = NULL;  
IDBCreateCommand*   pIDBCreateCommand   = NULL;  
IRowset*            pIRowset            = NULL;  
  
HRESULT             hr;  
  
// Get the command creation and local transaction interfaces for the  
// session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
if (FAILED(hr = pIDBCreateCommand->QueryInterface(IID_ITransactionLocal,  
    (void**) &pITransaction)))  
    {  
    // Process error. Release any references and return.  
    }  
  
// Start the local transaction.  
if (FAILED(hr = ((ITransactionLocal*) pITransaction)->StartTransaction(  
    ISOLATIONLEVEL_REPEATABLEREAD, 0, NULL, NULL)))  
    {  
    // Process error from StartTransaction. Release any references and  
    // return.  
    }  
  
// Get data into a rowset, then update the data. Functions are not  
// illustrated in this example.  
if (FAILED(hr = ExecuteCommand(pIDBCreateCommand, &pIRowset)))  
    {  
    // Release any references and return.  
    }  
  
// If rowset data update fails, then terminate the transaction, else  
// commit. The example doesn't retain the rowset.  
if (FAILED(hr = UpdateDataInRowset(pIRowset, bDelayedUpdate)))  
    {  
    // Get error from update, then terminate.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, XACTTC_SYNC, 0)))  
        {  
        // Get error from failed commit.  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a>Consulte también  
 [Transactions](transactions.md)   
 [Trabajar con aislamiento de instantánea](../native-client/features/working-with-snapshot-isolation.md)  
  
  
