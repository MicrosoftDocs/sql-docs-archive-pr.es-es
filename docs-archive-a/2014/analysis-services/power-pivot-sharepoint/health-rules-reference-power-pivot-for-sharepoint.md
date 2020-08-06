---
title: Referencia de reglas de estado (PowerPivot para SharePoint) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 47ae04ce-7b9d-49c2-8dbc-bafcb73d4603
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5e4c895cf55742b8db89bd86f7fe4c5277ef7a6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744396"
---
# <a name="health-rules-reference-powerpivot-for-sharepoint"></a>Referencia de reglas de estado (PowerPivot para SharePoint)
  Este tema de referencia se describen las reglas de estado de SharePoint que se agregan a una instalación de PowerPivot para SharePoint. Estas reglas se usan para notificar problemas con el mantenimiento, la disponibilidad o la configuración del servidor de una aplicación de servicio [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] o su instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] asociada.  
  
 En la tabla siguiente se enumeran las reglas en el orden en que aparecen en la página Definiciones de la regla de analizador de mantenimiento de Administración central de SharePoint. Las reglas configurables son aquellas para las que puede cambiar los umbrales en los que se desencadenan. Para obtener más información, vea [reglas de estado de PowerPivot: configurar](configure-power-pivot-health-rules.md). La reparación automática indica que hay un remedio integrado en el que se puede hacer clic en la página de informes de problemas para resolver el problema.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|  
  
 **Nota** [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] instala distintos conjuntos de reglas de mantenimiento para las diferentes versiones de SharePoint. Vea la columna "versión" de la tabla siguiente, o bien puede ejecutar el siguiente comando de Windows PowerShell para ver las reglas instaladas.  
  
```powershell
Get-SPHealthAnalysisRule | Select name, enabled, summary | Where {$_.summary -like "*power*"}  | Format-Table -Property * -AutoSize | Out-Default  
```  
  
