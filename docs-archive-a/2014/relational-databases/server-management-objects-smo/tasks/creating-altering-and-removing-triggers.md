---
title: Crear, modificar y quitar desencadenadores | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- triggers [SMO]
ms.assetid: 8ddbe23b-6e31-4f8e-8a70-17bd5072413e
author: stevestein
ms.author: sstein
ms.openlocfilehash: c2cdd1573c488fbe7b2309f656cd6bf42e82a527
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676975"
---
# <a name="creating-altering-and-removing-triggers"></a>Crear, modificar y eliminar desencadenadores
  En SMO, los desencadenadores se representan utilizando el objeto <xref:Microsoft.SqlServer.Management.Smo.Trigger>. El [!INCLUDE[tsql](../../../includes/tsql-md.md)] código que se ejecuta cuando el desencadenador que se activa se establece mediante la <xref:Microsoft.SqlServer.Management.Smo.Trigger.TextBody%2A> propiedad del objeto desencadenador. El tipo de desencadenador se establece utilizando otras propiedades del objeto <xref:Microsoft.SqlServer.Management.Smo.Trigger>, como la propiedad <xref:Microsoft.SqlServer.Management.Smo.Trigger.Update%2A>. Se trata de una propiedad booleana que especifica si el desencadenador se activa por una `UPDATE` de los registros en la tabla primaria.  
  
 El objeto <xref:Microsoft.SqlServer.Management.Smo.Trigger> representa los desencadenadores tradicionales del lenguaje de manipulación de datos (DML). En [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] y en versiones posteriores, también se admiten los desencadenadores del lenguaje de definición de datos (DDL). El objeto <xref:Microsoft.SqlServer.Management.Smo.DatabaseDdlTrigger> y el objeto <xref:Microsoft.SqlServer.Management.Smo.ServerDdlTrigger> representan los desencadenadores DDL.  
  
## <a name="example"></a>Ejemplo  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="creating-altering-and-removing-a-trigger-in-visual-basic"></a>Crear, modificar y quitar un desencadenador en Visual Basic  
 En este ejemplo de código se muestra cómo crear e insertar un desencadenador de actualización en una tabla existente, denominada `Sales`, en la base de datos [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] . El desencadenador envía un mensaje de aviso cuando la tabla se actualiza o cuando se inserta un nuevo registro.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBTriggers1](SMO How to#SMO_VBTriggers1)]  -->  
  
## <a name="creating-altering-and-removing-a-trigger-in-visual-c"></a>Crear, modificar y quitar un desencadenador en Visual C#  
 En este ejemplo de código se muestra cómo crear e insertar un desencadenador de actualización en una tabla existente, denominada `Sales`, en la base de datos [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] . El desencadenador envía un mensaje de aviso cuando la tabla se actualiza o cuando se inserta un nuevo registro.  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server mysrv;  
            mysrv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database mydb;  
            mydb = mysrv.Databases["AdventureWorks2012"];  
            //Declare a Table object variable and reference the Customer table.   
            Table mytab;  
            mytab = mydb.Tables["Customer", "Sales"];  
            //Define a Trigger object variable by supplying the parent table, schema ,and name in the constructor.   
            Trigger tr;  
            tr = new Trigger(mytab, "Sales");  
            //Set TextMode property to False, then set other properties to define the trigger.   
            tr.TextMode = false;  
            tr.Insert = true;  
            tr.Update = true;  
            tr.InsertOrder = ActivationOrder.First;  
            string stmt;  
            stmt = " RAISERROR('Notify Customer Relations',16,10) ";  
            tr.TextBody = stmt;  
            tr.ImplementationType = ImplementationType.TransactSql;  
            //Create the trigger on the instance of SQL Server.   
            tr.Create();  
            //Remove the trigger.   
            tr.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-trigger-in-powershell"></a>Crear, modificar y quitar un desencadenador en PowerShell  
 En este ejemplo de código se muestra cómo crear e insertar un desencadenador de actualización en una tabla existente, denominada `Sales`, en la base de datos [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] . El desencadenador envía un mensaje de aviso cuando la tabla se actualiza o cuando se inserta un nuevo registro.  
  
```powershell
# Set the path context to the local, default instance of SQL Server and to the  
#database tables in Adventureworks2012  
CD \sql\localhost\default\databases\AdventureWorks2012\Tables\  
  
#Get reference to the trigger's target table  
$mytab = Get-Item Sales.Customer  
  
# Define a Trigger object variable by supplying the parent table, schema ,and name in the constructor.  
$tr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Trigger -argumentlist $mytab, "Sales"  
  
# Set TextMode property to False, then set other properties to define the trigger.
$tr.TextMode = $false  
$tr.Insert = $true  
$tr.Update = $true  
$tr.InsertOrder = [Microsoft.SqlServer.Management.SMO.Agent.ActivationOrder]::First  
$tr.TextBody = " RAISERROR('Notify Customer Relations',16,10) "  
$tr.ImplementationType = [Microsoft.SqlServer.Management.SMO.ImplementationType]::TransactSql  
  
# Create the trigger on the instance of SQL Server.
$tr.Create()  
  
#Remove the trigger.
$tr.Drop()  
```  
