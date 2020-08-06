---
title: Ejecución de opciones de consulta (página ANSI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.ansi.f1
ms.assetid: c90d7cdf-3309-46f4-b900-220521bb9552
author: rothja
ms.author: jroth
ms.openlocfilehash: 013a7a318ed7f8db9156700f789ae64cf3e4e017
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87747727"
---
# <a name="query-options-execution-ansi-page"></a>Ejecución de Opciones de consulta (página ANSI)
  Use esta página para especificar que [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ejecutará las consultas utilizando todos o parte de los valores de configuración especificados en el estándar ISO (ANSI).  
  
## <a name="ui-element-list"></a>Lista de elementos de la interfaz de usuario  
 **SET ANSI_DEFAULTS**  
 Selecciona todos los valores de configuración ISO predeterminados. Este cuadro no está disponible de forma predeterminada, ya que solo se configuran algunos valores ISO.  
  
 **SET QUOTED_IDENTIFIER**  
 Especifica los identificadores de objeto entre comillas. Esta opción está activada de forma predeterminada.  
  
 **SET ANSI_NULL_DFLT_ON**  
 Permite usar valores NULL para todos los tipos de datos definidos por el usuario que no se hayan definido explícitamente como NOTNULL en una instrucción CREATE TABLE o ALTER TABLE (estado predeterminado). Esta opción está activada de forma predeterminada.  
  
 **SET IMPLICIT_TRANSACTIONS**  
 Esta opción no está activada de forma predeterminada.  
  
 **SET CURSOR_CLOSE_ON_COMMIT**  
 Cierra automáticamente cualquier cursor abierto (de conformidad con ISO) al confirmarse una transacción. Si esta opción no está activada (está establecida en OFF), los cursores permanecen abiertos a lo largo de los límites de las transacciones y solo se cierran cuando termina la conexión o cuando se cierran de manera explícita. Esta opción no está activada de forma predeterminada.  
  
 **SET ANSI_PADDING**  
 Controla el modo en que la columna almacena valores más cortos que el tamaño definido de la columna y el modo en que almacena valores con espacios en blanco finales en datos de tipo **Char**, **VARCHAR**, **Binary**y **varbinary** . Esta opción solo afecta a la definición de nuevas columnas. Una vez creada la columna, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] almacena los valores de acuerdo con la opción establecida en el momento de su creación. Las columnas existentes no se ven afectadas por los cambios posteriores de esta opción. Esta casilla está activada de forma predeterminada.  
  
 **SET ANSI_WARNINGS**  
 Especifica el comportamiento estándar ISO para diversas condiciones de error:  
  
-   Cuando esta casilla está activada, si aparecen valores NULL en funciones de agregado (como SUM, AVG, MAX, MIN, STDEV, STDEVP, VAR, VARP o COUNT), se genera un mensaje de advertencia. Cuando es **OFF**, no se emite ninguna advertencia.  
  
-   Cuando esta casilla está desactivada, los errores de división por cero y desbordamiento aritmético hacen que la instrucción se revierta y que se genere un mensaje de error. Cuando es OFF, los errores de división por cero y de desbordamiento aritmético hacen que se devuelvan valores NULL. El comportamiento por el cual una división por cero o un error de desbordamiento aritmético provocan que se devuelvan valores NULL se produce si se intentan ejecutar instrucciones INSERT o UPDATE en una columna de tipo carácter, Unicode o binaria en la que la longitud del nuevo valor excede el tamaño máximo de la columna. Si **SET ANSI_WARNINGS está establecido** en ON, la operación de inserción o actualización se cancela según lo especificado por el estándar ISO. Los espacios finales se omiten para las columnas de caracteres y los valores NULL finales se omiten para las columnas binarias. Cuando es OFF, los datos se truncan para ajustarlos al tamaño de la columna y la instrucción se ejecuta correctamente.  
  
 Esta opción está activada de forma predeterminada.  
  
 **SET ANSI_NULLS**  
 Especifica el comportamiento conforme a ISO de los operadores de comparación Es igual a (`=`) y No es igual a (`<>`) cuando se utilizan con valores NULL. Cuando la opción **SET ANSI_NULLS** está seleccionada, todas las comparaciones con un valor NULL se evalúan como UNKNOWN, el comportamiento conforme a ISO. Si **SET ANSI_NULLS** no se selecciona, las comparaciones de los datos con un valor NULL se evalúan como TRUE si el valor de datos es NULL. Esta opción está activada de forma predeterminada.  
  
 **Valores predeterminados**  
 Restablece todos los valores de esta página a los valores predeterminados originales.  
  
  
