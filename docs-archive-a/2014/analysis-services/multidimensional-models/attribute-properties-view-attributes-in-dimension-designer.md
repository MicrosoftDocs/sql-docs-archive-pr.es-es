---
title: Ver atributos en el diseñador de dimensiones | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- displaying attributes
- attributes [Analysis Services], viewing
- viewing attributes
ms.assetid: 855bef07-b72d-4ce3-bf02-de77abeee71a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 22e837aa038cb30947632194d829a383afcf4a82
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746029"
---
# <a name="view-attributes-in-dimension-designer"></a>Ver atributos en el Diseñador de dimensiones
  Los atributos se crean en objetos de dimensión. Puede ver y configurar atributos mediante el diseñador de dimensiones en [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . El panel **Atributos** de la pestaña **Estructura de dimensión** del Diseñador de dimensiones contiene los atributos presentes en una dimensión. Use este panel para agregar, quitar o configurar atributos. También puede seleccionar atributos para usarlos como un nivel en una jerarquía nueva o para agregarlos como un nivel a una jerarquía existente.

 Para ver los atributos de una dimensión, abra el Diseñador de dimensiones para la dimensión. En el panel **Atributos** de la pestaña **Estructura de dimensión**  del diseñador se muestran los atributos presentes en la dimensión. Para cambiar entre una vista de lista, un árbol o una cuadrícula, seleccione **Mostrar atributos en** en el menú **dimensión** de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] y, a continuación, haga clic en uno de los comandos que se muestran en la tabla siguiente.

|Mostrar atributos en|Descripción|
|------------------------|-----------------|
|**Lista**|Muestra los atributos con formato de lista.<br /><br /> Haga clic con el botón secundario en un atributo para eliminarlo de la lista, para cambiar su nombre o para cambiar su uso.<br /><br /> Use esta vista para crear jerarquías. La información del atributo y las propiedades de miembro no están visibles.|
|**Palmera**|Muestra los atributos con formato de árbol, con la dimensión como nodo de nivel superior del árbol. Use esta vista para ver y crear propiedades de miembros. También puede utilizarla para generar jerarquías. Expanda un atributo para ver las relaciones de atributo correspondientes o para crear una nueva relación de atributo, efectuando las siguientes acciones:<br /><br /> Haga clic en la dimensión, un atributo o una propiedad del miembro para ver sus propiedades en la ventana **Propiedades** .<br /><br /> Haga clic con el botón secundario en un atributo o una propiedad del miembro para eliminarlo de la lista, para cambiar su nombre o para cambiar su uso.|
|**Grid**|Muestra los atributos con formato de cuadrícula. Haga clic en una fila de la cuadrícula para ver las propiedades correspondientes a ese atributo.  Use esta vista para crear y configurar atributos. La cuadrícula contiene las columnas siguientes:<br /><br /> **Nombre**: muestra el valor de la propiedad **nombre** . Escriba otro nombre para cambiar la configuración.<br /><br /> **Usage**: especifica si se trata de un atributo regular, Key, Parent o AccountType. Haga clic en un valor de la columna para seleccionar otra opción.<br /><br /> **Tipo**: especifica la categoría de Business Intelligence para el atributo. Haga clic en esta celda para seleccionar otra opción.<br /><br /> **Columna de clave**: muestra el tipo de datos OLE DB para la propiedad **KeyColumn** en el atributo. Esta columna no puede modificarse.<br /><br /> **Columna Nombre**: indica si el valor de la propiedad **NameColumn** en el atributo es la misma columna que el valor de la propiedad **KeyColumn** . Esta columna no puede modificarse.|

 En [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], los iconos que aparecen en la tabla siguiente marcan los atributos según su uso.

|Iconos|Uso del atributo|
|----------|---------------------|
|![Icono de atributo](../media/as-icon-attribute.gif "Icono de atributo")|Regular o AccountType|
|![Icono de atributo clave](../media/as-icon-key-attribute.gif "Icono de atributo clave")|Clave|
|![Icono de atributo primario](../media/as-icon-parent-attribute.gif "Icono de atributo primario")|Parent|

## <a name="see-also"></a>Consulte también
 [Referencia de las propiedades de los atributos de dimensión](dimension-attribute-properties-reference.md)


