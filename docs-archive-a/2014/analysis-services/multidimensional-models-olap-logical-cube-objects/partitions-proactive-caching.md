---
title: Almacenamiento en caché automático (particiones) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- hybrid OLAP
- partitions [Analysis Services], proactive caching
- relational OLAP
- multidimensional OLAP
- MOLAP
- proactive caching [Analysis Services]
- ROLAP
- cache [Analysis Services]
ms.assetid: 422660b2-4d80-4165-b1c9-3963bcde556b
author: minewiskan
ms.author: owend
ms.openlocfilehash: a903d73394b191dbfe96dea710fb2c6c86165402
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87677915"
---
# <a name="proactive-caching-partitions"></a>Almacenamiento en caché automático (Particiones)
  El almacenamiento en caché automático proporciona la creación y administración automáticas de la memoria caché MOLAP para objetos OLAP. Los cubos incorporan inmediatamente los cambios que se realizan en los datos de la base de datos, basándose en las notificaciones recibidas de la base de datos. El objetivo del almacenamiento en caché automático consiste en proporcionar el rendimiento de MOLAP tradicional, a la vez que se conserva la inmediatez y la facilidad de administración que proporciona ROLAP.  
  
 Un objeto <xref:Microsoft.AnalysisServices.ProactiveCaching> simple se compone de una especificación de tiempo y una notificación de tabla. La especificación de tiempo define el horario para actualizar la caché una vez recibida una notificación de cambio. La notificación de tabla define el esquema de la notificación entre la tabla de datos y el objeto <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
 El almacenamiento OLAP multidimensional (MOLAP) proporciona la mejor respuesta de consultas, a pesar de cierta latencia de datos. El almacenamiento OLAP relacional (ROLAP) en tiempo real permite a los usuarios examinar inmediatamente los cambios más recientes en un origen de datos, a pesar de un rendimiento considerablemente inferior que el almacenamiento OLAP multidimensional (MOLAP) debido a la ausencia de resúmenes de datos precalculados y a que el almacenamiento relacional no está optimizado para consultas de estilo OLAP. Si tiene aplicaciones en las que los usuarios necesitan ver los datos recientes y también desea obtener las ventajas de rendimiento del almacenamiento MOLAP, SQL Server Analysis Services ofrece la opción del almacenamiento en caché automático para solucionar este escenario, especialmente en combinación con el uso de particiones. El almacenamiento en caché automático se establece por partición y por dimensión. Las opciones de almacenamiento en caché automático proporcionan un equilibrio entre el rendimiento mejorado del almacenamiento MOLAP y la inmediatez del almacenamiento ROLAP, así como un procesamiento automático de las particiones cuando los datos subyacentes cambian o conforme a una programación establecida.  
  
## <a name="proactive-caching-configuration-options"></a>Opciones de configuración del almacenamiento en caché automático  
 SQL Server Analysis Services proporciona varias opciones de configuración del almacenamiento en caché automático que permiten maximizar el rendimiento, minimizar la latencia y programar el procesamiento. Las características de almacenamiento en caché automático simplifican el proceso de administrar la obsolescencia de datos. La configuración del almacenamiento en caché automático determina la frecuencia con la que se vuelve a generar la estructura OLAP multidimensional, también denominada caché MOLAP, si se consulta el almacenamiento MOLAP desusado mientras se vuelve a generar la caché o el origen de datos ROLAP subyacente y si se vuelve a generar la caché según una programación o según los cambios en la base de datos.  
  
### <a name="minimizing-latency"></a>Minimizar la latencia  
 Si se configura el almacenamiento en caché automático para minimizar la latencia, las consultas del usuario en un objeto OLAP se realizan en un almacenamiento ROLAP o en un almacenamiento MOLAP, dependiendo de si se han realizado cambios recientes en los datos y la forma en que el almacenamiento en caché automático está configurado. El motor de consultas dirige las consultas a los datos de origen del almacenamiento MOLAP hasta que se realicen los cambios en el origen de datos. A fin de minimizar la latencia, una vez realizados los cambios en un origen de datos, se pueden quitar los objetos MOLAP almacenados en la caché y la consulta cambia al almacenamiento ROLAP mientras que los objetos MOLAP se vuelven a generar en la caché. Después de que se vuelvan a generar y se procesen los objetos MOLAP, las consultas se cambian de forma automática al almacenamiento MOLAP. La actualización de la caché puede ser muy rápida en una partición pequeña, como la actual, que puede ser tan pequeña como el día actual.  
  
### <a name="maximizing-performance"></a>Maximizar el rendimiento  
 Para maximizar el rendimiento y al mismo tiempo reducir la latencia, el almacenamiento en caché también se puede utilizar sin quitar los objetos MOLAP actuales. Pueden continuar ejecutándose las consultas en los objetos MOLAP mientras se leen y se procesan los datos en una nueva caché. Este método proporciona un mejor rendimiento, pero podría devolver datos desusados en algunas consultas mientras se genera la nueva caché.  
  
## <a name="see-also"></a>Consulte también  
 [Almacenamiento de dimensiones](../multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md)   
 [Establecer el almacenamiento de particiones &#40;Analysis Services - Multidimensional&#41;](../multidimensional-models/set-partition-storage-analysis-services-multidimensional.md)  
  
  
