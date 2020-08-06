---
title: Agregar inteligencia de dimensiones a una dimensión | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Business Intelligence enhancements [Analysis Services], dimension intelligence
- dimensions [Analysis Services], Business Intelligence enhancements
- dimension intelligence [Analysis Services]
- Type property
ms.assetid: b64fa386-eac2-4286-a320-0631a1887aac
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5cad591d3e89dc306571efa9aeef9d81a235c9fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87670657"
---
# <a name="add-dimension-intelligence-to-a-dimension"></a>Agregar inteligencia de dimensiones a una dimensión
  Agregar la mejora de inteligencia de dimensiones a un cubo o dimensión para especificar un tipo de negocio estándar para una dimensión. Esta mejora también especifica los tipos correspondientes para los atributos de dimensión. Las aplicaciones cliente pueden utilizar estas especificaciones de tipos al analizar datos.  
  
 Para agregar la inteligencia de dimensiones, use el Asistente de Business Intelligence y seleccione la opción **Definir la inteligencia de dimensiones** en la página **Elegir mejora** . A continuación, este asistente le guía por los pasos de la selección de una dimensión a la que desee aplicar la inteligencia de dimensiones e identificar los atributos para la dimensión seleccionada.  
  
## <a name="selecting-a-dimension"></a>Seleccionar una dimensión  
 En la primera página del asistente, **Establecer las opciones de la inteligencia de dimensiones** , se especifica la dimensión a la que se desea aplicar la inteligencia de dimensiones. La mejora de inteligencia de dimensiones agregada a esta dimensión seleccionada produce cambios en la dimensión. Estos cambios son heredados por todos los cubos que incluyan la dimensión seleccionada.  
  
> [!NOTE]  
>  Si se selecciona **Cuenta** como la dimensión, se especifica la inteligencia de cuenta para la dimensión. Para obtener más información, vea [Agregar inteligencia de cuentas a una dimensión](bi-wizard-add-account-intelligence-to-a-dimension.md).  
  
## <a name="specifying-dimension-attributes"></a>Especificar atributos de dimensión  
 En la página **definir la inteligencia de dimensiones** , en la lista tipo de **dimensión** , la selección realizada establece la propiedad de la dimensión `Type` . La configuración de la propiedad `Type` proporciona información a los servidores y aplicaciones cliente sobre el contenido de una dimensión. Algunas configuraciones solo proporcionan instrucciones para aplicaciones cliente; estas configuraciones son opcionales. Otras configuraciones, como Cuentas o Tiempo, determinan comportamientos específicos y pueden ser necesarias para implementar mejoras específicas de inteligencia empresarial. Por ejemplo, SQL Server Management Studio usa el tipo de dimensión para identificar una dimensión de Moneda y establecer las normas pertinentes de conversión de moneda. La configuración predeterminada para **Tipo de dimensión** es **Normal**, que no hace suposiciones sobre el contenido de la dimensión.  
  
 Después de seleccionar el tipo de dimensión en **Atributos de dimensión**, en la columna **Incluir** , active la casilla situada junto a cada tipo de atributo estándar para el que haya un atributo correspondiente en la dimensión. Finalmente, en la columna **Atributo de dimensión** , expanda la lista desplegable y seleccione el atributo en la dimensión que corresponde al tipo de atributo seleccionado. Seleccionar el atributo de la lista establece la propiedad `Type` del atributo para los atributos.  
  
 Por ejemplo, desea agregar inteligencia de dimensiones a una dimensión Cuentas. En **Tipo de dimensión**, seleccione **Cuentas**. Entonces, si la dimensión tiene los atributos **Tipo de cuenta** y **Descripción de cuenta** , en la columna **Incluir** , active las casillas para los tipos de cuenta **Nombre de cuenta** y **Tipo de cuenta** . A continuación, en la columna **Atributo de dimensión** , asocie estos tipos de cuenta con los atributos **Descripción de cuenta** y **Tipo de cuenta** , respectivamente, en la dimensión.  
  
## <a name="see-also"></a>Consulte también  
 [Definir cálculos de inteligencia de tiempo mediante el Asistente de Business Intelligence](define-time-intelligence-calculations-using-the-business-intelligence-wizard.md)  
  
  
