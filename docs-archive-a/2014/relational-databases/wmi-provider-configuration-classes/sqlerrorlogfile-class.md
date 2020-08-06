---
title: Clase SqlErrorLogFile | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
ms.assetid: 2b83ae4a-c0d4-414c-b6e5-a41ec7c13159
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d73f97ebddd7a1d18c73a2cbce7fe79dafc17a77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744567"
---
# <a name="sqlerrorlogfile-class"></a>Clase SqlErrorLogFile
  Proporciona propiedades para ver información sobre un archivo de registro de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
class SQLErrorLogFile  
{  
   uint32ArchiveNumber;  
   stringInstanceName;  
   datetimeLastModified;  
   uint32LogFileSize;  
   stringName;  
  
};  
```  
  
## <a name="properties"></a>Propiedades  
 La clase SQLErrorLogFile define las siguientes propiedades.  
  
|||  
|-|-|  
|ArchiveNumber|Tipo de datos: `uint32`<br /><br /> Tipo de acceso: solo lectura<br /><br /> <br /><br /> El número de archivo para el archivo de registro.|  
|InstanceName|Tipo de datos: `string`<br /><br /> Tipo de acceso: solo lectura<br /><br /> Calificadores: clave<br /><br /> <br /><br /> El nombre de la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] donde reside el archivo de registro.|  
|LastModified|Tipo de datos: `datetime`<br /><br /> Tipo de acceso: solo lectura<br /><br /> <br /><br /> Fecha de la última modificación del archivo de registro.|  
|LogFileSize|Tipo de datos: `uint32`<br /><br /> Tipo de acceso: solo lectura<br /><br /> <br /><br /> El tamaño del archivo de registro en bytes.|  
|Nombre|Tipo de datos: `string`<br /><br /> Tipo de acceso: solo lectura<br /><br /> Calificadores: clave<br /><br /> <br /><br /> El nombre del archivo de registro.|  
  
## <a name="remarks"></a>Observaciones  
  
|||  
|-|-|  
|MOF|Sqlmgmprovider xpsp2up.mof|  
|Archivo DLL|Sqlmgmprovider.dll|  
|Espacio de nombres|\raíz\Microsoft\SqlServer\ComputerManagement10|  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se recupera información sobre todos los archivos de registro de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en una instancia especificada de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para ejecutar el ejemplo, reemplace \<*Instance_Name*> por el nombre de la instancia, por ejemplo, ' Instance1 '.  
  
```  
on error resume next  
set strComputer = "."  
set objWMIService = GetObject("winmgmts:\\.\root\Microsoft\SqlServer\ComputerManagement10")  
set LogFiles = objWmiService.ExecQuery("SELECT * FROM SqlErrorLogFile WHERE InstanceName = '<Instance_Name>'")  
  
For Each logFile in LogFiles  
  
WScript.Echo "Instance Name:  " & logFile.InstanceName & vbNewLine _  
    & "Log File Name:  " & logFile.Name & vbNewLine _  
    & "Archive Number: " & logFile.ArchiveNumber & vbNewLine _  
    & "Log File Size:  " & logFile.LogFileSize & " bytes" & vbNewLine _  
    & "Last Modified:  " & logFile.LastModified & vbNewLine _  
  
Next   
```  
  
## <a name="comments"></a>Comentarios  
 Cuando no se proporciona *InstanceName* en la instrucción WQL, la consulta devolverá información para la instancia predeterminada. Por ejemplo, la siguiente instrucción WQL devolverá información sobre todos los archivos de registro de la instancia predeterminada (MSSQLSERVER).  
  
```  
"SELECT * FROM SqlErrorLogFile"  
```  
  
## <a name="security"></a>Seguridad  
 Para conectarse a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] archivo de registro a través de WMI, debe tener los siguientes permisos en los equipos locales y remotos:  
  
-   Acceso de lectura al espacio de nombres WMI **Root\Microsoft\SqlServer\ComputerManagement10** . De forma predeterminada, todos tienen acceso de lectura mediante el permiso Habilitar cuenta.  
  
    > [!NOTE]  
    >  Para obtener información sobre cómo comprobar los permisos de WMI, consulte la sección seguridad del tema [ver archivos de registro sin conexión](../logs/view-offline-log-files.md).  
  
-   Permiso de lectura a la carpeta que contiene los registros de errores. De forma predeterminada, los registros de errores se encuentran en la siguiente ruta de acceso (donde \<*Drive> * representa la unidad donde se instaló [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y \<*InstanceName*> es el nombre de la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ):  
  
     ** \<Drive> : \Archivos de Programa\microsoft SQL Server\MSSQL11** **. \<InstanceName> \Mssql\log.**  
  
 Si se conecta a través de un firewall, asegúrese de que se establece una excepción en el firewall para WMI en los equipos de destino remotos. Para obtener más información, consulte [conectarse a WMI de forma remota a partir de Windows Vista](https://go.microsoft.com/fwlink/?LinkId=178848).  
  
## <a name="see-also"></a>Consulte también  
 [Clase SqlErrorLogEvent](sqlerrorlogevent-class.md)   
 [Ver archivos del registro sin conexión](../logs/view-offline-log-files.md)  
  
  
