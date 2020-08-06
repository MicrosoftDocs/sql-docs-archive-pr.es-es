---
title: Deshabilitar la publicación y la distribución | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- disabling publishing
- publishing [SQL Server replication], disabling
- distribution disabling [SQL Server replication]
- removing replication
- replication [SQL Server], removing
- disabling replication
- disabling distribution
ms.assetid: 6d4a1474-4d13-4826-8be2-80050fafa8a5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8843dac310d1e023fe7ce63eded02c9e1bed3731
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663392"
---
# <a name="disable-publishing-and-distribution"></a>Deshabilitar la publicación y la distribución
  En este tema se describe cómo deshabilitar la publicación y la distribución en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]o Replication Management Objects (RMO).  
  
 Puede hacer lo siguiente:  
  
-   Eliminar todas las bases de datos del distribuidor.  
  
-   Deshabilitar todos los publicadores que utilizan el distribuidor y eliminar todas las publicaciones en esos publicadores.  
  
-   Eliminar todas las suscripciones a las publicaciones. Los datos de las bases de datos de publicaciones y de suscripciones no se eliminarán; sin embargo, pierden su relación de sincronización con todas las bases de datos de publicaciones. Si desea eliminar los datos del suscriptor, debe hacerlo de forma manual.  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Requisitos previos](#Prerequisites)  
  
-   **Para deshabilitar la publicación y la distribución con:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Replication Management Objects (RMO)](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Requisitos previos  
  
-   Para deshabilitar la publicación y la distribución, todas las bases de datos de distribución y de publicaciones deben estar en línea. Si existe alguna *instantánea de base de datos* para las bases de datos de distribución o de publicaciones, deben quitarse antes de deshabilitar la publicación y distribución. Una instantánea de base de datos es una copia de solo lectura sin conexión de una base de datos y no está relacionada con una instantánea de replicación. Para más información, vea [Instantáneas de base de datos &#40;SQL Server&#41;](../databases/database-snapshots-sql-server.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Uso de SQL Server Management Studio  
 Deshabilite la publicación y la distribución con el Asistente para deshabilitar la publicación y distribución.  
  
#### <a name="to-disable-publishing-and-distribution"></a>Para deshabilitar la publicación y la distribución  
  
1.  Conéctese al publicador o el distribuidor que quiere deshabilitar en [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] y expanda el nodo de servidor.  
  
2.  Haga clic con el botón secundario en la carpeta **Replicación** y, a continuación, haga clic en **Deshabilitar publicación y distribución**.  
  
3.  Siga todos los pasos del Asistente para deshabilitar la publicación y distribución.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Usar Transact-SQL  
 Puede deshabilitarse la publicación y la distribución mediante programación con los procedimientos almacenados de la replicación.  
  
#### <a name="to-disable-publishing-and-distribution"></a>Para deshabilitar la publicación y la distribución  
  
1.  Detenga todos los trabajos relacionados con replicación. Para obtener una lista de nombres de tarea, vea la sección "Seguridad de agentes con el Agente SQL Server" de [Modelo de seguridad del Agente de replicación](security/replication-agent-security-model.md).  
  
2.  En cada suscriptor de la base de datos de suscripciones, ejecute [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) para quitar los objetos de replicación de dicha base de datos. Este procedimiento almacenado no quitará los trabajos de replicación del distribuidor.  
  
3.  En la base de datos de publicación del publicador, ejecute [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) para quitar los objetos de replicación de dicha base de datos.  
  
4.  Si el publicador usa un distribuidor remoto, ejecute [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql).  
  
5.  En el distribuidor, ejecute [sp_dropdistpublisher](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql). Este procedimiento almacenado se debería ejecutar una vez para cada publicador registrado en el distribuidor.  
  
6.  En el distribuidor, ejecute [sp_dropdistributiondb](/sql/relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql) para eliminar la base de datos de distribución. Este procedimiento almacenado se debería ejecutar una vez para cada base de datos de distribución en el distribuidor. Esto también quita cualquier trabajo del Agente de lectura de cola asociado a la base de datos de distribución.  
  
7.  En el distribuidor, ejecute [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql) para quitar la designación de distribuidor del servidor.  
  
    > [!NOTE]  
    >  Si no se quitan todos los objetos de distribución y publicación de replicación antes de ejecutar [sp_dropdistpublisher](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql) y [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql), estos procedimientos devolverán un error. Para quitar todos los objetos relacionados con la replicación cuando se quita un publicador o un distribuidor, el parámetro ** \@ no_checks** debe establecerse en **1**. Si un publicador o un distribuidor está sin conexión o no está accesible, el parámetro ** \@ ignore_distributor** se puede establecer en **1** para que se puedan quitar; sin embargo, cualquier publicación y distribución de objetos restantes debe quitarse manualmente.  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> Ejemplos (Transact-SQL)  
 Este script de ejemplo quita los objetos de replicación de la base de datos de suscripciones.  
  
 [!code-sql[HowTo#sp_removedbreplication](../../snippets/tsql/SQL15/replication/howto/tsql/dropdistpub.sql#sp_removedbreplication)]  
  
 Este script de ejemplo deshabilita la publicación y la distribución en un servidor que sea publicador y distribuidor, y quita la base de datos de distribución.  
  
 [!code-sql[HowTo#sp_DropDistPub](../../snippets/tsql/SQL15/replication/howto/tsql/dropdistpub.sql#sp_dropdistpub)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> Uso de Replication Management Objects (RMO)  
  
#### <a name="to-disable-publishing-and-distribution"></a>Para deshabilitar la publicación y la distribución  
  
1.  Quite todas las suscripciones a las publicaciones que usan el Distribuidor. Para obtener más información, consulte [Delete a Pull Subscription](delete-a-pull-subscription.md) y [Delete a Push Subscription](delete-a-push-subscription.md).  
  
2.  Quite todas las publicaciones que usan el Distribuidor y deshabilite la publicación para todas las bases de datos si el Publicador y el Distribuidor están en el mismo servidor. Para más información, consulte [Delete a Publication](publish/delete-a-publication.md).  
  
3.  Cree una conexión al distribuidor mediante la clase <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
4.  Cree una instancia de la clase <xref:Microsoft.SqlServer.Replication.DistributionPublisher>. Especifique la propiedad <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> y pase el objeto <xref:Microsoft.SqlServer.Management.Common.ServerConnection> del paso 3.  
  
5.  (Opcional) Llame al método <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> para obtener las propiedades del objeto y compruebe que el Publicador existe. Si este método devuelve `false`, el nombre del Publicador establecido en el paso 4 era incorrecto o este Distribuidor no usa el Publicador.  
  
6.  Llame al método <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Remove%2A> . Pase un valor de `true` para *Force* si el publicador y el distribuidor están en servidores diferentes, y cuando el publicador se debe desinstalar en el distribuidor sin comprobar primero que las publicaciones ya no existen en el publicador.  
  
7.  Cree una instancia de la clase <xref:Microsoft.SqlServer.Replication.ReplicationServer>. Pase el objeto <xref:Microsoft.SqlServer.Management.Common.ServerConnection> del paso 3.  
  
8.  Llame al método <xref:Microsoft.SqlServer.Replication.ReplicationServer.UninstallDistributor%2A> . Pase un valor de `true` for *Force* para quitar todos los objetos de replicación en el distribuidor sin comprobar primero que todas las bases de datos de publicación locales se han deshabilitado y que se han desinstalado las bases de datos de distribución.  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> Ejemplos (RMO)  
 Este ejemplo quita el registro del Publicador en el Distribuidor, coloca la base de datos de distribución y desinstala el Distribuidor.  
  
 [!code-csharp[HowTo#rmo_DropDistPub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_dropdistpub)]  
  
 [!code-vb[HowTo#rmo_vb_DropDistPub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_dropdistpub)]  
  
 Este ejemplo desinstala el Distribuidor sin deshabilitar primero las bases de datos de publicación locales o quitar la base de datos de distribución.  
  
 [!code-csharp[HowTo#rmo_DropDistPubForce](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_dropdistpubforce)]  
  
 [!code-vb[HowTo#rmo_vb_DropDistPubForce](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_dropdistpubforce)]  
  
## <a name="see-also"></a>Consulte también  
 [Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md)   
 [Conceptos de procedimientos almacenados del sistema de replicación](concepts/replication-system-stored-procedures-concepts.md)  
  
  
