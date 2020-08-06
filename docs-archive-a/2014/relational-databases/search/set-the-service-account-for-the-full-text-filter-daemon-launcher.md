---
title: Establecer la cuenta del servicio para el selector del demonio de filtro completo | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], FDHOST Launcher (MSSQLFDLauncher) service account
- FDHOST Launcher (MSSQLFDLauncher) [SQL Server]
ms.assetid: 3ab1d101-7ae0-488f-9b57-468e2517b737
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d69e68f0b00e760c4b11d1f842f22911ac8dd2c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669573"
---
# <a name="set-the-service-account-for-the-full-text-filter-daemon-launcher"></a>Establecer la cuenta del servicio para el selector del demonio de filtro completo
  En este tema se describe cómo establecer la cuenta de servicio para el servicio Selector del demonio de filtro de texto completo de SQL Server (MSSQLFDLauncher) mediante el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . La búsqueda de texto completo ssNoVersion usa el servicio Selector de demonio de filtro de texto completo de SQL para iniciar el proceso de host de demonio de filtro, que administra las operaciones de filtrado y separación de palabras de la búsqueda de texto completo. Este servicio debe estar ejecutándose para poder utilizar la búsqueda de texto completo.  
  
 El servicio Selector del demonio de filtro de texto completo de SQL Server es un servicio que reconoce instancias y que está asociado a una instancia específica de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. El servicio Selector de demonio de filtro de texto completo de SQL propaga la información de la cuenta de servicio a cada proceso de host de demonio de filtro.  
  
  
##  <a name="setting-the-service-account"></a><a name="setting"></a>Establecimiento de la cuenta de servicio  
  
#### <a name="to-set-the-sql-full-text-filter-daemon-launcher-service-account-for-full-text-search"></a>Para establecer la cuenta del servicio Selector del demonio de filtro de texto completo de SQL Server para la búsqueda de texto completo  
  
1.  En el menú **Inicio** , elija **Todos los programas**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Herramientas de configuración**y, por último, **Administrador de configuración de SQL Server**.  
  
2.  En **Administrador de configuración de SQL Server**, haga clic en **servicios de SQL Server**, haga clic con el botón secundario en **selector de demonio de filtro de texto completo de SQL ( *`instance name`* )** y, a continuación, haga clic en **propiedades**.  
  
3.  Haga clic en la pestaña **Iniciar sesión** del cuadro de diálogo y luego seleccione o escriba la cuenta en la que se va a ejecutar cada proceso creado por el servicio Selector de demonio de filtro de texto completo de SQL.  
  
4.  Después de cerrar el cuadro de diálogo, haga clic en **Reiniciar** para reiniciar el servicio Selector de demonio de filtro de texto completo de SQL.  
  
  
##  <a name="if-the-sql-full-text-filter-daemon-launcher-service-does-not-start"></a><a name="error"></a>Si el servicio Selector de demonio de filtro de texto completo de SQL no se inicia  
 Si el servicio Selector del demonio de filtro de texto completo de SQL no se inicia, la causa puede ser una o más de las siguientes:  
  
-   La contraseña asociada a la cuenta del servicio Selector del demonio de filtro de texto completo de SQL ha expirado.  
  
     Si usa una cuenta de usuario local para el servicio Selector del demonio de filtro de texto completo de SQL y su contraseña expira, debe:  
  
    1.  Establecer una nueva contraseña de Windows para la cuenta.  
  
    2.  En el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , actualizar el servicio Selector del demonio de filtro de texto completo de SQL de modo que use la nueva contraseña.  
  
-   La cuenta de usuario o contraseña de la cuenta de servicio es incorrecta.  
  
     El servicio Selector del demonio de filtro de texto completo de SQL podría intentar iniciar sesión con una cuenta de usuario y una contraseña incorrectas. Siga los procedimientos anteriores para comprobar que no se ha cambiado la cuenta de usuario para el servicio.  
  
-   La cuenta que se usó para iniciar sesión en el servicio no tiene privilegios.  
  
     Es posible que esté utilizando una cuenta que no tenga privilegios de inicio de sesión en el equipo donde está instalada la instancia del servidor. Compruebe que está iniciando sesión con una cuenta que tiene derechos y permisos de usuario en el equipo local.  
  
-   Otra instancia de la misma canalización con nombre ya se está ejecutando.  
  
     El servicio de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] actúa como servidor de canalizaciones con nombre para el cliente del servicio Selector del demonio de filtro de texto completo de SQL. Si otro proceso ya creó la canalización con nombre antes de que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se inicie, se grabará un error en el registro de errores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y en el registro de eventos de Windows, y la búsqueda de texto completo no estará disponible.  Averigüe qué proceso o aplicación está intentando utilizar la misma canalización con nombre y detenga la aplicación.  
  
-   El servicio Selector del demonio de filtro de texto completo de SQL no está configurado correctamente.  
  
     El servicio no se puede configurar correctamente en el equipo local.  
  
     Si la funcionalidad de canalizaciones con nombre se ha deshabilitado en el equipo local, o si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se ha configurado para usar una canalización con nombre distinta de la predeterminada, el servicio Selector de demonio de filtro de texto completo de SQL podría no iniciarse.  
  
-   El grupo de servicio de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no tiene permiso para iniciar el servicio Selector de demonio de filtro de texto completo de SQL.  
  
     Durante la instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], al grupo de servicios de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se le concede el permiso predeterminado para administrar, consultar e iniciar el servicio Selector del demonio de filtro de texto completo de SQL. Si los permisos del grupo de servicios de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para la cuenta del servicio Selector de demonio de filtro de texto completo de SQL se han quitado después de la instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , dicho servicio no se iniciará y la búsqueda de texto completo se deshabilitará. Asegúrese de que el grupo de servicios de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tenga permisos para la cuenta de servicio del Selector de demonio de filtro de texto completo de SQL.  
  
  
## <a name="see-also"></a>Consulte también  
 [Temas de procedimientos de administración de servicios &#40;Administrador de configuración de SQL Server&#41;](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md)  
 [Actualizar la búsqueda de texto completo](upgrade-full-text-search.md)  
  
  
