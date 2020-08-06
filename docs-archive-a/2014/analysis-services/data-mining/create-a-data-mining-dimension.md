---
title: Crear una dimensión de minería de datos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], dimensions
ms.assetid: 9f0c39e5-3516-43ab-b203-f3f6dbcff89a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 265cf671bbc825258f0b2bd6627690e8c52f252b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743695"
---
# <a name="create-a-data-mining-dimension"></a>Crear una dimensión de minería de datos
  Si su estructura de minería de datos está basada en un cubo OLAP, puede crear una dimensión que incluya el contenido del modelo de minería de datos. A continuación, puede volver a incorporar la dimensión en el cubo de origen.  
  
 También puede examinar la dimensión, utilizarla para explorar los resultados del modelo o consultar la dimensión mediante MDX.  
  
### <a name="to-create-a-data-mining-dimension"></a>Para crear una dimensión de minería de datos  
  
1.  En el Diseñador de minería de datos de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], seleccione la pestaña **Estructura de minería de datos** o la pestaña **Modelos de minería de datos** .  
  
2.  En el menú **Modelo de minería de datos** , seleccione **Crear una dimensión de minería de datos**.  
  
     Aparece el cuadro de diálogo **Crear una dimensión de minería de datos** .  
  
3.  En la lista **Nombre del modelo** del cuadro de diálogo **Crear una dimensión de minería de datos** , seleccione el modelo de minería de datos OLAP.  
  
4.  En el cuadro **Nombre de dimensión** , escriba el nombre de la nueva dimensión de minería de datos.  
  
5.  Si desea crear un cubo que incluya la nueva dimensión de minería de datos, seleccione **Crear cubo**. Después de seleccionar **Crear cubo**, puede escribir un nuevo nombre para el cubo.  
  
6.  Haga clic en **OK**.  
  
     La dimensión de minería de datos se crea y se agrega a la carpeta **Dimensiones** del Explorador de dimensiones. Si ha seleccionado **Crear cubo**, también se crea un cubo nuevo que se agrega a la carpeta **Cubos** .  
  
## <a name="see-also"></a>Consulte también  
 [Tareas y procedimientos de las estructuras de minería de datos](mining-structure-tasks-and-how-tos.md)  
  
  
