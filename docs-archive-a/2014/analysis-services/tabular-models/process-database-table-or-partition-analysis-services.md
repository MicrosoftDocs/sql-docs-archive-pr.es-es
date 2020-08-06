---
title: Procesar base de datos, tabla o partición | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- SQL12.ASVS.SSMS.PARTITIONS.PROCESSINGOPTIONS.IMBI.F1
ms.assetid: 307d69c3-cabb-4dfa-b90c-9852492c1213
author: minewiskan
ms.author: owend
ms.openlocfilehash: b5d3840be43798536f1bb517007a7974a1e08728
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744340"
---
# <a name="process-database-table-or-partition"></a>Procesar base de datos, tabla o partición
  En las tareas de este tema se describe cómo procesar una base de datos de modelo tabular, una tabla o particiones manualmente mediante el cuadro de diálogo **proceso \<object> ** de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
 Para obtener más información sobre el procesamiento de modelos tabulares, vea [Procesar datos &#40;SSAS tabular&#41;](../process-data-ssas-tabular.md).  
  
##  <a name="tasks"></a><a name="bkmk_process_tasks"></a> Tareas  
  
###  <a name="to-process-a-database"></a><a name="bkmk_process_db"></a>Para procesar una base de datos  
  
1.  En [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], haga clic con el botón derecho en la base de datos que quiere procesar y, después, haga clic en **Procesar base de datos**.  
  
2.  En el cuadro de diálogo **Procesar base de datos** , en el cuadro de lista **Modo** , seleccione uno de los modos de procesamiento siguientes:  
  
    |Mode|Descripción|  
    |----------|-----------------|  
    |**Proceso predeterminado**|Detecta el estado de proceso de los objetos de base de datos y realiza el procesamiento necesario para devolver objetos sin procesar o procesados parcialmente a un estado de procesamiento completo. Se cargan los datos de las tablas vacías y las particiones; se generan o se vuelven a generar (recalcular) las jerarquías, las columnas calculadas y las relaciones.|  
    |**Proceso completo**|Procesa una base de datos y todos los objetos que contiene. Cuando se ejecuta Proceso completo en un objeto que ya se ha procesado, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] quita todos los datos del objeto y, a continuación, lo procesa. Este tipo de procesamiento es necesario cuando se ha realizado un cambio estructural en un objeto. Esta opción requiere la mayoría de los recursos.|  
    |**Procesar borrado**|Quita todos los datos de los objetos de base de datos.|  
    |**Procesar recálculo**|Actualización y recalcula jerarquías, relaciones y columnas calculadas.|  
  
3.  En la columna de casilla **Procesar** , seleccione las particiones que desea procesar con el modo seleccionado y haga clic en **Aceptar**.  
  
###  <a name="to-process-a-table"></a><a name="bkmk_process_table"></a>Para procesar una tabla  
  
1.  En [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], en la base de datos de modelo tabular que contiene la tabla que quiere procesar, expanda el nodo **Tablas** , haga clic con el botón derecho en la tabla que quiere procesar y, después, haga clic en **Procesar tabla**.  
  
2.  En el cuadro de diálogo **Procesar tabla** , en el cuadro de lista **Modo** , seleccione uno de los modos de procesamiento siguientes:  
  
    |Mode|Descripción|  
    |----------|-----------------|  
    |**Proceso predeterminado**|Detecta el estado de proceso de un objeto de tabla y realiza el procesamiento necesario para devolver objetos sin procesar o procesados parcialmente a un estado de procesamiento completo. Se cargan los datos de las tablas vacías y las particiones; se generan o se vuelven a generar (recalcular) las jerarquías, las columnas calculadas y las relaciones.|  
    |**Proceso completo**|Procesa un objeto de tabla y todos los objetos que contiene. Cuando se ejecuta Proceso completo en un objeto que ya se ha procesado, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] quita todos los datos del objeto y, a continuación, lo procesa. Este tipo de procesamiento es necesario cuando se ha realizado un cambio estructural en un objeto. Esta opción requiere la mayoría de los recursos.|  
    |**Procesar datos**|Carga datos en una tabla sin volver a generar las jerarquías o las relaciones, ni volver a calcular las columnas calculadas y las medidas.|  
    |**Procesar borrado**|Quita todos los datos de una tabla y cualquier partición de tabla.|  
    |**Procesar desfragmentación**|Desfragmenta los índices de tabla auxiliares.|  
  
3.  En la columna de casilla de tabla, compruebe la tabla y, opcionalmente, seleccione cualquier tabla adicional que desee procesar; a continuación, haga clic en **Aceptar**.  
  
###  <a name="to-process-one-or-more-partitions"></a><a name="bkmk_process_partition"></a>Para procesar una o más particiones  
  
1.  En [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], haga clic con el botón derecho en la tabla que tiene las particiones que quiere procesar y, después, haga clic en **Particiones**.  
  
2.  En el cuadro de diálogo **Particiones** , en **Particiones**, haga clic en el botón Procesar.  
  
3.  En el cuadro de diálogo **Procesar partición** , en el cuadro de lista **Modo** , seleccione uno de los modos de procesamiento siguientes:  
  
    |Mode|Descripción|  
    |----------|-----------------|  
    |**Proceso predeterminado**|Detecta el estado de proceso de un objeto de partición y realiza el procesamiento necesario para devolver objetos de partición sin procesar o procesados parcialmente a un estado de procesamiento completo. Se cargan los datos de las tablas vacías y las particiones; se generan o se vuelven a generar (recalcular) las jerarquías, las columnas calculadas y las relaciones.|  
    |**Proceso completo**|Procesa un objeto de partición y todos los objetos que contiene. Cuando se ejecuta Proceso completo en un objeto que ya se ha procesado, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] quita todos los datos del objeto y, a continuación, lo procesa. Este tipo de procesamiento es necesario cuando se ha realizado un cambio estructural en un objeto.|  
    |**Procesar datos**|Carga datos en una partición o en una tabla sin volver a generar las jerarquías o las relaciones, ni volver a calcular las columnas calculadas y las medidas.|  
    |**Procesar borrado**|Quita todos los datos de una partición.|  
    |**Procesar adición**|Actualiza la partición con nuevos datos de forma incremental.|  
  
4.  En la columna de casilla **Procesar** , seleccione las particiones que desea procesar con el modo seleccionado y haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Consulte también  
 [Particiones de modelos tabulares &#40;SSAS tabular&#41;](tabular-model-partitions-ssas-tabular.md)   
 [Crear y administrar particiones de modelos tabulares &#40;SSAS tabular&#41;](create-and-manage-tabular-model-partitions-ssas-tabular.md)  
  
  
