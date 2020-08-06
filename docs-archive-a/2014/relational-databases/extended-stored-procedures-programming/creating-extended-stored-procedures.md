---
title: Crear procedimientos almacenados extendidos | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- warnings [SQL Server]
- extended stored procedures [SQL Server], debugging
- extended stored procedures [SQL Server], creating
- messages [SQL Server], extended stored procedures
ms.assetid: 9f7c0cdb-6d88-44c0-b049-29953ae75717
author: rothja
ms.author: jroth
ms.openlocfilehash: d243b27b8542ec5fe10d795de1729d6c1fe484c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87675390"
---
# <a name="creating-extended-stored-procedures"></a>Crear procedimientos almacenados extendidos
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] En su lugar, utilice la integración con CLR.  
  
 Un procedimiento almacenado extendido es una función con un prototipo:  
  
 *Xp_extendedProcName* SRVRETCODE **(** SRVPROC ** \* );**  
  
 El uso del prefijo xp_ es opcional. Los nombres de procedimiento almacenado extendido distinguen mayúsculas de minúsculas cuando se hace referencia a ellos en instrucciones [!INCLUDE[tsql](../../includes/tsql-md.md)], independientemente de la página de códigos o criterio de ordenación que se haya instalado en el servidor. Cuando genere un archivo DLL:  
  
-   Si se necesita un punto de entrada, escriba una función DllMain.  
  
     Esta función es opcional; si no se proporciona en código fuente, el compilador vincula su propia versión, que solo devuelve TRUE. Si se proporciona una función DllMain, el sistema operativo llama a esta función cuando se adjunta o se separa un proceso o subproceso en el archivo DLL.  
  
-   Deben exportarse todas las funciones a las que se llama desde el exterior del archivo DLL (todas las funciones Efunction de procedimiento almacenado extendido).  
  
     Puede exportar una función enumerando su nombre en la sección Exports de un archivo. def o puede anteponer el nombre de función en el código fuente con __declspec (dllexport), una extensión de compilador de Microsoft (tenga en cuenta que \_ _declspec () comienza con dos guiones bajos).  
  
 Estos archivos son necesarios para crear un archivo DLL de procedimientos almacenados extendidos.  
  
|Archivo|Descripción|  
|----------|-----------------|  
|Srv.h|Archivo de encabezado de la API Procedimiento almacenado extendido|  
|Opends60.lib|Biblioteca de importación de Opends60.dll|  
  
 Para crear un archivo DLL de procedimientos almacenados extendidos, cree un proyecto de tipo biblioteca de vínculos dinámicos. Para obtener más información sobre la forma de crear un archivo DLL, vea la documentación del entorno de desarrollo.  
  
 Se recomienda encarecidamente que todos los archivos DLL de procedimientos almacenados extendidos implementen y exporten la siguiente función:  
  
```  
__declspec(dllexport) ULONG __GetXpVersion()  
{  
   return ODS_VERSION;  
}  
```  
  
> [!NOTE]  
>  __declspec(dllexport) es una extensión de compilador específica de Microsoft. Si el compilador no admite esta directiva, debe exportar esta función en el archivo DEF, bajo la sección EXPORTS.  
  
 Cuando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se inicia con la marca de seguimiento-T260 o si un usuario con privilegios de administrador del sistema ejecuta DBCC TRACEON (260), y si la dll de procedimiento almacenado extendido no admite __GetXpVersion (), un mensaje de advertencia (Error 8131: el archivo dll de procedimientos almacenados extendidos '% ' no exporta \_ _GetXpVersion ().) se imprime en el registro de errores. (Tenga en cuenta que \_ _GetXpVersion () comienza con dos guiones bajos).  
  
 Si el archivo DLL de procedimientos almacenados extendidos exporta __GetXpVersion() pero la versión devuelta por la función es menor que la que requiere el servidor, en el registro de errores se imprime un mensaje de advertencia que indica la versión devuelta por la función y la versión esperada por el servidor. Si recibe este mensaje, devuelve un valor incorrecto de \_ _GetXpVersion () o está compilando con una versión anterior de SRV. h.  
  
> [!NOTE]  
>  No debe llamarse a SetErrorMode, una función Win32 de [!INCLUDE[msCoName](../../includes/msconame-md.md)], en procedimientos almacenados extendidos.  
  
 Se recomienda que un procedimiento almacenado extendido de ejecución prolongada llame periódicamente a srv_got_attention para que el procedimiento pueda finalizarse si se elimina la conexión o se anula el lote.  
  
 Para depurar un archivo DLL de procedimientos almacenados extendidos, cópielo en el directorio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\Binn. Para especificar el archivo ejecutable para la sesión de depuración, escriba la ruta de acceso y el nombre del archivo [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ejecutable (por ejemplo, C:\Archivos de programa\microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Sqlservr.exe). Para obtener información acerca de los argumentos de sqlservr, vea [sqlservr Application](../../tools/sqlservr-application.md).  
  
## <a name="see-also"></a>Consulte también  
 [srv_got_attention API de procedimiento almacenado extendido &#40;&#41;](../extended-stored-procedures-reference/srv-got-attention-extended-stored-procedure-api.md)  
  
  
