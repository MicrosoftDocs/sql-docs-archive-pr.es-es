---
title: Identificadores de SQL Server de escape | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 8a73e945-daa6-4e5d-93da-10f000f1f3a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1821187632aeeea0b7a18bf9c4d51d933e947d43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673053"
---
# <a name="escape-sql-server-identifiers"></a>Identificadores de SQL Server de escape
  A menudo, se puede usar el carácter de escape de acento invertido (`) de Windows PowerShell para hacer que se eludan los caracteres que se permiten en los identificadores delimitados de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pero no en los nombres de ruta de Windows PowerShell. Sin embargo, algunos caracteres no se pueden evitar. Por ejemplo, no puede hacer que se eluda el carácter de dos puntos (:) en Windows PowerShell. Los identificadores con ese carácter deben codificarse. La codificación es más confiable que hacer que el carácter se eluda porque funciona para todos los caracteres.  
  
## <a name="before-you-begin"></a>Antes de empezar  
 El carácter de acento invertido (`) suele estar en la tecla de la parte superior izquierda del teclado, debajo de la tecla ESC.  
  
## <a name="examples"></a>Ejemplos  
 Este es un ejemplo en el que se hace que se eluda un carácter #:  
  
```  
cd SQLSERVER:\SQL\MyComputer\MyInstance\MyDatabase\MySchema\`#MyTempTable  
```  
  
 Este es un ejemplo en el que se hace que se eluda un paréntesis al especificar (local) como nombre de equipo:  
  
```  
Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
```  
  
## <a name="see-also"></a>Consulte también  
 [SQL Server identificadores en PowerShell](sql-server-identifiers-in-powershell.md)   
 [Proveedor de SQL Server PowerShell](sql-server-powershell-provider.md)   
 [SQL Server PowerShell](sql-server-powershell.md)  
  
  
