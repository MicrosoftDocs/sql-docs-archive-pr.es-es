---
title: 'SQL Server de la copia de seguridad administrada en Azure: configuración de retención y almacenamiento | Microsoft Docs'
description: En este tema se describe cómo configurar SQL Server copia de seguridad administrada en Microsoft Azure para una base de datos y configurar las opciones predeterminadas de la instancia.
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: c4aa26ea-5465-40cc-8b83-f50603cb9db1
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8ebdb81f8aa9edb9cd9326bcb1d286d5d3fe632c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748244"
---
# <a name="sql-server-managed-backup-to-azure---retention-and-storage-settings"></a>Copia de seguridad administrada de SQL Server en Azure: configuración de la retención y el almacenamiento
  En este tema se describen los pasos básicos para configurar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] para una base de datos y configurar las opciones predeterminadas de la instancia. En el tema también se describen los pasos necesarios para pausar y reanudar los servicios de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] de la instancia.  
  
 Para ver un tutorial completo sobre la configuración [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] , consulte [configuración de SQL Server copia de seguridad administrada en Azure](../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md) y [configuración de SQL Server copia de seguridad administrada en Azure para grupos de disponibilidad](../../2014/database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitaciones y restricciones  
  
-   No habilite [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] en las bases de datos que usen actualmente planes de mantenimiento o el trasvase de registros. Para obtener más información sobre la interoperabilidad y coexistencia con otras características de SQL Server, consulte [SQL Server copia de seguridad administrada en Azure: interoperabilidad y coexistencia](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Requisitos previos  
  
-   El Agente SQL Server debe estar ejecutándose.  
  
    > [!WARNING]  
    >  Si el Agente SQL Server se detiene durante un período de tiempo y después se reinicia, es posible que observe un incremento en la actividad de copia de seguridad en función del tiempo que transcurrió entre la detención y el inicio del Agente SQL Server y puede que haya copias de seguridad de registros pendientes en espera de ejecución. Se recomienda configurar un Agente SQL Server que se inicie de forma automática en el arranque.  
  
-   Antes de configurar, debe crearse una cuenta de almacenamiento de Azure y una credencial SQL que almacene la información de autenticación en la cuenta de almacenamiento [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] . Para obtener más información, consulte la sección [Introduction to Key Components and Concepts](../relational-databases/backup-restore/sql-server-backup-to-url.md#intorkeyconcepts) del tema **Copiar de seguridad de SQL Server a URL** y [Lesson 2: Create a SQL Server Credential](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md).  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] crea los contenedores necesarios para almacenar las copias de seguridad. El nombre del contenedor se crea con el formato ' nombre de equipo-nombre de instancia '. Para los Grupos de disponibilidad AlwayOn, el contenedor se denomina con el GUID del grupo de disponibilidad.  
  
###  <a name="security"></a><a name="Security"></a> Seguridad  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permisos  
 Para ejecutar los procedimientos almacenados que habilitan [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] , debe ser un `System Administrator` miembro o en el rol de base de datos **Db_backupoperator** con permisos **ALTER any Credential** , y `EXECUTE` permisos en el **sp_delete_backuphistory**y `smart_admin.sp_backup_master_switch` procedimientos almacenados.  Los procedimientos almacenados y las funciones que se usan para revisar la configuración existente normalmente requieren permisos `Execute` en el procedimiento almacenado y `Select` en la función, respectivamente.  
  

  
###  <a name="considerations-for-enabling-ss_smartbackup-for-databases-and-instances"></a><a name="Considerations"></a>Consideraciones para habilitar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] para las bases de datos y las instancias  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] se puede habilitar para las bases de datos individuales por separado o para toda la instancia. Las opciones dependen de los requisitos de capacidad de recuperación de las bases de datos de la instancia, los requisitos para administrar varias bases de datos y las instancias, y el uso estratégico del almacenamiento de Azure.  
  
#### <a name="enabling-ss_smartbackup-at-the-database-level"></a>Habilitar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] en el nivel de base de datos  
 Si una base de datos tiene requisitos concretos para el periodo de retención (la capacidad de recuperación SLA) y la copia de seguridad diferentes de otras bases de datos de la instancia, configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] en el nivel de base de datos para esta base de datos. La configuración en el nivel de base de datos invalida la configuración en el nivel de instancia. Sin embargo, ambas opciones se pueden utilizar conjuntamente en la misma instancia. La siguiente es una lista de ventajas y de consideraciones al habilitar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] en el nivel de base de datos.  
  
-   Más específico: opciones de configuración independientes para cada base de datos. Puede admitir periodos de retención diferentes para bases de datos individuales.  
  
-   Invalida los valores de nivel de instancia para la base de datos.  
  
-   Se puede utilizar para reducir los costos de almacenamiento seleccionando las bases de datos individuales cuya copia de seguridad se va a realizar.  
  
-   Requiere administrar cada base de datos  
  
#### <a name="enabling-ss_smartbackup-at-the-instance-level-with-default-settings"></a>Habilitar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] en el nivel de instancia con la configuración predeterminada  
 Utilice esta configuración si la mayoría de las bases de datos de la instancia tiene los mismos requisitos para las directivas de retención y copia de seguridad o si desea realizar la copia de seguridad de las nuevas instancias de base de datos automáticamente tras su creación. Algunas bases de datos que constituyen la excepción de la directiva todavía se pueden configurar individualmente. A continuación se muestra una lista de ventajas y consideraciones a la hora de habilitar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] en el nivel de instancia.  
  
