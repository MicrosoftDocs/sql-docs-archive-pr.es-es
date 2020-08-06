---
title: Tablas y columnas (SSAS tabular) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c428d717-05de-436c-b9dc-e8c1925a60ca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3f23b21ce492fd3160df727c1562ee706848fa99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748934"
---
# <a name="tables-and-columns-ssas-tabular"></a>Definir tablas y columnas (SSAS tabular)
  Después de haber agregado tablas y datos a un modelo mediante el Asistente para la importación de tablas, puede empezar a trabajar con las tablas agregando nuevas columnas de datos, creando relaciones entre las tablas, definiendo cálculos que amplían los datos y filtrando y ordenando datos en las tablas para facilitar su visualización.  
  
 Secciones de este tema:  
  
-   [Ventajas](#bkmk_benefits)  
  
-   [Trabajar con tablas y columnas](#bkmk_working)  
  
-   [Tareas relacionadas](#bkmk_related_tasks)  
  
##  <a name="benefits"></a><a name="bkmk_benefits"></a> Ventajas  
 En los modelos tabulares, las tablas proporcionan el marco en el que se definen las columnas y otros metadatos. Las tablas incluyen:  
  
 **Definición de tabla**  
 La definición de tabla incluye el conjunto de columnas. Las columnas se pueden importar desde un origen de datos o agregar manualmente, como en el caso de las columnas calculadas.  
  
 **Metadatos de tabla**  
 Las relaciones, las medidas, los roles, las perspectivas y los datos pegados son los metadatos que definen los objetos en el contexto de una tabla.  
  
 **Data**  
 Los datos se rellenan en las columnas de las tablas la primera vez que se importan las tablas usando el Asistente para la importación de tablas o creando nuevos datos en columnas calculadas. Cuando los datos cambian en el origen, o cuando se quita un modelo de la memoria, es necesario ejecutar una operación de proceso para volver a rellenar los datos en las tablas.  
  
##  <a name="working-with-tables-and-columns"></a><a name="bkmk_working"></a>Trabajar con tablas y columnas  
 No se pueden crear tablas de modelos directamente en el diseñador de modelos. Se crea automáticamente una pestaña nueva cada vez que se importan o copian datos de otro origen de datos. Cada pestaña (en el diseñador de modelos) contiene una tabla de datos, que puede incluir lo siguiente:  
  
-   Una tabla o vista única de una base de datos relacional, o de otros orígenes no relacionales, como un cubo de Analysis Services.  
  
-   Un conjunto tabular de datos importado de una fuente o archivo de texto.  
  
-   Una combinación de datos relacionales y de datos tabulares (HTML) copiados y pegados en la tabla.  
  
 Al importar datos, cada tabla o vista, hoja o archivo de datos se agrega como una tabla en el diseñador de modelos. Normalmente, los datos de varios orígenes se agregan en pestañas independientes, pero puede combinar datos en una única tabla usando **Pegar** y **Pegar y anexar**. Para más información, vea [Copiar y pegar datos &#40;SSAS tabular&#41;](../copy-and-paste-data-ssas-tabular.md).  
  
 Después de agregar los datos que necesita, puede crear relaciones adicionales entre las tablas, buscar o hacer referencia a los valores relacionados en otras tablas, o crear valores derivados agregando nuevas columnas calculadas.  
  
 Si trabaja con conjuntos de datos muy grandes, es posible que necesite filtrar determinados datos para que no sean visibles. Puede que también desee ordenar los datos en un orden diferente. El diseñador de modelos le permite usar las características de filtrado, ordenación y ocultación para mostrar, o no mostrar, columnas completas o determinados datos.  
  
##  <a name="related-tasks"></a><a name="bkmk_related_tasks"></a> Tareas relacionadas  
  
|Tema|Descripción|  
|-----------|-----------------|  
|[Agregar columnas a una tabla &#40;SSAS tabular&#41;](add-columns-to-a-table-ssas-tabular.md)|Describe cómo agregar una columna de origen a una definición de tabla.|  
|[Eliminar una columna &#40;SSAS tabular&#41;](delete-a-column-ssas-tabular.md)|Describe cómo eliminar una columna de la tabla modelo mediante el diseñador de modelos o mediante el cuadro de diálogo Propiedades de la tabla.|  
|[Cambiar las asignaciones de filtros de tabla, columna o fila &#40;SSAS tabular&#41;](change-table-column-or-row-filter-mappings-ssas-tabular.md)|Describe cómo cambiar las asignaciones de filtros de tabla, columna o fila mediante la vista previa de tabla o el Editor de consultas de SQL en el cuadro de diálogo Editar propiedades de tabla.|  
|[Especificar Marcar como tabla de fechas con inteligencia de tiempo &#40;SSAS tabular&#41;](specify-mark-as-date-table-for-use-with-time-intelligence-ssas-tabular.md)|Describe cómo se usa el cuadro de diálogo Marcar como tabla de fechas para especificar una tabla de fechas y una columna de identificador único. Es necesario especificar una tabla de fechas y un identificador único de fecha cuando se utilizan funciones de inteligencia de tiempo en fórmulas DAX.|  
|[Agregar una tabla &#40;SSAS tabular&#41;](add-a-table-ssas-tabular.md)|Describe cómo se agrega una tabla desde un origen de datos utilizando una conexión de origen de datos existente.|  
|[Eliminar una tabla &#40;SSAS tabular&#41;](delete-a-table-ssas-tabular.md)|Describe cómo eliminar tablas que ya no necesita de la base de datos del área de trabajo del modelo.|  
|[Cambiar el nombre de una tabla o una columna &#40;SSAS tabular&#41;](rename-a-table-or-column-ssas-tabular.md)|Describe cómo cambiar el nombre de una tabla o una columna para que sea más identificable en el modelo.|  
|[Establecer el tipo de datos de una columna &#40;SSAS tabular&#41;](set-the-data-type-of-a-column-ssas-tabular.md)|Describe cómo modificar el tipo de datos de una columna. El tipo de datos define cómo se almacenan y presentan los datos de la columna.|  
|[Ocultar o inmovilizar columnas &#40;SSAS tabular&#41;](hide-or-freeze-columns-ssas-tabular.md)|Describe cómo ocultar las columnas que no desea mostrar y cómo mantener visible un área de un modelo mientras se desplaza a otra área del modelo inmovilizando (bloqueando) columnas específicas en un área.|  
|[Columnas calculadas &#40;SSAS tabular&#41;](ssas-calculated-columns.md)|En los temas de esta sección se describe cómo usar las columnas calculadas para incorporar datos agregados al modelo.|  
|[Filtrar y ordenar datos &#40;SSAS tabular&#41;](../filter-and-sort-data-ssas-tabular.md)|En los temas de esta sección se describe cómo filtrar u ordenar los datos usando los controles del diseñador de modelos.|  
  
  
