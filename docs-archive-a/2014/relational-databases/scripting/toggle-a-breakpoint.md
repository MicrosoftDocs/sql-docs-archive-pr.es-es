---
title: Alternar un punto de interrupción
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c477ab89-a1cd-4f2c-aa7c-40525041100f
author: rothja
ms.author: jroth
ms.openlocfilehash: 72e26e9b1d04bc2eced6bcb6d93d3c86a016d308
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87675792"
---
# <a name="toggle-a-breakpoint"></a>Alternar un punto de interrupción
  El hecho de establecer un punto de interrupción en una instrucción [!INCLUDE[tsql](../../includes/tsql-md.md)] se denomina alternar un punto de interrupción.  
  
## <a name="breakpoints"></a>Puntos de interrupción  
 Una vez establecido el punto de interrupción, se representa mediante un icono en la barra gris situada a la izquierda de la instrucción. El icono se denomina glifo de punto de interrupción. [!INCLUDE[tsql](../../includes/tsql-md.md)] se aplican a instrucciones [!INCLUDE[tsql](../../includes/tsql-md.md)] completadas. Cuando se alterna un punto de interrupción, el depurador resalta la instrucción [!INCLUDE[tsql](../../includes/tsql-md.md)] asociada.  
  
 Si hay varias instrucciones [!INCLUDE[tsql](../../includes/tsql-md.md)] en una línea, puede alternar un punto de interrupción para cada instrucción. Al hacer clic en la barra gris de la izquierda de la ventana se alterna un punto de interrupción en la primera instrucción de la línea. Para alternar un punto de interrupción en una instrucción subsiguiente, resalte cualquier parte de la instrucción o mueva el cursor a la instrucción y, a continuación, presione F9 o haga clic en **Alternar punto de interrupción** en el menú **Depurar** . Si hay varios puntos de interrupción en una línea, solo hay un glifo de punto de interrupción en la barra gris de la izquierda.  
  
 Una vez que se ha alternado un punto de interrupción, puede realizar diversas acciones en el punto de interrupción, como editar sus propiedades o deshabilitarlo provisionalmente. Para obtener más información, vea [Utilizar puntos de interrupción de Transact-SQL](transact-sql-breakpoints.md).  
  
## <a name="toggle-a-breakpoint"></a>Alternar un punto de interrupción  
 **Para alternar un punto de interrupción en una instrucción Transact-SQL**  
  
1.  Haga clic en la barra deshabilitada situada a la izquierda de la instrucción [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
2.  Alternativamente, puede resaltar cualquier parte de la instrucción o mover el cursor a la instrucción y, a continuación, realizar cualquiera de las acciones siguientes:  
  
    -   Presione F9.  
  
    -   En el menú **Depurar** , haga clic en **Alternar punto de interrupción**.  
  
  
