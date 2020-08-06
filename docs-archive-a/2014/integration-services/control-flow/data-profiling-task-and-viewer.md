---
title: Visor y tarea de generación de perfiles de datos | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling task [Integration Services], about data profiling
- data profiling
- profiling data
ms.assetid: 756840e3-aa09-45cd-9951-1a17af4b5925
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ae15d1cc75f8db04c36a830e44d07800c5aecf75
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87671625"
---
# <a name="data-profiling-task-and-viewer"></a>Visor y tarea de generación de perfiles de datos
  La tarea de generación de perfiles de datos proporciona la funcionalidad para generar perfiles de datos dentro del proceso de extracción, transformación y carga de datos. El uso de esta tarea le permitirá:  
  
-   Analizar los datos de origen de forma más eficaz.  
  
-   Comprender mejor la estructura de los datos de origen.  
  
-   Evitar problemas de calidad en los datos antes de incluirlos en el almacenamiento de datos.  
  
> [!IMPORTANT]  
>  La tarea de generación de perfiles de datos solo funciona con datos que estén almacenados en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. No funciona con orígenes de datos de otros fabricantes o basados en archivos.  
  
## <a name="data-profiling-overview"></a>Información general de generación de perfiles de datos  
 La calidad de los datos es importante en todos los negocios. A medida que las empresas desarrollan sistemas analíticos y de inteligencia empresarial sobre sus sistemas transaccionales, la fiabilidad de los indicadores clave de rendimiento y de las predicciones de la minería de datos dependerán por completo de la validez de los datos en los que se basan. Pero aunque la importancia de disponer de datos válidos para la toma de decisiones empresariales está aumentando, también lo hace en la misma medida el desafío de garantizar la validez de los mismos. La información fluye de forma ininterrumpida en la empresa procedente de diversos sistemas y orígenes, y de un gran número de usuarios.  
  
 Las métricas para determinar la calidad de los datos pueden ser difíciles de definir porque son específicas del dominio o de la aplicación. Un método común para definir la calidad de los datos es la generación de perfiles de datos.  
  
 Un perfil de datos es una colección de estadísticas acumuladas sobre los datos que puede incluir la siguiente información:  
  
-   El número de filas de la tabla de clientes.  
  
-   El número de valores distintos en la columna Estado.  
  
-   El número de valores nulos o ausentes en la columna Código postal.  
  
-   La distribución de los valores en la columna Ciudad.  
  
-   La intensidad de la dependencia funcional entre la columna Estado y la columna Código postal; es decir, el estado siempre tendría que ser el mismo para un valor de código postal determinado.  
  
 Las estadísticas proporcionadas por un perfil de datos le ofrecen la información que necesita para minimizar de forma eficaz los problemas de calidad derivados del uso de los datos de origen.  
  
## <a name="integration-services-and-data-profiling"></a>Integration Services y generación de perfiles de datos  
 En [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], el proceso de generación de perfiles de datos consta de los pasos siguientes:  
  
 **Paso 1: Preparación de la tarea de generación de perfiles de datos**  
 La tarea de generación de perfiles de datos es una tarea que se utiliza para configurar los perfiles que se desean calcular. A continuación, se ejecuta el paquete que contiene la tarea de generación de perfiles de datos para calcular los perfiles. La tarea guarda el perfil generado en formato XML en un archivo o en una variable de paquete.  
  
 **Para obtener más información:** [Configuración de la tarea de generación de perfiles de datos](data-profiling-task.md)  
  
 **Paso 2: Revisión de los perfiles calculados por la tarea de generación de perfiles de datos**  
 Para ver los perfiles de datos calculados por la tarea de generación de perfiles de datos, se envía la salida a un archivo y, a continuación, se utiliza el Visor de perfil de datos. Este visor es una utilidad independiente que muestra el perfil generado tanto en formato resumen como en formato detallado, y que también permite la obtención de detalles.  
  
 **Para obtener más información:** [Visor de perfil de datos](data-profile-viewer.md)  
  
### <a name="addition-of-conditional-logic-to-the-data-profiling-workflow"></a>Inclusión de la lógica condicional al flujo de trabajo que genera perfiles de datos  
 La tarea de generación de perfiles de datos no tiene características integradas que le permitan utilizar lógica condicional para conectar esta tarea a las tareas de nivel inferior según el perfil generado. Sin embargo, puede agregar fácilmente esta lógica, con una pequeña cantidad de programación, en una tarea Script. Por ejemplo, la tarea Script puede realizar una consulta XPath en el archivo de salida de la tarea de generación de perfiles de datos. La consulta podría determinar si el porcentaje de valores nulos en una columna determinada supera un cierto umbral. Si el porcentaje supera el umbral, puede interrumpir el paquete y resolver el problema en los datos de origen antes de continuar. Para obtener más información, vea [Incorporar una tarea de generación de perfiles de datos en un flujo de trabajo de paquetes](incorporate-a-data-profiling-task-in-package-workflow.md).  
  
## <a name="related-content"></a>Contenido relacionado  
 [Esquema del generador de perfiles de datos](https://go.microsoft.com/fwlink/?LinkId=251524)  
  
  
