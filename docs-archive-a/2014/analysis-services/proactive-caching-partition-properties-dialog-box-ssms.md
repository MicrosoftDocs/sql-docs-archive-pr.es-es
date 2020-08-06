---
title: Almacenamiento en caché automático (cuadro de diálogo Propiedades de la partición) (SSMS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.partitionproperties.proactivecaching.f1
ms.assetid: ecba72a3-703f-4ede-9d85-9a3318a749e5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8dae559ad1229407ca39744e52d8ee6842069075
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750266"
---
# <a name="proactive-caching-partition-properties-dialog-box-ssms"></a>Almacenamiento en caché automático (cuadro de diálogo Propiedades de la partición, SSMS)
  Utilice la página **Almacenamiento en caché automático** del cuadro de diálogo **Propiedades de la partición** de SQL Server Management Studio para definir las propiedades de almacenamiento y de almacenamiento en caché automático de una partición en un grupo de medida para un cubo de una base de datos de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
## <a name="options"></a>Opciones  
 **Configuración estándar**  
 Seleccione esta opción para habilitar el control deslizante de la opción **Configuración estándar** y utilice los parámetros de configuración predefinidos para el modo de almacenamiento y las características de almacenamiento en caché automático.  
  
 **Configuración estándar**  
 Establezca uno de los parámetros de configuración predefinidos que se indican en la tabla siguiente.  
  
|Configuración|Descripción|  
|-------------|-----------------|  
|**ROLAP en tiempo real**|Seleccione esta opción para utilizar los siguientes parámetros de configuración de almacenamiento y almacenamiento en caché automático:<br /><br /> Modo de almacenamiento ROLAP.<br /><br /> Habilitar el almacenamiento en caché automático.<br /><br /> Quitar la caché no actualizada, con un período de latencia de 0 segundos.<br /><br /> Colocar el objeto en línea de forma inmediata.|  
|**HOLAP en tiempo real**|Seleccione esta opción para utilizar los siguientes parámetros de configuración de almacenamiento y almacenamiento en caché automático:<br /><br /> Modo de almacenamiento HOLAP.<br /><br /> Habilitar el almacenamiento en caché automático.<br /><br /> Quitar la caché no actualizada, con un período de latencia de 0 segundos.<br /><br /> Actualizar la caché cuando los datos sufren cambios, con un intervalo de latencia de 0 segundos y sin reemplazo de intervalo de latencia.<br /><br /> Colocar el objeto en línea de forma inmediata.|  
|**MOLAP de latencia baja**|Seleccione esta opción para utilizar los siguientes parámetros de configuración de almacenamiento y almacenamiento en caché automático:<br /><br /> Modo de almacenamiento MOLAP.<br /><br /> Habilitar el almacenamiento en caché automático.<br /><br /> Quitar la caché no actualizada, con un período de latencia de 30 minutos.<br /><br /> Actualiza el almacenamiento en caché cuando cambian los datos, con un intervalo de latencia de 10 segundos y un reemplazo de intervalo de latencia de 10 minutos.<br /><br /> Actualiza el almacenamiento en caché cuando cambian los datos, con un intervalo de latencia de 10 segundos y un reemplazo de intervalo de latencia de 10 minutos.<br /><br /> Colocar el objeto en línea de forma inmediata.|  
|**MOLAP de latencia media**|Seleccione el objeto useBrings en línea inmediatamente.<br /><br /> la siguiente configuración de almacenamiento y almacenamiento en caché automático:<br /><br /> Modo de almacenamiento MOLAP.<br /><br /> Habilitar el almacenamiento en caché automático.<br /><br /> Quita la caché no actualizada, con un periodo de latencia de 4 horas.<br /><br /> Actualiza el almacenamiento en caché cuando cambian los datos, con un intervalo de latencia de 10 segundos y un reemplazo de intervalo de latencia de 10 minutos.<br /><br /> Colocar el objeto en línea de forma inmediata.|  
|**MOLAP automático**|Seleccione esta opción para utilizar los siguientes parámetros de configuración de almacenamiento y almacenamiento en caché automático:<br /><br /> Modo de almacenamiento MOLAP.<br /><br /> Habilitar el almacenamiento en caché automático.<br /><br /> Actualizar la caché cuando los datos sufren cambios, con un intervalo de latencia de 0 segundos y sin reemplazo de intervalo de latencia.|  
|**MOLAP programado**|Seleccione esta opción para utilizar los siguientes parámetros de configuración de almacenamiento y almacenamiento en caché automático:<br /><br /> Modo de almacenamiento MOLAP<br /><br /> Habilita el almacenamiento en caché automático<br /><br /> Actualiza la caché de forma periódica, con un intervalo de regeneración de 1 día|  
|**MOLAP**|Seleccione esta opción para utilizar los siguientes parámetros de configuración de almacenamiento y almacenamiento en caché automático:<br /><br /> Modo de almacenamiento MOLAP.|  
  
 **Configuración personalizada**  
 Seleccione esta opción para establecer de forma explícita las opciones de modo de almacenamiento, almacenamiento en caché automático y notificación.  
  
 **Opciones**  
 Haga clic para abrir el cuadro de diálogo **Opciones de almacenamiento** para establecer explícitamente las opciones de modo de almacenamiento, almacenamiento en caché automático y notificación. Para más información, sobre el cuadro de diálogo **Opciones de almacenamiento**, vea [Cuadro de diálogo Opciones de almacenamiento &#40;Analysis Services - Datos multidimensionales&#41;](storage-options-dialog-box-analysis-services-multidimensional-data.md).  
  
## <a name="see-also"></a>Consulte también  
 [Almacenamiento en caché automático &#40;particiones&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)   
 [Cuadro de diálogo Propiedades de la partición &#40;SSMS&#41;](partition-properties-dialog-box-ssms.md)   
 [Selección &#40;cuadro de diálogo Propiedades de la partición&#41; &#40;SSMS&#41;](selection-partition-properties-dialog-box-ssms.md)   
 [Cuadro de diálogo Propiedades de la partición de &#40;general&#41; &#40;SSMS&#41;](general-partition-properties-dialog-box-ssms.md)   
 [Configuración de errores para el procesamiento de cubos, particiones y dimensiones &#40;SSAS-multidimensional&#41;](multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md)  
  
  
