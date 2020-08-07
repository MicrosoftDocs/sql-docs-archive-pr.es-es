---
title: 'Configuración de correo electrónico: Configuration Manager (modo nativo de SSRS) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.rsconfigtool.emailsettings.f1
helpviewer_keywords:
- SQL11.rsconfigtool.emailsettings.F1
ms.assetid: cdad1529-bfa6-41fb-9863-d9ff1b802577
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8c5f276f8d6566e052ee291118eb1d1c12fbddc9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746177"
---
# <a name="e-mail-settings---configuration-manager-ssrs-native-mode"></a>Configuración de correo electrónico - Administrador de configuración (Modo nativo de SSRS)
  Utilice esta página para especificar la configuración del Protocolo simple de transferencia de correo (SMTP) que habilita la entrega de correo electrónico del servidor de informes desde este. Puede utilizar la extensión de entrega por correo electrónico del servidor de informes para distribuir informes o notificaciones de procesamiento de informes a través de suscripciones por correo electrónico. La extensión de entrega por correo electrónico del servidor de informes requiere un servidor SMTP y una dirección de correo electrónico para el campo De:.  
  
 Se pueden utilizar parámetros de configuración adicionales para personalizar suscripciones por correo electrónico, incluidos los parámetros que restrinjan la disponibilidad de extensiones de representación y hosts del servidor de correo. No se puede especificar esta configuración en el Administrador de configuración de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Para configurar los parámetros adicionales, debe editar el archivo RSReportServer.config manualmente. Para obtener más información, vea [configurar un servidor de informes para la entrega por correo electrónico &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) y [Reporting Services archivos de configuración en los](../report-server/reporting-services-configuration-files.md) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] libros en pantalla de.  
  
 Para abrir esta página, inicie la Administrador de configuración de Reporting Services y haga clic en **configuración de correo electrónico** en el panel de navegación. Para obtener más información, vea [Administrador de configuración de Reporting Services &#40;modo nativo&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Modo nativo.  
  
## <a name="options"></a>Opciones  
 **Dirección del remitente**  
 Especifica la dirección de correo electrónico que se utiliza en el campo De: de un mensaje de correo electrónico generado. Debe especificar una cuenta de usuario que tenga permiso para enviar correo desde el servidor SMTP.  
  
 **Método de entrega SMTP actual**  
 Especifica que el correo electrónico del servidor de informes se enruta a través de un servidor SMTP. Este es el único método de entrega que puede especificar en el Administrador de configuración de Reporting Services.  
  
 Un método de entrega alternativo es utilizar un directorio de recogida del servicio SMTP local. Puede utilizar este método de entrega si no hay disponible un servicio SMTP de red. Para especificar un directorio de recogida del servicio SMTP local, debe editar el archivo RSReportServer.config. Si edita el archivo de configuración para usar un directorio de recogida del servicio SMTP local, el Administrador de configuración de Reporting Services establece la opción **Método de entrega** en *personalizado* para indicar que el método de entrega se especifica en el archivo de configuración.  
  
 En el archivo de configuración, el método de entrega se establece a través del parámetro de configuración `SendUsing`. Para obtener más información sobre cómo especificar la `SendUsing` configuración, vea [configurar un servidor de informes para la entrega por correo electrónico &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).  
  
 **Servidor SMTP**  
 Especifique el servidor SMTP o la puerta de enlace que se va a usar. Puede utilizar un servidor local o un servidor SMTP en la red.  
  
## <a name="see-also"></a>Consulte también  
 [Configurar un servidor de informes para la entrega por correo electrónico &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)   
 [Administrador de configuración de Reporting Services temas de la ayuda F1 &#40;el modo nativo de SSRS&#41;](../../sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)  
  
  
