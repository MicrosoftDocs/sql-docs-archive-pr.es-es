---
title: Editor de origen de CDC (página salida de error) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsource.errorhandling.f1
ms.assetid: 8a4c2cb8-fd2f-4c45-824f-b93473a8981e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b39532304fddfa90fabe8cafe2a6caf5b1fb5c8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676622"
---
# <a name="cdc-source-editor-error-output-page"></a>Editor de origen de CDC (página Salida de error)
  Use la página **Salida de error** del cuadro de diálogo **Editor de origen de CDC** para seleccionar las opciones de control de errores.  
  
 Para obtener más información acerca del origen de CDC, vea [CDC Source](data-flow/cdc-source.md).  
  
## <a name="task-list"></a>Lista de tareas  
 **Para abrir la página Salida de error del Editor de origen de CDC**  
  
1.  En [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], abra el paquete [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] que tiene el origen de CDC.  
  
2.  En la pestaña **Flujo de datos** , haga doble clic en el origen de CDC.  
  
3.  En el **Editor de origen de CDC**, haga clic en **Salida de error**.  
  
## <a name="options"></a>Opciones  
 **Entrada/salida**  
 Muestra el nombre del origen de datos.  
  
 **Columna**  
 Muestra las columnas externas (origen) que se han seleccionado en la página **Administrador de conexiones** del cuadro de diálogo **Editor de origen de CDC** .  
  
 **Error**  
 Seleccione la forma en la que el origen de CDC debe controlar errores en un flujo: omitir el error, redirigir la fila o hacer que el componente no funcione.  
  
 **Truncamiento**  
 Seleccione la forma en la que el origen de CDC debe controlar el truncamiento en un flujo: omitir el error, redirigir la fila o hacer que el componente no funcione.  
  
 **Descripción**  
 No se usa.  
  
 **Establecer este valor en las celdas seleccionadas**  
 Seleccione la forma en la que el origen de CDC controla todas las celdas seleccionadas cuando se produce un error o un truncamiento: omitir el error, redirigir la fila o hacer que el componente no funcione.  
  
 **Aplicar**  
 Aplica las opciones de control de errores a las celdas seleccionadas.  
  
## <a name="error-handling-options"></a>Opciones de control de errores  
 Use las opciones siguientes para configurar la forma en la que el origen de CDC controla errores y truncamientos.  
  
 **Error de componente**  
 La tarea Flujo de datos genera un error cuando se produce un error o truncamiento. Este es el comportamiento predeterminado.  
  
 **Omitir error**  
 El error o el truncamiento se omite y la fila de datos se dirige a la salida de origen de CDC.  
  
 **Redirigir fila**  
 La fila de datos de error o truncamiento se dirige a la salida de error del origen de CDC. En este caso, se usa el control de errores de origen de CDC. Para más información, consulte [CDC Source](data-flow/cdc-source.md).  
  
## <a name="see-also"></a>Consulte también  
 [Editor de origen de CDC &#40;página Administrador de conexiones&#41;](../../2014/integration-services/cdc-source-editor-connection-manager-page.md)   
 [Editor de origen de CDC &#40;página Columnas&#41;](../../2014/integration-services/cdc-source-editor-columns-page.md)  
  
  