-   Automatización en el nivel de instancia: se aplica automáticamente una configuración común a las nuevas bases de datos agregadas posteriormente.  
  
-   La copia de seguridad de las nuevas bases de datos se realiza automáticamente en cuanto se crean en las instancias  
  
-   Puede aplicarse a las bases de datos que tienen los mismos requisitos del período de retención.  
  
-   Todavía puede configurar bases de datos individuales que requieren otro periodo de retención diferente incluso con la copia de seguridad de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] habilitada en el nivel de instancia con la configuración predeterminada. También puede deshabilitar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] para las bases de datos si no pretende usar Azure Storage para las copias de seguridad.  
  
##  <a name="enable-and-configure-ss_smartbackup-for-a-database"></a><a name="DatabaseConfigure"></a>Habilitar y configurar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] para una base de datos  
 El procedimiento almacenado del sistema `smart_admin.sp_set_db_backup` se utiliza para habilitar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] para una base de datos específica. Cuando [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] se habilita por primera vez en la base de datos, la siguiente información se debe especificar además de habilitar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]:  
  
-   El nombre de la base de datos.  
  
-   El período de retención.  
  
-   Credencial SQL usada para autenticarse en la cuenta de almacenamiento de Azure.  
  
-   Especifique que no se cifre mediante * \@ encryption_algorithm*  =  **NO_ENCRYPTION** o especifique un algoritmo de cifrado admitido. Para obtener más información sobre cifrado, vea [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).  
  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] para la configuración del nivel de base de datos solo se admite con Transact-SQL.  
  
 Una vez que [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] está habilitada para una base de datos, esta información se conserva. Si va a cambiar la configuración, solo se requiere el nombre de la base de datos y el valor que desea cambiar, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] retiene los valores existentes para los otros parámetros cuando no se especifiquen.  
  
> [!IMPORTANT]  
>  Antes de configurar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] en una base de datos puede ser útil para la configuración existente. El paso para revisar la configuración de una base de datos se describe más adelante en esta sección.  
  
