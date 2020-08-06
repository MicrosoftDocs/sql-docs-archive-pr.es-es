---
title: MSSQLSERVER_7916 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7916 (Database Engine error)
ms.assetid: 9bac3536-de14-4e98-84c2-bde9a59ba0d1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 21b31eedf61369d9c4d1cfdfd5f53eebd3f5341c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673707"
---
# <a name="mssqlserver_7916"></a>MSSQLSERVER_7916
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre de producto|SQL Server|  
|Id. de evento|7916|  
|Origen de eventos|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|DBCC2_REPAIR_RECORD_DELETED|  
|Texto del mensaje|Reparación: se ha eliminado el registro para el id. de objeto O_ID, id. de índice I_ID, id. de partición PN_ID, id. de unidad de asignación A_ID (tipo TYPE), en la página P_ID, ranura S_ID. Se volverán a generar los índices.|  
  
## <a name="explanation"></a>Explicación  
 Este es un mensaje informativo de REPAIR que indica que el registro especificado se eliminó de la página.  
  
## <a name="user-action"></a>Acción del usuario  
 None  
  
  
