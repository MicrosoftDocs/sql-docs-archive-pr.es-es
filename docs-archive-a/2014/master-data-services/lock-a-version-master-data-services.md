---
title: Bloquear una versión (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- versions [Master Data Services], locking
- locking versions [Master Data Services]
ms.assetid: 7bb62a84-12d8-4b29-9b6e-6aa25410618e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 68ef979b14d9bd228c7ca89a260b31b2fc6efccd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748816"
---
# <a name="lock-a-version-master-data-services"></a>Bloquear una versión (Master Data Services)
  En [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], bloquee una versión de un modelo para impedir cambios en los miembros del modelo y en sus atributos.  
  
> [!NOTE]  
>  Cuando se bloquea una versión, los administradores del modelo pueden continuar agregando, modificando y quitando los miembros. Otros usuarios con permiso en el modelo solo pueden ver los miembros.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para realizar este procedimiento:  
  
-   Debe disponer del permiso para tener acceso al área funcional de **Administración de versiones** .  
  
-   Debe ser administrador de modelo. Para obtener más información, vea [administradores &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   El estado de la versión debe ser **Abierta**.  
  
### <a name="to-lock-a-version"></a>Para bloquear una versión  
  
1.  En [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], haga clic en **Administración de versiones**.  
  
2.  En la página **Administrar versiones** , seleccione la fila de la versión que desea bloquear.  
  
3.  Haga clic en **Bloquear**.  
  
4.  En el cuadro de diálogo de confirmación, haga clic en **Aceptar**.  
  
## <a name="next-steps"></a>Pasos siguientes  
  
-   [Validar una versión con las reglas de negocios &#40;Master Data Services&#41;](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   [Confirmar una versión &#40;Master Data Services&#41;](../../2014/master-data-services/commit-a-version-master-data-services.md)  
  
## <a name="see-also"></a>Consulte también  
 [Versiones &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)   
 [Desbloquear una versión &#40;Master Data Services&#41;](../../2014/master-data-services/unlock-a-version-master-data-services.md)  
  
  
