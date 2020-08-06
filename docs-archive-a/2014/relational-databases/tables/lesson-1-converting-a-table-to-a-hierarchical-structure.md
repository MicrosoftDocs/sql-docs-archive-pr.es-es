---
title: 'Lección 1: Conversión de una tabla en una estructura jerárquica | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 5ee6f19a-6dd7-4730-a91c-bbed1bd77e0b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 196a546093786f9be4b88536763b3150ae750f97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87749693"
---
# <a name="lesson-1-converting-a-table-to-a-hierarchical-structure"></a>Lección 1: Convertir una tabla en una estructura jerárquica
  Los clientes que tienen tablas que utilizan autocombinaciones para expresar las relaciones jerárquicas pueden convertir sus tablas en una estructura jerárquica usando esta lección como guía. Es relativamente fácil migrar de esta representación a una que use `hierarchyid`. Después de la migración, los usuarios tendrán una representación jerárquica compacta y fácil de entender, que se puede indizar de varias maneras para conseguir consultas eficaces.  
  
 En esta lección se examina una tabla existente, se crea una nueva tabla que contiene una columna `hierarchyid`, se rellena la tabla con los datos de la tabla de origen y, a continuación, se muestran tres estrategias de indización. En esta lección se incluyen los temas siguientes:  
  
-   [Examen de la estructura actual de la tabla Empleado](lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
-   [Rellenar una tabla con los datos jerárquicos existentes](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
-   [Optimizar la tabla NewOrg](lesson-1-3-optimizing-the-neworg-table.md)  
  
-   [Resumen: Conversión de una tabla en una estructura jerárquica](lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
## <a name="prerequisites"></a>Requisitos previos  
 Esta lección requiere la base de datos de ejemplo [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
## <a name="next-task-in-lesson"></a>Siguiente tarea de la lección  
 [Examen de la estructura actual de la tabla Empleado](lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
## <a name="next-lesson"></a>Lección siguiente  
 [Lección 2: Creación y administración de los datos de una tabla jerárquica](lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
  
  
