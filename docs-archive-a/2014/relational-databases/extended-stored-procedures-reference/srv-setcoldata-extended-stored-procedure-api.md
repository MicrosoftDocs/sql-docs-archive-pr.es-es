---
title: srv_setcoldata (API de procedimiento almacenado extendido) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_setcoldata
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_setcoldata
ms.assetid: 2e19205a-25ca-4d4a-916b-d591cf2c892b
author: rothja
ms.author: jroth
ms.openlocfilehash: b67aa2f7b5a37057d2ed87846689919d84ec4aaf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87749325"
---
# <a name="srv_setcoldata-extended-stored-procedure-api"></a>srv_setcoldata (API de procedimiento almacenado extendido)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Use la integración con CLR en su lugar.  
  
 Especifica la dirección actual para los datos de una columna.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
int srv_setcoldata (  
SRV_PROC *  
srvproc  
,  
int   
column  
,  
void *  
data   
);  
  
```  
  
## <a name="arguments"></a>Argumentos  
 *srvproc*  
 Es un puntero a la estructura SRV_PROC que es el identificador de una conexión cliente determinada. La estructura contiene información que la biblioteca de API de procedimiento almacenado extendido usa para administrar la comunicación y los datos entre la aplicación y el cliente.  
  
 *column*  
 Indica el número de la columna para la que se especificó la dirección. Las columnas se numeran comenzando por 1.  
  
 *data*  
 Es un puntero para los datos de una columna. La memoria asignada para *data* no se debería liberar hasta que los datos de la columna se sustituyan por otra llamada a **srv_setcoldata**, o hasta que se realice una llamada a **srv_senddone** .  
  
## <a name="returns"></a>Devoluciones  
 SUCCEED o FAIL.  
  
## <a name="remarks"></a>Observaciones  
 Cada columna de la fila se debe definir antes con **srv_describe**. Las direcciones de datos de columna se establecen inicialmente con **srv_describe**. Si la dirección de datos de columna cambia, se debe llamar a **srv_setcoldata** para especificar la nueva dirección de los datos y se debe llamar a **srv_setcoldata** por separado para cada columna modificada.  
  
 Los datos nulos se representan estableciendo la longitud de la columna en 0 con **srv_setcollen**. Entonces, se omite la dirección de datos.  
  
> [!IMPORTANT]  
>  Debe revisar minuciosamente el código fuente de los procedimientos almacenados extendidos y debe probar las DLL compiladas antes de instalarlas en el servidor de producción. Para obtener información acerca de la revisión y pruebas de seguridad, vea este [sitio web de Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Consulte también  
 [srv_describe &#40;API de procedimiento almacenado extendido&#41;](srv-describe-extended-stored-procedure-api.md)  
  
  
