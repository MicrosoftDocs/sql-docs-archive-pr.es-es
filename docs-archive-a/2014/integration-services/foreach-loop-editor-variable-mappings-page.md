---
title: Editor de bucles foreach (página asignaciones de variables) | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.foreachloopcontainer.mapping.f1
ms.assetid: aa847b87-f391-48a5-9849-eeda2d6b00b9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cd37c8c6c00f18d8b5493a058239cc880ecc1f5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87752277"
---
# <a name="foreach-loop-editor-variable-mappings-page"></a>Editor de bucles Foreach (página Asignaciones de variables)
  Use la página **Asignaciones de variables** del cuadro de diálogo **Editor de bucles Foreach** para asignar variables al valor de la colección. El valor de la variable se actualiza con los valores de la colección en cada iteración del bucle.  
  
 Para obtener más información acerca de cómo utilizar el contenedor de bucles Foreach en un paquete de Integration Services, vea [Foreach Loop Container](control-flow/foreach-loop-container.md) . Para saber cómo se configura, vea [Configurar un contenedor de bucles Foreach](../../2014/integration-services/configure-a-foreach-loop-container.md).  
  
 El tutorial de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], llamado Tutorial para crear un paquete ETL sencillo, incluye una lección que le enseña a agregar y configurar un bucle Foreach.  
  
## <a name="options"></a>Opciones  
 **Variable**  
 Seleccione una variable existente o haga clic en \<**New variable...**> para crear una nueva.  
  
> [!NOTE]  
>  Una vez asignada una variable, se agregará automáticamente una nueva fila a la lista **Variable**.  
  
 **Temas relacionados**: [Variables de Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Agregar variable](../../2014/integration-services/add-variable.md)  
  
 **Index**  
 Si utiliza el enumerador de elementos para Foreach, especifique el índice de la columna en el valor de la colección para asignarlo a la variable. Si utiliza otros tipos de enumeradores, el índice será de solo lectura.  
  
> [!NOTE]  
>  El índice se basa en 0.  
  
 **Temas relacionados**: crear [bucles entre archivos y tablas de Excel mediante un contenedor de bucles foreach](control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
 **Eliminar**  
 Seleccione una variable y haga clic en **Eliminar**.  
  
## <a name="see-also"></a>Consulte también  
 [Referencia de errores y mensajes de Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor de bucles foreach &#40;página general&#41;](general-page-of-integration-services-designers-options.md)   
 [Página colección de &#40;del editor de bucles foreach&#41;](../../2014/integration-services/foreach-loop-editor-collection-page.md)   
 [Página Expresiones](expressions/expressions-page.md)   
 [Contenedor de bucles For](control-flow/for-loop-container.md)  
  
  
