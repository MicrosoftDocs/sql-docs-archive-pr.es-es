---
title: La nueva columna en la salida de sp_helptrigger puede afectar a las aplicaciones | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sp_helptrigger
ms.assetid: b7c42a8f-f2e0-4fa3-b046-3cf39c854c47
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0b1f5e936843ed84a5c6b88e2f3685e7a4272bc2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676808"
---
# <a name="new-column-in-output-of-sp_helptrigger-may-impact-applications"></a>La nueva columna de la salida de sp_helptrigger podría afectar a las aplicaciones
  trigger_schemaias la última columna del conjunto de resultados devuelto por el procedimiento almacenado del sistema sp_helptrigger.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Para obtener más información acerca de los desencadenadores definidos en una tabla determinada, consulte la vista de catálogo sys.triggers.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Acción correctora  
 Revise el uso de sp_helptrigger en las aplicaciones. Puede que tenga que modificar las aplicaciones para que se ajusten a la columna adicional. O bien, puede utilizar en su lugar la vista de catálogo sys.triggers.  
  
## <a name="see-also"></a>Consulte también  
 [Problemas de actualización Motor de base de datos](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server el asesor de actualizaciones de 2014 &#91;nuevo&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
