---
title: Cmdlet Invoke-Sqlcmd | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- PowerShell [SQL Server], Invoke-Sqlcmd
- Cmdlets [SQL Server], Invoke-Sqlcmd
- Invoke-Sqlcmd cmdlet
- sqlcmd utility, PowerShell
ms.assetid: 0c74d21b-84a5-4fa4-be51-90f0f7230044
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b1572b03b5772f35ac68a6b85aeedde43d150c07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745396"
---
# <a name="invoke-sqlcmd-cmdlet"></a>cmdlet Invoke-Sqlcmd
  **Invoke-Sqlcmd** es un cmdlet de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] que ejecuta scripts que contienen instrucciones de los lenguajes ([!INCLUDE[tsql](../includes/tsql-md.md)] y XQuery) y comandos admitidos por la utilidad **sqlcmd**.  
  
## <a name="using-invoke-sqlcmd"></a>Usar Invoke-Sqlcmd  
 El cmdlet **Invoke-Sqlcmd** permite ejecutar archivos de script de **sqlcmd** en un entorno de Windows PowerShell. **Invoke-Sqlcmd** permite llevar a cabo una gran parte de lo que se puede hacer con **sqlcmd**.  
  
 Aquí se muestra un ejemplo en el que se llama a Invoke-Sqlcmd para ejecutar una consulta simple, similar a especificar **sqlcmd** con las opciones **-Q** y **-S** :  
  
```powershell
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance"  
```  
  
 Aquí se muestra un ejemplo en el que se llama a **Invoke-Sqlcmd**, donde se especifica un archivo de entrada y se canaliza la salida a un archivo. Esto es similar a especificar **sqlcmd** con las opciones **-i** y **-o** :  
  
```powershell
Invoke-Sqlcmd -InputFile "C:\MyFolder\TestSQLCmd.sql" | Out-File -FilePath "C:\MyFolder\TestSQLCmd.rpt"  
```  
  
 Este es un ejemplo del uso de una matriz de Windows PowerShell para pasar varias variables de scripting de **sqlcmd** a **Invoke-Sqlcmd**. El escape de los caracteres "$" que identifican las variables de scripting de **sqlcmd** en la instrucción SELECT se ha realizado mediante el carácter de escape de acento invertido "`" de PowerShell:  
  
```powershell
$MyArray = "MyVar1 = 'String1'", "MyVar2 = 'String2'"  
Invoke-Sqlcmd -Query "SELECT `$(MyVar1) AS Var1, `$(MyVar2) AS Var2;" -Variable $MyArray  
```  
  
 En este ejemplo se muestra cómo usar el proveedor de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] para Windows PowerShell para ir a una instancia de [!INCLUDE[ssDE](../includes/ssde-md.md)]y después usar el cmdlet **Get-Item** de Windows PowerShell para recuperar el objeto del servidor SMO de la instancia y pasarlo a **Invoke-Sqlcmd**:  
  
```powershell
Set-Location SQLSERVER:\SQL\MyComputer\MyInstance  
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance (Get-Item .)  
```  
  
 El parámetro -Query es posicional y no es necesario asignarle un nombre. Si la primera cadena que se pasa a **Invoke-Sqlcmd**: no tiene nombre, se trata como el parámetro -Query.  
  
```powershell
Invoke-Sqlcmd "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance"  
```  
  
## <a name="path-context-in-invoke-sqlcmd"></a>Contexto de la ruta de acceso en Invoke-Sqlcmd  
 Si no utiliza el parámetro -Database, el contexto de base de datos para Invoke-Sqlcmd se establece mediante la ruta de acceso que está activa cuando se llama al cmdlet.  
  
|Path|Contexto de base de datos|  
|----------|----------------------|  
|Empieza con una unidad diferente de SQLSERVER:|La base de datos predeterminada para el identificador de inicio de sesión en la instancia predeterminada del equipo local.|  
|SQLSERVER:\SQL|La base de datos predeterminada para el identificador de inicio de sesión en la instancia predeterminada del equipo local.|  
|SQLSERVER:\SQL\nombreDeEquipo|La base de datos predeterminada para el identificador de inicio de sesión en la instancia predeterminada del equipo especificado.|  
|SQLSERVER:\SQL\nombreDeEquipo\nombreDeInstancia|La base de datos predeterminada para el identificador de inicio de sesión en la instancia especificada del equipo especificado.|  
|SQLSERVER:\SQL\nombreDeEquipo\nombreDeInstancia\Bases de datos|La base de datos predeterminada para el identificador de inicio de sesión en la instancia especificada del equipo especificado.|  
|SQLSERVER:\SQL\nombreDeEquipo\nombreDeInstancia\Bases de datos\nombreDeBaseDeDatos|La base de datos especificada en la instancia especificada del equipo especificado. Esto también es aplicable a rutas de acceso más largas, como una que especifique el nodo de tablas y columnas en una base de datos.|  
  
 Por ejemplo, suponga que la base de datos predeterminada para su cuenta de Windows en la instancia predeterminada del equipo local es master (maestra). Entonces, los comandos siguientes devolverían master:  
  
```powershell
Set-Location SQLSERVER:\SQL  
Invoke-Sqlcmd "SELECT DB_NAME() AS DatabaseName;"  
```  
  
 Los comandos siguientes devolverían [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]:  
  
```powershell
Set-Location SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Person.Person  
Invoke-Sqlcmd "SELECT DB_NAME() AS DatabaseName;"  
```  
  
 Invoke-Sqlcmd muestra una advertencia cuando utiliza el contexto de base de datos establecido mediante la ruta de acceso. Puede utilizar el parámetro -SuppressProviderContextWarning para desactivar el mensaje de advertencia. Puede usar el parámetro -IgnoreProviderContext para indicar a Invoke-Sqlcmd que use siempre la base de datos predeterminada para el inicio de sesión.  
  
