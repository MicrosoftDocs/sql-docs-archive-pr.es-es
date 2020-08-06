---
title: 'Paso 3: Modificar el Administrador de conexiones de archivos planos | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 459e3995-2116-4f15-aaa2-32f26113869c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b897f9412a8f2978ebe4137e3e79bf1d28c97844
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663580"
---
# <a name="step-3-modifying-the-flat-file-connection-manager"></a>Paso 3: Modificación del Administrador de conexiones de archivos planos
  En esta tarea, modificará el administrador de conexiones de archivos planos que creó y configuró en la lección 1. Cuando se creó inicialmente, el administrador de conexiones de archivos planos se configuró para cargar de forma estática un único archivo. Para permitir que el Administrador de conexiones de archivos planos cargue archivos de forma iterativa, debe modificar la propiedad ConnectionString del administrador de conexiones de modo que acepte la variable `User:varFileName`, definida por el usuario, que contiene la ruta de acceso del archivo que se cargará en tiempo de ejecución.  
  
 Al modificar el administrador de conexiones para que use la variable definida por el usuario `User::varFileName`para rellenar la propiedad ConnectionString del administrador de conexiones, este podrá conectarse a distintos archivos planos. En tiempo de ejecución, cada iteración del contenedor de bucles Foreach actualizará dinámicamente la variable `User::varFileName` . A su vez, actualizar esta variable da lugar a que el administrador de conexiones se conecte a un archivo plano distinto, y que la tarea de flujo de datos procese un conjunto de datos distinto.  
  
### <a name="to-configure-the-flat-file-connection-manager-to-use-a-variable-for-the-connection-string"></a>Para configurar el Administrador de conexiones de archivos planos de modo que utilice una variable para la cadena de conexión  
  
1.  En el panel **Administradores de conexión** , haga clic con el botón derecho en **Sample Flat File Source Data**y, después, seleccione **Propiedades**.  
  
2.  En el ventana Propiedades, para las **expresiones**, haga clic en la celda vacía y, a continuación, haga clic en el botón de puntos suspensivos **(...)**.  
  
3.  En el cuadro de diálogo **Editor de expresiones de propiedad** , en la columna **propiedad** , escriba o seleccione `ConnectionString` .  
  
4.  En la columna **expresión** , haga clic en el botón de puntos suspensivos **(...)** para abrir el cuadro de diálogo **generador de expresiones** .  
  
5.  En el cuadro de diálogo **Generador de expresiones** , expanda el nodo **Variables** .  
  
6.  Arrastre la variable **User:: varFileName**al cuadro **expresión** .  
  
7.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Generador de expresiones** .  
  
8.  Haga clic en **Aceptar** de nuevo para cerrar el cuadro de diálogo **Editor de expresiones de propiedad** .  
  
## <a name="next-lesson-task"></a>Tarea de la siguiente lección  
 [Paso 4: Prueba del paquete del tutorial de la lección 2](../integration-services/lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
  
