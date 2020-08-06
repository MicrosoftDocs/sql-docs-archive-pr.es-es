---
title: Cálculos en modelos multidimensionales | Microsoft Docs
ms.custom: ''
ms.date: 12/10/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- calculations [Analysis Services], creating
- deleting calculations
- calculations [Analysis Services], scripts
- Cube Designer
- modifying scripts
- removing calculations
- calculations [Analysis Services], deleting
- scripts [Analysis Services], calculations
- cubes [Analysis Services], calculations
- solve orders [Analysis Services]
ms.assetid: c21b3459-9bef-45a2-aba5-c992eba5b66e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 64a9733c4fd198a9906e28c437f7ba4fb10dd39a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748382"
---
# <a name="calculations-in-multidimensional-models"></a>Cálculos en modelos multidimensionales
  Use la pestaña **Cálculos** del Diseñador de cubos para crear miembros calculados, conjuntos con nombre y otros cálculos de expresiones multidimensionales (MDX).  
  
 La pestaña **Cálculos** presenta los siguientes tres paneles:  
  
-   En el panel **Organizador de script** se enumeran los cálculos de un cubo. Utilice este panel para crear, organizar y seleccionar cálculos para su edición.  
  
-   El panel **Herramientas de cálculo** proporciona metadatos, funciones y plantillas con los que se crean los cálculos.  
  
-   El panel de las expresiones de cálculo admite una vista de formulario y otra de script.  
  
> [!NOTE]  
>  Para obtener más información acerca del scripting MDX, vea [Introducción al scripting MDX en Microsoft SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=81892), y consulte la sección recursos adicionales en la página [SQL Server 2005-Analysis Services](https://go.microsoft.com/fwlink/?LinkId=80853) en el sitio web de Microsoft TechNet. Para obtener más información acerca de los problemas de rendimiento relacionados con el diseño de cubos, vea la [guía de rendimiento de SQL Server 2005 Analysis Services](https://download.microsoft.com/download/8/5/e/85eea4fa-b3bb-4426-97d0-7f7151b2011c/ssas2005perfguide.doc).  
  
## <a name="creating-a-new-calculation"></a>Crear un cálculo  
 Para crear un cálculo, en la pestaña **Cálculos** del Diseñador de cubos, en el menú **Cubo** , haga clic en **Nuevo miembro calculado**, **Nuevo conjunto con nombre**, o **Nuevo comando de script**, según el tipo de cálculo que desee crear. También se puede hacer clic en cualquiera de los botones correspondientes de la barra de herramientas, o bien hacer clic con el botón derecho en cualquier punto del panel **Organizador de scripts** y, después, hacer clic en uno de los comandos del menú contextual. Esta acción agrega un nuevo cálculo al panel **Organizador de script** y muestra los campos correspondientes del formulario de cálculos del panel de las expresiones de cálculo. Si crea un nuevo script, esta acción abre la Vista de script del panel de las expresiones de cálculo. Para más información sobre cómo crear los tres tipos de cálculos, vea [Crear miembros calculados](create-calculated-members.md), [Crear conjuntos con nombre](create-named-sets.md)y [Definir asignaciones y otros comandos de script](define-assignments-and-other-script-commands.md).  
  
## <a name="editing-scripts"></a>Editar scripts  
 Edite los scripts en el panel de las expresiones de cálculo de la pestaña **cálculos** . El panel de las expresiones de cálculo tiene dos vistas: vista de script y vista de formulario. En la vista de formulario se muestran las expresiones y propiedades para un solo comando. Al editar un script MDX, un cuadro de expresión llena toda la Vista de formulario.  
  
 La Vista de script proporciona un editor de códigos en el que se editan los scripts. Cuando el panel de las expresiones de cálculo se encuentra en la Vista de script, el panel **Organizador de script** se encuentra oculto. La Vista de script proporciona codificación de color, coincidencia de paréntesis, autocompletar y regiones de código MDX. Las regiones de código MDX se pueden contraer o expandir para facilitar la edición.  
  
 Se puede alternar entre la Vista de formulario y la Vista de script haciendo clic en el menú **Cubo** , seleccionando **Mostrar cálculos en**y, a continuación, haciendo clic en **Script** o **Formulario**. También se puede hacer clic en **Vista de formulario** o **Vista de script** en la barra de herramientas.  
  
## <a name="changing-solve-order"></a>Cambiar el orden de resolución  
 Los cálculos se resuelven en el orden enumerado en el panel del **Organizador de script** . Para volver a ordenar los cálculos, haga clic con el botón derecho en cualquier cálculo y, después, haga clic en **Subir** o **Bajar** en el menú contextual. Puede hacer clic en un cálculo y luego hacer clic en el botón **Subir** o **Bajar** en la barra de herramientas.  
  
 Puede anular este orden de forma manual para las celdas calculadas y los miembros calculados. Para más información sobre el orden de paso y el orden de resolución, vea [Información sobre el orden de paso y el orden de solución &#40;MDX&#41;](mdx/mdx-data-manipulation-understanding-pass-order-and-solve-order.md).  
  
## <a name="deleting-a-calculation"></a>Eliminar un cálculo  
 Para eliminar un cálculo existente, en la pestaña **Cálculos** , en el panel **Organizador de script** , seleccione el cálculo que desee eliminar y haga clic en **Eliminar** en el menú **Editar** o haga clic en el icono de **Eliminar** de la barra de herramientas. También puede hacer clic con el botón derecho en el cálculo en el panel **Organizador de scripts** y seleccionar **Eliminar** en el menú contextual.  
  
  
