---
title: Acceso a código nativo desde una UDF de CLR | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: 161afa9d-74a1-40f5-af17-162e355e7a46
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d36e93fc39e9231a4d8677535c6e13c905d55a4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87670545"
---
# <a name="accessing-native-code-from-a-clr-udf"></a>Acceso a código nativo desde una UDF de CLR
  Este ejemplo muestra cómo invocar una función en código C++ nativo (no administrado) desde una función definida por el usuario en un ensamblado, en la base de datos.  
  
 En este ejemplo, el directorio de trabajo debe ser `c:\test` .  
  
 Primero compile el código C++:  
  
```  
// Win32Sleep.cpp  
// compile with: /LD /link /noentry kernel32.lib  
#include <windows.h>  
  
extern "C"  
__declspec( dllexport ) void _cdecl SleepyLoop(DWORD sleep_interval) {  
   Sleep(sleep_interval);  
}  
```  
  
 A continuación, compile el código C# en un ensamblado:  
  
```  
// proc.cs  
// compile with: /target:library  
using System;  
using System.Threading;  
using System.Data.Sql;  
using System.Runtime.InteropServices;  
  
public class StoreProcedures {  
  
   public static readonly uint SLEEP_LOOP_TIMES = 10;  
   public static readonly uint SLEEP_DURATION = 1000;  
  
   [DllImport(@"c:\test\Win32Sleep.dll")]  
   internal static extern void SleepyLoop(uint sleepInterval);  
  
   public static void SleepInProcedure(int loopTimes) {  
      for ( int i = 0 ; i < loopTimes ; i++ ) {  
         // invoke the unmanaged routine  
         SleepyLoop(SLEEP_DURATION);  
      }  
   }  
}  
```  
  
 Por último, ejecute los siguientes comandos [!INCLUDE[tsql](../../includes/tsql-md.md)]:  
  
```  
USE MASTER  
GO  
  
IF DB_ID('testdb') IS NOT NULL  
DROP DATABASE testdb  
GO  
  
CREATE DATABASE testdb  
GO  
  
USE testdb  
GO  
  
ALTER DATABASE testdb SET TRUSTWORTHY ON   
GO  
  
sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
  
CREATE ASSEMBLY myasm FROM 'c:\test\proc.dll' WITH PERMISSION_SET=UNSAFE   
go  
  
CREATE PROCEDURE SleepProc(@loopTimes INT)  
AS EXTERNAL NAME myasm.[StoreProcedures].[SleepInProcedure]  
go  
  
-- sleep 5 seconds  
EXEC SleepProc 5  
GO  
```  
  
## <a name="see-also"></a>Consulte también  
 [Escenarios de uso y ejemplos para la integración de Common Language Runtime &#40;CLR&#41;](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  
