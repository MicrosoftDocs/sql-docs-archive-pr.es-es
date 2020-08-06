---
title: Propiedades del conjunto de propiedades (cuadro de diálogo), opciones | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10130"
- sql12.rtp.rptdesigner.datasetproperties.options.f1
ms.assetid: 95299049-71ba-427f-b723-775cb696243f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 778365e8fc7f40700b0f8c1683260f15c860a32a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87677443"
---
# <a name="dataset-properties-dialog-box-options"></a>Propiedades del conjunto de datos (cuadro de diálogo), Opciones
  Seleccione **Opciones** en el cuadro de diálogo **propiedades** para cambiar las opciones de datos, como las opciones de intercalación y los subtotales, de la consulta. Para más información, consulte [Compatibilidad con la intercalación y Unicode](../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="options"></a>Opciones  
 **Intercalación**  
 Seleccione una configuración regional que determine la secuencia de intercalación que se va a utilizar para ordenar los datos. **Predeterminado** indica que el servidor de informes debería intentar obtener el valor del proveedor de datos al ejecutar el informe. Si no se puede obtener, el valor predeterminado se deriva de la configuración regional del equipo.  
  
 **Distinción de mayúsculas y minúsculas**  
 Seleccione un valor que determine la distinción de mayúsculas y minúsculas. Esta opción indica si en los datos se hace esta distinción. Puede establecer la **distinción de mayúsculas y minúsculas** en **true**, **false**o **auto**. El valor predeterminado, **auto**, indica que el servidor de informes debería intentar obtener el valor del proveedor de datos cuando se ejecuta el informe. Si el proveedor de datos no admite el tipo de distinción de mayúsculas y minúsculas, el informe se ejecuta como si el valor fuera **False**. Si conoce el valor y sabe que el proveedor lo admite, elija **True**.  
  
 **Distinción de acentos**  
 Seleccione un valor que determine la distinción de acentos. La **distinción de acentos** indica si los datos distinguen acentos y se pueden establecer en **true**, **false**o **auto**. El valor predeterminado, **auto**, indica que el servidor de informes debería intentar obtener el valor del proveedor de datos al ejecutar el informe. Si el proveedor de datos no admite el tipo de distinción de acentos, el informe se ejecuta como si el valor fuera **False**. Si conoce el valor y sabe que el proveedor lo admite, elija **True**.  
  
 **Distinción de tipos de kana**  
 Seleccione un valor que determine la distinción de tipos de kana. Esta opción indica si los datos distinguen Kana; se puede establecer en **true**, **false**o **auto**. El valor predeterminado, **auto**, indica que el servidor de informes debería intentar obtener el valor del proveedor de datos cuando se ejecuta el informe. Si el proveedor de datos no admite el tipo de distinción de tipos de kana, el informe se ejecuta como si el valor fuera **False**. Si conoce el valor y sabe que el proveedor lo admite, elija **True**.  
  
 **Distinción de ancho**  
 Seleccione un valor que determine la distinción de ancho. Esta opción indica si los datos distinguen el ancho y se pueden establecer en **true**, **false**o **auto**. El valor predeterminado, **auto**, indica que el servidor de informes debería intentar obtener el valor del proveedor de datos cuando se ejecuta el informe. Si el proveedor de datos no admite el tipo de distinción de ancho, el informe se ejecuta como si el valor fuera **False**. Si conoce el valor y sabe que el proveedor lo admite, elija **True**.  
  
 **Interpretar los subtotales como filas de detalles**  
 Seleccione un valor que indique si desea que las filas de subtotales se interpreten como filas de detalles en lugar de como filas agregadas. El valor predeterminado, **auto**, indica que las filas de subtotales se deben tratar como filas de detalles si el informe no usa la `Aggregate` función () para tener acceso a los campos del conjunto de datos. Si desea que las filas de subtotales se interpreten como filas agregadas, elija **False**. Si desea que las filas de subtotales se interpreten como filas de detalles y sabe que no usan la `Aggregate` función (), elija **true**.  
  
## <a name="see-also"></a>Consulte también  
 [Establecer la configuración regional de un informe o un cuadro de texto &#40;Reporting Services&#41;](report-design/set-the-locale-for-a-report-or-text-box-reporting-services.md)   
 [Agregar datos a un informe &#40;Generador de informes y SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Nombre de intercalación de Windows &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql)   
 [Nombre de intercalación de SQL Server &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql)   
 [Función de agregado &#40;Generador de informes y SSRS&#41;](report-design/report-builder-functions-aggregate-function.md)  
  
  
