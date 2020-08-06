---
title: Creación de una suscripción de inserción | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- push subscriptions [SQL Server replication], creating
- merge replication subscribing [SQL Server replication], push subscriptions
- subscriptions [SQL Server replication], push
- snapshot replication [SQL Server], subscribing
- transactional replication, subscribing
ms.assetid: adfbbc61-58d1-4330-9ad6-b14ab1142e2b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2195d96f4337cc60ba213deb5e3cc2831d27da76
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87678166"
---
# <a name="create-a-push-subscription"></a>Crear una suscripción de inserción
  En este tema se describe cómo crear una suscripción de inserción en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]o Replication Management Objects (RMO). Para obtener información acerca de cómo crear una suscripción de extracción para un suscriptor que no sea de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vea [crear una suscripción para un suscriptor que no sea de SQL Server](create-a-subscription-for-a-non-sql-server-subscriber.md).  
  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Uso de SQL Server Management Studio  
 Cree una suscripción de inserción en el publicador o en el suscriptor con el Asistente para nuevas suscripciones. Siga las páginas del asistente para:  
  
-   Especificar el publicador y la publicación.  
  
-   Seleccionar dónde se ejecutarán los agentes de replicación. Para una suscripción de inserción, seleccione **Ejecutar todos los agentes en el distribuidor (suscripciones de inserción)** en la página **Ubicación del Agente de distribución** o **Ubicación del Agente de mezcla** , dependiendo del tipo de publicación.  
  
-   Especificar suscriptores y bases de datos de suscripciones.  
  
-   Especifique los nombres de inicio de sesión y las contraseñas que se utilizan para las conexiones realizadas por los agentes de replicación:  
  
    -   Para las suscripciones a publicaciones de instantáneas y transaccionales, especifique las credenciales en la página **Seguridad del Agente de distribución** .  
  
    -   Para las suscripciones a publicaciones de combinación, especifique las credenciales en la página **Seguridad del Agente de mezcla** .  
  
     Para obtener información acerca de los permisos que necesita cada agente, vea [Modelo de seguridad del agente de replicación](security/replication-agent-security-model.md).  
  
-   Especifique una programación de sincronización y cuándo se debe inicializar el suscriptor.  
  
-   Especifique otras opciones para las publicaciones de combinación: el tipo de suscripción y los valores para los filtros con parámetros.  
  
-   Especifique otras opciones para las publicaciones transaccionales que permitan actualizar suscripciones: si los suscriptores deben confirmar los cambios inmediatamente en el publicador o escribirlos en una cola; las credenciales que se emplean para conectarse desde el suscriptor al publicador.  
  
-   Opcionalmente, puede crear un script para la suscripción.  
  
#### <a name="to-create-a-push-subscription-from-the-publisher"></a>Para crear una suscripción de inserción desde el publicador  
  
1.  Conéctese al publicador de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] y expanda el nodo de servidor.  
  
2.  Expanda la carpeta **Replicación** y, a continuación, expanda la carpeta **Publicaciones locales** .  
  
3.  Haga clic con el botón secundario en la publicación en la que desea crear una o varias suscripciones y, a continuación, haga clic en **Nuevas suscripciones**.  
  
4.  Complete las páginas del Asistente para nuevas suscripciones.  
  
#### <a name="to-create-a-push-subscription-from-the-subscriber"></a>Para crear una suscripción de inserción desde el suscriptor  
  
1.  Conéctese al suscriptor en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]y expanda el nodo de servidor.  
  
2.  Expanda la carpeta **Replicación** .  
  
3.  Haga clic con el botón secundario en la carpeta **Suscripciones locales** y, a continuación, haga clic en **Nuevas suscripciones**.  
  
4.  En la página **Publicación** del Asistente para nueva suscripción, seleccione **\<Find SQL Server Publisher>** o **\<Find Oracle Publisher>** en la lista desplegable **Publicador**.  
  
5.  Conéctese al publicador en el cuadro de diálogo **Conectar al servidor** .  
  
