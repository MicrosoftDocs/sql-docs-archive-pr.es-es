---
title: Cuadro de diálogo Conectar con una base de datos de Master Data Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.srvconnect.f1
ms.assetid: b2f8c9b9-c31e-4f0d-9095-978709423190
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 731e195ca60ca09bc76934af09ae1efeba7a0093
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744173"
---
# <a name="connect-to-a-master-data-services-database-dialog-box"></a>Conectar a un cuadro de diálogo Base de datos de Master Data Services
  Utilice el cuadro de diálogo **Conectar con una base de datos de Master Data Services** para seleccionar una base de datos de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
 En [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], este cuadro de diálogo se encuentra disponible en las siguientes páginas:  
  
-   En la página **Configuración de base de datos** , haga clic en **Seleccionar base de datos** . Utilice este diálogo para seleccionar una base de datos donde establecer la configuración del sistema.  
  
-   En la página **Configuración web** , en **Asociar aplicación con base de datos**, haga clic en **Seleccionar** para seleccionar la base de datos que se va a asociar con el sitio web o aplicación de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
## <a name="select-database"></a>Seleccionar base de datos  
 Especifique la información de conexión a una instancia de [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] local o remota que hospede la base de datos de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Para conectarse a una instancia remota, se debe estar habilitado para realizar conexiones remotas.  
  
|Nombre del control|Descripción|  
|------------------|-----------------|  
|**Instancia de SQL Server**|Especifique el nombre de la instancia de [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] que vaya a hospedar a la base de datos de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Puede ser una instancia predeterminada o con nombre en un equipo local o remoto. Especifique la información, para ello escriba:<br /><br /> Un punto (.) para conectarse a la instancia predeterminada en su equipo local.<br /><br /> El nombre del servidor o dirección IP para conectarse a la instancia predeterminada en el equipo local o remoto especificado.<br /><br /> El nombre del servidor o dirección IP y el nombre de instancia para conectarse a la instancia con nombre en el equipo local o remoto especificado. Especifique esta información en el formato *SERVER_NAME* \\ *instance_name*.|  
|**Tipo de autenticación**|Seleccione el tipo de autenticación que se va a utilizar en la conexión con la instancia de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] especificada. Las credenciales que use para conectarse determinarán las bases de datos que se van a mostrar en la lista desplegable **Base de datos de Master Data Services** . Entre los tipos de autenticación se incluyen:<br /><br /> **Usuario actual: seguridad integrada**: utiliza la autenticación integrada de Windows para conectarse con las credenciales de la cuenta de usuario de Windows actual. [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] utiliza las credenciales de Windows del usuario que inició sesión en el equipo y abrió la aplicación. No puede especificar unas credenciales de Windows diferentes en la aplicación. Si desea conectarse con credenciales diferentes de Windows, debe iniciar sesión en el equipo como ese usuario y, a continuación, abrir [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].<br /><br /> **Cuenta de SQL Server**: utiliza una cuenta de SQL Server para la conexión. Al seleccionar esta opción, se habilitan los campos **Nombre de usuario** y **Contraseña** y es preciso que especifique las credenciales para una cuenta de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] en la instancia de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] especificada.|  
|**Nombre de usuario**|Especifique el nombre de la cuenta de usuario que se utilizará para conectar a la instancia de SQL Server especificada. La cuenta debe inscribirse en el rol **sysadmin** en la instancia de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] especificada:<br /><br /> Cuando el **tipo de autenticación** es **usuario actual: seguridad integrada**, el cuadro **nombre de usuario** es de solo lectura y muestra el nombre de la cuenta de usuario de Windows que ha iniciado sesión en el equipo.<br /><br /> Cuando el **Tipo de autenticación** es **Cuenta de SQL Server**, se habilitará el cuadro **Nombre de usuario** y deberá especificar las credenciales para una cuenta de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] en la instancia [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] especificada.|  
|**Contraseña**|Especifique la contraseña asociada a la cuenta de usuario:<br /><br /> Cuando el **tipo de autenticación** es el **usuario actual: seguridad integrada**, el cuadro **contraseña** es de solo lectura y las credenciales de la cuenta de usuario de Windows especificada se usan para conectarse.<br /><br /> Cuando el **Tipo de autenticación** sea **Cuenta de SQL Server**, se habilitará el cuadro **Contraseña** y deberá especificar la contraseña asociada a la cuenta de usuario especificada.|  
|**Conexión**|Conéctese a la instancia [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] con las credenciales especificadas.|  
|**Master Data Services base de datos**|Muestra las bases de datos de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] en la instancia de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] especificada según los siguientes criterios:<br /><br /> Cuando el usuario es un miembro del rol de servidor **sysadmin** para esa instancia, se muestran todas las bases de datos de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] en esa instancia.<br /><br /> Cuando el usuario es un miembro del rol de base de datos de **db_owner** para cualquier base de datos de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] en esa instancia, se muestran esas bases de datos de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .<br /><br /> <br /><br /> Para obtener más información sobre los roles de SQL Server, consulte [Roles de nivel de servidor](../relational-databases/security/authentication-access/server-level-roles.md) y [Roles de nivel de base de datos](../relational-databases/security/authentication-access/database-level-roles.md).|  
  
## <a name="see-also"></a>Consulte también  
 [Página configuración de base de datos &#40;Administrador de configuración de Master Data Services&#41;](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md)   
 [Configurar la base de datos y el sitio web para Master Data Services](set-up-the-database-and-website-for-master-data-services.md)  
  
  
