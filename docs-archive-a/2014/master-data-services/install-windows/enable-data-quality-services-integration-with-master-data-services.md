---
title: Habilitar la integración de Data Quality Services con Master Data Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: ab32938d-a80e-4106-80d4-94b2de3d67dc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8d2fa25254cae2a129b6e08ff657d92af4ff9455
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87671112"
---
# <a name="enable-data-quality-services-integration-with-master-data-services"></a>Habilitar la integración de Data Quality Services con Master Data Services
  En el [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], Data Quality Services (DQS) proporciona la funcionalidad de coincidencia. Esta funcionalidad debe habilitarse para poder usarse.  
  
## <a name="prerequisites"></a>Requisitos previos  
  
-   Una aplicación web y una base de datos de [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] deben existir.  
  
-   La característica Data Quality Services y Data Quality Client deben estar instalados en la misma instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que hospeda la base de datos MDS. Para más información, consulte [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).  
  
### <a name="to-enable-data-quality-services-integration"></a>Para habilitar la integración con Data Quality Services  
  
1.  Abra [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
2.  En el panel izquierdo, haga clic en **Configuración web**.  
  
3.  En la página **Configuración web** , seleccione el sitio web y la aplicación web.  
  
4.  En la sección **Habilitar la integración DQS** , haga clic en **Habilitar la integración con Data Quality Services**.  
  
5.  En el cuadro de diálogo de confirmación, haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Consulte también  
 [Coincidencia de calidad de datos en el Complemento MDS para Excel](../microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Complemento Master Data Services para Microsoft Excel](../microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)   
 [Instalar Master Data Services](install-master-data-services.md)  
  
  
