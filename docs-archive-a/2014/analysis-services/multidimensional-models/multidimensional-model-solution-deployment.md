---
title: Implementación de soluciones de modelos multidimensionales | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services deployments, planning
- deploying [Analysis Services]
- deploying [Analysis Services], planning
ms.assetid: 7259c201-ff54-43e8-bda5-a6d51474e0e6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 638e211f261b0a8654dfbe2d8ab937aa3dee24d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87675601"
---
# <a name="multidimensional-model-solution-deployment"></a>Implementación de soluciones de modelos multidimensionales
  Una vez completado el desarrollo de un proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , puede implementar la base de datos en un servidor de Analysis Services. Analysis Services proporciona seis métodos de implementación posibles que se pueden usar para mover la base de datos a un servidor de prueba o de producción. Estos son los métodos de implementación, por orden de ventaja: automatización AMO, XMLA, Asistente para la implementación, Utilidad de implementación, Asistente para sincronizar y Copia de seguridad y restauración.  
  
 Este tema incluye las siguientes secciones:  
  
 [Métodos de implementación](#bkmk_meth)  
  
 [Consideraciones de la implementación](#bkmk_considerations)  
  
 [Tareas relacionadas](#bkmk_rel)  
  
##  <a name="deployment-methods"></a><a name="bkmk_meth"></a>Métodos de implementación  
  
|Método|Descripción|Vínculo|  
|------------|-----------------|----------|  
|**Automatización AMO (Objetos de administración de análisis)**|AMO ofrece una interfaz programática para el conjunto de comandos completo establecido para [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], incluidos los comandos que se pueden usar para la implementación de soluciones. Como método para la implementación de soluciones, la automatización AMO es el más flexible, pero también requiere un esfuerzo de programación.  Una ventaja clave de AMO es que puede usar el Agente SQL Server con la aplicación AMO para ejecutar la implementación siguiendo una programación preestablecida.|[Desarrollar con Objetos de administración de análisis &#40;AMO&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)|  
|**XMLA**|Use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] para generar un script XMLA de los metadatos de una base de datos existente de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] y, a continuación, ejecute el script en otro servidor para volver a crear la base de datos inicial. Los scripts XMLA se forman fácilmente en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] definiendo el proceso de implementación, codificándolo y guardándolo en un script XMLA. Una vez que se tiene un script XMLA en un archivo guardado, se puede ejecutar fácilmente de acuerdo con una programación, o bien se puede incrustar en una aplicación que se conecta directamente con una instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].<br /><br /> También se pueden ejecutar Scripts XMLA de forma preestablecida con el Agente SQL Server, pero este método no presenta la misma flexibilidad que AMO. AMO ofrece una mayor funcionalidad, al hospedar todo el espectro de comandos administrativos.|[Implementar soluciones de modelo mediante XMLA](deploy-model-solutions-using-xmla.md)|  
|**Asistente para la implementación**|Use el Asistente para la implementación cuando desee usar los archivos de salida XMLA generados por un proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] para implementar los metadatos del proyecto en un servidor de destino. Con el Asistente para la implementación, puede implementar directamente desde el archivo de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , tal como lo creó el directorio de salida en la compilación del proyecto.<br /><br /> La principal ventaja de usar el Asistente para la implementación de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] es la comodidad. Al igual que se puede guardar un script XMLA para su uso posterior en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], se pueden guardar los scripts del Asistente para la implementación. El Asistente para la implementación se puede ejecutar interactivamente y desde el símbolo del sistema mediante la utilidad de implementación.|[Implementar soluciones con el Asistente para la implementación](deploy-model-solutions-using-the-deployment-wizard.md)|  
|**Utilidad de implementación**|La utilidad de implementación le permite iniciar el motor de implementación de Analysis Services desde un símbolo del sistema.|[Implementar soluciones de modelos con la utilidad de implementación](deploy-model-solutions-with-the-deployment-utility.md)|  
|**Asistente para sincronizar bases de datos**|Use el Asistente para sincronizar bases de datos cuando desee sincronizar los metadatos y los datos de dos bases de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] cualquiera.<br /><br /> El Asistente para sincronizar se puede usar para copiar datos y metadatos de un servidor de origen en un servidor de destino. Si el servidor de destino no tiene una copia de la base de datos que desea implementar, se copia una nueva base de datos en el servidor de destino. Si el servidor de destino ya tiene una copia de la misma base de datos, la base de datos del servidor de destino se actualiza para que use los metadatos y los datos de la base de datos de origen.|[Sincronizar bases de datos de Analysis Services](synchronize-analysis-services-databases.md)|  
|**Copia de seguridad y restauración**|La copia de seguridad es la forma más simple de transferir bases de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Desde el cuadro de diálogo **Copia de seguridad**, puede establecer la configuración de las opciones y, a continuación, puede ejecutar la copia de seguridad desde el mismo cuadro de diálogo. O bien, puede crear un script que se puede guardar y ejecutar con la frecuencia necesaria.<br /><br /> Las copias de seguridad y restauración no se usan con la misma frecuencia que los otros métodos de implementación, pero es una forma de completar rápidamente una implementación con requisitos mínimos de infraestructura.|[Realizar una copia de seguridad y restaurar las bases de datos de Analysis Services](backup-and-restore-of-analysis-services-databases.md)|  
  
