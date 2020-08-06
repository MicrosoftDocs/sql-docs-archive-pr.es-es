---
title: Editor de rutas de flujo de datos (página general) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.patheditor.general.f1
helpviewer_keywords:
- Data Flow Path Editor dialog box
ms.assetid: 72a9ff1d-3748-41d1-a9b2-63f4a77bba24
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 71eca61b1454e2e8cb811bbe450f584191ae77b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744811"
---
# <a name="data-flow-path-editor-general-page"></a>Editor de rutas de flujo de datos (página General)
  Utilice el cuadro de diálogo **Editor de rutas de flujo de datos** para establecer propiedades de ruta, ver metadatos de columna y administrar los visores de datos adjuntados a la ruta.  
  
 Utilice el nodo **General** del cuadro de diálogo **Editor de rutas de flujo de datos** para nombrar y describir la ruta, y para especificar las opciones de anotación de ruta.  
  
## <a name="options"></a>Opciones  
 **Nombre**  
 Proporcione un nombre único para la ruta.  
  
 **ID**  
 El identificador de linaje de la ruta. Esta propiedad es de sólo lectura.  
  
 **IdentificationString**  
 La cadena que identifica la ruta. Se automáticamente a partir del nombre especificado con anterioridad.  
  
 **Descripción**  
 Describe la ruta.  
  
 **PathAnnotation**  
 Especificar el tipo de anotación que se va a usar. Elija **Nunca** para deshabilitar anotaciones, **AsNeeded** para habilitar anotaciones a petición, **SourceName** para realizar anotaciones automáticamente utilizando el valor de la opción **SourceName** y **PathName** para realizar anotaciones automáticamente utilizando el valor de la propiedad **Nombre** .  
  
 **DestinationName**  
 Muestra la entrada que es el final de la ruta.  
  
 **SourceName**  
 Muestra la salida que es el inicio de la ruta.  
  
## <a name="see-also"></a>Consulte también  
 [Editor de rutas de flujo de datos &#40;página de metadatos&#41;](../../2014/integration-services/data-flow-path-editor-metadata-page.md)   
 [Editor de rutas de flujo de datos &#40;página visores de datos&#41;](../../2014/integration-services/data-flow-path-editor-data-viewers-page.md)   
 [Flujo de datos](data-flow/data-flow.md)   
 [Usar anotaciones en paquetes](use-annotations-in-packages.md)  
  
  
