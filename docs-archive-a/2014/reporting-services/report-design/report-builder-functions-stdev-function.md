---
title: Función StDev (Generador de informes y SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: cb51e96e-a828-42f0-b67c-cee3f4d221e7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 58f913501c708b10ca01c24dd591d3378584afa5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672689"
---
# <a name="stdev-function-report-builder-and-ssrs"></a>Función StDev (Generador de informes y SSRS)
  Devuelve la desviación estándar de todos los valores numéricos no NULL especificados por la expresión, que se evalúa en el contexto del ámbito especificado.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
StDev(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *expression*  
 (`Integer` o `Float`). Expresión en la que se lleva a cabo la agregación.  
  
 *scope*  
 (`String`) (opcional). Nombre de un conjunto de datos, un grupo o una región de datos que contiene los elementos de informe a los que se va a aplicar la función de agregado. Si no se especifica el parámetro *scope* , se usa el ámbito actual.  
  
 *recursive*  
 (**Tipo enumerado**) Opcional. `Simple` (predeterminado) o `RdlRecursive`. Especifica si se debe realizar la agregación de forma recursiva.  
  
## <a name="return-type"></a>Tipo de valor devuelto  
 Devuelve un valor `Decimal` para expresiones decimales y un valor `Double` para las demás expresiones.  
  
## <a name="remarks"></a>Observaciones  
 El conjunto de datos especificado en la expresión debe tener el mismo tipo de datos. Si desea convertir datos de varios tipos de datos numéricos al mismo tipo de datos, use funciones de conversión como `CInt`, `CDbl` o `CDec`. Para obtener más información, vea [Funciones de conversión de tipos](https://go.microsoft.com/fwlink/?LinkId=96142).  
  
 El valor de *scope* debe ser una constante de cadena y no puede ser una expresión. Para los agregados exteriores o los que no especifican a otros agregados, *scope* debe hacer referencia al ámbito actual o a un ámbito de contenido. Para los agregados de agregados, los agregados anidados pueden especificar un ámbito secundario.  
  
 *Expression* puede contener las llamadas a las funciones de agregados anidados con las siguientes excepciones y condiciones:  
  
-   *Scope* , para los agregados anidados, debe ser igual que el ámbito del agregado exterior, o ser contenido por él. Para todos los ámbitos distintos de la expresión, un ámbito debe estar en una relación secundaria con respecto a todos los otros ámbitos.  
  
-   *Scope* , para los agregados anidados, no puede ser el nombre de un conjunto de datos.  
  
-   *Expression* no debe contener `First` `Last` `Previous` las funciones,, o `RunningValue` .  
  
-   *Expression* no debe contener a los agregados anidados que especifican *recursive*.  
  
 Para más información, vea [Funciones del generador de informes - referencia de funciones de agregado &#40;Generador de informes y SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) y [Ámbito de expresión para los totales, agregados y colecciones integradas &#40;Generador de informes y SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Para más información sobre los agregados recursivos, vea [Crear un grupo de jerarquía recursiva &#40;Generador de informes y SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo de código devuelve la desviación estándar de los totales para cada artículo del grupo o de la región de datos `Order` .  
  
```  
=StDev(Fields!LineTotal.Value, "Order")  
```  
  
## <a name="see-also"></a>Consulte también  
 [Usar expresiones en informes &#40;Generador de informes y SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Ejemplos de expresiones &#40;Generador de informes y SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Tipos de datos en expresiones &#40;Generador de informes y SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Ámbito de expresión para los totales, agregados y colecciones integradas &#40;Generador de informes y SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
