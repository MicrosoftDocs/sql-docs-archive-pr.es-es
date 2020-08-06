---
title: Definir dimensiones de base de datos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], defining
ms.assetid: fe84588b-66a3-4100-a1cf-59b21b7adf01
author: minewiskan
ms.author: owend
ms.openlocfilehash: ad5334e71b0f133f80933a7d1702d8ada7565501
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744401"
---
# <a name="define-database-dimensions"></a>Definir dimensiones de base de datos
  Use el diseñador de dimensiones de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] para configurar una dimensión de base de datos existente en un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] proyecto o base de datos de. Puede usar el Diseñador de dimensiones para realizar lo siguiente:  
  
-   Configurar las propiedades de dimensión-nivel.  
  
-   Agregar y configurar atributos de dimensión.  
  
-   Definir y configurar jerarquías definidas por el usuario.  
  
-   Definir y configurar relaciones entre los atributos.  
  
-   Definir las traducciones de las dimensiones.  
  
-   En dimensiones procesadas, puede examinar la estructura de la dimensión y ver sus datos.  
  
 Después de modificar una dimensión, un atributo o una jerarquía, debe procesar la dimensión para ver los cambios. Al trabajar en modo de proyecto, el usuario implementa los cambios en la instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] antes del procesamiento.  
  
 Para más información sobre cómo abrir una dimensión en el Diseñador de dimensiones, vea [Modificar o eliminar una dimensión de base de datos en el Explorador de soluciones](database-dimensions-modify-or-delete-a-database-dimension-in-solution-explorer.md).  
  
 El Diseñador de dimensiones tiene tres pestañas, que se describen en la siguiente tabla.  
  
|Pestaña|Descripción|  
|---------|-----------------|  
|**Estructura de dimensión**|Use esta pestaña para trabajar con la estructura de una dimensión: para examinar o crear el esquema de la vista del origen de datos para una dimensión, trabajar con atributos y organizar atributos en jerarquías definidas por el usuario.|  
|**Relaciones de atributo**|Utilice esta pestaña para crear, modificar o eliminar las relaciones de atributo de una dimensión.|  
|**Translations**|Utilice esta pestaña para agregar y modificar traducciones de metadatos de dimensiones en distintos idiomas.|  
|**Browser**|Utilice esta pestaña para examinar los miembros de una dimensión procesada y revisar las traducciones de metadatos de dimensiones.|  
  
 En los siguientes temas se describen las tareas que puede realizar en el Diseñador de dimensiones.  
  
 [Referencia de las propiedades de los atributos de dimensión](dimension-attribute-properties-reference.md)  
 Describe cómo definir y configurar un atributo de dimensión.  
  
 [Crear jerarquías definidas por el usuario](user-defined-hierarchies-create.md)  
 Describe cómo definir y configurar una jerarquía definida por el usuario.  
  
 [Definir relaciones de atributo](attribute-relationships-define.md)  
 Describe cómo definir y configurar una relación de atributo.  
  
 [Usar el Asistente de Business Intelligence para mejorar dimensiones](../use-the-business-intelligence-wizard-to-enhance-dimensions.md)  
 Describe cómo mejorar una dimensión con el Asistente de Business Intelligence.  
  
  
