---
title: Aplicar reglas de negocios (complemento MDS para Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cd106345-f561-4966-88d3-a69139b2bd78
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: aad5ce6bcebb635fa4659c32654d67406d4ba0dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745360"
---
# <a name="apply-business-rules-mds-add-in-for-excel"></a>Aplicar reglas de negocios (complemento MDS para Excel)
  En el [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] , puede aplicar reglas de negocios cuando desee validar datos y confirmar que son válidos. Puede corregir validaciones y volver a publicar los datos.  
  
> [!NOTE]  
>  La validación de datos aparece automáticamente al publicar datos. Para obtener más información, consulte [Procedimiento almacenado de validación &#40;Master Data Services&#41;](../validation-stored-procedure-master-data-services.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para realizar este procedimiento:  
  
-   Debe tener acceso al área funcional **Explorador** .  
  
-   Debe tener una hoja de cálculo activa que contenga datos administrados por MDS.  
  
### <a name="to-apply-business-rules"></a>Para aplicar reglas de negocios  
  
1.  En el grupo **Publicar y validar** , haga clic **Aplicar las reglas**.  
  
    > [!NOTE]  
    >  El número de miembros (filas) que se validan al mismo tiempo depende de un valor de [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]. Para más información, consulte [Business Rule Settings](../system-settings-master-data-services.md#BusinessRules).  
  
2.  Los datos se validan comparándolos con las reglas de negocios y se muestran dos columnas de estado. Si estas columnas no se muestran automáticamente, en el grupo **Publicar y validar** , haga clic en **Mostrar estado** para verlas.  
  
## <a name="see-also"></a>Consulte también  
 [Complemento MDS para Excel de &#40;de datos de publicación&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
