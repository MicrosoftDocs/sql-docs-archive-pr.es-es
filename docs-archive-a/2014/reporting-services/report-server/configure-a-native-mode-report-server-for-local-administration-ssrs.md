---
title: Configurar un servidor de informes en modo nativo para la administración local (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- UAC
- installing Reporting Services
- Windows Vista
- Localhost
- windows server 2008
- Vista
ms.assetid: 312c6bb8-b3f7-4142-a55f-c69ee15bbf52
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ad53f293ef825a382d9e39b58527a36ef291687a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674601"
---
# <a name="configure-a-native-mode-report-server-for-local-administration-ssrs"></a>Configurar un servidor de informes en modo nativo para la administración local (SSRS)
  La implementación de un servidor de informes de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en uno de los sistemas operativos siguientes requiere más pasos de configuración si desea administrar la instancia del servidor de informes localmente. En este tema, se describe cómo configurar el servidor de informes para la administración local. Si aún no ha instalado o configurado el servidor de informes, vea [instalar SQL Server 2014 desde el Asistente para la instalación &#40;&#41;de instalación](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) y [Administración de un servidor de informes en modo nativo de Reporting Services](manage-a-reporting-services-native-mode-report-server.md).  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** Modo nativo de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
  
-   [!INCLUDE[winblue_server_2](../../includes/winblue-server-2-md.md)]  
  
-   [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]  
  
-   [!INCLUDE[win8](../../includes/win8-md.md)]  
  
-   [!INCLUDE[win8srv](../../includes/win8srv-md.md)]  
  
-   [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]  
  
-   [!INCLUDE[win7](../../includes/win7-md.md)]  
  
-   [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)]  
  
 Puesto que los sistemas operativos indicados limitan los permisos, los miembros del grupo local Administradores ejecutan la mayoría de las aplicaciones como si usaran la cuenta de usuario estándar.  
  
 Aunque esta práctica mejora la seguridad global del sistema, impide que utilice las asignaciones de roles predefinidas e integradas que Reporting Services crea para los administradores locales.  
  
-   [Información general de los cambios de configuración](#bkmk_configuraiton_overview)  
  
-   [Para configurar el servidor de informes local y la administración del Administrador de informes](#bkmk_configure_local_server)  
  
-   [Para configurar SQL Server Management Studio (SSMS) para la administración del servidor de informes local](#bkmk_configure_ssms)  
  
-   [Para configurar SQL Server Data Tools BI (SSDT) para publicar en un servidor de informes local](#bkmk_configure_ssdt)  
  
-   [Información adicional](#bkmk_addiitonal_informaiton)  
  
##  <a name="overview-of-configuration-changes"></a><a name="bkmk_configuraiton_overview"></a>Información general de los cambios de configuración  
 Los cambios de configuración siguientes configuran el servidor de forma que pueda usar los permisos de usuario estándar para administrar el contenido y las operaciones del servidor de informes:  
  
-   Agrega direcciones URL de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] a los sitios de confianza. De forma predeterminada, cuando Internet Explorer se ejecuta en los sistemas operativos enumerados lo hace en **Modo protegido**, una característica que impide que las solicitudes del explorador lleguen a los procesos de alto nivel que se ejecutan en el mismo equipo. Puede deshabilitar el modo protegido para las aplicaciones del servidor de informes agregándolas como sitios de confianza.  
  
-   Crea asignaciones de roles que le conceden, como administrador del servidor de informes, permiso para administrar el contenido y las operaciones sin tener que utilizar la característica **Ejecutar como administrador** de Internet Explorer. Mediante la creación de asignaciones de roles para su cuenta de usuario de Windows, obtiene acceso a un servidor de informes con los permisos Administrador de contenido y Administrador del sistema a través de las asignaciones de roles explícitas que reemplazan a las asignaciones de roles predefinidas e integradas, que Reporting Services crea.  
  
##  <a name="to-configure-local-report-server-and-report-manager-administration"></a><a name="bkmk_configure_local_server"></a>Para configurar el servidor de informes local y la administración de Administrador de informes  
 Complete los pasos de configuración de esta sección si va a examinar un servidor de informes local y ve errores similares a los siguientes:  
  
-   El usuario `'Domain\[user name]`' no tiene los permisos requeridos. Compruebe que se han concedido suficientes permisos y que se han tratado las restricciones del control de cuentas de usuario (UAC) de Windows.  
  
###  <a name="trusted-site-settings-in-the-browser"></a><a name="bkmk_site_settings"></a>Configuración del sitio de confianza en el explorador  
  
1.  Abra una ventana del explorador con los permisos Ejecutar como administrador. En el menú **Inicio** , haga clic en **Todos los programas**, haga clic con el botón derecho en **Internet Explorer**y seleccione **Ejecutar como administrador**.  
  
2.  Haga clic en **Permitir** para continuar.  
  
3.  En la dirección URL, escriba la dirección URL del Administrador de informes. Para obtener instrucciones, vea [Administrador de informes &#40;Modo nativo de SSRS&#41;](../report-manager-ssrs-native-mode.md) en los Libros en pantalla de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
4.  Haga clic en **Herramientas**.  
  
5.  Haga clic en **Opciones de Internet**.  
  
6.  Haga clic en **Seguridad**.  
  
7.  Haga clic en **Sitios de confianza**.  
  
8.  Haga clic en **Sitios**.  
  
9. Agregue `http://<your-server-name>`.  
  
10. Desactive la casilla **Requerir comprobación del servidor (https:) para todos los sitios de esta zona** si no usa HTTP en el sitio predeterminado.  
  
11. Haga clic en **Agregar**.  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
###  <a name="report-manager-folder-settings"></a><a name="bkmk_configure_folder_settings"></a> Configuración de carpeta del Administrador de informes  
  
1.  En el Administrador de informes, en la página Inicio, haga clic en **Configuración de carpeta**.  
  
2.  En la página Configuración de carpeta, haga clic en **Seguridad**.  
  
3.  Haga clic en **Nueva asignación de roles**.  
  
4.  En el campo **Nombre de grupo o de usuario** , escriba su cuenta de usuario de Windows en este formato: `<domain>\<user>`.  
  
5.  Seleccione **Administrador de contenido**.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
###  <a name="report-manager-site-settings"></a><a name="bkmk_configure_site_settings"></a> Configuración del sitio del Administrador de informes  
  
1.  Abra el explorador con privilegios administrativos y vaya al administrador de informes, `http://<server name>/reports`.  
  
2.  Haga clic en **Configuración del sitio** en la esquina superior de la página Inicio.  
  
    > [!TIP]  
    >  **Nota** : si no ve la opción **Configuración del sitio** , cierre y vuelva a abrir el explorador y vaya al Administrador de informes con privilegios administrativos.  
  
3.  Haga clic en **seguridad**.  
  
4.  Haga clic en **Nueva asignación de roles**.  
  
5.  En el campo **Nombre de grupo o de usuario** , escriba su cuenta de usuario de Windows en este formato: `<domain>\<user>`.  
  
6.  Seleccione **Administrador del sistema**.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  Cierre el Administrador de informes.  
  
9. Vuelva a abrir el Administrador de informes en Internet Explorer, sin usar **Ejecutar como administrador**.  
  
##  <a name="to-configure-sql-server-management-studio-ssms-for-local-report-server-administration"></a><a name="bkmk_configure_ssms"></a>Para configurar SQL Server Management Studio (SSMS) para la administración del servidor de informes local  
 De forma predeterminada, no puede tener acceso a todas las propiedades del servidor de informes disponibles en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] a menos que inicie [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] con privilegios administrativos.  
  
 **Para configurar asignaciones de roles de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]** no es necesario iniciar [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] con permisos elevados todas las veces:  
  
-   En el menú **Inicio** , haga clic en **Todos los programas**y en **SQL Server 2014**, haga clic con el botón derecho en **[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]** y luego haga clic en **Ejecutar como administrador**.  
  
-   Conéctese al servidor local de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
-   En el nodo **Seguridad** , haga clic en **Roles del sistema**.  
  
-   Haga clic con el botón derecho en **Administrador del sistema** y, después, haga clic en **Propiedades**.  
  
-   En la página **Propiedades de rol del sistema** , seleccione **Ver propiedades del servidor de informes**. Seleccione todas las demás propiedades que desee asociar a miembros del rol de administradores del sistema.  
  
-   Haga clic en **OK**.  
  
-   Cerrar [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]  
  
-   Para agregar un usuario al rol del sistema "administrador del sistema", vea la anterior sección [Configuración del sitio del Administrador de informes](#bkmk_configure_site_settings) en este tema.  
  
 Ahora, cuando abra [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] y no seleccione explícitamente **Ejecutar como administrador** tendrá acceso a las propiedades del servidor de informes.  
  
##  <a name="to-configure-sql-server-data-tools-bi-ssdt-to-publish-to-a-local-report-server"></a><a name="bkmk_configure_ssdt"></a>Para configurar SQL Server Data Tools BI (SSDT) para publicar en un servidor de informes local  
 Si instaló [!INCLUDE[SSDTDev11](../../includes/ssdtdev11-md.md)] en uno de los sistemas operativos enumerados en la primera sección de este tema y desea que SSDT interactúe con un servidor de informes local en modo nativo, aparecerán errores con los permisos a menos que abra [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] con permisos elevados o que configure roles de Reporting Services. Por ejemplo, si no tiene los permisos necesarios, encontrará problemas similares a los siguientes:  
  
-   Cuando intenta implementar elementos de informe en el servidor de informes local, aparece un mensaje de error similar al siguiente en la ventana **Lista de errores** :  
  
    -   Los permisos otorgados al usuario "Dominio\\<nombre de usuario\>" son insuficientes para realizar esta operación.  
  
 **Para ejecutar SSDT con permisos elevados cada vez que lo abre:**  
  
1.  En la pantalla Inicio, escriba `sql server` y, a continuación, haga clic con el botón derecho en **SQL Server Data Tools para Visual Studio**. Haga clic en **Ejecutar como administrador**  
  
     **O bien**, en sistemas operativos anteriores:  
  
     En el menú **Inicio** , haga clic en **Todos los programas**y en **SQL Server 2014**, haga clic con el botón derecho en **Herramientas de datos de SQL Server**y luego haga clic en **Ejecutar como administrador**.  
  
2.  Haga clic en **Continuar**.  
  
3.  Haga clic en **Ejecutar programa**.  
  
 Ahora debe poder implementar informes y otros elementos en un servidor de informes local.  
  
 **Para configurar asignaciones de roles de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] no es necesario iniciar SSDT con permisos elevados todas las veces:**  
  
-   Vea las secciones [Configuración de carpeta del Administrador de informes](#bkmk_configure_folder_settings) y [Configuración del sitio del Administrador de informes](#bkmk_configure_site_settings) anteriores de este tema.  
  
##  <a name="additional-information"></a><a name="bkmk_addiitonal_informaiton"></a>Información adicional  
 Un paso de configuración frecuente adicional relacionado con la administración de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] consiste en abrir el puerto 80 en Firewall de Windows para permitir el acceso al equipo servidor de informes. Para obtener instrucciones, consulte [Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md).  
  
## <a name="see-also"></a>Consulte también  
 [Administración de un servidor de informes en modo nativo de Reporting Services](manage-a-reporting-services-native-mode-report-server.md)  
  
  
