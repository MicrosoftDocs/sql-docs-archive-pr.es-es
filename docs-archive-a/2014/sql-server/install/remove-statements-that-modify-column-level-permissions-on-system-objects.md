---
title: Quitar instrucciones que modifican permisos de nivel de columna en objetos del sistema | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- column-level permissions [SQL Server]
- removed statement permissions [SQL Server]
ms.assetid: 7f4fbbef-2696-4911-903b-63f6d9e4484a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e55af3dca0c55c2babd09bc6cfc48ed0ddf3ad7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87675145"
---
# <a name="remove-statements-that-modify-column-level-permissions-on-system-objects"></a>Eliminar instrucciones que modifican los permisos de nivel de columna en los objetos del sistema
  El Asesor de actualizaciones ha detectado permisos de nivel de columna no estándar en objetos del sistema. No se mantendrán estos cambios en los permisos cuando se lleve a cabo la actualización. Además, ya no se admite el uso de permisos de nivel de columna en objetos del sistema. Elimine aquellas instrucciones de sus aplicaciones que establezcan permisos de nivel de columna en objetos del sistema.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Acción correctora  
 Elimine todas aquellas instrucciones de sus aplicaciones que concedan, denieguen o revoquen permisos de nivel de columna para objetos del sistema.  
  
## <a name="see-also"></a>Consulte también  
 [Problemas de actualización Motor de base de datos](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server el asesor de actualizaciones de 2014 &#91;nuevo&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
