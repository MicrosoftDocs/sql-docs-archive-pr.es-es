---
title: Conectar tareas mediante programación | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- tasks [Integration Services], precedence constraints
- precedence constraints [Integration Services], connecting tasks
- constraints [Integration Services]
ms.assetid: 23668e88-cef4-4009-a9cf-38e607eab7a2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5aeeb70ed5741cc7372fdfc63e637fd53d932f91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87671638"
---
# <a name="connecting-tasks-programmatically"></a>Conectar tareas mediante programación
  Una restricción de precedencia, representada en el modelo de objetos por la clase <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>, establece el orden en que se ejecutan los objetos <xref:Microsoft.SqlServer.Dts.Runtime.Executable> en un paquete. La restricción de precedencia permite que la ejecución de los contenedores y las tareas de un paquete dependa del resultado de la ejecución de una tarea o un contenedor anterior. Las restricciones de precedencia se establecen entre pares de objetos <xref:Microsoft.SqlServer.Dts.Runtime.Executable> con una llamada al método <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraints.Add%2A> de la colección <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraints> en el objeto contenedor. Después de crear una restricción entre dos objetos ejecutables, establece la propiedad <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> para establecer los criterios de ejecución del segundo ejecutable definido en la restricción.  
  
 Puede utilizar una restricción y una expresión en una restricción de precedencia única, según el valor que especifique para la propiedad <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.EvalOp%2A>, tal como se describe en la tabla siguiente:  
  
|Valor de la propiedad EvalOp|Descripción|  
|----------------------------------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.Constraint>|Especifica que el resultado de ejecución determina si se ejecutan el contenedor o la tarea restringidos. Establezca la propiedad <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> de <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> en el valor deseado de la enumeración <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult>.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.Expression>|Especifica que el valor de una expresión determina si se ejecutan el contenedor o la tarea restringidos. Establezca la propiedad <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> de <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.ExpressionAndConstraint>|Especifica que se debe producir el resultado de la restricción y que se debe evaluar la expresión para que se ejecuten el contenedor o la tarea restringidos. Establezca las propiedades <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> y <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> de <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>, y establezca su propiedad <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.LogicalAnd%2A> en `true`.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.ExpressionOrConstraint>|Especifica que se debe producir el resultado de la restricción o que se debe evaluar la expresión para que se ejecuten el contenedor o la tarea restringidos. Establezca las propiedades <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> y <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> de <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>, y establezca su propiedad <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.LogicalAnd%2A> en `false`.|  
  
 En el ejemplo de código siguiente se muestra cómo agregar dos tareas a un paquete. Se crea un objeto <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> entre ellas que evita que se ejecute la segunda tarea hasta que finalice la primera.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
  
      // Add a File System task.  
      Executable eFileTask1 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileHost1 = eFileTask1 as TaskHost;  
  
      // Add a second File System task.  
      Executable eFileTask2 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileHost2 = eFileTask2 as TaskHost;  
  
      // Put a precedence constraint between the tasks.  
      // Set the constraint to specify that the second File System task cannot run  
      // until the first File System task finishes.  
      PrecedenceConstraint pcFileTasks =   
        p.PrecedenceConstraints.Add((Executable)thFileHost1, (Executable)thFileHost2);  
      pcFileTasks.Value = DTSExecResult.Completion;  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    ' Add a File System task.  
    Dim eFileTask1 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileHost1 As TaskHost = CType(eFileTask1, TaskHost)  
  
    ' Add a second File System task.  
    Dim eFileTask2 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileHost2 As TaskHost = CType(eFileTask2, TaskHost)  
  
    ' Put a precedence constraint between the tasks.  
    ' Set the constraint to specify that the second File System task cannot run  
    ' until the first File System task finishes.  
    Dim pcFileTasks As PrecedenceConstraint = _  
      p.PrecedenceConstraints.Add(CType(thFileHost1, Executable), CType(thFileHost2, Executable))  
    pcFileTasks.Value = DTSExecResult.Completion  
  
  End Sub  
  
End Module  
```  
  
![Integration Services icono (pequeño)](../media/dts-16.gif "Icono de Integration Services (pequeño)")  **Manténgase al día con Integration Services**<br /> Para obtener las descargas, artículos, ejemplos y vídeos más recientes de Microsoft, así como soluciones seleccionadas de la comunidad, visite la página de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] en MSDN:<br /><br /> [Visite la página de Integration Services en MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Para recibir notificaciones automáticas de estas actualizaciones, suscríbase a las fuentes RSS disponibles en la página.  
  
## <a name="see-also"></a>Consulte también  
 [Agregar la tarea de flujo de datos mediante programación](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md)  
  
  
