---
title: Descripción del script de implementación de Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services Deployment Wizard, scripts
- deploying [Analysis Services], scripts
- Analysis Services deployments, scripts
- scripts [Analysis Services], deployment
ms.assetid: a63ebee9-9848-48f1-82ad-64ecf2e47019
author: minewiskan
ms.author: owend
ms.openlocfilehash: 25df0b377918316e54a14787d7492a681c81778d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746006"
---
# <a name="understanding-the-analysis-services-deployment-script"></a>Descripción del script de implementación de Analysis Services
  El script de implementación XMLA generado por el Asistente para la implementación de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] está formado por dos secciones:  
  
-   La primera parte del script de implementación contiene los comandos necesarios para crear, modificar o eliminar los objetos adecuados [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en la base de datos de destino. De forma predeterminada, los archivos de entrada generados por el proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] se basan en una implementación incremental. En consecuencia, el script de implementación XMLA solamente afectará a los objetos que se cambiaron o se eliminaron.  
  
-   La segunda parte del script de implementación contiene los comandos necesarios para procesar únicamente los objetos creados o modificados en el servidor de destino (opción Procesar predeterminado) o para procesar completamente la base de datos de destino. Además, puede elegir que el script de implementación no contenga comandos de procesamiento.  
  
 El script de implementación completa se puede ejecutar en una única transacción o en varias transacciones. Si el script se ejecuta en varias transacciones, la primera parte del mismo se ejecuta en una única transacción y cada objeto se procesa en su propia transacción.  
  
> [!IMPORTANT]  
>  El Asistente para la implementación de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] solamente implementa los objetos en una sola base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . No implementa ningún objeto o datos en el nivel de servidor.  
  
## <a name="see-also"></a>Consulte también  
 [Ejecutar el Asistente para la implementación de Analysis Services](running-the-analysis-services-deployment-wizard.md)   
 [Comprender los archivos de entrada utilizados para crear el script de implementación](deployment-script-files-input-used-to-create-deployment-script.md)  
  
  
