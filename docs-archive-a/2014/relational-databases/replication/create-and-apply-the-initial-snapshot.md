---
title: Creación y aplicación de la instantánea inicial | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], creating
- snapshot replication [SQL Server], initial snapshots
ms.assetid: 742727a1-5189-44ec-b3ae-6fd7aa1f5347
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b7ac008fe139adf55376bb50fbf60dddcd6b9ae5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663407"
---
# <a name="create-and-apply-the-initial-snapshot"></a>Crear y aplicar la instantánea inicial
  En este tema se describe cómo crear y aplicar la instantánea inicial en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]o Replication Management Objects (RMO). Las publicaciones de mezcla que usan filtros con parámetros necesitan una instantánea de dos partes. Para más información, consulte [Crear una instantánea para una publicación de mezcla con filtros con parámetros](create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
 **En este tema**  
  
-   **Para crear y aplicar la instantánea inicial con:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Replication Management Objects (RMO)](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Uso de SQL Server Management Studio  
 De forma predeterminada, si se está ejecutando el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , el Agente de instantáneas genera una instantánea inmediatamente después de que se cree una publicación con el Asistente para nueva publicación. A continuación, el Agente de distribución (para la replicación de instantáneas y transaccional) o el Agente de mezcla (para las suscripciones de mezcla) la aplican a todas las suscripciones. Las instantáneas también se pueden generar mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] y el Monitor de replicación. Para información sobre cómo iniciar el Monitor de replicación, vea [Iniciar el Monitor de replicación](monitor/start-the-replication-monitor.md).  
  
#### <a name="to-create-a-snapshot-in-management-studio"></a>Para crear una instantánea en Management Studio  
  
1.  Conéctese al publicador en [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]y luego expanda el nodo del servidor.  
  
2.  Expanda la carpeta **Replicación** y, a continuación, expanda la carpeta **Publicaciones locales** .  
  
3.  Haga clic con el botón secundario en la publicación para la que desee crear una instantánea y, a continuación, haga clic en **Ver estado del agente de instantáneas**.  
  
4.  En el cuadro de diálogo **Ver estado del Agente de instantáneas: \<Publication>** , haga clic en **Iniciar**.  
  
 Cuando el Agente de instantáneas termina de generar la instantánea, aparece un mensaje del tipo "[100%] Se ha generado una instantánea de 17 artículos".  
  
#### <a name="to-create-a-snapshot-in-replication-monitor"></a>Para crear una instantánea en el Monitor de replicación  
  
1.  En el Monitor de replicación, expanda un grupo de publicador en el panel izquierdo y, a continuación, expanda un publicador.  
  
2.  Haga clic con el botón secundario en la publicación para la que desee crear una instantánea y, a continuación, haga clic en **Generar instantánea**.  
  
3.  Para ver el estado del Agente de instantáneas, haga clic en la pestaña **Agentes** . Para obtener información más detallada, haga clic con el botón secundario en el Agente de instantáneas en la cuadrícula y, a continuación, haga clic en **Ver detalles**.  
  
#### <a name="to-apply-a-snapshot"></a>Para aplicar una instantánea  
  
