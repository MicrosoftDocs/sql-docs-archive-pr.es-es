---
title: Tarea Comprobar la integridad de la base de datos (Plan de mantenimiento) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.maintplanproperties.integrity.f1
- sql12.swb.maint.integrity.f1
helpviewer_keywords:
- Check Database Integrity Task dialog box
ms.assetid: 3534494a-5dfe-4738-b49a-e7fabd731c47
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f786755a3b7ed5d991b4cf0e32c067e355c111ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87675356"
---
# <a name="check-database-integrity-task-maintenance-plan"></a>Tarea Comprobar la integridad de la base de datos (Plan de mantenimiento)
  Utilice el cuadro de diálogo **Tarea Comprobar la integridad de la base de datos** para comprobar la asignación e integridad estructural de las tablas de usuario y del sistema, y los índices de la base de datos por medio de la ejecución de la instrucción `DBCC CHECKDB`[!INCLUDE[tsql](../../includes/tsql-md.md)] . La ejecución de `DBCC` garantiza que se notifiquen todos los problemas de integridad que puedan existir en la base de datos, lo que permitirá su tratamiento posterior por parte de un administrador del sistema o del propietario de la base de datos.  
  
## <a name="options"></a>Opciones  
 **Connection**  
 Seleccione la conexión al servidor que va a utilizar para la realización de esta tarea.  
  
 **Nuevo**  
 Cree una nueva conexión de servidor que utilizará al realizar esta tarea. El cuadro de diálogo **Nueva conexión** se describe a continuación.  
  
 **Bases de datos**  
 Especifique las bases de datos a las que afecta esta tarea.  
  
-   **Todas las bases de datos**  
  
     Genere un plan de mantenimiento que ejecute tareas de mantenimiento en todas las bases de datos de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a excepción de **tempdb**.  
  
-   **Todas las bases de datos del sistema**  
  
     Genera un plan de mantenimiento que ejecuta tareas de mantenimiento en todas las bases de datos del sistema de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , a excepción de **tempdb**. No se ejecutarán tareas de mantenimiento en las bases de datos creadas por usuarios.  
  
-   **Todas las bases de datos de usuario**  
  
     Genera un plan de mantenimiento que ejecuta tareas de mantenimiento en todas las bases de datos creadas por usuarios. No se ejecutarán tareas de mantenimiento en las bases de datos del sistema de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   **Las bases de datos**  
  
     Genera un plan de mantenimiento que ejecuta tareas de mantenimiento únicamente en las bases de datos seleccionadas. Si elige esta opción, deberá seleccionar al menos una base de datos de la lista.  
  
    > [!NOTE]  
    >  Los planes de mantenimiento solo se ejecutan en bases de datos con un nivel de compatibilidad de 80 o superior. Las bases de datos con un nivel de compatibilidad de 70 o inferior no se muestran.  
  
 **Incluir índices**  
 Comprueba la integridad de todas las páginas de índice y de todas las páginas de datos de tabla.  
  
 **Ver T-SQL**  
 Muestra las instrucciones [!INCLUDE[tsql](../../includes/tsql-md.md)] realizadas en el servidor para esta tarea, en función de las opciones seleccionadas.  
  
> [!NOTE]  
>  Si el número de objetos afectados es elevado, es posible que deba esperar un rato hasta que se muestren.  
  
## <a name="new-connection-dialog-box"></a>Cuadro de diálogo Nueva conexión  
 **Nombre de la conexión**  
 Escriba un nombre para la nueva conexión.  
  
 **Seleccionar o especificar un nombre de servidor**  
 Seleccione un servidor al que conectarse cuando se realice esta tarea.  
  
 **Actualizar**  
 Actualiza la lista de servidores disponibles.  
  
 **Especificar información para iniciar sesión en el servidor**  
 Especifica el modo de autenticación en el servidor.  
  
 **Usar seguridad integrada de Windows NT**  
 Conéctese a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] con autenticación de Windows.  
  
 **Utilizar un nombre de usuario y una contraseña específicos**  
 Conéctese a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] mediante autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Esta opción no está disponible.  
  
 **Nombre de usuario**  
 Proporcione un inicio de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para la autenticación. Esta opción no está disponible.  
  
 **Contraseña**  
 Proporcione una contraseña para que se utilice en la autenticación. Esta opción no está disponible.  
  
## <a name="see-also"></a>Consulte también  
 [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  
