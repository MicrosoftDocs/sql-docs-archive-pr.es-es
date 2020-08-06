---
title: Planes de mantenimiento de bases de datos reemplazados | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- suspended database maintenance plans
- database maintenance plans [SQL Server Agent]
- maintenance plans [SQL Server Agent]
ms.assetid: efac127c-6c81-4c7a-a6c4-9aae5d15545d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3aea75cc4ecc94ccbaeb1f35cecd0b18ff3a65ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662508"
---
# <a name="database-maintenance-plans-superseded"></a>Se han reemplazado los planes de mantenimiento de bases de datos
    
## <a name="component"></a>Componente  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Agente de  
  
## <a name="description"></a>Descripción  
 Los planes de mantenimiento de bases de datos existentes se actualizarán y continuarán funcionando. Sin embargo, no podrá crear nuevos planes de mantenimiento de bases de datos utilizando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Para ver los planes de mantenimiento en el Explorador de objetos, expanda Administración y, a continuación, expanda Heredado. Puede migrar los planes de mantenimiento de bases de datos existentes al nuevo formato seleccionando **migrar** en el menú contextual de cualquier plan de mantenimiento de bases de datos. Dado que la nueva característica de plan de mantenimiento no sustituye directamente a los planes de mantenimiento de bases de datos, es posible que se pierda alguna funcionalidad tras la migración. Al migrar un plan de mantenimiento de bases de datos no se elimina el plan anterior, por lo que puede probar su funcionalidad como plan de mantenimiento antes de quitar el plan anterior.  
  
 Las características siguientes ya no se admiten dentro de los planes de mantenimiento de bases de datos:  
  
-   Trasvase de registros  
  
-   La opción **intentar reparar los problemas secundarios** de la tarea de comprobación de integridad de la **base de datos**  
  
## <a name="corrective-action"></a>Acción correctora  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] evita que el trasvase de registros se incluya en un plan de mantenimiento de bases de datos. Para obtener más información, vea "Trasvase de registros" en los Libros en pantalla de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
