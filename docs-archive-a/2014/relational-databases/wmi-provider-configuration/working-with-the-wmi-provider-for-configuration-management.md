---
title: Trabajar con el proveedor WMI para la administración de configuración | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- permissions [WMI]
- connection strings [WMI]
- security [WMI]
- WMI Provider for Configuration Management, connection strings
- WMI Provider for Configuration Management, security
- late binding [WMI]
- WMI Provider for Configuration Management, late binding
- binding [WMI]
ms.assetid: 34daa922-7074-41d0-9077-042bb18c222a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 80f311fb0abae2337f6ea4a5d5d85aaa0d320b94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672834"
---
# <a name="working-with-the-wmi-provider-for-configuration-management"></a>Trabajar con el proveedor WMI para la administración de configuración
  Tenga en cuenta la siguiente información antes de programar con el proveedor WMI para la Administración de equipos:  
  
## <a name="binding"></a>Enlace  
 El proveedor WMI para la administración de configuración es un modelo de objetos COM y admite el enlace en tiempo de diseño y en tiempo de ejecución. Con el enlace en tiempo de ejecución puede utilizar lenguajes de script, como VBScript, para manipular mediante programación los servicios de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la configuración de red y los alias.  
  
 Para obtener más información acerca de la programación de implementaciones del proveedor WMI mediante lenguajes de scripting, vea el [!INCLUDE[msCoName](../../includes/msconame-md.md)] [sitio web](https://go.microsoft.com/fwlink/?linkid=15426)de MSDN.  
  
## <a name="specifying-a-connection-string"></a>Especificar una cadena de conexión  
 Las aplicaciones dirigen el proveedor WMI para la administración de configuración a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mediante la conexión a un espacio de nombres WMI definido por el proveedor. El servicio WMI de Windows asigna este espacio de nombres a la DLL del proveedor DLL y lo carga en memoria. Todas las instancias de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se representan con un único espacio de nombres WMI. El valor predeterminado del espacio de nombres es  
  
```  
\\.\root\Microsoft\SqlServer\ComputerManagement12\instance_name  
```  
  
 donde `instance_name` tiene como valor predeterminado `MSSQLSERVER` en una instalación predeterminada de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Nota:** Si se va a conectar a través de Firewall de Windows, deberá asegurarse de que los equipos estén configurados correctamente. Vea el artículo sobre la conexión a través de Firewall de Windows en la documentación de Instrumental de administración de Windows en el [!INCLUDE[msCoName](../../includes/msconame-md.md)] [sitio web](https://go.microsoft.com/fwlink/?linkid=15426)de MSDN.  
  
## <a name="permissions-and-server-authentication"></a>Permisos y autenticación del servidor  
 Para tener acceso al proveedor WMI para la administración de configuración, el script de administración de WMI de cliente se debe ejecutar en el contexto de un administrador en el equipo de destino. Necesita ser miembro del grupo administradores de Windows local en el equipo que desea administrar.  
  
 El administrador puede establecer directivas de grupo para controlar el acceso de usuario a los proveedores WMI. Para obtener más información sobre cómo establecer directivas de grupo, vea el tema sobre directiva de grupo y MMC en la Ayuda del Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 El script de administración de WMI se puede utilizar para actualizar la cuenta con la que se ejecutan los servicios de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 El proveedor WMI para la administración de configuración admite los certificados de seguridad. Para obtener más información acerca de los certificados, consulte [jerarquía de cifrado](../security/encryption/encryption-hierarchy.md).  
  
## <a name="see-also"></a>Consulte también  
 [Administrador de configuración de SQL Server](../sql-server-configuration-manager.md)  
  
  
