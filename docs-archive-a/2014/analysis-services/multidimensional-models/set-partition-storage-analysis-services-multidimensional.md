---
title: Establecer el almacenamiento de particiones (Analysis Services-multidimensional) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- low latency MOLAP
- standard storage [Analysis Services]
- hybrid OLAP
- automatic MOLAP
- relational OLAP
- multidimensional OLAP
- scheduled MOLAP [Analysis Services]
- partitions [Analysis Services], storage
- HOLAP
- MOLAP
- real time ROLAP
- real time HOLAP
- ROLAP
- medium latency MOLAP
ms.assetid: e525e708-f719-4905-a4cc-20f6a9a3edcd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 10e9a269fd2a33cc2510823d042f18aee1e91f02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673348"
---
# <a name="set-partition-storage-analysis-services---multidimensional"></a>Establecer el almacenamiento de particiones (Analysis Services - Multidimensional)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] proporciona varias configuraciones de almacenamiento estándar para los modos de almacenamiento y las opciones de almacenamiento en caché. Estas configuraciones proporcionan parámetros de uso común para la notificación de actualizaciones, la latencia y la regeneración de datos.  
  
 Puede especificar el almacenamiento de las particiones en la pestaña Particiones del cubo en [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]o en la página de propiedades de la partición de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="guidelines-for-choosing-a-storage-mode"></a>Directrices para elegir un modo de almacenamiento  
 En el caso de un grupo de medida grande, es frecuente configurar el almacenamiento de forma diferente para las distintas particiones. Tenga en cuenta las directrices siguientes:  
  
-   Usar ROLAP en tiempo real para los datos actuales que se actualizan continuamente.  
  
-   Usar el almacenamiento en caché automático con baja latencia o latencia media para las particiones basadas en orígenes de datos que se actualizan con menor frecuencia.  
  
-   Usar MOLAP automático para los orígenes de datos donde los usuarios necesitan alto rendimiento, pero pueden tolerar cierta latencia en los datos.  
  
-   Usar MOLAP programado para los orígenes de datos donde los usuarios necesitan obtener acceso a los datos continuamente, pero solo los ven de forma periódica.  
  
-   Usar el almacenamiento MOLAP sin almacenamiento en caché automático para las particiones que no cambian o lo hacen con poca frecuencia; para las particiones donde los usuarios no necesitan examinar los datos más recientes; y donde los datos no tienen que estar constantemente disponibles para los usuarios durante las actualizaciones o los procesamientos necesarios.  
  
 Éstas son directrices generales, y es posible que sean necesarios cuidadosos análisis y pruebas para desarrollar el mejor esquema de almacenamiento para los datos. También puede configurar manualmente los parámetros de almacenamiento para una partición si ninguna de las configuraciones estándar satisface sus necesidades.  
  
## <a name="storage-settings-descriptions"></a>Descripción de las configuraciones de almacenamiento  
  
