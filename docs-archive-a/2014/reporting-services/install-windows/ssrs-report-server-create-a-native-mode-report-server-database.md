---
title: Crear una base de datos del servidor de informes de modo nativo (Administrador de configuración de SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], databases
- databases [Reporting Services], creating
ms.assetid: 81b9f4ad-800b-4688-8b47-a5a83dc8ff10
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 06ad4afe3b8d70899d7299f3b4eb7b97eef6ab66
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751825"
---
# <a name="create-a-native-mode-report-server-database--ssrs-configuration-manager"></a>Crear una base de datos del servidor de informes de modo nativo (Administrador de configuración de SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de modo nativo usa una base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para el almacenamiento interno. La base de datos es un componente necesario y se utiliza para almacenar los informes publicados, modelos, orígenes de datos compartidos, datos de sesión, recursos y metadatos del servidor.  
  
 Para crear una base de datos del servidor de informes o cambiar la cadena de conexión o las credenciales, utilice las opciones de la página Base de datos del Administrador de configuración de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Modo nativo|  
  
## <a name="when-to-create-or-configure-the-report-server-databases"></a>Cuándo crear o configurar la base de datos del servidor de informes  
 Debe crear y configurar la base de datos del servidor de informes si lo instaló en el modo de solo archivos.  
  
 Si instaló [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] con la configuración predeterminada para el modo nativo, la base de datos del servidor de informes se creó y configuró automáticamente cuando se instaló la instancia del servidor de informes. Puede utilizar el Administrador de configuración de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] para ver o modificar los valores que el programa de configuración estableció automáticamente.  
  
