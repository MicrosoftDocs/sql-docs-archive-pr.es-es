---
title: Actualizar Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- upgrading databases
- databases [Analysis Services], upgrading
- installing Analysis Services, side-by-side installations
- Analysis Services upgrades
- Analysis Services upgrades, about upgrading Analysis Services
- SSAS, database migration
- upgrading Analysis Services
- installing Analysis Services, upgrading
- SSAS, upgrading
ms.assetid: a131d329-386e-4470-aaa9-ffcde4e5ec0c
author: Minewiskan
ms.author: owend
ms.openlocfilehash: 78bf7f27233bcfd46bc1f189324eddc72adcc961
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87671159"
---
# <a name="upgrade-analysis-services"></a>Actualizar Analysis Services
  Use el programa de instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para actualizar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para obtener información detallada sobre cómo actualizar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en modo de SharePoint, vea [Actualizar PowerPivot para SharePoint](upgrade-power-pivot-for-sharepoint.md). Para obtener más información acerca de la actualización de una instancia de SQL Server existente, consulte [actualización a SQL Server 2014 mediante el Asistente para la instalación &#40;&#41;de instalación ](upgrade-sql-server-using-the-installation-wizard-setup.md).  
  
## <a name="known-upgrade-issues"></a>Problemas de actualización conocidos  
 Antes de actualizarse a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], revise lo siguiente:  
  
-   [SQL Server notas](https://go.microsoft.com/fwlink/?LinkID=296445)de la versión de 2014.  
  
-   Para saber qué [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] características y funcionalidades se han dejado de usar, están en desuso o han cambiado, consulte [Analysis Services compatibilidad con versiones anteriores](https://docs.microsoft.com/analysis-services/analysis-services-backward-compatibility).  
  
## <a name="pre-upgrade-checklist"></a>Lista de comprobación previa a la actualización  
 Antes de actualizar, revise la información siguiente:  
  
-   [Actualizaciones de ediciones y versiones admitidas](supported-version-and-edition-upgrades.md)  
  
-   [Requisitos de hardware y software para instalar SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
-   [Comprobar los parámetros del Comprobador de configuración del sistema](check-parameters-for-the-system-configuration-checker.md)  
  
-   [Consideraciones de seguridad para una instalación de SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
-   [Realizar una copia de seguridad y restaurar las bases de datos de Analysis Services](https://docs.microsoft.com/analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases)  
  
-   [Usar el Asesor de actualizaciones para preparar las actualizaciones](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)  
  
## <a name="upgrading-analysis-services"></a>Actualizar Analysis Services  
 Puede elegir entre varios enfoques para actualizar el servidor y los datos:  
  
-   Una **actualización en contexto** reemplaza los archivos de programa existentes por [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] los archivos de programa. Las bases de datos permanecen en la misma ubicación. Las carpetas de programas se actualizan para reflejar el nuevo nombre.  
  
-   Una **actualización en paralelo** es una nueva instalación de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] en el mismo equipo que tiene una instancia de Analysis Services existente. Puede mover bases de datos a la nueva instancia en el mismo equipo y desinstalar después la versión anterior si ya no la utiliza.  
  
-   También puede instalar Analysis Services en el nuevo hardware y migrar después las bases de datos existentes a ese servidor.  
  
## <a name="in-place-upgrade"></a>Actualización en contexto  
 Puede actualizar una instancia existente de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] y, como parte del proceso de actualización, migrar automáticamente las bases de datos existentes de la antigua instancia a la nueva instancia de. Dado que los metadatos y los datos binarios son compatibles entre las dos versiones, después de actualizar se conservarán los datos y no es necesario migrarlos manualmente.  
  
 Para actualizar una instancia existente, ejecute el programa de instalación y especifique el nombre de la instancia existente como nombre de la nueva instancia.  
  
## <a name="upgrading-databases"></a>Actualizar bases de datos  
 Las bases de datos creadas en versiones anteriores de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] se ejecutan en el servidor actualizado con la configuración de nivel de compatibilidad de base de datos más antigua. Las bases de datos creadas en las siguientes versiones tienen un nivel de compatibilidad de base de datos de 105. Puede cambiar el nivel de compatibilidad si desea utilizar las características que requieren un nivel de compatibilidad de base de datos más reciente. De lo contrario, puede ejecutar las bases de datos del servidor actualizado utilizando la configuración original. Para obtener más información, vea [establecer el nivel de compatibilidad de una base de datos multidimensional &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services).  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
  
## <a name="see-also"></a>Consulte también  
 [Características admitidas por las ediciones de SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Planear una instalación de SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Descripción de la arquitectura OLAP de Microsoft](https://docs.microsoft.com/analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture)   
 [PowerPivot para SharePoint de actualización](upgrade-power-pivot-for-sharepoint.md)   
 [Instalar Analysis Services en modo multidimensional y de minería de datos](../../sql-server/install/install-analysis-services-in-multidimensional-and-data-mining-mode.md)   
 [Instalación de PowerPivot para SharePoint 2010](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
