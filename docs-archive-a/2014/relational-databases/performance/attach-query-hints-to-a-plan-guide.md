---
title: Asociar sugerencias de consulta a una guía de plan | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 2131f796-6359-4f9e-9047-da0b3d4dedaf
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 074c69ffefd2b5a7b2ef445f941f97b7130b0732
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674784"
---
# <a name="attach-query-hints-to-a-plan-guide"></a>Asociar sugerencias de consulta a una guía de plan
  En una guía de plan se puede usar cualquier combinación de sugerencias de consulta válidas. Cuando una guía de plan coincide con una consulta, la cláusula OPTION especificada en la cláusula de sugerencia de una guía de plan se agrega a la consulta antes de la compilación y optimización. Si una consulta que coincide con una guía de plan ya tiene una cláusula OPTION, las sugerencias de consulta especificadas en la guía de plan sustituirán a las de la consulta. Sin embargo, para que una guía de plan coincida con una consulta que ya tiene una cláusula OPTION, debe incluir esta cláusula de la consulta al especificar el texto con el que debe coincidir la instrucción sp_create_plan_guide. Si desea que las sugerencias especificadas en la guía de plan se agreguen a las que ya existen en la consulta, en lugar de sustituirlas, debe especificar tanto las originales como las adicionales en la cláusula OPTION de la guía de plan.  
  
> [!CAUTION]  
>  Las guías de plan que usan incorrectamente las sugerencias de consulta pueden provocar problemas de compilación, ejecución o rendimiento. Solo deben utilizarlas los programadores y administradores de bases de datos con experiencia.  
  
## <a name="common-query-hints-used-in-plan-guides"></a>Sugerencias de consulta comúnmente utilizadas en las guías de plan  
 Las consultas que pueden aprovechar las guías de plan suelen estar basadas en parámetros, y puede que su rendimiento sea bajo porque utilizan planes de consulta en caché cuyos valores de parámetros no representan un caso del tipo "el peor de los casos" o el más representativo. Este problema se puede solucionar con las sugerencias de consulta OPTIMIZE FOR y RECOMPILE. OPTIMIZE FOR indica a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que utilice un valor determinado para un parámetro cuando se optimiza la consulta. RECOMPILE indica al servidor que descarte un plan de consulta tras la ejecución, con lo que se forzará al optimizador de consultas a volver a compilar un nuevo plan de consulta la próxima vez que se ejecute la misma consulta. Para obtener un ejemplo, vea [Guías de plan](plan-guides.md).  
  
 Por otro lado, puede especificar las sugerencias de tabla INDEX, FORCESCAN y FORCESEEK como sugerencias de consulta. Cuando se especifican como sugerencias de consulta, estas sugerencias se comportan de la misma manera que una tabla insertada o una sugerencia de vista. La sugerencia INDEX obliga al optimizador de consultas a usar solo los índices especificados para tener acceso a los datos a los que se hace referencia en la tabla o vista. La sugerencia FORCESEEK obliga al optimizador de consultas a usar solo una operación Index Seek para tener acceso a los datos a los que se hace referencia en la tabla o en la vista. Estas sugerencias proporcionan la funcionalidad de la guía de plan adicional y permiten tener más influencia sobre la optimización de consultas que usan la guía de plan.  
  
  
