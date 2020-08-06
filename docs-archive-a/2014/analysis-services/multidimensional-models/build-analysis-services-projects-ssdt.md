---
title: Compilar proyectos de Analysis Services (SSDT) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- projects [Analysis Services], building
- Business Intelligence Development Studio, project building [Analysis Services]
ms.assetid: caac03cb-b2b4-4652-8913-3dd39c4b0127
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0e447da20df3d7894df1a9afcf4888a4d9799e37
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748383"
---
# <a name="build-analysis-services-projects-ssdt"></a>Generar proyectos de Analysis Services (SSDT)
  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], los proyectos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] se generan de forma muy similar a como se generan los proyectos de programación de Visual Studio. Al generar el proyecto, se crea un conjunto de archivos XML en el directorio de salida. Estos archivos XML usan el Lenguaje de scripting de Analysis Services (ASSL), que es el dialecto XML que usan las aplicaciones cliente, incluidos [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] y [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , para comunicarse con una instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] a fin de crear o modificar objetos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Los archivos XML se usan para implementar definiciones de objetos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de un proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en una instancia especificada de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
## <a name="building-a-project"></a>Generar un proyecto  
 Al generar un proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] generará un conjunto completo de archivos XML en la carpeta de salida con todos los comandos ASSL necesarios para generar todos los objetos de base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en el proyecto. Si el proyecto ya se había generado y se había especificado la implementación incremental para la configuración activa, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] generará también un archivo XML con los comandos ASSL para realizar una actualización incremental en los objetos implementados. Este archivo XML se escribe en la carpeta ..\obj\\<configuración activa\> del proyecto. Las generaciones incrementales pueden ahorrar tiempo al implementar y procesar proyectos o bases de datos de gran tamaño.  
  
> [!NOTE]  
>  Puede usar el comando Volver a generar todo para omitir la opción de implementación incremental.  
  
 La generación de un proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] valida las definiciones de objetos del proyecto. La validación incluye los ensamblados a los que se hace referencia. Los errores de generación se muestran en la ventana Lista de tareas, junto con el texto de error de Objetos de administración de análisis (AMO). Puede hacer clic en un error para abrir el diseñador necesario para solucionarlo.  
  
 La validación correcta no garantiza que los objetos se puedan crear en el servidor de destino durante la implementación ni se puedan procesar correctamente tras la implementación. Los siguientes problemas pueden evitar la implementación o el procesamiento correctos tras la implementación:  
  
-   No se realizan comprobaciones de seguridad en el servidor, por lo que los bloqueos pueden evitar la implementación.  
  
-   Las ubicaciones físicas no se validan en el servidor.  
  
-   Los detalles de las vistas del origen de datos no se comprueban en el origen de datos real del servidor de destino.  
  
 Si la validación es correcta, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] genera los archivos XML. Después de la generación, la carpeta de salida contiene los archivos descritos en la siguiente tabla.  
  
|Archivos (en la carpeta BIN)|Descripción|  
|-----------------------------|-----------------|  
|*nombre de proyecto*.asdatabase|Contiene los elementos ASSL que definen los metadatos de los objetos del proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en un archivo de script de implementación. El motor de implementación utiliza este archivo para implementar los objetos en una base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|*nombre de proyecto*.configsettings|Contiene las opciones de configuración usadas en la implementación que se pueden modificar directamente o en el Asistente para la implementación de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (por ejemplo, la cadena de conexión de los orígenes de datos).|  
|*nombre de proyecto*.deploymenttargets|Contiene la configuración de destino utilizada en la implementación que puede modificar directamente o en el Asistente para la implementación de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (por ejemplo, los nombres del servidor y la base de datos).|  
|*nombre de proyecto*.deploymentoptions|Contiene diversas opciones de configuración usadas en la implementación que se pueden modificar directamente o en el Asistente para la implementación de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (por ejemplo, ubicaciones de almacenamiento)|  
|*AssemblyName* / *DllName.* dll|Hay carpetas independientes para cada ensamblado al que se hace referencia; cada carpeta contiene el archivo DLL del ensamblado, los ensamblados a los que se hace referencia y los archivos .pdb asociados para la información de depuración del resultado.|  
  
|Archivos (en la carpeta OBJ)|Descripción|  
|-----------------------------|-----------------|  
|\<Configuration Name>\LastBuilt.xml|Contiene la marca de tiempo y el código hash que identifica la última vez que se generó el proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
  
 Estos archivos XML no contienen \<Create> etiquetas y \<Alter> , que se crean durante la implementación.  
  
 Los ensamblados a los que se hace referencia (excepto los ensamblados estándar del sistema y de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ) también se copian en el directorio de salida. Si hay referencias a otros proyectos de una solución, dichos proyectos se generan primero, con la configuración de proyecto adecuada y las dependencias de generación establecidas por las referencias a proyectos; a continuación, los proyectos a los que se hace referencia se copian en la carpeta de salida del proyecto.  
  
## <a name="see-also"></a>Consulte también  
 [Referencia de ASSL&#41; &#40;de lenguaje de scripting Analysis Services](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)   
 [Implementar proyectos de Analysis Services &#40;SSDT&#41;](deploy-analysis-services-projects-ssdt.md)  
  
  
