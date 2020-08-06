---
title: Ejecutar el asesor de actualizaciones (símbolo del sistema) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], running
- command prompt [Upgrade Advisor]
- UpgradeAdvisorWizardCmd utility
- XML formats [Upgrade Advisor]
ms.assetid: 7c83049b-9227-4723-9b7f-66288bc6bd1d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a968f9d70788e1100af263f3ef9947493b4bd0c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662492"
---
# <a name="running-upgrade-advisor-command-prompt"></a>Ejecutar el Asesor de actualizaciones (símbolo del sistema)
  Use la utilidad **UpgradeAdvisorWizardCmd** para ejecutar el asesor de actualizaciones desde el símbolo del sistema. Puede elegir recibir los resultados en formato XML o en un archivo con valores separados por comas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      UpgradeAdvisorWizardCmd [ -? ]  |   
    [ -ConfigFilefilename | <server_info> ]  
    [ -SqlUserlogin_id-SqlPasswordpassword ]  
    [ -CSV ]  
  
where <server_info> is any combination of the following:  
        -Serverserver_name-Instanceinstance_name-ASInstanceAS_instance_name-RSInstanceRS_instance_name  
```  
  
## <a name="arguments"></a>Argumentos  
 **-?**  
 Muestra la sintaxis del comando.  
  
 **-CONFIGFILE** _nombreDeArchivo_  
 Es el nombre de la ruta de acceso y el nombre de un archivo XML que contiene la configuración que se va a usar al ejecutar la utilidad **UpgradeAdvisorWizardCmd** .  
  
 *<server_info>*  
 Especifica qué equipo e instancia se deben analizar. Use estas opciones si no usa un archivo de configuración.  
  
 *<server_info>* puede ser cualquier combinación de los cuatro argumentos siguientes:  
  
 **-SERVER_NAME de servidor** _server_name_  
 Especifica el nombre del equipo que se va a analizar. Éste puede ser el equipo local, que es el valor predeterminado, o un equipo remoto.  
  
 **-Instance_name de instancia** _instance_name_  
 Especifica el nombre de la instancia que se va a analizar. No hay ningún valor predeterminado. Si no especifica este parámetro, [!INCLUDE[ssDE](../../includes/ssde-md.md)] no se examina. El valor para una instancia predeterminada de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] es MSSQLSERVER. Para una instancia con nombre, utilice el nombre de la instancia.  
  
 **-Instance**  _AS_instance_name_  
 Especifica el nombre de la instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] que se va a analizar. No hay ningún valor predeterminado. Si no especifica este valor, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] no se examina. El valor para la instancia predeterminada de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] es MSSQLServerOLAPService. Para una instancia con nombre, utilice el nombre de la instancia.  
  
 **-RSInstance**  _RS_instance_name_  
 Especifica el nombre de la instancia de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] que se va a analizar. No hay ningún valor predeterminado. Si no especifica este valor, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] no se examina. El valor para una instancia predeterminada de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] es ReportServer. Para una instancia con nombre, utilice el nombre de la instancia.  
  
 **-SqlUser** _login_id_  
 Si está utilizando la autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], este valor representa el inicio de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que utilizará el Asesor de actualizaciones para conectarse con la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si no especifica un inicio de sesión, se utilizará el sistema de autenticación de Windows para conectarse a la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **-SqlPassword** _contraseña_  
 Si usa el argumento **-SqlUser** , use este argumento para especificar la contraseña para el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Inicio de sesión.  
  
 **-CSV**  
 Proporciona los resultados como valores separados por comas en un archivo .csv, además de los resultados XML estándar. Los resultados se escriben en la carpeta My Documents \\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] upgrade Advisor\110\Reports  
  
## <a name="return-values"></a>Valores devueltos  
 En la tabla siguiente se muestran los valores que devuelve **UpgradeAdvisorWizardCmd** .  
  
|Value|Descripción|  
|-----------|-----------------|  
|0|El análisis se llevó a cabo correctamente y no se encontró ningún problema de actualización.|  
|entero positivo|El análisis se llevó a cabo correctamente pero se encontraron problemas de actualización.|  
|entero negativo|Error en el análisis.|  
  
## <a name="remarks"></a>Observaciones  
 Es posible proporcionar toda la información que se requiere para ejecutar el análisis, excepto los nombres de usuarios y contraseñas para la autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], en un archivo de configuración XML. Este archivo de configuración XML se documenta en la plantilla. Si no utiliza un archivo de configuración, puede analizar todos los componentes instalados en una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con la configuración predeterminada especificando nombres de equipos y nombres de instancias. Vea la tabla "Descripción de los elementos" más adelante en este tema para obtener una descripción de la configuración del archivo de configuración predeterminada.  
  
## <a name="configuration-file-template"></a>Plantilla del archivo de configuración  
 Use el siguiente XML como plantilla para crear sus propios archivos de configuración. Puede modificar la plantilla para adecuarla a las necesidades de la organización.  
  
```xml  
<Configuration>  
    <Server> </Server>  
    <Instance></Instance>  
    <Components>  
        <SQLServer>  
            <Databases>  
                <Database></Database>  
            </Databases>  
            <TraceFiles>  
                <TraceFile></TraceFile>  
            </TraceFiles>  
            <BatchFiles>  
                <BatchFile></BatchFile>  
            </BatchFiles>  
            <BatchSeparator></BatchSeparator>  
        </SQLServer>  
        <AnalysisServices>  
            <ASInstance></ASInstance>  
            <Databases>  
                <Database></Database>  
            </Databases>  
        </AnalysisServices>  
        <ReportingServices>  
            <RSInstance></RSInstance>  
        </ReportingServices>  
        <IntegrationServices>  
            <PackagePath></PackagePath>  
        </IntegrationServices>  
    </Components>  
