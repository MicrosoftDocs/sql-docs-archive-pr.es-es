---
title: 'Ejemplo: crear una alerta de Agente SQL Server mediante el proveedor WMI para eventos de servidor | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- SQL Server Agent [WMI]
- WMI Provider for Server Events, samples
- sample applications [WMI]
ms.assetid: d44811c7-cd46-4017-b284-c863ca088e8f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f23a3a8738435dc6a27a230f4521300a3ee2470f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746799"
---
# <a name="sample-creating-a-sql-server-agent-alert-by-using-the-wmi-provider-for-server-events"></a>Sample: Creación de una alerta del Agente SQL Server con el proveedor WMI para eventos de servidor
  Una manera común de utilizar el Proveedor de eventos WMI es crear alertas del Agente SQL Server que respondan a eventos concretos. En el ejemplo siguiente se presenta una alerta simple que guarda los eventos de grafo de interbloqueo de XML en una tabla para el análisis posterior. El Agente SQL Server envía una solicitud WQL, recibe los eventos WMI y ejecuta un trabajo en respuesta al evento. Observe que, aunque varios objetos Service Broker están implicados para procesar el mensaje de notificación, el Proveedor de eventos WMI administra los detalles de creación y administración de estos objetos.  
  
## <a name="example"></a>Ejemplo  
 Primero, se crea una tabla en la base de datos `AdventureWorks` para contener el evento de grafo de interbloqueo. La tabla contiene dos columnas: la columna `AlertTime` contiene la hora a la que se ejecuta la alerta y la columna `DeadlockGraph` contiene el documento XML que contiene el grafo de interbloqueo.  
  
 A continuación, se crea la alerta. El script crea primero el trabajo que la alerta ejecutará, agrega un paso de trabajo al trabajo y dirige el trabajo a la instancia actual de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. A continuación, el script crea la alerta.  
  
 El paso de trabajo recupera la propiedad **TextData** de la instancia de evento WMI e inserta ese valor en la columna **DeadlockGraph** de la tabla **DeadlockEvents** . Observe que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] convierte implícitamente la cadena al formato XML. Dado que el paso de trabajo utiliza el subsistema [!INCLUDE[tsql](../../includes/tsql-md.md)], el paso de trabajo no especifica un proxy.  
  
 La alerta ejecuta el trabajo cada vez que se registraría un evento de seguimiento de grafo de interbloqueo. Para una alerta WMI, el Agente SQL Server crea una consulta de notificación mediante el espacio de nombres y la instrucción WQL especificados. Para este alerta, el Agente SQL Server supervisa la instancia predeterminada en el equipo local. La instrucción WQL solicita cualquier evento `DEADLOCK_GRAPH` en la instancia predeterminada. Para cambiar la instancia que supervisa la alerta, sustituya el nombre de instancia por `MSSQLSERVER` en el `@wmi_namespace` para la alerta.  
  
> [!NOTE]  
>  Para Agente SQL Server recibir eventos de WMI, [!INCLUDE[ssSB](../../includes/sssb-md.md)] debe estar habilitado en **msdb** y [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
```  
USE AdventureWorks ;  
GO  
  
IF OBJECT_ID('DeadlockEvents', 'U') IS NOT NULL  
BEGIN  
    DROP TABLE DeadlockEvents ;  
END ;  
GO  
  
CREATE TABLE DeadlockEvents  
    (AlertTime DATETIME, DeadlockGraph XML) ;  
GO  
-- Add a job for the alert to run.  
  
EXEC  msdb.dbo.sp_add_job @job_name=N'Capture Deadlock Graph',   
    @enabled=1,   
    @description=N'Job for responding to DEADLOCK_GRAPH events' ;  
GO  
  
-- Add a jobstep that inserts the current time and the deadlock graph into  
-- the DeadlockEvents table.  
  
EXEC msdb.dbo.sp_add_jobstep  
    @job_name = N'Capture Deadlock Graph',  
    @step_name=N'Insert graph into LogEvents',  
    @step_id=1,   
    @on_success_action=1,   
    @on_fail_action=2,   
    @subsystem=N'TSQL',   
    @command= N'INSERT INTO DeadlockEvents  
                (AlertTime, DeadlockGraph)  
                VALUES (getdate(), N''$(ESCAPE_SQUOTE(WMI(TextData)))'')',  
    @database_name=N'AdventureWorks' ;  
GO  
  
-- Set the job server for the job to the current instance of SQL Server.  
  
EXEC msdb.dbo.sp_add_jobserver @job_name = N'Capture Deadlock Graph' ;  
GO  
  
-- Add an alert that responds to all DEADLOCK_GRAPH events for  
-- the default instance. To monitor deadlocks for a different instance,  
-- change MSSQLSERVER to the name of the instance.  
  
EXEC msdb.dbo.sp_add_alert @name=N'Respond to DEADLOCK_GRAPH',   
@wmi_namespace=N'\\.\root\Microsoft\SqlServer\ServerEvents\MSSQLSERVER',   
    @wmi_query=N'SELECT * FROM DEADLOCK_GRAPH',   
    @job_name='Capture Deadlock Graph' ;  
GO  
```  
  
## <a name="testing-the-sample"></a>Probar el ejemplo  
 Para ver cómo se ejecuta el trabajo, provoque un interbloqueo. En [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , abra dos pestañas de **consulta SQL** y conecte ambas consultas a la misma instancia. Ejecute el script siguiente en una de las pestañas de consulta. Este script genera un conjunto de resultados y finaliza.  
  
```  
USE AdventureWorks ;  
GO  
  
BEGIN TRANSACTION ;  
GO  
  
SELECT TOP(1) Name FROM Production.Product WITH (XLOCK) ;  
GO  
```  
  
 Ejecute el siguiente script en la segunda pestaña de consulta. Este script genera un conjunto de resultados y, a continuación, se bloquea, a la espera de adquirir un bloqueo en `Production.Product` .  
  
```  
USE AdventureWorks ;  
GO  
  
BEGIN TRANSACTION ;  
GO  
  
SELECT TOP(1) Name FROM Production.Location WITH (XLOCK) ;  
GO  
  
SELECT TOP(1) Name FROM Production.Product WITH (XLOCK) ;  
GO  
```  
  
 Ejecute el siguiente script en la primera pestaña de consulta. Este script se bloquea, a la espera de adquirir un bloqueo en `Production.Location` . Después de un tiempo de espera corto, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] elegirá este script o el script del ejemplo como víctima del interbloqueo y finalizará la transacción.  
  
```  
SELECT TOP(1) Name FROM Production.Location WITH (XLOCK) ;  
GO  
```  
  
 Después de provocar el interbloqueo, espere unos momentos a que el Agente SQL Server active la alerta y ejecute el trabajo. Examine el contenido de la tabla `DeadlockEvents` ejecutando el script siguiente:  
  
```  
SELECT * FROM DeadlockEvents ;  
GO  
```  
  
 La columna `DeadlockGraph` debería contener un documento XML que muestra todas las propiedades del evento de grafo de interbloqueo.  
  
## <a name="see-also"></a>Consulte también  
 [Conceptos del proveedor WMI para eventos de servidor](wmi-provider-for-server-events-concepts.md)  
  
  
