---
title: Editor de orígenes de ADO NET (página salida de error) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetsource.erroroutput.f1
ms.assetid: 4dd9d129-a95c-4d3a-bbbf-e84a39089950
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b9ee480caa8764d70b52b25a416f200f353d30c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87749415"
---
# <a name="ado-net-source-editor-error-output-page"></a>Editor de orígenes de ADO NET (página Salida de error)
  Utilice la página **Salida de error** del cuadro de diálogo **Editor de orígenes de ADO NET** para seleccionar las opciones de control de errores y para establecer las propiedades en las columnas de salida de errores.  
  
 Para obtener más información acerca del origen de ADO NET, vea [ADO NET Source](data-flow/ado-net-source.md).  
  
 **Para abrir la página Salida de error**  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], abra el paquete [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] que tiene el origen de ADO NET.  
  
2.  En la pestaña **Flujo de datos** , haga doble clic en el origen de ADO NET.  
  
3.  En el **Editor de orígenes de ADO NET**, haga clic en **Salida de error**.  
  
## <a name="options"></a>Opciones  
 **Entrada/salida**  
 Muestra el nombre del origen de datos.  
  
 **Columna**  
 Muestra las columnas externas (origen) que se han seleccionado en la página **Administrador de conexiones** del cuadro de diálogo **Editor de orígenes de ADO NET** .  
  
 **Error**  
 Permite especificar qué debe ocurrir cuando se produce un error: omitir el error, redirigir la fila o hacer que el componente no funcione.  
  
 **Temas relacionados:** [Control de errores en los datos](data-flow/error-handling-in-data.md)  
  
 **Truncamiento**  
 Permite especificar qué debe ocurrir cuando se produce un truncamiento: omitir el error, redirigir la fila o hacer que el componente no funcione.  
  
 **Descripción**  
 Muestra la descripción del error.  
  
 **Establecer este valor en las celdas seleccionadas**  
 Permite especificar qué debe ocurrir en todas las celdas seleccionadas cuando se produce un error o un truncamiento: omitir el error, redirigir la fila o hacer que el componente no funcione.  
  
 **Aplicar**  
 Aplica la opción de control de errores a las celdas seleccionadas.  
  
## <a name="see-also"></a>Consulte también  
 [Editor de orígenes de ADO NET &#40;página Administrador de conexiones&#41;](../../2014/integration-services/ado-net-source-editor-connection-manager-page.md)   
 [Editor de orígenes de ADO NET &#40;página columnas&#41;](../../2014/integration-services/ado-net-source-editor-columns-page.md)   
 [Administrador de conexiones ADO.NET](connection-manager/ado-net-connection-manager.md)  
  
  
