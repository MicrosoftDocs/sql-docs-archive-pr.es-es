---
title: Archivos de registro de seguimiento predeterminados deshabilitados | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c27761e6-75ed-4ee4-a236-0cbc42e500a1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0fed8fb006427b4dda9d99c57cbabca8538efcad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87671000"
---
# <a name="default-trace-log-files-disabled"></a>Archivos de registro de seguimiento predeterminados deshabilitados
  Esta regla comprueba el valor de la opción de procedimiento almacenado sp_configure default trace enabled para determinar si el seguimiento predeterminado está establecido en ON (1) o en OFF (0). Cuando esta opción está habilitada, el seguimiento predeterminado proporciona información sobre la configuración y los cambios de DDL de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. En algunos casos, esta información puede ser útil para los clientes y el Servicio de atención al cliente y soporte técnico de [!INCLUDE[msCoName](../../includes/msconame-md.md)] al solucionar problemas con el [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="best-practices-recommendations"></a>Prácticas recomendadas  
 Utilice el procedimiento almacenado sp_configure para habilitar el seguimiento estableciendo el valor de default trace enabled en 1.  
  
## <a name="for-more-information"></a>Para obtener más información  
 [Opciones de configuración de servidor &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>Consulte también  
 [Supervisar y aplicar las prácticas recomendadas usando la administración basada en directivas](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