##  <a name="deployment-considerations"></a><a name="bkmk_considerations"></a>Consideraciones de implementación  
 Antes de implementar un proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , considere cuáles de estas preguntas se aplican a la solución y luego revise el vínculo relacionado para saber cómo solucionar el problema:  
  
|Consideración|Más información|  
|-------------------|------------------------------|  
|¿Qué recursos de hardware y software se requieren para esta solución?|[Requisitos y consideraciones para la implementación de Analysis Services](requirements-and-considerations-for-analysis-services-deployment.md)|  
|¿Cómo implementará los objetos relacionados que se encuentran fuera del ámbito del proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , como paquetes, informes o esquemas de las bases de datos relacionales de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ?||  
|¿Cómo cargará y actualizará los datos de la base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] implementada?<br /><br /> ¿Cómo actualizará los metadatos (por ejemplo, cálculos) de la base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] implementada?|[Métodos de implementación](#bkmk_meth) en este tema.|  
|¿Desea ofrecer a los usuarios acceso a los datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] a través de Internet?|[Configurar el acceso HTTP a Analysis Services en Internet Information Services &#40;IIS&#41; 8.0](../instances/configure-http-access-to-analysis-services-on-iis-8-0.md)|  
|¿Desea proporcionar acceso continuo de consulta a los datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ?|[Requisitos y consideraciones para la implementación de Analysis Services](requirements-and-considerations-for-analysis-services-deployment.md)|  
|¿Desea implementar objetos en un entorno distribuido mediante el uso de objetos vinculados o particiones remotas?|[Crear y administrar una partición local &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md), [Crear y administrar una partición remota &#40;Analysis Services&#41;](create-and-manage-a-remote-partition-analysis-services.md) y [Grupos de medida vinculados](linked-measure-groups.md).|  
|¿Cómo protegerá los datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ?|[Cómo autorizar el acceso a objetos y operaciones &#40;Analysis Services&#41;](authorizing-access-to-objects-and-operations-analysis-services.md)|  
  
##  <a name="related-tasks"></a><a name="bkmk_rel"></a> Tareas relacionadas  
 [Requisitos y consideraciones para la implementación de Analysis Services](requirements-and-considerations-for-analysis-services-deployment.md)  
  
 [Implementar soluciones de modelo mediante XMLA](deploy-model-solutions-using-xmla.md)  
  
 [Implementar soluciones con el Asistente para la implementación](deploy-model-solutions-using-the-deployment-wizard.md)  
  
 [Implementar soluciones de modelos con la utilidad de implementación](deploy-model-solutions-with-the-deployment-utility.md)  
  
  
