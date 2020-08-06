---
title: Configuración del área expuesta | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- reducing attackable surface area
- upgrading SQL Server, security
- surface area configuration [SQL Server]
- surface area configuration [SQL Server], about surface area configuration
- attackable surface area [SQL Server]
- installing SQL Server, security
ms.assetid: f741169c-1453-4ad2-830b-bf2be27d712f
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ef64fbbeb2b8953ff3816db63572b499d42f012e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745108"
---
# <a name="surface-area-configuration"></a>Configuración de Área expuesta
  Con la configuración predeterminada de nuevas instalaciones de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], no se habilitan muchas de las características. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instala selectivamente y solo inicia servicios y características claves para minimizar el número de características que pueden ser atacadas por un usuario malintencionado. Un administrador del sistema puede cambiar esta configuración predeterminada en el momento de la instalación y puede habilitar o deshabilitar de forma selectiva las características de una instancia en ejecución de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Además, algunos componentes no pueden estar disponibles al conectar desde otros equipos hasta que se configuren los protocolos.  
  
> [!NOTE]  
>  A diferencia de las nuevas instalaciones, los servicios o características existentes no se desactivan durante una actualización, pero las opciones de configuración adicionales de área expuesta pueden aplicarse una vez completada la actualización.  
  
## <a name="protocols-connection-and-startup-options"></a>Opciones de protocolo, conexión e inicio  
 Utilice el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para iniciar y detener servicios, configurar opciones de inicio, y habilitar protocolos y otras opciones de conexión.  
  
#### <a name="to-start-sql-server-configuration-manager"></a>Para iniciar el Administrador de configuración de SQL Server  
  
1.  En el menú **Inicio** , elija **Todos los programas**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Herramientas de configuración**y, por último, **Administrador de configuración de SQL Server**.  
  
    -   Utilice el área **Servicios de SQL Server** para iniciar los componentes y configurar las opciones de inicio automáticas.  
  
    -   Use el área **Configuración de red de SQL Server** para habilitar protocolos de conexión y opciones de conexión tales como los puertos TCP/IP fijos o para forzar el cifrado.  
  
 Para obtener más información, vea [SQL Server Configuration Manager](../sql-server-configuration-manager.md). La conectividad remota también puede depender de la configuración correcta de un firewall. Para más información, consulte [Configurar Firewall de Windows para permitir el acceso a SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
## <a name="enabling-and-disabling-features"></a>Habilitar y deshabilitar características  
 Habilitar y deshabilitar características [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se puede configurar utilizando facetas en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-configure-surface-area-using-facets"></a>Para configurar área expuesta mediante facetas  
  
1.  En [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] , conecte con un componente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  En el Explorador de objetos, haga clic con el botón derecho en el servidor y, luego, haga clic en **Facetas**.  
  
3.  En el cuadro de diálogo **Ver facetas** , expanda la lista **Faceta** y seleccione la faceta **Configuración de área expuesta** apropiada (**Configuración de área expuesta**, **Configuración de área expuesta para Analysis Services**o **Configuración de área expuesta para Reporting Services**).  
  
4.  En el área **Propiedades de faceta** , seleccione los valores que desee para cada propiedad.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 Para comprobar periódicamente la configuración de una faceta, use la Administración basada en directivas. Para obtener más información sobre la administración basada en directivas, vea [Administrar servidores mediante administración basada en directivas](../policy-based-management/administer-servers-by-using-policy-based-management.md).  
  
 También puede establecer opciones de [!INCLUDE[ssDE](../../includes/ssde-md.md)] mediante el procedimiento almacenado `sp_configure`. Para obtener más información, vea [Opciones de configuración de servidor &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
 Para cambiar la propiedad **EnableIntegrated Security** de [!INCLUDE[ssRS](../../includes/ssrs.md)], utilice la configuración de las propiedades de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Para cambiar la propiedad **Eventos de programación y entrega de informes habilitados** y la propiedad **Acceso HTTP y de servicios Web** , modifique el archivo de configuración **RSReportServer.config** .  
  
## <a name="command-prompt-options"></a>Opciones del símbolo del sistema  
 Use el cmdlet **Invoke-PolicyEvaluation** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell para invocar Directivas de configuración de área expuesta. Para obtener más información, vea [Utilizar los cmdlets del motor de base de datos](../../database-engine/use-the-database-engine-cmdlets.md).  
  
## <a name="soap-and-service-broker-endpoints"></a>Extremos SOAP y de Service Broker  
 Para desactivar los extremos, use la Administración basada en directivas. Para crear y modificar las propiedades de los puntos de conexión, use [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) y [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).  
  
## <a name="related-content"></a>Contenido relacionado  
 [Centro de seguridad para el Motor de base de datos de SQL Server y Azure SQL Database](security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