-   **Usar Transact-SQL:**  
  
     Si va a habilitar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] por primera vez, los parámetros necesarios son: * \@ database_name*, * \@ credential_name* * \@ encryption_algorithm*, * \@ enable_backup* el parámetro * \@ storage_url* es opcional. Si no proporciona un valor para el @storage_url parámetro, el valor se deriva utilizando la información de la cuenta de almacenamiento de la credencial de SQL. Si proporciona la dirección URL de almacenamiento, debe proporcionar solo la dirección URL de la raíz de la cuenta de almacenamiento y debe coincidir con la información de la credencial SQL que especificó.  
  
    1.  Conéctese con el [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
    2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
    3.  Copie y pegue el ejemplo siguiente en la ventana de consulta y haga clic en `Execute` . Este ejemplo habilita [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] para la base de datos ' TestDB '. El período de retención se establece en 30 días. Este ejemplo utiliza la opción de cifrado especificando el algoritmo de cifrado y la información del sistema de cifrado.  
  
    ```sql
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='TestDB'   
                    ,@enable_backup=1  
                    ,@retention_days =30   
                    ,@credential_name ='MyCredential'  
                    ,@encryption_algorithm ='AES_256'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
    GO
    ```  
  
    > [!IMPORTANT]  
    >  El periodo de retención se puede establecer en cualquier valor entre 1 y 30 días.  
    >   
    >  Para obtener más información sobre cómo crear un certificado para cifrado, vea el paso Crear un certificado de copia de seguridad en [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md).  
  
     Para obtener más información acerca de este procedimiento almacenado, vea [smart_admin. set_db_backup &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/dn451013(v=sql.120).aspx)  
  
     Para revisar la configuración de una base de datos, utilice la siguiente consulta:  
  
    ```sql
    Use msdb  
    GO  
    SELECT * FROM smart_admin.fn_backup_db_config('TestDB')  
    ```  
  
##  <a name="enable-and-configure-default-ss_smartbackup-settings-for-the-instance"></a><a name="InstanceConfigure"></a>Habilitar y configurar los valores predeterminados [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] para la instancia  
 Puede habilitar y configurar los valores predeterminados en [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] el nivel de instancia de dos maneras: mediante el procedimiento almacenado del sistema `smart_admin.set_instance_backup` o **SQL Server Management Studio**. Los dos métodos se explica a continuación:  
  
 **smart_admin. set_instance_backup:**. Al especificar el valor **1** para * \@ enable_backup* parámetro, puede habilitar la copia de seguridad y establecer las configuraciones predeterminadas. Una vez aplicadas en el nivel de instancia, estas configuraciones predeterminadas se aplican a todas las bases de datos nuevas que se agregan a esta instancia.  Cuando [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] se habilita por primera vez, la siguiente información se debe proporcionar además de habilitar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] en la instancia:  
  
-   El período de retención.  
  
-   Credencial SQL usada para autenticarse en la cuenta de almacenamiento de Azure.  
  
-   La opción de cifrado. Especifique que no se cifre mediante * \@ encryption_algorithm*  =  **NO_ENCRYPTION** o especifique un algoritmo de cifrado admitido. Para obtener más información sobre cifrado, vea [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).  
  
 Una vez que están habilitadas estas opciones, se conservan. Si va a cambiar la configuración, solo se requiere el nombre de la base de datos y el valor que desea cambiar. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] conserva los valores existentes cuando no se especifica.  
  
> [!IMPORTANT]  
>  Antes de configurar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] en una instancia, puede ser útil comprobar la configuración existente. El paso para revisar la configuración de una base de datos se describe más adelante en esta sección.  
  
 **SQL Server Management Studio**: para realizar esta tarea en SQL Server Management Studio, vaya el Explorador de objetos, expanda el nodo **Administración** y haga clic con el botón derecho en **Copia de seguridad administrada**. Seleccione **Configurar**. Esto abre el cuadro de diálogo **Copia de seguridad administrada**. Use este cuadro de diálogo para especificar el período de retención, la credencial de SQL, la dirección URL de almacenamiento y la configuración de cifrado. Para obtener ayuda específica sobre este cuadro de diálogo, vea [configurar la &#40;de copia de seguridad administrada SQL Server Management Studio&#41;](configure-managed-backup-sql-server-management-studio.md).  
  
#### <a name="using-transact-sql"></a>Usar Transact-SQL  
  
1.  Conéctese con el [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el ejemplo siguiente en la ventana de consulta y haga clic en `Execute` .  
  
```sql
Use msdb;  
Go  
   EXEC smart_admin.sp_set_instance_backup  
                @retention_days=30   
                ,@credential_name='sqlbackuptoURL'  
                ,@encryption_algorithm ='AES_128'  
                ,@encryptor_type= 'Certificate'  
                ,@encryptor_name='MyBackupCert'  
                ,@enable_backup=1;  
GO  
  
```  
  
> [!IMPORTANT]  
>  El periodo de retención se puede establecer en cualquier valor entre 1 y 30 días.  
>   
>  Para obtener más información sobre cómo crear un certificado para cifrado, vea el paso Crear un certificado de copia de seguridad en [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md).  
  
 Para ver la configuración predeterminada de la instancia, utilice la siguiente consulta:  
  
```sql
Use msdb;  
GO  
SELECT * FROM smart_admin.fn_backup_instance_config ();
```  
  
#### <a name="using-powershell"></a>Usar PowerShell  
  
1.  Iniciar una instancia de PowerShell  
  
2.  Ejecutar el script siguiente después de modificarlo para adecuarlo a sus valores  
  
    ```powershell
    cd SQLSERVER:\SQL\Computer\MyInstance
    $encryptionOption = New-SqlBackupEncryptionOption -EncryptionAlgorithm Aes128 -EncryptorType ServerCertificate -EncryptorName "MyBackupCert"  
    Get-SqlSmartAdmin | Set-SqlSmartAdmin -BackupEnabled $True -BackupRetentionPeriodInDays 10 -EncryptionOption $encryptionOption  
    ```  
  
> [!IMPORTANT]  
>  Cuando crea una nueva base de datos después de configurar la configuración predeterminada, puede llevar hasta 15 minutos el que la base de datos se configure con las opciones predeterminadas. Esto también se aplica a las bases de datos que se cambian de **Simple** a **Full** o al modo de recuperación **Bulk-Logged** .  
  
##  <a name="disable-ss_smartbackup-for-a-database"></a><a name="DatabaseDisable"></a> Deshabilitar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] para una base de datos  
 Puede deshabilitar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] la configuración mediante el `sp_set_db_backup` procedimiento almacenado del sistema. * \@ Enableparameter* se usa para habilitar y deshabilitar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] las configuraciones de una base de datos específica, donde 1 habilita y 0 deshabilita los valores de configuración.  
  
