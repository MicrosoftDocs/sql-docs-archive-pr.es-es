---
title: Procesamiento de objetos del modelo multidimensional | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- online mode [Analysis Services]
- processing objects [Analysis Services]
- partitions [Analysis Services], processing
- jobs [Analysis Services]
- objects [Analysis Services], processing
- reprocessing objects
- impact analysis [Analysis Services]
- dimensions [Analysis Services], processing
- project mode [Analysis Services]
- cubes [Analysis Services], processing
ms.assetid: 625aa5a6-aa09-4bac-be8a-778fa81c5a61
author: minewiskan
ms.author: owend
ms.openlocfilehash: e61ff8f80579bba59aced5de4e824f036d633cac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673918"
---
# <a name="multidimensional-model-object-processing"></a>Procesamiento de objetos del modelo multidimensional
  El procesamiento es el paso, o serie de pasos, en los que Analysis Services carga datos de un origen de datos relacional en un modelo multidimensional. Para los objetos que utilizan el almacenamiento MOLAP, los datos se guardan en el disco en la carpeta de archivos de base de datos. Para el almacenamiento ROLAP, el procesamiento se produce a petición, en respuesta a una consulta MDX en un objeto. Para los objetos que utilizan el almacenamiento ROLAP, el procesamiento hace referencia a la actualización de la memoria caché antes de devolver los resultados de la consulta.  
  
 De forma predeterminada, el procesamiento aparece cuando se implementa una solución al servidor. También puede procesar toda o parte de una solución, ya sea de modo ad hoc mediante herramientas como [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] o [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], o según una programación utilizando [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] y el Agente SQL Server. Al realizar un cambio estructural en el modelo, como quitar una dimensión o cambiar el nivel de compatibilidad, deberá procesarse de nuevo para sincronizar los aspectos físicos y lógicos del modelo.  
  
 Este tema incluye las siguientes secciones:  
  
 [Requisitos previos](#bkmk_prereq)  
  
 [Elegir una herramienta o un enfoque](#bkmk_tool)  
  
 [Procesar objetos](#bkmk_proc)  
  
 [Volver a procesar objetos](#bkmk_reproc)  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> Requisitos previos  
  
-   El procesamiento requiere permisos administrativos en la instancia de Analysis Services. Si está procesando de forma interactiva desde [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] o [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], debe ser miembro del rol de administrador de servidor de la instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Para el procesamiento que se ejecuta de forma desatendida, por ejemplo mediante un paquete de SSIS que se programa mediante el Agente SQL Server, la cuenta utilizada para ejecutar el paquete debe ser miembro del rol administrador del servidor. Para obtener más información acerca de cómo establecer permisos de administrador, vea [conceder permisos de administrador de servidor &#40;Analysis Services&#41;](../instances/grant-server-admin-rights-to-an-analysis-services-instance.md).  
  
-   La cuenta utilizada para recuperar los datos se especifica en el objeto de origen de datos, ya sea como opción de suplantación si utiliza la autenticación de Windows, o como el nombre de usuario en la cadena de conexión si utiliza la autenticación de base de datos. La cuenta debe tener permisos de lectura en orígenes de datos relacionales que utiliza el modelo.  
  
-   El proyecto o la solución se deben implementar para poder procesar objetos.  
  
     Inicialmente, en las primeras fases del desarrollo del modelo, la implementación y la procesamiento se producen conjuntamente. Sin embargo, puede establecer opciones para procesar el modelo más adelante, después de implementar la solución. Para obtener más información sobre la implementación, vea [Implementar proyectos de Analysis Services &#40;SSDT&#41;](deploy-analysis-services-projects-ssdt.md).  
  
##  <a name="choosing-a-tool-or-approach"></a><a name="bkmk_tool"></a>Elegir una herramienta o un enfoque  
 Puede procesar objetos de forma interactiva mediante una aplicación cliente como [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] o [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], o una operación incluida en un script que se ejecuta como un trabajo del Agente SQL Server o un paquete de [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 La forma de procesar una base de datos varía considerablemente dependiendo de si el modelo se encuentra en desarrollo activo o en producción. Una vez implementado un modelo en un servidor de producción, el procesamiento debe controlarse rigurosamente para garantizar la integridad y la disponibilidad de los datos multidimensionales. Dado que los objetos son interdependientes, el procesamiento suele tener un efecto en cascada en el modelo cuando se procesan otros objetos o no se procesan en tándem. Si algunos objetos permanecen en estado no procesado, las consultas correspondientes a esos datos no se resolverán, interrumpiendo los informes o las aplicaciones que los usan. Cuando se desarrolla una estrategia para procesar una base de datos de producción, considere la posibilidad de usar el script o los paquetes de [!INCLUDE[ssIS](../../includes/ssis-md.md)] que ha depurado y probado para evitar errores de operador o la omisión de pasos.  
  
 Para obtener más información, vea [Herramientas y enfoques de procesamiento &#40;Analysis Services&#41;](tools-and-approaches-for-processing-analysis-services.md).  
  
##  <a name="processing-objects"></a><a name="bkmk_proc"></a>Procesar objetos  
 El procesamiento afecta a los siguientes objetos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] : grupos de medida, particiones, dimensiones, cubos, modelos de minería de datos, estructuras de minería de datos y bases de datos. Cuando un objeto contiene uno o más objetos, el procesamiento del objeto del nivel más alto provoca una cascada de procesamiento de todos los objetos de nivel inferior. Por ejemplo, un cubo suele contener uno o más grupos de medida (cada uno de los cuales contiene una o varias particiones) y dimensiones. El procesamiento de un cubo hace que se procesen todos los grupos de medida de un cubo y las dimensiones que lo constituyen y que actualmente están en estado no procesado. Para obtener más información sobre el procesamiento de objetos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , vea [Procesar objetos de Analysis Services](processing-analysis-services-objects.md).  
  
 Mientras el trabajo de procesamiento está en funcionamiento, se puede obtener acceso a los objetos afectados de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] para realizar consultas. El trabajo de procesamiento funciona dentro de una transacción y la transacción se puede confirmar o revertir. Si se produce un error en el trabajo de procesamiento, la transacción se revierte. Si el trabajo de procesamiento se realiza correctamente, se aplica un bloqueo exclusivo al objeto al confirmar los cambios, lo que significa que el objeto no está disponible temporalmente para consultas o procesamiento. Durante la fase de confirmación de la transacción, se pueden seguir enviando consultas al objeto, pero se pondrán en cola hasta que la confirmación se complete.  
  
 Durante un trabajo de procesamiento, si se procesa un objeto, y la manera en que se procesará, depende de la opción de procesamiento que se establece para dicho objeto. Para obtener más información sobre las opciones específicas de procesamiento que se pueden aplicar a cada objeto, vea [Opciones y valores de procesamiento &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md).  
  
##  <a name="reprocessing-objects"></a><a name="bkmk_reproc"></a>Volver a procesar objetos  
 Los cubos que contienen elementos sin procesar se deben volver a procesar antes de poder examinarlos. Los cubos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] contienen grupos de medida y particiones que se deben procesar antes de que el cubo se pueda consultar. El procesamiento de un cubo hace que [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] procese las dimensiones del cubo que lo constituyen, si dichas dimensiones están en un estado sin procesar. Una vez procesado un objeto por primera vez, debe volver a procesarse parcial o completamente cuando se produzca una de estas situaciones:  
  
-   La estructura del objeto se modifica, por ejemplo, quitando una columna en una tabla de hechos.  
  
-   Cambia el diseño de agregaciones del objeto.  
  
-   Deben actualizarse los datos del objeto.  
  
 Si procesa objetos en [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], puede seleccionar una opción de procesamiento o puede habilitar [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] para que determine el tipo de procesamiento adecuado. Los métodos de procesamiento disponibles difieren de un objeto a otro y se basan en el tipo de objeto. Además, los métodos disponibles se basan en los cambios producidos en el objeto desde el último procesamiento. Si habilita [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] para seleccionar automáticamente un método de procesamiento, el programa utilizará el método que devuelve el objeto a un estado totalmente procesado en el menor tiempo posible. Para más información, vea [Opciones y valores de procesamiento &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md).  
  
## <a name="see-also"></a>Consulte también  
 [Arquitectura lógica &#40;Analysis Services de datos multidimensionales&#41;](olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Objetos de base de datos &#40;Analysis Services - Datos multidimensionales&#41;](olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  
