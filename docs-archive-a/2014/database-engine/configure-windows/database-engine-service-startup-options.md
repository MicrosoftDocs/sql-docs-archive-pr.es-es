---
title: Opciones de inicio del servicio de motor de base de datos | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- single-user mode [SQL Server], startup option
- overriding default startup options
- minimal configuration mode [SQL Server], startup option
- default startup options
- temporarily override default startup options [SQL Server]
- startup options [SQL Server]
- starting SQL Server, options
ms.assetid: d373298b-f6cf-458a-849d-7083ecb54ef5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 844c0813453d371ed204dff6f8976f08bad63fe5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674316"
---
# <a name="database-engine-service-startup-options"></a>Opciones de inicio del servicio de motor de base de datos
  Las opciones de inicio señalan ciertas ubicaciones de archivos necesarios durante el inicio y especifican algunas condiciones generales del servidor. La mayoría de los usuarios no necesitan especificar opciones de inicio a menos que estén solucionando un problema de [!INCLUDE[ssDE](../../includes/ssde-md.md)] o que tengan un problema muy poco frecuente y que se les indique que usen una opción de inicio desde el soporte al cliente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!WARNING]  
>  El uso incorrecto de opciones de inicio puede afectar al rendimiento del servidor y puede impedir que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inicie.  
  
