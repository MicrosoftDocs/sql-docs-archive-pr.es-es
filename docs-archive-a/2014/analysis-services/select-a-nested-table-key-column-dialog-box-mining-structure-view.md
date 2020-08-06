---
title: Seleccionar una columna de clave de tabla anidada (cuadro de diálogo de la vista estructura de minería de datos) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.structure.addnestedtable.f1
helpviewer_keywords:
- Select a Nested Table Key Column dialog box
ms.assetid: f68b89a7-17df-45f8-ba7f-b458cd9b1ec3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4dc524f6913b7be15e87869355515397a3e0b65c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87675562"
---
# <a name="select-a-nested-table-key-column-dialog-box-mining-structure-view"></a>Seleccione una columna de clave de tabla anidada (cuadro de diálogo de la vista Estructura de minería de datos)
  Utilice el cuadro de diálogo **Seleccione una columna de clave de tabla anidada** para designar una columna que actuará como la clave para la nueva tabla anidada. Cuando salga del cuadro de diálogo, se agrega una nueva tabla a la estructura de minería de datos que contiene la columna de clave designada. Puede agregar columnas adicionales a la tabla anidada haciendo clic con el botón derecho en la estructura y seleccionando **Agregar una columna**. El cuadro de diálogo contiene diferentes opciones dependiendo de si está trabajando con un modelo de minería OLAP o un modelo de minería relacional.  
  
## <a name="options"></a>Opciones  
 **Tabla de origen**  
 La tabla en la que se basa el modelo de minería de datos.  
  
 Solo se utiliza para modelos de minería relacionales.  
  
 **Columna de origen**  
 Lista de todas las columnas disponibles en la tabla de origen que puede emplear como la clave de la tabla anidada.  
  
 Solo se utiliza para modelos de minería relacionales.  
  
 **Mostrar tipos de columna**  
 Una lista de los tipos de datos de columnas disponibles. Seleccione o deseleccione los tipos de datos para filtrar la lista de columnas en **Columna de origen**. En la lista **Columna de origen** solo se mostrarán las columnas que coinciden con los tipos de datos seleccionados.  
  
 Solo se utiliza para modelos de minería relacionales.  
  
 **Atributos**  
 Lista de atributos que puede utilizar como la clave de la tabla anidada.  
  
 Solo se utiliza para modelos de minería de datos OLAP.  
  
## <a name="see-also"></a>Consulte también  
 [Vista estructura de minería de datos &#40;diseñador de modelos de minería de datos&#41;](mining-structure-view-data-mining-model-designer.md)  
  
  
