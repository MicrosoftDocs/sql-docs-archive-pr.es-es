---
title: Panel Resultados (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- result sets [SQL Server], queries
- synchronization [SQL Server], query results with definition
- displaying query results in grid
- grid showing query results [SQL Server]
- showing query results in grid
- Query Designer [SQL Server], Results pane
- results [SQL Server], query
- viewing query results
- queries [SQL Server], results
- Results pane
ms.assetid: 6309a1bc-a628-4141-8bb5-b35924bd19f9
author: stevestein
ms.author: sstein
ms.openlocfilehash: f0db32336931f74777be56befcde9501dc484b69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662458"
---
# <a name="results-pane-visual-database-tools"></a>Panel Resultados (Visual Database Tools)
  El panel Resultados muestra los resultados de la consulta SELECT que se ha ejecutado más recientemente (Los resultados de otros tipos de consultas se muestran en cuadros de mensaje). Para abrir el panel de resultados, abra o cree una consulta, o vea o devuelva los datos de una tabla. Si el panel de resultados no aparece de manera predeterminada, en el menú **Diseñador de consultas** , elija **Panel**y, a continuación, haga clic en **Resultados**.  
  
## <a name="what-you-can-do-in-the-results-pane"></a>Lo que se puede hacer en el panel Resultados  
  
-   Ver el conjunto de resultados de la consulta SELECT ejecutada más recientemente en una cuadrícula con forma de hoja de cálculo.  
  
-   Para las consultas o vistas que muestran datos de una única tabla o vista, puede editar los valores en columnas individuales en el conjunto de resultados, agregar nuevas filas y eliminar las filas existentes.  
  
## <a name="limitations-in-the-results-pane"></a>Limitaciones del panel Resultados  
  
-   Los resultados devueltos mediante funciones con valores de tabla solo pueden actualizarse en algunos casos.  
  
-   Las consultas o vistas que incluyen columnas de más de una tabla o vista no pueden actualizarse.  
  
-   Los resultados devueltos mediante un procedimiento almacenado no pueden actualizarse.  
  
-   Las consultas o vistas que utilizan las cláusulas GROUP BY o DISTINCT no se pueden actualizar.  
  
## <a name="navigating-in-the-results-pane"></a>Desplazarse por el panel de resultados  
 Puede navegar rápidamente por los registros utilizando la barra de navegación de la parte inferior del panel Resultados.  
  
 Hay botones para ir al primer y último registro, al registro anterior y siguiente, y para ir a un registro concreto.  
  
 Para ir a un registro concreto, escriba el número de la fila en el cuadro de texto de la barra de navegación y, a continuación, presione ENTRAR.  
  
 Para información sobre cómo usar los métodos abreviados de teclado en el Diseñador de consultas y vistas, consulte [Desplazarse por el Diseñador de consultas y vistas &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
## <a name="keeping-the-results-set-synchronized-with-the-query-definition"></a>Mantener el conjunto de resultados sincronizado con la definición de la consulta  
 Es posible que, mientras se trabaja con los resultados de una consulta o vista, los registros del panel de resultados dejen de estar sincronizados con la definición de la consulta. Por ejemplo, si se ejecuta una consulta para cuatro de las cinco columnas de una tabla y, a continuación, se utiliza el panel Diagrama para agregar la quinta columna a la definición de la consulta, los datos de esa quinta columna no se agregarán automáticamente al panel Resultados. Para hacer que el panel de resultados refleje la nueva definición, vuelva a ejecutar la consulta.  
  
 Si se cambia una consulta, aparecerá un icono de alerta y el texto "Consulta cambiada" en la esquina inferior derecha del panel de resultados. El icono aparecerá repetido en la esquina superior izquierda del panel.  
  
## <a name="see-also"></a>Consulte también  
 [Crear consultas &#40;Visual Database Tools&#41;](create-queries-visual-database-tools.md)   
 [Ejecutar consultas &#40;Visual Database Tools&#41;](run-queries-visual-database-tools.md)   
 [Temas de procedimientos de diseño de consultas y vistas &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [Panel Diagrama &#40;Visual Database Tools&#41;](diagram-pane-visual-database-tools.md)   
 [Panel criterios &#40;Visual Database Tools&#41;](criteria-pane-visual-database-tools.md)   
 [Trabajar con datos en el panel Resultados &#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md)  
  
  
