---
title: Referencia del programador de procedimientos almacenados extendidos | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- extended stored procedures [SQL Server], listed
ms.assetid: 4e9d0374-0927-4f17-bab9-2215b1b8fea8
author: rothja
ms.author: jroth
ms.openlocfilehash: f3b1beade751cd7a7407f3c33eb7f8ae58c9fd4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87677108"
---
# <a name="extended-stored-procedures-programmer39s-reference"></a>Referencia del programador de procedimientos almacenados extendidos&#39;s
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Use la integración con CLR en su lugar.  
  
 La API Procedimiento almacenado extendido de [!INCLUDE[msCoName](../../includes/msconame-md.md)], previamente parte de Servicios abiertos de datos, proporciona una interfaz de programación de aplicaciones (API) basada en servidor para extender la funcionalidad de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La API está compuesta de funciones y macros de C y C++ que se utilizan para generar aplicaciones.  
  
 Con la aparición de las más recientes y eficaces tecnologías, como la integración CLR, se ha reemplazado en gran medida la necesidad de procedimientos almacenados extendidos.  
  
> [!IMPORTANT]  
>  Debe revisar minuciosamente el código fuente de los procedimientos almacenados extendidos y debe probar las DLL compiladas antes de instalarlas en el servidor de producción. Para obtener información acerca de la revisión y pruebas de seguridad, vea este [sitio web de Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="in-this-section"></a>En esta sección  
  
|||  
|-|-|  
|[Tipo de datos](srv-pfield-extended-stored-procedure-api.md)|  
|[srv_alloc](srv-alloc-extended-stored-procedure-api.md)||  
|[srv_convert](srv-pfieldex-extended-stored-procedure-api.md)|  
|[srv_describe](srv-rpcdb-extended-stored-procedure-api.md)|  
|[srv_getbindtoken](srv-rpcname-extended-stored-procedure-api.md)|  
|[srv_got_attention](srv-rpcnumber-extended-stored-procedure-api.md)|  
||[srv_rpcoptions](srv-rpcoptions-extended-stored-procedure-api.md)|  
|[srv_message_handler](srv-rpcowner-extended-stored-procedure-api.md)|  
|[srv_paramdata](srv-rpcparams-extended-stored-procedure-api.md)|  
|[srv_paraminfo](srv-senddone-extended-stored-procedure-api.md)|  
|[srv_paramlen](srv-sendmsg-extended-stored-procedure-api.md)|  
|[srv_parammaxlen](srv-sendrow-extended-stored-procedure-api.md)|  
|[srv_paramname](srv-setcoldata-extended-stored-procedure-api.md)|  
|[srv_paramnumber](srv-setcollen-extended-stored-procedure-api.md)|  
|[srv_paramset](srv-setutype-extended-stored-procedure-api.md)|  
|[srv_paramsetoutput](srv-willconvert-extended-stored-procedure-api.md)|  
|[srv_paramstatus](srv-wsendmsg-extended-stored-procedure-api.md)|  
|[srv_paramtype](srv-paramtype-extended-stored-procedure-api.md)||  
  
  
