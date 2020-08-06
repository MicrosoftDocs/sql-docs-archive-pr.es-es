---
title: Solo los usuarios de sysadmin pueden escribir archivos de registro de pasos de trabajo en el sistema de archivos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- job step log files [SQL Server Agent]
- log files [SQL Server Agent]
- writing job step log files
ms.assetid: d26a7cef-1a60-4c95-b9df-f8b4fec59f9b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9e2bf5095ac1e6b67f6c6f3f87444879913916e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673443"
---
# <a name="only-sysadmin-users-can-write-job-step-log-files-to-the-file-system"></a>Los administradores del sistema son los únicos usuarios que pueden escribir archivos de registro de paso de trabajo en el sistema de archivos
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] escribe opcionalmente un registro para cada paso de trabajo.  
  
## <a name="component"></a>Componente  
 e[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
## <a name="description"></a>Descripción  
 En [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] , [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] el agente puede escribir registros en el sistema de archivos para los trabajos que son propiedad de los miembros del rol fijo de servidor **sysadmin** . Si el propietario del trabajo no es miembro del rol **sysadmin** y la cuenta de proxy está habilitada, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agente puede escribir registros en el sistema de archivos mediante las credenciales de la cuenta de proxy.  
  
 Después de la actualización, los trabajos que pertenecen a usuarios que no son miembros del rol fijo de servidor **sysadmin** ya no pueden escribir registros en el sistema de archivos. En su lugar, estos usuarios pueden seleccionar la opción de escribir los registros en una tabla de la base de datos **msdb** . Los miembros del rol **sysadmin** pueden seguir escribiendo archivos de registro en el sistema de archivos.  
  
## <a name="corrective-action"></a>Acción correctora  
 Después de la actualización, los trabajos que pertenecen a usuarios que no son miembros del rol **sysadmin** seguirán ejecutándose, pero no se crearán los registros. Para registrar los pasos de trabajo en una tabla, los usuarios que no sean miembros del rol **sysadmin** deben actualizar manualmente sus trabajos.  
  
 Para obtener más información, vea los temas "Crear trabajos", "Crear pasos de trabajo" y "Controlar varios pasos del trabajo" en los Libros en pantalla de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Consulte también  
 [Problemas de actualización del Agente SQL Server](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
