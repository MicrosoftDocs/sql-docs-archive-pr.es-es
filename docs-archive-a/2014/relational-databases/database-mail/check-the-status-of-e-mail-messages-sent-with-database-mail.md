---
title: Comprobación del estado de los mensajes de correo electrónico enviados con Correo electrónico de base de datos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- e-mail [SQL Server], status information
- mail [SQL Server], status information
- Database Mail [SQL Server], message status
- status information [Database Mail]
ms.assetid: eb290f24-b52f-46bc-84eb-595afee6a5f3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1642c456cd64484dede64f8127ff2f979f2242e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87677666"
---
# <a name="check-the-status-of-e-mail-messages-sent-with-database-mail"></a>Comprobar el estado de los mensajes de correo electrónico enviados con Correo electrónico de base de datos
  En este tema se describe cómo comprobar el estado del mensaje de correo electrónico enviado con Correo electrónico de base de datos en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   **Antes de empezar:**  
  
-   **Para ver el estado del correo electrónico enviado con Correo electrónico de base de datos, mediante:**  [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de comenzar  
 Correo electrónico de base de datos conserva copias de los mensajes de correo electrónico salientes y las muestra en las vistas **sysmail_allitems**, **sysmail_sentitems**, **sysmail_unsentitems**y **sysmail_faileditems** de la base de datos **msdb** . El programa externo de Correo electrónico de base de datos registra la actividad y muestra ese registro por medio del registro de eventos de aplicación Windows y la vista **sysmail_event_log** de la base de datos **msdb** . Para comprobar el estado de un mensaje de correo electrónico, ejecute una consulta en esta vista. Los mensajes de correo electrónico tienen cuatro posibles estados: **enviado**, **no enviado**, **reintentando**y **error**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Usar Transact-SQL  
 **Para ver el estado del correo electrónico enviado con Correo electrónico de base de datos**  
  
> [!NOTE]  
>  Para ver un ejemplo de este procedimiento, vea [Ejemplo (Transact-SQL)](#TsqlExample)más adelante en esta sección.  
  
1.  Seleccione los mensajes que le interesen de la tabla **sysmail_allitems** por medio de **mailitem_id** o **sent_status**.  
  
2.  Para comprobar el estado devuelto por el programa externo para los mensajes de correo electrónico, combine las vistas **sysmail_allitems** y **sysmail_event_log** en la columna **mailitem_id** , como se muestra en la sección siguiente.  
  
     De forma predeterminada, el programa externo no registra información acerca de los mensajes que se enviaron correctamente. Para registrar todos los mensajes, establezca el nivel de registro en detallado mediante la página **Configurar parámetros del sistema** del **Asistente para configuración de Correo electrónico de base de datos**.  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> Ejemplo (Transact-SQL)  
 En el siguiente ejemplo se muestra información acerca de los mensajes de correo electrónico enviados a `danw` que el programa externo no ha podido enviar correctamente. La instrucción incluye el asunto, la fecha y la hora en que el programa externo no pudo enviar el mensaje, así como el mensaje de error del registro de Correo electrónico de base de datos.  
  
```  
USE msdb ;  
GO  
  
-- Show the subject, the time that the mail item row was last  
-- modified, and the log information.  
-- Join sysmail_faileditems to sysmail_event_log   
-- on the mailitem_id column.  
-- In the WHERE clause list items where danw was in the recipients,  
-- copy_recipients, or blind_copy_recipients.  
-- These are the items that would have been sent  
-- to danw.  
  
SELECT items.subject,  
    items.last_mod_date  
    ,l.description FROM dbo.sysmail_faileditems as items  
INNER JOIN dbo.sysmail_event_log AS l  
    ON items.mailitem_id = l.mailitem_id  
WHERE items.recipients LIKE '%danw%'    
    OR items.copy_recipients LIKE '%danw%'   
    OR items.blind_copy_recipients LIKE '%danw%'  
GO  
```  
  
## <a name="see-also"></a>Consulte también  
 [Registro y auditorías del Correo electrónico de base de datos](database-mail-log-and-audits.md)  
  
  