## <a name="comparing-invoke-sqlcmd-and-the-sqlcmd-utility"></a>Diferencias entre Invoke-Sqlcmd y la utilidad sqlcmd  
 **Invoke-Sqlcmd** se puede usar para ejecutar muchos de los scripts que se pueden ejecutar con la utilidad **sqlcmd** . Pero **Invoke-Sqlcmd** se ejecuta en un entorno de Windows PowerShell que es diferente del entorno del símbolo del sistema en el que se ejecuta **sqlcmd** . El comportamiento de **Invoke-Sqlcmd** se ha modificado para que funcione en un entorno de Windows PowerShell.  
  
 No todos los comandos de **sqlcmd** se implementan en **Invoke-Sqlcmd**. Entre los comandos que no se implementan se incluyen los siguientes: **:!!**, **: Connect**, **: error**, **: out**, **: Ed**, **: List**, **: listvar**, **: RESET**, **:p erftrace**y **: ServerList**.  
  
 **Invoke-Sqlcmd** no inicializa el entorno de **sqlcmd** ni variables de scripting como SQLCMDDBNAME o SQLCMDWORKSTATION.  
  
 **Invoke-Sqlcmd** no muestra mensajes, como la salida de las instrucciones PRINT, a menos que se especifique el parámetro común de Windows PowerShell **-Verbose** . Por ejemplo:  
  
```powershell
Invoke-Sqlcmd -Query "PRINT N'abc';" -Verbose  
```  
  
 No todos los parámetros de **sqlcmd** son necesarios en un entorno de PowerShell. Por ejemplo, Windows PowerShell da formato a toda la salida de los cmdlets, de modo que los parámetros de **sqlcmd** que especifican las opciones de formato no se implementan en **Invoke-Sqlcmd**. En la tabla siguiente se muestra la relación entre los parámetros **de Invoke-SQLCMD** y las opciones de **sqlcmd** :  
  
|Descripción|Opción sqlcmd|Parámetro de Invoke-Sqlcmd|  
|-----------------|-------------------|------------------------------|  
|Nombre de servidor e instancia.|-S|-ServerInstance|  
|Base de datos inicial que se utilizará.|-d|-Database|  
|Ejecutar la consulta especificada y salir.|-Q|-Query|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|-U|-Username|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|-P|-Password|  
|Definición de variable.|-v|-Variable|  
|Consultar el intervalo de tiempo de espera.|-T|-QueryTimeout|  
|Detener la ejecución cuando se produce un error.|-b|-AbortOnError|  
|Conexión de administrador dedicada.|-A|-DedicatedAdministratorConnection|  
|Deshabilitar comandos interactivos, script de inicio y variables de entorno.|-X|-DisableCommands|  
|Deshabilitar la sustitución de variables.|-X|-DisableVariables|  
|Nivel de gravedad mínimo que se ha de notificar.|-v|-SeverityLevel|  
|Nivel de error mínimo que se ha de notificar.|-M|-ErrorLevel|  
|Intervalo de tiempo de espera de inicio de sesión.|-l|-ConnectionTimeout|  
|Nombre de host.|-H|-HostName|  
|Cambiar contraseña y salir.|-Z|-NewPassword|  
|Archivo de entrada que contiene una consulta.|-i|-InputFile|  
|Longitud máxima de la salida de caracteres.|-w|-MaxCharLength|  
|Longitud máxima de la salida binaria.|-w|-MaxBinaryLength|  
|Conectarse con cifrado SSL.|Ningún parámetro.|-EncryptConnection|  
|Mostrar los errores.|Ningún parámetro.|-OutputSqlErrors|  
|Mensajes de salida a stderr.|-r|Ningún parámetro.|  
|Usar la configuración regional del cliente.|-R|Ningún parámetro.|  
|Ejecutar la consulta especificada y continuar la ejecución.|-q|Ningún parámetro.|  
|Página de códigos que se ha de utilizar para los datos de salida.|-f|Ningún parámetro.|  
|Cambiar una contraseña y continuar la ejecución.|-Z|Ningún parámetro.|  
|Tamaño del paquete|-a|Ningún parámetro.|  
|Delimitador de columnas.|-S|Ningún parámetro.|  
|Controlar los encabezados de salida|-H|Ningún parámetro.|  
|Especificar los caracteres de control.|-k|Ningún parámetro.|  
|Ancho de presentación de longitud fija.|-y|Ningún parámetro.|  
|Ancho de presentación de longitud variable.|-y|Ningún parámetro.|  
|Entrada de eco.|-E|Ningún parámetro.|  
|Habilitar los identificadores entre comillas.|-I|Ningún parámetro.|  
|Quitar los espacios finales.|-w|Ningún parámetro.|  
|Enumerar instancias.|-l|Ningún parámetro.|  
|Dar formato al resultado como Unicode.|-U|Ningún parámetro.|  
|Imprimir las estadísticas.|-p|Ningún parámetro.|  
|Fin del comando.|-c|Ningún parámetro.|  
|Conectar con la autenticación de Windows.|-E|Ningún parámetro.|  
  
## <a name="see-also"></a>Consulte también  
 [Usar los cmdlets de Motor de base de datos](../../2014/database-engine/use-the-database-engine-cmdlets.md)   
 [sqlcmd (utilidad)](../tools/sqlcmd-utility.md)   
 [Usar la utilidad sqlcmd](../relational-databases/scripting/sqlcmd-use-the-utility.md)  
