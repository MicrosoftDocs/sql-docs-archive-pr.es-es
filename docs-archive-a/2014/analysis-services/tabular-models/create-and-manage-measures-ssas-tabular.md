---
title: Crear y administrar medidas (SSAS tabular) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: edc1a4b2-96d3-4f34-bb70-6cacec79e819
author: minewiskan
ms.author: owend
ms.openlocfilehash: da507bf48b285a1414ffb85ba79da50508a2ae2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87671204"
---
# <a name="create-and-manage-measures-ssas-tabular"></a>Crear y administrar medidas (SSAS tabular)
  Una medida es una fórmula que se crea específicamente para su uso en un informe o una tabla dinámica de Excel (o gráfico dinámico). Las medidas pueden estar basadas en funciones de agregación estándar, como COUNT o SUM, o puede definir su propia fórmula utilizando DAX. En las tareas de este tema se describe cómo crear y administrar medidas mediante la cuadrícula de medidas de una tabla.  
  
 En este tema se incluyen las tareas siguientes:  
  
-   [Para crear una medida usando una fórmula de agregación estándar](#bkmk_create_stand)  
  
-   [Para crear una medida mediante una fórmula personalizada](#bkmk_create_custom)  
  
-   [Para editar las propiedades de las medidas](#bkmk_edit)  
  
-   [Para cambiar el nombre de una medida](#bkmk_rename)  
  
-   [Para eliminar una medida](#bkmk_delete)  
  
## <a name="tasks"></a>Tareas  
 Para crear y administrar medidas, usará la cuadrícula de medidas de una tabla. Solo puede ver la cuadrícula de medidas de una tabla en el diseñador de modelos en la Vista de datos. No puede crear medidas ni ver la cuadrícula de medidas en la Vista Diagrama; sin embargo, podrá ver las medidas existentes en dicha vista. Para mostrar la cuadrícula de medidas de una tabla, haga clic en el menú **Tabla** y en **Mostrar cuadrícula de medidas**.  
  
###  <a name="to-create-a-measure-using-a-standard-aggregation-formula"></a><a name="bkmk_create_stand"></a>Para crear una medida mediante una fórmula de agregación estándar  
  
-   Haga clic en la columna para la que desea crear la medida, haga clic en el menú **Columna** , seleccione **Autosuma**y, a continuación, haga clic en un tipo de agregación.  
  
     La medida se creará automáticamente con un nombre predeterminado, seguido de la fórmula en la primera celda de la cuadrícula de medidas directamente debajo de la columna.  
  
###  <a name="to-create-a-measure-using-a-custom-formula"></a><a name="bkmk_create_custom"></a> Para crear una medida usando una fórmula personalizada  
  
-   En la cuadrícula de medidas, debajo de la columna para la que quiere crear la medida, haga clic en una celda y, después, en la barra de fórmulas, escriba un nombre, seguido de un signo de dos puntos (:), un signo igual (=) y de la fórmula. Presione ENTRAR para aceptar la fórmula.  
  
###  <a name="to-edit-measure-properties"></a><a name="bkmk_edit"></a>Para editar las propiedades de la medida  
  
-   En la cuadrícula de medidas, haga clic en una medida y, a continuación, en la ventana **Propiedades** , escriba o seleccione un valor de propiedad distinto.  
  
###  <a name="to-rename-a-measure"></a><a name="bkmk_rename"></a>Para cambiar el nombre de una medida  
  
-   En la cuadrícula de medidas, haga clic en una medida y, a continuación, en la ventana **Propiedades** , en **Nombre de medida**, escriba un nombre nuevo y haga clic en ENTRAR.  
  
     También puede cambiar el nombre de una medida en la barra de fórmulas. El nombre de la medida precede a la fórmula, y va seguido de un signo de dos puntos.  
  
###  <a name="to-delete-a-measure"></a><a name="bkmk_delete"></a>Para eliminar una medida  
  
-   En la cuadrícula de medidas, haga clic con el botón derecho en una medida y, después, haga clic en **Eliminar**.  
  
## <a name="see-also"></a>Consulte también  
 [Medidas &#40;&#41;tabular de SSAS](measures-ssas-tabular.md)   
 [KPI &#40;&#41;tabular de SSAS](kpis-ssas-tabular.md)   
 [Columnas calculadas &#40;SSAS tabular&#41;](ssas-calculated-columns.md)  
  
  
