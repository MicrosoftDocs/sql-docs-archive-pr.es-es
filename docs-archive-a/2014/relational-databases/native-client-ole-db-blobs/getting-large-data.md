---
title: Obtención de datos grandes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- DBPROP_ACCESSORDER property
- SQL Server Native Client OLE DB provider, BLOBs
- large data, OLE objects
ms.assetid: a31c5632-96aa-483f-a307-004c5149fbc0
author: rothja
ms.author: jroth
ms.openlocfilehash: 38602df026d2e752a758672dde23a59a26ad4917
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750825"
---
# <a name="getting-large-data"></a><span data-ttu-id="06223-102">Obtener datos grandes</span><span class="sxs-lookup"><span data-stu-id="06223-102">Getting Large Data</span></span>
  <span data-ttu-id="06223-103">En general, los consumidores deben aislar el código que crea un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objeto de almacenamiento de proveedor OLE DB Native Client desde otro código que controle los datos a los que no se hace referencia a través de un puntero de interfaz **ISequentialStream** .</span><span class="sxs-lookup"><span data-stu-id="06223-103">In general, consumers should isolate code that creates a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider storage object from other code that handles data not referenced through an **ISequentialStream** interface pointer.</span></span>  
  
 <span data-ttu-id="06223-104">En este tema se hace referencia a la funcionalidad disponible con las funciones siguientes:</span><span class="sxs-lookup"><span data-stu-id="06223-104">This topic refers to functionality available with the following functions:</span></span>  
  
-   <span data-ttu-id="06223-105">IRowset:GetData</span><span class="sxs-lookup"><span data-stu-id="06223-105">IRowset:GetData</span></span>  
  
-   <span data-ttu-id="06223-106">IRow::GetColumns</span><span class="sxs-lookup"><span data-stu-id="06223-106">IRow::GetColumns</span></span>  
  
-   <span data-ttu-id="06223-107">ICommand::Execute</span><span class="sxs-lookup"><span data-stu-id="06223-107">ICommand::Execute</span></span>  
  
 <span data-ttu-id="06223-108">Si la propiedad DBPROP_ACCESSORDER (en el grupo de propiedades de conjunto de filas) está establecida en cualquiera de los valores DBPROPVAL_AO_SEQUENTIAL o DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS, el consumidor solo debe capturar una fila de datos en una llamada al método **GetNextRows** porque los datos de BLOB no se almacenan en búfer.</span><span class="sxs-lookup"><span data-stu-id="06223-108">If the DBPROP_ACCESSORDER property (in the rowset property group) is set to either of the values DBPROPVAL_AO_SEQUENTIAL or DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS, the consumer should fetch only a single row of data in a call to the **GetNextRows** method because BLOB data is not buffered.</span></span> <span data-ttu-id="06223-109">Si el valor de DBPROP_ACCESSORDER está establecido en DBPROPVAL_AO_RANDOM, el consumidor puede capturar varias filas de datos en **GetNextRows**.</span><span class="sxs-lookup"><span data-stu-id="06223-109">If the value of DBPROP_ACCESSORDER is set to DBPROPVAL_AO_RANDOM, the consumer can fetch multiple rows of data in **GetNextRows**.</span></span>  
  
 <span data-ttu-id="06223-110">El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client no recupera datos grandes desde [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hasta que el consumidor lo solicite.</span><span class="sxs-lookup"><span data-stu-id="06223-110">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not retrieve large data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] until requested to do so by the consumer.</span></span> <span data-ttu-id="06223-111">El consumidor debe enlazar todos los datos cortos en un descriptor de acceso y, a continuación, utilizar uno o más descriptores de acceso temporales para recuperar los valores de datos grandes según se precise.</span><span class="sxs-lookup"><span data-stu-id="06223-111">The consumer should bind all short data in one accessor, and then use one or more temporary accessors to retrieve large data values as required.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06223-112">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="06223-112">Example</span></span>  
 <span data-ttu-id="06223-113">En este ejemplo se recupera un valor de datos grandes de una única columna:</span><span class="sxs-lookup"><span data-stu-id="06223-113">This example retrieves a large data value from a single column:</span></span>  
  
