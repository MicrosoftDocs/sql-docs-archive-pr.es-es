---
title: Configuración de la información del dispositivo ATOM | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fe4a56a4-5552-423c-85c1-895e2e212fee
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bdbac1500063accf868d4b538b82ba9f3b5aebb0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672812"
---
# <a name="atom-device-information-settings"></a>Configuración de la información del dispositivo ATOM
  La configuración de información de dispositivo para la extensión de representación Atom admite el envío de un nombre de una fuente Atom y la codificación de caracteres que se usará.  
  
 En la siguiente tabla se enumera la configuración de información de dispositivo para la representación en un documento de servicio de datos.  
  
|Configuración|Value|  
|-------------|-----------|  
|`DataFeed`|Si se especifica, representa la fuente Atom que corresponde al nombre de fuente proporcionado en esta configuración. De lo contrario, representa el documento de servicio Atom para el informe. El identificador único generado automáticamente de la fuente de distribución de datos. Este valor se usa internamente y no se debe cambiar.|  
|**Codificación**|Nombre del organismo Internet Assigned Numbers Authority (IANA) de una codificación de caracteres que es compatible con .NET Framework. El valor predeterminado es `UTF-8`. Entre los ejemplos de otros valores se incluyen ASCII, UTF-7 y UTF-16.|  
  
## <a name="see-also"></a>Consulte también  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Pasar la configuración de información de dispositivo a las extensiones de representación](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personalizar los parámetros de extensión de representación en RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Referencia técnica &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
