---
title: MSSQLSERVER_18452 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18456 (Database Engine error)
- 18452 (Database Engine error)
ms.assetid: 21da332c-e81d-4dee-a9d2-95598911b3be
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5786d5de4748f6bbf59d2bd4acecd7ca77977f11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674141"
---
# <a name="mssqlserver_18452"></a>MSSQLSERVER_18452
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre de producto|SQL Server|  
|Id. de evento|18452|  
|Origen de eventos|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|LOGON_INVALID_CONNECT|  
|Texto del mensaje|Error de inicio de sesión del usuario '%.*ls'. El inicio de sesión es un inicio de sesión de SQL Server y no se puede usar con la autenticación de Windows.%.\*ls|  
  
## <a name="explanation"></a>Explicación  
 El usuario intentó iniciar sesión con credenciales que no se pueden validar. Las posibles causas son:  
  
-   El inicio de sesión puede ser un inicio de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pero el servidor solo acepta la autenticación de Windows.  
  
-   Intenta conectar utilizando la autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pero el inicio de sesión utilizado no existe en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   El inicio de sesión puede utilizar la autenticación de Windows pero el inicio de sesión es una entidad de seguridad de Windows no reconocida. Una entidad de seguridad de Windows no reconocida significa que Windows no puede comprobar el inicio de sesión. Esto podría deberse a que el inicio de sesión de Windows procede de un dominio que no es de confianza.  
  
 Problemas similares pueden producir el error menos específico 18456.  
  
## <a name="user-action"></a>Acción del usuario  
 Si intenta establecer conexión usando la Autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], compruebe que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] está configurado en modo de autenticación mixto.  
  
 Si intenta establecer conexión usando la autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], compruebe que el inicio de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] existe.  
  
 Si intenta establecer conexión usando la Autenticación de Windows, compruebe que está registrado correctamente en el dominio correcto.  
  
  
