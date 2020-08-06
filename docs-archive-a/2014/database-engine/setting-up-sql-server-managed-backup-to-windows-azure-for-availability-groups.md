---
title: Configuración de SQL Server copia de seguridad administrada en Azure para grupos de disponibilidad | Microsoft Docs
description: En este tutorial se muestra cómo configurar SQL Server copia de seguridad administrada en Microsoft Azure para las bases de datos que participan en Always On grupos de disponibilidad.
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 0c4553cd-d8e4-4691-963a-4e414cc0f1ba
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ebae9f75ac25698582b7f3e4c78c2fb773bd803e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662232"
---
# <a name="setting-up-sql-server-managed-backup-to-azure-for-availability-groups"></a>Configuración de copia de seguridad administrada de SQL Server para Azure para grupos de disponibilidad
  Este tema es un tutorial sobre la configuración de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] para las bases de datos participantes en Grupos de disponibilidad AlwaysOn.  
  
## <a name="availability-group-configurations"></a>Configuraciones de grupo de disponibilidad  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]se admite para las bases de datos del grupo de disponibilidad, tanto si todas las réplicas están configuradas de forma local o completamente en Azure, como si se trata de una implementación híbrida entre el entorno local y una o varias máquinas virtuales de Azure. No obstante, puede ser necesario tener en cuenta lo siguiente para una o varias implementaciones:  
  
-   Frecuencia de copia de seguridad de registros: la frecuencia de la copia de seguridad de registros es tanto el tiempo como el crecimiento de los registros. Por ejemplo, la copia de seguridad de registros se realiza una vez cada 2 horas a menos que el espacio de registro usado en ese período de dos horas sea 5 MB o más. Esto se aplica a todas las implementaciones, ya sean locales, en la nube o híbridas.  
  
-   Ancho de banda de red: se aplica a las implementaciones en las que las réplicas se encuentran en diferentes ubicaciones físicas, como en una nube híbrida, o en distintas regiones de Azure en una configuración solo en la nube. El ancho de banda de red puede afectar a la latencia de las secundarias y, si las secundarias están establecidas en replicación sincrónica, esto puede provocar el crecimiento de los registros en la principal. Si las secundarias están establecidas en replicación sincrónica, las secundarias quizás no puedan seguir el ritmo debido a la latencia de red, que puede provocar la pérdida de datos en caso de conmutación por error a la réplica secundaria.  
  
### <a name="configuring-ss_smartbackup-for-availability-databases"></a>Configurar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] para las bases de datos de disponibilidad.  
 **Permisos:**  
  
-   Requiere la pertenencia al rol de base de datos **db_backupoperator** , con permisos **ALTER any Credential** y `EXECUTE` permisos en **sp_delete_backuphistory**procedimiento almacenado.  
  
-   Requiere permisos **Select** en la función **smart_admin. fn_get_current_xevent_settings**.  
  
-   Requiere `EXECUTE` permisos en el procedimiento almacenado **smart_admin. sp_get_backup_diagnostics** . Además, requiere permisos `VIEW SERVER STATE` ya que internamente llama a otros objetos del sistema que requieren este permiso.  
  