#### <a name="to-disable-ss_smartbackup-for-a-specific-database"></a>Para deshabilitar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] para una base de datos específica:  
  
1.  Conéctese con el [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el ejemplo siguiente en la ventana de consulta y haga clic en `Execute` .  
  
```sql
Use msdb;  
Go  
EXEC smart_admin.sp_set_db_backup   
                @database_name='TestDB'   
                ,@enable_backup=0;  
GO
```  
  
##  <a name="disable-ss_smartbackup-for-all-the-databases-on-the-instance"></a><a name="DatabaseAllDisable"></a> Deshabilitar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] para todas las bases de datos de la instancia  
 El siguiente procedimiento es válido cuando se desea deshabilitar la configuración de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] de todas las bases de datos que tienen habilitado [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] en la instancia.  Las opciones de configuración como la dirección URL de almacenamiento, la retención y la credencial de SQL permanecerán en los metadatos y se pueden utilizar si [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] se habilita posteriormente para la base de datos. Si solo desea pausar los servicios de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] temporalmente, puede usar el modificador principal explicado en las siguientes secciones más adelante en este tema.  
  
#### <a name="to-disable-ss_smartbackupfor-all-the-databases"></a>Para deshabilitar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]para todas las bases de datos:  
  
1.  Conéctese con el [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el ejemplo siguiente en la ventana de consulta y haga clic en `Execute` . El ejemplo siguiente identifica si [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] se configura en el nivel de instancia y todas las bases de datos habilitadas para [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] en la instancia y ejecuta el procedimiento almacenado del sistema `sp_set_db_backup` para deshabilitar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].  
  
```sql
-- Create a working table to store the database names  
Declare @DBNames TABLE  
  
       (  
             RowID int IDENTITY PRIMARY KEY  
             ,DBName varchar(500)  
  
       )  
-- Define the variables  
DECLARE @rowid int  
DECLARE @dbname varchar(500)  
DECLARE @SQL varchar(2000)  
-- Get the database names from the system function  
  
INSERT INTO @DBNames (DBName)  
  
SELECT db_name  
       FROM
  
       smart_admin.fn_backup_db_config (NULL)  
       WHERE is_smart_backup_enabled = 1  
  
       --Select DBName from @DBNames 
       select @rowid = min(RowID) FROM @DBNames  
  
       WHILE @rowID IS NOT NULL  
       Begin
             Set @dbname = (Select DBName From @DBNames Where RowID = @rowid)  
             Begin  
             Set @SQL = 'EXEC smart_admin.sp_set_db_backup    
                @database_name= '''+'' + @dbname+ ''+''',   
                @enable_backup=0'  
  
            EXECUTE (@SQL)  
  
             END  
             Select @rowid = min(RowID)  
             From @DBNames Where RowID > @rowid  
  
       END
```  
  
 Para revisar la configuración predeterminada de todas las bases de datos en la instancia, utilice la siguiente consulta:  
  
