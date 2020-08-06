---
title: Utilizar variables en la tarea Script | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Foreach Loop containers
- Script task [Integration Services], variables
- scripts [Integration Services], variables
- Variables property
- Variable object
- SSIS Script task, variables
- variables [Integration Services], Script task
ms.assetid: 593b5961-4bfa-4ce1-9531-a251c34e89d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2cd8fee5741c3d0e28e52c8712c3896428a05e8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87752282"
---
# <a name="using-variables-in-the-script-task"></a>Utilizar variables en la tarea Script
  Las variables permiten que la tarea Script intercambie datos con otros objetos del paquete. Para más información, vea [Variables de Integration Services &#40;SSIS&#41;](../../integration-services-ssis-variables.md).  
  
 La tarea Script utiliza la propiedad <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> del objeto `Dts` para leer de y escribir en los objetos <xref:Microsoft.SqlServer.Dts.Runtime.Variable> del paquete.  
  
> [!NOTE]  
>  La propiedad <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> de la clase <xref:Microsoft.SqlServer.Dts.Runtime.Variable> es del tipo `Object`. Dado que la tarea Script tiene `Option Strict` habilitado, debe convertir la propiedad <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> al tipo adecuado antes de utilizarla.  
  
 Las variables existentes se agregan a las listas <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadOnlyVariables%2A> y <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadWriteVariables%2A> en el **Editor de la tarea Script** para que estén disponibles en el script personalizado. Tenga presente que los nombres de variable distinguen entre mayúsculas y minúsculas. Dentro del script, tiene acceso a las variables de ambos tipos a través de la propiedad <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> del objeto `Dts`. Utilice la propiedad `Value` para leer de y escribir en las variables individuales. La tarea Script administra de forma transparente el bloqueo a medida que el script lee y modifica los valores de las variables.  
  
 Puede utilizar el método <xref:Microsoft.SqlServer.Dts.Runtime.Variables.Contains%2A> de la colección <xref:Microsoft.SqlServer.Dts.Runtime.Variables> que devuelve la propiedad <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> para comprobar la existencia de una variable antes de utilizarla en el código.  
  
 También puede utilizar la propiedad <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> (Dts.VariableDispenser) para trabajar con variables en la tarea Script. Al utilizar <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>, debe administrar la semántica de bloqueo y la conversión de tipos de datos para los valores de variables en su propio código. Puede que necesite utilizar la propiedad <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> en lugar de la propiedad <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> si desea trabajar con una variable que no está disponible en tiempo de diseño pero que se crea mediante programación en tiempo de ejecución.  
  
## <a name="using-the-script-task-within-a-foreach-loop-container"></a>Utilizar la tarea Script dentro de un contenedor de bucles Foreach  
 Cuando una tarea Script se ejecuta repetidamente dentro de un contenedor de bucles Foreach, normalmente el script necesita trabajar con el contenido del elemento actual en el enumerador. Por ejemplo, al utilizar un enumerador de archivos Foreach, el script necesita conocer el nombre del archivo actual; al utilizar un enumerador de ADO para Foreach, el script necesita conocer el contenido de las columnas en la fila actual de datos.  
  
 Las variables consiguen que sea posible esta comunicación entre el contenedor de bucles Foreach y la tarea Script. En la página **Asignaciones de variables** del **Editor de bucles Para cada uno**, asigne variables a cada elemento de datos que devuelve un único elemento enumerado. Por ejemplo, un enumerador de archivos Foreach solamente devuelve un nombre de archivo en Índice 0 y por tanto solamente requiere una asignación de variable, en tanto que un enumerador que devuelve varias columnas de datos en cada fila requiere que asigne una variable diferente a cada columna que desea utilizar en la tarea Script.  
  
 Después de asignar los elementos enumerados a las variables, debe agregar las variables asignadas a la `ReadOnlyVariables` propiedad en la página **script** del editor de la **tarea script** para que estén disponibles para el script. Para obtener un ejemplo de una tarea Script dentro de un contenedor de bucles Para cada uno que procesa los archivos de imagen en una carpeta, vea [Trabajar con imágenes con la tarea Script](../../extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md).  
  
## <a name="variables-example"></a>Ejemplo de variables  
 En el ejemplo siguiente se muestra cómo obtener acceso y utilizar las variables en una tarea Script para determinar la ruta de acceso de flujo de trabajo del paquete. En el ejemplo se supone que ha creado variables de entero denominadas `CustomerCount` y `MaxRecordCount` y las ha agregado a la `ReadOnlyVariables` colección en el editor de la **tarea script**. La variable `CustomerCount` contiene el número de registros del cliente que se van a importar. Si su valor es mayor que el valor de `MaxRecordCount`, la tarea Script informa del error. Cuando se produce un error porque se ha superado el umbral `MaxRecordCount`, la ruta de acceso de error del flujo de trabajo puede implementar cualquier limpieza necesaria.  
  
 Para compilar correctamente el ejemplo, debe agregar una referencia al ensamblado Microsoft.SqlServer.ScriptTask.  
  
```vb  
Public Sub Main()  
  
    Dim customerCount As Integer  
    Dim maxRecordCount As Integer  
  
    If Dts.Variables.Contains("CustomerCount") = True AndAlso _  
        Dts.Variables.Contains("MaxRecordCount") = True Then  
  
        customerCount = _  
            CType(Dts.Variables("CustomerCount").Value, Integer)  
        maxRecordCount = _  
            CType(Dts.Variables("MaxRecordCount").Value, Integer)  
  
    End If  
  
    If customerCount > maxRecordCount Then  
            Dts.TaskResult = ScriptResults.Failure  
    Else  
            Dts.TaskResult = ScriptResults.Success  
    End If  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime;  
  
public class ScriptMain  
{  
  
    public void Main()  
    {  
        int customerCount;  
        int maxRecordCount;  
  
        if (Dts.Variables.Contains("CustomerCount")==true&&Dts.Variables.Contains("MaxRecordCount")==true)  
  
        {  
            customerCount = (int) Dts.Variables["CustomerCount"].Value;  
            maxRecordCount = (int) Dts.Variables["MaxRecordCount"].Value;  
  
        }  
  
        if (customerCount>maxRecordCount)  
        {  
            Dts.TaskResult = (int)ScriptResults.Failure;  
        }  
        else  
        {  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
  
    }  
  
}  
  
```  
  
![Integration Services icono (pequeño)](../../media/dts-16.gif "Icono de Integration Services (pequeño)")  **Manténgase al día con Integration Services**<br /> Para obtener las descargas, artículos, ejemplos y vídeos más recientes de Microsoft, así como soluciones seleccionadas de la comunidad, visite la página de [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] en MSDN:<br /><br /> [Visite la página de Integration Services en MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Para recibir notificaciones automáticas de estas actualizaciones, suscríbase a las fuentes RSS disponibles en la página.  
  
## <a name="see-also"></a>Consulte también  
 [Variables de Integration Services &#40;SSIS&#41;](../../integration-services-ssis-variables.md)   
 [Usar variables en paquetes](../../use-variables-in-packages.md)  
  
  
