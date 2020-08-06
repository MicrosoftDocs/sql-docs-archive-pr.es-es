---
title: Inicios de sesión, usuarios y roles en bases de datos (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- security [Master Data Services], database roles
- database [Master Data Services], users
- security [Master Data Services], database users
- database [Master Data Services], roles
- database [Master Data Services], logins
- security [Master Data Services], database logins
ms.assetid: 72ee383e-a619-461b-9f9d-1cac162ab0c5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: eadd6fb4d5b9798920d65119386aa2c58afebfa0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748151"
---
# <a name="database-logins-users-and-roles-master-data-services"></a>Inicios de sesión, usuarios y roles en bases de datos (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] incluye inicios de sesión, usuarios y roles que se instalan automáticamente en la instancia de [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] que hospeda la base de datos de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . No se deberían modificar estos inicios de sesión, usuarios y roles.  
  
## <a name="logins"></a>Inicios de sesión  
  
|Iniciar sesión|Descripción|  
|-----------|-----------------|  
|`mds_dlp_login`|Permite la creación de ensamblados de UNSAFE.<br /><br /> -Inicio de sesión deshabilitado con contraseña generada de forma aleatoria.<br /><br /> -Asigna dbo para la base de datos [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .<br /><br /> -Para msdb, mds_clr_user asigna este inicio de sesión.<br /><br /> <br /><br /> Para más información, consulte [Creating an Assembly](../relational-databases/clr-integration/assemblies/creating-an-assembly.md).|  
|`mds_email_login`|Inicio de sesión habilitado usado para las notificaciones.<br /><br /> Para msdb y la base de datos [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , mds_email_user asigna este inicio de sesión.|  
  
## <a name="msdb-users"></a>Usuarios de msdb  
  
|Usuario|Descripción|  
|----------|-----------------|  
|`mds_clr_user`|No se utiliza.<br /><br /> Asigna mds_dlp_login.|  
|`mds_email_user`|Se usa para notificaciones.<br /><br /> Asigna mds_email_login.<br /><br /> Es un miembro del rol: DatabaseMailUserRole.|  
  
## <a name="master-data-services-database-users"></a>Usuarios de la base de datos de Master Data Services  
  
|Usuario|Descripción|  
|----------|-----------------|  
|`mds_email_user`|Se usa para notificaciones.<br /><br /> Tiene el permiso SELECT para el esquema de mdm.<br /><br /> Tiene el permiso EXECUTE para el tipo de tabla definida por el usuario mdm.MemberGetCriteria.<br /><br /> Tiene el permiso EXECUTE para el procedimiento almacenado mdm.udpNotificationQueueActivate.|  
|**mds_schema_user**|Posee los esquemas de mdq y mdm. El esquema predeterminado es mdm.<br /><br /> No tiene un inicio de sesión asignado a él.|  
|**mds_ssb_user**|Se usa para ejecutar tareas de Service Broker.<br /><br /> Tiene todos los esquemas de permisos para DELETE, INSERT, REFERENCES, SELECT y UPDATE.<br /><br /> No tiene un inicio de sesión asignado a él.|  
  
## <a name="master-data-services-database-role"></a>Rol de la base de datos Master Data Services  
  
|Role|Descripción|  
|----------|-----------------|  
|`mds_exec`|Este rol contiene la cuenta que se ha designado en [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] al crear una aplicación web de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] y designa una cuenta para el grupo de aplicaciones. El rol mds_exec tiene:<br /><br /> Permiso **Execute** en todos los esquemas.<br /><br /> Permisos **ALTER**, **Insert**y **Select** en estas tablas:<br />mdm.tblStgMember<br />mdm.tblStgMemberAttribute<br />mdm.tbleStgRelationship<br /><br /> Permiso **Select** en estas tablas:<br />mdm.tblUser<br />mdm.tblUserGroup<br />mdm.tblUserPreference<br /><br /> Permiso **Select** en estas vistas:<br />mdm.viw_SYSTEM_SECURITY_NAVIGATION<br />mdm.viw_SYSTEM_SECURITY_ROLE_ACCCESSCONTROL<br />mdm.viw_SYSTEM_SECURITY_ROLE_ACCCESSCONTROL_MEMBER<br />mdm.viw_SYSTEM_SECURITY_USER_MODEL|  
  
## <a name="schemas"></a>Esquemas  
  
|Role|Descripción|  
|----------|-----------------|  
|`mdm`|Contiene todos los objetos de Service Broker y bases de datos de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] que no sean las funciones contenidas en el esquema mdq.|  
|`mdq`|Contiene funciones de base de datos de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] relacionadas con el filtrado de los resultados de miembros basados en expresiones regulares o de similitud, y el formato de los correos electrónicos de notificación.|  
|**stg**|Contiene las tablas de bases de datos, los procedimientos almacenados y las vistas de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] relacionadas con el proceso de almacenamiento provisional. No elimine ninguno de estos objetos. Para obtener más información acerca del proceso de almacenamiento provisional, vea [importación de datos &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).|  
  
## <a name="see-also"></a>Consulte también  
 [Seguridad de objetos de base de datos &#40;Master Data Services&#41;](../../2014/master-data-services/database-object-security-master-data-services.md)  
  
  