</Configuration>  
```  
  
## <a name="element-descriptions"></a>Descripción de los elementos  
  
|Etiqueta|Definición|Repetición|  
|---------|----------------|----------------|  
|`Configuration`|Elemento primario para el archivo de configuración del Asesor de actualizaciones.|Se requiere una vez por cada archivo de configuración.|  
|`Server`|Nombre del servidor que se debe analizar.|Se puede utilizar una vez por cada archivo de configuración. El valor predeterminado es el nombre del equipo local.|  
|`Instance`|Nombre de la instancia de [!INCLUDE[ssDE](../../includes/ssde-md.md)] que se va a analizar.|Se puede utilizar una vez por cada archivo de configuración. El valor predeterminado es la instancia predeterminada.<br /><br /> Si hay un elemento de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o de `IntegrationServices` presente en el servidor, se requiere una vez por archivo de configuración.|  
|`Components`|Contiene elementos que especifican qué componentes se van a analizar.|Se requiere una vez por cada archivo de configuración.|  
|`SQLServer`|Contiene la configuración del análisis para una instancia de [!INCLUDE[ssDE](../../includes/ssde-md.md)].|Se puede utilizar una vez por cada archivo de configuración. Si no se especifica, no se analizarán las bases de datos de [!INCLUDE[ssDE](../../includes/ssde-md.md)].|  
|`Databases` para el elemento `SQLServer`|Contiene una lista de bases de datos que se van a analizar.|Opcional una vez por `SQLServer` elemento. Si este elemento no está presente, se analizarán todas las bases de datos en la instancia.|  
|`Database` para el elemento `SQLServer`|Especifica el nombre de la base de datos que se va a analizar.|Se requiere una vez o más en caso de que esté presente el elemento `Databases`. Si un elemento `Database` contiene el valor "*", se analizarán todas las bases de datos de la instancia. No hay ningún valor predeterminado.|  
|`TraceFiles`|Contiene una lista de los archivos de seguimiento que se van a analizar.|Opcional una vez por `SQLServer` elemento.|  
|`TraceFile`|Especifica la ruta y el nombre del archivo de seguimiento que se va a analizar.|Se requiere una vez o más en caso de que esté presente el elemento `TraceFiles`. No hay ningún valor predeterminado.|  
|`BatchFiles`|Contiene una lista de los archivos por lotes que se van a analizar.|Opcional una vez por `SQLServer` elemento.|  
|`BatchFile`|Especifica un archivo por lotes que se va a analizar. Pueden ser varios.|Se requiere una vez o más en caso de que esté presente el elemento `BatchFiles`. No hay ningún valor predeterminado.|  
|`BatchSeparator`|Especifica el separador de lotes utilizado en sus archivos por lotes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|Opcional una vez por `SQLServer` elemento. El valor predeterminado es GO.|  
|`AnalysisServices`|Contiene la configuración de análisis para [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|Se puede utilizar una vez por cada archivo de configuración. Si no se especifica, no se analizarán las bases de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|`ASInstance`|Especifica el nombre de una instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|Se requiere una vez por elemento `AnalysisServices`. No hay ningún valor predeterminado.|  
|`Databases` para el elemento `Analysis Services`|Contiene una lista de bases de datos que se van a analizar.|Opcional una vez por `AnalysisServices` elemento. Si este elemento no está presente, se analizarán todas las bases de datos en la instancia.|  
|`Database` para el elemento `AnalysisServices`|Especifica el nombre de la base de datos que se va a analizar.|Se requiere una vez o más en caso de que esté presente el elemento `Databases`. Si un elemento `Database` contiene el valor "*", se analizarán todas las bases de datos de la instancia. No hay ningún valor predeterminado.|  
|`ReportingServices`|Especifica que se ejecute análisis contra [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|Se puede utilizar una vez por cada archivo de configuración. Si no se especifica, no se analizará [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
|`RSInstance`|Especifica el nombre de una instancia de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|Se requiere una vez por elemento `ReportingServices`. No hay ningún valor predeterminado.|  
|`IntegrationServices`|Contiene la configuración de análisis para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].|Se puede utilizar una vez por cada archivo de configuración. Si no se especifica, no se analizará [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].|  
|`PackagePath`|Especifica la ruta de acceso de un conjunto de paquetes de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].|Opcional una vez por `IntegrationServices` elemento. Si este elemento no está presente, el análisis se produce en la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instancia y no se analiza ningún paquete almacenado externamente. No hay ningún valor predeterminado.|  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-run-upgrade-advisor-using-a-configuration-file"></a>A. Ejecutar el Asesor de actualizaciones mediante un archivo de configuración  
 En el ejemplo siguiente se muestra cómo ejecutar el Asesor de actualizaciones desde el símbolo del sistema o mediante un archivo de configuración que especifica los elementos que se deben analizar. En este ejemplo se usa la autenticación de Windows para conectarse con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
UpgradeAdvisorWizardCmd -ConfigFile "C:\My Documents\UpgradeConfig1.xml"  
```  
  
