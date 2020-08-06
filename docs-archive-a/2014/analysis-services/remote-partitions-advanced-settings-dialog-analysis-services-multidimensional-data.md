---
title: Particiones remotas-cuadro de diálogo Configuración avanzada (Analysis Services-datos multidimensionales) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.advancedrestoresettings.f1
ms.assetid: a03bb7e1-efaf-47c8-b0ee-f3e4438311cb
author: minewiskan
ms.author: owend
ms.openlocfilehash: e68aea7325094af7b60d4b3f0c8ca0cd9525df71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662265"
---
# <a name="remote-partitions---advanced-settings-dialog-box-analysis-services---multidimensional-data"></a>Particiones remotas - Cuadro de diálogo Configuración avanzada (Analysis Services - Datos multidimensionales)
  Use el cuadro de diálogo **Particiones remotas - Configuración avanzada** de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] para editar la configuración avanzada, como la cadena de conexión del origen de datos que representa la base de datos remota de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] que mantiene las particiones remotas, a la vez que restaura las particiones remotas desde un archivo de copia de seguridad remoto a una base de datos de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] mediante el cuadro de diálogo **Restaurar base de datos** . Puede mostrar el cuadro de diálogo **Particiones remotas - Configuración avanzada** desde la página **Particiones** del cuadro de diálogo **Restaurar base de datos** si hace clic en el botón de puntos suspensivos (**…**) de una partición remota tras seleccionar la opción **Restaurar particiones remotas** .  
  
## <a name="options"></a>Opciones  
  
|Término|Definición|  
|----------|----------------|  
|**Nombre del origen de datos**|Muestra el nombre del origen de datos que representa la base de datos remota de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] que administra las particiones remotas de la lista.|  
|**Archivo de copia de seguridad**|Muestra el nombre del archivo de copia de seguridad remoto que contiene los datos que se restaurarán para las particiones remotas de la lista.<br /><br /> Nota: no se muestra ningún archivo de copia de seguridad si se especificó un archivo de copia de seguridad remoto en la columna **archivo de copia** de seguridad en la página **particiones** del cuadro de diálogo **restaurar base de datos** .|  
|**Cadena de conexión**|Muestra la cadena de conexión para el origen de datos mostrado en **Nombre del origen de datos**.|  
|**Edición**|Haga clic para mostrar el cuadro de diálogo **Propiedades del vínculo de datos** y editar las propiedades contenidas en la cadena de conexión.|  
|**Lista de particiones**|Seleccione esta opción para especificar distintas ubicaciones en las que desea restaurar las particiones remotas. Tenga en cuenta que solo puede cambiar la carpeta de restauración de una partición remota si se ha especificado una ubicación distinta de la predeterminada para dicha partición remota en el cubo. La siguiente cuadrícula, que se habilita al seleccionar esta opción, se utiliza para especificar una carpeta de restauración para cada partición remota:<br /><br /> **Cubo**: muestra el nombre del cubo que contiene la partición remota.<br /><br /> **MeasureGroup**: muestra el nombre del grupo de medida que contiene la partición remota.<br /><br /> **Partición**: muestra el nombre de la partición remota.<br /><br /> **Tamaño (MB)**: muestra el tamaño, en megabytes, de la partición remota.<br /><br /> **Carpeta original**: muestra el nombre de la carpeta original en la que se almacenó la partición remota.<br /><br /> **Carpeta de restauración**: escriba el nombre de la carpeta de restauración para la partición remota o haga clic en el botón de puntos suspensivos (**...**) para mostrar el cuadro de diálogo **Buscar carpeta remota** y seleccione la ruta de acceso de la carpeta que desea usar. Para obtener más información sobre el cuadro de diálogo **Buscar carpeta remota**, vea [Cuadro de diálogo Buscar carpeta remota &#40;Analysis Services - Datos multidimensionales&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md).|  
  
## <a name="see-also"></a>Consulte también  
 [Analysis Services diseñadores y cuadros de diálogo &#40;datos multidimensionales&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Particiones &#40;cuadro de diálogo restaurar base de datos&#41; &#40;Analysis Services-datos multidimensionales&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Realizar una copia de seguridad y restaurar las bases de datos de Analysis Services](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
