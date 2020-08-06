---
title: Comprobar que se pueden escribir todos los grupos de archivos durante el proceso de actualización | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- filegroups [SQL Server], writeable
- writeable filegroups [SQL Server]
ms.assetid: 2985efc1-4b14-46c3-abbd-a656b159f23c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8146efb876bf97c36c549a2b58d104592df611e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751646"
---
# <a name="verify-all-filegroups-are-writeable-during-the-upgrade-process"></a>Comprobar que es posible escribir en todos los grupos de archivos durante el proceso de actualización
  El Asesor de actualizaciones ha detectado una base de datos que tiene uno o más grupos de archivos de solo lectura. Todas las bases de datos de la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deben tener los grupos de archivos establecidos en READ_WRITE antes de llevar a cabo la actualización.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Acción correctora  
 Utilice ALTER DATABASE para establecer el grupo de archivos en READ_WRITE.  
  
## <a name="see-also"></a>Consulte también  
 [Problemas de actualización Motor de base de datos](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server el asesor de actualizaciones de 2014 &#91;nuevo&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
