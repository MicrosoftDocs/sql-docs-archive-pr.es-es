---
title: Suscripción, historial de sincronizaciones (suscripción de mezcla, SQL Server 2005 y versiones posteriores) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.subscription.synchhistory.f1
- sql12.rep.monitor.subscription.downlevelsynchhistory.f1
ms.assetid: 85f666f6-14ee-4f19-b385-e5cc508aabe4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 49fe19f22976116813ac2454b2d08fc1fe47d8de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87675808"
---
# <a name="subscription-synchronization-history-merge-subscription-sql-server-2005-and-later"></a>Suscripción, Historial de sincronizaciones (suscripción de mezcla, SQL Server 2005 y versiones posteriores)
  La pestaña **Historial de sincronizaciones** muestra información detallada sobre el Agente de mezcla, incluido el estado, las estadísticas de artículos, el historial, mensajes de información y mensajes de error.  
  
## <a name="options"></a>Opciones  
 Seleccione en el menú **Ver** las sesiones del Agente de mezcla que desea ver y después seleccione una sesión específica en la cuadrícula con la etiqueta **Sesiones del Agente de mezcla**. En la cuadrícula con la etiqueta **Artículos procesados en la sesión seleccionada**se muestra información detallada sobre la sesión.  
  
 **Vista**  
 Permite seleccionar las sesiones del Agente de mezcla que desea ver.  
  
 **Estado**  
 Estado del Agente de mezcla al final de la sesión. En la lista siguiente se muestran los valores de estado posibles:  
  
-   Error  
  
-   Completed  
  
-   Intentando de nuevo  
  
-   En ejecución  
  
 **Start Time**  
 Muestra la hora de inicio de la sesión.  
  
 **Hora de finalización**  
 Muestra la hora de finalización de la sesión. Si no se ha detenido el agente, el campo se mostrará vacío.  
  
 **Duration**  
 Tiempo de ejecución del Agente de mezcla en una sesión. Este tiempo representa el tiempo transcurrido si el agente se está ejecutando actualmente o el tiempo total de ejecución si ya finalizó la ejecución.  
  
 **Comandos cargados**  
 Número de filas cargadas durante la sesión del Agente de mezcla.  
  
 **Comandos descargados**  
 Número de filas descargadas durante la sesión del Agente de mezcla.  
  
 **Mensaje de error**  
 Si la sesión finalizó con un error, este campo muestra el último mensaje de error registrado por el Agente de mezcla. Si la sesión no ha finalizado con error, el campo se mostrará vacío.  
  
 **Artículo**  
 Nombre de cada artículo de la publicación y las siguientes fases de procesamiento para la publicación completa:  
  
-   **Inicialización**. Se refiere a iniciar el Agente de mezcla (no es sinónimo de inicializar una suscripción, que implica aplicar una instantánea).  
  
-   **Cambios de esquema e inserciones masivas**.  
  
-   **Cargar cambios al publicador**.  
  
-   **Descargar cambios al suscriptor**.  
  
 Se incluyen las fases para que la cuadrícula pueda mostrar la cantidad de tiempo y el porcentaje del tiempo total dedicado a cada fase en la sesión seleccionada.  
  
 **% del total**  
 Porcentaje del tiempo total de procesamiento dedicado a cada fase en la sesión seleccionada.  
  
 **Duration**  
 Tiempo dedicado a cada fase de procesamiento. Este tiempo representa el tiempo transcurrido si el Agente de mezcla se está ejecutando actualmente para la sesión y el tiempo total de ejecución si ya finalizó su ejecución.  
  
 **Inserts**  
 Número de filas insertadas en esta fase de la sesión seleccionada.  
  
 **Actualizaciones**  
 Número de filas actualizadas en esta fase de la sesión seleccionada.  
  
 **Eliminaciones**  
 Número de filas eliminadas en esta fase de la sesión seleccionada.  
  
 **Conflictos**  
 Número de conflictos en la sesión seleccionada.  
  
 **Cambios de esquema**  
 Número de cambios de esquema en la sesión seleccionada. Los cambios de esquema pueden ser resultado de: cambios de esquema replicados desde la base de datos de publicación, adición o eliminación de artículos, o cambios de propiedades de un artículo o una publicación.  
  
 **Último mensaje de la sesión seleccionada**  
 Esta área de texto muestra el último mensaje de la sesión seleccionada. Cuando se produce un error se muestra información detallada sobre el error y el comando que se estaba ejecutando. También incluye vínculos a la información adicional relativa al error.  
  
## <a name="see-also"></a>Consulte también  
 [Iniciar el Monitor de replicación](monitor/start-the-replication-monitor.md)   
 [Visualización de información y realización de tareas mediante el Monitor de replicación](monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Monitoring Replication](monitoring-replication.md)  (Supervisar la replicación)  
 [Información general sobre los agentes de replicación](agents/replication-agents-overview.md)  
  
  
