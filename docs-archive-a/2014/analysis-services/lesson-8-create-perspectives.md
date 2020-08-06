---
title: 'Lección 9: crear perspectivas | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 55b0f0d0-1cdf-4876-9c3d-d0c848be3f5d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 417b6a4d3b16857f48bcc2f39dc8ec4c010a2b10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748999"
---
# <a name="lesson-9-create-perspectives"></a>Lección 9: Crear perspectivas
  En esta lección, creará una perspectiva Venta por Internet. Una perspectiva define un subconjunto visible de un modelo que ofrece puntos de vista centrados, específicos del negocio o específicos de la aplicación. Cuando un usuario se conecta a un modelo utilizando una perspectiva, solo ve los objetos del modelo (tablas, columnas, medidas, jerarquías y KPI) como campos definidos en esa perspectiva.  
  
 La perspectiva Venta por Internet que va a crear en esta lección excluirá el objeto de tabla Cliente. Al crear una perspectiva que excluye ciertos objetos en la vista, ese objeto todavía existe en el modelo; sin embargo, no está visible en una lista de campos del cliente de informe. Las columnas calculadas y medidas se pueden incluir en una perspectiva o no pueden calcularse a partir de los datos del objeto excluido.  
  
 El propósito de esta lección es describir cómo se crean las perspectivas y permitir que se familiarice con las herramientas de creación de modelos tabulares. Si posteriormente amplía el modelo para incluir tablas adicionales, puede crear otras perspectivas para definir puntos de vista diferentes del modelo, como Inventario y Personal de ventas.  
  
 Para obtener más información, consulte [Perspectivas &#40;SSAS tabular&#41;](tabular-models/perspectives-ssas-tabular.md).  
  
 Tiempo estimado para completar esta lección: **5 minutos**  
  
## <a name="prerequisites"></a>Requisitos previos  
 Este tema forma parte de un tutorial de modelado tabular, que se debe completar en orden. Antes de realizar las tareas de esta lección, debe haber completado la lección anterior: [Lección 8: Crear indicadores clave de rendimiento](lesson-7-create-key-performance-indicators.md).  
  
## <a name="create-perspectives"></a>Crear perspectivas  
  
#### <a name="to-create-an-internet-sales-perspective"></a>Para crear una perspectiva Venta por Internet  
  
1.  En el diseñador de modelos, haga clic en el menú **modelo** y, a continuación, en **perspectivas**.  
  
2.  En el cuadro de diálogo **Perspectivas** , haga clic en **Nueva perspectiva**.  
  
3.  Para cambiar el nombre de la perspectiva, haga doble clic en el encabezado de columna **nueva perspectiva 1** y, a continuación, escriba `Internet Sales` .  
  
4.  En **campos**, seleccione las tablas siguientes: **Date**, **Geography**, **Product**, **Product Category**, **Product**subcategory y `Internet Sales` .  
  
     Tenga en cuenta que excluyó la tabla Cliente y todas sus columnas de esta perspectiva. Más adelante, en la lección 12, utilizará la característica Analizar en Excel para probar esta perspectiva. La lista de campos de tabla dinámica de Excel incluirá todas las tablas, excepto la tabla Cliente.  
  
5.  Compruebe sus selecciones, asegúrese de que no está marcada la tabla **Cliente** y, después, haga clic en **Aceptar**  
  
## <a name="next-steps"></a>Pasos siguientes  
 Para continuar este tutorial, vaya a la lección siguiente: [Lección 10: Crear jerarquías](lesson-9-create-hierarchies.md).  
  
  
