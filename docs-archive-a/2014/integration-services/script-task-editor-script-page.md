---
title: Editor de la tarea script (página script) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scripttask.script.f1
helpviewer_keywords:
- Script Task Editor
ms.assetid: 93da0e0d-83f5-406d-b144-4cce216571cb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4eec491cc689d7d5c616e0819075e1ee5159d4e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744195"
---
# <a name="script-task-editor-script-page"></a>Editor de la tarea Script (página Script)
  Use la página **Script** del cuadro de diálogo **Editor de la tarea Script** para establecer las propiedades del script y para especificar las variables a las que se puede tener acceso desde el mismo.  
  
> [!NOTE]  
>  En [!INCLUDE[ssISversion10](../includes/ssisversion10-md.md)] y versiones posteriores, se recompilan todos los scripts. En versiones anteriores, se establece una propiedad **PrecompileScriptIntoBinaryCode** para especificar que se precompiló el script.  
  
 Para obtener más información acerca de la tarea Script, vea [Script Task](control-flow/script-task.md) y [Configurar la tarea Script en el editor de la tarea Script](extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md). Para obtener información sobre cómo programar la tarea Script, vea [Extending the Package with the Script Task](extending-packages-scripting/task/extending-the-package-with-the-script-task.md).  
  
## <a name="options"></a>Opciones  
 **Lenguaje de script**  
 Seleccione el lenguaje de scripting para la tarea, [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic o [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C#.  
  
 Una vez haya creado un script para la tarea, no podrá cambiar el valor de la propiedad **ScriptLanguage** .  
  
 Para establecer el lenguaje de scripting predeterminado para la tarea Script, utilice la opción **Lenguaje de scripting** en la página **General** del cuadro de diálogo **Opciones** . Para obtener más información, vea [General Page](general-page-of-integration-services-designers-options.md).  
  
 **EntryPoint**  
 Especifique el método que el tiempo de ejecución de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] llama como punto de entrada en el código de la tarea Script. El método especificado debe estar en la clase ScriptMain del [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proyecto Tools for Applications (VSTA). la clase ScriptMain es la clase predeterminada que generan las plantillas de script.  
  
 Si cambia el nombre del método en el proyecto VSTA, deberá cambiar el valor de la propiedad **EntryPoint** .  
  
 **Variables de solo lectura**  
 Escriba una lista separada por comas de variables de solo lectura que estén disponibles para el script, o bien haga clic en el botón de puntos suspensivos (**…**) y seleccione las variables en el cuadro de diálogo **Seleccionar variables**.  
  
> [!NOTE]  
>  Los nombres de variables distinguen entre mayúsculas y minúsculas.  
  
 **Variables de lectura/escritura**  
 Escriba una lista separada por comas de variables de lectura y escritura que estén disponibles para el script, o bien haga clic en el botón de puntos suspensivos (**…**) y seleccione las variables en el cuadro de diálogo **Seleccionar variables**.  
  
> [!NOTE]  
>  Los nombres de variables distinguen entre mayúsculas y minúsculas.  
  
 **Editar script**  
 Abre la VSTA IDE donde puede crear o modificar el script.  
  
## <a name="see-also"></a>Consulte también  
 [Referencia de errores y mensajes de Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Página general](general-page-of-integration-services-designers-options.md)   
 [Editor de la tarea script &#40;página general&#41;](../../2014/integration-services/script-task-editor-general-page.md)   
 [Página Expresiones](expressions/expressions-page.md)   
 [Ejemplos de tareas de script](extending-packages-scripting-task-examples/script-task-examples.md)   
 [Variables de Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md)   
 [Agregar, eliminar, cambiar el ámbito de la variable definida por el usuario en un paquete](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
  
