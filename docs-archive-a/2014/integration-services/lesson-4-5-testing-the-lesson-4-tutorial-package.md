---
title: 'Paso 5: Probar el paquete del tutorial de la lección 4 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5f18df92-0248-4858-836b-c8b02f0e0439
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4a897f99bf68805e4e66c3b6bbe818b312077fb4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87747690"
---
# <a name="step-5-testing-the-lesson-4-tutorial-package"></a>Paso 5: Prueba del paquete del tutorial de la lección 4
  En tiempo de ejecución, el archivo dañado, Currency_BAD.txt, no podrá generar una coincidencia en la transformación Lookup Currency Key. Puesto que la salida de errores de Lookup Currency Key se ha configurado para redirigir las filas con errores al nuevo destino de filas con errores, el componente no genera ningún error y el paquete se ejecuta correctamente. Todas las filas que generan un error se escriben en el archivo ErrorOutput.txt.  
  
 En esta tarea, probará la configuración de la salida de error revisada ejecutando el paquete. Tras ejecutar correctamente el paquete, verá el contenido del archivo ErrorOutput.txt.  
  
> [!NOTE]  
>  Si no desea acumular filas con errores en el archivo ErrorOutput.txt, debe eliminar manualmente el contenido del archivo entre ejecuciones de paquetes.  
  
## <a name="checking-the-package-layout"></a>Comprobar el diseño del paquete  
 Antes de probar el paquete, debe comprobar que los flujos de datos y de control del paquete de la lección 4 contienen los objetos mostrados en los diagramas siguientes. El flujo de control debe ser idéntico al flujo de datos de las lecciones 2 a 4.  
  
 **Flujo de control**  
  
 ![Flujo de control del paquete](../../2014/tutorials/media/task4lesson2control.gif "Flujo de control del paquete")  
  
 **Flujo de datos**  
  
 ![Flujo de datos del paquete](../../2014/tutorials/media/task5lesson5data.gif "Flujo de datos del paquete")  
  
### <a name="to-run-the-lesson-4-tutorial-package"></a>Para ejecutar el paquete de tutorial de la lección 4  
  
1.  En el menú **Depurar**, haga clic en **Iniciar depuración**.  
  
2.  Una vez que se haya completado la ejecución del paquete, en el menú **Depurar** , haga clic en **Detener depuración**.  
  
### <a name="to-verify-the-contents-of-the-erroroutputtxt-file"></a>Para comprobar el contenido del archivo ErrorOutput.txt  
  
-   En el Bloc de notas o en cualquier otro editor de texto, abra el archivo ErrorOutput.txt. El orden predeterminado de las columnas es: AverageRate, CurrencyID, CurrencyDate, EndOfDateRate, ErrorCode, ErrorColumn, ErrorDescription.  
  
     Observe que todas las filas del archivo contienen el valor BAD de CurrencyID sin coincidencia, el valor -1071607778 de ErrorCode, el valor 0 de ErrorColumn y el valor "La fila no produjo ninguna coincidencia durante la búsqueda" de ErrorDescription. El valor de ErrorColumn se establece en 0 porque el error no es específico de columna. Es la operación de búsqueda la que ha generado el error. .  
  
  
