---
title: Página seleccionar sincronización de datos iniciales (asistentes para grupos de disponibilidad AlwaysOn) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.selectinitialdatasync.f1
- sql12.swb.adddatabasewizard.selectinitialdatasync.f1
- sql12.swb.newagwizard.selectinitialdatasync.f1
ms.assetid: 457b1140-4819-4def-8f7c-54a406e6db12
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 20f7d8fbe6f885136e030c80719f2e16d1c689f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87749485"
---
# <a name="select-initial-data-synchronization-page-alwayson-availability-group-wizards"></a>Página Seleccionar sincronización de datos iniciales (asistentes para grupos de disponibilidad AlwaysOn)
  Use la página de AlwaysOn **Seleccionar sincronización de datos iniciales** para indicar sus preferencias para la sincronización de datos inicial de las nuevas bases de datos secundarias. Esta página es compartida por tres asistentes: [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)], el [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] y el [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)].  
  
 Las opciones posibles son **Completa**, **Solo unión**u **Omitir la sincronización de datos iniciales**. Antes de seleccionar **Completa** o **Solo unión** asegúrese de que el entorno cumpla los requisitos previos.  
  

  
##  <a name="recommendations"></a><a name="Recommendations"></a> Recomendaciones  
  
-   Suspenda las tareas de copia de seguridad de registros para las bases de datos principales durante la sincronización de datos inicial.  
  
