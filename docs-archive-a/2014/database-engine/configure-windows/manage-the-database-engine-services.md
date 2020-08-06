---
title: Administrar los Servicios de Motor de base de datos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Configuration Manager, accessing
- Database Engine [SQL Server], services
- managing services [SQL Server], about service management
- services [SQL Server]
- SQL Server Agent service, managing
- SQL Server services, about SQL Server service
- MSSQLServer
- server configuration [SQL Server]
- managing services [SQL Server]
- SQL Server Agent service
- services [SQL Server], managing
- administering SQL Server, services
- SQL Server services
ms.assetid: aa732e43-53ba-4eea-bb9b-089da0766fc1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c18338493777d14c5e6fe28cb38bd71aaffd5da3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744306"
---
# <a name="manage-the-database-engine-services"></a>Administrar el servicio del motor de base de datos
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se ejecuta en los sistemas operativos como un servicio. Un servicio es un tipo de aplicación que se ejecuta en segundo plano en el sistema. Los servicios suelen proporcionar características básicas del sistema operativo, como el servicio web, el registro de eventos o el servicio de archivos. Los servicios se pueden ejecutar sin mostrar una interfaz de usuario en el escritorio. El [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y algunos otros componentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se ejecutan como servicios. Estos servicios suelen iniciarse cuando se inicia el sistema operativo. Esto depende de lo que se especifique durante la instalación; algunos servicios no se inician de forma predeterminada. En esta sección se describe la administración de los diversos servicios de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Antes de iniciar una sesión en una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], debe saber cómo iniciar, detener, pausar, reanudar y reiniciar una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Una vez iniciada la sesión, puede realizar diversas tareas, como administrar el servidor o consultar la base de datos.  
  
## <a name="using-the-sql-server-service"></a>Usar el servicio SQL Server  
 Cuando se inicia una instancia del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], se inicia el servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Una vez iniciado el servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , los usuarios pueden establecer nuevas conexiones al servidor. El servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se puede iniciar y detener como un servicio, ya sea localmente o de forma remota. El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servicio se conoce como [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) si es la instancia predeterminada, o MSSQL $ *\<instancename>* si es una instancia con nombre.  
  
## <a name="using-sql-server-configuration-manager"></a>Usar el Administrador de configuración de SQL Server  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le permite detener, iniciar o pausar diversos servicios de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  El Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no puede administrar servicios de [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
 También puede utilizar el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para ver las propiedades del servicio seleccionado. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] El Administrador de configuración es un complemento de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console (MMC). Para obtener más información sobre MMC y cómo funciona un complemento, vea la Ayuda de Windows.  
  
 **Para tener acceso al Administrador de configuración de SQL Server**  
  
-   En el menú **Inicio** , elija **Todos los programas**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Herramientas de configuración**y, por último, **Administrador de configuración de SQL Server**.  
  
 **Para tener acceso al Administrador de configuración de SQL Server mediante Windows 8**  
  
 Como el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] es un complemento del programa [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console y no un programa independiente, el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no aparece como aplicación al ejecutar Windows 8.0. Para abrir el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , en el acceso a **Buscar** , en **Aplicaciones**, escriba **SQLServerManager12.msc** si la versión es [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], **SQLServerManager11.msc** si es [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]o **SQLServerManager10.msc** si es[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]y, luego, pulse **Entrar**.  
  
## <a name="in-this-section"></a>En esta sección  
  
|||  
|-|-|  
|[Requisitos de seguridad para administrar servicios](security-requirements-for-managing-services.md)|[Evitar el inicio automático de una instancia de SQL Server &#40;Administrador de configuración de SQL Server&#41;](scm-services-prevent-automatic-startup-of-an-instance.md)|  
|[Configurar los permisos y las cuentas de servicio de Windows](configure-windows-service-accounts-and-permissions.md)|[Cambiar la cuenta de inicio del servicio para SQL Server &#40;Administrador de configuración de SQL Server&#41;](scm-services-change-the-service-startup-account.md)|  
|[Ejecutar SQL Server con o sin red](run-sql-server-with-or-without-a-network.md)|[Configurar opciones de inicio del servidor &#40;Administrador de configuración de SQL Server&#41;](scm-services-configure-server-startup-options.md)|  
|[Servicio SQL Server Browser &#40;motor de base de datos y SSAS&#41;](sql-server-browser-service-database-engine-and-ssas.md)|[Cambiar la contraseña de las cuentas que usa SQL Server &#40;Administrador de configuración de SQL Server&#41;](scm-services-change-the-password-of-the-accounts-used.md)|  
|[Opciones de inicio del servicio de motor de base de datos](database-engine-service-startup-options.md)|[Configurar registros de errores de SQL Server](scm-services-configure-sql-server-error-logs.md)|  
|[Iniciar, detener, pausar, reanudar y reiniciar el motor de base de datos, Agente SQL Server o el Servicio SQL Server Browser](start-stop-pause-resume-restart-sql-server-services.md)|[Cambiar el modo de autenticación del servidor](change-server-authentication-mode.md)|  
|[Iniciar SQL Server en modo de usuario único](start-sql-server-in-single-user-mode.md)|[servicio del objeto de escritura de SQL](sql-writer-service.md)|  
|[Iniciar SQL Server con la configuración mínima](start-sql-server-with-minimal-configuration.md)|[Difundir un mensaje de cierre del sistema &#40;símbolo del sistema&#41;](broadcast-a-shutdown-message-command-prompt.md)|  
|[Conectarse a otro equipo &#40;Administrador de configuración de SQL Server&#41;](scm-services-connect-to-another-computer.md)|[Iniciar una sesión en una instancia de SQL Server &#40;símbolo del sistema&#41;](log-in-to-an-instance-of-sql-server-command-prompt.md)|  
|[Configurar una instancia de SQL Server para que se inicie automáticamente &#40;Administrador de configuración de SQL Server&#41;](scm-services-set-an-instance-to-start-automatically.md)|[Configurar permisos del sistema de archivos para el acceso al motor de base de datos](configure-file-system-permissions-for-database-engine-access.md)|  
  
## <a name="related-content"></a>Contenido relacionado  
 [Configurar el Agente SQL Server](../../ssms/agent/sql-server-agent.md)  
  
 [Iniciar una sesión en SQL Server](logging-in-to-sql-server.md)  
  
  
