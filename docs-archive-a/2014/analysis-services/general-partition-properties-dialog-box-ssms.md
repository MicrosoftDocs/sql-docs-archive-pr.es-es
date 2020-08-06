---
title: General (cuadro de diálogo Propiedades de la partición) (SSMS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.partitionproperties.general.f1
ms.assetid: efb505be-354f-4d23-8f2d-3e76fa50d27b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6fd64197b34cb52673c2389456257e92e30c41e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669964"
---
# <a name="general-partition-properties-dialog-box-ssms"></a>General (cuadro de diálogo Propiedades de la partición, SSMS)
  Use la página **General** del cuadro de diálogo **Propiedades de la partición** en SQL Server Management Studio para establecer las propiedades generales de una partición en un grupo de medida para un cubo de una base de datos de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
## <a name="options"></a>Opciones  
  
|Término|Definición|  
|----------|----------------|  
|**Id. de diseño de agregaciones**|Muestra el identificador del diseño de agregaciones utilizado por la partición.|  
|**Prefijo de agregación**|Muestra el prefijo predeterminado de las instancias de agregación que contiene la partición.|  
|**Marca de tiempo de creación**|Muestra la fecha y hora en que se creó la partición.|  
|**Modo de almacenamiento actual**|Muestra el modo de almacenamiento actual de la partición.<br /><br /> Nota: Este modo puede variar en función de la configuración del almacenamiento en caché automático de la partición. Para más información sobre almacenamiento en caché automático, vea [Almacenamiento en caché automático &#40;Particiones&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).|  
|**Descripción**|Escriba o modifique la descripción de la partición.|  
|**Filas estimadas**|Escriba el número estimado de filas del origen de datos subyacente representadas por la partición. Este valor se utiliza durante el procesamiento para estimar el tiempo y el almacenamiento necesarios para procesar la partición.|  
|**Tamaño estimado**|Muestra el tamaño estimado de la partición.|  
|**ID**|Muestra el identificador de la partición.|  
|**Procesado por última vez**|Muestra la fecha y la hora de la última vez en que se procesó la partición.|  
|**Última actualización de esquema**|Muestra la fecha y la hora de la última vez en que se actualizaron los metadatos de la partición.|  
|**Nombre**|Muestra el nombre de la partición.|  
|**Modo de procesamiento**|Seleccione el modo de procesamiento para la partición. Para obtener más información sobre los modos de procesamiento de los [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objetos, vea [procesamiento de objetos de modelo multidimensional](multidimensional-models/processing-a-multidimensional-model-analysis-services.md).|  
|**Id. de origen de datos remoto**|Muestra el identificador del origen de datos remoto desde el que se recuperan los datos de origen para la partición.<br /><br /> Nota: Esta propiedad contiene un valor únicamente para las particiones remotas.|  
|**Segmento**|Muestra la expresión que identifica el segmento de datos representado por la partición.|  
|**Origen**|Muestra la tabla o consulta que proporciona el origen de datos para la partición.|  
|**State**|Muestra el estado de procesamiento actual de la partición.|  
|**Ubicación de almacenamiento**|Muestra la carpeta en la que se almacenan los datos de la partición.<br /><br /> Nota: Esta propiedad solo contiene un valor si se ha especificado una ubicación de almacenamiento distinta de la ubicación de almacenamiento predeterminada de la instancia de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .|  
|**Tipo**|Muestra el tipo de la partición.|  
  
## <a name="see-also"></a>Consulte también  
 [Particiones &#40;Analysis Services de datos multidimensionales&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)   
 [Particiones remotas](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md)   
 [Cuadro de diálogo Propiedades de la partición &#40;SSMS&#41;](partition-properties-dialog-box-ssms.md)   
 [Selección &#40;cuadro de diálogo Propiedades de la partición&#41; &#40;SSMS&#41;](selection-partition-properties-dialog-box-ssms.md)   
 [Cuadro de diálogo Propiedades de la partición del almacenamiento en caché automático &#40;&#41; &#40;SSMS&#41;](proactive-caching-partition-properties-dialog-box-ssms.md)   
 [Configuración de errores para el procesamiento de cubos, particiones y dimensiones &#40;SSAS-multidimensional&#41;](multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md)  
  
  
