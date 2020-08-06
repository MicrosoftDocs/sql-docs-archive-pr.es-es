---
title: Visor de perfil de datos ayuda de F1 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dataprofileviewer.f1
helpviewer_keywords:
- Data Profile Viewer [Integration Services]
- Data Profiling task [Integration Services], viewer
ms.assetid: 3469c60a-8f4f-46ba-999a-cb9070197fea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7003e1299938bd53a6d16a5597d4566ba5c46579
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669770"
---
# <a name="data-profile-viewer-f1-help"></a>Visor de perfiles de datos (Ayuda F1)
  Utilice el Visor de perfil de datos para ver la salida de la Tarea de generación de perfiles de datos.  
  
 Para más información sobre cómo usar el Visor de perfil de datos, vea [Visor de perfil de datos](control-flow/data-profile-viewer.md). Para más información sobre cómo usar la Tarea de generación de perfiles de datos, que crea la salida del perfil que se analiza en el Visor de perfil de datos, vea [Configuración de la Tarea de generación de perfiles de datos](control-flow/data-profiling-task.md).  
  
## <a name="static-options"></a>Opciones estáticas  
 **Abrir**  
 Haga clic para buscar el archivo guardado que contiene la salida de la Tarea de generación de perfiles de datos.  
  
 Panel**Perfiles**  
 Expanda el árbol del panel **Perfiles** para ver los perfiles que están incluidos en la salida. Seleccione un perfil para ver los resultados de ese perfil.  
  
 Panel**Mensaje**  
 Muestra mensajes de estado.  
  
 Panel**Obtención de detalles**  
 Muestra las filas de datos que coinciden con un valor en la salida, si el origen de datos que usa la Tarea de generación de perfiles de datos está disponible.  
  
 Por ejemplo, si está viendo la salida de un perfil Distribución de valores de columna de una columna de estados americanos, el panel **Distribución de valor detallado** podría contener una fila para "WA". Haga doble clic en la fila en el panel **Distribución de valores detallados** para ver las filas de datos en las que el valor de la columna de estado sea "WA" en el panel de obtención de detalles.  
  
## <a name="dynamic-options"></a>Opciones dinámicas  
  
### <a name="profile-type--column-length-distribution-profile"></a>Tipo de perfil = Perfil de distribución de longitud de columnas  
  
#### <a name="column-length-distribution-profile---column-pane"></a>Panel Perfil de distribución de longitud de columnas- \<column>  
 **Longitud mínima**  
 Muestra la longitud mínima de los valores de esta columna.  
  
 **Longitud máxima**  
 Muestra la longitud máxima de los valores de esta columna.  
  
 **Omitir espacios iniciales**  
 Muestra si este perfil se calculó con un valor de `IgnoreLeadingSpaces` True o False. Esta propiedad se estableció en la página **Solicitudes de perfil** del Editor de tareas de generación de perfiles de datos.  
  
 **Omitir espacios finales**  
 Muestra si este perfil se calculó con un valor de `IgnoreTrailingSpaces` True o False. Esta propiedad se estableció en la página **Solicitudes de perfil** del Editor de tareas de generación de perfiles de datos.  
  
 **Recuento de filas**  
 Muestra el número de filas de la tabla o vista.  
  
#### <a name="detailed-length-distribution-pane"></a>Panel Distribución de longitud detallado  
 **Longitud**  
 Muestra las longitudes de columna encontradas en la columna de perfiles.  
  
 **Recuento**  
 Muestra el número de filas en las que el valor de la columna de perfiles tiene la longitud que se muestra en la columna **Longitud** .  
  
 **Porcentaje**  
 Muestra el porcentaje de filas en las que el valor de la columna de perfiles tiene la longitud que se muestra en la columna **Longitud** .  
  
### <a name="profile-type--column-null-ratio-profile"></a>Tipo de perfil = Perfil de proporción de columnas nulas  
  
#### <a name="column-null-ratio-profile---column-pane"></a>Panel Perfil de proporción de columnas nulas - \<column>  
 **Recuento nulo**  
 Muestra el número de filas en las que la columna de perfiles tiene el valor null.  
  
 **Porcentaje nulo**  
 Muestra el porcentaje de filas en las que la columna de perfiles tiene el valor null.  
  
 **Recuento de filas**  
 Muestra el número de filas de la tabla o vista.  
  
### <a name="profile-type--column-pattern-profile"></a>Tipo de perfil = Perfil de patrón de columnas  
  
#### <a name="column-pattern-profile---column-pane"></a>Panel Perfil de patrón de columnas - \<column>  
 **Recuento de filas**  
 Muestra el número de filas de la tabla o vista.  
  
#### <a name="pattern-distribution-pane"></a>Panel Distribución del patrón  
 **Patrón**  
 Muestra los patrones calculados para la columna de perfiles.  
  
 **Porcentaje**  
 Muestra el porcentaje de filas cuyos valores coinciden con el patrón que se muestra en la columna **Patrón** .  
  
### <a name="profile-type--column-statistics-profile"></a>Tipo de perfil = Perfil de estadísticas de columnas  
  
#### <a name="column-statistics-profile---column-pane"></a>Panel Perfil de estadísticas de columnas - \<column>  
 **Mínimo**  
 Muestra el valor mínimo situado en la columna de perfiles.  
  
 **Máximo**  
 Muestra el valor máximo situado en la columna de perfiles.  
  
 **Promedio**  
 Muestra el promedio de los valores que se encuentran en la columna de perfiles.  
  
 **Desviación estándar**  
 Muestra la desviación estándar de los valores que se encuentran en la columna de perfiles.  
  