1.  Una vez generada la instantánea, se aplica mediante la sincronización de la suscripción con el Agente de distribución o el Agente de mezcla:  
  
    -   Si el agente se ejecuta de forma continua (valor predeterminado para la replicación transaccional), la instantánea se aplica inmediatamente después de haberse generado.  
  
    -   Si el agente se ejecuta según una programación, la instantánea se aplica la siguiente vez que está programada la ejecución del agente.  
  
    -   Si el agente se ejecuta a petición, se aplica la siguiente vez que se ejecuta el agente.  
  
     Para obtener más información acerca de cómo sincronizar suscripciones, vea [Synchronize a Push Subscription](synchronize-a-push-subscription.md) y [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Usar Transact-SQL  
 Las instantáneas iniciales se pueden crear mediante programación o creando y ejecutando un trabajo del Agente de instantáneas o ejecutando el archivo ejecutable Agente de instantáneas desde un archivo por lotes. Una vez generada una instantánea inicial, se transfiere y se aplica en el suscriptor cuando se sincroniza la suscripción por primera vez. Si ejecuta el Agente de instantáneas desde un símbolo del sistema o un archivo por lotes, necesitará volver a ejecutar el agente cada vez que la instantánea existente deje de ser válida.  
  
> [!IMPORTANT]  
>  Cuando sea posible, pida a los usuarios que proporcionen credenciales de seguridad en tiempo de ejecución. Si debe almacenar las credenciales en un archivo de script, proteja el archivo para evitar el acceso no autorizado.  
  
#### <a name="to-create-and-run-a-snapshot-agent-job-to-generate-the-initial-snapshot"></a>Para crear y ejecutar un trabajo del Agente de instantáneas que genere la instantánea inicial  
  
1.  Cree una publicación de instantáneas, transaccional o de combinación. Para obtener más información, vea [Crear una suscripción](publish/create-a-publication.md).  
  
2.  Ejecute [sp_addpublication_snapshot &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql). Especifique **@publication** y los parámetros siguientes:  
  
    -   **@job_login, que especifica** las credenciales de autenticación de Windows con las que se ejecuta el Agente de instantáneas en el distribuidor.  
  
    -   **@job_password**, que es la contraseña para las credenciales de Windows proporcionadas.  
  
    -   (Opcional) El valor **0** para **@publisher_security_mode** si el agente va a utilizar autenticación de SQL Server para conectarse al publicador. En este caso, también debe especificar la información de inicio de sesión de autenticación de SQL Server para **@publisher_login** y **@publisher_password** .  
  
    -   (Opcional) Un programa de sincronización para el trabajo del Agente de instantáneas. Para obtener más información, consulte [Specify Synchronization Schedules](specify-synchronization-schedules.md).  
  
    > [!IMPORTANT]  
    >  Al configurar un publicador con un distribuidor remoto, los valores suministrados para todos los parámetros, incluidos *job_login* y *job_password*, se envían al distribuidor como texto sin formato. Antes de ejecutar este procedimiento almacenado, se recomienda cifrar la conexión entre el publicador y su distribuidor remoto. Para obtener más información, vea [Habilitar conexiones cifradas en el motor de base de datos &#40;Administrador de configuración de SQL Server&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
3.  Agregue artículos a la publicación. Para más información, consulte [Define an Article](publish/define-an-article.md).  
  
4.  En el publicador de la base de datos de publicación, ejecute [sp_startpublication_snapshot &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-startpublication-snapshot-transact-sql) especificando el valor de **@publication** del paso 1.  
  
#### <a name="to-run-the-snapshot-agent-to-generate-the-initial-snapshot"></a>Para ejecutar el Agente de instantáneas y generar una instantánea inicial  
  
1.  Cree una publicación de instantáneas, transaccional o de combinación. Para obtener más información, vea [Crear una suscripción](publish/create-a-publication.md).  
  
2.  Agregue artículos a la publicación. Para más información, consulte [Define an Article](publish/define-an-article.md).  
  
3.  Desde el símbolo del sistema o en un archivo por lotes, inicie el [Replication Snapshot Agent](agents/replication-snapshot-agent.md) ejecutando **snapshot.exe**y especifique los argumentos de la línea de comandos siguientes:  
  
    -   **-Publication**  
  
    -   **-Publisher**  
  
    -   **-Distributor**  
  
    -   **-PublisherDB**  
  
    -   **-ReplicationType**  
  
     Si está usando la autenticación de SQL Server, también debe especificar los argumentos siguientes:  
  
    -   **-DistributorLogin**  
  
    -   **-DistributorPassword**  
  
    -   **-DistributorSecurityMode** = **0**  
  
    -   **-PublisherLogin**  
  
    -   **-PublisherPassword**  
  
    -   **-PublisherSecurityMode** = **0**  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> Ejemplos (Transact-SQL)  
 Este ejemplo muestra cómo crear una publicación transaccional y agregar un trabajo del Agente de instantáneas para la nueva publicación (utilizando variables de scripting de **sqlcmd** ). En el ejemplo también se inicia el trabajo.  
  
 [!code-sql[HowTo#sp_trangenerate_snapshot](../../snippets/tsql/SQL15/replication/howto/tsql/createtranpubinitialsnapshot.sql#sp_trangenerate_snapshot)]  
  
 En este ejemplo se crea una publicación de combinación y se agrega un trabajo del Agente de instantáneas (utilizando variables de **sqlcmd** ) para la publicación. En este ejemplo también se inicia el trabajo.  
  
 [!code-sql[HowTo#sp_mergegenerate_snapshot](../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubinitialsnapshot.sql#sp_mergegenerate_snapshot)]  
  
 Los siguientes argumentos de la línea de comandos inician el Agente de instantáneas para que genere la instantánea para una publicación de combinación.  
  
> [!NOTE]  
>  Los saltos de línea se incluyeron para mejorar la legibilidad. En un archivo por lotes, los comandos se deben realizar en una única línea.  
  
 [!code-sql[HowTo#startmergesnapshot_10](../../snippets/tsql/SQL15/replication/howto/tsql/createmergesnapshot_10.bat)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> Uso de Replication Management Objects (RMO)  
 El Agente de instantáneas genera instantáneas una vez creada la publicación. Puede generar estas instantáneas mediante programación utilizando Replication Management Objects (RMO) y el acceso de código administrado directo a las funcionalidades del agente de replicación. Los objetos que se usan dependen del tipo de replicación. El Agente de instantáneas se puede iniciar sincrónicamente con el objeto <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> o de forma asincrónica con el trabajo de agente. Una vez generada la instantánea inicial, se transfiere y se aplica al suscriptor cuando se sincroniza la suscripción por primera vez. Deberá volver a ejecutar el agente cada vez que la instantánea existente no contenga datos válidos y actualizados. Para obtener más información, vea [Mantener publicaciones](publish/maintain-publications.md).  
  
> [!IMPORTANT]  
>  Cuando sea posible, pida a los usuarios que proporcionen credenciales de seguridad en tiempo de ejecución. Si debe almacenar credenciales, use los [servicios de cifrado](https://go.microsoft.com/fwlink/?LinkId=34733) (en inglés) proporcionados por [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
#### <a name="to-generate-the-initial-snapshot-for-a-snapshot-or-transactional-publication-by-starting-the-snapshot-agent-job-asynchronous"></a>Para generar la instantánea inicial de una publicación transaccional o de instantáneas iniciando el trabajo del Agente de instantáneas (asincrónico)  
  
1.  Cree una conexión al publicador mediante la clase <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Cree una instancia de la clase <xref:Microsoft.SqlServer.Replication.TransPublication>. Establezca las propiedades <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> y <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> para la publicación y la propiedad <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> en la conexión creada en el paso 1.  
  
3.  Llame al método <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> para cargar las propiedades restantes del objeto. Si este método devuelve `false`, significa que las propiedades de publicación del paso 2 se definieron incorrectamente, o bien que la publicación no existe.  
  
4.  Si el valor de <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> es `false`, llame a <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> para crear el trabajo de Agente de instantáneas para esta publicación.  
  
5.  Llame al método <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> para iniciar el trabajo del agente que genera la instantánea inicial de esta publicación.  
  
6.  (Opcional) Cuando el valor de <xref:Microsoft.SqlServer.Replication.TransPublication.SnapshotAvailable%2A> es `true`, la instantánea está disponible para los suscriptores.  
  
#### <a name="to-generate-the-initial-snapshot-for-a-snapshot-or-transactional-publication-by-running-the-snapshot-agent-synchronous"></a>Para generar la instantánea inicial de una publicación transaccional o de instantáneas ejecutando el trabajo del Agente de instantáneas (sincrónico)  
  
1.  Cree una instancia de la clase <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> y establezca las propiedades necesarias siguientes:  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> - nombre del publicador  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> - nombre de la base de datos de publicación  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> - nombre de la publicación  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> - nombre del distribuidor  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> - un valor de <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> para usar la autenticación de Windows al conectarse al publicador o un valor de <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> y valores para <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherLogin%2A> y <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherPassword%2A> para usar la autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] al conectarse al publicador. Se recomienda la autenticación de Windows.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> - un valor de <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> para usar la autenticación de Windows al conectarse al distribuidor o un valor de <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> y valores para <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorLogin%2A> y <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorPassword%2A> para usar la autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] al conectarse al distribuidor. Se recomienda la autenticación de Windows.  
  
2.  Establezca un valor de <xref:Microsoft.SqlServer.Replication.ReplicationType.Transactional> o <xref:Microsoft.SqlServer.Replication.ReplicationType.Snapshot> para <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>.  
  
3.  Llame al método <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A> .  
  
#### <a name="to-generate-the-initial-snapshot-for-a-merge-publication-by-starting-the-snapshot-agent-job-asynchronous"></a>Para generar la instantánea inicial de una publicación de combinación iniciando el trabajo del Agente de instantáneas (asincrónico)  
  
1.  Cree una conexión al publicador mediante la clase <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Cree una instancia de la clase <xref:Microsoft.SqlServer.Replication.MergePublication>. Establezca las propiedades <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> y <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> para la publicación y la propiedad <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> en la conexión creada en el paso 1.  
  
3.  Llame al método <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> para cargar las propiedades restantes del objeto. Si este método devuelve `false`, significa que las propiedades de publicación del paso 2 se definieron incorrectamente, o bien que la publicación no existe.  
  
4.  Si el valor de <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> es `false`, llame a <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> para crear el trabajo de Agente de instantáneas para esta publicación.  
  
5.  Llame al método <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> para iniciar el trabajo del agente que genera la instantánea inicial de esta publicación.  
  
6.  (Opcional) Cuando el valor de <xref:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable%2A> es `true`, la instantánea está disponible para los suscriptores.  
  
#### <a name="to-generate-the-initial-snapshot-for-a-merge-publication-by-running-the-snapshot-agent-synchronous"></a>Para generar la instantánea inicial de una publicación de combinación ejecutando el Agente de instantáneas (sincrónico)  
  
1.  Cree una instancia de la clase <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> y establezca las propiedades necesarias siguientes:  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> - nombre del publicador  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> - nombre de la base de datos de publicación  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> - nombre de la publicación  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> - nombre del distribuidor  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> - un valor de <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> para usar la autenticación de Windows al conectarse al publicador o un valor de <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> y valores para <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherLogin%2A> y <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherPassword%2A> para usar la autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] al conectarse al publicador. Se recomienda la autenticación de Windows.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> - un valor de <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> para usar la autenticación de Windows al conectarse al distribuidor o un valor de <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> y valores para <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorLogin%2A> y <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorPassword%2A> para usar la autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] al conectarse al distribuidor. Se recomienda la autenticación de Windows.  
  
2.  Establezca un valor <xref:Microsoft.SqlServer.Replication.ReplicationType.Merge> para <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>.  
  
3.  Llame al método <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A> .  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> Ejemplos (RMO)  
 Este ejemplo ejecuta sincrónicamente el Agente de instantáneas para generar la instantánea inicial de una publicación transaccional.  
  
 [!code-csharp[HowTo#rmo_GenerateSnapshot](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_generatesnapshot)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateSnapshot](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_generatesnapshot)]  
  
 Este ejemplo inicia asincrónicamente el Agente de instantáneas para generar la instantánea inicial de una publicación transaccional.  
  
 [!code-csharp[HowTo#rmo_GenerateSnapshot_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_generatesnapshot_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateSnapshot_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_generatesnapshot_withjob)]  
  
## <a name="see-also"></a>Consulte también  
 [Create a Publication](publish/create-a-publication.md)   
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Create a Push Subscription](create-a-push-subscription.md)   
 [Specify Synchronization Schedules](specify-synchronization-schedules.md)   
 [Crear y aplicar la instantánea](create-and-apply-the-snapshot.md)   
 [Inicializar una suscripción con una instantánea](initialize-a-subscription-with-a-snapshot.md)   
 [Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md)   
 [Replication Security Best Practices](security/replication-security-best-practices.md)   
 [Replication System Stored Procedures Concepts](concepts/replication-system-stored-procedures-concepts.md)   
 [Usar sqlcmd con variables de script](../scripting/sqlcmd-use-with-scripting-variables.md)  
  
  
