---
title: Trabajar con proyectos de Analysis Services y bases de datos en un entorno de producción | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, projects
ms.assetid: c589097f-ad29-4b97-8c7e-b8a910909c1a
author: minewiskan
ms.author: owend
ms.openlocfilehash: e9a2555511c422e5553662e2fcd292a5a2ec7c67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673343"
---
# <a name="working-with-analysis-services-projects-and-databases-in-a-production-environment"></a>Trabajar con bases de datos de proyectos de Analysis Services en un entorno de producción
  Una vez que haya desarrollado e implementado la base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] del proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en una instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , debe decidir cómo desea realizar cambios en los objetos de la base de datos implementada. Ciertos cambios, como los relacionados con los roles de seguridad, las particiones y la configuración del almacenamiento, se pueden hacer con [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Otros cambios, como la adición de atributos o jerarquías definidas por el usuario, solo se pueden hacer con [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]en el modo de proyecto o en el modo en línea.  
  
 Tan pronto como haga un cambio en una base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] implementada mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] en el modo en línea, el proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] que se usó para la implementación queda desusado. Si un programador hace cambios en el proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] y trata de implementar el proyecto modificado, se le solicitará que sobrescriba la base de datos completa. Si el programador sobrescribe toda la base de datos, también tiene que procesarla. Todo esto se puede complicar si los cambios realizados directamente en la base de datos implementada por el personal de producción no han sido comunicados al equipo de desarrollo, ya que este último no comprenderá por qué sus cambios ya no aparecen en la base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Las herramientas de SQL Server 2005 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] se pueden usar de varias maneras para evitar los problemas que conlleva esta situación.  
  
-   Método 1: siempre que se haga un cambio en una versión de producción de una base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , use [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] para crear un proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] basado en la versión modificada de la base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Este nuevo proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] se puede registrar en el sistema de control de origen como copia maestra del proyecto. Este método funcionará aunque el cambio se haya realizado en la base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] con [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] en el modo en línea.  
  
-   Método 2: realice los cambios únicamente en una versión de producción de una base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] con [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] en el modo de proyecto. Con este método, puede usar las opciones disponibles en el Asistente para la implementación de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] a fin de conservar los cambios realizados por [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], por ejemplo los roles de seguridad y la configuración del almacenamiento. Así se garantiza que la configuración relacionada con el diseño se conserva en el archivo del proyecto (la configuración del almacenamiento y los roles de seguridad se pueden omitir) y se usa el servidor en línea para la configuración del almacenamiento y los roles de seguridad.  
  
-   Método 3: realice los cambios únicamente en una versión de producción de una base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] con [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] en el modo en línea. Puesto que las dos herramientas solo trabajan con el mismo servidor en línea, no hay posibilidad de obtener versiones diferentes no sincronizadas.  
  
  