```  
HRESULT GetUnboundData  
    (  
    IRowset* pIRowset,  
    HROW hRow,  
    ULONG nCol,   
    BYTE* pUnboundData  
    )  
    {  
    UINT                cbRow = sizeof(IUnknown*) + sizeof(ULONG);  
    BYTE*               pRow = new BYTE[cbRow];  
  
    DBOBJECT            dbobject;  
  
    IAccessor*          pIAccessor = NULL;  
    HACCESSOR           haccessor;  
  
    DBBINDING           dbbinding;  
    ULONG               ulbindstatus;  
  
    ULONG               dwStatus;  
    ISequentialStream*  pISequentialStream;  
    ULONG               cbRead;  
  
    HRESULT             hr;  
  
    // Set up the DBOBJECT structure.  
    dbobject.dwFlags = STGM_READ;  
    dbobject.iid = IID_ISequentialStream;  
  
    // Create the DBBINDING, requesting a storage-object pointer from  
    // The SQL Server Native Client OLE DB provider.  
    dbbinding.iOrdinal = nCol;  
    dbbinding.obValue = 0;  
    dbbinding.obStatus = sizeof(IUnknown*);  
    dbbinding.obLength = 0;  
    dbbinding.pTypeInfo = NULL;  
    dbbinding.pObject = &dbobject;  
    dbbinding.pBindExt = NULL;  
    dbbinding.dwPart = DBPART_VALUE | DBPART_STATUS;  
    dbbinding.dwMemOwner = DBMEMOWNER_CLIENTOWNED;  
    dbbinding.eParamIO = DBPARAMIO_NOTPARAM;  
    dbbinding.cbMaxLen = 0;  
    dbbinding.dwFlags = 0;  
    dbbinding.wType = DBTYPE_IUNKNOWN;  
    dbbinding.bPrecision = 0;  
    dbbinding.bScale = 0;  
  
    if (FAILED(hr = pIRowset->  
        QueryInterface(IID_IAccessor, (void**) &pIAccessor)))  
        {  
        // Process QueryInterface failure.  
        return (hr);  
        }  
  
    // Create the accessor.  
    if (FAILED(hr = pIAccessor->CreateAccessor(DBACCESSOR_ROWDATA, 1,  
        &dbbinding, 0, &haccessor, &ulbindstatus)))  
        {  
        // Process error from CreateAccessor.  
        pIAccessor->Release();  
        return (hr);  
        }  
  
    // Read and process BLOCK_SIZE bytes at a time.  
    if (SUCCEEDED(hr = pIRowset->GetData(hRow, haccessor, pRow)))  
        {  
        dwStatus = *((ULONG*) (pRow + dbbinding.obStatus));  
  
        if (dwStatus == DBSTATUS_S_ISNULL)  
            {  
            // Process NULL data  
            }  
        else if (dwStatus == DBSTATUS_S_OK)  
            {  
            pISequentialStream = *((ISequentialStream**)   
                (pRow + dbbinding.obValue));  
  
            do  
                {  
                if (SUCCEEDED(hr =  
                    pISequentialStream->Read(pUnboundData,  
                    BLOCK_SIZE, &cbRead)))  
                    {  
                    pUnboundData += cbRead;  
                    }  
                }  
            while (SUCCEEDED(hr) && cbRead >= BLOCK_SIZE);  
  
            pISequentialStream->Release();  
            }  
        }  
    else  
        {  
        // Process error from GetData.  
        }  
  
    pIAccessor->ReleaseAccessor(haccessor, NULL);  
    pIAccessor->Release();  
    delete [] pRow;  
  
    return (hr);  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="06223-114">Consulte también</span><span class="sxs-lookup"><span data-stu-id="06223-114">See Also</span></span>  
 <span data-ttu-id="06223-115">[Blobs y objetos OLE](blobs-and-ole-objects.md) </span><span class="sxs-lookup"><span data-stu-id="06223-115">[BLOBs and OLE Objects](blobs-and-ole-objects.md) </span></span>  
 [<span data-ttu-id="06223-116">Usar tipos de valor grande</span><span class="sxs-lookup"><span data-stu-id="06223-116">Using Large Value Types</span></span>](../native-client/features/using-large-value-types.md)  
  
  
