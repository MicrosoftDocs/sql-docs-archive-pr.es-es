---
title: 'Opciones (editor de texto: Transact-SQL-IntelliSense) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.SQL.Advanced
- VS.ToolsOptionsPages.Text_Editor.SQL_Server_Tools.Advanced
dev_langs:
- TSQL
ms.assetid: 1855d916-5bf9-4d94-b0fb-9f9bb05ff950
author: rothja
ms.author: jroth
ms.openlocfilehash: 2d8f9c865516dc5e4c0ddadbdc908a9b4c8ec366
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674987"
---
# <a name="options-text-editor-transact-sql-intellisense"></a>Opciones (editor de texto: Transact-SQL-IntelliSense)
  El cuadro de diálogo **Opciones** le permite modificar las opciones de IntelliSense para el Editor de consultas de [!INCLUDE[ssDE](../includes/ssde-md.md)] . Estas opciones se encuentran disponibles cuando, en el menú **Herramientas**, se hace clic en **Opciones**, se expande la carpeta **Editor de texto**, se expande la carpeta **Transact-SQL** y se selecciona **Avanzadas**.  
  
## <a name="transact-sql-intellisense-settings"></a>Configuración de Transact-SQL IntelliSense  
 Especifica las opciones de IntelliSense para el Editor de consultas de [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
### <a name="enable-intellisense"></a>Habilitar IntelliSense  
 Habilita las características de IntelliSense. Si este cuadro no está seleccionado, las opciones específicas de IntelliSense no están disponibles. De forma predeterminada, esta casilla está activada.  
  
 **Subrayar errores**  
 Identifica errores sintácticos y semánticos en las instrucciones [!INCLUDE[tsql](../includes/tsql-md.md)] en la ventana de consulta. Todos los errores y advertencias aparecen en rojo. Los errores y advertencias solo se admiten en las instrucciones [!INCLUDE[tsql](../includes/tsql-md.md)] para las que se ha implementado IntelliSense. De forma predeterminada, esta casilla está activada.  
  
 **Instrucciones de esquema**  
 Habilita la función de esquematización al abrir un archivo. Esto crea bloques plegables de código [!INCLUDE[tsql](../includes/tsql-md.md)] . De forma predeterminada, esta casilla está activada.  
  
 **Tamaño máximo de script**  
 Especifica el tamaño en el que se deshabilita la funcionalidad de IntelliSense. Si un script supera el tamaño especificado, se emite un mensaje de advertencia. Todas las características de IntelliSense, excepto la codificación en colores, se deshabilitan para esa ventana del editor. IntelliSense se vuelve a habilitar cuando se elimina el texto suficiente como para reducir el tamaño del script por debajo del límite. Si se habilita IntelliSense para los scripts grandes, se puede disminuir el rendimiento en equipos lentos. Los tamaños permitidos son 100 KB, 500 KB, 1 MB, 2 MB e Ilimitado. El valor predeterminado es 1 MB.  
  
 **Uso de mayúsculas o minúsculas en nombres de funciones integradas**  
 Especifica si los nombres de funciones de [!INCLUDE[tsql](../includes/tsql-md.md)] integradas que están incluidas en listas de finalización usan letras mayúsculas, como DATEADD, o minúsculas, como dateadd. Seleccione la opción que mejor convenga a las convenciones de codificación de [!INCLUDE[tsql](../includes/tsql-md.md)] que está utilizando.  
  
## <a name="see-also"></a>Consulte también  
 [Solución de problemas de IntelliSense &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/troubleshooting-intellisense.md)  
  
  
