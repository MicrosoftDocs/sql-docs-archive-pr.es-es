---
title: Transformación Muestreo de porcentaje | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.percentagesamplingtrans.f1
helpviewer_keywords:
- testing mining models
- sampling seeds [Integration Services]
- data mining [Analysis Services], sample data sets
- Percentage Sampling transformation
- sample data sets [Integration Services]
- datasets [Integration Services], sample
- training mining models
ms.assetid: 59767e52-f732-4b3f-8602-be50d0a64ef2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e5fe41ecf4a2ca0f9d20eec2c8e10af8ed4cd47b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87752321"
---
# <a name="percentage-sampling-transformation"></a>Muestreo de porcentaje, transformación
  La transformación Muestreo de porcentaje crea un conjunto de datos de muestra seleccionando un porcentaje de las filas de entrada de transformación. El conjunto de datos de muestra es una selección aleatoria de filas de la entrada de transformación, de forma que la muestra resultante sea representativa de la entrada.  
  
> [!NOTE]  
>  Además del porcentaje especificado, la transformación Muestreo de porcentaje utiliza un algoritmo para determinar si se debe incluir una fila en la salida de ejemplo. Esto significa que el número de filas de la salida de ejemplo podría no reflejar exactamente el porcentaje especificado. Por ejemplo, si especifica 10% para un conjunto de datos de entrada que tiene 25.000 filas, no se generará una muestra con exactamente 2.500 filas; la muestra puede tener unas pocas filas más o menos.  
  
 La transformación Muestreo de porcentaje es especialmente útil para la minería de datos. Utilizando esta transformación, puede dividir de forma aleatoria un conjunto de datos en dos conjuntos de datos: uno para el entrenamiento del modelo de minería de datos y otro para probar el modelo.  
  
 La transformación Muestreo de porcentaje también es útil para crear conjuntos de datos de ejemplo de desarrollo de paquetes. Si aplica la transformación Muestreo de porcentaje a un flujo de datos, puede reducir uniformemente el tamaño de los conjuntos de datos conservando sus características. El paquete de prueba podrá ejecutarse más rápido porque utilizará un conjunto de datos pequeño, pero representativo.  
  
## <a name="configuration-the-percentage-sampling-transformation"></a>Configuración de la transformación Muestreo de porcentaje  
 Puede especificar un valor de inicialización de muestreo para modificar el comportamiento del generador de números aleatorios utilizado por la transformación para seleccionar filas. Si se usa el mismo valor de inicialización de muestreo, la transformación siempre creará la misma salida de ejemplo. Si no se especifica un valor de inicialización, la transformación utilizará el contador del sistema operativo para crear el número aleatorio. Por tanto, puede elegir usar un valor de inicialización estándar cuando desee comprobar los resultados de la transformación durante el desarrollo y las pruebas de un paquete, y después usar un valor de inicialización aleatorio cuando el paquete pase a producción.  
  
 Esta transformación es similar a la transformación Muestreo de fila, que crea a conjunto de datos de ejemplo seleccionando un número especificado de filas de entrada. Para más información, consulte [Row Sampling Transformation](row-sampling-transformation.md).  
  
 La transformación Muestreo de porcentaje incluye la propiedad personalizada `SamplingValue`. Esta propiedad se puede actualizar a través de una expresión de propiedad, al cargar el paquete. Para más información, vea [Expresiones de Integration Services &#40;SSIS&#41;](../../expressions/integration-services-ssis-expressions.md), [Usar expresiones de propiedad en paquetes](../../expressions/use-property-expressions-in-packages.md) y [Propiedades personalizadas de transformación](transformation-custom-properties.md).  
  
 La transformación tiene una entrada y dos salidas. No admite una salida de error.  
  
 Puede establecer propiedades a través del Diseñador de [!INCLUDE[ssIS](../../../includes/ssis-md.md)] o mediante programación.  
  
 Para obtener más información acerca de las propiedades que puede establecer en el cuadro de diálogo **Editor de transformación Muestreo de porcentaje** , vea [Percentage Sampling Transformation Editor](../../percentage-sampling-transformation-editor.md).  
  
 El cuadro de diálogo **Editor avanzado** indica las propiedades que se pueden establecer mediante programación. Para obtener más información acerca de las propiedades que puede establecer a través del cuadro de diálogo **Editor avanzado** o mediante programación, haga clic en uno de los temas siguientes:  
  
-   [Common Properties](../../common-properties.md)  
  
-   [Propiedades personalizadas de transformación](transformation-custom-properties.md)  
  
 Para más información sobre cómo establecer propiedades, vea [Establecer las propiedades de un componente de flujo de datos](../set-the-properties-of-a-data-flow-component.md).  
  
  
