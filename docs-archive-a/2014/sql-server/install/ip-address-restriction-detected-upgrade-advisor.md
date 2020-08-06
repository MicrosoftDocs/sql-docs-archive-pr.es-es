---
title: Restricción de dirección IP detectada (Asesor de actualizaciones) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 9a154455-c68f-4403-a3a7-b90f4d35eecb
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2028e59e91d42bfdced2d18fa6ce129dfb108302
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746105"
---
# <a name="ip-address-restriction-detected-upgrade-advisor"></a>Se detectó una restricción de dirección IP (Asesor de actualizaciones)
  El Asesor de actualizaciones ha detectado una o varias restricciones de dirección IP en el sitio web de IIS que hospeda los directorios virtuales del servidor de informes o del Administrador de informes. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] no proporciona compatibilidad nativa con las restricciones de dirección IP.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Nativos.|  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Descripción  
 La instalación no puede definir las restricciones de dirección IP en URL creadas para un servidor de informes actualizado. La actualización puede continuar, pero las restricciones de dirección IP no se definirán en las URL de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="corrective-action"></a>Acción correctora  
 Tras la actualización, utilice ISA Server, su software de firewall u otra solución para permitir o denegar las solicitudes realizadas desde direcciones IP específicas al servidor de informes.  
  
## <a name="see-also"></a>Consulte también  
 [Reporting Services problemas de actualización &#40;el asesor de actualizaciones&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
