---
title: Página Expresiones | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.expressionspage.f1
helpviewer_keywords:
- Expressions Page dialog box
ms.assetid: c9016ec6-11c1-4ebd-b2a7-0fa6631fd9e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ba4e73ea495456e8f9e452108ab09106a65543ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672210"
---
# <a name="expressions-page"></a>Página Expresiones
  Utilice la página **Expresiones** para editar expresiones de propiedad y obtener acceso a los cuadros de diálogo **Editor de expresiones de propiedad** y **Generador de expresiones** .  
  
 Las expresiones de propiedad actualizan los valores de las propiedades cuando se ejecuta el paquete. Se pueden utilizar expresiones de propiedad con las propiedades de paquetes, tareas, contenedores, administradores de conexión y algunos componentes de flujo de datos. Las expresiones se evalúan y se usan los resultados en lugar de los valores en los que se han establecido las propiedades al configurar el paquete y los objetos de paquete. Las expresiones pueden incluir variables y las funciones y los operadores que proporciona el lenguaje de expresiones. Por ejemplo, se puede generar la línea de asunto de la tarea Enviar correo mediante la concatenación del valor de una variable que contenga la cadena "Pronóstico meteorológico para" y los resultados devueltos de la función GETDATE() para crear la cadena "Pronóstico meteorológico para 5/4/2006".  
  
 Para obtener más información sobre cómo se escriben las expresiones y cómo se usan las expresiones de propiedad, vea [Expresiones de Integration Services &#40;SSIS&#41;](integration-services-ssis-expressions.md) y [Usar expresiones de propiedad en paquetes](use-property-expressions-in-packages.md).  
  
## <a name="options"></a>Opciones  
 **Expresiones (…)**  
 Haga clic en los puntos suspensivos para abrir el cuadro de diálogo **Editor de expresiones de propiedad** . Para más información, consulte [Property Expressions Editor](property-expressions-editor.md).  
  
 **\<property name>**  
 Haga clic en los puntos suspensivos para abrir el cuadro de diálogo **Generador de expresiones** . Para más información, consulte [Expression Builder](expression-builder.md).  
  
## <a name="see-also"></a>Consulte también  
 [Variables de Integration Services &#40;SSIS&#41;](../integration-services-ssis-variables.md)   
 [Variables del sistema](../system-variables.md)   
 [Expresiones de Integration Services &#40;SSIS&#41;](integration-services-ssis-expressions.md)  
  
  
