---
title: Jerarquías (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services]
- hierarchies [Master Data Services], about hierarchies
ms.assetid: 70dbb1fc-ead7-45be-9552-a45e3ccd8d21
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 126a01c03134c6859426c09fda398408694795f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674177"
---
# <a name="hierarchies-master-data-services"></a>Jerarquías (Master Data Services)
  En [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], una jerarquía es una estructura en forma de árbol que se puede usar para:

-   Agrupar miembros similares con fines organizativos.

-   Consolidar y resumir miembros para la elaboración de informes y análisis.

## <a name="what-hierarchies-contain"></a>Qué contienen las jerarquías
 Cada jerarquía contiene todos los miembros de una o más entidades. Cuando un miembro se agrega, cambia o elimina, todas las jerarquías se actualizan. Esto garantiza que los datos sean exactos en todas las jerarquías. Las jerarquías también ayudan a asegurarse de que cada miembro se cuenta solamente una vez.

 Si desea crear una agrupación de un subconjunto de miembros, considere la posibilidad de usar una colección. Para obtener más información, consulte [Colecciones &#40;Master Data Services&#41;](collections-master-data-services.md).

## <a name="kinds-of-hierarchies"></a>Tipos de jerarquías
 Puede crear varias jerarquías para ver y organizar los miembros de diferentes maneras. Puede crear:

-   Jerarquías irregulares a partir de una entidad única, que se denominan jerarquías explícitas. Para obtener más información, consulte [Jerarquías explícitas &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md).

-   Jerarquías basadas en el nivel a partir de varias entidades, basándose en las relaciones existentes entre las entidades y sus atributos, que se denominan jerarquías derivadas. Para obtener más información, consulte [Jerarquías derivadas &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md).

> [!NOTE]
>  Todos los miembros de una jerarquía deben estar dentro del mismo modelo.

## <a name="hierarchies-are-not-taxonomies"></a>Las jerarquías no son taxonomías
 Las jerarquías son distintas a las taxonomías. Una taxonomía organiza los miembros según diversos atributos al mismo tiempo, mientras que una jerarquía organiza los miembros según un atributo cada vez. Una taxonomía puede incluir al mismo miembro varias veces, mientras que una jerarquía solo incluye un miembro una vez.

 Por ejemplo, la misma bicicleta se puede incluir dos veces en una taxonomía: una vez porque sea roja y otra porque sea de la talla 38. En una jerarquía, la bicicleta solo se incluye una vez, por lo que debe decidir si mostrarla en relación con su color o su tamaño.

## <a name="hierarchy-example"></a>Ejemplo de jerarquía
 En el ejemplo siguiente, los miembros de Product se agrupan según los miembros de la subcategoría.

 ![Ejemplo de jerarquía agrupada por subcategoría](../../2014/master-data-services/media/mds-conc-hierarchy.gif "Ejemplo de jerarquía agrupada por subcategoría")

## <a name="related-tasks"></a>Related Tasks

|Descripción de la tarea|Tema|
|----------------------|-----------|
|Habilitar una entidad para colecciones y jerarquías explícitas.|[Habilitar una entidad para colecciones y jerarquías explícitas &#40;Master Data Services&#41;](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)|
|Crear una jerarquía explícita.|[Crear una jerarquía explícita &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)|
|Crear una jerarquía derivada.|[Crear una jerarquía derivada &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md)|
|Ocultar o eliminar niveles en una jerarquía derivada existente.|[Ocultar o eliminar niveles en una jerarquía derivada &#40;Master Data Services&#41;](../../2014/master-data-services/hide-or-delete-levels-in-a-derived-hierarchy-master-data-services.md)|

## <a name="related-content"></a>Contenido relacionado

-   [Jerarquías explícitas &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)

-   [Jerarquías derivadas &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)

-   [Jerarquías recursivas &#40;Master Data Services&#41;](../../2014/master-data-services/recursive-hierarchies-master-data-services.md)

-   [Jerarquías derivadas con límites explícitos &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)

-   [Colecciones &#40;Master Data Services&#41;](collections-master-data-services.md)


