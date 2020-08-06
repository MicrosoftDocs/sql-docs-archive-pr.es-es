---
title: Depurar un paquete estableciendo puntos de interrupción en una tarea o un contenedor | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], breakpoints
- breakpoints [Integration Services]
- tasks [Integration Services], breakpoints
ms.assetid: e7fa106a-2221-403a-bb74-efc9f12bb450
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 21e334faff95e63e59bbf9c40fdf7e479de949da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669760"
---
# <a name="debug-a-package-by-setting-breakpoints-on-a-task-or-a-container"></a>Depurar un paquete estableciendo puntos de interrupción en una tarea o un contenedor
  Este procedimiento describe cómo establecer puntos de interrupción en un paquete, una tarea, un contenedor de bucles For o Foreach o un contenedor de secuencias.  
  
### <a name="to-set-breakpoints-in-a-package-a-task-or-a-container"></a>Para establecer puntos de interrupción en un paquete, una tarea o un contenedor  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], abra el proyecto de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] que contiene el paquete que desea.  
  
2.  Haga doble clic en el paquete en el que desee establecer puntos de interrupción.  
  
3.  En el Diseñador SSIS, siga estos pasos:  
  
    -   Para establecer puntos de interrupción en el objeto de paquete, haga clic en la pestaña **Flujo de control** , coloque el cursor en cualquier lugar del fondo de la superficie de diseño, haga clic con el botón derecho y, después, haga clic en **Editar puntos de interrupción**.  
  
    -   Para establecer puntos de interrupción en un flujo de control de paquete, haga clic en la pestaña **Flujo de control** , haga clic con el botón derecho en una tarea, un contenedor de bucles For o Foreach o un contenedor de secuencias y, después, haga clic en **Editar puntos de interrupción**.  
  
    -   Para establecer puntos de interrupción en un controlador de eventos, haga clic en la pestaña **Controlador de eventos** , haga clic con el botón derecho en una tarea, un contenedor de bucles For o Foreach o un contenedor de secuencias y, después, haga clic en **Editar puntos de interrupción**.  
  
4.  En el cuadro de diálogo **Establecer puntos de interrupción \<container name>** , seleccione los puntos de interrupción que quiera habilitar.  
  
5.  Opcionalmente, modifique el tipo y la cantidad de número de llamadas para cada punto de interrupción.  
  
6.  Para guardar el paquete, haga clic en **Guardar los elementos seleccionados** , en el menú **Archivo** .  
  
## <a name="see-also"></a>Consulte también  
 [Herramientas para solucionar problemas con el desarrollo de paquetes](troubleshooting/troubleshooting-tools-for-package-development.md)   
 [Depurar un script estableciendo puntos de interrupción en una tarea script y un componente script](data-flow/transformations/script-component.md)   
 [Codificar y depurar la tarea script](control-flow/script-task.md)   
 [Codificar y depurar el componente de script](extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
  
  
