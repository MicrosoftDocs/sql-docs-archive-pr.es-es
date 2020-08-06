---
title: Requisitos de seguridad para administrar servicios | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent service, security
- services [SQL Server], security
- SQL Server services, security
- WMI Providers [SQL Server]
- server configuration [SQL Server]
- security [SQL Server], services
- services [SQL Server], WMI
ms.assetid: 1874a317-ddb2-425d-98d9-b53e1be6fc6a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 46a777858c01bf3057093d34b29b9a2093668e97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748913"
---
# <a name="security-requirements-for-managing-services"></a>Requisitos de seguridad para administrar servicios
  Para administrar los servicios de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], use el Administrador de configuración de SQL Server o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Los servicios de los servidores en clúster se administran con el Administrador de clústeres.  
  
 Para poder administrar el servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y establecer las opciones de configuración del servidor, debe ser miembro del rol fijo de servidor **serveradmin** o **sysadmin** . Los miembros del grupo **Administradores** de Windows pueden iniciar y detener servicios, así como configurar las opciones del servidor que ofrece Windows.  
  
> [!NOTE]  
>  Para que funcionen correctamente, las cuentas utilizadas por los servicios deben estar configurar con el dominio, el sistema de archivos y los permisos de registro correctos. Para obtener información sobre los permisos necesarios, vea [Configurar los permisos y las cuentas de servicio de Windows](configure-windows-service-accounts-and-permissions.md).  
  
## <a name="windows-management-instrumentation"></a>Instrumental de administración de Windows  
 El Administrador de configuración de SQL Server y [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] utilizan Instrumental de administración de Windows (WMI) para visualizar y modificar algunas de las propiedades del servidor. Para administrar servicios y obtener su estado, el usuario debe tener los derechos necesarios para el acceso al objeto de WMI. En [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], utilizan WMI las páginas de propiedades del servidor siguientes:  
  
-   Servicios de inicio automático  
  
-   Parámetros de inicio  
  
-   Seguridad  
  
-   Configuración adicional del servidor  
  
## <a name="related-tasks"></a>Related Tasks  
 [Configurar WMI para mostrar el estado del servidor en Herramientas de SQL Server](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
## <a name="related-content"></a>Contenido relacionado  
 [Conceptos del proveedor WMI de administración de configuración](../../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