6.  Seleccione una publicación en la página **Publicación** .  
  
7.  Complete las páginas del Asistente para nuevas suscripciones.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Usar Transact-SQL  
 Las suscripciones de inserción pueden crearse mediante programación con procedimientos almacenados de replicación. Los procedimientos almacenados que se usen dependerán del tipo de publicación a la que corresponda la suscripción.  
  
> [!IMPORTANT]  
>  Cuando sea posible, pida a los usuarios que proporcionen credenciales de seguridad en tiempo de ejecución. Si debe almacenar las credenciales en un archivo de script, proteja el archivo para evitar el acceso no autorizado.  
  
#### <a name="to-create-a-push-subscription-to-a-snapshot-or-transactional-publication"></a>Para crear una suscripción de inserción para una publicación de instantáneas o transaccional  
  
1.  En el publicador de la base de datos de publicaciones, compruebe que la publicación admita suscripciones de inserción mediante la ejecución de [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).  
  
    -   Si el valor de **allow_push** es **1**, se admiten las suscripciones de inserción.  
  
    -   Si el valor de **allow_push** es **0**, ejecute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), especificando **allow_push** para **@property** y `true` para **@value** .  
  
2.  En el publicador de la base de datos de publicaciones, ejecute [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql). Especifique **@publication** , **@subscriber** y **@destination_db** . Especifique un valor **push** para **@subscription_type**. Para obtener información sobre cómo actualizar suscripciones, vea [crear una suscripción actualizable a una publicación transaccional](publish/create-an-updatable-subscription-to-a-transactional-publication.md) .  
  
3.  En el publicador de la base de datos de publicaciones, ejecute [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql). Especifique lo siguiente:  
  
    -   Los **@subscriber** **@subscriber_db** parámetros, y **@publication** .  
  
    -   Las [!INCLUDE[msCoName](../../includes/msconame-md.md)] credenciales de Windows con las que se ejecuta el agente de distribución en el distribuidor para **@job_login** y **@job_password** .  
  
        > [!NOTE]  
        >  Las conexiones realizadas mediante la autenticación integrada de Windows siempre utilizan las credenciales de Windows especificadas por **@job_login** y **@job_password** . El Agente de distribución siempre realiza la conexión local con el distribuidor mediante la autenticación integrada de Windows. De forma predeterminada, el agente se conectará con el suscriptor mediante la autenticación integrada de Windows.  
  
    -   (Opcional) El valor **0** para **@subscriber_security_mode** y la información de inicio de sesión de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para **@subscriber_login** y **@subscriber_password**. Especifique estos parámetros si necesita usar Autenticación de SQL Server al conectarse al suscriptor.  
  
    -   Una programación para el trabajo del Agente de distribución de esta suscripción. Para obtener más información, consulte [Specify Synchronization Schedules](specify-synchronization-schedules.md).  
  
    > [!IMPORTANT]  
    >  Al crear una suscripción de inserción en un publicador con un distribuidor remoto, los valores suministrados para todos los parámetros, incluidos *job_login* y *job_password*, se envían al distribuidor como texto simple. Antes de ejecutar este procedimiento almacenado, se recomienda cifrar la conexión entre el publicador y su distribuidor remoto. Para obtener más información, vea [Habilitar conexiones cifradas en el motor de base de datos &#40;Administrador de configuración de SQL Server&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
#### <a name="to-create-a-push-subscription-to-a-merge-publication"></a>Para crear una suscripción de inserción para una publicación de combinación  
  
1.  En el publicador de la base de datos de publicaciones, compruebe que la publicación admita suscripciones de inserción mediante la ejecución de [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql).  
  
    -   Si el valor de **allow_push** es **1**, la publicación admite operaciones de inserción.  
  
    -   Si el valor de **allow_push** no es **1**, ejecute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), especificando **allow_push** para **@property** y `true` para **@value** .  
  
