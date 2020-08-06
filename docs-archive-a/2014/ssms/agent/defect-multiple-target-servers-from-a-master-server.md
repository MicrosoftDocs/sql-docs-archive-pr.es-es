---
title: Dar de baja varios servidores de destino desde un servidor maestro | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
- multiple target server defections
ms.assetid: 61a3713b-403a-4806-bfc4-66db72ca1156
author: stevestein
ms.author: sstein
ms.openlocfilehash: b31a8bc38968733de0a23f67a71772721c8baedd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745636"
---
# <a name="defect-multiple-target-servers-from-a-master-server"></a>Defect Multiple Target Servers from a Master Server
  En este tema se describe cómo dar de baja varios servidores de destino desde una configuración de administración multiservidor en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Ejecute este procedimiento en el servidor maestro.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Uso de SQL Server Management Studio  
  
#### <a name="to-defect-multiple-target-servers-from-a-master-server"></a>Para dar de baja varios servidores de destino desde un servidor maestro  
  
1.  En el **Explorador de objetos**, expanda un servidor que esté configurado como servidor maestro.  
  
2.  Haga clic con el botón derecho en **Agente SQL Server**, seleccione **Administración multiservidor**y, luego, haga clic en **Administrar servidores de destino**.  
  
3.  Haga clic en **Exponer instrucciones**, y, a continuación, en la lista **Tipo de instrucción** , haga clic en **Dar de baja**.  
  
4.  En **Destinatarios**, realice una de las siguientes acciones:  
  
    -   Haga clic en **Todos los servidores de destino** para dar de baja todos los servidores de destino de este servidor principal. Utilice esta opción si desea desinstalar totalmente la configuración de la administración multiservidor actual.  
  
    -   Haga clic en **Estos servidores de destino**y, a continuación, active la casilla **Seleccionar** correspondiente para dar de baja algunos servidores de destino, pero no todos, de este servidor principal.  
  
## <a name="see-also"></a>Consulte también  
 [Crear un entorno multiservidor](create-a-multiserver-environment.md)   
 [Administración automatizada en una empresa](automated-administration-across-an-enterprise.md)   
 [Dar de baja un servidor de destino desde un servidor maestro](defect-a-target-server-from-a-master-server.md)  
  
  
