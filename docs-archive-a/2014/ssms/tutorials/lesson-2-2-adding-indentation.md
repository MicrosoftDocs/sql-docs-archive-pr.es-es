---
title: Agregar sangría | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 9dce05c1-c52f-455d-8b8d-6f303e242760
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2d0b7ee8819f98df5e5658321a3d950ca31083b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674498"
---
# <a name="adding-indentation"></a>Agregar sangría
  El Editor de consultas permite aplicar sangría a grandes secciones de código en un solo paso y cambiar la extensión de la sangría.  
  
## <a name="indenting-code"></a>Aplicar sangría a líneas de código  
  
#### <a name="to-indent-multiple-lines-of-code"></a>Para aplicar sangría a varias líneas de código  
  
1.  En la barra de herramientas, haga clic en **Nueva consulta**.  
  
2.  Cree una segunda consulta que seleccione las columnas **BusinessEntityID**, FirstName, **MiddleName**y **LastName** de la tabla **Person** del esquema **Person** . Coloque cada columna en una línea separada de manera que el código tenga el aspecto siguiente:  
  
    ```  
    -- Search for a contact  
    SELECT   
    BusinessEntityID,  
    FirstName,   
    MiddleName,   
    LastName  
    FROM Person.Person  
    WHERE LastName = 'Sanchez';  
    GO  
    ```  
  
3.  Seleccione todo el texto desde `BusinessEntityID` hasta `LastName`.  
  
4.  En la barra de herramientas del **Editor SQL** , haga clic en **Aumentar sangría** para aplicar la sangría a todas las líneas al mismo tiempo.  
  
#### <a name="to-change-the-default-indentation"></a>Para cambiar la sangría predeterminada  
  
1.  En el menú **Herramientas** , haga clic en **Opciones**.  
  
2.  Expanda **Editor de texto**, **Todos los lenguajes**, haga clic en **Pestañas** y configure los valores de sangría apropiados. Observe que puede cambiar tanto el tamaño de la sangría como el de las pestañas y especificar si éstas deben cambiarse por espacios.  
  
     ![Apariencia del cuadro de diálogo Pestañas](media/tabsdialog.gif "Apariencia del cuadro de diálogo Pestañas")  
  
3.  Haga clic en **OK**.  
  
## <a name="next-task-in-lesson"></a>Siguiente tarea de la lección  
 [Maximizar el Editor de consultas](lesson-2-3-maximizing-query-editor.md)  
  
  
