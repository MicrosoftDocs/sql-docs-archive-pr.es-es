---
title: MSSQLSERVER_33028 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33028 (Database Engine error)
ms.assetid: c5cec0e4-0bcd-4907-826f-e7d835cfcb37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 555dcf0220793abc0e8af81b3f56867f9960c5f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672055"
---
# <a name="mssqlserver_33028"></a>MSSQLSERVER_33028
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre de producto|SQL Server|  
|Id. de evento|33028|  
|Origen de eventos|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|SEC_CRYPTOPROV_CANTOPENSESSION|  
|Texto del mensaje|No se puede abrir la sesión para %S_MSG '%.*ls'. Código de error de proveedor: %d.|  
  
## <a name="explanation"></a>Explicación  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no pudo abrir el proveedor de servicios criptográficos enumerado en el mensaje de error. El proveedor de servicios criptográficos proporcionó el código de error enumerado. Puede que tenga que ponerse en contacto con su proveedor de servicios criptográficos para obtener más información sobre el error.  
  
|Código de error|Descripción|  
|----------------|-----------------|  
|0|Correcto. Ningún error.|  
|1|Error. Se ha producido un error no especificado o inesperado. No se dispone de información adicional.|  
|2|Búfer insuficiente. No se pudo asignar espacio para el proveedor de servicios criptográficos.|  
|3|No compatible. El proveedor de servicios criptográficos no admite esta versión. Seleccione otro proveedor de servicios criptográficos.|  
|4|Not Found. El proveedor de servicios criptográficos especificado no está presente o no se tiene autorización para el acceso a los archivos.|  
|5|Error de autorización. Puede ser el resultado de proporcionar un nombre de usuario o una contraseña incorrectos al crear la credencial. Puede producirse si la credencial no existe.|  
|6|Argumento no válido. Se ha pasado un argumento no válido al proveedor de servicios criptográficos.|  
  
## <a name="user-action"></a>Acción del usuario  
 Resuelva el error o póngase en contacto con el proveedor de servicios criptográficos para obtener más información.  
  
  
