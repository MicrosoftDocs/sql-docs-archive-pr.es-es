---
title: srv_setutype (API de procedimiento almacenado extendido) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_setutype
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_setutype
ms.assetid: 6160f15d-1b68-411e-ab6d-491ec288f264
author: rothja
ms.author: jroth
ms.openlocfilehash: e9e02605995e44f5869633d5e8778a955236005f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87749324"
---
# <a name="srv_setutype-extended-stored-procedure-api"></a>srv_setutype (API de procedimiento almacenado extendido)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Use la integración con CLR en su lugar.  
  
 Establece el tipo de datos definido por el usuario para una columna de una fila.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
int srv_setutype (  
SRV_PROC *  
srvproc  
,  
int   
column  
,   
DBINT  
user_type   
);  
  
```  
  
## <a name="arguments"></a>Argumentos  
 *srvproc*  
 Es un puntero a la estructura SRV_PROC que es el identificador de una conexión cliente determinada. La estructura contiene información que la biblioteca de API de procedimiento almacenado extendido usa para administrar la comunicación y los datos entre la aplicación y el cliente.  
  
 *column*  
 Indica qué columna se va a establecer. Las columnas se numeran comenzando por 1.  
  
 *user_type*  
 Especifica el código del tipo de datos definido por el usuario.  
  
## <a name="returns"></a>Devoluciones  
 SUCCEED o FAIL. Devuelve FAIL si la columna no existe.  
  
## <a name="remarks"></a>Observaciones  
 Una columna tiene dos tipos de datos: el tipo de datos real y el tipo de datos definido por el usuario. Usa el tipo de datos definido por el usuario [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para almacenar el tipo de datos definido por el usuario real de la columna, si existe, y la información de descripción de la columna, como la nulabilidad y la actualización, para la columna.  
  
 Se puede llamar a la función **srv_setutype** en cualquier momento siempre que se haya definido *column* con **srv_describe** y antes de que se haya enviado la última fila.  
  
> [!IMPORTANT]  
>  Debe revisar minuciosamente el código fuente de los procedimientos almacenados extendidos y debe probar las DLL compiladas antes de instalarlas en el servidor de producción. Para obtener información acerca de la revisión y pruebas de seguridad, vea este [sitio web de Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Consulte también  
 [srv_describe &#40;API de procedimiento almacenado extendido&#41;](srv-describe-extended-stored-procedure-api.md)  
  
  
