---
title: Eliminar relaciones (SSAS tabular) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d40e3f05-54e8-4c4b-807a-0b06f446079b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3c63324918eb6919ce0abd65b5ee0765f9d7243b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744380"
---
# <a name="delete-relationships-ssas-tabular"></a>Eliminar relaciones (SSAS tabular)
  Puede eliminar las relaciones existentes utilizando el diseñador de modelos en la Vista de diagrama o utilizando el cuadro de diálogo Administrar relaciones. Para más información sobre cómo se usan las relaciones en los modelos tabulares, vea [Relaciones &#40;SSAS tabular&#41;](relationships-ssas-tabular.md).  
  
## <a name="considerations-for-deleting-relationships"></a>Aspectos que se deben tener en cuenta al eliminar relaciones  
 Tenga en cuenta los siguientes problemas a la hora de decidir si va a eliminar una relación:  
  
-   No hay ninguna manera de deshacer la eliminación de una relación. Puede volver a crearla, pero esta acción requiere que se vuelvan a calcular completamente las fórmulas del modelo. Por consiguiente, compruebe siempre si una relación se usa en fórmulas antes de eliminarla.  
  
-   Eliminar una relación entre dos tablas puede provocar errores en las fórmulas que hacen referencia a estas tablas.  
  
-   La función RELATED de las Expresiones de análisis de datos (DAX) usa las relaciones entre tablas para buscar valores relacionados en otra tabla. Devolverá resultados diferentes una vez eliminada la relación. Para obtener más información, vea la función RELATED (DAX).  
  
-   Además de cambiar los resultados de las fórmulas y las tablas dinámicas, tanto la creación como la eliminación de relaciones harán que el libro se vuelva a calcular, lo que puede tardar algún tiempo.  
  
## <a name="delete-relationships"></a>Eliminar relaciones  
  
#### <a name="to-delete-a-relationship-by-using-diagram-view"></a>Para eliminar una relación utilizando la Vista de diagrama  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], haga clic en el menú **Modelo** , elija **Vista de modelo**y haga clic en **Vista de diagrama**.  
  
2.  Haga clic con el botón derecho en una línea de relación entre dos tablas y, después, haga clic en **Eliminar**.  
  
#### <a name="to-delete-a-relationship-by-using-the-manage-relationships-dialog-box"></a>Para eliminar una relación utilizando el cuadro de diálogo Administrar relaciones  
  
1.  En [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], haga clic en el menú **Tabla** y, a continuación, haga clic en **Administrar relaciones**.  
  
2.  En el cuadro de diálogo **Administrar relaciones** , seleccione una o más relaciones en la lista.  
  
     Para seleccionar varias relaciones, mantenga presionada la tecla CTRL mientras hace clic en cada una.  
  
3.  Haga clic en **Eliminar relación**.  
  
4.  En el cuadro de diálogo **Administrar las relaciones** , haga clic en **Cerrar**.  
  
## <a name="see-also"></a>Consulte también  
 [Relaciones &#40;&#41;tabular de SSAS](relationships-ssas-tabular.md)   
 [Crear una relación entre dos tablas &#40;SSAS tabular&#41;](create-a-relationship-between-two-tables-ssas-tabular.md)  
  
  
