---
title: Usar el panel de AlwaysOn (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
- Availability Groups [SQL Server], dashboard
ms.assetid: c9ba2589-139e-42bc-99e1-94546717c64d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c4ce0072bcd6642dcb4f3ac63e04c98786bd550e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87670588"
---
# <a name="use-the-alwayson-dashboard-sql-server-management-studio"></a>Usar el Panel de AlwaysOn (SQL Server Management Studio)
  Los administradores de bases de datos utilizan el Panel AlwaysOn para obtener una vista global del estado de un grupo de disponibilidad AlwaysOn y de sus réplicas y bases de datos de disponibilidad en [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Algunas de los usos típicos del Panel AlwaysOn son:  
  
-   Elegir una réplica para una conmutación por error manual.  
  
-   Estimar la pérdida de datos si se fuerza la conmutación por error.  
  
-   Evaluar el rendimiento de la sincronización de datos.  
  
-   Evaluar el impacto en el rendimiento de una réplica secundaria de confirmación asincrónica  
  
 El Panel AlwaysOn proporciona indicadores de rendimiento y estados de grupos de disponibilidad, lo que permite tomar fácilmente decisiones operativas para conseguir una alta disponibilidad utilizando los siguientes tipos de información.  
  
-   Estado acumulado de réplica  
  
-   Modo y estado de sincronización  
  
-   Pérdida de datos calculada  
  
-   Tiempo calculado de recuperación (rehacer puesta al día)  
  
-   Detalles de réplica de base de datos  
  
-   Modo y estado de sincronización  
  
-   Tiempo para restaurar registro  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Requisitos previos  
 Debe estar conectado a la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (instancia del servidor) que hospeda la réplica principal o una réplica secundaria de un grupo de disponibilidad.  
  
###  <a name="security"></a><a name="Security"></a> Seguridad  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permisos  
 Requiere permisos CONNECT TO, VIEW SERVER STATE y VIEW ANY DEFINITION.  
  
##  <a name="to-start-the-alwayson-dashboard"></a><a name="SSMSProcedure"></a>Para iniciar el panel de AlwaysOn  
  
1.  En el Explorador de objetos, conéctese a la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en la que desea ejecutar el Panel AlwaysOn.  
  
2.  Expanda el nodo **Alta disponibilidad de AlwaysOn** , haga clic con el botón secundario en el nodo **Grupos de disponibilidad** y, a continuación, haga clic en **Mostrar panel**.  
  
###  <a name="to-change-alwayson-dashboard-options"></a><a name="DashboardOptions"></a>Para cambiar las opciones del panel de AlwaysOn  
 Puede usar el cuadro de diálogo **Opciones** de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] para configurar el comportamiento del Panel AlwaysOn de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] respecto a la actualización y habilitación automática de una directiva de AlwaysOn autodefinida.  
  
1.  En el menú **Herramientas** , haga clic en **Opciones**.  
  
2.  Para actualizar automáticamente el panel, en el cuadro de diálogo **Opciones** , seleccione **Activar actualización automática**, escriba el intervalo de actualización en segundos y especifique el número de veces que desea volver a intentar la conexión.  
  
3.  Para habilitar una directiva definida por el usuario, seleccione **Habilitar la directiva de AlwaysOn definida por el usuario**.  
  
##  <a name="availability-group-summary"></a><a name="AvGroupsView"></a> Resumen de grupos de disponibilidad  
 La pantalla de grupos de disponibilidad muestra una línea de resumen para cada grupo de disponibilidad para el que la instancia del servidor conectado hospeda una réplica. Este panel muestra las columnas siguientes.  
  
 **Nombre del grupo de disponibilidad**  
 El nombre de un grupo de disponibilidad para el que la instancia del servidor conectado hospeda una réplica.  
  
 **Instancia principal**  
 Nombre de la instancia de servidor que hospeda la réplica de disponibilidad del grupo de disponibilidad.  
  
 **Modo de conmutación por error**  
 Muestra el modo de conmutación por error para el que se configura la réplica. Los valores de modo de conmutación por error posibles son:  
  
