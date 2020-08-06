---
title: Definir la ordenación de una dimensión | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- OrderBy property
- dimensions [Analysis Services], ordering
- Business Intelligence enhancements [Analysis Services], ordering
- dimensions [Analysis Services], Business Intelligence enhancements
- ordering dimensions [Analysis Services]
- OrderByAttributeID property
ms.assetid: c42fbd58-244d-4e0a-b715-6f919cbc3ad9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8cd5ea148e374c18c530ba0a15c80dbb23983020
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87670658"
---
# <a name="define-the-ordering-for-a-dimension"></a>Definir la ordenación en una dimensión
  Agregar la mejora de orden de los atributos a un cubo o una dimensión para especificar de qué manera se ordenan los miembros de un atributo. Los miembros pueden ordenarse por el nombre o la clave del atributo, o bien por el nombre o la clave de otro atributo (en función de la relación de atributo). De forma predeterminada, los miembros se ordenan por nombre. Esta mejora cambia la configuración de las propiedades `OrderBy` y `OrderByAttributeID` de los atributos para una dimensión.  
  
 Para agregar el orden de atributos, se usa el Asistente de Business Intelligence y se selecciona la opción **Especificar el orden de los atributos** en la página **Elegir mejora** . A continuación, este asistente le guía por los pasos para seleccionar una dimensión a la que desee aplicar el orden de los atributos y especificar cómo se deben ordenar los atributos para la dimensión seleccionada.  
  
## <a name="selecting-a-dimension"></a>Seleccionar una dimensión  
 En la primera página **Especificar el orden de los atributos** del asistente, se especifica la dimensión a la que se desea aplicar el orden de los atributos. La mejora de orden de los atributos agregada a esta dimensión seleccionada produce cambios en la dimensión. Estos cambios son heredados por todos los cubos que incluyan la dimensión seleccionada.  
  
## <a name="specifying-ordering"></a>Especificar el orden  
 En la segunda página **Especificar el orden de los atributos** del asistente, se especifica de qué manera se ordenan todos los atributos de la dimensión.  
  
 En la columna **Atributo de orden** , se puede cambiar el atributo utilizado para aplicar el orden. Si el atributo que desea usar para ordenar los miembros no se encuentra en la lista, desplácese hacia abajo en la lista y, a continuación, seleccione **\<New attribute...>** para abrir el cuadro de diálogo **seleccionar una columna** , donde puede seleccionar una columna de una tabla de dimensiones. Al seleccionar una columna mediante el cuadro de diálogo **Seleccionar una columna** se crea un atributo adicional con el que se ordenan los miembros de un atributo.  
  
 En la columna **Criterios** , puede seleccionar si ordena los miembros del atributo por **Clave** o **Nombre**.  
  
  
