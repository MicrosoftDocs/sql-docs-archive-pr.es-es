---
title: Compatibilidad con UTF-16 en SQL Server Native Client 11,0 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: f2520424-8ef4-409f-8147-d83da5076e96
author: rothja
ms.author: jroth
ms.openlocfilehash: af8581071400db888fb508b88f8e8ae93bc71f70
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87675307"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a>Compatibilidad con UTF-16 en SQL Server Native Client 11.0
  A partir de [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] , si se proporciona un búfer de longitud fija al enlazar un resultado de columna o un parámetro de salida y si el `wchar` carácter escrito en el búfer antes del carácter de terminación es un punto de código suplente alto de un par suplente, y si el siguiente `wchar` carácter es un punto de código suplente bajo, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client no agregará el punto de código suplente alto al búfer.  
  
## <a name="see-also"></a>Consulte también  
 [Características de SQL Server Native Client](sql-server-native-client-features.md)  
  
  