##  <a name="before-you-start"></a><a name="rsdbrequirements"></a> Antes de empezar  
 La creación o configuración de una base de datos del servidor de informes son procesos que constan de varios pasos. Antes de crear la base de datos del servidor de informes, considere cómo desea especificar los elementos siguientes:  
  
 Seleccionar un servidor de base de datos  
 Revise las versiones compatibles de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] y revise las ediciones compatibles en el tema [Crear una base de datos del servidor de informes &#40;Administrador de configuración de SSRS&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md).  
  
 Habilitar las conexiones TCP/IP  
 Habilite las conexiones TCP/IP para el [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Algunas ediciones de [!INCLUDE[ssDE](../../includes/ssde-md.md)] no habilitan TCP/IP de forma predeterminada. En este tema se proporcionan instrucciones al respecto.  
  
 Abrir el puerto para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 En un servidor remoto, si usa software de firewall, debe abrir el puerto en el que [!INCLUDE[ssDE](../../includes/ssde-md.md)] escucha.  
  
 Decidir las credenciales del servidor de informes  
 Decida cómo se conectará el servidor de informes a las bases de datos del servidor de informes. Los tipos de credenciales incluyen la cuenta de dominio, la cuenta de usuario de base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o la cuenta del servicio Servidor de informes.  
  
 Estas credenciales se cifran y almacenan en el archivo RSReportServer.config. El servidor de informes usa estas credenciales para las conexiones salientes a la base de datos del servidor de informes. Si desea utilizar una cuenta de usuario de Windows o una cuenta de usuario de base de datos, asegúrese de especificar una que ya exista. Aunque el Administrador de configuración de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] creará un inicio de sesión y establecerá los permisos necesarios, no creará una cuenta para usted. Para obtener más información, vea [configurar una conexión de base de datos del servidor de informes &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 Decidir un idioma para el servidor de informes  
 Elija el idioma que se especificará para el servidor de informes. Los nombres de roles predefinidos, las descripciones y las carpetas Mis informes no aparecen en idiomas diferentes cuando los usuarios se conectan al servidor con las distintas versiones de un explorador en varios idiomas.  
  
 Comprobar las credenciales para crear y proporcionar la base de datos  
 Compruebe que tiene las credenciales de la cuenta que tengan permiso para crear bases de datos en la instancia de [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Estas credenciales se usan para una conexión esporádica con el fin de crear la base de datos del servidor de informes y **RSExecRole**. Si no existe aún un inicio de sesión, se creará un inicio de sesión de usuario de base de datos para la cuenta que use el servidor de informes para conectarse a la base de datos. Puede conectarse con la cuenta de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows en la que haya iniciado sesión o puede especificar un inicio de sesión de base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="to-enable-access-to-a-remote-report-server-database"></a>Para habilitar el acceso a una base de datos remota del servidor de informes  
  
1.  Si está utilizando una instancia de [!INCLUDE[ssDE](../../includes/ssde-md.md)] remota, inicie sesión en el servidor de bases de datos para comprobar o habilitar las conexiones TCP/IP.  
  
2.  Seleccione **Inicio**, **Todos los programas**, **Microsoft SQL Server**y **Herramientas de configuración**, y a continuación haga clic en **Administrador de configuración de SQL Server**.  
  
3.  Abra **SQL Server configuración de red**.  
  
4.  Seleccione la instancia.  
  
5.  Haga clic con el botón secundario en **TCP/IP** y haga clic en **habilitado**.  
  
6.  Reinicie el servicio.  
  
7.  Abra el software de firewall y abra el puerto en el que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] escucha. Para la instancia predeterminada, suele ser el puerto 1433 de las conexiones TCP/IP. Para obtener más información, vea [Configurar Firewall de Windows para el acceso al motor de base de datos](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) en los Libros en pantalla de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="to-create-a-local-report-server-database"></a>Crear una base de datos del servidor de informes local  
  
1.  Inicie el Administrador de configuración de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] y conéctese a la instancia del servidor de informes para la que va a crear la base de datos. Para obtener más información, vea [Administrador de configuración de Reporting Services &#40;modo nativo&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
2.  En la página Base de datos, haga clic en **Cambiar base de datos**.  
  
3.  Haga clic en **crear una nueva base de datos del servidor de informes**y, a continuación, en **siguiente**.  
  
4.  Conéctese a la instancia del [!INCLUDE[ssDE](../../includes/ssde-md.md)] que va a usar para crear y hospedar la base de datos del servidor de informes:  
  
    1.  Escriba la instancia de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] que desea utilizar. El asistente mostrará un [!INCLUDE[ssDE](../../includes/ssde-md.md)] local que se ejecuta como instancia predeterminada, si está disponible. De lo contrario, debe escribir el servidor y la instancia que va a utilizar. Las instancias con nombre se especifican en este formato: \<servername> \\<InstanceName \> .  
  
    2.  Escriba las credenciales que se usan para una conexión esporádica al [!INCLUDE[ssDE](../../includes/ssde-md.md)] con el propósito de crear las bases de datos del servidor de informes. Para obtener más información sobre cómo se utilizan estas credenciales, vea [Antes de empezar](#rsdbrequirements) en este tema.  
  
    3.  Haga clic en **Probar conexión** para validar la conexión al servidor.  
  
    4.  Haga clic en **Next**.  
  
5.  Especifique las propiedades que se usan para crear la base de datos. Para obtener más información acerca de cómo se utilizan estas propiedades, vea [Antes de empezar](#rsdbrequirements) en este tema:  
  
    1.  Escriba el nombre de la base de datos de servidor de informes. Se crea una base de datos temporal junto con la base de datos principal. Considere utilizar un nombre descriptivo para ayudarle a recordar cómo se utiliza la base de datos. Tenga en cuenta que el nombre que especifique se utilizará durante la duración de la base de datos. No puede cambiar el nombre de una base de datos del servidor de informes una vez creada.  
  
    2.  Seleccione el idioma en el que desea que aparezcan las definiciones de roles y Mis informes.  
  
    3.  El modo de servidor de informes siempre está establecido en **Nativo**.  
  
    4.  Haga clic en **Next**.  
  
6.  Especifique las credenciales que usa el servidor de informes para conectarse a la base de datos del servidor de informes.  
  
    1.  Especifique el tipo de autenticación:  
  
         Seleccione **Credenciales de base de datos** para conectarse con un inicio de sesión de base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que ya esté definido. Se recomienda utilizar las credenciales de base de datos si el servidor de informes está en un equipo que se encuentra en un dominio diferente, un dominio que no sea de confianza o detrás de un firewall.  
  
         Seleccione **Credenciales de Windows** si tiene una cuenta de usuario de dominio con privilegios mínimos que tenga permiso para iniciar sesión en el equipo y en el servidor de bases de datos.  
  
         Seleccione **Credenciales de servicio** si desea que el servidor de informes se conecte con su cuenta de servicio. Con esta opción, el servidor se conecta utilizando la seguridad integrada; las credenciales no se cifran ni almacenan.  
  
    2.  Haga clic en **Next**.  
  
7.  Revise la información de la página Resumen para comprobar que la configuración es correcta y, a continuación, haga clic en **Siguiente**.  
  
8.  Compruebe la conexión haciendo clic en una dirección URL en las páginas Dirección URL del servidor de informes o Dirección URL del Administrador de informes. Las direcciones URL deben estar definidas para que esta prueba funcione. Si la conexión de base de datos del servidor de informes es válida, verá la jerarquía de carpetas del servidor de informes o el Administrador de informes en una ventana del explorador. Para obtener más información, vea [Comprobar una instalación de Reporting Services](verify-a-reporting-services-installation.md) en los Libros en pantalla de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Consulte también  
 [Configurar una conexión a la base de datos del servidor de informes &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Base de datos &#40;modo nativo de SSRS&#41;](../../sql-server/install/database-ssrs-native-mode.md)   
 [Administrar un servidor de informes en modo nativo Reporting Services](../report-server/manage-a-reporting-services-native-mode-report-server.md)   
 [Administrador de configuración de Reporting Services &#40;modo nativo&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