```sql
Use msdb;  
GO  
SELECT * FROM smart_admin.fn_backup_db_config (NULL);  
GO
```  
  
##  <a name="disable-default-ss_smartbackup-settings-for-the-instance"></a><a name="InstanceDisable"></a> Deshabilitar la configuración predeterminada de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] de la instancia  
 La configuración predeterminada en el nivel de instancia se aplica a todas las nuevas bases de datos creadas en esa instancia.  Si ya no requiere configuración predeterminada, puede deshabilitarla mediante el procedimiento almacenado del sistema **smart_admin.sp_set_instance_backup** . Al deshabilitarla, no se quita las otras opciones de configuración como la dirección URL de almacenamiento, el valor de retención o el nombre de la credencial de SQL. Estas opciones se utilizarán si [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] se habilita para la instancia posteriormente.  
  
#### <a name="to-disable-ss_smartbackup-default-configuration-settings"></a>Para deshabilitar la configuración predeterminada de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] :  
  
1.  Conéctese con el [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el ejemplo siguiente en la ventana de consulta y haga clic en `Execute` .  
  
    ```sql
    Use msdb;  
    Go  
    EXEC smart_admin.sp_set_instance_backup  
                    @enable_backup=0;  
    GO
    ```  
  
#### <a name="using-powershell"></a>Usar PowerShell  
  
1.  Iniciar una instancia de PowerShell  
  
2.  Ejecute el siguiente script:  
  
    ```powershell
    cd SQLSERVER:\SQL\Computer\MyInstance
    Set-SqlSmartAdmin -BackupEnabled $False  
    ```  
  
##  <a name="pause-ss_smartbackup-at-the-instance-level"></a><a name="InstancePause"></a> Pause [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] en el nivel de instancia  
 Puede haber ocasiones en que deba detener temporalmente los servicios de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] durante un breve período.  El procedimiento almacenado del sistema `smart_admin.sp_backup_master_switch` permite deshabilitar el servicio de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] en el nivel de instancia.  El mismo procedimiento almacenado se utiliza para reanudar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. El parámetro @state se utiliza para definir si [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] debe desactivarse o activarse.  
  
#### <a name="to-pause-ss_smartbackup-services-using-transact-sql"></a>Para pausar los servicios de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] con Transact-SQL:  
  
1.  Conéctese con el [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el ejemplo siguiente en la ventana de consulta y, a continuación, haga clic en`Execute`  
  
```sql
Use msdb;  
GO  
EXEC smart_admin.sp_backup_master_switch @new_state=0;  
Go  
  
```  
  
#### <a name="to-pause-ss_smartbackup-using-powershell"></a>Para pausar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] usando PowerShell  
  
1.  Iniciar una instancia de PowerShell  
  
2.  Ejecutar el script siguiente después de modificarlo para adecuarlo a sus valores  
  
    ```powershell
    cd SQLSERVER:\SQL\Computer\MyInstance
    Get-SqlSmartAdmin | Set-SqlSmartAdmin -MasterSwitch $False  
    ```  
  
#### <a name="to-resume-ss_smartbackup-using-transact-sql"></a>Para reanudar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] con Transact-SQL  
  
1.  Conéctese con el [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el ejemplo siguiente en la ventana de consulta y, a continuación, haga clic en `Execute` .  
  
```sql
Use msdb;  
Go  
EXEC smart_admin. sp_backup_master_switch @new_state=1;  
GO
```  
  
#### <a name="to-resume-ss_smartbackup-using-powershell"></a>Para reanudar [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] usando PowerShell  
  
1.  Iniciar una instancia de PowerShell  
  
2.  Ejecutar el script siguiente después de modificarlo para adecuarlo a sus valores  
  
    ```powershell
    cd SQLSERVER:\SQL\Computer\MyInstance
    Get-SqlSmartAdmin | Set-SqlSmartAdmin -MasterSwitch $True  
    ```  