2.  En el publicador de la base de datos de publicaciones, ejecute [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql)y especifique los siguientes parámetros:  
  
    -   **@publication**. Éste es el nombre de la publicación.  
  
    -   **@subscriber_type**. Para una suscripción de cliente, especifique **local** y para una suscripción de servidor, especifique **global**.  
  
    -   **@subscription_priority**. Para una suscripción de servidor, especifique una prioridad para la suscripción (de**0,00** a **99,99**).  
  
         Para más información, consulte [Replicación de mezcla avanzada: detección y resolución de conflictos](merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
3.  En el publicador de la base de datos de publicaciones, ejecute [sp_addmergepushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql). Especifique lo siguiente:  
  
    -   Los **@subscriber** **@subscriber_db** parámetros, y **@publication** .  
  
    -   Las credenciales de Windows con las que se ejecuta el Agente de mezcla en el distribuidor para **@job_login** y **@job_password** .  
  
        > [!NOTE]  
        >  Las conexiones realizadas mediante la autenticación integrada de Windows siempre utilizan las credenciales de Windows especificadas por **@job_login** y **@job_password** . El Agente de mezcla siempre realiza la conexión local con el distribuidor mediante la Autenticación integrada de Windows. De forma predeterminada, el agente se conectará con el suscriptor mediante la autenticación integrada de Windows.  
  
    -   (Opcional) El valor **0** para **@subscriber_security_mode** y la información de inicio de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para **@subscriber_login** y **@subscriber_password**. Especifique estos parámetros si necesita usar Autenticación de SQL Server al conectarse al suscriptor.  
  
    -   (Opcional) El valor **0** para **@publisher_security_mode** y la información de inicio de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para **@publisher_login** y **@publisher_password**. Especifique estos valores si necesita usar Autenticación de SQL Server al conectarse al publicador.  
  
    -   Una programación para el Agente de mezcla para la suscripción. Para obtener más información, consulte [Specify Synchronization Schedules](specify-synchronization-schedules.md).  
  
    > [!IMPORTANT]  
    >  Al crear una suscripción de inserción en un publicador con un distribuidor remoto, los valores suministrados para todos los parámetros, incluidos *job_login* y *job_password*, se envían al distribuidor como texto simple. Antes de ejecutar este procedimiento almacenado, se recomienda cifrar la conexión entre el publicador y su distribuidor remoto. Para obtener más información, vea [Habilitar conexiones cifradas en el motor de base de datos &#40;Administrador de configuración de SQL Server&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> Ejemplos (Transact-SQL)  
 El siguiente ejemplo crea una suscripción de inserción en una publicación transaccional. Los valores de inicio de sesión y contraseña se proporcionan en tiempo de ejecución mediante variables de scripting de **sqlcmd** .  
  
 [!code-sql[HowTo#sp_addtranpushsubscription_agent](../../snippets/tsql/SQL15/replication/howto/tsql/createtranpushsub.sql#sp_addtranpushsubscription_agent)]  
  
 El siguiente ejemplo crea una suscripción de inserción en una publicación de combinación. Los valores de inicio de sesión y contraseña se proporcionan en tiempo de ejecución mediante variables de scripting de **sqlcmd** .  
  
 [!code-sql[HowTo#sp_addmergepushsubscriptionagent](../../snippets/tsql/SQL15/replication/howto/tsql/createmergepushsub.sql#sp_addmergepushsubscriptionagent)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> Uso de Replication Management Objects (RMO)  
 Las suscripciones de inserción se pueden crear mediante programación usando Replication Management Objects (RMO). Las clases RMO que se utilizan para crear una suscripción de inserción dependen del tipo de publicación para el que se crea la suscripción.  
  
> [!IMPORTANT]  
>  Cuando sea posible, pida a los usuarios que proporcionen credenciales de seguridad en tiempo de ejecución. Si debe almacenar credenciales, use los [servicios de cifrado](https://go.microsoft.com/fwlink/?LinkId=34733) (en inglés) proporcionados por [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
#### <a name="to-create-a-push-subscription-to-a-snapshot-or-transactional-publication"></a>Para crear una suscripción de inserción para una publicación de instantáneas o transaccional  
  
1.  Cree una conexión al publicador mediante la clase <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Cree una instancia de la clase <xref:Microsoft.SqlServer.Replication.TransPublication> con la conexión de publicador del paso 1. Especifique <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>y <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Llame al método <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Si este método devuelve `false` , las propiedades especificadas en el paso 2 son incorrectas o la publicación no existe en el servidor.  
  
4.  Ejecuta una operación lógica AND bit a bit (`&` en Visual C# y `And` en Visual Basic) entre la propiedad <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> y <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>. Si el resultado es <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None>, establezca <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> en el resultado de una operación lógica OR bit a bit (`|` en Visual C# y `Or` en Visual Basic) entre <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> y <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>. A continuación, llame a <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> para habilitar las suscripciones de inserción.  
  
5.  Si la base de datos de suscripciones no existe, créela con la clase <xref:Microsoft.SqlServer.Management.Smo.Database> . Para obtener más información, consulte [Crear, modificar y eliminar bases de datos](../server-management-objects-smo/tasks/creating-altering-and-removing-databases.md).  
  
6.  Cree una instancia de la clase <xref:Microsoft.SqlServer.Replication.TransSubscription>.  
  
7.  Establezca las siguientes propiedades de la suscripción:  
  
    -   La conexión <xref:Microsoft.SqlServer.Management.Common.ServerConnection> al publicador creada en el paso 1 para <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   El nombre de la base de datos de suscripciones para <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>.  
  
    -   El nombre del suscriptor para <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>.  
  
    -   El nombre de la base de datos de publicaciones para <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>.  
  
    -   El nombre de la publicación para <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>.  
  
    -   Los campos <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> y <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> o <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> de <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> para proporcionar las credenciales para la cuenta de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows con la que se ejecuta el Agente de distribución en el distribuidor. Esta cuenta se utiliza para realizar conexiones locales al distribuidor y conexiones remotas con la autenticación de Windows.  
  
        > [!NOTE]  
        >  No es necesario configurar <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> cuando un miembro del rol fijo de servidor `sysadmin` crea la suscripción; sin embargo, es recomendable. En este caso, el agente suplantará a la cuenta del Agente SQL Server. Para más información, consulte [Modelo de seguridad del agente de replicación](security/replication-agent-security-model.md).  
  
    -   (Opcional) el valor `true` (predeterminado) para <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A> para crear un trabajo del agente que se utiliza para sincronizar la suscripción. Si especifica `false`, la suscripción solo puede sincronizarse mediante programación.  
  
    -   (Opcional) configure los campos <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> y <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> o <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> de <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> si utiliza la autenticación de SQL Server para conectarse al suscriptor.  
  
8.  Llame al método <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> .  
  
    > [!IMPORTANT]  
    >  Al crear una suscripción de inserción en un publicador con un distribuidor remoto, los valores proporcionados para todas las propiedades, incluido <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A>, se envían al distribuidor como texto simple. Debe cifrar la conexión entre el publicador y su distribuidor remoto antes de llamar al método <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> . Para obtener más información, vea [Habilitar conexiones cifradas en el motor de base de datos &#40;Administrador de configuración de SQL Server&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
#### <a name="to-create-a-push-subscription-to-a-merge-publication"></a>Para crear una suscripción de inserción para una publicación de combinación  
  
1.  Cree una conexión al publicador mediante la clase <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Cree una instancia de la clase <xref:Microsoft.SqlServer.Replication.MergePublication> con la conexión de publicador del paso 1. Especifique <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>y <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Llame al método <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Si este método devuelve `false` , las propiedades especificadas en el paso 2 son incorrectas o la publicación no existe en el servidor.  
  
4.  Ejecuta una operación lógica AND bit a bit (`&` en Visual C# y `And` en Visual Basic) entre la propiedad <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> y <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>. Si el resultado es <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None>, establezca <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> en el resultado de una operación lógica OR bit a bit (`|` en Visual C# y `Or` en Visual Basic) entre <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> y <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>. A continuación, llame a <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> para habilitar las suscripciones de inserción.  
  
5.  Si la base de datos de suscripciones no existe, créela con la clase <xref:Microsoft.SqlServer.Management.Smo.Database> . Para obtener más información, consulte [Crear, modificar y eliminar bases de datos](../server-management-objects-smo/tasks/creating-altering-and-removing-databases.md).  
  
6.  Cree una instancia de la clase <xref:Microsoft.SqlServer.Replication.MergeSubscription>.  
  
7.  Establezca las siguientes propiedades de la suscripción:  
  
    -   La conexión <xref:Microsoft.SqlServer.Management.Common.ServerConnection> al publicador creada en el paso 1 para <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   El nombre de la base de datos de suscripciones para <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>.  
  
    -   El nombre del suscriptor para <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>.  
  
    -   El nombre de la base de datos de publicaciones para <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>.  
  
    -   El nombre de la publicación para <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>.  
  
    -   Los campos <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> y <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> o <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> de <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> para proporcionar las credenciales para la cuenta de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows con la que se ejecuta el Agente de mezcla en el distribuidor. Esta cuenta se utiliza para realizar conexiones locales al distribuidor y conexiones remotas con la autenticación de Windows.  
  
        > [!NOTE]  
        >  No es necesario configurar <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> cuando un miembro del rol fijo de servidor `sysadmin` crea la suscripción; sin embargo, es recomendable. En este caso, el agente suplantará a la cuenta del Agente SQL Server. Para más información, consulte [Modelo de seguridad del agente de replicación](security/replication-agent-security-model.md).  
  
    -   (Opcional) el valor `true` (predeterminado) para <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A> para crear un trabajo del agente que se utiliza para sincronizar la suscripción. Si especifica `false`, la suscripción solo puede sincronizarse mediante programación.  
  
    -   (Opcional) configure los campos <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> y <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> o <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> de <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> si utiliza la autenticación de SQL Server para conectarse al suscriptor.  
  
    -   (Opcional) configure los campos <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> y <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> o <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> de <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherSecurity%2A> si utiliza la autenticación de SQL Server para conectarse al publicador.  
  
8.  Llame al método <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> .  
  
    > [!IMPORTANT]  
    >  Al crear una suscripción de inserción en un publicador con un distribuidor remoto, los valores proporcionados para todas las propiedades, incluido <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A>, se envían al distribuidor como texto simple. Debe cifrar la conexión entre el publicador y su distribuidor remoto antes de llamar al método <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> . Para obtener más información, vea [Habilitar conexiones cifradas en el motor de base de datos &#40;Administrador de configuración de SQL Server&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> Ejemplos (RMO)  
 En este ejemplo se crea una suscripción de inserción para una publicación transaccional. Las credenciales de la cuenta de Windows utilizada para ejecutar el trabajo del Agente de distribución se pasan en tiempo de ejecución.  
  
 [!code-csharp[HowTo#rmo_CreateTranPushSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createtranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranPushSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createtranpushsub)]  
  
 En este ejemplo se crea una suscripción de inserción para una publicación de combinación. Las credenciales de la cuenta de Windows utilizada para ejecutar el trabajo del Agente de mezcla se pasan en tiempo de ejecución.  
  
 [!code-csharp[HowTo#rmo_CreateMergePushSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePushSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergepushsub)]  
  
## <a name="see-also"></a>Consulte también  
 [Ver y modificar las propiedades de una suscripción de inserción](view-and-modify-push-subscription-properties.md)   
 [Replication Security Best Practices](security/replication-security-best-practices.md)   
 [Create a Publication](publish/create-a-publication.md)   
 [Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md)   
 [Sincronizar una suscripción de inserción](synchronize-a-push-subscription.md)   
 [Subscribe to Publications](subscribe-to-publications.md)   
 [Usar sqlcmd con variables de script](../scripting/sqlcmd-use-with-scripting-variables.md)  
  
  
