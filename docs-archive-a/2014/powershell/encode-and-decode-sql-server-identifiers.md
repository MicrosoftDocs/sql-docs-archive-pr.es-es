---
title: Codificar y descodificar identificadores de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: bb9fe0d3-e432-42d3-b324-64dc908b544a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 88e7ebbc81d9c3cb91b1bf678075c5b5d0884890
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744732"
---
# <a name="encode-and-decode-sql-server-identifiers"></a>Codificar y descodificar identificadores de SQL Server
  Los identificadores delimitados de SQL Server a veces contienen caracteres no admitidos en las rutas de acceso de Windows PowerShell. Estos caracteres se pueden especificar codificando sus valores hexadecimales.  
  
1.  **Antes de empezar:**  [Limitaciones y restricciones](#LimitationsRestrictions)  
  
2.  **Para procesar los caracteres especiales:**  [Codificar un identificador](#EncodeIdent), [Descodificar un identificador](#DecodeIdent)  
  
## <a name="before-you-begin"></a>Antes de empezar  
 Los caracteres que no se admiten en los nombres de ruta de acceso de Windows PowerShell se pueden representar, o codificar, como el carácter "%" seguido del valor hexadecimal del patrón de bits que representa el carácter, como en " **%** XX". La codificación siempre se puede usar para controlar los caracteres que no se admiten en las rutas de Windows PowerShell.  
  
 El cmdlet **Encode-SqlName** toma como entrada un identificador de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Genera una cadena con todos los caracteres que no son admitidos por el lenguaje de Windows PowerShell codificados con "%xx". El cmdlet **Decode-SqlName** toma como entrada un identificador de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] codificado y devuelve el identificador original.  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Limitaciones y restricciones  
 Los cmdlets de `Encode-Sqlname` y de `Decode-Sqlname` solo codifican o descodifican caracteres que se permiten en los identificadores delimitados de SQL Server, pero no solo se admiten en las rutas de PowerShell. Estos son los caracteres codificados por **Encode-SqlName** y descodificados por **Decode-SqlName**:  
  
|||||||||||||  
|-|-|-|-|-|-|-|-|-|-|-|-|  
|**Carácter**|\ |/|:|%|\<|>|*|?|[|]|&#124;|  
|**Codificación hexadecimal**|%5C|%2F|%3A|%25|%3C|%3E|%2A|%3F|%5B|%5D|%7C|  
  
##  <a name="encoding-an-identifier"></a><a name="EncodeIdent"></a> Codificar un identificador  
 **Para codificar un identificador de SQL Server en una ruta de acceso de PowerShell**  
  
-   Use uno de los dos métodos para codificar un identificador de SQL Server:  
  
    -   Especifique el código hexadecimal para el carácter no compatible mediante la sintaxis %XX, donde el código hexadecimal es XX.  
  
    -   Pase el identificador como una cadena entrecomillada al cmdlet `Encode-Sqlname`  
  
### <a name="examples-encoding"></a>Ejemplos (codificación)  
 Este ejemplo especifica la versión codificada del carácter (%3A) ":":  
  
```  
Set-Location Table%3ATest  
```  
  
 También puede usar **Encode-SqlName** para compilar un nombre admitido por Windows PowerShell:  
  
```powershell
Set-Location (Encode-SqlName "Table:Test")  
```  
  
##  <a name="decoding-an-identifier"></a><a name="DecodeIdent"></a> Descodificar un identificador  
 **Descodificar un identificador de SQL Server de una ruta de PowerShell**  
  
 Use el cmdlet `Decode-Sqlname` para reemplazar las codificaciones hexadecimales con caracteres representados por la codificación.  
  
### <a name="examples-decoding"></a>Ejemplos (descodificación)  
 Este ejemplo devuelve “Table:Test”:  
  
```powershell
Decode-SqlName "Table%3ATest"  
```  
  
## <a name="see-also"></a>Consulte también  
 [SQL Server identificadores en PowerShell](sql-server-identifiers-in-powershell.md)   
 [Proveedor de SQL Server PowerShell](sql-server-powershell-provider.md)   
 [SQL Server PowerShell](sql-server-powershell.md)  
