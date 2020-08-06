---
title: Opciones de configuración de Reporting Services (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.ins.instwizard.reportserverinstoptions.f1
helpviewer_keywords:
- Report Server Installation Options page [SQL Server Installation Wizard]
- report servers [Reporting Services], installing
- SQL Server Installation Wizard, Report Server Installation Options page
ms.assetid: e4561f6c-bc7f-467e-821a-cde8e5cd7391
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 8d76701cab2c8cd8141241651d3e771ba4114504
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672454"
---
# <a name="reporting-services-configuration-options-ssrs"></a>Opciones de configuración de Reporting Services (SSRS)
  Use la página **Configuración de Reporting Services** del Asistente para la instalación de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para especificar la forma en que se instala y configura un servidor de informes. La disponibilidad de una opción de instalación depende de las opciones que se seleccionaron en la página **Selección de características** y de si también se está instalando una instancia local del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] al mismo tiempo que se instala el servidor de informes.  
  
 En algunos casos, si un certificado de Capa de sockets seguros (SSL) se instala en el equipo y se enlaza a un carácter comodín seguro, el programa de instalación creará las direcciones URL de Reporting Services usando el prefijo HTTPS. Para obtener más información sobre cómo se asignan los certificados a las direcciones URL de Reporting Services, vea [configurar un servidor de informes para conexiones capa de sockets seguros (SSL)](https://go.microsoft.com/fwlink/?LinkId=199089) ( https://go.microsoft.com/fwlink/?LinkId=199089) en libros en pantalla de SQL Server.  
  
 Para obtener la información más reciente relacionada con [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] y la instalación y configuración de esta versión, vea [información adicional sobre la instalación](https://go.microsoft.com/fwlink/?LinkId=207425) ( https://go.microsoft.com/fwlink/?LinkId=207425) .  
  
## <a name="options"></a>Opciones  
  
### <a name="reporting-services-native-mode"></a>Modo nativo de Reporting Services  
 Si el programa de instalación no puede realizar una configuración predeterminada del servidor de informes porque no se cumplen uno o más requisitos, el Asistente para la instalación solo permitirá la opción mínima de instalación; copiará los archivos que necesita, pero le obligará a usar el Administrador de configuración de Reporting Services para configurar un servidor de informes en modo nativo una vez completada la instalación.  
  
> [!NOTE]  
>  Un archivo de base de datos del servidor de informes existente puede provocar un error en la instalación si elige una de las opciones de instalación predeterminadas. Cuando elige la opción de instalación predeterminada, el programa de instalación intenta crear una base de datos de servidor de informes empleando el nombre predeterminado. Si ya existe una base de datos con ese nombre, se producirá un error en la instalación y tendrá que revertirla. Para evitar este problema, puede cambiar el nombre de la base de datos existente antes de ejecutar la instalación o elegir la opción **Solo instalar** para poder especificar la configuración personalizada de la base de datos una vez terminada la instalación.  
  
#### <a name="install-and-configure"></a>Instalar y configurar  
 Instala una instancia del servidor de informes en modo nativo con los valores predeterminados para las bases de datos, la cuenta de servicio y las reservas de direcciones URL del servidor de informes. Si elige esta opción, la instancia del servidor de informes estará lista para ser utilizada una vez finalizada la instalación. El programa de instalación crea la base de datos del servidor de informes utilizando una instancia de [!INCLUDE[ssDE](../../includes/ssde-md.md)] local y configura un servidor de informes para que utilice valores predeterminados.  
  
 Esta opción solo está disponible si los valores predeterminados utilizados en una instalación del servidor de informes son válidos para el sistema. Esta opción es recomendable para programadores que deseen instalar todos los componentes localmente y para usuarios que estén evaluando el software.  
  
 Para ver información sobre la configuración predeterminada que utiliza el programa de instalación, o para conocer los motivos por los que no se puede instalar la configuración predeterminada, haga clic en **Detalles**. Para obtener más información acerca de la configuración predeterminada para un servidor de informes en modo nativo, vea [configuración predeterminada para una instalación en modo nativo (Reporting Services)](https://go.microsoft.com/fwlink/?LinkId=199091) ( https://go.microsoft.com/fwlink/?LinkId=199091) .  
  
#### <a name="install-only"></a>Solo instalar  
 Instala los archivos de programa del servidor de informes, crea la cuenta del servicio Servidor de informes y registra el proveedor de Instrumental de administración de Windows (WMI) del servidor de informes. Esta opción de instalación se denomina instalación de "solo archivos". Seleccione esta opción si no desea utilizar la configuración predeterminada. Si no se puede instalar la configuración predeterminada, o si está instalando un clúster de conmutación por error de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que incluye [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], ésta es la única opción disponible. Para obtener más información sobre la instalación de solo archivos, vea [instalación de solo archivos (Reporting Services)](https://go.microsoft.com/fwlink/?LinkId=199093) ( https://go.microsoft.com/fwlink/?LinkId=199093) .  
  
 Una vez finalizada la instalación, deberá crear la base de datos del servidor de informes y configurar el servidor de informes antes de utilizarla. Para configurar un servidor de informes y crear la base de datos, utilice el Administrador de configuración de Reporting Services. Para obtener más información, vea [Cómo: crear una base de datos del servidor de informes (configuración de Reporting Services)](https://go.microsoft.com/fwlink/?LinkId=199094) ( https://go.microsoft.com/fwlink/?LinkId=199094) y [configurar una conexión de base de datos del servidor de informes](https://go.microsoft.com/fwlink/?LinkId=199095) () https://go.microsoft.com/fwlink/?LinkId=199095) .  
  
### <a name="reporting-services-sharepoint-mode"></a>Modo de SharePoint de Reporting Services  
  
#### <a name="install-only"></a>Solo instalar  
 Instala los archivos de programa del servidor de informes y los cmdlets de PowerShell. Una vez completada la instalación, necesitará iniciar los servicios de SharePoint de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] y crear una aplicación de servicio de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Para obtener más información, vea:  
  
-   [Instalar Reporting Services servidor de informes en modo de SharePoint para Power View y alertas de datos](https://go.microsoft.com/fwlink/?LinkId=207543) ( https://go.microsoft.com/fwlink/?LinkId=207543) .  
  
-   [Instale Reporting Services modo de SharePoint como una sola granja de servidores](https://go.microsoft.com/fwlink/?LinkId=207544) ( https://go.microsoft.com/fwlink/?LinkId=207544) .  
  
-   [Reporting Services servidor de informes (SSRs)](https://go.microsoft.com/fwlink/?LinkID=207244) ( https://go.microsoft.com/fwlink/?LinkID=207244) .  
  
## <a name="installing-the-reporting-services-add-in-for-sharepoint-technologies"></a>Instalar el complemento Reporting Services para tecnologías de SharePoint  
 A partir de la versión de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , el complemento se puede instalar como parte de la instalación de SQL Server, en la página de selección de características del asistente para la instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 No obstante, puede instalar el Complemento [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] para SharePoint 2010 mediante uno de los métodos siguientes:  
  
-   Ejecute la herramienta **PreRequisiteInstaller.exe**de preparación de productos de SharePoint 2010.  
  
-   Realice la instalación desde el medio de instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Haga clic en el archivo **rsSharePoint.msi** de la carpeta Setup del medio de instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] una vez completada la instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Descargue e instale el complemento. Para obtener más información, consulte [dónde encontrar el complemento de Reporting Services para productos de SharePoint](https://go.microsoft.com/fwlink/?LinkID=208634) ( https://go.microsoft.com/fwlink/?LinkID=208634) .  
  
## <a name="see-also"></a>Consulte también  
 [Inicio Administrador de configuración de Reporting Services](https://go.microsoft.com/fwlink/?LinkId=199096)   
 [Crear una base de datos del servidor de informes (configuración Reporting Services)](https://go.microsoft.com/fwlink/?LinkId=199094)   
 [Actualizar y migrar Reporting Services](https://go.microsoft.com/fwlink/?LinkID=245628)   
 [Instalación desde el símbolo del sistema del modo de SharePoint y el modo nativo de Reporting Services](https://go.microsoft.com/fwlink/?LinkId=217620)  
  
  
