---
title: Agente de instantáneas de replicación | Microsoft Docs
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Snapshot Agent, executables
- agents [SQL Server replication], Snapshot Agent
- command prompt [SQL Server replication]
- Snapshot Agent, parameter reference
ms.assetid: 2028ba45-4436-47ed-bf79-7c957766ea04
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a26aca7b33a7355500350572ea5e8ed21bddeacb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663416"
---
# <a name="replication-snapshot-agent"></a>Agente de instantáneas de replicación
  El Agente de instantáneas de replicación es un archivo ejecutable que prepara archivos de instantáneas que contienen el esquema y los datos de las tablas y objetos de base de datos publicados, almacena los archivos en la carpeta de instantáneas y registra los trabajos de sincronización en la base de datos de distribución.  
  
> [!NOTE]  
>  Los parámetros se pueden especificar en cualquier orden.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      snapshot [ -?]   
-Publisherserver_name[\instance_name]   
-Publication publication_name   
[-70Subscribers]   
[-BcpBatchSizebcp_batch_size]  
[-DefinitionFiledef_path_and_file_name]  
[-Distributorserver_name[\instance_name]]  
[-DistributorDeadlockPriority [-1|0|1] ]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1] ]  
[-DynamicFilterHostNamedynamic_filter_host_name]  
[-DynamicFilterLogindynamic_filter_login]  
[-DynamicSnapshotLocationdynamic_snapshot_location]   
[-EncryptionLevel [0|1|2]]  
[-FieldDelimiterfield_delimiter]  
[-HistoryVerboseLevel [0|1|2|3] ]  
[-HRBcpBlocksnumber_of_blocks ]  
[-HRBcpBlockSizeblock_size ]  
[-HRBcpDynamicBlocks ]  
[-KeepAliveMessageIntervalkeep_alive_interval]  
[-LoginTimeOutlogin_time_out_seconds]  
[-MaxBcpThreadsnumber_of_threads ]  
[-MaxNetworkOptimization [0|1]]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2] ]  
[-PacketSizepacket_size]
[-PrefetchTables [0|1] ]  
[-ProfileNameprofile_name]  
[-PublisherDBpublisher_database]  
[-PublisherDeadlockPriority [-1|0|1] ]  
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-PublisherLoginpublisher_login]  
[-PublisherPasswordpublisher_password]   
[-PublisherSecurityMode [0|1] ]  
[-QueryTimeOutquery_time_out_seconds]  
[-ReplicationType [1|2] ]  
[-RowDelimiterrow_delimiter]  
[-StartQueueTimeoutstart_queue_timeout_seconds]  
[-UsePerArticleContentsViewuse_per_article_contents_view]  
```  
  
## <a name="arguments"></a>Argumentos  
 **-?**  
 Imprime todos los parámetros disponibles.  
  
 **-Publisher** _server_name_[ **\\** _instance_name_]  
 Es el nombre del publicador. Especifique server_name para la instancia predeterminada de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en ese servidor. Especifique _server_name_ **\\** _instance_name_ para una instancia con nombre de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en ese servidor.  
  
 **-Publication** _publication_  
 Es el nombre de la publicación. Este parámetro solamente es válido si la publicación se define para tener siempre una instantánea disponible para las suscripciones nuevas o reinicializadas.  
  
 **-70Subscribers**  
 Se debe usar si algún suscriptor ejecuta la versión 7.0 de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 **-BcpBatchSize** _bcp_\_ *batch*\_ *size*  
 Es el número de filas para enviar en una operación de copia masiva. Al realizar una operación **bcp in** , el tamaño del lote es el número de filas para enviar al servidor como una transacción y también el número de filas que se deben enviar antes de que el Agente de distribución registre un mensaje de progreso de **bcp** . Al realizar una operación **bcp out** , se usa un tamaño de lote fijo de 1000. Un valor 0 indica que no se registran mensajes.  
  
 **-DefinitionFile** _def_path_and_file_name_  
 Es la ruta de acceso del archivo de definición de agente. Un archivo de definición de agente contiene los argumentos de línea de comandos para el agente. El contenido del archivo se analiza como un archivo ejecutable. Utilice las comillas tipográficas (") para especificar valores de argumento que contienen caracteres arbitrarios.  
  
 **-Distributor** _server_name_[ **\\** _instance_name_]  
 Es el nombre del distribuidor. Especifique *server_name* para conectarse a la instancia predeterminada del [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en ese servidor. Especifique _server_name_ **\\** _instance_name_ para una instancia con nombre de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en ese servidor.  
  
 **-DistributorDeadlockPriority** [ **-1**|**0**|**1**]  
 Es la prioridad de la conexión del Agente de instantáneas al distribuidor cuando se produce un interbloqueo. Este parámetro se especifica para resolver interbloqueos que se pueden producir entre las aplicaciones de usuario y el Agente de instantáneas durante la generación de instantáneas.  
  
|Valor DistributorDeadlockPriority|Descripción|  
|---------------------------------------|-----------------|  
|**-1**|Cuando se produce un interbloqueo en el distribuidor, tienen prioridad las aplicaciones distintas del Agente de instantáneas.|  
|**0** (predeterminado)|No se asigna prioridad.|  
|**1**|El Agente de instantáneas tiene la prioridad cuando se produce un interbloqueo en el distribuidor.|  
  
 **-DistributorLogin** _distributor_login_  
 Es el inicio de sesión que se usa al conectar con el distribuidor mediante autenticación de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 **-DistributorPassword** _distributor_password_  
 Es la contraseña que se usa al conectar con el distribuidor mediante autenticación de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . .  
  
 **-DistributorSecurityMode** [ **0**| **1**]  
 Especifica el modo de seguridad del distribuidor. Un valor de **0** hace referencia a la autenticación de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (valor predeterminado) y un valor de **1** hace referencia al modo de autenticación de Windows.  
  
 **-DynamicFilterHostName** _dynamic_filter_host_name_  
 Se usa para establecer un valor para [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql) al filtrar cuando se crea una instantánea dinámica. Por ejemplo, si especifica la cláusula de filtro de subconjunto `rep_id = HOST_NAME()` para un artículo y establece la propiedad **DynamicFilterHostName** en "FBJones" antes de llamar al Agente de mezcla, solo se replicarán las filas que tienen "FBJones" en la columna **rep_id** .  
  
 **-DynamicFilterLogin** _dynamic_filter_login_  
 Se usa para establecer un valor para [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql) al filtrar cuando se crea una instantánea dinámica. Por ejemplo, si especifica la cláusula de filtro de subconjunto `user_id = SUSER_SNAME()` en un artículo y establece la propiedad **DynamicFilterLogin** en "rsmith" antes de llamar al método **Run** del objeto **SQLSnapshot** , solo se incluirán en la instantánea las filas que tienen "rsmith" en la columna **user_id** .  
  
 **-DynamicSnapshotLocation** _dynamic_snapshot_location_  
 Es la ubicación donde se generará la instantánea dinámica.  
  
 **-EncryptionLevel** [ **0** | **1** | **2** ]  
 Es el nivel de cifrado de Capa de sockets seguros (SSL) que usa el Agente de instantáneas cuando realiza conexiones.  
  
|Valor de EncryptionLevel|Descripción|  
|---------------------------|-----------------|  
|**0**|Especifica que no se utiliza SSL.|  
|**1**|Especifica que se utiliza SSL, pero el agente no comprueba que un emisor confiable haya firmado el certificado del servidor SSL.|  
|**2**|Especifica que se usa SSL y que se ha comprobado el certificado.|  

 > [!NOTE]  
 >  Un certificado SSL válido se define con un nombre de dominio completo de SQL Server. Para que el agente se conecte correctamente al establecer -EncryptionLevel en 2, cree un alias en la instancia local de SQL Server. El parámetro "Alias Name" debe ser el nombre del servidor, mientras que el parámetro "Server" se debe establecer en el nombre completo de la instancia de SQL Server.
  
 Para obtener más información, consulte [replicación de SQL Server Security](../security/view-and-modify-replication-security-settings.md).  
  
 **-FieldDelimiter** _field_delimiter_  
 Es el carácter o secuencia de caracteres que marca el fin de un campo en el archivo de datos de copia masiva de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . El valor predeterminado es \n\<x$3>\n.  
  
 **-HistoryVerboseLevel** [ **1**| **2**| **3**]  
 Especifica la cantidad de historial registrado durante una operación de instantánea. Puede minimizar el efecto sobre el rendimiento del registro del historial seleccionando **1**.  
  
|Valor HistoryVerboseLevel|Descripción|  
|-------------------------------|-----------------|  
|**0**|Los mensajes de progreso se escriben en la consola o bien en un archivo de resultados. Los registros del historial no se registran en la base de datos de distribución.|  
|**1**|Siempre actualiza un mensaje del historial anterior del mismo estado (inicio, progreso, éxito, etc.). Si no existe ningún registro anterior con el mismo estado, inserta un nuevo registro.|  
|**2** (predeterminado)|Inserta nuevos registros de historial a menos que el registro sea para mensajes de inactividad o mensajes de trabajos de ejecución prolongada, en cuyo caso actualiza los registros anteriores.|  
|**3**|Siempre inserta nuevos registros, a menos que sea para mensajes inactivos.|  
  
 **-HRBcpBlocks** _number_of_blocks_  
 Es el número de bloques de datos de **bcp** que se ponen en la cola entre los subprocesos de escritor y lector. El valor predeterminado es 50. **HRBcpBlocks** solamente se usa con publicaciones de Oracle.  
  
> [!NOTE]  
>  Este parámetro se usa para el ajuste del rendimiento de **bcp** en un publicador de Oracle.  
  
 -**HRBcpBlockSize**_BLOCK_SIZE_ HRBcpBlockSize  
 Es el tamaño, en kilobytes (KB), de cada bloque de datos de **bcp** . El valor predeterminado es 64 KB. **HRBcpBlocks** solamente se usa con publicaciones de Oracle.  
  
> [!NOTE]  
>  Este parámetro se usa para el ajuste del rendimiento de **bcp** en un publicador de Oracle.  
  
 **-HRBcpDynamicBlocks**  
 Indica si el tamaño de cada bloque de datos de **bcp** puede crecer dinámicamente o no. **HRBcpBlocks** solamente se usa con publicaciones de Oracle.  
  
> [!NOTE]  
>  Este parámetro se usa para el ajuste del rendimiento de **bcp** en un publicador de Oracle.  
  
 **-KeepAliveMessageInterval** _keep_alive_interval_  
 Es la cantidad de tiempo, en segundos, que el Agente de instantáneas espera antes de registrar una espera por el mensaje de back-end en la tabla [MSsnapshot_history](/sql/relational-databases/system-tables/mssnapshot-history-transact-sql) . El valor predeterminado es 300 segundos.  
  
 **-LoginTimeOut** _login_time_out_seconds_  
 Es el número de segundos antes de que el inicio de sesión exceda el tiempo de espera. El valor predeterminado es de **15** segundos.  
  
 **-MaxBcpThreads** _number_of_threads_  
 Especifica el número de operaciones de copia masiva que se pueden realizar en paralelo. El número máximo de subprocesos y conexiones ODBC que existen simultáneamente es el menor entre **MaxBcpThreads** y el número de solicitudes de copia masiva que aparecen en la transacción de sincronización en la base de datos de distribución. **MaxBcpThreads** debe tener un valor mayor que **0** y no tiene ningún límite superior codificado de forma rígida. El valor predeterminado es **1**.  
  
 \- **MaxNetworkOptimization** [ **0**| **1**]  
 Si es irrelevante, las eliminaciones se envían al suscriptor. Las eliminaciones irrelevantes son comandos DELETE que se envían a los suscriptores para filas que no pertenecen a la partición del suscriptor. Las eliminaciones irrelevantes no afectan a integridad o convergencia de los datos, pero pueden producir un tráfico de red innecesario. El valor predeterminado de **MaxNetworkOptimization** es **0**. Al establecer **MaxNetworkOptimization** en **1** , se reducen las oportunidades eliminaciones irrelevantes, lo que a su vez reduce el tráfico de red y mejora la optimización de la red. Si se establece este parámetro en **1** , también puede aumentar el almacenamiento de metadatos y afectar negativamente al rendimiento en el publicador si existen varios niveles de filtros de combinación y filtros de subconjunto complejos. Debe evaluar cuidadosamente su topología de replicación y establecer **MaxNetworkOptimization** en **1** solo si el tráfico de red debido a eliminaciones irrelevantes es inaceptablemente alto.  
  
> [!NOTE]
>  Establecer este parámetro en **1** solo es útil cuando la opción de optimización de sincronización de la publicación de combinación está establecida en **true** (el **@keep_partition_changes** parámetro de [SP_ADDMERGEPUBLICATION &#40;&#41;de Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)).  
  
 **-Output** _output_path_and_file_name_  
 Es la ruta de acceso del archivo de salida del agente. Si no se proporciona un nombre de archivo, el resultado se envía a la consola. Si el nombre de archivo especificado existe, el resultado se anexa al archivo.  
  
 **-OutputVerboseLevel** [ **0**| **1**| **2**]  
 Especifica si el resultado debería ser detallado.  
  
|Valor OutputVerboseLevel|Descripción|  
|------------------------------|-----------------|  
|**0**|Solo se imprimen los mensajes de error.|  
|**1** (predeterminado)|Se imprimen todos los mensajes de informe de progreso (predeterminado).|  
|**2**|Se imprimen todos los mensajes de error y mensajes del informe de progreso, la información útil para depurar.|  

 **-PrefetchTables** [ **0**| **1**]  
 Parámetro opcional que especifica si se va a realizar una captura previa de los objetos de la tabla y se almacenarán en caché.  El comportamiento predeterminado es la captura previa de determinadas propiedades de tabla mediante el componente SMO basado en un cálculo interno.  Este parámetro puede ser útil en escenarios en los que la operación de captura previa de SMO tarda bastante más tiempo en ejecutarse. Si no se utiliza este parámetro, esta decisión se toma en tiempo de ejecución en función del porcentaje de tablas que se agregan como artículos a la publicación.  
  
|Valor OutputVerboseLevel|Descripción|  
|------------------------------|-----------------|  
|**0**|La llamada al método de captura previa del componente SMO está deshabilitada.|  
|**1**|El Agente de instantáneas llamará al método de captura previa para almacenar en caché algunas propiedades de tabla mediante SMO.|  
  
 **-PacketSize** _packet_size_  
 Es el tamaño del paquete (en bytes) que usa el Agente de instantáneas al conectar a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. El valor predeterminado es 8192 bytes.  
  
> [!NOTE]  
>  No cambie el tamaño de los paquetes a menos que esté seguro de que mejorará el rendimiento. En la mayoría de las aplicaciones, el tamaño más conveniente de los paquetes es el tamaño predeterminado.  
  
 **-ProfileName** _profile_name_  
 Especifica un perfil de agente para utilizar para los parámetros del agente. Si **ProfileName** es NULL, el perfil de agente se deshabilita. Si no se especifica **ProfileName** , se utiliza el perfil predeterminado para el tipo de agente. Para obtener información, vea [Perfiles del Agente de replicación](replication-agent-profiles.md).  
  
 **-PublisherDB** _publisher_database_  
 Es el nombre de la base de datos de publicación. *Este parámetro no se admite en publicadores de Oracle*.  
  
 **-PublisherDeadlockPriority** [ **-1**|**0**|**1**]  
 Es la prioridad de la conexión del Agente de instantáneas al publicador cuando se produce un interbloqueo. Este parámetro se especifica para resolver interbloqueos que se pueden producir entre las aplicaciones de usuario y el Agente de instantáneas durante la generación de instantáneas.  
  
|Valor PublisherDeadlockPriority|Descripción|  
|-------------------------------------|-----------------|  
|**-1**|Cuando se produce un interbloqueo en el publicador, tienen prioridad las aplicaciones distintas del Agente de instantáneas.|  
|**0** (predeterminado)|No se asigna prioridad.|  
|**1**|El Agente de instantáneas tiene la prioridad cuando se produce un interbloqueo en el publicador.|  
  
 **-PublisherFailoverPartner** _server_name_[ **\\** _instance_name_]  
 Especifica la instancia del asociado de conmutación por error de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que participa en una sesión de creación de reflejo de la base de datos con la base de datos de publicación. Para obtener más información, vea [Replicación y creación de reflejo de la base de datos &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).  
  
 **-PublisherLogin** _publisher_login_  
 Es el inicio de sesión que se usa al conectar con el publicador mediante autenticación de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 **-PublisherPassword** _publisher_password_  
 Es la contraseña que se usa al conectar con el publicador mediante autenticación de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . .  
  
 **-PublisherSecurityMode** [ **0**| **1**]  
 Especifica el modo de seguridad del publicador. Un valor de **0** hace referencia a la autenticación de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (predeterminado) y un valor de **1** hace referencia al modo de autenticación de Windows.  
  
 **-QueryTimeOut** _query_time_out_seconds_  
 Es el número de segundos antes de que la consulta exceda el tiempo de espera. El valor predeterminado es 1800 segundos.  
  
 **-ReplicationType** [ **1**| **2**]  
 Especifica el tipo de replicación. Un valor de **1** indica la replicación transaccional y un valor de **2** indica la replicación de mezcla.  
  
 **-RowDelimiter** _row_delimiter_  
 Es el carácter o secuencia de caracteres que marca el fin de una fila en el archivo de datos de copia masiva de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . El valor predeterminado es \n\<,@g>\n.  
  
 **-StartQueueTimeout** _start_queue_timeout_seconds_  
 Es el número máximo de segundos que el Agente de instantáneas espera cuando el número de procesos de instantáneas dinámicas simultáneas que se ejecutan está en el límite establecido por la **@max_concurrent_dynamic_snapshots** propiedad de [Sp_addmergepublication &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql). Si se alcanza el número máximo de segundos y el Agente de instantáneas todavía está esperando, se cerrará. Un valor de 0 significa que el agente espera indefinidamente, aunque se puede cancelar.  
  
 \- **UsePerArticleContentsView** _use_per_article_contents_view_  
 Este parámetro ha quedado desusado y solamente se admite por compatibilidad con versiones anteriores.  
  
## <a name="remarks"></a>Observaciones  
  
> [!IMPORTANT]  
>  Si ha instalado el Agente [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] para que se ejecute en una cuenta de sistema local en lugar de hacerlo en una cuenta de usuario de dominio (el valor predeterminado), el servicio solamente puede tener acceso al equipo local. Si el Agente de instantáneas que se ejecuta en el Agente [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] se configura para usar el modo de autenticación de Windows cuando inicia sesión en una instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], el Agente de instantáneas devuelve un error. La configuración predeterminada es la autenticación de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 Para iniciar el Agente de instantáneas, ejecute **snapshot.exe** desde el símbolo del sistema. Para obtener información, vea [Aplicaciones ejecutables del Agente de replicación](../concepts/replication-agent-executables-concepts.md).  
  
## <a name="see-also"></a>Consulte también  
 [Administración del Agente de replicación](replication-agent-administration.md)  
  
  
