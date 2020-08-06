---
title: Transformación Conversión de datos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataconversiontrans.f1
helpviewer_keywords:
- converting data types [Integration Services]
- Data Conversion transformation
- data types [Integration Services], converting
ms.assetid: fd515bbc-6f49-4d0c-ae7f-6ea3c3f24a1c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 57b1f70c070cdf81dc0bc899ed365d048db26cc9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663037"
---
# <a name="data-conversion-transformation"></a>Conversión de datos, transformación
  La transformación Conversión de datos convierte los datos de una columna de entrada a otro tipo de datos diferente y después los copia a una nueva columna de salida. Por ejemplo, un paquete puede extraer los datos de diferentes orígenes y después usar esta transformación para convertir las columnas al tipo de datos necesario para el almacén de datos de destino. Puede aplicar múltiples conversiones a una sola columna de entrada.  
  
 Un paquete puede utilizar esta transformación para realizar las siguientes conversiones de tipos de datos:  
  
-   Cambiar el tipo de datos. Para obtener más información, vea [Integration Services Data Types](../integration-services-data-types.md).  
  
    > [!NOTE]  
    >  Si va a convertir datos a un tipo de datos de fecha o de fecha y hora, la fecha de la columna de salida tiene el formato ISO, aunque las preferencias de la configuración regional especifiquen un formato diferente.  
  
-   Establecer la longitud de la columna de los datos de cadena así como la precisión y la escala de los datos numéricos. Para más información, vea [Precisión, escala y longitud &#40;Transact-SQL&#41;](/sql/t-sql/data-types/precision-scale-and-length-transact-sql).  
  
-   Especificar una página de códigos. Para más información, consulte [Comparing String Data](../comparing-string-data.md).  
  
    > [!NOTE]  
    >  Al copiar datos entre columnas con un tipo de datos de cadena, las dos columnas deben usar la misma página de códigos.  
  
 Si la longitud de una columna de salida de datos de tipo cadena es menor que la longitud de la columna de entrada correspondiente, se truncarán los datos de salida. Para más información, vea [Control de errores en los datos](../error-handling-in-data.md).  
  
 Esta transformación tiene una entrada, una salida y una salida de error.  
  
## <a name="related-tasks"></a>Related Tasks  
 Puede establecer propiedades a través del Diseñador [!INCLUDE[ssIS](../../../includes/ssis-md.md)] o mediante programación. Para más información sobre cómo usar la transformación Conversión de datos en el Diseñador SSIS, vea [Convertir datos en un tipo de datos diferente mediante la transformación Conversión de datos](data-conversion-transformation.md) y [Editor de transformación Conversión de datos](../../data-conversion-transformation-editor.md). Para más información sobre cómo establecer las propiedades de esta transformación mediante programación, vea [Propiedades comunes](../../common-properties.md) y [Propiedades personalizadas de transformación](transformation-custom-properties.md).  
  
## <a name="related-content"></a>Contenido relacionado  
 Entrada de blog, sobre la [comparación de rendimiento entre las técnicas de conversión de tipos de datos en SSIS 2008](https://techcommunity.microsoft.com/t5/datacat/performance-comparison-between-data-type-conversion-techniques/ba-p/305035), en blogs.msdn.com.  
  
## <a name="see-also"></a>Consulte también  
 [Análisis rápido](../../fast-parse.md)   
 [Flujo de datos](../data-flow.md)   
 [Transformaciones de Integration Services](integration-services-transformations.md)  
  
  