-   Requiere `EXECUTE` permisos en los `smart_admin.sp_set_instance_backup` `smart_admin.sp_backup_master_switch` procedimientos almacenados y.  
  
 Los siguientes son los pasos básicos para configurar un Grupo de disponibilidad AlwaysOn con [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Más adelante en este tema se describe un tutorial detallado paso a paso.  
  
1.  Una vez que haya creado el Grupo de disponibilidad, configure la réplica de copia de seguridad que prefiera. Este valor para el Grupo de disponibilidad también es usado por [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] para determinar qué réplica usar para la copia de seguridad. Para obtener instrucciones paso a paso sobre cómo configurar las preferencias de copia de seguridad, vea [configurar la copia de seguridad en réplicas de disponibilidad &#40;SQL Server&#41;](availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md).  Si va a crear un nuevo grupo de disponibilidad AlwaysOn, consulte [Introducción con Grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](availability-groups/windows/getting-started-with-always-on-availability-groups-sql-server.md).  
  
2.  Configure el acceso de conexión de solo lectura en las réplicas secundarias. Para obtener instrucciones paso a paso sobre cómo configurar el acceso de solo lectura, vea [configurar el acceso de solo lectura en una réplica de disponibilidad &#40;SQL Server&#41;](availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
3.  Especifique la réplica de copia de seguridad. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] usa la configuración de la réplica de copia de seguridad preferida para determinar qué base de datos usar para programar las copias de seguridad.  Para determinar si la réplica actual es la réplica de copia de seguridad preferida, use la función de [&#41;de Transact-SQL &#40;sys. fn_hadr_backup_is_preferred_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) .  
  
4.  En cada [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] configuración de ejecución de réplicas para la base de datos, use el procedimiento almacenado **Smart-admin. sp_set_db_backup** .  
  
     ** [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] comportamiento después de una conmutación por error:** seguirá [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] funcionando y manteniendo las copias de seguridad y la capacidad de recuperación después de un evento de conmutación por error. No se requiere ninguna acción concreta después de una conmutación por error.  
  
#### <a name="considerations-and-requirements"></a>Consideraciones y requisitos:  
 La configuración de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] para las bases de datos participantes en el Grupo de disponibilidad AlwaysOn requiere consideraciones y requisitos concretos. La siguiente es una lista de las consideraciones y los requisitos:  
  
-   La configuración de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] debe ser la misma para todas las bases de datos en todos los nodos de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] que participan en el mismo Grupo de disponibilidad. Puede lograr esto estableciendo la misma configuración de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] para las réplicas principales y para todas las réplicas en la base de datos, o estableciendo los mismos valores predeterminados de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] en todos los nodos participantes en los Grupos de disponibilidad. Se recomienda establecer [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] en la base de datos porque la configuración de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] en el nivel de base de datos permite aislar los valores para las bases de datos y los cambios en la configuración predeterminada afectan a todas las demás bases de datos en la instancia.  
  
-   Especifique la réplica de copia de seguridad. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] usa la configuración de la réplica de copia de seguridad preferida para programar las copias de seguridad. Para determinar si la réplica actual es la réplica de copia de seguridad preferida, use la función de [&#41;de Transact-SQL &#40;sys. fn_hadr_backup_is_preferred_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) .  
  
-   Si la réplica secundaria está configurada como la preferida, debe configurarse para que tenga al menos acceso de conexión de solo lectura. Los grupos de disponibilidad que no tienen acceso de conexión a las bases de datos secundarias no se admiten.  Para obtener más información, vea [Configurar el acceso de solo lectura en una réplica de disponibilidad &#40;SQL Server&#41;](availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md).  
  
-   Si configura [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] después de configurar el Grupo de disponibilidad, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] intentará copiar las copias de seguridad existentes y las copiará en el contenedor de almacenamiento.  Si [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] no encuentra o no tiene acceso a las copias de seguridad existentes, programará una copia de seguridad completa de la base de datos. Esto se hace específicamente para optimizar las operaciones de copia de seguridad para las bases de datos del Grupo de disponibilidad.  
  
-   Es posible que desee considerar la posibilidad de deshabilitar la configuración de nivel de instancia si está creando una nueva base de datos de disponibilidad y no pretende aplicar la configuración de nivel de instancia a la base de datos.  
  
-   Cuando se usa cifrado, emplee el mismo certificado en todas las réplicas. Esto facilita operaciones de copia de seguridad continuadas e ininterrumpidas en caso de conmutación por error o restauraciones en otra réplica diferente.  
  
#### <a name="enable-and-configure-ss_smartbackup-for-an-availability-database"></a>Habilitar y configurar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] para una base de datos de disponibilidad  
 En este tutorial se describen los pasos para habilitar y configurar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] para una base de datos (AGTestDB) en los equipos Node1 y Node2, además de los pasos para habilitar la supervisión del estado de mantenimiento de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].  
  
