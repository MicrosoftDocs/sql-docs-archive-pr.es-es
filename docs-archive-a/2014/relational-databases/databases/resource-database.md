---
title: Base de datos Resource | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- system objects [SQL Server]
- read-only databases
- mssqlsystemresource.mdf file
- Resource database [SQL Server]
ms.assetid: d592b2b4-bc36-4eb9-9385-8fe4dff0dced
author: stevestein
ms.author: sstein
ms.openlocfilehash: cca2f9e1ff6069a608beb1df1880b37e15f4e869
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672089"
---
# <a name="resource-database"></a>Base de datos Resource
  La base de datos Resource es de solo lectura y contiene todos los objetos del sistema que se incluyen con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objetos del sistema, tales como sys.objects, persisten físicamente en la base de datos Resource, pero aparecen lógicamente en el esquema sys de cada base de datos. La base de datos Resource no contiene datos o metadatos del usuario.  
  
 La base de datos de recursos hace que el procedimiento de actualizar a una versión nueva de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sea más rápido y sencillo. En versiones anteriores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la actualización requiere quitar y crear los objetos del sistema. Como el archivo de la base de datos Resource contiene todos los objetos del sistema, ahora para realizar una actualización basta con copiar el único archivo de base de datos Resource en el servidor local.  
  
## <a name="physical-properties-of-resource"></a>Propiedades físicas de recurso  
 Los nombres de archivos físicos de la base de datos de recursos son mssqlsystemresource.mdf y mssqlsystemresource.ldf. Estos archivos se encuentran en \<*drive*>:\Archivos de programa\Microsoft SQL Server\MSSQL\<version>.\<*instance_name*>\MSSQL\Binn\ y no deben cambiarse. Cada instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tiene un solo archivo mssqlsystemresource.mdf asociado y las instancias no lo comparten.  
  
> [!WARNING]  
>  En ocasiones, las actualizaciones y los paquetes de servicios ofrecen una base de datos de nuevos recursos, que se instala en la carpeta BINN. No es compatible ni recomendable cambiar la ubicación de la base de datos de recursos.  
  
## <a name="backing-up-and-restoring-the-resource-database"></a>Realizar copias de seguridad y restaurar la base de datos Resource  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no puede hacer una copia de seguridad de la base de datos de recursos. Puede realizar su propia copia de seguridad basada en archivos o en un disco si trata el archivo mssqlsystemresource.mdf como si fuera binario (.EXE), en lugar de un archivo de base de datos, pero no puede utilizar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para restaurar las copias de seguridad. La restauración de una copia de seguridad de mssqlsystemresource.mdf solo se puede hacer de forma manual y hay que tener cuidado de no sobrescribir la base de datos Resource actual con una versión desusada potencialmente insegura.  
  
> [!IMPORTANT]  
>  Después de restaurar una copia de seguridad de mssqlsystemresource.mdf, debe volver a aplicar cualquier actualización posterior.  
  
## <a name="accessing-the-resource-database"></a>Acceso a la base de datos Resource  
 Solo un experto de los Servicios de soporte al cliente (CSS) de Microsoft debe modificar o dirigir la modificación de la base de datos Resource. El identificador de la base de datos Resource siempre es 32767. Otros valores importantes asociados a la base de datos Resource son el número de versión y la última vez que se actualizó la base de datos.  
  
 **Para determinar el número de versión de la base de datos** Resource **utilice**:  
  
```  
SELECT SERVERPROPERTY('ResourceVersion');  
GO  
```  
  
 **Para determinar cuándo se actualizó por última vez la base de datos** Resource **, utilice**:  
  
```  
SELECT SERVERPROPERTY('ResourceLastUpdateDateTime');  
GO  
```  
  
 **Para obtener acceso a definiciones SQL de objetos del sistema, use la función OBJECT_DEFINITION:**  
  
```  
SELECT OBJECT_DEFINITION(OBJECT_ID('sys.objects'));  
GO  
```  
  
## <a name="related-content"></a>Contenido relacionado  
 [Bases de datos del sistema](system-databases.md)  
  
 [Conexión de diagnóstico para administradores de bases de datos](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)  
  
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql)  
  
 [SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql)  
  
 [Iniciar SQL Server en modo de usuario único](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)  
  
  
