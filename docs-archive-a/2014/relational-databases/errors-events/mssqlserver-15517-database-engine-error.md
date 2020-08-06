---
title: MSSQLSERVER_15517 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15517 (Database Engine error)
ms.assetid: f94287f5-129f-4c52-9d34-62b996088001
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b8e66e211faf03e1457953d0292e711cde1798ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87675941"
---
# <a name="mssqlserver_15517"></a>MSSQLSERVER_15517
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre de producto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Id. de evento|15517|  
|Origen de eventos|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|SEC_CANNOTEXECUTEASUSER|  
|Texto del mensaje|No se puede ejecutar como la entidad de seguridad de base de datos porque la entidad "*entidad*" no existe, este tipo de entidad de seguridad no se puede suplantar o el usuario no tiene permiso.|  
  
## <a name="user-action"></a>Acción del usuario  
 Use el nombre de una entidad de seguridad existente u obtenga el permiso IMPERSONATE para esa entidad de seguridad.  
  
 También puede producirse el evento 15517 después de que alguien que no sea el propietario de la base de datos original adjunte y restaure una base de datos. Para resolver este error, cambie el db_owner a un inicio de sesión en el servidor mediante el comando siguiente:  
  
```  
ALTER AUTHORIZATION ON DATABASE:: DBName TO [NewLogin]  
```  
  
## <a name="see-also"></a>Consulte también  
 [OLTP en memoria &#40;optimización en memoria&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
