---
title: Dimensiones en modelos multidimensionales | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- OLAP [Analysis Services], dimensions
- dimensions [Analysis Services], about dimensions
- OLAP objects [Analysis Services], dimensions
ms.assetid: 2b62b05c-00fd-4e60-b77f-f707ba83a19b
author: minewiskan
ms.author: owend
ms.openlocfilehash: b9e452453b80de3656abf62cdcd90519cf4a6c99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750294"
---
# <a name="dimensions-in-multidimensional-models"></a>Dimensiones en modelos multidimensionales
  Una dimensión de base de datos es una colección de objetos relacionados, denominados atributos, que se pueden usar para proporcionar información sobre los datos de hechos de uno o varios cubos. Por ejemplo, los atributos típicos de una dimensión de producto pueden ser el nombre, la categoría, la línea, el tamaño y el precio del producto. Estos objetos están enlazados a una o varias columnas de una o varias tablas de una vista del origen de datos. De manera predeterminada, estos atributos están visibles como jerarquías de atributo y se pueden utilizar para comprender los datos de hechos en un cubo. Los atributos se pueden organizar en jerarquías definidas por el usuario que proporcionan rutas de navegación para ayudar a los usuarios al examinar los datos de un cubo.  
  
 Los cubos contienen todas las dimensiones en las que los usuarios basan sus análisis de los datos de hechos. Una instancia de una dimensión de base de datos en un cubo se denomina dimensión de cubo y se relaciona con uno o más grupos de medida en el cubo. Una dimensión de base de datos se puede utilizar varias veces en un cubo. Por ejemplo, una tabla de hechos puede tener varios hechos relacionados con el tiempo y se puede definir una dimensión de cubo independiente que sirva de ayuda para analizar cada uno de ellos. Sin embargo, solo es necesario que haya una dimensión de base de datos relacionada con el tiempo, lo que significa también que solo es necesario que haya una tabla de base de datos relacional relacionada con el tiempo para admitir varias dimensiones de cubo basadas en el tiempo.  
  
> [!NOTE]  
>  Para obtener información sobre los problemas de rendimiento relacionados con el diseño de dimensiones, vea la [Guía de rendimiento de SQL Server 2008 R2 Analysis Services](https://go.microsoft.com/fwlink/?LinkId=306717).  
  
## <a name="defining-dimensions-attributes-and-hierarchies"></a>Definir dimensiones, atributos y jerarquías  
 El método más simple para definir dimensiones, atributos y jerarquías de base de datos y de cubo es utilizar el Asistente para cubos para crear las dimensiones a la vez que se define el cubo. El Asistente para cubos creará dimensiones basadas en las tablas de dimensiones en la vista del origen de datos que el asistente identifique o que el usuario especifique para su uso en el cubo. A continuación, el asistente crea las dimensiones de base de datos y las agrega al cubo nuevo, con lo que se crean dimensiones de cubo.  
  
 Cuando se crea un cubo, también se pueden agregar al nuevo cubo las dimensiones que existen en la base de datos. Estas dimensiones pueden haber sido definidas previamente para otro cubo o por el Asistente para dimensiones. Una vez definida una dimensión de base de datos, no puede modificar ni configurar la dimensión de base de datos en el Diseñador de dimensiones. También puede personalizar la dimensión de cubo, de forma limitada, en el Diseñador de cubos  
  
> [!NOTE]  
>  Además puede diseñar y configurar dimensiones, atributos y jerarquías mediante programación utilizando XMLA u Objetos de administración de análisis (AMO). Para obtener más información, vea [Analysis Services scripting Language &#40;ASSL&#41; referencia](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla) y [desarrollo con objetos de administración de análisis &#40;amo ](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)&#41;.  
  
## <a name="in-this-section"></a>En esta sección  
 En la tabla siguiente se describen los temas de esta sección.  
  
 [Definir dimensiones de base de datos](define-database-dimensions.md)  
 Describe cómo modificar y configurar una dimensión de base de datos mediante el Diseñador de dimensiones.  
  
 [Referencia de las propiedades de los atributos de dimensión](dimension-attribute-properties-reference.md)  
 Describe cómo definir, modificar y configurar un atributo de dimensión de base de datos mediante el Diseñador de dimensiones.  
  
 [Definir relaciones de atributo](attribute-relationships-define.md)  
 Describe cómo definir, modificar y configurar una relación de atributo mediante el Diseñador de dimensiones.  
  
 [Crear jerarquías definidas por el usuario](user-defined-hierarchies-create.md)  
 Describe cómo definir, modificar y configurar una jerarquía definida por el usuario de atributos de dimensión mediante el Diseñador de dimensiones.  
  
 [Usar el Asistente de Business Intelligence para mejorar dimensiones](../use-the-business-intelligence-wizard-to-enhance-dimensions.md)  
 Describe cómo mejorar una dimensión de base de datos mediante el Asistente de Business Intelligence.  
  
## <a name="see-also"></a>Consulte también  
 [Cubos en modelos multidimensionales](cubes-in-multidimensional-models.md)  
  
  