### <a name="profile-type--column-value-distribution-profile"></a>Tipo de perfil = Perfil de distribución de valores de columna  
  
#### <a name="column-value-distribution-profile---column-pane"></a>Panel Perfil de distribución de valores de columna - \<column>  
 **Número de valores distintos**  
 Muestra el recuento de valores distintos que se encuentran en la columna de perfiles.  
  
 **Recuento de filas**  
 Muestra el número de filas de la tabla o vista.  
  
#### <a name="detailed-value-distribution-pane"></a>Panel Distribución de valores detallado  
 **Valor**  
 Muestra los distintos valores que se encuentran en la columna de perfiles.  
  
 **Recuento**  
 Muestra el número de filas en las que la columna de perfiles tiene el valor que se muestra en la columna **Valor** .  
  
 **Porcentaje**  
 Muestra el porcentaje de filas en las que la columna de perfiles tiene el valor que se muestra en la columna **Valor** .  
  
### <a name="profile-type--candidate-key-profile"></a>Tipo de perfil = Perfil de claves candidatas  
  
#### <a name="candidate-key-profile---table-pane"></a>Panel Perfil de claves candidatas - \<table>  
 **Columnas de clave**  
 Muestra las columnas que se seleccionaron para los perfiles como clave candidata.  
  
 **Nivel de clave**  
 Muestra el nivel (como porcentaje) de la columna de clave candidata o de una combinación de columnas. Un nivel de clave menor del 100% indica que hay valores duplicados.  
  
#### <a name="key-violations-pane"></a>Panel Infracciones de clave  
 **\<column1>, \<column2>, etc.**  
 Muestra los valores duplicados que se encontraron en la columna de perfiles.  
  
 **Recuento**  
 Muestra el número de filas en las que la columna especificada tiene el valor que se muestra en la primera columna.  
  
### <a name="profile-type--functional-dependency-profile"></a>Tipo de perfil = Perfil de dependencia funcional  
  
#### <a name="functional-dependency-profile-pane"></a>Panel Perfil de dependencia funcional  
 **Columnas determinantes**  
 Muestra la columna o columnas seleccionadas como columna determinante. En el ejemplo en el que el mismo código postal de Estados Unidos siempre debería tener el mismo estado, el código postal es la columna determinante.  
  
 **Columnas dependientes**  
 Muestra la columna o columnas seleccionadas como columna dependiente. En el ejemplo en el que el mismo código postal de Estados Unidos siempre debería tener el mismo estado, el estado es la columna dependiente.  
  
 **Nivel de dependencia funcional**  
 Muestra el nivel (como porcentaje) de la dependencia funcional entre las columnas. Un nivel de clave menor del 100% indica que hay casos en los que el valor determinante no determina el valor dependiente. En el ejemplo en el que el mismo código postal de Estados Unidos siempre debería tener el mismo estado, esto probablemente indica que algunos valores de estado no son válidos.  
  
#### <a name="functional-dependency-violations-pane"></a>Panel Infracciones de dependencia funcional  
  
> [!NOTE]  
>  Un porcentaje alto de valores erróneos en los datos podría provocar resultados inesperados en un perfil Dependencia funcional. Por ejemplo, el 90% de las filas tienen el valor "WI" como estado para el valor "98052" de código postal. El perfil notifica filas que contienen valor de estado correcto de "WA" como infracciones.  
  
 **\<determinant column name>**  
 Muestra el valor de la columna determinante o la combinación de columnas en esta infracción de la dependencia funcional.  
  
 **\<dependent column name>**  
 Muestra el valor de la columna dependiente en esta infracción de la dependencia funcional.  
  
 **Recuento de soporte**  
 Muestra el número de filas en las que el valor de columna determinante determina la columna dependiente.  
  
 **Recuento de infracciones**  
 Muestra el número de filas en las que el valor de columna determinante no determina la columna dependiente. (Estas son las filas en las que el valor dependiente es el que se muestra en la columna **\<dependent column name>** ).  
  
 **Porcentaje admitido**  
 Muestra el porcentaje de filas en las que el valor de columna determinante determina la columna dependiente.  
  
### <a name="profile-type--value-inclusion-profile"></a>Tipo de perfil = Perfil de inclusión de valores  
  
#### <a name="value-inclusion-profile-pane"></a>Panel Perfil de inclusión de valores  
 **Columnas de subconjunto**  
 Muestra la columna o combinación de columnas que se incluyeron en el perfil para determinar si están en las columnas de superconjunto.  
  
 **Columnas de superconjunto**  
 Muestra la columna o combinación de columnas que se incluyeron en el perfil para determinar si incluyen los valores en las columnas de subconjunto.  
  
 **Nivel de inclusión**  
 Muestra el nivel (como porcentaje) de la superposición entre las columnas. Un nivel de clave menor que 100% indica que hay casos en los que el valor de subconjunto no se encuentra entre los valores del superconjunto.  
  
#### <a name="inclusion-violations-pane"></a>Panel Infracciones de inclusión  
 **\<column1>, \<column2>, etc.**  
 Muestra los valores en la columna o columnas del subconjunto que no se encontraban en la columna o columnas del superconjunto.  
  
 **Recuento**  
 Muestra el número de filas en las que la columna especificada tiene el valor que se muestra en la primera columna.  
  
## <a name="see-also"></a>Consulte también  
 [Visor de perfil de datos](control-flow/data-profile-viewer.md)   
 [Visor y tarea de generación de perfiles de datos](control-flow/data-profiling-task-and-viewer.md)  
  
  