1.  **Cree una cuenta de almacenamiento de Azure:** Las copias de seguridad se almacenan en el servicio de almacenamiento de blobs de Azure. En primer lugar, debe crear una cuenta de almacenamiento de Azure, si aún no tiene una. Para obtener más información, consulte [crear una cuenta de Azure Storage](https://www.windowsazure.com/manage/services/storage/how-to-create-a-storage-account/). Anote el nombre, las claves de acceso y la dirección URL de la cuenta de almacenamiento. La información del nombre de cuenta y de la clave de acceso se utiliza para crear una credencial SQL. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] usa la credencial de SQL durante las operaciones de copia de seguridad para autenticarse en la cuenta de almacenamiento.  
  
2.  **Cree una credencial de SQL:** Cree una credencial de SQL con el nombre de la cuenta de almacenamiento como identidad y la clave de acceso de almacenamiento como contraseña.  
  
3.  **Asegúrese de que el servicio del Agente SQL Server está iniciado y en ejecutándose:** inicie el Agente SQL Server si no se está ejecutando actualmente. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] requiere que el Agente SQL Server se ejecute en la instancia para realizar operaciones de copia de seguridad.  Puede ser conveniente configurar el Agente SQL Server para que se ejecute automáticamente con el fin de asegurarse de que las operaciones de copia de seguridad pueden realizarse periódicamente.  
  
4.  **Determinar el período de retención:** Determine el período de retención que desea para los archivos de copia de seguridad. El período de retención se especifica en días y puede abarcar de 1 a 30. Este período de retención determina el margen de tiempo durante el cual se puede recuperar la base de datos.  
  
5.  **Cree un certificado o una clave asimétrica que se usará para el cifrado durante la copia de seguridad:** Cree el certificado en el primer nodo Nodo1 y, a continuación, expórtelo a un archivo mediante el [certificado de copia de seguridad &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql). En el Nodo 2, cree un certificado mediante el archivo exportado del Nodo 1. Para obtener más información sobre cómo crear un certificado a partir de un archivo, vea el ejemplo de [Create certificate &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql).  
  
6.  **Habilite y configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] para AGTestDB en nodo1:** inicie SQL Server Management Studio y conéctese a la instancia en el nodo1 donde está instalada la base de datos de disponibilidad. En la ventana de consulta, ejecute la siguiente instrucción después de modificar los valores correspondientes al nombre de la base de datos, la dirección URL de almacenamiento, la credencial SQL y el período de retención según sus requisitos:  
  
    ```sql  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='AGTestDB'   
                    ,@retention_days=30   
                    ,@credential_name='MyCredential'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
                    ,@enable_backup=1;  
    GO  
    ```  
  
     Para obtener más información sobre la creación de un certificado para el cifrado, vea el paso **crear un certificado de copia** de seguridad en [creación de una copia de seguridad cifrada](../relational-databases/backup-restore/create-an-encrypted-backup.md).  
  
7.  **Habilite y configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] para AGTestDB en nodo2:** inicie SQL Server Management Studio y conéctese a la instancia en el nodo 2, donde está instalada la base de datos de disponibilidad. En la ventana de consulta, ejecute la siguiente instrucción después de modificar los valores correspondientes al nombre de la base de datos, la dirección URL de almacenamiento, la credencial SQL y el período de retención según sus requisitos:  
  
    ```sql  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='AGTestDB'   
                    ,@retention_days=30   
                    ,@credential_name='MyCredential'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
                    ,@enable_backup=1;  
    GO  
    ```  
  
     [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] está habilitada ahora en la base de datos especificada. Puede tardarse hasta 15 minutos en que las operaciones de copia de seguridad de la base de datos empiecen a ejecutarse. La copia de seguridad tendrá lugar en la réplica de la copia de seguridad preferida.  
  
