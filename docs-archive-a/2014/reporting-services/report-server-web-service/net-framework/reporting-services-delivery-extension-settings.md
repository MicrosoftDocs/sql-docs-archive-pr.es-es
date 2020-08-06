---
title: Configuración de la extensión de entrega de Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- XML Web service [Reporting Services], delivery extension settings
- Report Server Web service, delivery extension settings
- delivery [Reporting Services]
- network share delivery [Reporting Services]
- file share delivery [Reporting Services]
- e-mail [Reporting Services]
- mailing reports [Reporting Services]
- sharing reports
- extensions [Reporting Services], delivery
- mail [Reporting Services]
- Web service [Reporting Services], delivery extension settings
ms.assetid: 68c31a85-261c-4ec4-b8df-1f9842b46f8a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d5363c99cb858ce61f7be3b039e27a69944767b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745021"
---
# <a name="reporting-services-delivery-extension-settings"></a>Configuración de la extensión de entrega de Reporting Services
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] contiene una extensión de entrega por correo electrónico y una extensión de entrega a recursos compartidos de archivos. La entrega por correo electrónico proporciona una manera de enviar un informe a usuarios individuales o grupos a través del correo electrónico. La entrega a recursos compartidos de archivos permite enviar los informes representados automáticamente a un recurso compartido de la red. Puede utilizar cualquiera de las dos extensiones de entrega admitidas con las suscripciones estándar o las suscripciones controladas por datos. La configuración de entrega específica del tipo de extensión de entrega se pasa siempre que se llama a los métodos <xref:ReportService2010.ReportingService2010.CreateSubscription%2A>,<xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>,<xref:ReportService2010.ReportingService2010.SetSubscriptionProperties%2A> y <xref:ReportService2010.ReportingService2010.SetDataDrivenSubscriptionProperties%2A>. Para recuperar mediante programación una lista de configuración de entrega, utilice el método <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A>.  
  
> [!NOTE]  
>  La configuración de la extensión de entrega distingue mayúsculas y minúsculas.  
  
## <a name="e-mail-delivery-settings"></a>Configuración de entrega por correo electrónico  
 En la tabla siguiente se enumeran las opciones de configuración de la entrega por correo electrónico para las suscripciones que utilizan el correo electrónico del servidor de informes.  
  
|Configuración|Value|  
|-------------|-----------|  
|**Para**|Dirección de correo electrónico que aparece en la línea `To` del mensaje. Varias direcciones de correo electrónico se separan mediante puntos y coma. Necesario.|  
|**CORREOS**|Dirección de correo electrónico que aparece en la línea `Cc` del mensaje. Varias direcciones de correo electrónico se separan mediante puntos y coma. Opcional.|  
|**BCC**|Dirección de correo electrónico que aparece en la línea `Bcc` del mensaje. Varias direcciones de correo electrónico se separan mediante puntos y coma. Opcional.|  
|**ReplyTo**|Dirección de correo electrónico que aparece en el encabezado `Reply-To` del mensaje. El valor debe ser una dirección de correo electrónico única. Opcional.|  
|`IncludeReport`|Valor que indica si incluir el informe en la entrega por correo electrónico. El valor `true` indica que el informe se entrega en el cuerpo del mensaje de correo electrónico.|  
|**RenderFormat**|Nombre de la extensión de representación que se usa para generar el informe representado. El nombre debe corresponder a una de las extensiones de representación visibles instaladas en el servidor de informes. Se requiere este valor si el valor `IncludeReport` está establecido en `true`.|  
|**Prioridad**|Prioridad con la que se envía el mensaje de correo electrónico. Valores válidos son `LOW`, `NORMAL` y `HIGH`. El valor predeterminado es `NORMAL`.|  
|**Subject**|El texto de la línea de asunto del mensaje de correo electrónico.|  
|**Comentario**|Texto incluido en el cuerpo del mensaje de correo electrónico.|  
|**IncludeLink**|Valor que indica si incluir un vínculo al informe en el cuerpo del correo electrónico.|  
  
## <a name="file-share-delivery-settings"></a>Configuración de la entrega a recursos compartidos de archivos  
 En la tabla siguiente se enumeran las opciones de configuración de la entrega a recursos compartidos de archivos para las suscripciones.  
  
|Configuración|Value|  
|-------------|-----------|  
|**EXTENSIÓN**|Nombre del archivo que se va a guardar en disco.|  
|**FILEEXTN**|Indica si incluir una extensión de archivo para el informe representado. El valor es `true` o `false`.|  
|**PATH**|Ruta de acceso a la carpeta o al recurso compartido de archivos UNC donde guardar el informe.|  
|**RENDER_FORMAT**|Formato del informe que se guarda en el disco.|  
|**NOMBRE**|Nombre de usuario necesario para tener acceso al recurso de la red o disco.|  
|**CONTRASEÑA**|Contraseña necesaria para tener acceso al recurso de la red o disco.|  
|**WRITEMODE**|Modo de escritura que utilizar al tener acceso al disco. Valores válidos son `None`, `Overwrite` y `AutoIncrement`.|  
  
## <a name="see-also"></a>Consulte también  
 [Referencia técnica &#40;SSRS&#41;](../../technical-reference-ssrs.md)   
 [Creación de aplicaciones con el servicio web y .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