|Configuración de almacenamiento estándar|Descripción|  
|------------------------------|-----------------|  
|ROLAP en tiempo real|OLAP se lleva a cabo en tiempo real. Los datos de detalle y las agregaciones se almacenan en formato relacional. El servidor escucha notificaciones cuando los datos cambian y todas las consultas reflejan el estado actual de los datos (latencia cero).<br /><br /> Por lo general, esta configuración se utiliza para un origen de datos con actualizaciones muy frecuentes y continuas, cuando los usuarios necesitan siempre los datos más recientes. Dependiendo de los tipos de consultas que generan las aplicaciones cliente, este método puede ofrecer los tiempos de respuesta más lentos.|  
|HOLAP en tiempo real|OLAP se lleva a cabo en tiempo real. Los datos de detalle se almacenan en formato relacional, en tanto que las agregaciones se almacenan en un formato multidimensional. El servidor escucha notificaciones cuando los datos cambian y actualiza las agregaciones OLAP multidimensionales (MOLAP) siempre que sea necesario. No se crea una caché MOLAP. Siempre que el origen de datos se actualiza, el servidor cambia a OLAP relacional (ROLAP) en tiempo real hasta que se actualizan las agregaciones. Todas las consultas reflejan el estado actual de los datos (latencia cero).<br /><br /> Por lo general, esta configuración se utiliza para un origen de datos con actualizaciones frecuentes y continuas (pero no tan frecuentes como para que sea necesario ROLAP en tiempo real) donde los usuarios requieren siempre los datos más recientes. Este método proporciona, en general, un mejor rendimiento global que el almacenamiento ROLAP. Los usuarios pueden obtener el rendimiento MOLAP de esta configuración si el origen de datos permanece en silencio un período suficientemente largo.|  
|MOLAP de latencia baja|Los datos de detalle y las agregaciones se almacenan en formato multidimensional. El servidor escucha notificaciones de los cambios en los datos y cambia a ROLAP en tiempo real mientras los objetos MOLAP se vuelven a procesar en una caché. Antes de actualizar la caché se requiere un intervalo de latencia de, al menos, 10 segundos. Si el intervalo de latencia no se obtiene, hay un intervalo de reemplazo de 10 minutos. El procesamiento se produce automáticamente cuando los datos cambian, con una latencia de destino de 30 minutos después del primer cambio.<br /><br /> Por lo general, esta configuración se utiliza para un origen de datos con actualizaciones frecuentes y cuando, de algún modo, el rendimiento de la consulta es más importante que la obtención de los datos más actualizados. Esta configuración procesa automáticamente los objetos MOLAP siempre que sea necesario después del intervalo de latencia. El rendimiento es más lento durante el reprocesamiento de los objetos MOLAP.|  
|MOLAP de latencia media|Los datos de detalle y las agregaciones se almacenan en formato multidimensional. El servidor escucha notificaciones de los cambios en los datos y cambia a ROLAP en tiempo real mientras los objetos MOLAP se reprocesan en la caché. Antes de actualizar la caché se requiere un intervalo de latencia de, al menos, 10 segundos. Si el intervalo de latencia no se obtiene, hay un intervalo de reemplazo de 10 minutos. El procesamiento se produce automáticamente cuando los datos cambian, con una latencia de destino de cuatro horas.<br /><br /> Por lo general, esta configuración se utiliza para un origen de datos con actualizaciones frecuentes (o menos frecuentes) y cuando el rendimiento de la consulta es más importante que la obtención continua de los datos más actualizados. Esta configuración procesa automáticamente los objetos MOLAP siempre que sea necesario después del intervalo de latencia. El rendimiento es más lento durante el reprocesamiento de los objetos MOLAP.|  
|MOLAP automático|Los datos de detalle y las agregaciones se almacenan en formato multidimensional. El servidor escucha notificaciones, pero mantiene la caché MOLAP actual mientras genera una nueva. El servidor nunca cambia a OLAP en tiempo real y las consultas pueden quedar desusadas durante la generación de la nueva caché.<br /><br /> Se requiere un intervalo de latencia de, al menos, 10 segundos, antes de crear la nueva caché MOLAP. Si el intervalo de latencia no se obtiene, hay un intervalo de reemplazo de 10 minutos. El procesamiento se produce automáticamente cuando los datos cambian, con una latencia de destino de dos horas.<br /><br /> Por lo general, esta configuración se utiliza para un origen de datos cuando el rendimiento de la consulta es un factor importante. Esta configuración procesa automáticamente los objetos MOLAP siempre que sea necesario después del intervalo de latencia. Las consultas no devuelven los datos más recientes mientras se genera y procesa la nueva caché.|  
|MOLAP programado|Los datos de detalle y las agregaciones se almacenan en formato multidimensional. El servidor no recibe notificaciones cuando los datos cambian. El procesamiento se lleva a cabo automáticamente cada 24 horas.<br /><br /> Por lo general, esta configuración se utiliza para un origen de datos cuando solamente se requieren actualizaciones diarias. Las consultas se hacen siempre con los datos de la caché MOLAP, y ésta no se descarta hasta que se genera una nueva caché y se procesan sus objetos.|  
|MOLAP|No se habilita el almacenamiento en caché automático. Los datos de detalle y las agregaciones se almacenan en formato multidimensional. El servidor no recibe notificaciones cuando los datos cambian. El procesamiento debe estar programado o realizarse manualmente.<br /><br /> Por lo general, esta configuración se utiliza para un origen de datos en la que no se necesitan actualizaciones periódicas para las aplicaciones cliente, pero donde el rendimiento resulta esencial.<br /><br /> El almacenamiento MOLAP sin almacenamiento en caché automático proporciona el mejor rendimiento posible si las aplicaciones no requieren los datos más recientes. Requiere tiempo de inactividad para procesar los objetos actualizados, aunque este período puede reducirse mediante la actualización y el procesamiento de los cubos en un servidor de prueba y la utilización de la sincronización de bases de datos para copiar los objetos MOLAP actualizados y procesados al servidor de producción.|  
  
## <a name="custom-storage-options"></a>Opciones de almacenamiento personalizado  
 En vez de utilizar una de las configuraciones de almacenamiento estándar, puede configurar manualmente el almacenamiento y el almacenamiento en caché automático. Antes de crear valores de almacenamiento personalizados, haga clic en la opción **Configuración estándar** y mueva el control deslizante hasta la configuración estándar que más se aproxime a los valores que desee utilizar. A continuación, para crear una configuración personalizada, haga clic en la opción **Configuración personalizada** y elija **Opciones**.  
  
-   Puede especificar si los cambios en los datos del origen de datos desencadenan actualizaciones en la caché. Para permitir un nivel tolerable de cambios, puede especificar un intervalo mínimo de silencio tras las actualizaciones del origen de datos. También puede especificar una anulación del intervalo de silencio que actualice la caché después de un período de tiempo especificado si el intervalo entre los cambios del origen de datos no alcanza nunca el mínimo.  
  
-   Puede especificar si se quita la caché anterior cuando se produce una actualización. Si selecciona esta opción, cuando se supera la latencia especificada el servidor cambia a OLAP relacional (ROLAP) en tiempo real mientras actualiza la caché. Si no la selecciona, el servidor continua realizando consultas en la caché OLAP multidimensional (MOLAP) desusada mientras genera una nueva.  
  
     Puede especificar el intervalo de latencia que debe transcurrir entre los cambios y la eliminación de una caché desusada. Este intervalo indica la cantidad de tiempo que los usuarios pueden continuar explorando datos en una caché desusada antes de que se elimine. Si se producen cambios y la caché todavía se está actualizando o procesando al final de este intervalo, las consultas se redirigirán a ROLAP.  
  
-   Puede programar actualizaciones impuestas de la caché si desea actualizar periódicamente los objetos MOLAP de la caché independientemente de los cambios en el origen de datos. Las ventajas de OLAP en tiempo real varían según el tamaño de la base de datos y el periodo de latencia asignado por frecuencia de cambios en el origen de datos. Lo más recomendable es que los usuarios envíen consultas a la caché tan a menudo como sea posible, no a ROLAP.  
  
 Si activa la casilla **Aplicar configuración a dimensiones** , se aplica la misma configuración de almacenamiento a las dimensiones relacionadas con el grupo de medida. Los valores de la dimensión son inicialmente los mismos que los valores de la partición.  
  
## <a name="see-also"></a>Consulte también  
 [Particiones en modelos multidimensionales](partitions-in-multidimensional-models.md)  
  
  
