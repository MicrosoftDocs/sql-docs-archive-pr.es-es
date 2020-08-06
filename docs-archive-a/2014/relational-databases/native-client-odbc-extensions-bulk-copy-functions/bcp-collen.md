---
title: bcp_collen | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_collen
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_collen function
ms.assetid: faaf1f7a-81f2-4852-a178-56602c33673a
author: rothja
ms.author: jroth
ms.openlocfilehash: 3099e26b0c2cd0d1cfee7578f5b149b812f01765
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750906"
---
# <a name="bcp_collen"></a>bcp_collen
  Establece la longitud de los datos de la variable del programa para la copia masiva actual en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
RETCODE bcp_collen (  
HDBC   
hdbc  
,  
DBINT   
cbData  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a>Argumentos  
 *hdbc*  
 Es el identificador de la conexión ODBC habilitada para la copia masiva.  
  
 *cbData*  
 Es la longitud de los datos de la variable del programa; no incluye la longitud del indicador ni del terminador de longitud. Si se establece *cbData* en SQL_NULL_DATA, se indica que todas las filas copiadas en el servidor contienen un valor NULL para la columna. Si se establece en SQL_VARLEN_DATA, se indica que se utiliza un terminador de cadena u otro método para determinar la longitud de los datos copiados. Si hay un indicador y un terminador de longitud, el sistema utiliza el que permita que se copien menos datos.  
  
 *idxServerCol*  
 Es la posición ordinal de la columna en la tabla en la que se copian los datos. La primera columna es 1. La posición ordinal de una columna se notifica mediante [SQLColumns](../native-client-odbc-api/sqlcolumns.md).  
  
## <a name="returns"></a>Devoluciones  
 SUCCEED o FAIL.  
  
## <a name="remarks"></a>Observaciones  
 La función **bcp_collen** permite cambiar la longitud de los datos en la variable del programa para una determinada columna al copiar los datos en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con [bcp_sendrow](bcp-sendrow.md).  
  
 La longitud de los datos se determina inicialmente cuando se llama a [bcp_bind](bcp-bind.md) . Si la longitud de los datos cambia entre las llamadas a **bcp_sendrow** y no se utiliza ningún prefijo o terminador de longitud, puede llamar a **bcp_collen** para restablecer la longitud. La llamada siguiente a **bcp_sendrow** utiliza la longitud establecida por la llamada a **bcp_collen**.  
  
 Debe llamar una vez a **bcp_collen** para cada columna de la tabla cuya longitud de los datos desee modificar.  
  
## <a name="see-also"></a>Consulte también  
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
