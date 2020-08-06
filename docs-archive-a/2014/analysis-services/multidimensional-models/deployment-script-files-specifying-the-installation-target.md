---
title: Especificando el destino de la instalación | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input files [Analysis Services]
- installation targets [Analysis Services]
- Analysis Services deployments, installation targets
- Analysis Services Deployment Wizard, installation targets
- deploying [Analysis Services], installation targets
- modifying installation targets
ms.assetid: cb706817-6f63-4771-92c3-b70030bbce3d
author: minewiskan
ms.author: owend
ms.openlocfilehash: e830fc353898e3ec835b338e84765a0cad0de43f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673932"
---
# <a name="specifying-the-installation-target"></a>Especificar el destino de instalación
  El [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Asistente para la implementación de Lee la información de destino de la instalación del \<*project name*> archivo. deploymenttargets. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]crea este archivo al compilar el [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] proyecto. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]usa la base de datos y el servidor especificados en la página **implementación** del *\<project name>* cuadro de diálogo páginas de **propiedades** para crear el \<*project name*> archivo. targets.  
  
## <a name="modifying-the-installation-target-for-deployment"></a>Modificar el destino de instalación para la implementación  
 En algunas situaciones, puede que necesite implementar un proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en una base de datos o en una instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] que sea diferente a la especificada en la página **Implementación** . Por ejemplo, puede que desee implementar el proyecto en un servidor para realizar pruebas antes de la implementación y, a continuación, implementarlo en un servidor de producción. Puede que también desee implementar un proyecto finalizado y probado en varios servidores de producción de un clúster de equilibrio de carga de red (NLB), o en un servidor de ensayo y un servidor de producción.  
  
 Para implementar un proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en una base de datos o una instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] diferentes, puede cambiar el destino de instalación del archivo de entrada mediante uno de los métodos descritos en el siguiente procedimiento.  
  
#### <a name="to-change-the-installation-target-after-the-input-files-have-been-generated"></a>Para cambiar el destino de instalación después de haber generado los archivos de entrada  
  
-   Ejecute el Asistente para la implementación de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de forma interactiva. En la página **Destino de instalación** , especifique un nuevo destino para la instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] y la base de datos.  
  
     O bien  
  
-   Ejecute el Asistente para la implementación de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en el símbolo del sistema y ajuste el asistente de manera que se ejecute en modo de archivo de respuesta. Para obtener más información acerca del modo de archivo de respuesta, vea [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md).  
  
     O bien  
  
-   Modifique el \<*project name*> archivo. deploymenttargets con cualquier editor de texto.  
  
## <a name="see-also"></a>Consulte también  
 [Especificar las opciones de implementación de roles y particiones](deployment-script-files-partition-and-role-deployment-options.md)   
 [Especificar los valores de configuración para la implementación de la solución](deployment-script-files-solution-deployment-config-settings.md)   
 [Especificar opciones de procesamiento](deployment-script-files-specifying-processing-options.md)  
  
  
