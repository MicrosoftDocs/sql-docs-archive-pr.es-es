---
title: Programa externo de Correo electrónico de base de datos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- external programs [Database Mail]
- DatabaseMail90.exe
- Database Mail [SQL Server], external programs
ms.assetid: bc124164-eb6e-4b7f-bf66-98a3113d02f7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 698fc8d97a565b4181552691a0260486c9c43bfd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751166"
---
# <a name="database-mail-external-program"></a>Programa externo Correo electrónico de base de datos
  El ejecutable externo de Correo electrónico de base de datos es **DatabaseMail.exe**, que está ubicado en el directorio **MSSQL\Binn directory** de la instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Correo electrónico de base de datos utiliza la activación de Service Broker para iniciar el programa externo cuando es necesario procesar mensajes de correo electrónico. Correo electrónico de base de datos inicia una instancia del programa externo. El programa externo se ejecuta en el contexto de seguridad de la cuenta de servicio de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **En este tema:**  
  
-   [Conceptos del programa externo de Correo electrónico de base de datos](#ComponentsAndConcepts)  
  
-   [Tareas relacionadas con la configuración del programa externo de Correo electrónico de base de datos](#RelatedTasks)  
  
##  <a name="database-mail-external-program-concepts"></a><a name="ComponentsAndConcepts"></a> Conceptos del programa externo de Correo electrónico de base de datos  
 Cuando se inicia el programa externo, se conecta a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mediante la autenticación de Windows y empieza a procesar los mensajes de correo electrónico. El programa termina cuando ya no hay mensajes para enviar durante el período de tiempo de espera especificado. Si lo desea, puede configurar el tiempo que el programa debe esperar antes de terminar mediante el Asistente para configuración de Correo electrónico de base de datos o los procedimientos almacenados de Correo electrónico de base de datos. Para obtener más información, vea [sysmail_configure_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql).  
  
 El programa externo almacena información de las tablas del sistema en la base de datos **msdb** . Si el programa externo no puede comunicarse con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], registrará una serie de errores en el registro de eventos de aplicación de Microsoft Windows. Se proporcionan funciones de registro de mensajes adicionales cuando el nivel de registro está establecido en **Detallado** en el cuadro de diálogo **Configurar parámetros del sistema** del **Asistente para configuración de Correo electrónico de base de datos**.  
  
 Por motivos de eficacia, el programa externo almacena en la memoria caché la información de la cuenta y del perfil. Por lo tanto, los cambios de configuración que se realicen en las cuentas y los perfiles no surtirán efecto en el programa externo hasta pasados unos minutos.  
  
##  <a name="tasks-related-to-configuring-database-mail-external-program"></a><a name="RelatedTasks"></a> Tareas relacionadas con la configuración del programa externo de Correo electrónico de base de datos  
  
|Tarea de configuración|Vínculo de tema|  
|------------------------|----------------|  
|Especifique el tiempo que el programa externo espera antes de salir.|[sysmail_configure_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql)|  
  
## <a name="see-also"></a>Consulte también  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)   
 [Registro y auditorías del Correo electrónico de base de datos](database-mail-log-and-audits.md)   
 [Correo electrónico de base de datos](database-mail.md)  
  
  
