---
title: Formulario de perfil rápido de tabla única (tarea de generación de perfiles de datos) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataprofilingtask.quickprofile.f1
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: d2fac9ce-730e-474e-961a-69406b633778
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3d7793097a73eeda66d6ec48e183c550ca8e78ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676120"
---
# <a name="single-table-quick-profile-form-data-profiling-task"></a>Formulario de perfil rápido de tabla única (tarea de generación de perfiles de datos)
  Utilice el **Formulario de perfil rápido de tabla única** para configurar rápidamente la tarea de generación de perfiles de datos de una sola tabla o vista utilizando la configuración predeterminada.  
  
 Para más información sobre cómo usar la tarea de generación de perfiles de datos, vea [Configuración de la Tarea de generación de perfiles de datos](data-profiling-task.md). Para más información sobre cómo usar el Visor de perfil de datos para analizar la salida de la tarea de generación de perfiles de datos, vea [Visor de perfil de datos](data-profile-viewer.md).  
  
## <a name="options"></a>Opciones  
 **Connection**  
 Seleccione un administrador de conexiones de [!INCLUDE[vstecado](../../includes/vstecado-md.md)] existente que use el Proveedor de datos .NET para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) para conectarse a la base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que contiene la tabla o la vista que se usará para generar el perfil.  
  
 **Tabla o vista**  
 Seleccione una tabla o vista en la base de datos a la que se conecta el administrador de conexiones seleccionado.  
  
 **Proceso**  
 Seleccione qué perfiles hay que calcular.  
  
|Value|Descripción|  
|-----------|-----------------|  
|**Perfil de proporción de columnas nulas**|Calcule un perfil de proporción de columnas nulas con la configuración predeterminada para todas las columnas aplicables en la tabla o vista seleccionadas.<br /><br /> Este perfil notifica el porcentaje de valores nulos en la columna seleccionada. Este perfil puede ayudarle a identificar problemas en los datos, por ejemplo una proporción inesperadamente alta de valores nulos en una columna. Para más información sobre la configuración de este perfil, vea [Opciones de Solicitud de perfil de proporción de columnas nulas &#40;tarea de generación de perfiles de datos&#41;](column-null-ratio-profile-request-options-data-profiling-task.md).|  
|**Perfil de estadísticas de columnas**|Calcule un perfil de estadísticas de columnas con la configuración predeterminada para todas las columnas aplicables en la tabla o vista seleccionadas.<br /><br /> Este perfil notifica estadísticas, como los valores mínimo, máximo y promedio, y la desviación estándar para las columnas numéricas, y los valores mínimo y máximo para las columnas `datetime`. Este perfil puede ayudarle a identificar problemas de los datos, por ejemplo fechas que no sean válidas. Para más información sobre la configuración de este perfil, vea [Opciones de Solicitud de perfil de estadísticas de columnas &#40;tarea de generación de perfiles de datos&#41;](column-statistics-profile-request-options-data-profiling-task.md).|  
|**Perfil de distribución de valores de columna**|Calcule un perfil de distribución de valores de columna con la configuración predeterminada para todas las columnas aplicables en la tabla o vista seleccionadas.<br /><br /> Este perfil notifica todos los valores distintos existentes en la columna seleccionada y el porcentaje de filas de la tabla que representa cada valor. Este perfil también puede notificar los valores que representan más de un porcentaje especificado de filas en la tabla. Este perfil puede ayudarle a identificar problemas en los datos, por ejemplo un número incorrecto de valores distintos en una columna. Para más información sobre este perfil, vea [Opciones de Solicitud de perfil de distribución de valores de columna &#40;tarea de generación de perfiles de datos&#41;](column-value-distribution-profile-request-options-data-profiling-task.md).|  
|**Perfil de distribución de longitud de columnas**|Calcule un perfil de distribución de longitud de columnas con la configuración predeterminada para todas las columnas aplicables en la tabla o vista seleccionadas.<br /><br /> Este perfil notifica las diferentes longitudes de los valores de cadena de la columna seleccionada y el porcentaje de filas de la tabla que cada longitud representa. Este perfil puede ayudarle a identificar los problemas de los datos, por ejemplo valores que no sean válidos. Para más información sobre la configuración de este perfil, vea [Opciones de Solicitud de perfil de distribución de longitud de columnas &#40;tarea de generación de perfiles de datos&#41;](column-length-distribution-profile-request-options-data-profiling-task.md).|  
|**Perfil de patrón de columnas**|Calcule un perfil de patrón de columnas con la configuración predeterminada para todas las columnas aplicables en la tabla o vista seleccionadas.<br /><br /> Este perfil notifica un conjunto de expresiones regulares que abarcan los valores en una columna de cadena. Este perfil puede ayudarle a identificar problemas de los datos, por ejemplo cadenas que no sean válidas. Este perfil también puede sugerir expresiones regulares que se pueden usar en el futuro para validar los valores nuevos. Para más información sobre la configuración de este perfil, vea [Opciones de Solicitud de perfil de patrón de columnas &#40;tarea de generación de perfiles de datos&#41;](column-pattern-profile-request-options-data-profiling-task.md).|  
|**Perfil de claves candidatas**|Calcule un perfil de claves candidatas para las combinaciones de columnas que incluyen hasta el número de columnas que se especifica en **para un máximo de N claves de columna**.<br /><br /> Este perfil notifica si una columna o conjunto de columnas es adecuado para actuar como una clave para la tabla seleccionada. Este perfil también puede ayudarle a identificar problemas de los datos, por ejemplo valores en una posible columna de clave. Para más información sobre la configuración de este perfil, vea [Opciones de Solicitud de perfil de claves candidatas &#40;tarea de generación de perfiles de datos&#41;](candidate-key-profile-request-options-data-profiling-task.md).|  
|**para un máximo de N claves de columna**|Seleccione el número máximo de columnas que probar en posibles combinaciones como clave para la tabla o vista. El valor predeterminado es 1. El valor máximo es 1000. Por ejemplo, si se selecciona 3, se prueban combinaciones de claves de una columna, dos columnas y tres columnas.|  
|**Perfil de dependencia funcional**|Calcule un perfil de dependencia funcional para las combinaciones de columnas determinantes que incluyen hasta el número de columnas que se especifica en **para un máximo de N columnas como determinante**.<br /><br /> Este perfil notifica hasta qué punto los valores de una columna (la columna dependiente) dependen de los valores de otra columna o de un conjunto de columnas (la columna determinante). Este perfil puede ayudarle también a identificar problemas de los datos, por ejemplo valores que no sean válidos. Para más información sobre la configuración de este perfil, vea [Opciones de Solicitud de perfil de dependencia funcional &#40;tarea de generación de perfiles de datos&#41;](functional-dependency-profile-request-options-data-profiling-task.md).|  
|**para un máximo de N columnas como determinante**|Seleccione el número máximo de columnas para probar en posibles combinaciones como las columnas determinantes. El valor predeterminado es 1. El valor máximo es 1000. Al seleccionar 2, por ejemplo, se prueban combinaciones en las que las columnas determinantes de otra columna (dependiente) son las combinaciones de dos columnas o de columnas únicas.|  
  
> [!NOTE]  
>  El tipo Perfil de inclusión de valores no está disponible en el **Formulario de perfil rápido de tabla única**.  
  
## <a name="see-also"></a>Consulte también  
 [Editor de tareas de generación de perfiles de datos &#40;página General&#41;](../general-page-of-integration-services-designers-options.md)   
 [Editor de tareas de generación de perfiles de datos &#40;página Solicitudes de perfil&#41;](data-profiling-task-editor-profile-requests-page.md)  
  
  
