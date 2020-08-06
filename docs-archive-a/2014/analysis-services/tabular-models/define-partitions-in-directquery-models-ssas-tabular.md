---
title: Particiones y el modo DirectQuery (SSAS tabular) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5f179ba9-6efb-46ae-90e5-945bbfddb719
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5957ed919f15a5c7f39c3c78133786ae6687a2d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87675516"
---
# <a name="partitions-and-directquery-mode-ssas-tabular"></a>Particiones y el modo DirectQuery (SSAS tabular)
  En esta sección se explica cómo se utilizan las particiones en los modelos DirectQuery. Para obtener información general sobre las particiones en los modelos tabulares, vea [Particiones &#40;SSAS tabular&#41;](partitions-ssas-tabular.md).  
  
 Para obtener instrucciones sobre cómo cambiar la partición que se utiliza o ver información acerca de la partición, vea [cambiar la partición de DirectQuery &#40;&#41;tabular de SSAS ](../change-the-directquery-partition-ssas-tabular.md).  
  
## <a name="using-partitions-in-directquery-mode"></a>El uso de particiones en el modo DirectQuery  
 Para cada tabla, debe especificar una única partición para utilizar como origen de datos de DirectQuery.  De forma predeterminada, si existen varias particiones, al cambiar el modelo para habilitar el modo DirectQuery, la primera partición que se creó en la tabla se marcará como la partición DirectQuery. Puede cambiar este comportamiento posteriormente mediante el Administrador de particiones de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 ¿Por qué permitir únicamente una sola partición en el modo DirectQuery?  
  
 En los modelos tabulares (al igual que en los modelos OLAP), las particiones de una tabla se definen mediante consultas SQL. El desarrollador que crea la definición de la partición es el responsable de garantizar que las particiones no superpongan. Analysis Services no comprueba si los registros pertenecen a una o a varias particiones.  
  
 Las particiones de un modelo tabular almacenado en caché se comportan de la misma manera. Si se utiliza un modelo en memoria, las fórmulas DAX se evalúan para cada partición mientras se obtiene acceso a la caché, y se combinan los resultados. Sin embargo, cuando un modelo tabular utiliza el modo DirectQuery, no se puede evaluar varias particiones, combinar los resultados y convertir todo esto en una instrucción SQL para enviarla al almacén de datos relacional. Esto podría ocasionar una pérdida inaceptable de rendimiento, así como posibles imprecisiones a medida que se agregan los resultados.  
  
 Por lo tanto, para las consultas respondidas en modo DirectQuery, el servidor usa una única partición que se ha marcado como partición principal para el acceso de DirectQuery, denominada *partición DirectQuery*.  La consulta SQL especificada en la definición de esta partición define el conjunto completo de datos que pueden usarse para responder consultas en el modo DirectQuery.  
  
 Si no define de forma explícita una partición, el motor simplemente emite una consulta SQL al origen de datos relacional completo, realiza las operaciones basadas en conjuntos dictadas por la fórmula DAX y devuelve los resultados de la consulta.  
  
 Si tiene varias particiones en una tabla, y selecciona una partición como la partición de DirectQuery, las demás particiones se marcan de forma predeterminada para su uso solo en memoria.  
  
## <a name="partitions-in-cached-models-and-in-directquery-models"></a>Particiones de modelos almacenados en caché y modelos DirectQuery  
 Al configurar una partición DirectQuery, debe especificar las opciones de procesamiento para la partición.  
  
 Hay dos opciones de procesamiento para la partición DirectQuery. Para establecer esta propiedad, use el **Administrador de particiones** en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], y seleccione la propiedad **Opción de procesamiento** . En la tabla siguiente se muestran los valores de esta propiedad y se describen los efectos de cada valor cuando se combinan con la propiedad DirectQueryUsage en la cadena de conexión:  
  
|Propiedad **DirectQueryUsage**|Propiedad**Opción de procesamiento**|Notas|  
|-----------------------------------|------------------------------------|-----------|  
|DirectQuery|No procesar nunca esta partición|Cuando el modelo utiliza Solo DirectQuery, el procesamiento no es necesario nunca.<br /><br /> En los modelos híbridos, es posible configurar la partición DirectQuery para que no se procese nunca. Por ejemplo, si está trabajando con un conjunto de datos muy grande y no desea que los resultados completos se agreguen a la memoria caché, puede especificar que la partición DirectQuery incluya la unión de los resultados para el resto de particiones de la tabla y no procesar nunca dicha unión. Las consultas dirigidas al origen relacional no se verán afectadas, y las consultas en los datos en caché combinarán datos del resto de particiones|  
|Inmemory con DirectQuery|Permitir procesar la partición|Si el modelo utiliza el modo híbrido, debe usar la misma partición para las consultas en memoria y las consultas en el origen de datos de DirectQuery.|  
  
## <a name="see-also"></a>Consulte también  
 [Particiones &#40;SSAS tabular&#41;](partitions-ssas-tabular.md)  
  
  