|Regla|Configurable|Reparación automática|Versión|Descripción|  
|----------|------------------|-----------------|-------------|-----------------|  
|PowerPivot: el proveedor OLE DB de Analysis Services no está instalado en este equipo.|No|No|SharePoint 2010|El proveedor OLE DB de Analysis Services no está instalado en el servidor o la versión es incorrecta. Esta regla aparece cuando la granja de SharePoint incluye las instancias de Excel Services en los servidores de aplicaciones que no tienen PowerPivot para SharePoint. La regla le advierte de que el proveedor OLE DB de Analysis Services que Excel Services usa para conectarse a los datos PowerPivot no está instalado. Para resolver este problema, instale el proveedor OLE DB en cada servidor Excel Services que no tenga el proveedor OLE DB de Analysis Services. Puede descargar e instalar el proveedor OLE DB de Analysis Services desde el centro de descarga de Microsoft. Para más información, consulte [Instalar el proveedor OLE DB de Analysis Services en servidores de SharePoint](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).|  
|PowerPivot: la configuración del Registro para Microsoft.AnalysisServices.ChannelTransport.dll no es válida después de instalar la versión SQL Server 2008 R2 del proveedor MSOLAP en este equipo.|No|Sí|SharePoint 2010|Se trata de un problema de configuración del servidor. Probablemente, el archivo ChannelTransport.dll no esté registrado en el ensamblado global. Ejecute la reparación automática para esta regla a fin de registrar el archivo .dll en cada servidor que tenga una instalación de PowerPivot para SharePoint. Como alternativa, puede ejecutar regasm.exe manualmente para registrar el archivo. Si el servicio de temporizador de SharePoint no se está ejecutando como administrador local, se deberá realizar un registro manual. Si no se pueden actualizar los valores del Registro, se ralentiza la comunicación del servidor entre Excel Services y el servicio de sistema de PowerPivot, y puede producir errores de conexión en determinadas configuraciones de seguridad.|  
|PowerPivot: la aplicación de servicio PowerPivot no tiene permiso para completar la operación.|No|No|SharePoint 2010|Esta regla comprueba si la identidad de aplicación de servicio PowerPivot es la propietaria de la base de datos de aplicación de servidor PowerPivot y tiene permisos administrativos en la instancia local de SQL Server Analysis Services. Estos permisos se conceden automáticamente durante la instalación e implementación pero, si este paso no pudo completarse, se producirá esta regla de estado.|  
|PowerPivot: la identidad de la aplicación de servicio PowerPivot no debería ser miembro del grupo Administradores local.|No|No|SharePoint 2010|Es aconsejable que mejora la seguridad total de la implementación. Si configuró la aplicación de servicio PowerPivot para que se ejecute en una cuenta que pertenezca al grupo de administradores local, debe cambiar la cuenta de servicio a una que no pertenezca a ese grupo. Se recomienda utilizar para cada servicio una cuenta dedicada que tenga los mínimos privilegios. De ese modo, permite el aislamiento del servicio y facilita la auditoría de los inicios de sesión. Para obtener más información acerca de cómo cambiar la cuenta de servicio, vea [configurar las cuentas de servicio PowerPivot](configure-power-pivot-service-accounts.md).|  
|PowerPivot: la instancia de Analysis Services se ejecuta en modo tabular, pero la opción de configuración que especifica este modo está desactivada.|No|No|SharePoint 2010|Esta regla comprueba si la instancia de SQL Server Analysis Services en una instalación de PowerPivot para SharePoint tiene la propiedad de servidor `DeploymentMode` establecida en 1. Si la propiedad se establece en otro valor o si el servicio de temporizador de SharePoint que ejecuta el comprobador de la regla no tiene permiso para abrir el archivo, esta regla producirá un error. Para obtener más información sobre la propiedad del modo de implementación, vea [Determinar el modo de servidor de una instancia de Analysis Services](../instances/determine-the-server-mode-of-an-analysis-services-instance.md).|  
|PowerPivot: el trabajo de temporizador de actualización de datos PowerPivot está deshabilitado.|No|No|SharePoint 2013<br /><br /> SharePoint 2010|Compruebe la configuración del trabajo de temporizador para comprobar que el trabajo de temporizador está habilitado. Si no usa la característica de actualización de datos PowerPivot, puede omitir esta regla. Para obtener más información, vea [actualización de datos PowerPivot con SharePoint 2010](../powerpivot-data-refresh-with-sharepoint-2010.md).|  
|PowerPivot: la información de la cuenta de servicio de SQL Server Analysis Services (PowerPivot) que el Administrador de configuración de SQL Server administra es diferente de la información de la cuenta que se administra mediante Administración central.|No|No|SharePoint 2010|Esta regla comprueba si la información de la cuenta de servicio en el Administrador de configuración de SQL Server es idéntica a la información de la cuenta administrada en Administración central para la misma instancia de Analysis Services. Si las cuentas son diferentes, se agrega una entrada al informe de problemas y resolución para poder cambiar la información de la cuenta de servicio en el Administrador de configuración de SQL Server de nuevo a la cuenta especificada en Administración central. El Administrador de configuración de SQL Server no es una herramienta admitida para cambiar el nombre de usuario de una cuenta de servicio en una instalación de PowerPivot para SharePoint. Usar Administración central habilita el uso de la característica de cuentas administradas en SharePoint. Y, lo que es más importante, si la granja incluye varios servidores PowerPivot para SharePoint, tener una configuración incoherente de las cuentas de servicio puede interrumpir las operaciones de procesamiento y consulta en el servidor que tiene información de servicio incorrecta.<br /><br /> En un solo servidor, los libros PowerPivot funcionarán temporalmente cuando esta regla se desencadene, pero se aconseja que corrija el problema lo antes posible. Los permisos del sistema de archivos y base de datos se actualizan utilizando la información de cuentas especificada en Administración central.|  
|PowerPivot: la solución de granja implementada no está actualizada.|No|Sí|SharePoint 2010|Una instalación de PowerPivot para SharePoint utiliza una solución de nivel de granja y una solución de nivel de aplicación Web para instalar sus características. Esta regla indica que la solución de granja no es actual en relación con la versión, el servidor o, posiblemente, la solución Web. Probablemente, es problema de la implementación del servidor. Para remediar este problema, considere ejecutar el programa de instalación de SQL Server para reparar una de las instalaciones de PowerPivot para SharePoint en la granja. Para obtener más información sobre las soluciones de una instalación de PowerPivot para SharePoint, vea [implementar soluciones de PowerPivot en SharePoint](deploy-power-pivot-solutions-to-sharepoint.md).|  
|PowerPivot: el uso total de CPU es demasiado alto.|Sí|No|SharePoint 2010|Esta regla notifica el consumo de CPU en el nivel de sistema. El uso total de CPU se supervisa porque el servicio de sistema de PowerPivot lo utiliza como medida del estado de servidor, para el equilibrio de carga basado en el estado entre varios servidores PowerPivot para SharePoint en una granja. Considere agregar a otro servidor de aplicaciones a la granja y trasladar las aplicaciones que usen mucho la CPU a ese servidor.|  
|PowerPivot: Analysis Services no tiene suficientes recursos de CPU para realizar las operaciones solicitadas.|Sí|No|SharePoint 2010|La cantidad de recursos de CPU disponible para el proceso de Analysis Services (msmdsrv.exe) no es suficiente para el nivel de actividad en este servidor. Considere agregar otro servidor PowerPivot para SharePoint a la granja. Para obtener más información, vea [lista de comprobación de implementación: escalado horizontal mediante la adición de servidores de PowerPivot a una granja de servidores de SharePoint 2010](../../sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md).|  
|PowerPivot: Analysis Services no tiene suficientes recursos de memoria para realizar las operaciones solicitadas.|No|No|SharePoint 2010|Esta regla se desencadena cuando hay solo un 5% de memoria disponible para Analysis Services. En un servidor de aplicaciones SharePoint, una instancia de SQL Server Analysis Services siempre debe tener una pequeña cantidad de memoria en reserva sin usar. Dado que el servidor está enlazado a memoria en la mayoría de sus operaciones, el servidor se ejecuta mejor si no se ejecuta hasta el final del límite superior.<br /><br /> De forma predeterminada, las advertencias de memoria insuficiente aparecen cuando la memoria disponible es menor del 5 por ciento. Puede cambiar este valor para que sea mayor o menor ajustando los valores en la instancia de Analysis Services. Para obtener más información, vea [reglas de estado de PowerPivot: configurar](configure-power-pivot-health-rules.md).<br /><br /> El 5% de la memoria sin usar se calcula como un porcentaje de la memoria asignada a Analysis Services. Por ejemplo, si tiene 200 GB de memoria total y a Analysis Services se le asigna el 80% (o 160 GB), el 5% de la memoria sin usar es el 5% de 160 GB (u 8 GB).|  
|PowerPivot: el número elevado de conexiones indica que deben implementarse más servidores para administrar la carga actual.|Sí|No|SharePoint 2010|De forma predeterminada, esta regla de estado se desencadena cuando el número de conexiones distintas de usuario es superior a 100. Este valor predeterminado es arbitrario (no se basa en las especificaciones de hardware del servidor o en la actividad del usuario) de modo que podría elevar o disminuir el valor según la capacidad del servidor y la actividad de los usuarios en el entorno. Para obtener más información, vea [reglas de estado de PowerPivot: configurar](configure-power-pivot-health-rules.md).|  
|PowerPivot: la proporción de los eventos de carga y las conexiones es demasiado alta.|Sí|No|SharePoint 2013<br /><br /> SharePoint 2010|De forma predeterminada, se desencadena esta regla de estado cuando el porcentaje de eventos de carga con respecto a los eventos de conexión supere el 50% durante el período total de recopilación de datos (de forma predeterminada, 4 horas). Una proporción elevada indica un número muy alto de conexiones a libros únicos o una configuración de reducción de la memoria caché demasiado alta (donde los libros se descargan y se quitan con rapidez del sistema, mientras que las solicitudes de esos datos siguen estando activas). Para evitar contar los falsos positivos, debe haber al menos 20 conexiones por cada período de 4 horas, antes de que la proporción puede calcularse. Puede basar esta regla de estado en otra proporción. Para obtener más información, vea [reglas de estado de PowerPivot: configurar](configure-power-pivot-health-rules.md). Para obtener más información sobre la configuración de la memoria caché, vea [configurar el uso del espacio en disco &#40;PowerPivot para SharePoint&#41;](configure-disk-space-usage-power-pivot-for-sharepoint.md).|  
|PowerPivot: se encontraron uno o varios archivos de minidump en el directorio de registros, lo que indica un bloqueo del programa.|No|No|SharePoint 2013<br /><br /> SharePoint 2010|Los archivos de Minidump se generan durante el bloqueo de un programa para capturar información sobre el estado de la aplicación de servicio PowerPivot solo antes del error. Esta información se puede enviar a Microsoft y utilizarse para solucionar problemas. Esta regla se desencadena cuando los archivos .dmp se detectan en el servidor. La regla proporciona un vínculo al archivo, que se encuentra en la carpeta \OLAP\Log de la instancia PowerPivot para SharePoint. Tenga en cuenta que no puede utilizar un editor de texto para ver el contenido. Para ver un archivo de minidump es necesario descargar e instalar una herramienta de depuración independiente. Para obtener más información, vea [Herramientas de depuración de Windows](/windows-hardware/drivers/debugger/).|  
|PowerPivot: el espacio en disco está disminuyendo demasiado en la unidad de disco donde los datos PowerPivot se almacenan en caché.|Sí|No|SharePoint 2010|De forma predeterminada, esta regla de estado se desencadena cuando el espacio en disco es menor del 5% en la unidad de disco donde se encuentra la carpeta de copia de seguridad. Para obtener más información sobre la configuración de este porcentaje, vea [reglas de estado de PowerPivot-configurar](configure-power-pivot-health-rules.md). Para obtener más información acerca del uso de disco, vea [configurar el uso del espacio en disco &#40;PowerPivot para SharePoint&#41;](configure-disk-space-usage-power-pivot-for-sharepoint.md).|  
|PowerPivot: los datos de uso no se actualizan con la frecuencia esperada.|Sí|No|SharePoint 2013<br /><br /> SharePoint 2010|PowerPivot para SharePoint utiliza la infraestructura del sistema de recopilación de datos de uso integrada para recopilar la métrica de las conexiones, la actualización de datos y los tiempos de respuesta de la consulta. Almacena estos datos de uso en la base de datos de aplicación de servicio PowerPivot, que a su vez actualiza un libro PowerPivot (PowerPivot Management Data.xlsx) que proporciona datos a los informes del Panel de administración de PowerPivot. Esta regla indica que los datos de uso no se van a mover al archivo PowerPivot Management Data.xlsx con suficiente frecuencia. La regla utiliza la marca de tiempo en el archivo .xlsx como prueba que el archivo está actualizado. Si hay otros problemas en el sistema de recopilación de datos de uso que desvirtúan la precisión de los datos, esta regla no se detectará. Para solucionar este error, examine los trabajos del temporizador para comprobar que se están ejecutando. Para obtener más información acerca de la recopilación de datos de uso, vea [configurar la recopilación de datos de uso para &#40;PowerPivot para SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md).|  
|PowerPivot: la cuenta de proceso de nivel intermedio debe tener el permiso ' acceso completo de lectura ' en todas las SPWebApplications asociadas.|No|Sí|SharePoint 2013<br /><br /> SharePoint 2010|La identidad de la aplicación de servicio PowerPivot debe tener permisos de **lectura completos** para tener acceso a las bases de datos de contenido de SharePoint en nombre de los usuarios que tienen permisos de solo visualización en un documento. Para determinar qué cuenta se usa como identidad de aplicación de servicio PowerPivot, abra la página **configurar cuentas de servicio** en administración central. Probablemente, la aplicación de servicio se ejecuta en el grupo de aplicaciones de servicio de **SharePoint Web Services System** o en un grupo de aplicaciones dedicado. Aunque esta regla proporciona una opción de reparación automática, obtendrá mejores resultados si concede los permisos manualmente haciendo lo siguiente:<br /><br /> 1) En Administración central, haga clic en **Administrar aplicaciones web**.<br /><br /> 2) Seleccione un sitio web y haga clic en **Directiva de usuario**.<br /><br /> 3) Haga clic en **Agregar usuarios**.<br /><br /> 4) Seleccione (Todas las zonas) y haga clic en **Siguiente**.<br /><br /> 5) en usuarios, escriba la identidad de aplicación de servicio PowerPivot y, a continuación, haga clic en la casilla **lectura completa** . Haga clic en **Finalizar**<br /><br /> 6) Compruebe la reparación. En Supervisión, haga clic en **Revisar las definiciones de la regla**. Busque y abra la regla de PowerPivot. Haga clic en **Ejecutar ahora**. Vuelva a **Revisar los problemas y las soluciones** para comprobar que la regla ya no aparece.|  
|PowerPivot: el servicio de Inicio de sesión secundario (seclogon) está deshabilitado|No|No|SharePoint 2013<br /><br /> SharePoint 2010|El servicio de inicio de sesión secundario se utiliza para generar imágenes en miniatura para los libros PowerPivot en la Galería de PowerPivot. De forma predeterminada, el servicio de inicio de sesión secundario se establece en inicio manual. Si el servicio está deshabilitado, la generación de la miniatura producirá un error. Además, los registros de ULS contendrán el siguiente error: "el error 1058 puede tener como causa el hecho que el servicio de Windows" Inicio de sesión secundario "está deshabilitado".<br /><br /> Para comprobar la configuración del servicio, utilice la aplicación de consola Servicios para buscar el Inicio de sesión secundario y cambiar su **Tipo de inicio** a **Manual**. Si no puede habilitar el servicio, su organización podría tener una directiva de grupo que lo deshabilite. Consulte al administrador para determinar si es así.<br /><br /> Después de habilitar el servicio, las imágenes de vista previa en miniatura o de instantáneas se actualizarán con el tiempo. Opcionalmente, puede forzar una actualización reiniciando el servicio y abriendo y guardando después las páginas de propiedades de un informe específico. Para obtener más información, vea [Cómo usar la galería de PowerPivot](https://go.microsoft.com/fwlink/?LinkId=246462).|  
|PowerPivot: ADOMD.NET no está instalado en un front-end web independiente que se configura para administración central|No|No|SharePoint 2013<br /><br /> SharePoint 2010|ADOMD.NET es una biblioteca de cliente de Analysis Services que admite las conexiones a una base de datos de Analysis Services. En una implementación de PowerPivot para SharePoint, ADOMD.NET proporciona acceso a los informes integrados en el panel de administración de PowerPivot en Administración central. Los informes integrados son realmente libros PowerPivot que contienen datos incrustados de Analysis Services. El panel de administración utiliza ADOMD.NET para enviar una solicitud de conexión al servidor que carga los datos incluidos en el libro.<br /><br /> En las topologías que incluyen la Administración central ejecutándose en un servidor front-end web independiente, debe instalar ADOMD.NET de forma manual si desea ver estos informes en el panel de administración. Para obtener más información, vea [Instalar ADOMD.NET en servidores front-end web ejecutando Administración central](../../sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md).|  