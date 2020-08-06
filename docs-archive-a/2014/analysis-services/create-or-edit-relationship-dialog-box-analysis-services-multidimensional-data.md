---
title: Cuadro de diálogo crear o editar relación (Analysis Services-datos multidimensionales) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.createrelationship.f1
helpviewer_keywords:
- Create Relationship dialog box
ms.assetid: da3c7074-623e-4ddf-a707-d3276a47cf1c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4edae3f78ac6b764d91e1be97787fe59d49421db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87671272"
---
# <a name="create-or-edit-relationship-dialog-box-analysis-services---multidimensional-data"></a>Cuadro de diálogo Crear o Editar relación (Analysis Services - Datos multidimensionales)
  Use el cuadro de diálogo **Crear/Editar relación** en [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] para definir o modificar una relación en una vista del origen de datos. Puede mostrar el cuadro de diálogo **Crear relación/Editar relación** de las siguientes maneras:  
  
-   Haciendo clic en **Nueva relación** en el panel **Barra de herramientas** del **Diseñador de vistas del origen de datos**.  
  
-   Haciendo clic con el botón derecho en una tabla de los paneles **Tablas** o **Diagrama** del **Diseñador de vistas del origen de datos** y seleccionando **Nueva relación**.  
  
-   Haciendo clic con el botón derecho en el panel **Diagrama** del **Diseñador de vistas del origen de datos** y seleccionando **Editar relación**.  
  
> [!NOTE]  
>   Puede crear relaciones en el **Diseñador de vistas del origen de datos** que no existen en el origen de datos subyacente y eliminar relaciones creadas mediante el **Diseñador de vistas del origen de datos** a partir de relaciones de clave externa en el origen de datos subyacente.  
  
## <a name="options"></a>Opciones  
 **Tabla de origen (de clave externa)**  
 Seleccione la tabla o consulta con nombre que contiene la referencia a una o varias columnas de la tabla de destino.  
  
 **Tabla de destino (de clave principal)**  
 Seleccione la tabla que contiene una o varias columnas a las que la tabla de origen hace referencia. Para autocombinaciones, seleccione la misma tabla seleccionada en la **Tabla de origen (de clave externa)**.  
  
 **Columnas de origen**  
 Seleccione las columnas que hacen referencia a columnas de la tabla de destino.  
  
 **Columnas de destino**  
 Seleccione las columnas a las que hacen referencia las columnas de la tabla de origen.  
  
 **Viceversa**  
 Haga clic para invertir la dirección de la relación.  
  
 **Descripción**  
 Escriba una descripción opcional para la relación.  
  
## <a name="see-also"></a>Consulte también  
 [Analysis Services diseñadores y cuadros de diálogo &#40;datos multidimensionales&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Diseñador de vistas del origen de datos &#40;Analysis Services - Datos multidimensionales&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  
