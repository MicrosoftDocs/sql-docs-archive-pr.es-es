---
title: Modificar las cuentas de servicios de controlador y de cliente | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 44a73ddb-18ad-415c-bfbe-126ab2e3290b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 62a054749f1d53323bde5c9d05a1e7632b1dda85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87747368"
---
# <a name="modify-the-controller-and-client-services-accounts"></a>Modificar las cuentas de servicios de controlador y de cliente
  En este tema, aprenderá a modificar las cuentas de servicio del cliente y Distributed Replay Controller; y, a continuación, volverá a aplicar las listas de control de acceso (ACL).  
  
### <a name="to-start-or-stop-the-distributed-replay-services-using-computer-management"></a>Iniciar o detener los servicios de Distributed Replay utilizando Administración de equipos  
  
1.  En el equipo en el que se instalan los servicios de Distributed Replay, desde el símbolo del sistema, escriba `dcomcnfg`.  
  
2.  Haga doble clic en **servicios**, desplácese hacia abajo y haga clic con el botón secundario en ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay \<service name> **y, a continuación, haga clic en **iniciar** o **detener**.  
  
### <a name="to-modify-the-distributed-replay-controller-service"></a>Para modificar el servicio Distributed Replay Controller  
  
1.  En el equipo del controlador, detenga el servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller.  
  
2.  En **Servicios**, haga clic con el botón derecho en **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller**y luego seleccione **Propiedades**.  
  
3.  En la ventana **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller** , en la pestaña **Iniciar sesión** , seleccione **Esta cuenta**, escriba la nueva cuenta de inicio de sesión o haga clic en **Examinar** para buscarla y, a continuación, haga clic en **Aceptar**.  
  
     **Importante**: Al configurar Distributed Replay Controller, puede especificar una o más cuentas de usuario que se usarán para ejecutar los servicios Distributed Replay Client. La lista siguiente es una relación de las cuentas admitidas:  
  
    -   Cuenta de usuario de dominio  
  
    -   Cuenta de usuario local creada por el usuario  
  
    -   Administrador  
  
    -   Cuenta virtual y MSA (cuenta de servicio administrada)  
  
    -   Network Services, servicios locales y sistema  
  
     No se aceptan cuentas de grupo (locales o de dominio) y otras cuentas integradas (como Todos).  
  
4.  Inicie el servicio Distributed Replay Controller.  
  
### <a name="to-modify-the-distributed-replay-client-service"></a>Para modificar el servicio Distributed Replay Client  
  
1.  Antes de modificar el servicio Distributed Replay Client, asegúrese de que la cuenta del servicio de cliente que va a cambiar se especificó durante la instalación (en el parámetro CTLRUSERS en el equipo del controlador). Si la cuenta de servicio de cliente que va a cambiar no se especificó durante la configuración, primero debe realizar los siguientes pasos:  
  
    1.  Detenga el servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller.  
  
    2.  En el equipo del controlador en el que esté instalado el servicio del controlador, desde el símbolo del sistema, escriba `dcomcnfg`.  
  
    3.  En la ventana **Servicios de componentes**, vaya a **Raíz de consola -> Servicios de componentes -> Equipos -> Mi PC -> DCOM Config ->DReplayController**.  
  
    4.  Haga clic con el botón derecho en **DReplayController**y luego haga clic en **Propiedades**.  
  
    5.  En la ventana **Propiedades de DReplayController** , en la pestaña **Seguridad** , haga clic en **Editar** en la sección **Permisos de inicio y activación** .  
  
    6.  Conceda a la nueva cuenta de inicio de sesión del servicio de cliente los permisos **Activación local y remota** y, a continuación, haga clic en **Aceptar**.  
  
    7.  Haga clic en **Editar** en la sección **Permisos de acceso** y conceda a la nueva cuenta de inicio de sesión del servicio cliente los permisos **Acceso local y remoto** y, a continuación, haga clic en **Aceptar**.  
  
    8.  Haga clic en **Aceptar** para cerrar la ventana **Propiedades de DReplayController** .  
  
    9. En el equipo del controlador, agregue la cuenta de inicio de sesión de servicio de cliente cambiada al grupo **Usuarios COM distribuidos** .  
  
    10. Inicie el servicio SQL Server Distributed Replay Controller.  
  
2.  Detenga el servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Client.  
  
3.  En la ventana **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Client** , en la pestaña **Iniciar sesión** , seleccione **Esta cuenta**, escriba la nueva cuenta de inicio de sesión o haga clic en **Examinar** para buscarla y, a continuación, haga clic en **Aceptar**.  
  
4.  Inicie el servicio Distributed Replay Client.  
  
  
