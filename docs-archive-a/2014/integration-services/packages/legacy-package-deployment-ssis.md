---
title: Implementación de paquetes (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, deploying
- deploying packages [Integration Services]
- SQL Server Integration Services packages, deploying
- deploying packages [Integration Services], about deploying packages
- packages [Integration Services], deploying
- SSIS packages, deploying
ms.assetid: 0f5fc7be-e37e-4ecd-ba99-697c8ae3436f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 32627eddf5e7a696decd549e9b87ebb5c3b9d031
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674192"
---
# <a name="package-deployment-ssis"></a>Implementación de paquetes (SSIS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] incluye herramientas y asistentes para facilitar la implementación de paquetes del equipo de desarrollo en el servidor de producción o en otros equipos.  
  
 El proceso de implementación de paquetes consta de cuatro pasos:  
  
1.  El primer paso es opcional e implica crear configuraciones de paquetes que actualizan las propiedades de los elementos de los paquetes en tiempo de ejecución. Las configuraciones se incluyen automáticamente al implementar los paquetes.  
  
2.  El segundo paso es generar el proyecto de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] para crear una utilidad de implementación de paquetes. La utilidad de implementación del proyecto contiene los paquetes que desea implementar.  
  
3.  El tercer paso es copiar la carpeta de implementación que se creó al generar el proyecto de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] en el equipo de destino.  
  
4.  El cuarto paso es ejecutar en el equipo de destino el Asistente para la instalación de paquetes con el fin de instalar los paquetes en el sistema de archivos o en una sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="related-tasks"></a>Related Tasks  
 Para obtener información sobre cómo crear una utilidad de implementación, vea [Crear una utilidad de implementación](../create-a-deployment-utility.md).  
  
 Para obtener información sobre cómo implementar paquetes mediante la utilidad de implementación, vea [Implementar los paquetes mediante la utilidad de implementación](../deploy-packages-by-using-the-deployment-utility.md).  
  
 Para obtener información sobre cómo crear configuraciones de paquete, vea [Crear configuraciones de paquetes](../create-package-configurations.md).  
  
  
