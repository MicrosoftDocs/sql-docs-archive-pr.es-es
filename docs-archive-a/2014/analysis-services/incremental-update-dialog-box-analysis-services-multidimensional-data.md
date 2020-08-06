---
title: Cuadro de diálogo actualización incremental (Analysis Services-datos multidimensionales) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.incrementalupdate.f1
ms.assetid: d5a5ae27-44e7-4179-b9e2-efbf21d6c5f5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6115a5123fd6e72cee0ebccaac5f539be8aebfbe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676712"
---
# <a name="incremental-update-dialog-box-analysis-services---multidimensional-data"></a>Cuadro de diálogo Actualización incremental (Analysis Services - Datos multidimensionales)
  Use el cuadro de diálogo **Actualización incremental** en [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] y [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] para definir la configuración que se utiliza cuando los grupos de medidas y particiones se actualizan de forma incremental. Se puede mostrar el cuadro de diálogo **Actualización incremental** haciendo clic en **Configurar** en la columna **Configuración** de la cuadrícula **Lista de objetos** del cuadro de diálogo **Procesar** .  
  
## <a name="options"></a>Opciones  
  
|Término|Definición|  
|----------|----------------|  
|**Grupo de medida**|Seleccione el grupo de medida que se va a actualizar incrementalmente.<br /><br /> Nota: Esta opción está habilitada únicamente si se está actualizando incrementalmente un cubo. Si está actualizando incrementalmente una partición o un grupo de medida, esta opción está deshabilitada.|  
|**Partición**|Seleccione la partición que se va a actualizar.<br /><br /> Nota: Esta opción está habilitada únicamente si se está actualizando incrementalmente un cubo. Si está actualizando incrementalmente una partición o un grupo de medida, esta opción está deshabilitada.|  
|**Tabla**|Haga clic para actualizar el objeto de una tabla.|  
|**Origen de datos o vista**|Seleccione el origen de datos o la vista del origen de datos en la que se encuentra la tabla de origen.<br /><br /> Nota: Esta opción solo está habilitada si se ha seleccionado **Tabla** .|  
|**Esquema y nombre de tabla**|Seleccione la tabla de origen utilizada para recuperar los datos para actualizar incrementalmente el cubo, grupo de medida o partición.<br /><br /> Nota: Esta opción solo está habilitada si se ha seleccionado **Tabla** .|  
|**Consultar**|Haga clic para actualizar el objeto de una consulta.|  
|**Data Source** (Origen de datos)|Seleccione el origen de datos en los que se encuentran las tablas que se van a consultar.<br /><br /> Nota: Esta opción solo está habilitada si se ha seleccionado **Consulta** .|  
|**Texto de la consulta**|Escriba el texto de la consulta utilizada para recuperar los datos para actualizar incrementalmente el cubo, grupo de medida o partición.<br /><br /> Nota: Esta opción solo está habilitada si se ha seleccionado **Consulta** .|  
  
## <a name="see-also"></a>Consulte también  
 [Analysis Services diseñadores y cuadros de diálogo &#40;datos multidimensionales&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Cuadro de diálogo procesar &#40;Analysis Services-datos multidimensionales&#41;](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  
