---
title: MSSQLSERVER_802 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 802 (Database Engine error)
ms.assetid: 5892ed24-4dcb-4bf9-a8a4-a7ca898832d5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9edcdda1410d7651f7c7531ef98c64c85741f15a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87678207"
---
# <a name="mssqlserver_802"></a>MSSQLSERVER_802
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre de producto|SQL Server|  
|Id. de evento|802|  
|Origen de eventos|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|NO_BUFS|  
|Texto del mensaje|No hay suficiente memoria disponible en el grupo de búferes.|  
  
## <a name="explanation"></a>Explicación  
 Esto se debe a que el grupo de búferes está lleno y no puede crecer más.  
  
## <a name="user-action"></a>Acción del usuario  
 En la siguiente lista se describen los pasos generales que ayudarán a resolver los errores de memoria:  
  
1.  Compruebe si otras aplicaciones o servicios están consumiendo memoria en este servidor. Vuelva a configurar las aplicaciones o servicios menos críticos para que consuman menos memoria.  
  
2.  Empiece a recopilar los contadores del monitor de rendimiento para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **: Administrador de búfer**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **: Administrador de memoria**.  
  
3.  Compruebe los siguientes parámetros de configuración de memoria de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
    -   **memoria de servidor máxima**  
  
    -   **memoria de servidor mínima**  
  
    -   **memoria mínima por consulta**  
  
     Observe si hay algún valor fuera de lo normal y corríjalo según sea necesario. Investigue el porqué de los mayores requisitos de memoria de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se hace una lista de la configuración predeterminada en "Establecer las opciones de configuración del servidor" en los Libros en pantalla de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
4.  Observe la salida de DBCC MEMORYSTATUS y la forma en que cambia cuando aparecen estos mensajes de error.  
  
5.  Compruebe la carga de trabajo (el número de sesiones simultáneas y las consultas que se están ejecutando actualmente).  
  
 Las siguientes acciones pueden hacer que haya más memoria disponible para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Si otras aplicaciones además de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] están consumiendo recursos, intente detenerlas o ejecutarlas en otro servidor.  
  
-   Si ha configurado **max server memory**, aumente su valor.  
  
 Ejecute los siguientes comandos DBCC para liberar varias cachés de la memoria de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   DBCC FREESYSTEMCACHE  
  
-   DBCC FREESESSIONCACHE  
  
-   DBCC FREEPROCCACHE  
  
 Si el problema persiste, necesitará investigar más y, posiblemente, reducir la carga de trabajo.  
  
  