## <a name="about-startup-options"></a>Acerca de las opciones de inicio  
 Cuando instala [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], el programa de instalación escribe una serie de opciones de inicio predeterminadas en el Registro de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Puede utilizar estas opciones de inicio para especificar un archivo alternativo para la base de datos maestra, el archivo de registro de la base de datos maestra o un archivo de registro de errores. Si [!INCLUDE[ssDE](../../includes/ssde-md.md)] no puede encontrar los archivos necesarios, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no se iniciará.  
  
 Las opciones de inicio se pueden definir mediante el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para obtener más información, vea [Configurar opciones de inicio del servidor &#40;Administrador de configuración de SQL Server&#41;](scm-services-configure-server-startup-options.md).  
  
## <a name="list-of-startup-options"></a>Lista de opciones de inicio  
  
|Opciones de inicio predeterminadas|Descripción|  
|-----------------------------|-----------------|  
|**-d**  *master_file_path*|Ruta de acceso completa del archivo de base de datos maestra (normalmente, C:\Archivos de programa\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\master.mdf). Si no proporciona esta opción, se usarán los parámetros del Registro existentes.|  
|**-e**  *error_log_path*|Ruta de acceso completa del archivo de registro de errores (normalmente, C:\Archivos de programa\Microsoft SQL Server\MSSQL.*n*\MSSQL\LOG\ERRORLOG). Si no proporciona esta opción, se usarán los parámetros del Registro existentes.|  
|**-l**  *master_log_path*|Ruta de acceso completa del archivo de registro de la base de datos maestra (normalmente, C:\Archivos de programa\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\mastlog.ldf). Si no especifica esta opción, se usarán los parámetros del Registro existentes.|  
  
|Otras opciones de inicio|Descripción|  
|---------------------------|-----------------|  
|**-c**|Acorta el tiempo de inicio al iniciar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] desde el símbolo del sistema. Normalmente, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] se inicia como un servicio llamando al Administrador de control de servicios. Dado que [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] no se inicia como un servicio cuando se inicia desde el símbolo del sistema, use **-c** para omitir este paso.|  
|**-f**|Inicia una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con la configuración mínima. Esta opción resulta útil si el valor de una opción de configuración (por ejemplo, la confirmación excesiva de memoria) ha impedido el inicio del servidor. Al iniciar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en modo de configuración mínimo, se coloca [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en modo de usuario único. Para obtener más información, vea la descripción para **-m** de aquí.|  
|**-g**  *memoria_para_reserva*|Especifica un número entero de megabytes (MB) de memoria que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dejará disponible para asignaciones de memoria dentro del proceso de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , pero fuera del bloque de memoria de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . La memoria fuera del bloque de memoria es el área que utiliza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para cargar elementos, como archivos .dll de procedimientos extendidos, proveedores OLE DB a los que hacen referencia las consultas distribuidas y objetos de automatización a los que se hace referencia en instrucciones [!INCLUDE[tsql](../../includes/tsql-md.md)] . El valor predeterminado es 256 MB.<br /><br /> El uso de esta opción puede ayudarle a optimizar la asignación de memoria, pero solo cuando la memoria física supera el límite establecido por el sistema operativo de memoria virtual disponible para las aplicaciones. El uso de esta opción puede ser apropiado para configuraciones con mucha memoria en las que los requisitos de memoria de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no sean típicos y el espacio de direcciones virtuales del proceso de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se utilice completamente. Si se usa esta opción de manera incorrecta, una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] podría no iniciarse o tener errores en tiempo de ejecución.<br /><br /> Use el valor predeterminado del parámetro **-g** , a menos que vea alguna de las siguientes advertencias en el registro de errores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :<br /><br /> -"Failed virtual allocate bytes: FAIL_VIRTUAL_RESERVE \<size> "<br /><br /> -"Failed virtual allocate bytes: FAIL_VIRTUAL_COMMIT \<size> "<br /><br /> Estos mensajes podrían indicar que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] está intentando liberar partes del bloque de memoria de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a fin de buscar espacio para elementos como los archivos .dll de procedimientos almacenados extendidos u objetos de automatización. En este caso, considere la posibilidad de aumentar la cantidad de memoria reservada con el modificador **-g** .<br /><br /> Si usa un valor inferior al predeterminado, aumentará la cantidad de memoria disponible para el bloque de memoria controlado por el administrador de memoria de SQL Server y las pilas de subprocesos; esto podría proporcionar ventajas de rendimiento para cargas de trabajo que consuman mucha memoria en sistemas que no Usen procedimientos almacenados extendidos, consultas distribuidas u objetos de automatización.|  
|**-m**|Inicia una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en modo de usuario único. Al iniciar una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en modo de usuario único, solo se podrá conectar un usuario y no se iniciará el proceso CHECKPOINT. CHECKPOINT garantiza que se escriban periódicamente las transacciones completadas desde la memoria caché de disco al dispositivo de la base de datos. (Normalmente, esta opción se utiliza si las bases de datos del sistema tienen problemas y es necesario repararlas). Habilita la opción sp_configure allow updates. De manera predeterminada, la opción allow updates está deshabilitada. Al iniciar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en modo de usuario único se permite que cualquier miembro del grupo local de administradores del equipo se conecte a la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] como miembro del rol fijo de servidor sysadmin. Para obtener más información, vea [Conectarse a SQL Server cuando los administradores del sistema no tienen acceso](connect-to-sql-server-when-system-administrators-are-locked-out.md). Para obtener más información sobre el modo de usuario único, vea [Iniciar SQL Server en modo de usuario único](start-sql-server-in-single-user-mode.md).|  
|**-m "nombre de la aplicación cliente"**|Limita las conexiones a una aplicación cliente especificada cuando se usa la opción **-m** con **SQLCMD** o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Por ejemplo, **-m"SQLCMD"** limita las conexiones a una conexión única y esa conexión se debe identificar como el programa cliente **SQLCMD**. Use esta opción cuando esté iniciando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en modo de usuario único y una aplicación cliente desconocida esté usando la única conexión disponible. Para conectarse a través del Editor de consultas en [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], use **-m"Microsoft SQL Server Management Studio - Query"** .<br /><br /> En el nombre de la aplicación cliente se distinguen mayúsculas y minúsculas.<br /><br /> Nota de seguridad no use esta opción como una característica de seguridad. ** \* \* \* \* ** La aplicación cliente proporciona el nombre de la misma y puede proporcionar un nombre falso como parte de la cadena de conexión.|  
|**-n**|No usa el registro de aplicaciones de Windows para registrar los eventos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Si inicia una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con **-n**, se recomienda usar también la opción de inicio **-e**. De lo contrario, no se registrarán los eventos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|**-s**|Permite iniciar una instancia con nombre de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si no establece el parámetro **-s** , intentará iniciarse la instancia predeterminada. Debe cambiar al directorio BINN apropiado para la instancia en una ventana del símbolo del sistema antes de iniciar **sqlservr.exe**. Por ejemplo, si Instance1 usara \mssql$Instance1 para sus archivos binarios, el usuario debería estar en el directorio \mssql$Instance1\binn para poder iniciar **sqlservr.exe -s instance1**.|  
|**-T**  *trace#*|Indica que se debe iniciar una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con una marca de seguimiento específica (*trace#* ) vigente. Las marcas de seguimiento se utilizan para iniciar el servidor con un comportamiento distinto del habitual. Para obtener más información, vea [Marcas de seguimiento &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).<br /><br /> ** \* \* Importante \* al \* ** especificar una marca de seguimiento con la opción **-T** , use una "T" mayúscula para pasar el número de marca de seguimiento. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]acepta una "t" minúscula, pero esto establece otras marcas de seguimiento internas que solo serán necesarias para los ingenieros de soporte de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . (Los parámetros especificados en la ventana de inicio del Panel de control no se leen).|  
|**-x**|Deshabilita las características de supervisión siguientes:<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contadores del monitor de rendimiento<br /><br /> Mantener estadísticas del tiempo de CPU y de la frecuencia de aciertos de caché<br /><br /> Recopilar información para el comando DBCC SQLPERF<br /><br /> Recopilar información para algunas vistas de administración dinámica<br /><br /> Muchos puntos de evento de eventos extendidos<br /><br /> <br /><br /> ** \* \* Advertencia \* cuando \* ** se usa la opción **de inicio-x** , [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se reduce enormemente la información que está disponible para diagnosticar problemas funcionales y de rendimiento.|  
|**-E**|Aumenta el número de extensiones que se asignan para cada archivo en un grupo de archivos. Esta opción puede ser útil para las aplicaciones de almacenamiento de datos que tienen un número limitado de usuarios que ejecutan índices o realizan exámenes de datos. No se debería usar en otras aplicaciones porque podría afectar negativamente al rendimiento. Esta opción no se admite en las versiones de 32 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
## <a name="using-startup-options-for-troubleshooting"></a>Usar opciones de inicio para solucionar problemas  
 Algunas opciones de inicio, como el modo de usuario único y el modo de configuración mínima, se usan principalmente para solucionar problemas. Iniciar el servidor para solucionar problemas con las opciones **-m** o **-f** es mucho más fácil si se hace en la línea de comandos, mientras se inicia sqlservr.exe de forma manual.  
  
> [!NOTE]  
>  Cuando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se inicia por medio de **net start**, las opciones de inicio usan una barra (/) en lugar de un guion (-).  
  
## <a name="using-startup-options-during-normal-operations"></a>Usar opciones de inicio durante operaciones normales  
 Es posible que desee usar algunas opciones de inicio siempre que se inicie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Estas opciones, como **-g** o a partir de una marca de seguimiento, se llevan a cabo más fácilmente configurando los parámetros de inicio mediante [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager. Esta herramienta guarda las opciones de inicio como claves del Registro, lo que habilita que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] siempre se inicie con las opciones de inicio activadas.  
  
## <a name="compatibility-support"></a>Soporte de compatibilidad  
 El parámetro **-h**  no es compatible con [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Este parámetro se usaba en versiones anteriores de instancias de 32 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para reservar espacio de direcciones de memoria virtual para los metadatos de Agregar memoria sin interrupción cuando AWE está habilitado. Para más información, vea [Características de SQL Server no disponibles en SQL Server 2014](../../getting-started/discontinued-sql-server-features-in-sql-server-2014.md).  
  
## <a name="related-tasks"></a>Related Tasks  
 [Establecer la opción de configuración del servidor Buscar procedimientos de inicio](configure-the-scan-for-startup-procs-server-configuration-option.md)  
  
 [Iniciar, detener, pausar, reanudar y reiniciar el motor de base de datos, Agente SQL Server o el Servicio SQL Server Browser](start-stop-pause-resume-restart-sql-server-services.md)  
  
## <a name="see-also"></a>Consulte también  
 [CHECKPOINT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/checkpoint-transact-sql)   
 [sqlservr (aplicación)](../../tools/sqlservr-application.md)  
  
  
