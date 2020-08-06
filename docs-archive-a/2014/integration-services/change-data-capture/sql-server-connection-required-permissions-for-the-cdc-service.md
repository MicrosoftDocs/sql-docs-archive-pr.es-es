---
title: Permisos de conexión con SQL Server necesarios para CDC Service | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: d9e968f9-180c-4fa0-a849-98f2b1942330
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e63b98ffd0371bd5b70ecc0ac843ad40a4a5d03e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87671630"
---
# <a name="sql-server-connection-required-permissions-for-the-cdc-service"></a>Permisos de conexión con SQL Server necesarios para el servicio CDC
  La Consola de configuración del servicio CDC necesita información de conexión con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para realizar sus tareas. En este tema se describe la información que se puede proporcionar en el cuadro de diálogo Conectar con SQL Server para configurar la conexión con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 El cuadro de diálogo Conectar con SQL Server se abre cuando es necesario, como cuando la información de conexión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no está disponible o si existe la información pero la conexión no tiene los permisos necesarios.  
  
 En la tabla siguiente se describen las diversas tareas en las que se necesita una conexión con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y los permisos que necesita el inicio de sesión o el usuario de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Tarea|Permisos mínimos|  
|----------|-------------------------|  
|Preparar la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|`dbcreator` Rol fijo de servidor|  
|Crear un inicio de sesión del servicio CDC de Oracle de SQL Server para su uso por parte del servicio CDC de Oracle.|`public` Rol fijo de servidor|  
|Crear un inicio de sesión del servicio CDC de Oracle que se usará para registrar el nuevo servicio en MSXDBCDC.|`db_datareader` y `db_datawriter` en MSXDBCDC|  
|Editar un inicio de sesión del servicio CDC de Oracle que se usará para actualizar el registro del servicio en MSXDBCDC.|`db_datareader` y `db_datawriter` en MSXDBCDC|  
|Eliminar un inicio de sesión del servicio CDC de Oracle que se usará para actualizar el registro del servicio en MSXDBCDC.|`db_datareader` y `db_datawriter` en MSXDBCDC|  
  
## <a name="see-also"></a>Consulte también  
 [Conexión con SQL Server](connection-to-sql-server.md)   
 [Conexión con SQL Server para eliminación](connection-to-sql-server-for-delete.md)  
  
  
