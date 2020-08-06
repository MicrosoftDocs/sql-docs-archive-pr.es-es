---
title: Referencias a la colección de campos de conjunto de datos (Generador de informes y SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 006c6bd3-d776-4c20-9092-32e40688ac49
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9e4140c35f8035e3ac8fae37aefb9d7f2afcaecc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676373"
---
# <a name="dataset-fields-collection-references-report-builder-and-ssrs"></a>Referencias a la colección de campos de conjunto de datos (Generador de informes y SSRS)
  Cada conjunto de datos de un informe contiene una colección Fields. La colección Fields es el conjunto de campos especificados por la consulta de conjunto de datos, más los campos calculados adicionales que se hayan creado. Una vez creado el conjunto de datos, la colección de campos aparece en el panel **Datos de informe** .  
  
 Una referencia de campo sencilla en una expresión se muestra en la superficie de diseño como una expresión simple. Por ejemplo, al arrastrar el campo `Sales` desde el panel Datos de informe hasta una celda de tabla en la superficie de diseño, se muestra `[Sales]` . Esto representa la expresión subyacente `=Fields!Sales.Value` que se establece en la propiedad Value del cuadro de texto. Cuando se ejecuta el informe, el procesador de informes evalúa esta expresión y muestra los datos reales del origen de datos en el cuadro de texto de la celda de tabla. Para más información, vea [Expresiones &#40;Generador de informes y SSRS&#41;](expressions-report-builder-and-ssrs.md) y [Colección Campos del conjunto de datos &#40;Generador de informes y SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="displaying-the-field-collection-for-a-dataset"></a>Mostrar la colección de campos para un conjunto de datos  
 Para mostrar los valores individuales de una colección de campos, arrastre cada campo hasta una fila de detalles de tabla y ejecute el informe. Las referencias desde la fila de detalles de una tabla o región de datos de lista muestran un valor para cada fila del conjunto de datos.  
  
 Si desea mostrar los valores resumidos de un campo, arrastre cada campo numérico hasta el área de datos de una matriz. La función de agregado predeterminada para la fila de totales es Sum; por ejemplo, `=Sum(Fields!Sales.Value)`. Puede cambiar la función predeterminada para calcular totales diferentes. Para más información, vea [Referencia a las funciones de agregado &#40;Generador de informes y SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).  
  
 Para mostrar los valores resumidos de una colección de campos en un cuadro de texto directamente en la superficie de diseño (que no sea parte de una región de datos), debe especificar el nombre del conjunto de datos como ámbito para la función de agregado. Por ejemplo, para un conjunto de datos denominado `SalesData`, la expresión siguiente especifica el total de todos los valores para el campo `Sales`: `=Sum(Fields!Sales,"SalesData")`.  
  
 Al usar el cuadro de diálogo **Expresión** para definir una referencia de campo sencilla, puede seleccionar la colección Fields en el panel Categoría y ver la lista de campos disponibles en el panel **Campo** . Cada campo tiene varias propiedades, entre las que se incluyen Value e IsMissing. Las demás son propiedades de campo extendidas predefinidas que pueden estar disponibles para el conjunto de datos dependiendo del tipo de origen de datos.  
  
### <a name="detecting-nulls-for-a-dataset-field"></a>Detectar valores NULL en un campo de conjunto de datos  
 Para detectar un valor de campo NULL (`Nothing` en [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), puede usar la función `IsNothing`. Cuando se coloca en un cuadro de texto de una fila de detalles de tabla, la expresión siguiente comprueba el valor del campo `MiddleName` y lo sustituye por el texto "No Middle Name" cuando dicho valor es NULL, y por el propio valor de campo en caso contrario:  
  
 `=IIF(IsNothing(Fields!MiddleName.Value),"No Middle Name",Fields!MiddleName.Value)`  
  
### <a name="detecting-missing-fields-for-dynamic-queries-at-run-time"></a>Detectar campos inexistentes en las consultas dinámicas en tiempo de ejecución  
 De manera predeterminada, los elementos de la colección Fields tienen dos propiedades: Value e IsMissing. La propiedad IsMissing indica si un campo que se ha definido para un conjunto de datos en tiempo de diseño se encuentra entre los campos recuperados en tiempo de ejecución. Por ejemplo, la consulta podría llamar a un procedimiento almacenado en el que el conjunto de resultados varía con un parámetro de entrada, o la consulta podría ser `SELECT * FROM` *\<table>* donde la definición de tabla cambió.  
  
> [!NOTE]  
>  IsMissing detecta cambios en el esquema de conjunto de datos entre el tiempo de diseño y el de ejecución para cualquier tipo de origen de datos. IsMissing no se puede usar para detectar miembros vacíos en un cubo multidimensional y no está relacionado con los conceptos del lenguaje de consulta MDX de `EMPTY` y `NON EMPTY` .  
  
 Puede probar la propiedad IsMissing en código personalizado para determinar si un campo se encuentra en el conjunto de resultados. No puede comprobar su presencia usando una expresión con una llamada a una función de [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], como `IIF` o `SWITCH`, porque [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] evalúa todos los parámetros en la llamada a la función, lo que produce un error cuando se evalúa la referencia al campo que falta.  
  
#### <a name="example-for-controlling-the-visibility-of-a-dynamic-column-for-a-missing-field"></a>Ejemplo de control de la visibilidad de una columna dinámica para un campo que no existe  
 Para establecer una expresión que controle la visibilidad de una columna que muestra un campo de un conjunto de datos, primero debe definir una función de código personalizada que devuelva un valor booleano que indique si el campo existe o no. Por ejemplo, la función de código personalizada siguiente devuelve true si el campo no existe y false en caso contrario.  
  
```  
Public Function IsFieldMissing(field as Field) as Boolean  
 If (field.IsMissing) Then  
 Return True  
  Else   
  Return False  
 End If  
End Function  
```  
  
 Si quiere usar esta función para controlar la visibilidad de una columna, establezca la propiedad Hidden de la columna en la expresión siguiente:  
  
 `=Code.IsFieldMissing(Fields!FieldName)`  
  
 La columna se oculta si el campo no existe.  
  
#### <a name="example-for-controlling-the-text-box-value-for-a-missing-field"></a>Ejemplo de control del valor del cuadro de texto para un campo que no existe  
 Si desea sustituir el valor de un campo inexistente por un texto determinado, debe escribir código personalizado que devuelva el texto que puede usar en lugar del valor de campo cuando el campo no exista. Por ejemplo, la función de código personalizada siguiente devuelve el valor del campo si el campo existe, y el mensaje especificado como segundo parámetro en caso contrario:  
  
```  
Public Function IsFieldMissingThenString(field as Field, strMessage as String) as String  
 If (field.IsMissing) Then  
  Return strMessage  
 Else   
  Return field.Value  
  End If  
End Function  
```  
  
 Para usar esta función en un cuadro de texto, agregue la expresión siguiente a la propiedad Value:  
  
 `=Code.IsFieldMissingThenString(Fields!FieldName,"Missing")`  
  
 El cuadro de texto muestra el valor de campo o el texto especificado.  
  
### <a name="using-extended-field-properties"></a>Usar propiedades de campo extendidas  
 Las propiedades de campo extendidas son propiedades adicionales que la extensión de procesamiento de datos define en un campo, extensión que está determinada por el tipo de origen de datos del conjunto de datos. Las propiedades de campo extendidas pueden ser predefinidas o específicas de un tipo de origen de datos. Para obtener más información, vea [Propiedades de campo extendidas para una base de datos de Analysis Services &#40;SSRS&#41;](../report-data/extended-field-properties-for-an-analysis-services-database-ssrs.md).  
  
 Si especifica una propiedad no admitida para ese campo, la expresión se evalúa como `null` (`Nothing` en [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]). Si un proveedor de datos no admite propiedades de campo extendidas o si no se encuentra el campo al ejecutar la consulta, el valor de la propiedad será `null` (`Nothing` en [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]) para las propiedades de tipo `String` y `Object`, y cero (0) para las propiedades de tipo `Integer`. Una extensión de procesamiento de datos puede sacar partido de las propiedades predefinidas optimizando consultas que incluyan esta sintaxis.  
  
## <a name="see-also"></a>Consulte también  
 [Ejemplos de expresiones &#40;Generador de informes y SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Agregar datos a un informe &#40;Generador de informes y SSRS&#41;](../report-data/report-datasets-ssrs.md)  
  
  
