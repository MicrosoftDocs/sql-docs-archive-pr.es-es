---
title: Cuentas de dominio necesarias para la granja de servidores de SharePoint (Asesor de actualizaciones) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 90cd6d3e-a271-4cb8-81f2-fc555b2d3cab
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7d180fbc12a264256156c878916838f7caeec723
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87677398"
---
# <a name="domain-accounts-required-for-sharepoint-farm-upgrade-advisor"></a>Cuentas de dominio necesarias para una granja de servidores de SharePoint (Asesor de actualizaciones)
  Los productos de SharePoint que están configurados para un entorno de una granja requieren el uso de cuentas de dominio.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Modo de SharePoint.|  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssRS](../../includes/ssrs.md)]  
  
### <a name="description"></a>Descripción  
 Los productos de SharePoint que se configuran para el entorno de una granja requieren el uso de cuentas de dominio para las conexiones a bases de datos y servicios. Esto incluye la cuenta que ha especificado para la cuenta de servicio de Reporting Services.  
  
 En las páginas de Administración central de SharePoint 2010 puede ver problemas si no utiliza una cuenta de usuario de dominio para Reporting Services. Al intentar configurar la integración de Reporting Services, verá un mensaje de error similar al siguiente:  
  
 "El servidor de informes se está ejecutando en la cuenta de servicio NT AUTHORITY\NETWORK integrada, lo que no se admite en una instalación de granja de SharePoint. Vuelva a configurar el servidor de informes para que se ejecute en una cuenta de dominio."  
  
## <a name="corrective-action"></a>Acción correctora  
 En [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] y versiones anteriores, use el administrador de configuración de Reporting Services para cambiar la cuenta asignada como cuenta de servicio del servidor de informes.  
  
#### <a name="to-change-the-service-account-from-configuration-manager"></a>Para cambiar la cuenta de servicio del Administrador de configuración  
  
1.  En el menú **Inicio** , seleccione **todos los programas**y, a continuación, haga clic en **Microsoft SQL Server 2008 R2**.  
  
2.  Seleccione **herramientas de configuración**y, a continuación, haga clic en **Administrador de configuración de Reporting Services**.  
  
3.  En Configuration Manager, seleccione la pestaña **cuenta de servicio** .  
  
4.  Seleccione **usar otra cuenta** y escriba las credenciales de una cuenta de dominio.  
  
5.  Haga clic en **Aplicar**.  
  
## <a name="see-also"></a>Consulte también  
 [Configurar la cuenta de servicio del servidor de informes &#40;Administrador de configuración de SSRS&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
  
  
