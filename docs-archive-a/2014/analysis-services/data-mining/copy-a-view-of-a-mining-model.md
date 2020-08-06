---
title: Copiar una vista de un modelo de minería de datos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- clipboards [data mining]
- Mining Model Viewer [Analysis Services], clipboards
- copying mining models to clipboard
ms.assetid: 768372db-e5b4-4990-b459-03d854fd9a6d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 36d4d372bd235cd1cc0c043ff98151091e242269
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743701"
---
# <a name="copy-a-view-of-a-mining-model"></a>Copiar una vista de un modelo de minería de datos
  La pestaña **Visor de modelos de minería de datos** del Diseñador de minería de datos de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] utiliza un visor separado para cada tipo de modelo de minería de datos. Varios de los visores tienen componentes cuyo contenido se puede copiar al Portapapeles, y desde ahí, pegar el contenido en un documento o en un software de tratamiento de imágenes. Los componentes que permiten realizar esta funcionalidad son:  
  
-   Diagrama del clúster en el Visor de clústeres de [!INCLUDE[msCoName](../../includes/msconame-md.md)] y el Visor de clústeres de secuencia de [!INCLUDE[msCoName](../../includes/msconame-md.md)]  
  
-   Árbol de decisión en el Visor de árboles de [!INCLUDE[msCoName](../../includes/msconame-md.md)] y el Visor de series temporales de [!INCLUDE[msCoName](../../includes/msconame-md.md)]  
  
-   Transiciones de estado en el Visor de clústeres de secuencia de [!INCLUDE[msCoName](../../includes/msconame-md.md)]  
  
-   Red de dependencias en el Visor de reglas de asociación de [!INCLUDE[msCoName](../../includes/msconame-md.md)] , Visor Bayes naive de [!INCLUDE[msCoName](../../includes/msconame-md.md)] y Visor de árboles de [!INCLUDE[msCoName](../../includes/msconame-md.md)]  
  
-   Contenido del modelo de minería de datos, del panel Detalles de nodo del Visor de árbol de contenido genérico de [!INCLUDE[msCoName](../../includes/msconame-md.md)]  
  
 Puede copiar la representación completa del modelo de minería de datos o solo la parte que está visible en el visor.  
  
> [!WARNING]  
>  Al copiar un modelo usando el visor, no se crea un objeto de modelo nuevo. Para crear un modelo nuevo, debe usar el asistente o el Diseñador de minería de datos. Para obtener más información, vea [Realizar una copia de un modelo de minería de datos](make-a-copy-of-a-mining-model.md).  
  
### <a name="to-copy-the-complete-model-to-the-clipboard"></a>Para copiar el modelo completo en el portapapeles  
  
1.  En la lista **Modelo de minería de datos** en la pestaña **Visor de modelos de minería de datos** , seleccione el modelo de minería de datos que desee ver.  
  
2.  Seleccione la pestaña adecuada, por ejemplo, la pestaña **Red de dependencias** y, a continuación, haga clic en **Copiar todo el gráfico** en la barra de herramientas de esa pestaña.  
  
### <a name="to-copy-the-visible-piece-of-the-model-to-the-clipboard"></a>Para copiar en el Portapapeles la parte visible del modelo  
  
1.  En la lista **Modelo de minería de datos** en la pestaña **Visor de modelos de minería de datos** , seleccione el modelo de minería de datos que desee ver.  
  
2.  Seleccione la pestaña adecuada, por ejemplo, la pestaña **Red de dependencias** y, a continuación, acerque o aleje para ver el modelo en el nivel que desee.  
  
3.  Haga clic en **Copiar vista del gráfico** en la barra de herramientas de la pestaña seleccionada.  
  
### <a name="to-copy-the-mining-model-content-to-the-clipboard"></a>Para copiar el contenido del modelo de minería de datos en el Portapapeles  
  
1.  En la lista **Modelo de minería de datos** en la pestaña **Visor de modelos de minería de datos** , seleccione el modelo de minería de datos que desee ver.  
  
2.  En la lista desplegable **Visor** , seleccione **Visor de árbol de contenido genérico de Microsoft**.  
  
3.  En el panel **Título del nodo (id. único)** , haga clic en un nodo.  
  
4.  Haga clic con el botón derecho en el panel **Detalles del nodo** y, después, seleccione **Seleccionar todo**.  
  
5.  Haga clic con el botón derecho en el panel **Detalles del nodo** de nuevo y seleccione **Copiar**.  
  
## <a name="see-also"></a>Consulte también  
 [Tareas y procedimientos del Visor de modelos de minería de datos](mining-model-viewer-tasks-and-how-tos.md)  
  
  
