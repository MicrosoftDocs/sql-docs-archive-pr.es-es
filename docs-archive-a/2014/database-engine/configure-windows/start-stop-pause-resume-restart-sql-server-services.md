---
title: Iniciar, detener, pausar, reanudar, reiniciar el servicio de Motor de base de datos, Agente SQL Server o SQL Server Browser | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Configuration Manager, start and stop services
- stopping SQL Server Agent
- parameters [SQL Server], startup options
- SQL Server, startup options
- Database Engine [SQL Server], starting and stopping services
- pausing SQL Server
- PowerShell [SQL Server], starting and stopping services
- single-user mode [SQL Server], starting in
- SQL Server Management Studio [SQL Server], starting or stopping services
- stopping SQL Server Browser service
- starting SQL Server Agent
- default instances [SQL Server], starting and stopping
- SQL Server Agent, starting and stopping
- command prompt [SQL Server], starting and stopping SQL Server services
- continuing SQL Server
- starting SQL Server Database Engine
- net stop commands [SQL Server]
- command prompt [SQL Server], SQL Browser service
- Configuration Manager, start and stop services
- resuming SQL Server
- startup options [SQL Server]
- named instances [SQL Server], starting and stopping
- net start commands [SQL Server]
- SQL Server, starting and stopping
- stopping SQL Server
- starting SQL Server Browser service
- SQL Server Database Engine setting startup options
- administering SQL Server, starting and stopping services
- Management Studio [SQL Server], starting or stopping services
ms.assetid: 32660a02-e5a1-411a-9e57-7066ca459df6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f4b102c8fd81923d7386c8e556896e715311a07e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748895"
---
# <a name="start-stop-pause-resume-restart-the-database-engine-sql-server-agent-or-sql-server-browser-service"></a>Iniciar, detener, pausar, reanudar y reiniciar el motor de base de datos, Agente SQL Server o el Servicio SQL Server Browser
  En este tema se describe cómo iniciar, comandos de detener, comandos de pausar, comandos de reanudar o reiniciar [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], comandos de el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o el servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser mediante el uso del Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , comandos de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], comandos de **net** desde un símbolo del sistema, comandos de [!INCLUDE[tsql](../../includes/tsql-md.md)], comandos de or PowerShell.  
  
