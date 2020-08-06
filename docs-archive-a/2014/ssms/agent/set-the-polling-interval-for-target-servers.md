---
title: Establecer el intervalo de sondeo de los servidores de destino | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- interval for polling [SQL Server]
- target servers [SQL Server], polling interval
- polling interval [SQL Server]
ms.assetid: 4ffbbefa-77fb-442e-a77c-cb8c6cab9f3c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 36517f60a99a1a844f6d14d489587eef1de9cb13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751630"
---
# <a name="set-the-polling-interval-for-target-servers"></a>Set the Polling Interval for Target Servers
  En este tema se describe cómo establecer la frecuencia con la que el [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agente actualiza la información del servidor maestro en los servidores de destino. Un trabajo es una serie especificada de acciones que realiza el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Un trabajo multiservidor es un trabajo que ejecuta un servidor maestro en uno o más servidores de destino.  
  
-   **Antes de empezar:**  [Seguridad](#Security)  
  
-   **Para establecer el intervalo de sondeo para servidores de destino, con:**  [SQL Server Management Studio](#SSMS), [Transact-SQL](#TSQL)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de comenzar  
 Cada servidor de destino puede ejecutar una instancia del mismo trabajo al mismo tiempo. Cada servidor de destino sondea periódicamente al servidor maestro, descarga una copia de cualquier nuevo trabajo asignado al servidor de destino y, a continuación, se desconecta. El servidor de destino ejecuta el trabajo de manera local y, a continuación, se vuelve a conectar al servidor maestro para cargar el estado del resultado del trabajo.  
  
> [!NOTE]  
>  Si no es posible el acceso al servidor maestro cuando el servidor de destino intenta cargar el estado del trabajo, dicho estado de trabajo se coloca en la cola hasta que se pueda obtener acceso al servidor principal.  
  
###  <a name="security"></a><a name="Security"></a> Seguridad  
 Para obtener información detallada, vea [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) y [Choose the Right SQL Server Agent Service Account for Multiserver Environments](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Uso de SQL Server Management Studio  
 **Para establecer el intervalo de sondeo para servidores de destino**  
  
1.  En **Explorador de objetos,** Conéctese a una instancia de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] y, a continuación, expándala.  
  
2.  Haga clic con el botón derecho en **Agente SQL Server**, seleccione **Administración multiservidor**y, luego, haga clic en **Administrar servidores de destino**.  
  
3.  En la pestaña **Estado de servidor de destino** , haga clic en **Exponer instrucciones**.  
  
4.  En la lista **Tipo de instrucción** , seleccione **Establecer intervalo de sondeo**.  
  
5.  En la casilla **Intervalo de sondeo** , escriba el número de segundos (entre 10 y 28.800) que deben transcurrir antes de que el servidor de destino sondee al servidor maestro.  
  
6.  En **Destinatarios**, realice una de las siguientes acciones:  
  
    1.  Haga clic en **Todos los servidores de destino** si todos los servidores de destino comparten el mismo intervalo de sondeo.  
  
    2.  Haga clic en **Estos servidores de destino** si no todos los servidores de destino comparten el mismo intervalo de sondeo y, a continuación, seleccione cada servidor de destino que usará este intervalo de sondeo.  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Usar Transact-SQL  
 **Para establecer el intervalo de sondeo para servidores de destino**  
  
1.  En el Explorador de objetos, conéctese a una instancia del Motor de base de datos y, a continuación, expándala.  
  
2.  En la barra de herramientas, haga clic en **Nueva consulta**.  
  
3.  En la ventana de consulta, use el sp_post_msx_operation &#40;procedimiento almacenado del sistema [&#41;de Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql) para establecer el intervalo de sondeo para los servidores de destino.  
  
## <a name="see-also"></a>Consulte también  
 [dbo.sysdownloadlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysdownloadlist-transact-sql)  
  
  
