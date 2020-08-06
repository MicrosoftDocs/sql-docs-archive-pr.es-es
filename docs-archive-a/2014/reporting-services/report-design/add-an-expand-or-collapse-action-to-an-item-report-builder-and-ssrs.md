---
title: Agregar una acción de expandir y contraer a un elemento (Generador de informes y SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 49f07ad6-242b-4861-8fc1-91ca78c36d6c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 331c6a14a4a898ffcdf86f274c00e7ad3c801ec7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744489"
---
# <a name="add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs"></a>Agregar una acción de expandir y contraer a un elemento (Generador de informes y SSRS)
  Podrá permitir a los usuarios expandir o contraer interactivamente elementos de informe o expandir o contraer las filas y columnas asociadas a un grupo para una tabla o una matriz. Para permitir a los usuarios expandir o contraer un elemento, debe establecer las propiedades de visibilidad del elemento. El establecimiento de la visibilidad funciona en un visor de informes HTML y en ocasiones se denomina acción *de obtención de detalles* .  
  
 En la vista de diseño del informe, especifique el nombre del cuadro de texto donde desea mostrar los iconos de alternancia de expandir y contraer. En el informe representado, el cuadro de texto mostrará un signo más (+) o menos (-), además de su contenido. Cuando el usuario haga clic en el control de visibilidad, la presentación del informe se actualizará para mostrar u ocultar el elemento de informe en función de los valores de visibilidad actuales para los elementos del informe.  
  
 Normalmente, la acción de expandir y contraer se usa para mostrar inicialmente solo datos de resumen y permitir a los usuarios hacer clic en el signo más para mostrar los datos detallados. Por ejemplo, puede ocultar inicialmente una tabla que muestre los valores usados en un gráfico u ocultar los grupos secundarios de una tabla con grupos de filas o de columnas anidadas, como en un informe detallado.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-expand-and-collapse-action-to-a-group"></a>Para agregar una acción de expandir y contraer a un grupo  
  
1.  En la vista de diseño del informe, haga clic en la tabla o la matriz para seleccionarla. El Panel de agrupación muestra los grupos de filas y de columnas.  
  
     ![Panel de agrupación](../media/groupingpane.png "Panel de agrupación")  
  
     Si el panel de agrupación no aparece, haga clic en el menú **Ver** y después en **Agrupación**.  
  
2.  Haga clic con el botón derecho en cualquier parte en la barra de título del panel Agrupación y, después, haga clic en **Avanzadas**. El modo del panel Agrupación alterna para mostrar la estructura de presentación subyacente para las filas y columnas en la superficie de diseño.  
  
     ![Panel de agrupación con menú Modo avanzado](../media/groupingpane-advancedmode.png "Panel de agrupación con menú Modo avanzado")  
  
3.  En panel de grupo adecuado, haga clic en el nombre del grupo de filas o del grupo de columnas cuyas filas o columnas asociadas desea ocultar. El grupo queda seleccionado y el panel de propiedades muestra las propiedades de **Miembro de Tablix** .  
  
    > [!NOTE]  
    >   Si el panel Propiedades no está visible, haga clic en **Ver** en la cinta de opciones y luego haga clic en **Propiedades**.  
  
4.  En `Hidden` , elija una de las siguientes opciones para establecer la visibilidad de este elemento de informe la primera vez que ejecute un informe:  
  
    -   Seleccione `False` esta opción para mostrar el elemento de informe.  
  
    -   Seleccione `True` esta opción para ocultar el elemento de informe.  
  
    -   Seleccione **\<Expression>** esta casilla para abrir el cuadro de diálogo **expresión** y crear una expresión que se evalúa en tiempo de ejecución para determinar la visibilidad.  
  
5.  En **ToggleItem**, en la lista desplegable, seleccione el nombre de un cuadro de texto al que quiera agregar la imagen de alternancia.  
  
     En la siguiente imagen, el grupo de filas Color está configurado para permitir a los usuarios expandir y contraer las filas asociadas.  
  
     ![Configuración de un grupo de filas que debe expandirse](../media/expandcollapse-confighiddentoggleitemwithnumbers.png "Configuración de un grupo de filas que debe expandirse")  
  
    > [!NOTE]  
    >  El cuadro de texto con la imagen de alternancia no puede ser el grupo de filas o columnas para el que desee ocultar las filas o columnas asociadas. Debe estar en el mismo grupo que el elemento que se va a ocultar o en otro grupo antecesor. Por ejemplo, para alternar la visibilidad de las filas asociadas a un grupo secundario, seleccione un cuadro de texto de una fila asociada al grupo primario.  
  
6.  Para probar el control de alternancia, ejecute el informe y haga clic en el cuadro de texto que contiene la imagen de alternancia. La presentación del informe se actualiza para mostrar los grupos de filas y los grupos de columnas con su visibilidad alternada.  
  
     ![Informe en ejecución con un grupo de filas que se pueden expandir](../media/expandcollapse-runreport-rowgroup.png "Informe en ejecución con un grupo de filas que se pueden expandir")  
  
### <a name="to-add-expand-and-collapse-action-to-a-report-item"></a>Para agregar una acción de expandir y contraer a un elemento de informe  
  
1.  En la vista de diseño del informe, haga clic con el botón secundario en el elemento de informe que desee mostrar u ocultar y, a continuación, haga clic en *\<report item>* **propiedades**. *\<report item>* Se abrirá el cuadro de diálogo **propiedades** del elemento de informe.  
  
2.  Haga clic en **Visibilidad**.  
  
3.  En **Cuando se ejecute inicialmente el informe**, elija una de las opciones siguientes para establecer la visibilidad de este elemento de informe la primera vez que se ejecute el informe:  
  
    -   Seleccione **Mostrar** para mostrar el elemento de informe.  
  
    -   Seleccione **Ocultar** para ocultar el elemento de informe.  
  
    -   Seleccione **Mostrar u ocultar en función de una expresión** para determinar la visibilidad mediante una expresión que se evalúa en tiempo de ejecución. Haga clic en (**FX**) para abrir el cuadro de diálogo **expresión** y crear una expresión.  
  
        > [!NOTE]  
        >  Al especificar una expresión para la visibilidad, está estableciendo la propiedad Hidden del elemento de informe. La expresión se evalúa como un valor `Boolean``True` para ocultar el elemento y `False` para mostrarlo.  
  
4.  En **La visualización se puede activar o desactivar para este elemento de informe**, en la lista desplegable, escriba o seleccione el nombre de un cuadro de texto del informe en el que quiera mostrar la imagen de alternancia; por ejemplo, Cuadrodetexto1.  
  
     En la siguiente imagen, la tabla está configurada para permitir a los usuarios expandirla y contraerla. La visualización de la tabla se alterna mediante el cuadro de texto de la tabla Products.  
  
     ![Configuración de una tabla de informes que debe expandirse](../media/expandcollapse-reporttable.png "Configuración de una tabla de informes que debe expandirse")  
  
    > [!NOTE]  
    >  El cuadro de texto que elija debe estar en el ámbito contenedor o actual de este elemento de informe (hasta el cuerpo del informe, inclusive). Por ejemplo, para alternar la visibilidad de un gráfico, seleccione un cuadro de texto que esté en el mismo ámbito contenedor que el gráfico; por ejemplo, un rectángulo o el cuerpo del informe. El cuadro de texto debe estar en la misma jerarquía contenedora o superior.  
  
5.  Para probar el control de alternancia, ejecute el informe y haga clic en el cuadro de texto que contiene la imagen de alternancia. La presentación del informe se actualiza para mostrar los elementos de informe con su visibilidad alternada.  
  
     ![Informe en ejecución con una tabla expandida](../media/expandcollapse-runreport-reporttable.png "Informe en ejecución con una tabla expandida")  
  
## <a name="see-also"></a>Consulte también  
 [Acción de obtención de detalles &#40;Generador de informes y SSRS&#41;](drilldown-action-report-builder-and-ssrs.md)   
 [Ocultar un elemento &#40;Generador de informes y SSRS&#41;](../report-builder/hide-an-item-report-builder-and-ssrs.md)  
  
  