8.  **Revise la configuración predeterminada del evento extendido:**  Revise la configuración de eventos extendidos ejecutando la siguiente instrucción Transact-SQL en la réplica que [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] usa para programar las copias de seguridad. Esta suele ser la configuración de la réplica de copia de seguridad preferida para el Grupo de disponibilidad al que pertenece la base de datos.  
  
    ```sql  
    SELECT * FROM smart_admin.fn_get_current_xevent_settings(); 
    ```  
  
     Debe ver que los eventos de canal Administración, Operativo y Analítico están habilitados de forma predeterminada y no se pueden deshabilitar. Debe ser suficiente supervisar los eventos que requieren intervención manual.  Puede habilitar los eventos de depuración, pero estos canales incluyen eventos informativos y de depuración que [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] usa para detectar problemas y solucionarlos. Para obtener más información, consulte [supervisión SQL Server copia de seguridad administrada en Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).  
  
9. **Habilite y configure la notificación del estado de mantenimiento:** [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] tiene un procedimiento almacenado que crea un trabajo del agente para enviar notificaciones por correo electrónico de los errores o las advertencias que puedan requerir atención.  Para recibir dichas notificaciones, debe habilitar el procedimiento almacenado que crea un trabajo del Agente SQL Server. En los pasos siguientes se describe el proceso para habilitar y configurar las notificaciones por correo electrónico:  
  
    1.  Configure Correo electrónico de base de datos si aún no está habilitado en la instancia. Para obtener más información, vea [Configure Database Mail](../relational-databases/database-mail/configure-database-mail.md).  
  
    2.  Configure la notificación del Agente SQL Server para que use Correo electrónico de base de datos. Para más información, consulte [Configurar el Agente SQL Server para que use el Correo electrónico de base de datos](../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).  
  
    3.  **Habilite las notificaciones por correo electrónico para recibir advertencias y errores de copia de seguridad:** En la ventana de consulta, ejecute las siguientes instrucciones Transact-SQL:  
  
        ```sql  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email>'  
        ```  
  
         Para obtener más información y un script de ejemplo completo, vea [Monitor SQL Server copia de seguridad administrada en Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).  
  
10. **Ver los archivos de copia de seguridad en la cuenta de Azure Storage:** Conéctese a la cuenta de almacenamiento desde SQL Server Management Studio o el Portal de administración de Azure. Verá un contenedor para la instancia de SQL Server que hospeda la base de datos que configuró para utilizar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. También puede ver una base de datos y una copia de seguridad de registros antes de 15 minutos después de habilitar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] para la base de datos.  
  
11. **Supervise el estado de mantenimiento:**  puede supervisar a través de notificaciones por correo electrónico que ha configurado previamente, o bien supervisar los eventos registrados de forma activa. Las siguientes son algunas instrucciones de Transact-SQL de ejemplo que se utilizan para ver los eventos:  
  
    ```sql  
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event varchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
    ```  
  
    ```sql  
    -- to enable debug events  
    Use msdb;  
    Go  
    EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
    ```  
  
    ```sql  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
    ```  
  
 Los pasos descritos en esta sección son específicos para configurar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] por primera vez en la base de datos. Puede modificar las configuraciones existentes mediante el mismo procedimiento almacenado del sistema **smart_admin. sp_set_db_backup** y proporcionar los nuevos valores. Para obtener más información, consulte [SQL Server la copia de seguridad administrada en Azure: configuración de retención y almacenamiento](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md).  
  
### <a name="considerations-when-removing-a-database-from-alwayson-availability-group-configuration"></a>Consideraciones al quitar una base de datos de la configuración del Grupo de disponibilidad AlwaysOn  
 Si se quita una base de datos de la configuración del grupo de disponibilidad AlwaysOn y ahora es una base de datos independiente, se recomienda realizar la copia de seguridad mediante [smart_admin. sp_backup_on_demand &#40;&#41;de Transact-SQL ](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-on-demand-transact-sql). Al crear una copia de seguridad de la base de datos de esta manera, establece una nueva cadena de copias de seguridad y el archivo se colocará en el contenedor específico de la instancia en lugar de en el contenedor Disponibilidad donde se almacenaban las copias de seguridad cuando la base de datos formaba parte del Grupo de disponibilidad.  
  
> [!WARNING]  
>  No se garantiza la posibilidad de recuperación de la base de datos en este escenario a partir de las copias de seguridad anteriores al cambio en el estado del Grupo de disponibilidad.  
  
