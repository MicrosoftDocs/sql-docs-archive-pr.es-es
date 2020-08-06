---
title: Configuración de la tarea de generación de perfiles de datos | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling task [Integration Services], configuring
ms.assetid: fe050ca4-fe45-43d7-afa9-99478041f9a8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fefe097905f2f5effaece8e352e21df095004e46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674245"
---
# <a name="setup-of-the-data-profiling-task"></a>Configuración de la Tarea de generación de perfiles de datos
  El primer paso previo a la revisión de un perfil de los datos de origen consiste en configurar y ejecutar la tarea de generación de perfiles de datos. Esta tarea se crea dentro de un paquete de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Para configurar la tarea de generación de perfiles de datos, utilice el Editor de tareas de generación de perfiles de datos. Este editor le permite seleccionar dónde deben generarse los perfiles y qué perfiles deben calcularse. Una vez configurada la tarea, se ejecuta el paquete para calcular los perfiles de datos.  
  
## <a name="requirements-and-limitations"></a>Requisitos y limitaciones  
 La tarea de generación de perfiles de datos solo funciona con datos que estén almacenados en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. No funciona con orígenes de datos de otros fabricantes o basados en archivos.  
  
 Además, para ejecutar un paquete que contiene la tarea de generación de perfiles de datos, debe utilizar una cuenta que tenga permisos de lectura/escritura, incluidos los permisos CREATE TABLE, en la base de datos tempdb.  
  
## <a name="data-profiling-task-in-a-package"></a>Tarea Generación de perfiles de datos en un paquete  
 La tarea de generación de perfiles de datos solo configura los perfiles y crea el archivo de salida que contiene los perfiles calculados. Para revisar este archivo de salida, debe usar el Visor de perfil de datos, un programa visor independiente. Dado que debe ver la salida de forma independiente, puede utilizar la tarea de generación de perfiles de datos en un paquete que no contenga ninguna otra tarea.  
  
 Sin embargo, no tiene que utilizar la tarea de generación de perfiles de datos como única tarea en un paquete. Si desea realizar la generación de perfiles de datos en el flujo de trabajo o en el flujo de datos de un paquete más complejo, tiene las opciones siguientes:  
  
-   Implementar una lógica condicional basada en el archivo de salida de la tarea, en el flujo de control del paquete, colocar una tarea Script después de la tarea de generación de perfiles de datos. A continuación, puede utilizar esta tarea Script para consultar el archivo de salida.  
  
-   Para generar perfiles de datos en el flujo de datos una vez cargados y transformados los datos, tiene que guardar temporalmente los datos cambiados en una tabla de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . A continuación, puede generar perfiles de los datos guardados.  
  
 Para obtener más información, vea [Incorporar una tarea de generación de perfiles de datos en un flujo de trabajo de paquetes](incorporate-a-data-profiling-task-in-package-workflow.md).  
  
