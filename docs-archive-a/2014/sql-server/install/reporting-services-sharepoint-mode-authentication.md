---
title: Autenticación en modo de Reporting Services SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade SharePoint Mode [Reporting Services]
- SharePoint integration
- SharePoint Mode
ms.assetid: 2c19794a-dd55-4fe5-b901-6dd93e9f6beb
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3b1316a1a49726ab0754f39160125425fec116d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748508"
---
# <a name="reporting-services-sharepoint-mode-authentication"></a>Autenticación del modo de SharePoint de Reporting Services
  Use la página **Autenticación del modo de SharePoint de Reporting Services** del Asistente para la instalación de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para especificar las credenciales de la cuenta de servicio que se usa en la instalación actual de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Las credenciales se usarán para crear un nuevo grupo de aplicaciones de SharePoint. Además, se creará una nueva aplicación de servicio de SharePoint para [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . El nombre de la aplicación de servicio contendrá el nombre de la instancia anterior de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
## <a name="options"></a>Opciones  
  
-   La opción **Nombre de la cuenta del grupo de aplicaciones SSRS** es de solo lectura. El valor se rellena automáticamente con el valor actual de la instalación de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] existente que va a actualizar.  
  
-   La opción **Contraseña de la cuenta del grupo de aplicaciones SSRS** estará deshabilitada si la cuenta del grupo de aplicaciones no requiere una contraseña. Por ejemplo, "NT Authority\NetworkService". Si la cuenta del grupo de aplicaciones requiere una contraseña, no podrá continuar con la actualización hasta que escriba la contraseña correcta.  
  
 Para obtener más información, vea [actualizar y migrar Reporting Services](https://go.microsoft.com/fwlink/?LinkID=245628) ( https://go.microsoft.com/fwlink/?LinkID=245628) .  
  
## <a name="see-also"></a>Consulte también  
 [Actualizar y migrar Reporting Services](https://go.microsoft.com/fwlink/?LinkID=245628)  
  
  
