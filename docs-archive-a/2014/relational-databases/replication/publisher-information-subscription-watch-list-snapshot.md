---
title: Información del publicador, lista de supervisión de suscripciones (publicación de instantáneas, SQL Server 2005 y versiones posteriores) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.subscriptionssummary.snapshot.f1
ms.assetid: 2ebeee62-7f54-4c77-9d37-15708bc5cc23
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ea44958c81465570c036ab7dd83247fb55652f1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746245"
---
# <a name="publisher-information-subscription-watch-list-snapshot-publication-sql-server-2005-and-later"></a>Información de publicador, Lista de supervisión de suscripciones (Publicación de instantáneas, SQL Server 2005 y posteriores)
  La pestaña **Lista de supervisión de suscripciones** está disponible para distribuidores que ejecutan [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] y versiones posteriores; está pensada para mostrar información sobre las suscripciones de todas las publicaciones disponibles en el publicador seleccionado. Puede filtrar la lista de suscripciones para ver errores, advertencias y las suscripciones que tienen un rendimiento bajo. Esta pestaña proporciona una ubicación única para que un administrador supervise toda la actividad de replicación en un publicador: el Monitor de replicación muestra todas las suscripciones que necesitan atención, basándose en el tipo de replicación seleccionado y en la opción elegida en el cuadro de lista desplegable **Mostrar** . Puesto que los elementos mostrados en esta pestaña se basan en el rendimiento y el estado actual, las suscripciones se muestran en esta página solo si coinciden con la opción del cuadro de lista **Mostrar** en el momento actual.  
  
## <a name="options"></a>Opciones  
 Para obtener información más detallada y las tareas de una suscripción, haga clic con el botón secundario en la fila de dicha suscripción y, a continuación, haga clic en una opción del menú contextual. Para cambiar la manera que la cuadrícula muestra los datos, haga clic con el botón secundario en la cuadrícula y, a continuación, haga clic en una de las opciones siguientes:  
  
-   **Ordenar**: ordene en una o más columnas en el cuadro de diálogo **Ordenar columnas** .  
  
-   **Elegir columnas para mostrar**: seleccione las columnas que se mostrarán y el orden en el que se mostrarán en el cuadro de diálogo **Elegir columnas** .  
  
-   **Filtro**: filtre filas en la cuadrícula basándose en los valores de columna en el cuadro de diálogo **Configuración del filtro** .  
  
-   **Borrar filtro**: borre cualquier configuración de filtro para la cuadrícula.  
  
 La configuración del filtro es específica de cada cuadrícula. La selección y ordenación de las columnas se aplica a todas las cuadrículas del mismo tipo, como la cuadrícula de las publicaciones para cada Publicador.  
  
 **Mostrar suscripciones de instantáneas**  
 Seleccione el tipo de suscripción (transaccional, de instantánea o de mezcla) que se mostrará para el publicador seleccionado.  
  
 **Mostrar**  
 Seleccione los estados de la suscripción que se mostrarán para el tipo de suscripción seleccionado. Por ejemplo, puede seleccionar mostrar solo aquellas suscripciones que tienen errores.  
  
 **Estado**  
 Muestra el estado de cada suscripción, que viene determinado por el estado del Agente de instantáneas o el Agente de distribución (se muestra el estado de prioridad más alto).  
  
 De forma predeterminada, la cuadrícula que contiene la información de la suscripción se ordena por la columna **Estado** . La siguiente lista muestra los valores de estado posibles y el criterio de ordenación de los valores (por ejemplo, los errores se muestran siempre en la parte superior de la cuadrícula).  
  
-   Error  
  
-   Con expiración en breve/Expirada  
  
-   Suscripción no inicializada  
  
-   Reintentando comando con errores  
  
-   Sincronizando  
  
-   No se están sincronizando  
  
 El criterio de clasificación también determina qué valor se muestra si una misma suscripción presenta varios estados. Por ejemplo, si una suscripción tiene un error y expirará en breve, la columna **Estado** muestra **Error**.  
  
 Los valores de estado **Con expiración en breve/Expirado** y **Suscripción no inicializada** son advertencias. Cuando se muestra una advertencia, también aparece la columna **Estado** si un agente está ejecutándose. Por ejemplo, el estado podría ser **En ejecución, Con expiración en breve/Expirado**.  
  
 El valor de estado **Con expiración en breve/Expirado** solamente se muestra si se ha establecido un umbral. Para obtener más información, vea [Establecer umbrales y advertencias en el Monitor de replicación](monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
 **Suscripción**  
 Muestra el nombre de cada suscripción, en el formato: *nombreDeSuscriptor: nombreDeBaseDeDatosDeSuscripción*.  
  
 **Publicación**  
 Muestra el nombre de la publicación con la que se sincroniza una suscripción, en el formato: *nombreDeBaseDeDatosDePublicación: nombreDePublicación*.  
  
 **Última sincronización**  
 Indica la hora en que se ejecutó por última vez el Agente de distribución. Si la sincronización está en curso, se muestra **En curso** .  
  
## <a name="see-also"></a>Consulte también  
 [Iniciar el monitor de replicación](monitor/start-the-replication-monitor.md)   
 [Visualización de información y realización de tareas mediante el Monitor de replicación](monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Supervisar la replicación](monitoring-replication.md)  
  
  