-   **Antes de empezar:**  
  
    -   [¿Cuáles son estos servicios?](#Services)  
  
    -   [Información adicional](#MoreInformation)  
  
    -   [Seguridad](#Security)  
  
-   **Instrucciones mediante:**  
  
    -   [Administrador de configuración de SQL Server](#SSCMProcedure)  
  
    -   [SQL Server Management Studio](#SSMSProcedure)  
  
    -   [Comandos net desde una ventana del símbolo de sistema](#CommandPrompt)  
  
    -   [Transact-SQL](#TsqlProcedure)  
  
    -   [PowerShell](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="what-is-the-ssdenoversion-service-the-ssnoversion-agent-service-and-the-ssnoversion-browser-service"></a><a name="Services"></a> ¿Qué es el servicio [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , el servicio Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y el servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser?  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] son programas ejecutables que funcionan como un servicio de Windows. Los programas que se ejecutan como servicio de Windows pueden seguir funcionando sin mostrar actividad alguna en la pantalla del equipo.  
  
 **[!INCLUDE[ssDE](../../includes/ssde-md.md)]servicio**  
 El proceso ejecutable que es [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. [!INCLUDE[ssDE](../../includes/ssde-md.md)] puede ser la instancia predeterminada (límite de una por equipo) o puede ser una de las numerosas instancias con nombre de [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Use el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para determinar las instancias de [!INCLUDE[ssDE](../../includes/ssde-md.md)] que están instaladas en el equipo. La instancia predeterminada (si la instala) aparece como ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER)**. Las instancias con nombre (si las instala) aparecen como ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (<instance_name>)**. De forma predeterminada, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express se instala como ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQLEXPRESS)**.  
  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Servicio del agente**  
 Servicio de Windows que ejecuta tareas administrativas programadas, denominadas trabajos y alertas. Para obtener más información, consulte [SQL Server Agent](../../ssms/agent/sql-server-agent.md). [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no está disponible en todas las ediciones de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para obtener una lista de las características admitidas por las ediciones de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vea [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Servicio Browser**  
 Servicio de Windows que escucha las solicitudes entrantes de recursos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y proporciona a los clientes información acerca de las instancias de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instaladas en el equipo. Una sola instancia del servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser se usa para todas las instancias de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instaladas en el equipo.  
  
###  <a name="additional-information"></a><a name="MoreInformation"></a>Información adicional  
  
-   Al pausar el servicio [!INCLUDE[ssDE](../../includes/ssde-md.md)] se impide que los nuevos usuarios se conecten a [!INCLUDE[ssDE](../../includes/ssde-md.md)], pero los que ya estén conectados pueden seguir trabajando hasta que sus conexiones se interrumpan. Use la pausa cuando desee esperar a que los usuarios completen su trabajo antes de detener el servicio. Esto les permite completar las transacciones que están en curso. La reanudación permite que [!INCLUDE[ssDE](../../includes/ssde-md.md)] vuelva a aceptar nuevas conexiones. El servicio Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no se puede pausar o reanudar.  
  
-   El Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] muestran el estado actual de los servicios mediante el uso de los siguientes iconos.  
  
     **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager**  
  
    -   La flecha verde del icono situado junto al nombre del servicio indica que el servicio está iniciado.  
  
    -   El cuadrado rojo del icono situado junto al nombre del servicio indica que el servicio está detenido.  
  
    -   Dos líneas azules verticales en el icono situado junto al nombre del servicio indica que el servicio está pausado.  
  
    -   Al reiniciar [!INCLUDE[ssDE](../../includes/ssde-md.md)], un cuadrado rojo indicará que el servicio se detuvo y una flecha verde indicará que el servicio se inició correctamente.  
  
     **[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
    -   La flecha blanca sobre un icono de círculo verde situado junto al nombre del servicio indica que el servicio está iniciado.  
  
    -   El cuadrado blanco sobre un icono de círculo rojo situado junto al nombre del servicio indica que el servicio está detenido.  
  
    -   Dos líneas blancas verticales sobre un icono de círculo azul situado junto al nombre del servicio indica que el servicio está pausado.  
  
-   Al usar el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], solo estarán disponibles las opciones que son posibles. Por ejemplo, si el servicio ya está iniciado, **Iniciar** no estará disponible.  
  
-   Al ejecutar en un clúster, el servicio [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] se administra mejor mediante el Administrador de clústeres.  
  
###  <a name="security"></a><a name="Security"></a> Seguridad  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permisos  
 De forma predeterminada, solo los miembros del grupo local de administradores pueden iniciar, detener, pausar, reanudar o reiniciar un servicio. Para conceder la capacidad de administrar servicios a usuarios que no son administradores, vea [CÓMO: Conceder a los usuarios derechos para administrar servicios en la familia Windows Server 2003](https://support.microsoft.com/kb/325349). El proceso es similar en las demás versiones de Windows.  
  
 La detención de [!INCLUDE[ssDE](../../includes/ssde-md.md)] mediante el [!INCLUDE[tsql](../../includes/tsql-md.md)] `SHUTDOWN` comando requiere la pertenencia a los roles fijos de servidor **sysadmin** o **ServerAdmin** , y no se pueden transferir.  
  
##  <a name="using-ssnoversion-configuration-manager"></a><a name="SSCMProcedure"></a> Usar el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-an-instance-of-the-ssdenoversion"></a>Para iniciar, detener, pausar, reanudar o reiniciar una instancia de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]  
  
1.  En el menú **Inicio** , elija **Todos los programas**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Herramientas de configuración**y, por último, **Administrador de configuración de SQL Server**.  
  
2.  Si aparece el cuadro de diálogo **Control de cuentas de usuario** , haga clic en **Sí**.  
  
3.  En el panel izquierdo del Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , haga clic en **Servicios de SQL Server**.  
  
4.  En el panel de resultados, haga clic con el botón derecho en **SQL Server (MSSQLServer)** o en una instancia con nombre y luego haga clic en **Iniciar**, **Detener**, **Pausar**, **Reanudar**o **Reiniciar**.  
  
5.  Haga clic en **Aceptar** para cerrar el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  Para iniciar una instancia de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] con opciones de inicio, vea [Configurar opciones de inicio del servidor &#40;Administrador de configuración de SQL Server&#41;](scm-services-configure-server-startup-options.md).  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-ssnoversion-browser-or-an-instance-of-the-ssnoversion-agent"></a>Para iniciar, detener, pausar, reanudar o reiniciar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser o una instancia de Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
1.  En el menú **Inicio** , elija **Todos los programas**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Herramientas de configuración**y, por último, **Administrador de configuración de SQL Server**.  
  
2.  Si aparece el cuadro de diálogo **Control de cuentas de usuario** , haga clic en **Sí**.  
  
3.  En el panel izquierdo del Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , haga clic en **Servicios de SQL Server**.  
  
4.  En el panel de resultados, haga clic con el botón derecho en ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorador**, o ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agente (MSSQLServer)** o ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agente (<instance_name>)** para una instancia con nombre y, a continuación, haga clic en **iniciar**, **detener**, **pausar**, **reanudar**o **reiniciar**.  
  
5.  Haga clic en **Aceptar** para cerrar el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  El Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no se puede pausar.  
  
##  <a name="using-ssnoversion-management-studio"></a><a name="SSMSProcedure"></a> Usar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-an-instance-of-the-ssdenoversion"></a>Para iniciar, detener, pausar, reanudar o reiniciar una instancia de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]  
  
1.  En el Explorador de objetos, conéctese a la instancia de [!INCLUDE[ssDE](../../includes/ssde-md.md)], haga clic con el botón derecho en la instancia de [!INCLUDE[ssDE](../../includes/ssde-md.md)] que quiere iniciar y luego haga clic en **Iniciar**, **Detener**, **Pausar**, **Reanudar**o **Reiniciar**.  
  
     O bien, en Servidores registrados, haga clic con el botón derecho en la instancia de [!INCLUDE[ssDE](../../includes/ssde-md.md)] que quiere iniciar, seleccione **Control de servicios**y, luego, haga clic en **Iniciar**, **Detener**, **Pausar**, **Reanudar**o **Reiniciar**.  
  
2.  Si aparece el cuadro de diálogo **Control de cuentas de usuario** , haga clic en **Sí**.  
  
3.  Cuando se le pregunte si desea realizar la acción, haga clic en **Sí**.  
  
#### <a name="to-start-stop-or-restart-the-an-instance-of-the-ssnoversion-agent"></a>Para iniciar, detener o reiniciar una instancia del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
1.  En Explorador de objetos, conéctese a la instancia de [!INCLUDE[ssDE](../../includes/ssde-md.md)] , haga clic con el botón secundario en ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agente**y, a continuación, haga clic en **iniciar**, **detener**o **reiniciar**.  
  
2.  Si aparece el cuadro de diálogo **Control de cuentas de usuario** , haga clic en **Sí**.  
  
3.  Cuando se le pregunte si desea realizar la acción, haga clic en **Sí**.  
  
##  <a name="from-the-command-prompt-window-using-net-commands"></a><a name="CommandPrompt"></a> Desde la ventana del símbolo del sistema con los comandos net  
 Los servicios de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se pueden iniciar, detener o pausar mediante comandos **net** de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
###  <a name="to-start-the-default-instance-of-the-ssde"></a><a name="dbDefault"></a> Para iniciar la instancia predeterminada de [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   En el símbolo del sistema, escriba uno de los siguientes comandos:  
  
     **net start "SQL Server (MSSQLSERVER)"**  
  
     O bien  
  
     **net start MSSQLSERVER**  
  
###  <a name="to-start-a-named-instance-of-the-ssde"></a><a name="dbNamed"></a> Para iniciar una instancia con nombre de [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   En el símbolo del sistema, escriba uno de los siguientes comandos. Sustituya *\<instancename>* por el nombre de la instancia que desea administrar.  
  
     **net start "SQL Server (** *instancename* **)"**  
  
     O bien  
  
     **net start MSSQL$** *instancename*  
  
###  <a name="to-start-the-ssde-with-startup-options"></a><a name="dbStartup"></a> Para iniciar [!INCLUDE[ssDE](../../includes/ssde-md.md)] con opciones de inicio  
  
-   Agregue las opciones de inicio al final de la instrucción **net start "SQL Server (MSSQLSERVER)"** , separadas por un espacio. Cuando se inicia mediante **net start**, las opciones de inicio usan una barra (/) en lugar de un guión (-).  
  
     **net start "SQL Server (MSSQLSERVER)" /f /m**  
  
     O bien  
  
     **net start MSSQLSERVER /f /m**  
  
    > [!NOTE]  
    >  Para obtener más información sobre las opciones de inicio del servicio, vea [Opciones de inicio del servicio de motor de base de datos](database-engine-service-startup-options.md).  
  
###  <a name="to-start-the-ssnoversion-agent-on-the-default-instance-of-ssnoversion"></a><a name="agDefault"></a> Para iniciar el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en la instancia predeterminada de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   En el símbolo del sistema, escriba uno de los siguientes comandos:  
  
     **net start "SQL Server Agent (MSSQLSERVER)"**  
  
     O bien  
  
     **net start SQLSERVERAGENT**  
  
###  <a name="to-start-the-ssnoversion-agent-on-a-named-instance-of-ssnoversion"></a><a name="agNamed"></a> Para iniciar el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en una instancia con nombre de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   En el símbolo del sistema, escriba uno de los siguientes comandos. Sustituya *instancename* por el nombre de la instancia que quiere administrar.  
  
     **net start "SQL Server Agent(** *instancename* **)"**  
  
     O bien  
  
     **net start SQLAgent$** *instancename*  
  
 Para obtener información sobre cómo ejecutar el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en modo detallado para la solución de problemas, vea [sqlagent90 (aplicación)](../../tools/sqlagent90-application.md).  
  
###  <a name="to-start-the-ssnoversion-browser"></a><a name="Browser"></a> Para iniciar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser  
  
-   En el símbolo del sistema, escriba uno de los siguientes comandos:  
  
     **net start "SQL Server Browser"**  
  
     O bien  
  
     **net start SQLBrowser**  
  
###  <a name="to-pause-or-stop-services-from-the-command-prompt-window"></a><a name="pauseStop"></a> Para pausar o detener los servicios desde la ventana del símbolo del sistema  
  
-   Para pausar o detener servicios, modifique los comandos de las formas que se indican a continuación.  
  
    -   Para pausar un servicio, reemplace **net start** por **net pause**.  
  
    -   Para detener un servicio, reemplace **net start** por **net stop**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Usar Transact-SQL  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] se puede detener mediante la instrucción `SHUTDOWN`.  
  
#### <a name="to-stop-the-ssde-using-tsql"></a>Para detener [!INCLUDE[ssDE](../../includes/ssde-md.md)] mediante [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
-   Para esperar a que finalicen las instrucciones [!INCLUDE[tsql](../../includes/tsql-md.md)] y los procedimientos almacenados que se encuentran en ejecución y, a continuación, detener [!INCLUDE[ssDE](../../includes/ssde-md.md)], ejecute la instrucción siguiente.  
  
    ```sql  
    SHUTDOWN;   
    ```  
  
-   Para detener [!INCLUDE[ssDE](../../includes/ssde-md.md)] inmediatamente, ejecute la instrucción siguiente.  
  
    ```sql  
    SHUTDOWN WITH NOWAIT;   
    ```  
  
 Para obtener más información acerca de la `SHUTDOWN` instrucción, vea [Shutdown &#40;TRANSACT-SQL&#41;](/sql/t-sql/language-elements/shutdown-transact-sql).  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Con PowerShell  
  
#### <a name="to-start-and-stop-ssde-services"></a>Para iniciar y detener servicios de [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
1.  En una ventana del símbolo del sistema, inicie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell con el comando siguiente.  
  
    ```ms-dos  
    sqlps  
    ```  
  
2.  En un símbolo del sistema de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ejecutando el comando siguiente. Reemplace `computername` por el nombre de su equipo.  
  
    ```powershell  
    # Get a reference to the ManagedComputer class.  
    CD SQLSERVER:\SQL\computername  
    $Wmi = (Get-Item .).ManagedComputer
    ```  
  
3.  Identifique el servicio que desea detener o iniciar. Elija una de las líneas siguientes. Reemplace `instancename` por el nombre de la instancia con nombre.  
  
    -   Para obtener una referencia a la instancia predeterminada de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['MSSQLSERVER']  
        ```  
  
    -   Para obtener una referencia a una instancia con nombre de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['MSSQL$instancename']  
        ```  
  
    -   Para obtener una referencia al servicio Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en la instancia predeterminada de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLSERVERAGENT']  
        ```  
  
    -   Para obtener una referencia al servicio Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en una instancia con nombre de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLAGENT$instancename']  
        ```  
  
    -   Para obtener una referencia al servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser.  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLBROWSER']  
        ```  
  
4.  Complete el ejemplo para iniciar y detener el servicio seleccionado.  
  
    ```powershell  
    # Display the state of the service.  
    $DfltInstance  
    # Start the service.  
    $DfltInstance.Start();  
    # Wait until the service has time to start.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    # Stop the service.  
    $DfltInstance.Stop();  
    # Wait until the service has time to stop.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    ```  
  
## <a name="see-also"></a>Consulte también  
 [Iniciar SQL Server con la configuración mínima](start-sql-server-with-minimal-configuration.md)   
 [Características admitidas por las ediciones de SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
