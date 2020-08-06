---
title: Procesar manualmente los datos (SSAS tabular) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.datarefreshprogressdb.f1
ms.assetid: 0918c04c-c1e6-45b4-acfa-96fa578e684b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 51bdb1b9535685db4fc35dbdd791e6b4d9bed1b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87675621"
---
# <a name="manually-process-data-ssas-tabular"></a>Procesar manualmente los datos (SSAS tabular)
  En este tema se describe cómo procesar manualmente los datos del área de trabajo en [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
 Si crea un modelo tabular que use datos externos, podrá actualizar manualmente los datos mediante el comando Procesar. Puede procesar una única tabla, todas las tablas del modelo o una o más particiones. Siempre que procese datos, puede que también tenga que volver a calcularlos.  Procesar los datos significa obtener los datos más recientes de los orígenes externos. Recalcular significa actualizar el resultado de cualquier fórmula que use los datos.  
  
 Secciones de este tema:  
  
-   [Procesar manualmente los datos](#bkmk_mahually_process)  
  
-   [Progreso del proceso de datos](#bkmk_data_process_progress)  
  
##  <a name="manually-process-data"></a><a name="bkmk_mahually_process"></a>Procesar manualmente los datos  
  
#### <a name="to-process-data-for-a-single-table-or-all-tables-in-a-model"></a>Para procesar los datos de una sola tabla o todas las tablas de un modelo  
  
1.  En el diseñador de modelos, haga clic en la tabla que desea procesar.  
  
2.  En el menú **Modelo** , haga clic en **Procesar**y, a continuación, haga clic en **Procesar** o en **Procesar todo**.  
  
#### <a name="to-process-data-for-all-tables-using-the-same-connection"></a>Para procesar los datos de todas las tablas utilizando la misma conexión  
  
1.  En [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], haga clic en el menú **Modelo** y, a continuación, en **Conexiones existentes**.  
  
2.  En el cuadro de diálogo **Conexiones existentes** , seleccione una conexión y, a continuación, haga clic en **Procesar**.  
  
#### <a name="to-process-data-for-one-or-more-partitions"></a>Para procesar los datos de una o más particiones  
  
1.  En [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], haga clic en el menú **Modelo** , seleccione **Procesar**y, a continuación, haga clic en **Procesar particiones**.  
  
2.  En el cuadro de diálogo **Procesar particiones** , en **Modo**, seleccione uno de los siguientes modos de procesamiento:  
  
    |Mode|Descripción|  
    |----------|-----------------|  
    |**Proceso predeterminado**|Detecta el estado de proceso de un objeto de partición y realiza el procesamiento necesario para devolver objetos de partición sin procesar o procesados parcialmente a un estado de procesamiento completo. Se cargan los datos de las tablas vacías y las particiones; se generan o se vuelven a generar las jerarquías, las columnas calculadas y las relaciones.|  
    |**Proceso completo**|Procesa un objeto de partición y todos los objetos que contiene. Cuando se ejecuta Proceso completo en un objeto que ya se ha procesado, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] quita todos los datos del objeto y, a continuación, lo procesa. Este tipo de procesamiento es necesario cuando se ha realizado un cambio estructural en un objeto.|  
    |**Procesar datos**|Carga datos en una partición o en una tabla sin volver a generar las jerarquías o las relaciones, ni volver a calcular las columnas calculadas y las medidas.|  
    |**Procesar borrado**|Quita todos los datos de una partición.|  
    |**Procesar adición**|Actualiza la partición con nuevos datos de forma incremental.|  
  
3.  En la lista Particiones, seleccione las particiones que desee procesar y haga clic en **Aceptar**.  
  
##  <a name="data-process-progress"></a><a name="bkmk_data_process_progress"></a> Progreso de procesamiento de datos  
 El cuadro de diálogo **Progreso de procesamiento de datos** le permite supervisar el procesamiento de los datos que ha importado en el modelo desde un origen externo. Para obtener acceso a este cuadro de diálogo, haga clic en el menú **Modelo** y, a continuación, en **Procesar particiones**, **Procesar tabla** o **Procesar todo**.  
  
 **Estado**  
 Indica si la operación de procesamiento fue correcta o no.  
  
 **Detalles**  
 Enumera las tablas y vistas que se importaron, el número de filas que se importaron y proporciona un vínculo a un informe de los problemas que se hayan producido.  
  
 **Detener actualización**  
 Haga clic aquí para detener la operación de procesamiento. Esta opción resulta útil si la operación tarda demasiado o hay demasiados errores.  
  
## <a name="see-also"></a>Consulte también  
 [Procesar datos &#40;SSAS tabular&#41;](process-data-ssas-tabular.md)   
 [Solucionar problemas del procesamiento de datos &#40;SSAS tabular&#41;](troubleshoot-process-data-ssas-tabular.md)  
  
  
