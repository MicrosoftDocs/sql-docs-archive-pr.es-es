---
title: MSSQLSERVER_8974 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8974 (Database Engine error)
ms.assetid: 52098678-0858-4a14-ad07-37ebbafca5fc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ff3107f5b62caf04e232532c2d2b93d5da19fb53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87678193"
---
# <a name="mssqlserver_8974"></a>MSSQLSERVER_8974
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre de producto|SQL Server|  
|Id. de evento|8974|  
|Origen de eventos|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|DBCC3_OFF_ROW_DATA_NODE_HAS_TWO_PARENTS|  
|Texto del mensaje|Error de tabla: id. de objeto O_ID, id. de índice I_ID, id. de partición PN_ID, id. de unidad de asignación A_ID (tipo TYPE). Las páginas P_ID2, zona S_ID2 y P_ID3, zona P_ID3 apuntan al nodo de datos no consecutivos de la página P_ID1, zona S_ID1, Id. de texto TEXT_ID.|  
  
## <a name="explanation"></a>Explicación  
 Un nodo de datos no consecutivos tiene dos registros de datos o índices que lo enumeran como un nodo secundario. Un nodo solo puede tener un nodo primario.  
  
## <a name="user-action"></a>Acción del usuario  
  
### <a name="look-for-hardware-failure"></a>Busque un error de hardware  
 Ejecute un diagnóstico de hardware y corrija cualquier problema. Examine también los registros del sistema y de aplicación de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows así como el registro de errores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para ver si el error se produjo como resultado de un error de hardware. Arregle cualquier problema relacionado con el hardware que encuentre en estos registros.  
  
 Si sigue teniendo problemas de datos dañados, intente intercambiar diferentes componentes de hardware para aislar el problema. Asegúrese de que el sistema no tiene habilitada la memoria caché de escritura en el controlador de disco. Si cree que el problema se debe a la caché de escritura, póngase en contacto con su proveedor de hardware.  
  
 Finalmente, puede resultarle útil cambiar a un nuevo sistema de hardware. Este cambio puede incluir volver a formatear las unidades de disco y volver a instalar el sistema operativo.  
  
### <a name="restore-from-backup"></a>Restaure mediante la copia de seguridad  
 Si el problema no está relacionado con el hardware y tiene una copia de seguridad limpia disponible, úsela para restaurar la base de datos.  
  
### <a name="run-dbcc-checkdb"></a>Ejecute DBCC CHECKDB  
 Si no tiene disponible una copia de seguridad limpia, ejecute DBCC CHECKDB sin una cláusula REPAIR para determinar el alcance de los daños. DBCC CHECKDB recomendará el uso de una cláusula REPAIR. A continuación, ejecute DBCC CHECKDB con la cláusula REPAIR apropiada para reparar el problema.  
  
> [!CAUTION]  
>  Si no está seguro del efecto que tendrá DBCC CHECKDB con una cláusula REPAIR en los datos, póngase en contacto con su proveedor principal de soporte antes de ejecutar esta instrucción.  
  
 Si ejecuta DBCC CHECKDB con una de las cláusulas REPAIR y no se soluciona el problema, póngase en contacto con su proveedor principal de soporte.  
  
#### <a name="results-of-running-repair-options"></a>Resultados de ejecutar opciones REPAIR  
 El nodo de datos no consecutivos de la página *P_ID1* se eliminará, así como las dos referencias de las páginas *P_ID2* y *P_ID3*.  
  
> [!CAUTION]  
>  Esta reparación puede causar la pérdida de datos.  
  
  
