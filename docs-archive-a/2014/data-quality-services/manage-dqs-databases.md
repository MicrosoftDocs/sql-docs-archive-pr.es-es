---
title: Administrar bases de datos de DQS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 655a67aa-d662-42f2-b982-c6217125ada8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7228021dd3fe0af61312eeb891081cc24e1aa95d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676682"
---
# <a name="manage-dqs-databases"></a>Manage DQS Databases
  En esta sección se proporciona información sobre las actividades de administración de bases de datos que se pueden realizar en las bases de datos de DQS, como la copia de seguridad/restauración o las operaciones de separar/adjuntar.  
  
##  <a name="backup-and-restore-the-dqs-databases"></a><a name="BackupRestore"></a> Copia de seguridad y restauración de las bases de datos de DQS  
 La copia de seguridad y la restauración de bases de datos de SQL Server son operaciones habituales que los administradores de bases de datos llevan a cabo para evitar la pérdida de datos en caso de desastre y que les permiten recuperar la información de las copias de seguridad de las bases de datos. Básicamente, hay dos bases de datos de SQL Server que implementan[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] : DQS_MAIN y DQS_PROJECTS. Los procedimientos de copia de seguridad y restauración de las bases de datos de [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) son similares a los del resto de bases de datos de SQL Server. Las operaciones de copia de seguridad y restauración de las bases de datos de DQS plantean estos tres retos:  
  
-   Dichas operaciones deben estar sincronizadas. En caso contrario, el [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] restaurado ya no será funcional.  
  
-   Las dos bases de datos de DQS, DQS_MAIN y DQS_PROJECTS, contienen ensamblados y otros objetos complejos, además de objetos de base de datos simples (como tablas y procedimientos almacenados).  
  
-   Existen entidades fuera de las bases de datos de DQS cuya existencia es necesaria para que estas sean funcionales como [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], especialmente los dos inicios de sesión de SQL Server (##MS_dqs_db_owner_login## y ##MS_dqs_service_login##) y un procedimiento almacenado de inicialización (DQInitDQS_MAIN) en la base de datos maestra.  
  
 Para obtener información detallada acerca de las copias de seguridad y restauración en SQL Server, vea [Realizar copias de seguridad y restaurar bases de datos de SQL Server](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).  
  
### <a name="default-autogrowth-size-and-recovery-model-for-the-dqs-databases"></a>Tamaño de crecimiento automático y modelo de recuperación predeterminados para las bases de datos de DQS  
 Para evitar que las bases de datos y los registros de transacciones de DQS aumenten de forma desmesurada y acaben llenando el disco duro:  
  
-   El tamaño predeterminado de **Crecimiento automático** de las bases de datos de DQS está establecido en un 10%.  
  
-   El modelo de recuperación predeterminado de las bases de datos de DQS está establecido en **Simple**. En el modelo de recuperación simple, se realiza un registro mínimo de las transacciones, y el truncamiento del registro se produce automáticamente después de que la transacción finaliza para liberar espacio en el registro de transacciones (archivo .ldf). Para obtener información detallada sobre el modelo de recuperación simple, vea [Copias de seguridad completas de bases de datos &#40;SQL Server&#41;](../relational-databases/backup-restore/full-database-backups-sql-server.md).  
  
> [!IMPORTANT]
>  -   En el modelo de recuperación simple, cuando las entradas de registro permanecen activas durante mucho tiempo (por ejemplo, una transacción prolongada), el truncamiento del registro se puede retrasar y, por tanto, se podría llenar el registro de transacciones. Además, el truncamiento del registro no reduce el tamaño del archivo de registro físico (archivo. ldf). Para reducir el tamaño de un archivo de registro físico, se debe reducir el archivo de registro. Para obtener información sobre la solución de problemas relativos al registro de transacciones, vea [El registro de transacciones &#40;SQL Server&#41;](../relational-databases/logs/the-transaction-log-sql-server.md) o el artículo del servicio de soporte técnico de Microsoft en [https://go.microsoft.com/fwlink/?LinkId=237446](https://go.microsoft.com/fwlink/?LinkId=237446).  
> -   Debe realizar periódicamente una copia de seguridad completa o diferencial de las bases de datos de DQS, y una copia de seguridad del registro de transacciones para crear un punto de recuperación de los datos. Para más información, vea [Copias de seguridad completas de bases de datos &#40;SQL Server&#41;](../relational-databases/backup-restore/full-database-backups-sql-server.md) y [Realizar copias de seguridad de un registro de transacciones &#40;SQL Server&#41;](../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md).  
  
##  <a name="detachattach-the-dqs-databases"></a><a name="DetachAttach"></a>Desasociar o adjuntar las bases de datos de DQS  
 Puede separar los datos y los archivos de registro de transacciones de las bases de datos de DQS y, a continuación, volver a adjuntar las bases de datos a la misma instancia o a otra instancia de SQL Server si desea cambiar las bases de datos de DQS a una instancia diferente de SQL Server en el mismo equipo o mover la base de datos.  
  
 Para obtener información detallada sobre los aspectos que se deben considerar tanto antes de las operaciones para separar y adjuntar bases de datos en SQL Server como durante dichas operaciones, vea [Adjuntar y separar bases de datos &#40;SQL Server&#41;](../relational-databases/databases/database-detach-and-attach-sql-server.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Descripción de la tarea|Tema|  
|----------------------|-----------|  
|Describe cómo realizar copias de seguridad de las bases de datos de DQS y cómo restaurarlas.|[Realizar copias de seguridad de bases de datos de DQS y restaurarlas](../../2014/data-quality-services/backing-up-and-restoring-dqs-databases.md)|  
|Describe cómo adjuntar y separar las bases de datos de DQS.|[Separar y adjuntar bases de datos de DQS](../../2014/data-quality-services/detaching-and-attaching-dqs-databases.md)|  
  
## <a name="see-also"></a>Consulte también  
 [dqs, administración](../../2014/data-quality-services/dqs-administration.md)  
  
  
