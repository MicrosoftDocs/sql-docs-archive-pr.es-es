---
title: Editor de transformación mapa de caracteres | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.charactermaptransformation.f1
helpviewer_keywords:
- Character Map Transformation Editor
ms.assetid: 3f1dbcf9-9cca-4606-bdcc-7ea6ad48cdf3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c6cdcdba448dafc6ccf03774d4f611dee704b823
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87670501"
---
# <a name="character-map-transformation-editor"></a>Editor de transformación Mapa de caracteres
  Use el cuadro de diálogo **Editor de transformación Mapa de caracteres** para seleccionar las funciones de cadena que se van a aplicar a datos de columna y para especificar si la asignación es una modificación en contexto o se agrega como una columna nueva.  
  
 Para obtener más información acerca de la transformación Mapa de caracteres, vea [Character Map Transformation](data-flow/transformations/character-map-transformation.md).  
  
## <a name="options"></a>Opciones  
 **Columnas de entrada disponibles**  
 Use las casillas para seleccionar las columnas que se van a transformar con las funciones de cadena. Las selecciones aparecen en la siguiente tabla.  
  
 **Columna de entrada**  
 Muestra las columnas de entrada seleccionadas de la tabla anterior. También puede cambiar o quitar una selección utilizando la lista de columnas de entrada disponibles.  
  
 **Destino**  
 Especifique si se guardan los resultados de las operaciones de cadena en contexto, utilizando la columna existente, o se guardan los datos modificados como una columna nueva.  
  
|Value|Descripción|  
|-----------|-----------------|  
|Nueva columna|Guardar los datos en una columna nueva. Asigne el nombre de columna en **Alias de salida**.|  
|Modificación en contexto|Guardar los datos modificados en la columna existente.|  
  
 **operación**  
 Seleccione de la lista las funciones de cadena que se aplicarán a los datos de la columna.  
  
|Value|Descripción|  
|-----------|-----------------|  
|Minúsculas|Convertir en minúsculas.|  
|Uppercase|Convertir en mayúsculas.|  
|Inversión de byte|Convertir invirtiendo el orden de los bytes.|  
|Hiragana|Convertir caracteres japoneses katakana en caracteres hiragana.|  
|Katakana|Convertir caracteres japoneses hiragana en caracteres katakana.|  
|Formato medio|Convertir caracteres de formato completo en formato medio.|  
|Formato completo|Convertir caracteres de formato medio en formato completo.|  
|Utilización lingüística de mayúsculas y minúsculas|Aplicar reglas lingüísticas de mayúsculas y minúsculas (asignación de caracteres Unicode simples del turco y otras configuraciones regionales) en vez de otras reglas del sistema.|  
|Chino simplificado|Convertir caracteres de chino tradicional en chino simplificado.|  
|Chino tradicional|Convertir caracteres de chino simplificado en chino tradicional.|  
  
 **Alias de salida**  
 Escriba un alias para cada columna de salida. El valor predeterminado es **Copy of** seguido del nombre de la columna de entrada; no obstante, puede elegir un nombre descriptivo exclusivo.  
  
 **Configurar la salida de errores**  
 Use el cuadro de diálogo [Configurar la salida de errores](../../2014/integration-services/configure-error-output.md) para especificar las opciones de control de errores de esta transformación.  
  
## <a name="see-also"></a>Consulte también  
 [Referencia de errores y mensajes de Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
