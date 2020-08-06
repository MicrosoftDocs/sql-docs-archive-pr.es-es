---
title: Editor de transformación división condicional | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.conditionalsplittransformation.f1
helpviewer_keywords:
- Conditional Split Transformation Editor
ms.assetid: c30e1633-537a-4837-9991-6203c6f2a21e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 386a93eb7c3058c7c3e98f2b652199d115d841f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663637"
---
# <a name="conditional-split-transformation-editor"></a>División condicional, editor de transformación
  Use el cuadro de diálogo **Editor de transformación División condicional** para crear expresiones, establecer el orden de evaluación de expresiones y asignar un nombre a los resultados de una división condicional. Este cuadro de diálogo incluye operadores y funciones matemáticas, de cadenas y de fecha y hora que puede utilizar para generar expresiones. La primera condición evaluada como True determinará la salida a la que se dirigirá una fila.  
  
> [!NOTE]  
>  La transformación División condicional dirige cada fila de entrada a una sola salida. Si escribe diversas condiciones, la transformación enviará cada fila a la primera salida para la que la condición es True y descartará las siguientes condiciones para dicha fila. Si necesita evaluar varias condiciones sucesivamente, podría necesitar concatenar diversas transformaciones de División condicional en el flujo de datos.  
  
 Para más información sobre la transformación División condicional, vea [Transformación División condicional](data-flow/transformations/conditional-split-transformation.md).  
  
## <a name="options"></a>Opciones  
 **Pedido**  
 Seleccione una fila y utilice las teclas de dirección de la derecha para cambiar el orden de evaluación de las expresiones.  
  
 **Nombre de salida**  
 Escriba un nombre de salida. El valor predeterminado es una lista numerada de casos, pero puede elegir cualquier nombre descriptivo único.  
  
 **Condition**  
 Escriba una expresión o genere una arrastrándola de la lista de columnas, variables, funciones y operadores disponibles.  
  
 Puede especificar el valor de esta propiedad con una expresión de propiedad.  
  
 **Temas relacionados: **  [Expresiones de Integration Services &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md), [Operadores &#40;expresión de SSIS&#41;](expressions/operators-ssis-expression.md) y [Funciones &#40;expresión de SSIS&#41](expressions/functions-ssis-expression.md)  
  
 **Nombre de salida predeterminado**  
 Escriba un nombre para la salida predeterminada o utilice el nombre predeterminado.  
  
 **Configurar la salida de errores**  
 Especifique cómo quiere controlar los errores mediante el cuadro de diálogo [Configurar la salida de errores](../../2014/integration-services/configure-error-output.md) .  
  
## <a name="see-also"></a>Consulte también  
 [Referencia de errores y mensajes de Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Dividir un conjunto de datos usando la transformación División condicional](data-flow/transformations/split-a-dataset-by-using-the-conditional-split-transformation.md)  
  
  