-   **Automática**. Indica que una o varias réplicas están en modo de conmutación por error automática.  
  
-   **Manual**. Indica que ninguna réplica está en modo de conmutación por error automática.  
  
 **Problemas**  
 Haga clic en el vínculo **Problemas** para abrir documentación de solución de problemas relativa a un problema determinado. Para obtener una lista de todos los problemas de directivas de AlwaysOn, vea [directivas de AlwaysOn para problemas operativos con grupos de disponibilidad AlwaysOn (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).  
  
> [!TIP]  
>  Haga clic en los encabezados de columna para ordenar la información de grupos de disponibilidad por nombre de grupo de disponibilidad, instancia principal, modo de conmutación por error o problema.  
  
##  <a name="availability-group-details"></a><a name="AvGroupDetails"></a> Detalles de grupos de disponibilidad  
 Se muestra la información detallada siguiente para el grupo de disponibilidad seleccionado de la pantalla de resumen:  
  
 **Estado de grupo de disponibilidad**  
 Muestra el estado de mantenimiento del grupo de disponibilidad.  
  
 **Primary instance**  
 Nombre de la instancia de servidor que hospeda la réplica de disponibilidad del grupo de disponibilidad.  
  
 **Failover mode**  
 Muestra el modo de conmutación por error para el que se configura la réplica. Los valores de modo de conmutación por error posibles son:  
  
-   **Automática**. Indica que una o varias réplicas están en modo de conmutación por error automática.  
  
-   **Manual**. Indica que ninguna réplica está en modo de conmutación por error automática.  
  
 **Estado de clúster**  
 Nombre y estado del clúster donde la instancia del servidor conectado y el grupo e disponibilidad es un nodo de miembro.  
  
##  <a name="availability-replica-details"></a><a name="AvReplicaDetails"></a> Detalles de la réplica de disponibilidad  
 El panel **Réplica de disponibilidad** muestra las columnas siguientes:  
  
 **Nombre**  
 El nombre de la instancia de servidor que hospeda la réplica de disponibilidad. Esta columna se muestra de forma predeterminada.  
  
 **Rol**  
 Indica el rol actual de la réplica de disponibilidad, **Principal** o **Secundaria**. Para más información sobre los roles de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vea [Información general de los grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md). Esta columna se muestra de forma predeterminada.  
  
 **Modo de conmutación por error**  
 Muestra el modo de conmutación por error para el que se configura la réplica. Los valores de modo de conmutación por error posibles son:  
  
-   **Automática**. Indica que una o varias réplicas están en modo de conmutación por error automática.  
  
-   **Manual**. Indica que ninguna réplica está en modo de conmutación por error automática.  
  
 **Estado de sincronización**  
 Indica si una réplica secundaria está sincronizada actualmente con la réplica principal. Esta columna se muestra de forma predeterminada. Los valores posibles son:  
  
-   **No sincronizado**. Una o más bases de datos de la réplica no están sincronizadas todavía no se han unido al grupo de disponibilidad.  
  
-   **Sincronizando**. Una o más bases de datos de la réplica se están sincronizando.  
  
-   **Sincronizado**. Todas las bases de datos de la réplica secundaria están sincronizadas con las bases de datos principales correspondientes en la réplica principal actual, si hay alguna, o en la última réplica principal.  
  
    > [!NOTE]  
    >  En modo de rendimiento, la base de datos nunca está en estado sincronizado.  
  
-   **Null**. Estado desconocido. Este valor aparece cuando la instancia del servidor local no puede comunicarse con el clúster de conmutación por error de WSFC (es decir, el nodo local no forma parte del quórum de WSFC).  
  
 **Problemas**  
 Muestra el nombre del problema. Este valor se muestra de forma predeterminada. Para obtener una lista de todos los problemas de directivas de AlwaysOn, vea [directivas de AlwaysOn para problemas operativos con grupos de disponibilidad AlwaysOn (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).  
  
 **Modo de disponibilidad**  
 Indica la propiedad de réplica que se establece por separado para cada réplica de disponibilidad. Este valor está oculto de forma predeterminada. Los valores posibles son:  
  
-   **Asincrónica**. La réplica secundaria nunca se sincroniza con la réplica principal.  
  
-   **Sincrónicos**. En la puesta al día de la base de datos principal, una base de datos secundaria entra en este estado permanece al día mientras continúe la sincronización de datos para la base de datos.  
  
 **Modo de conexión principal**  
 Indica el modo que se usa para conectarse a la réplica principal.  Este valor está oculto de forma predeterminada.  
  
 **Modo de conexión secundaria**  
 Indica el modo que se usa para conectarse a la réplica secundaria.  Este valor está oculto de forma predeterminada.  
  
 **Estado de conexión**  
 Indica si la réplica secundaria está conectada actualmente a la réplica principal. Esta columna está oculta de forma predeterminada. Los valores posibles son:  
  
-   **Desconectado**. En el caso de una réplica de disponibilidad remota, indica que está desconectada de la réplica de disponibilidad local. La respuesta de la réplica local al estado Desconectado depende de su rol, del siguiente modo:  
  
    -   En la réplica principal, si una réplica secundaria está desconectada, las bases de datos secundarias se marcan como **No sincronizadas** en la réplica principal y la réplica principal espera a que la réplica secundaria vuelva a conectarse.  
  
    -   En la réplica secundaria, cuando detecta que está desconectada, intenta volver a conectarse a la réplica principal.  
  
-   **Conectado**. Una réplica de disponibilidad remota que está conectada actualmente a la réplica local.  
  
 **Estado operativo**  
 Indica el estado operativo actual de la réplica secundaria. Este valor está oculto de forma predeterminada. Los valores posibles son:  
  
 **0**. Conmutación por error pendiente  
  
 **1**. Pendiente  
  
 **2**. En línea  
  
 **3**. Sin conexión  
  
 **4**. Error  
  
 **5**. No se pudo establecer quórum  
  
 **Null**. La réplica no es local  
  
 **Nº del último error de conexión**  
 Número del último error de conexión.  Este valor está oculto de forma predeterminada.  
  
 **Descripción del último error de conexión**  
 Descripción del último error de conexión.  Este valor está oculto de forma predeterminada.  
  
 **Marca de tiempo del último error de conexión**  
 Marca de tiempo del último error de conexión. Este valor está oculto de forma predeterminada.  
  
> [!NOTE]  
>  Para obtener más información sobre los contadores de rendimiento para réplicas de disponibilidad, vea [SQL Server, réplica de disponibilidad](../../../relational-databases/performance-monitor/sql-server-availability-replica.md).  
  
##  <a name="to-group-availability-group-information"></a><a name="AvDbDetails"></a> Para agrupar la información del grupo de disponibilidad  
 Para agrupar la información, haga clic en **Agrupar por**y seleccione una de las opciones siguientes:  
  
-   **Réplicas de disponibilidad**  
  
-   **Bases de datos de disponibilidad**  
  
-   **Estado de sincronización**  
  
-   **Preparación para la conmutación por error**  
  
-   **Problemas**  
  
 El panel que muestra que muestra la información agrupada tiene las siguientes columnas:  
  
 **Nombre**  
 El nombre de la base de datos de disponibilidad. Este valor se muestra de forma predeterminada.  
  
 **Réplica**  
 El nombre de la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que hospeda la réplica de disponibilidad. Este valor se muestra de forma predeterminada.  
  
 **Estado de sincronización**  
 Indica si la base de datos de disponibilidad está sincronizada actualmente con la réplica principal. Este valor se muestra de forma predeterminada. Los posibles estados de sincronización son los siguientes:  
  
-   **No se están sincronizando**  
  
    -   En el rol principal, indica que la base de datos no está lista para sincronizar su registro de transacciones con las bases de datos secundarias correspondientes.  
  
    -   En una base de datos secundaria, indica que la base de datos no ha iniciado la sincronización del registro debido a un problema de conexión, se está suspendiendo o está pasando por estados de transición durante el inicio o en una conmutación de roles.  
  
-   **Sincronizando**.  
  
     En una réplica principal:  
  
    -   En una base de datos principal, indica que esta base de datos está lista para aceptar una solicitud de examen de una base de datos secundaria.  
  
    -   En una réplica secundaria, indica que hay en curso un movimiento de datos activo para esa base de datos secundaria.  
  
     En una réplica secundaria, indica que hay en curso un movimiento de datos activo para esa réplica.  
  
-   **Sincronizado**.  
  
     Para una base de datos principal, indica que al menos una base de datos secundaria está sincronizada.  
  
     Para una base de datos secundaria, indica que la base de datos está sincronizada con la base de datos principal correspondiente.  
  
-   **Revirtiendo**.  
  
     Indica la fase en el proceso de reversión cuando una base de datos secundaria está obteniendo activamente páginas de la base de datos principal.  
  
    > [!CAUTION]  
    >  Cuando una base de datos está en estado REVERTING, la acción de forzar una conmutación por error a la réplica secundaria puede dejar esa base de datos en un estado en el que no se pueda iniciar.  
  
-   **Inicializando**  
  
     Indica la fase de reversión cuando el registro de transacciones necesario para la puesta al día de una base de datos secundaria respecto al LSN de reversión se envía y se protege en una réplica secundaria.  
  
    > [!CAUTION]  
    >  Cuando una base de datos está en estado INITIALIZING, la acción de forzar una conmutación por error a la réplica secundaria dejará siempre esa base de datos en un estado en el que no se podrá iniciar.  
  
 **Preparación para la conmutación por error**  
 Indica qué réplica de disponibilidad puede ser objeto de conmutación por error con o sin pérdida potencial de datos. Esta columna se muestra de forma predeterminada. Los valores posibles son:  
  
-   **Pérdida de datos**  
  
-   **No se produce pérdida de datos**  
  
 **Issues**  
 Muestra el nombre del problema. Esta columna se muestra de forma predeterminada. Los valores posibles son:  
  
-   **Advertencias**. Haga clic para mostrar los umbrales y problemas de advertencias.  
  
-   **Crítico**. Haga clic para mostrar los problemas críticos.  
  
 Para obtener una lista de todos los problemas de directivas de AlwaysOn, vea [directivas de AlwaysOn para problemas operativos con grupos de disponibilidad AlwaysOn (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).  
  
 **Suspendido**  
 Indica si la base de datos está **Suspendida** o se ha **Reanudado**. Este valor está oculto de forma predeterminada.  
  
 **Motivo de suspensión**  
 Indica la razón del estado suspendido. Este valor está oculto de forma predeterminada.  
  
 **Pérdida de datos calculada (segundos)**  
 Indica la diferencia de tiempo de la última entrada del registro de transacciones de la réplica principal y la réplica secundaria. Si se produce un error en la réplica principal, se perderán todas las entradas del registro de transacciones de la ventana de tiempo. Este valor está oculto de forma predeterminada.  
  
 **Tiempo de recuperación calculado (segundos)**  
 Indica el tiempo en segundos necesario para rehacer el tiempo de puesta al día. El *tiempo de puesta al día* es el tiempo que tardará la réplica secundaria en realizar la puesta la día con la réplica principal. Este valor está oculto de forma predeterminada.  
  
 **Rendimiento de sincronización (segundos)**  
 Indica el tiempo en segundos necesario para la sincronización entre las réplicas principal y secundaria. Este valor está oculto de forma predeterminada.  
  
 **Rendimiento de sincronización (KB)**  
 Indica la cantidad de entradas de registro en los archivos de registro de la base de datos principal que no se han enviado a la réplica secundaria. Este valor está oculto de forma predeterminada.  
  
 **Tasa de envío del registro (KB/seg)**  
 Indica la velocidad en KB por segundo a la que las entradas de registro se envían a la réplica secundaria. Este valor está oculto de forma predeterminada.  
  
 **Tamaño de la cola Rehacer (KB)**  
 Indica la cantidad de entradas de registro en los archivos de registro de la réplica secundaria que no se han rehecho todavía. Este valor está oculto de forma predeterminada.  
  
 **Tasa de puesta al día (KB/seg)**  
 Indica la velocidad en KB por segundo a la que las entradas de registro se están rehaciendo. Este valor está oculto de forma predeterminada.  
  
 **Tasa de envío de secuencia de archivos (KB/seg)**  
 Indica la velocidad de la secuencia de archivos en KB por segundo a la se envían las transacciones a la réplica. Este valor está oculto de forma predeterminada.  
  
 **LSN de fin de registro**  
 Indica el número de secuencia de registro (LSN) real que corresponde a la última entrada de registro en la memoria caché del registro en las réplicas principal y secundaria. Este valor está oculto de forma predeterminada.  
  
 **LSN de recuperación**  
 Indica el final del registro de transacciones antes de que la réplica escriba nuevas entradas de registro después de la recuperación o la conmutación por error de la réplica principal. Este valor está oculto de forma predeterminada.  
  
 **LSN de truncamiento**  
 Indica el valor mínimo de truncamiento del registro para la réplica principal. Este valor está oculto de forma predeterminada.  
  
 **LSN de última confirmación**  
 Indica el LSN real correspondiente al último registro de confirmación del registro de transacciones. Este valor está oculto de forma predeterminada.  
  
 **Última hora de confirmación**  
 Indica la hora correspondiente al último registro de confirmación. Este valor está oculto de forma predeterminada.  
  
 **Último LSN enviado**  
 Indica el punto en el que todos los bloques de registro han sido enviados por la réplica principal. Este valor está oculto de forma predeterminada.  
  
 **Última hora de envío**  
 Indica la hora a la que se envió el último bloque de registro. Este valor está oculto de forma predeterminada.  
  
 **Último LSN recibido**  
 Indica el punto en el que todos los bloques de registro han sido recibidos por la réplica secundaria que hospeda la base de datos secundaria. Este valor está oculto de forma predeterminada.  
  
 **Última hora de recepción**  
 Indica el momento en que el identificador del bloque de registro del último mensaje recibido se leyó en la réplica secundaria. Este valor está oculto de forma predeterminada.  
  
 **Último LSN protegido**  
 Indica el punto en el que todas las entradas de registro se han vaciado en el disco de la réplica secundaria. Este valor está oculto de forma predeterminada.  
  
 **Última hora de protección**  
 Indica la hora a la que el identificador de bloque de registro se recibió para el último LSN protegido en la réplica secundaria. Este valor está oculto de forma predeterminada.  
  
 **Último LSN rehecho**  
 Indica el LSN real de la entrada de registro que se ha rehecho por última vez en la réplica secundaria. Este valor está oculto de forma predeterminada.  
  
 **Última hora de rehacer**  
 Indica la hora en que la última entrada de registro se rehízo en la base de datos secundaria. Este valor está oculto de forma predeterminada.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tareas relacionadas  
  
-   [Usar directivas de AlwaysOn para ver el estado de un grupo de disponibilidad &#40;SQL Server&#41;](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a>Consulte también  
 [sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)   
 [Supervisión de los grupos de disponibilidad &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)  
  
  