## <a name="setup-of-the-task-output"></a>Configuración de la salida de la tarea  
 Después de que la tarea de generación de perfiles de datos esté en un paquete, debe configurar la salida para los perfiles que la tarea calculará. Para configurar la salida para los perfiles, se utiliza la página **General** del Editor de tareas de generación de perfiles de datos. Además de especificar el destino para la salida, la página **General** también le ofrece la capacidad de realizar un perfil rápido de los datos. Cuando selecciona **Perfil rápido**, la tarea de generación de perfiles de datos genera perfiles en una tabla o vista utilizando algunos o todos los perfiles predeterminados con su configuración predeterminada.  
  
 Para obtener más información, vea [Editor de tareas de generación de perfiles de datos &#40;página General&#41;](../general-page-of-integration-services-designers-options.md) y [Formulario de perfil rápido de tabla única &#40;tarea de generación de perfiles de datos&#41;](data-profiling-task.md).  
  
> [!IMPORTANT]  
>  El archivo de salida podría contener datos confidenciales acerca de la base de datos y de los datos que contiene. Para conocer sugerencias sobre cómo hacer que este archivo sea más seguro, vea [Acceso a los archivos usados por los paquetes](../access-to-files-used-by-packages.md).  
  
## <a name="selection-and-configuration-of-the-profiles-to-be-computed"></a>Selección y configuración de los perfiles que hay que calcular  
 Después de configurar el archivo de resultados, es preciso seleccionar los perfiles de datos que hay que calcular. La tarea de generación de perfiles de datos puede calcular ocho perfiles de datos diferentes. Cinco de estos perfiles analizan columnas individuales y los otros tres analizan varias columnas o relaciones entre las columnas y las tablas. En una única tarea de generación de perfiles puede calcular varias filas para varias columnas o combinaciones de columnas en varias tablas o vistas.  
  
 En la tabla siguiente se describen los informes que calcula cada uno de estos perfiles y los tipos de datos para los que el perfil es válido.  
  
|Para calcular|Que ayudan a identificar|Utilice este perfil|  
|----------------|-------------------------|----------------------|  
|Todas las longitudes de valores de cadena distintas existentes en la columna seleccionada y el porcentaje de filas de la tabla que representa cada longitud.|**Valores de cadena que no son válidos**: por ejemplo, si genera perfiles de una columna que se supone que usa dos caracteres para los códigos de estado de Estados Unidos, pero detecta valores que tienen más de dos caracteres.|**Distribución de longitud de columnas:** Válido para una columna con uno de estos tipos de datos:<br /><br /> Tipos de datos de caracteres: `char`, `nchar`, `varchar` y `nvarchar`|  
|Un conjunto de expresiones regulares que cubren el porcentaje especificado de valores de una columna de cadenas.<br /><br /> También, para buscar expresiones regulares que se pueden utilizar en el futuro para validar los nuevos valores|**Valores de cadena que no son válidos o que no tienen el formato correcto:** Por ejemplo, un perfil de patrón de una columna de códigos postales podría generar las expresiones regulares: \d {5} -\d {4} , \d {5} y \d {9} . Si la salida contiene otras expresiones regulares, los datos contienen valores que no son válidos o cuyo formato no es correcto.|**Perfil de patrón de columnas-** Válido para una columna con uno de estos tipos de datos:<br /><br /> Tipos de datos de caracteres: `char`, `nchar`, `varchar` y `nvarchar`|  
|El porcentaje de valores NULL existentes en la columna seleccionada.|**Una proporción inesperadamente alta de valores NULL en una columna:** Por ejemplo, si se va a generar un perfil de una columna que se supone que contiene Estados Unidos códigos postales, pero se detecta un porcentaje inaceptablemente alto de códigos postales que faltan.|**Proporción de columnas nulas:** Válido para una columna con estos tipos de datos:<br /><br /> Cualquier tipo de datos. Esto incluye los tipos `image`, `text`, `xml`, los tipos definidos por el usuario y los tipos variant.|  
|Estadísticas, como los valores mínimo, máximo, medio y la desviación estándar para las columnas numéricas, y los valores mínimo y máximo para las columnas `datetime`.|**Valores numéricos y fechas no válidas**: por ejemplo, si se va a generar un perfil de una columna de fechas históricas, pero se detecta una fecha máxima futura.|**Perfil de estadísticas de columnas-** Válido para una columna con uno de estos tipos de datos:<br /><br /> Tipos de datos numéricos: tipos enteros (excepto `bit`), `money`, `smallmoney`, `decimal`, `float`, `real` y `numeric`<br /><br /> Tipos de datos de fecha y hora: `datetime`, `smalldatetime`, `timestamp`, `date`, `time`, `datetime2` y `datetimeoffset`<br />Nota: Para una columna que tiene un tipo de datos de fecha y hora, el perfil calcula solo los valores mínimo y máximo.|  
|Todos los valores distintos existentes en la columna seleccionada y el porcentaje de filas de la tabla que representa cada valor. O bien, los valores de la tabla cuya frecuencia es superior a un cierto porcentaje.|**Un número incorrecto de valores distintos en una columna**, por ejemplo, generar un perfil de una columna que contiene Estados en el Estados Unidos, pero detectar más de 50 valores distintos.|**Distribución de valores de columna-** Válido para una columna con uno de estos tipos de datos:<br /><br /> Tipos de datos numéricos: tipos enteros (excepto `bit`), `money`, `smallmoney`, `decimal`, `float`, `real` y `numeric`<br /><br /> Tipos de datos de caracteres: `char`, `nchar`, `varchar` y `nvarchar`<br /><br /> Tipos de datos de fecha y hora: `datetime`, `smalldatetime`, `timestamp`, `date`, `time`, `datetime2` y `datetimeoffset`|  
|Si una columna o un conjunto de columnas es una clave, o una clave aproximada, para la tabla seleccionada.|**Valores duplicados en una columna de clave potencial:** Por ejemplo, puede generar el perfil de las columnas de nombre y dirección en una tabla Customers y detectar valores duplicados donde las combinaciones de nombre y dirección deben ser únicas.|**Clave candidata:** Un perfil de varias columnas que notifica si una columna o un conjunto de columnas es adecuado para actuar como clave para la tabla seleccionada. Válido para las columnas con uno de estos tipos de datos:<br /><br /> Tipos de datos enteros: `bit`, `tinyint`, `smallint`, `int` y `bigint`<br /><br /> Tipos de datos de caracteres: `char`, `nchar`, `varchar` y `nvarchar`<br /><br /> Tipos de datos de fecha y hora: `datetime`, `smalldatetime`, `timestamp`, `date`, `time`, `datetime2` y `datetimeoffset`|  
|Hasta qué punto los valores de una columna (la columna dependiente) dependen de los valores de otra columna o de un conjunto de columnas (la columna determinante).|**Valores que no son válidos en columnas dependientes:** Por ejemplo, puede generar un perfil de la dependencia entre una columna que contiene Estados Unidos códigos postales y una columna que contiene Estados en el Estados Unidos. El mismo código postal siempre debería corresponder al mismo estado. Sin embargo, el perfil detecta infracciones de la dependencia.|**Dependencia funcional:** Válido para columnas con uno de estos tipos de datos:<br /><br /> Tipos de datos enteros: `bit`, `tinyint`, `smallint`, `int` y `bigint`<br /><br /> Tipos de datos de caracteres: `char`, `nchar`, `varchar` y `nvarchar`<br /><br /> Tipos de datos de fecha y hora: `datetime`, `smalldatetime`, `timestamp`, `date`, `time`, `datetime2` y `datetimeoffset`|  
|Si una columna o un conjunto de columnas es adecuado para actuar como clave externa entre las tablas seleccionadas.<br /><br /> Es decir, este perfil notifica la superposición de valores entre dos columnas o conjuntos de columnas.|**Valores que no son válidos:** Por ejemplo, puede generar el perfil de la columna ProductID de una tabla de ventas. El perfil detecta que la columna contiene valores que no están en la columna IdProducto de la tabla Productos.|**Inclusión de valores:** Válido para columnas con uno de estos tipos de datos:<br /><br /> Tipos de datos enteros: `bit`, `tinyint`, `smallint`, `int` y `bigint`<br /><br /> Tipo de datos de caracteres: `char` , `nchar` , `varchar` y`nvarchar`<br /><br /> Tipos de datos de fecha y hora: `datetime`, `smalldatetime`, `timestamp`, `date`, `time`, `datetime2` y `datetimeoffset`|  
  
 Para seleccionar los perfiles que hay que calcular, se utiliza la página **Solicitudes de perfil** del Editor de tareas de generación de perfiles de datos. Para obtener más información, vea [Editor de tareas de generación de perfiles de datos &#40;página Solicitudes de perfil&#41;](data-profiling-task-editor-profile-requests-page.md).  
  
 En la página **Solicitudes de perfil** , también se especifica el origen de datos y se configuran los perfiles de datos. Al configurar la tarea, tenga en cuenta la información siguiente:  
  
-   Para simplificar la configuración y facilitar la detección de características de datos desconocidos, puede utilizar el carácter comodín **( \* )** en lugar de un nombre de columna individual. Si utiliza este carácter comodín, la tarea generará perfiles en cada columna que tengan tipo de datos adecuado, lo que, a su vez, puede reducir la velocidad del procesamiento.  
  
-   Cuando la tabla o la vista seleccionadas estén vacías, la tarea de generación de perfiles de datos no calculará ningún perfil.  
  
-   Cuando todos los valores de la columna seleccionada sean NULL, la tarea de generación de perfiles de datos solo calculará el Perfil de proporción de columnas nulas. No calculará el Perfil de distribución de longitud de columnas, el Perfil de patrón de columnas, el Perfil de estadísticas de columnas ni el Perfil de distribución de valores de columna para la columna vacía.  
  
 Cada uno de los perfiles de datos disponibles tiene sus propias opciones de configuración. Para obtener más información acerca de dichas opciones, vea los temas siguientes:  
  
-   [Opciones de Solicitud de perfil de claves candidatas &#40;tarea de generación de perfiles de datos&#41;](candidate-key-profile-request-options-data-profiling-task.md)  
  
-   [Opciones de Solicitud de perfil de distribución de longitud de columna &#40;tarea de generación de perfiles de datos&#41;](column-length-distribution-profile-request-options-data-profiling-task.md)  
  
-   [Opciones de Solicitud de perfil de proporción de columnas nulas &#40;tarea de generación de perfiles de datos&#41;](column-null-ratio-profile-request-options-data-profiling-task.md)  
  
-   [Opciones de Solicitud de perfil de patrón de columnas &#40;tarea de generación de perfiles de datos&#41;](column-pattern-profile-request-options-data-profiling-task.md)  
  
-   [Opciones de Solicitud de perfil de estadísticas de columnas &#40;tarea de generación de perfiles de datos&#41;](column-statistics-profile-request-options-data-profiling-task.md)  
  
-   [Opciones de Solicitud de perfil de distribución de valores de columna &#40;tarea de generación de perfiles de datos&#41;](column-value-distribution-profile-request-options-data-profiling-task.md)  
  
-   [Opciones de Solicitud de perfil de dependencia funcional &#40;tarea de generación de perfiles de datos&#41;](functional-dependency-profile-request-options-data-profiling-task.md)  
  
-   [Opciones de Solicitud de perfil de inclusión de valores &#40;tarea de generación de perfiles de datos&#41;](value-inclusion-profile-request-options-data-profiling-task.md)  
  
## <a name="execution-of-the-package-that-contains-the-data-profiling-task"></a>Ejecución del paquete que contiene la tarea de generación de perfiles de datos  
 Después de configurar la tarea de generación de perfiles de datos, puede ejecutarla. A continuación, la tarea calcula los perfiles de datos y genera esta información en formato XML en un archivo o en una variable de paquete. La estructura de este XML sigue el esquema DataProfile.xsd. Puede abrir el esquema en [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] u otro editor de esquemas, en un editor XML o en un editor de texto como el Bloc de notas. Este esquema de información sobre la calidad de los datos puede se útil para los siguientes fines:  
  
-   Intercambiar información sobre la calidad de los datos dentro de las organizaciones y entre ellas.  
  
-   Generar herramientas personalizadas para trabajar con información sobre la calidad de los datos.  
  
 El espacio de nombres de destino se identifica en el esquema como [https://schemas.microsoft.com/sqlserver/2008/DataDebugger/](https://schemas.microsoft.com/sqlserver/2008/DataDebugger/) .  
  
## <a name="next-step"></a>siguiente paso  
 [Visor de Perfil de datos](data-profile-viewer.md).  
  
  