-   Para una base de datos grande, las operaciones de copias de seguridad y restauración completa pueden tardar mucho tiempo y consumir gran cantidad de recursos extensos. En esos casos, se recomienda que usted mismo prepare las bases de datos secundarias. Para obtener más información, vea [Para preparar las bases de datos secundarias manualmente](#PrepareSecondaryDbs), más adelante en este tema.  
  
-   La sincronización de datos inicial completa requiere especificar un recurso compartido de red. Antes de utilizar un asistente para realizar la sincronización de datos iniciales completa, se recomienda implementar un plan de seguridad para los permisos de acceso en la carpeta del recurso compartido de red. Esta precaución es importante porque cualquiera que tenga un permiso de lectura (READ) en la carpeta puede tener acceso datos potencialmente datos confidenciales del archivo de copia de seguridad. Además, para proteger su operaciones de copias de seguridad y restauración, se recomienda proteger los canales de red entre todas las instancias de servidor que hospedan una réplica de disponibilidad y la carpeta del recurso compartido de red.  
  
     Si las operaciones de copia de seguridad y restauración deben estar muy protegidas, se recomienda seleccionar la opción **Solo unión** u **Omitir la sincronización de datos iniciales** .  
  
##  <a name="full"></a><a name="Full"></a>Total  
 Para cada base de datos principal, la opción **Completa** realiza varias operaciones en un flujo de trabajo: crear una copia de seguridad completa y de registros de la base de datos principal, crear las bases de datos secundarias correspondientes restaurando estas copias de seguridad en cada instancia de servidor que está hospedando una réplica secundaria y unir cada base de datos secundaria al grupo de disponibilidad.  
  
 Seleccione esta opción solo si su entorno cumple los requisitos previos para utilizar la sincronización de datos inicial completa y desea que el asistente inicie automáticamente la sincronización de datos.  
  
 **Requisitos previos para usar la sincronización de datos inicial completa**  
  
-   Todas las rutas de acceso de archivos de base de datos deben ser idénticas en todas las instancias de servidor que hospedan una réplica para el grupo de disponibilidad.  
  
    > [!NOTE]  
    >  Si las rutas de acceso de copias de seguridad y restauración difieren entre la instancia del servidor donde se ejecuta el asistente y cualquier instancia de servidor que vaya a hospedar una replicación secundaria. Las operaciones de copia de seguridad y restauración deben realizarse manualmente mediante la opción MOVE. Para obtener más información, vea [Para preparar las bases de datos secundarias manualmente](#PrepareSecondaryDbs), más adelante en este tema.  
  
-   Ningún nombre de base de datos principal puede existir en ninguna instancia de servidor que hospede una réplica secundaria. Esto significa que ninguna de las nuevas bases de datos secundarias puede existir todavía.  
  
-   Tendrá que especificar un recurso compartido de red para que el asistente cree y obtenga acceso a las copias de seguridad. Para la réplica principal, la cuenta usada para iniciar el [!INCLUDE[ssDE](../../../includes/ssde-md.md)] debe tener permisos del sistema de archivos de lectura y escritura en un recurso compartido de red. Para las réplicas secundarias, la cuenta debe tener permiso de lectura en el recurso compartido de red.  
  
    > [!IMPORTANT]  
    >  Las copias de seguridad de registros serán parte de la cadena de copias de seguridad de registros. Almacene adecuadamente los archivos de copia de seguridad del registro.  
  
 **Si los requisitos previos no se cumplen**  
  
 El asistente no puede crear las bases de datos secundarias para este grupo de disponibilidad. Para obtener información sobre cómo prepararlas, vea [Para preparar las bases de datos secundarias manualmente](#PrepareSecondaryDbs), más adelante en este tema.  
  
 **Si los requisitos previos se cumplen**  
  
 Si todos estos requisitos previos se cumplen y desea que el asistente realice la sincronización de datos inicial completa, seleccione la opción **Completo** y especifique un recurso compartido de red. Esto hará que el asistente cree la base de datos completa y de registros de cada base de datos seleccionada y coloque estas copias de seguridad en el recurso compartido de red que especifique. Después, en cada instancia de servidor que hospeda una de las nuevas réplicas secundarias, el asistente creará las bases de datos secundarias restaurando las copias de seguridad utilizando RESTORE WITH NORECOVERY. Después de crear cada una de las bases de datos secundarias, el asistente unirá la nueva base de datos secundaria al grupo de disponibilidad. En cuanto se une una base de datos secundaria, se inician las sincronizaciones de datos en ella.  
  
 **Especifique una ubicación de red compartida accesible por todas las réplicas**  
 Para crear y restaurar copias de seguridad, el asistente requiere que se especifique un recurso compartido de red. La cuenta utilizada para iniciar [!INCLUDE[ssDE](../../../includes/ssde-md.md)] en cada instancia de servidor que hospedará una réplica de disponibilidad debe tener permisos de sistema de archivos de lectura/escritura en el recurso compartido de red.  
  
> [!IMPORTANT]  
>  Las copias de seguridad de registros serán parte de la cadena de copias de seguridad de registros. Almacene adecuadamente los archivos de copia de seguridad.  
  
##  <a name="join-only"></a><a name="Joinonly"></a>Solo unirse  
 Seleccione esta opción solo si las nuevas bases de datos secundarias ya existen en cada instancia de servidor que hospeda una réplica secundaria del grupo de disponibilidad. Para obtener información sobre cómo preparar las bases de datos secundarias, vea la sección [Para preparar las bases de datos secundarias manualmente](#PrepareSecondaryDbs), más adelante en esta sección.  
  
 Si selecciona **Solo unión**, el asistente intentará unir cada base de datos secundaria existente al grupo de disponibilidad.  
  
## <a name="skip-initial-data-synchronization"></a>Omitir la sincronización de datos iniciales  
 Seleccione esta opción si desea realizar sus propias copias de seguridad de bases de datos y registros de cada base de datos principal, y restaurarlas en cada instancia del servidor que hospeda una réplica secundaria. Después de salir del asistente, tendrá que unir todas las base de datos secundaria en todas las réplicas secundarias.  
  
> [!NOTE]  
>  Para más información, vea [Iniciar el movimiento de datos en una base de datos secundaria AlwaysOn &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).  
  
##  <a name="to-prepare-secondary-databases-manually"></a><a name="PrepareSecondaryDbs"></a>Para preparar las bases de datos secundarias manualmente  
 Para preparar las bases de datos secundarias independientemente de cualquier asistente de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] , puede utilizar cualquiera de los métodos siguientes:  
  
-   Restaure manualmente una copia de seguridad reciente de la base de datos principal utilizando RESTORE WITH NORECOVERY y restaure después cada copia de seguridad de registros posterior utilizando RESTORE WITH NORECOVERY. Si las bases de datos principal y secundaria tienen distintas rutas de acceso, debe utilizar la opción WITH MOVE. Realice esta secuencia de restauración en cada instancia del servidor que hospeda una réplica secundaria del grupo de disponibilidad.  Puede utilizar [!INCLUDE[tsql](../../../includes/tsql-md.md)] o PowerShell para realizar este operaciones de copias de seguridad y restauración.  
  
     **Para obtener más información:**  
  
     [Preparar manualmente una base de datos secundaria para un grupo de disponibilidad &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   Si va a agregar una o varias bases de datos principales de trasvase de registros en un grupo de disponibilidad, es posible que pueda migrar una o varias de sus bases de datos secundarias correspondientes de los grupos de trasvase de registros a [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Para obtener más información, consulte [requisitos previos para migrar desde el trasvase de registros a Grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md).  
  
    > [!NOTE]  
    >  Después de crear todas las bases de datos secundarias para el grupo de disponibilidad, si desea realizar copias de seguridad en las réplicas secundarias, deberá configurar de nuevo la preferencia de copia de seguridad automatizada del grupo de disponibilidad.  
  
     **Para obtener más información:**  
  
     [Requisitos previos para la migración desde el trasvase de registros a Grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)  
  
     [Configurar la copia de seguridad en réplicas de disponibilidad &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
 Después de crear una base de datos secundaria, aplíquele todas las copias de seguridad de registros actuales.  
  
 Opcionalmente, puede preparar todas las bases de datos secundarias antes de ejecutar el asistente. Entonces, en la página **Especificar la sincronización de datos iniciales** del asistente, seleccione **Solo unión** para unir automáticamente las nuevas bases de datos secundarias al grupo de disponibilidad.  
  
##  <a name="related-tasks"></a><a name="LaunchWiz"></a> Tareas relacionadas  
  
-   [Usar el cuadro de diálogo Nuevo grupo de disponibilidad &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Usar el Asistente para agregar una réplica al grupo de disponibilidad &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Usar el Asistente para agregar una base de datos al grupo de disponibilidad &#40;SQL Server Management Studio&#41;](availability-group-add-database-to-group-wizard.md)  
  
-   [Usar el Asistente para grupo de disponibilidad de conmutación por error &#40;SQL Server Management Studio&#41;](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Iniciar el movimiento de datos en una base de datos secundaria AlwaysOn &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)  
  
-   [Combinar una base de datos secundaria con un grupo de disponibilidad &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Usar el cuadro de diálogo Nuevo grupo de disponibilidad &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
## <a name="see-also"></a>Consulte también  
 [Información general de Grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
  
