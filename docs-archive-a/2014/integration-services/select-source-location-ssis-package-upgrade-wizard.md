---
title: Seleccionar ubicación de origen (Asistente para actualización del paquete SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.selectsourcelocation.f1
ms.assetid: 429f146e-edb4-4401-a225-f2c8468971c5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e24eec77dc87a6215f9d686cf5af964cc244d68d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744186"
---
# <a name="select-source-location-ssis-package-upgrade-wizard"></a>Seleccionar ubicación de origen (Asistente para actualización del paquete SSIS)
  Utilice la página **Seleccionar ubicación de origen** para especificar el origen desde el que se actualizan los paquetes.  
  
> [!NOTE]  
>  Esta página solo está disponible cuando se ejecuta el Asistente para actualizar paquetes [!INCLUDE[ssIS](../includes/ssis-md.md)] desde [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] o en el símbolo del sistema.  
  
 **Para ejecutar el Asistente para actualización del paquete SSIS**  
  
-   [Actualizar paquetes de Integration Services mediante el Asistente para actualizar paquetes SSIS](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)  
  
## <a name="static-options"></a>Opciones estáticas  
 **Origen del paquete**  
 Seleccione la ubicación de almacenamiento que contiene los paquetes que se van a actualizar. Esta opción tiene los valores que figuran en la siguiente tabla.  
  
|Value|Descripción|  
|-----------|-----------------|  
|**Sistema de archivos**|Indica que los paquetes que se van a actualizar están en una carpeta en el equipo local.<br /><br /> Para hacer que el asistente realice una copia de seguridad de los paquetes originales antes de actualizarlos, estos deben estar almacenados en el sistema de archivos. Para obtener más información, vea el tema de procedimientos.|  
|**Almacén de paquetes SSIS**|Indica que los paquetes que se van a actualizar están en el almacén de paquetes. El almacén de paquetes consta del conjunto de carpetas del sistema de archivos que el servicio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] administra. Para obtener más información, vea [Administración de paquetes &#40;servicio SSIS&#41;](service/package-management-ssis-service.md).<br /><br /> Al seleccionar este valor, se muestran las opciones dinámicas de **Origen del paquete** correspondientes.|  
|**Microsoft SQL Server**|Indica que los paquetes que se van a actualizar son de una instancia existente de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].<br /><br /> Al seleccionar este valor, se muestran las opciones dinámicas de **Origen del paquete** correspondientes.|  
  
 **Carpeta**  
 Escriba el nombre de una carpeta que contenga los paquetes que quiere actualizar o haga clic en **Examinar** y busque la carpeta.  
  
 **Browse**  
 Busque la carpeta que contiene los paquetes que desea actualizar.  
  
## <a name="package-source-dynamic-options"></a>Opciones dinámicas de Origen del paquete  
  
### <a name="package-source--ssis-package-store"></a>Origen del paquete = Almacén de paquetes SSIS  
 **Server**  
 Escriba el nombre del servidor que tiene los paquetes que se van a actualizar o seleccione este servidor en la lista.  
  
### <a name="package-source--microsoft-sql-server"></a>Origen del paquete = Microsoft SQL Server  
 **Server**  
 Escriba el nombre del servidor que tiene los paquetes que se van a actualizar o seleccione este servidor en la lista.  
  
 **Usar autenticación de Windows**  
 Seleccione esta opción para utilizar la autenticación de Windows para conectarse al servidor.  
  
 **Usar autenticación SQL Server**  
 Seleccione esta opción para usar la autenticación de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] para conectarse al servidor. Si usa la autenticación de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , debe proporcionar un nombre de usuario y una contraseña.  
  
 **Nombre de usuario**  
 Escriba el nombre de usuario que la autenticación de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] usará para conectarse al servidor.  
  
 **Contraseña**  
 Escriba la contraseña que la autenticación de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] usará para conectarse al servidor.  
  
## <a name="see-also"></a>Consulte también  
 [Actualizar paquetes de Integration Services](install-windows/upgrade-integration-services-packages.md)  
  
  
