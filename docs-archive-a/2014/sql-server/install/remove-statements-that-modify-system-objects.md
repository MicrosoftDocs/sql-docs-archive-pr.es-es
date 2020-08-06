---
title: Quitar instrucciones que modifican objetos del sistema | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- direct system catalog updates [SQL Server]
- system catalogs [SQL Server]
ms.assetid: 221b46c2-c27e-4df8-bd8c-8b990d6d5e98
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 526181bc4bf7ab81df2eaa25f19e7627c9b7af10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751706"
---
# <a name="remove-statements-that-modify-system-objects"></a>Eliminar instrucciones que modifican objetos del sistema
  El Asesor de actualizaciones ha detectado la existencia de instrucciones que actualizan el catálogo del sistema. No se permite realizar actualizaciones directas del catálogo del sistema. Modifique los scripts de SQL para que utilicen API documentadas y oficiales.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Descripción  
 No se permite realizar actualizaciones directas del catálogo del sistema. Cualquier intento de hacerlo generará el siguiente error:  
  
 `Server: Msg 259, Level 16, State 1, Line 1`  
  
 `Ad hoc updates to system catalogs are not allowed.`  
  
## <a name="corrective-action"></a>Acción correctora  
 Modifique los scripts de SQL para que utilicen API documentadas y oficiales. Por ejemplo, utilice ALTER DATABASE *database_name* SET EMERGENCY en lugar de ejecutar una instrucción UPDATE en la tabla del sistema **sysdatabases** .  
  
## <a name="see-also"></a>Consulte también  
 [Problemas de actualización Motor de base de datos](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server el asesor de actualizaciones de 2014 &#91;nuevo&#93;](https://docs.microsoft.com/sql/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