### <a name="b-run-upgrade-advisor-using-default-configuration-settings"></a>B. Ejecutar el Asesor de actualizaciones utilizando la configuración predeterminada  
 En el ejemplo siguiente se muestra cómo ejecutar el Asesor de actualizaciones desde el símbolo del sistema mediante la configuración predeterminada y el sistema de autenticación de Windows.  
  
```  
UpgradeAdvisorWizardCmd -Server MyServer -Instance MyInst   
```  
  
### <a name="c-run-upgrade-advisor-using-ssnoversion-authentication"></a>C. Ejecutar el Asesor de actualizaciones mediante el sistema de autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 En el ejemplo siguiente se muestra cómo ejecutar el Asesor de actualizaciones desde el símbolo del sistema mediante un archivo de configuración. En este ejemplo se especifica un nombre de usuario y una contraseña de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para conectarse a la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
UpgradeAdvisorWizardCmd -ConfigFile "C:\My Documents\UpgradeConfig1.xml"   
    -SqlUser "MyUserName" -SqlPassword "QweRTy-55"  
```  
  
## <a name="see-also"></a>Consulte también  
 [Resolver problemas de actualización](../../../2014/sql-server/install/resolving-upgrade-issues.md)   
 [Trabajar con el asesor de actualizaciones](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Ejecutar el asesor de actualizaciones &#40;interfaz de usuario&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md)  
  
  
