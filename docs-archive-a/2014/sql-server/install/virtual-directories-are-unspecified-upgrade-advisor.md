---
title: Los directorios virtuales no están especificados (Asesor de actualizaciones) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- virtual directories [Reporting Services]
ms.assetid: 7d32b560-49d6-4558-b5d6-9127067f82d6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: e20c48d0bf58d28cb2894baa26c2e11db26fab96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672403"
---
# <a name="virtual-directories-are-unspecified-upgrade-advisor"></a>Los directorios virtuales no están especificados (Asesor de actualizaciones)
  El Asesor de actualizaciones no ha detectado ninguna configuración de directorios virtuales para el servicio web del servidor de informes o para el Administrador de informes. Una vez completada la actualización, debe configurar las reservas de direcciones URL para el servidor de informes mediante el Administrador de configuración de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Modo nativo.|  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Descripción  
 La actualización de una instalación de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] incluye reservar nuevas URL para el servicio web del servidor de informes y para el Administrador de informes. El Asesor de actualizaciones no ha detectado directorios virtuales para el servidor de informes o para el Administrador de informes de la instancia que se va a actualizar y, por consiguiente, el proceso de actualización no pudo recopilar información suficiente para crear las reservas de direcciones URL del servidor de informes actualizado. La actualización puede continuar, pero el directorio virtual del servidor de informes o del Administrador de informes quedará sin definir después de la instalación de la actualización.  
  
## <a name="corrective-action"></a>Acción correctora  
 Tras finalizar la actualización, use el Administrador de configuración de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] para establecer las direcciones URL para el servidor de informes y para el Administrador de informes. Use el administrador de IIS para quitar los directorios virtuales que ya no necesite.  
  
 Para obtener más información, vea [configurar una dirección URL &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) en los [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] libros en pantalla de.  
  
## <a name="see-also"></a>Consulte también  
 [Reporting Services problemas de actualización &#40;el asesor de actualizaciones&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
