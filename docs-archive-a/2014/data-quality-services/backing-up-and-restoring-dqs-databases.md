---
title: Realizar copias de seguridad de bases de datos de DQS y restaurarlas | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f3091f62-2234-4a80-a615-cf14c2a1da85
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 489664d8c64a99d1ea4dcec79b93e5b01b28f649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663737"
---
# <a name="backing-up-and-restoring-dqs-databases"></a>Realizar copias de seguridad de bases de datos de DQS y restaurarlas
  En este tema se describe cómo realizar copias de seguridad de las bases de datos de DQS y cómo restaurarlas.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Requisitos previos  
  
-   Debe saber o recordar la contraseña de la clave maestra de base de datos que proporcionó durante la instalación del servidor DQS.  
  
-   Asegúrese de que no haya actividades o procesos de DQS en ejecución. Utilice la pantalla **Supervisión de actividades** para comprobarlo. Para obtener información detallada sobre cómo utilizar esta pantalla, vea [Monitor DQS Activities](../../2014/data-quality-services/monitor-dqs-activities.md).  
  
-   Asegúrese de que ningún usuario haya iniciado sesión en el servidor DQS.  
  
###  <a name="security"></a><a name="Security"></a> Seguridad  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permisos  
  
-   La cuenta de usuario de Windows debe ser miembro del rol fijo de servidor sysadmin en la instancia de SQL Server para realizar las operaciones de copia de seguridad y restauración.  
  
-   Debe disponer del rol dqs_administrator en la base de datos DQS_MAIN para terminar las actividades o detener los procesos en ejecución en DQS.  
  
##  <a name="backup-and-restore-dqs-databases"></a><a name="BackupRestore"></a>Copia de seguridad y restauración de bases de datos de DQS  
  
1.  Inicie Microsoft SQL Server Management Studio y conéctese a la instancia adecuada de SQL Server.  
  
2.  En el Explorador de objetos, expanda el nodo **Bases de datos** .  
  
3.  Haga una copia de seguridad de la base de datos DQS_STAGING_DATA. Para obtener instrucciones paso a paso sobre cómo realizar una copia de seguridad de una base de datos de SQL Server, vea [Crear una copia de seguridad completa de base de datos &#40;SQL Server&#41;](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).  
  
4.  Haga una copia de seguridad de la base de datos DQS_PROJECTS.  
  
5.  Haga una copia de seguridad de la base de datos DQS_MAIN.  
  
6.  Desconéctese de la instancia actual de SQL Server y conéctese a la instancia de SQL Server donde desea restaurar estas bases de datos.  
  
7.  Restaure la base de datos DQS_MAIN. Para obtener instrucciones paso a paso para restaurar una base de datos de SQL Server, consulte [restaurar una copia de seguridad de base de datos &#40;SQL Server Management Studio&#41;](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md).  
  
8.  Restaure la base de datos DQS_PROJECTS.  
  
9. Restaure la base de datos DQS_STAGING_DATA.  
  
10. En el Explorador de objetos, haga clic con el botón secundario en el servidor y, a continuación, haga clic en **Nueva consulta**.  
  
11. En la ventana Editor de consultas, copie las instrucciones SQL siguientes y reemplace *\<PASSWORD>* por la contraseña que proporcionó durante la instalación de DQS para la clave maestra de base de datos:  
  
    ```sql  
    USE [DQS_MAIN]  
    GO  
    EXECUTE [internal_core].[RestoreDQDatabases] '<PASSWORD>'  
    GO  
    ```  
  
12. Presione F5 para ejecutar las instrucciones. Vea el panel **Resultados** para comprobar que las instrucciones se han ejecutado correctamente.  
  
## <a name="see-also"></a>Consulte también  
 [Manage DQS Databases](../../2014/data-quality-services/manage-dqs-databases.md)  
  
  
