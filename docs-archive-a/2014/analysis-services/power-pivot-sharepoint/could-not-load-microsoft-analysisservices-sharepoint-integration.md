---
title: No se pudo cargar el archivo o ensamblado &#39;Microsoft. Data. Services, version = 3.5.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089&#39; o una de sus dependencias. El sistema no encuentra el archivo especificado. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 81ed0f44-8782-462d-af8f-0ba5b975df27
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3f9eed7ad90c1e720d07c714e351c24ae6657717
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87675579"
---
# <a name="could-not-load-file-or-assembly-39microsoftdataservices-version3500-cultureneutral-publickeytokenb77a5c561934e08939-or-one-of-its-dependencies-the-system-cannot-find-the-file-specified"></a>No se pudo cargar el archivo o ensamblado &#39;Microsoft. Data. Services, version = 3.5.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089&#39; o una de sus dependencias. El sistema no encuentra el archivo especificado.
  En entornos de SharePoint 2010 que tienen PowerPivot para SharePoint, este error se producirá si intenta realizar la exportación de una fuente de distribución de datos y el sistema no tiene la versión necesaria de Microsoft ADO.NET Data Services.  
  
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Se aplica a|PowerPivot para SharePoint|  
|Versión del producto|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Causa|No se encontró ADO.NET Data Services 3.5 SP1.|  
|Texto del mensaje|No se puede cargar el archivo o ensamblado 'Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' ni una de sus dependencias. El sistema no encuentra el archivo especificado.|  
  
## <a name="explanation"></a>Explicación  
 SharePoint 2010 incluye un botón Exportar como fuente de distribución de datos que puede utilizar para exportar una lista de SharePoint como una fuente de distribución de datos XML. Además, tanto Reporting Services en el modo de SharePoint como PowerPivot para SharePoint admiten las características de fuentes de distribución de datos que requieren ADO.NET Data Services.  
  
 Si no está instalado ADO.NET Data Services, este error se producirá al solicitar una fuente de distribución de datos.  
  
## <a name="user-action"></a>Acción del usuario  
  
1.  Vaya a la documentación sobre los requisitos de hardware y software para SharePoint 2010, [determinar los requisitos de hardware y software (SharePoint 2010)](https://go.microsoft.com/fwlink/?LinkId=169734) ( https://go.microsoft.com/fwlink/?LinkId=169734) .  
  
2.  En **Instalar requisitos previos de software**, busque el vínculo de ADO.NET Data Services 3.5 correspondiente al sistema operativo que está usando.  
  
3.  Haga clic en el vínculo y ejecute el programa de instalación que instala el servicio.  
  
## <a name="see-also"></a>Consulte también  
 [Implementar las soluciones de PowerPivot en SharePoint](deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
