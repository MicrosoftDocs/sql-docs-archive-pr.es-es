---
title: Insertar, actualizar y quitar miembros (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- inserting dimension members
- XML for Analysis, members
- removing dimension members
- dropping dimension members
- write-enabled dimensions [Analysis Services]
- XMLA, members
- deleting dimension members
- dimensions [Analysis Services], XML for Analysis
ms.assetid: bba922b5-8b88-4051-9506-ff055248182a
author: minewiskan
ms.author: owend
ms.openlocfilehash: aef124abc8398f1b314a391291b52340a90689ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676223"
---
# <a name="inserting-updating-and-dropping-members-xmla"></a>Insertar, actualizar y quitar miembros (XMLA)
  Puede usar los comandos [Insert](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla), [Update](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)y [Drop](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla) en XML for Analysis (XMLA) para insertar, actualizar o eliminar los miembros de una dimensión habilitada para escritura, respectivamente. Para obtener más información acerca de las dimensiones habilitadas para escritura, consulte [dimensiones habilitadas para escritura](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md).  
  
## <a name="inserting-new-members"></a>Insertar nuevos miembros  
 El comando `Insert` inserta nuevos miembros en atributos especificados de una dimensión habilitada para escritura.  
  
 Antes de construir el comando `Insert`, debe tener disponible la siguiente información para los nuevos miembros que se van a insertar:  
  
-   La dimensión donde se van a insertar los nuevos miembros.  
  
-   El atributo de la dimensión donde se van a insertar los nuevos miembros.  
  
-   Los nombres de los nuevos miembros, incluida cualquier traducción aplicable del nombre.  
  
-   Las claves de los nuevos miembros. Si un atributo utiliza una clave compuesta, la clave puede requerir varios valores.  
  
-   Los valores de cualquier propiedad de atributo aplicable que no se implemente como otros atributos en la dimensión. Entre estas propiedades de atributo se incluyen operaciones unarias, traducciones, resúmenes personalizados, propiedades de resúmenes personalizados y niveles omitidos.  
  
 El comando `Insert` solamente acepta dos propiedades:  
  
-   La propiedad de [objeto](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) , que contiene una referencia de objeto para la dimensión en la que se van a insertar los miembros. La referencia de objeto contiene el identificador de la base de datos, el identificador del cubo y el identificador de dimensión para la dimensión.  
  
-   La propiedad [attributes](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/attributes-element-xmla) , que contiene uno o más elementos de [atributo](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/attribute-element-xmla) para identificar los atributos en los que se van a insertar los miembros. Cada elemento `Attribute` identifica un atributo y proporciona el nombre, el valor, las traducciones, el operador unario, el resumen personalizado, las propiedades de resúmenes personalizados y los niveles omitidos para un miembro único que se va a agregar al atributo identificado.  
  
    > [!NOTE]  
    >  Deben incluirse todas las propiedades del elemento `Attribute`. De lo contrario, puede producirse un error.  
  
## <a name="updating-existing-members"></a>Actualizar los miembros existentes  
 El comando `Update` actualiza los miembros existentes en atributos especificados, en función de las relaciones con otros miembros de otros atributos, en una dimensión habilitada para escritura. El comando `Update` puede mover los miembros a otros niveles de jerarquías incluidas en la dimensión y se puede utilizar para reestructurar las jerarquías de elementos primarios y secundarios definidas por atributos primarios.  
  
 Antes de construir el comando `Update`, debe tener disponible la siguiente información para los miembros que se van a actualizar:  
  
-   La dimensión donde se van a actualizar los miembros existentes.  
  
-   Los atributos de la dimensión donde se van a actualizar los miembros existentes.  
  
-   Las claves de los miembros existentes. Si un atributo utiliza una clave compuesta, la clave puede requerir varios valores.  
  
-   Los valores de cualquier propiedad de atributo aplicable que no se implemente como otros atributos en la dimensión. Entre estas propiedades de atributo se incluyen operaciones unarias, traducciones, resúmenes personalizados, propiedades de resúmenes personalizados y niveles omitidos.  
  
 El comando `Update` solamente acepta tres propiedades necesarias:  
  
-   La propiedad `Object`, que contiene una referencia de objeto para la dimensión donde se van a actualizar los miembros. La referencia de objeto contiene el identificador de la base de datos, el identificador del cubo y el identificador de dimensión para la dimensión.  
  
-   La propiedad `Attributes`, que contiene uno o más elementos `Attribute` para identificar los atributos donde se van a actualizar los miembros. El elemento `Attribute` identifica un atributo y proporciona el nombre, el valor, las traducciones, el operador unario, el resumen personalizado, las propiedades de resúmenes personalizados y los niveles omitidos para un miembro único actualizado para el atributo identificado.  
  
    > [!NOTE]  
    >  Deben incluirse todas las propiedades del elemento `Attribute`. De lo contrario, puede producirse un error.  
  
-   La propiedad [Where](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/where-element-xmla) , que contiene uno o más `Attribute` elementos que restringen los atributos en los que se van a actualizar los miembros. La `Where` propiedad es fundamental para limitar un `Update` comando a instancias específicas de un miembro. Si `Where` no se especifica la propiedad, se actualizan todas las instancias de un miembro determinado. Por ejemplo, hay tres clientes para los que desea cambiar el nombre de ciudad de Redmond a Bellevue. Para cambiar el nombre de la ciudad, debe proporcionar una propiedad `Where` que identifique a los tres miembros en el atributo Customer para el deben cambiarse los miembros en el atributo City. Si no proporciona esta propiedad `Where`, todos los clientes cuyo nombre de ciudad sea actualmente Redmond tendrán el nombre de ciudad Bellevue después de ejecutarse el comando `Update`.  
  
    > [!NOTE]  
    >  Con la excepción de los nuevos miembros, el comando `Update` solamente puede actualizar valores de clave de atributo para los atributos no incluidos en la cláusula `Where`. Por ejemplo, el nombre de ciudad no se puede actualizar cuando se actualiza un cliente; de lo contrario, dicho nombre se cambia para todos los clientes.  
  
### <a name="updating-members-in-parent-attributes"></a>Actualizar miembros de atributos primarios  
 Para admitir atributos primarios, el `Update` comando las propiedades [MoveWithDescendants](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/movewithdescendants-element-xmla)MovewithDescedants opcionales. Si se establece la propiedad `MoveWithDescendants` en true se indica que los descendientes del miembro primario deben moverse junto con éste cuando cambie el identificador de dicho miembro primario. Si este valor se establece en false, al mover un miembro primario, los descendientes inmediatos de dicho miembro ascienden al nivel donde residía anteriormente el miembro primario.  
  
 Cuando se actualizan los miembros de un atributo primario, el comando `Update` no puede actualizar los miembros de otros atributos.  
  
## <a name="dropping-existing-members"></a>Quitar miembros existentes  
 Antes de construir el comando `Drop`, debe tener disponible la siguiente información para los miembros que se van a quitar:  
  
-   La dimensión donde se van a quitar miembros existentes.  
  
-   Los atributos de la dimensión donde se van a quitar miembros existentes.  
  
-   Las claves de los miembros existentes que se van a quitar. Si un atributo utiliza una clave compuesta, la clave puede requerir varios valores.  
  
 El comando `Drop` solamente acepta dos propiedades necesarias:  
  
-   La propiedad `Object`, que contiene una referencia de objeto para la dimensión donde van a quitarse los miembros. La referencia de objeto contiene el identificador de la base de datos, el identificador del cubo y el identificador de dimensión para la dimensión.  
  
-   La propiedad `Where`, que contiene uno o más elementos `Attribute` para restringir los atributos donde se van a eliminar los miembros. La propiedad `Where` es fundamental para limitar un comando `Drop` a instancias específicas de un miembro. Si no se especifica el comando `Where`, se quitan todas las instancias de un miembro determinado. Por ejemplo, quiere quitar tres clientes de Redmond. Para quitar estos clientes, debe proporcionar una propiedad `Where` que identifique los tres miembros que se van a quitar en el atributo Customer y el miembro Redmond del atributo City del se van a quitar los tres clientes. Si la propiedad `Where` solamente especifica el miembro Redmond del atributo City, con el comando `Drop` se quitarán todos los clientes asociados a Redmond. Si la propiedad `Where` solamente especifica los tres miembros en el atributo Customer, el comando `Drop` eliminará por completo los tres clientes.  
  
    > [!NOTE]  
    >  Los elementos `Attribute` incluidos en un comando `Drop` solamente deben contener las propiedades `AttributeName` y `Keys`. De lo contrario, puede producirse un error.  
  
### <a name="dropping-members-in-parent-attributes"></a>Quitar miembros de atributos primarios  
 Al establecer la propiedad [DeleteWithDescendants](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/deletewithdescendants-element-xmla) , se indica que los descendientes de un miembro primario también deben eliminarse con el miembro primario. Sin embargo, si este valor se establece en false, los descendientes inmediatos del miembro primario ascienden al nivel donde residía anteriormente el miembro primario.  
  
> [!IMPORTANT]  
>  Para eliminar el miembro primario y sus descendientes, un usuario solamente debe tener permisos de eliminación para el miembro primario. No es necesario que el usuario tenga permisos de eliminación para los descendientes.  
  
## <a name="see-also"></a>Consulte también  
 [Elemento Drop &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla)   
 [Elemento Insert &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla)   
 [Elemento Update &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)   
 [Definir e identificar objetos &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)   
 [Desarrollar con XMLA en Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
