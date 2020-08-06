---
title: Cmdlets de PowerShell para el modo Reporting Services SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7835bc97-2827-4215-b0dd-52f692ce5e02
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2b20ad870fd8a9cd7f220eebb2b954d7a88a10c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751794"
---
# <a name="powershell-cmdlets-for-reporting-services-sharepoint-mode"></a>Cmdlets de PowerShell para el modo de SharePoint de Reporting Services
  Al instalar el [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] modo de SharePoint de, se instalan los cmdlets de PowerShell para admitir servidores de informes en modo de SharePoint. Los cmdlets abarcan tres categorías de funcionalidad.  
  
-   La instalación del proxy y el servicio compartido de SharePoint de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
-   El aprovisionamiento y administración de las aplicaciones de servicio de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] y servidores proxy asociados.  
  
-   La administración de las características de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , como las extensiones y las claves de cifrado.  
  
||  
|-|  
|[!INCLUDE[applies](../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]Modo de SharePoint|  
  
 **Este tema contiene lo siguiente:**  
  
-   [Resumen de cmdlets](#bkmk_cmdlet_sum)  
  
-   [Cmdlets de servicios compartidos y proxy](#bkmk_sharedservice_cmdlets)  
  
-   [Cmdlets de aplicación de servicio y proxy](#bkmk_serviceapp_cmdlets)  
  
-   [Cmdlets de funcionalidad personalizada de Reporting Services](#bkmk_ssrsfeatures_cmdlets)  
  
-   [Ejemplos básicos](#bkmk_basic_samples)  
  
-   [Ejemplos detallados](#bkmk_detailedsamples)  
  
    -   [Creación de una aplicación de servicio de Reporting Services y proxy](#bkmk_example_create_service_application)  
  
    -   [Revisar y actualizar una extensión de entrega de Reporting Services](#bkmk_example_delivery_extension)  
  
    -   [Obtener y establecer las propiedades de la base de datos de aplicación de Reporting Services como, por ejemplo, el tiempo de espera de la base de datos](#bkmk_example_db_properties)  
  
    -   [Enumerar extensiones de datos de Reporting Services-modo de SharePoint](#bkmk_example_list_data_extensions)  
  
    -   [Cambiar propietarios de suscripciones y agregarlos a listas](#bkmk_change_subscription_owner)  
  
##  <a name="cmdlet-summary"></a><a name="bkmk_cmdlet_sum"></a>Resumen de cmdlets  

 Para ejecutar los cmdlets es necesario abrir el Shell de administración de SharePoint. También puede usar el editor de la interfaz gráfica de usuario incluido en Microsoft Windows, **Entorno de scripting integrado (ISE) de Windows PowerShell**. Para más información, vea [Starting Windows PowerShell on Windows Server](https://docs.microsoft.com/powershell/scripting/getting-started/starting-windows-powershell). En los siguientes resúmenes de cmdlet, las referencias a las bases de datos de la aplicación de servicio, hacen referencia a todas las bases de datos creadas y usadas por una [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] aplicación de servicio. Esto incluye la configuración, la creación de alertas y las bases de datos temporales.  

  
 Si ve un mensaje de error similar al siguiente al escribir los ejemplos de PowerShell:  
  
-   Install-SPRSService : El término 'Install-SPRSService' no se reconoce como  
    nombre de un cmdlet, función, archivo de script o programa ejecutable. Compruebe si escribió correctamente el nombre o, si incluyó una ruta de acceso, compruebe que dicha ruta es correcta e inténtelo de nuevo.  
  
 Se está produciendo uno de los problemas siguientes:  
  
-   [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint no está instalado y, por tanto, los cmdlets de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] no están instalados.  
  
-   Ejecutó el comando de PowerShell en Windows Powershell o Windows PowerShell ISE en lugar del Shell de administración de SharePoint. Use el Shell de administración de SharePoint o agregue el Complemento de SharePoint a la ventana de Windows PowerShell con el comando siguiente:  
  
    ```powershell
    Add-PSSnapin Microsoft.SharePoint.PowerShell  
    ```  
  
 Para obtener más información, vea [usar Windows PowerShell para administrar SharePoint 2013](https://technet.microsoft.com/library/ee806878.aspx) ( https://technet.microsoft.com/library/ee806878.aspx) .  
  
#### <a name="to-open-the-sharepoint-management-shell-and-run-cmdlets"></a>Para abrir el Shell de administración de SharePoint y ejecutar cmdlets  
  
1.  Haga clic en el botón **Inicio** .  
  
2.  Haga clic en el grupo **Productos de Microsoft SharePoint** .  
  
3.  Haga clic en **Shell de administración de SharePoint**.  
  
 Para ver la ayuda de la línea de comandos para un cmdlet, use el comando "Get-Help" de PowerShell en el símbolo del sistema de PowerShell. Por ejemplo:  
  
 `Get-Help Get-SPRSServiceApplicationServers`  
  
###  <a name="shared-service-and-proxy-cmdlets"></a><a name="bkmk_sharedservice_cmdlets"></a> Cmdlets de servicios compartidos y servidores proxy  
 La tabla siguiente contiene los cmdlets de PowerShell para el servicio compartido de SharePoint de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
|Cmdlet|Descripción|  
|------------|-----------------|  
|Install-SPRSService|Instala y registra, o desinstala, el servicio compartido de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Esta operación solo se puede realizar en el equipo que tiene una instalación de SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en modo de SharePoint. Para la instalación, se producen dos operaciones:<br /><br /> 1) el [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] servicio está instalado en la granja.<br /><br /> 2) la [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] instancia de servicio se instala en el equipo actual.<br /><br /> Para la desinstalación, se producen dos operaciones:<br />1) el [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] servicio se desinstala del equipo actual.<br />2) el [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] servicio se desinstala de la granja.<br /><br /> <br /><br /> NOTA: si hay otros equipos en la granja que tienen el servicio de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] instalado, o si todavía hay aplicaciones de servicio de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ejecutándose en la granja, se muestra un mensaje de advertencia.|  
|Install-SPRSServiceProxy|Instala y registra, o desinstala, el proxy de servicio de Reporting Services en la granja de SharePoint.|  
|Get-SPRSProxyUrl|Obtiene las direcciones URL para acceder al servicio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
|Get-SPRSServiceApplicationServers|Obtiene todos los servidores de la granja de SharePoint que contienen una instalación del servicio compartido de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Este cmdlet es útil para las actualizaciones de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , con el fin de determinar qué servidores ejecutan el servicio compartido y por tanto no es necesario actualizar.|  
  
###  <a name="service-application-and-proxy-cmdlets"></a><a name="bkmk_serviceapp_cmdlets"></a> Cmdlets de aplicaciones de servicio y servidores proxy  
 La tabla siguiente contiene los cmdlets de PowerShell para las aplicaciones de servicio de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] y sus servidores proxy asociados.  
  
|cmdlet|Descripción|  
|------------|-----------------|  
|Get-SPRSServiceApplication|Obtiene uno o más objetos de la aplicación de servicio de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
|New-SPRSServiceApplication|Crea una nueva aplicación de servicio de Reporting Services y las bases de datos asociadas.<br /><br /> Parámetro LogonType: especifica si el servidor de informes utiliza la cuenta del grupo de aplicaciones SSRS o un inicio de sesión de SQL Server para tener acceso a la base de datos del servidor de informes. Puede tener uno de los valores siguientes:<br /><br /> 0 Autenticación de Windows<br /><br /> 1 SQL Server<br /><br /> 2 Cuenta del grupo de aplicaciones (valor predeterminado)|  
|Remove-SPRSServiceApplication|Quita la aplicación de servicio de Reporting Services especificada. También se quitarán las bases de datos asociadas.|  
|Set-SPRSServiceApplication|Edita las propiedades de una aplicación de servicio de Reporting Services existente.|  
|New-SPRSServiceApplicationProxy|Crea un nuevo proxy de aplicación de servicio de Reporting Services.|  
|Get-SPRSServiceApplicationProxy|Obtiene uno o varios servidores proxy de la aplicación de servicio de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
|Dismount-SPRSDatabase|Desmonta las bases de datos de la aplicación de servicio de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
|Remove-SPRSDatabase|Quita las bases de datos de la aplicación de servicio de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
|Set-SPRSDatabase|Establece las propiedades de las bases de datos asociadas a una aplicación de servicio de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
|Mount-SPRSDatabase|Monta las bases de datos de una aplicación de servicio de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
|New-SPRSDatabase|Crea las nuevas bases de datos para la aplicación de servicio de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] especificada.|  
|Get-SPRSDatabaseCreationScript|Muestra el script de creación de bases de datos en la pantalla para una aplicación de servicio de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Este script se puede ejecutar a continuación en SQL Server Management Studio.|  
|Get-SPRSDatabase|Obtiene una o varias bases de datos de la aplicación de servicio de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Use el comando para obtener el identificador de la base de datos de la aplicación del servicio de forma que pueda usar el cmdlet Set-SPRSDatabase para modificar las propiedades, por ejemplo `querytimeout`. Vea el ejemplo de este tema, [Obtener y establecer las propiedades de la base de datos de aplicación de Reporting Services como, por ejemplo, el tiempo de espera de la base de datos](#bkmk_example_db_properties).|  
|Get-SPRSDatabaseRightsScript|Muestra el script de permisos de base de datos en la pantalla para una aplicación de servicio de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Solicita el usuario y la base de datos, y luego devuelve Transact-SQL que se puede ejecutar para modificar los permisos. Este script se puede ejecutar a continuación en SQL Server Management Studio.|  
|Get-SPRSDatabaseUpgradeScript|Muestra el script de actualización de bases de datos en la pantalla. El script actualizará las bases de datos de la aplicación de servicio de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] a la versión de base de datos de la instalación de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] actual.|  
  
###  <a name="reporting-services-custom-functionality-cmdlets"></a><a name="bkmk_ssrsfeatures_cmdlets"></a> Cmdlets de funcionalidad personalizada de Reporting Services  
  
|Cmdlet|Descripción|  
|------------|-----------------|  
|Update-SPRSEncryptionKey|Actualiza la clave de cifrado para la aplicación de servicio de Reporting Services especificada y cifra de nuevo sus datos.|  
|Restore-SPRSEncryptionKey|Restaura una clave de cifrado de la que se hizo copia de seguridad anteriormente para una aplicación de servicio de Reporting Services.|  
|Remove-SPRSEncryptedData|Elimina los datos cifrados para la aplicación de servicio de Reporting Services especificada.|  
|Backup-SPRSEncryptionKey|Realiza una copia de seguridad de la clave de cifrado para la aplicación de servicio de Reporting Services especificada.|  
|New-SPRSExtension|Registra una nueva extensión con una aplicación de servicio de Reporting Services.|  
|Set-SPRSExtension|Establece las propiedades de una extensión de Reporting Services existente.|  
|Remove-SPRSExtension|Quita una extensión de una aplicación de servicio de Reporting Services.|  
|Get-SPRSExtension|Obtiene una o varias extensiones de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] para una aplicación de servicio de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .<br /><br /> Los valores válidos son:<br /><br /> **Entrega.**<br /><br /> **DeliveryUI**<br /><br /> **Representar**<br /><br /> **Data**<br /><br /> **Seguridad**<br /><br /> **Autenticación**<br /><br /> **EventProcessing**<br /><br /> **ReportItems**<br /><br /> **Diseñador**<br /><br /> **ReportItemDesigner**<br /><br /> **ReportItemConverter**<br /><br /> **ReportDefinitionCustomization**|  
|Get-SPRSSite|Obtiene los sitios de SharePoint basándose en si está habilitada la característica "ReportingService". De forma predeterminada, se devuelven los sitios que habilitan la característica "ReportingService".|  
  
##  <a name="basic-samples"></a><a name="bkmk_basic_samples"></a>Ejemplos básicos  
 Devolver una lista de cmdlets cuyo nombre contiene "SPRS". Será la lista completa de cmdlets de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
```powershell
Get-command -noun *SPRS*  
```  
  
 O con un poco más detalle, enviar la salida a un archivo de texto denominado commandlist.txt  
  
```powershell
Get-Command -Noun *SPRS* | Select name, definition | Format-List | Out-File c:\commandlist.txt  
```  
  
 Instalar el servicio de SharePoint de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] y el proxy del servicio.  
  
```powershell
Install-SPRSService  
```  
  
```powershell
Install-SPRSServiceProxy  
```  
  
 Iniciar el servicio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]  
  
```powershell
Get-SPServiceInstance -all | where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
```  
  
 Escriba el siguiente comando desde el Shell de administración de SharePoint para devolver una lista filtrada de filas de un archivo de registro. El comando filtrará las líneas que contengan "ssrscustomactionerror". En este ejemplo se examina el archivo de registro creado cuando se instaló rssharepoint.msi.  
  
```powershell
Get-Content -Path C:\Users\testuser\AppData\Local\Temp\rs_sp_0.log | Select-String "ssrscustomactionerror"  
```  
  
##  <a name="detailed-samples"></a><a name="bkmk_detailedsamples"></a>Ejemplos detallados  
 Además de los ejemplos siguientes, vea la sección "script de Windows PowerShell" en el tema [script de Windows PowerShell para los pasos 1-4](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md#bkmk_full_script).  
  
###  <a name="create-a-reporting-services-service-application-and-proxy"></a><a name="bkmk_example_create_service_application"></a>Creación de una aplicación de servicio de Reporting Services y proxy  
 Este script de ejemplo realiza las tareas siguientes:  
  
1.  Crea una aplicación de servicio de Reporting Services y un proxy. El script asume que el grupo de aplicaciones "My App Pool" ya existe.  
  
2.  Agrega el proxy al grupo de servidores proxy predeterminado.  
  
3.  Concede acceso a la aplicación de servicio al puerto 80 de la base de datos de contenido de la aplicación web. El script asume que el sitio " http://sitename " ya existe.  
  
```powershell
# Create service application and service application proxy  
$appPool = Get-SPServiceApplicationPool "My App Pool"  
$serviceApp = New-SPRSServiceApplication "My RS Service App" -ApplicationPool $appPool  
$serviceAppProxy = New-SPRSServiceApplicationProxy -Name "My RS Service App Proxy" -ServiceApplication $serviceApp  
  
# Add service application proxy to default proxy group.  Any web application that uses the default proxy group will now be able to use this service application.  
Get-SPServiceApplicationProxyGroup -default | Add-SPServiceApplicationProxyGroupMember -Member $serviceAppProxy  
  
# Grant application pool account access to the port 80 web application's content database.  
$webApp = Get-SPWebApplication "http://sitename"  
$appPoolAccountName = $appPool.ProcessAccount.LookupName()  
$webApp.GrantAccessToProcessIdentity($appPoolAccountName)
```  
  
###  <a name="review-and-update-a-reporting-services-delivery-extension"></a><a name="bkmk_example_delivery_extension"></a>Revisar y actualizar una extensión de entrega de Reporting Services  
 El siguiente ejemplo de script de PowerShell actualiza la configuración de la extensión de entrega de correo electrónico del servidor de informes para la aplicación de servicio denominada `My RS Service App`. Actualice los valores para el servidor SMTP (`<email server name>`) y el alias de correo electrónico FROM (`<your FROM email address>`).  
  
```powershell
$app = Get-SPRSServiceApplication -Name "My RS Service App"  
$emailCfg = Get-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml
$emailXml = [xml]$emailCfg
$emailXml.SelectSingleNode("//SMTPServer").InnerText = "<email server name>"  
$emailXml.SelectSingleNode("//SendUsing").InnerText = "2"  
$emailXml.SelectSingleNode("//SMTPAuthenticate").InnerText = "2"  
$emailXml.SelectSingleNode("//From").InnerText = '<your FROM email address>'  
Set-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" -ExtensionConfiguration $emailXml.OuterXml  
```  
  
 En el ejemplo anterior, si no supiera el nombre exacto de la aplicación de servicio, podría reescribir la primera instrucción para obtener la aplicación de servicio a partir de una búsqueda del nombre parcial. Por ejemplo:  
  
```powershell
$app = Get-SPRSServiceApplication | Where {$_.name -like " ssrs_testapp *"}  
```  
  
 El script siguiente devolverá los valores de configuración actual de la extensión de entrega por correo electrónico del servidor de informes para la aplicación de servicio denominada "Reporting Services Application". El primer paso establece el valor de la variable $app en el objeto de la aplicación de servicio denominada " My RS Service App "  
  
 La segunda instrucción obtendrá la extensión de entrega por correo electrónico del servidor de informes para el objeto de aplicación de servicio de la variable $app, y seleccionará el XML de configuración.  
  
```powershell
$app = Get-SPRSServiceapplication -Name "Reporting Services Application"  
Get-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml  
```  
  
 Asimismo, puede reescribir las dos instrucciones anteriores como una sola:  
  
```powershell
Get-SPRSServiceApplication -Name "Reporting Services Application" | Get-SPRSExtension -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml  
```  
  
###  <a name="get-and-set-properties-of-the-reporting-servicea-application-database-for-example-database-timeout"></a><a name="bkmk_example_db_properties"></a>Obtener y establecer propiedades de la base de datos de aplicación de Reporting Services, por ejemplo, tiempo de espera de base de datos  
 En el siguiente ejemplo, se obtiene, en primer lugar, una lista de las bases de datos y propiedades de forma que pueda determinar el GUID (identificador) de la base de datos que proporciona después al comando SET. Para obtener una lista completa de las propiedades, use `Get-SPRSDatabase | format-list`.  
  
```powershell
Get-SPRSDatabase | Select id, querytimeout,connectiontimeout, status, server, ServiceInstance
```  
  
 A continuación se muestra un ejemplo del resultado. Determine el identificador para la base de datos que desee modificar y use el identificador en el cmdlet SET.  
  
-   `Id                : 56f8d1bc-cb04-44cf-bd41-a873643c5a14`  
  
     `QueryTimeout      : 120`  
  
     `ConnectionTimeout : 15`  
  
     `Status            : Online`  
  
     `Server            : SPServer Name=uetestb01`  
  
     `ServiceInstance   : SPDatabaseServiceInstance`  
  
```powershell
Set-SPRSDatabase -Identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 -QueryTimeout 300  
```  
  
 Para comprobar que se ha establecido el valor, vuelva a ejecutar el cmdlet GET.  
  
```powershell
Get-SPRSDatabase -Identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 | Select id, querytimeout,connectiontimeout, status, server, ServiceInstance  
```  
  
###  <a name="list-reporting-services-data-extensions---sharepoint-mode"></a><a name="bkmk_example_list_data_extensions"></a>Enumerar extensiones de datos de Reporting Services-modo de SharePoint  
 El siguiente ejemplo recorre en bucle cada aplicación de servicio de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] y muestra las extensiones de datos actuales para cada una.  
  
```powershell
$apps = Get-SPRSServiceApplication  
foreach ($app in $apps)
{  
Write-host -ForegroundColor "yellow" Service App Name $app.Name  
Get-SPRSExtension -identity $app -ExtensionType "Data" | select name, extensiontype | Format-Table -AutoSize  
}  
```  
  
 **Ejemplo:**  
  
-   `Name           ExtensionType`  
  
     `----           -------------`  
  
     `SQL                     Data`  
  
     `SQLAZURE                Data`  
  
     `SQLPDW                  Data`  
  
     `OLEDB                   Data`  
  
     `OLEDB-MD                Data`  
  
     `ORACLE                  Data`  
  
     `ODBC                    Data`  
  
     `XML                     Data`  
  
     `SHAREPOINTLIST          Data`  
  
###  <a name="change-and-list-subscription-owners"></a><a name="bkmk_change_subscription_owner"></a>Cambiar y enumerar propietarios de suscripciones  
 Consulte [uso de PowerShell para cambiar y enumerar propietarios de suscripciones de Reporting Services y ejecutar una suscripción](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).  
  
## <a name="see-also"></a>Consulte también  
 [Usar PowerShell para cambiar y enumerar Reporting Services propietarios de suscripciones y ejecutar una suscripción](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md)   
 [Lista de comprobación: Use PowerShell para comprobar PowerPivot para SharePoint](https://docs.microsoft.com/analysis-services/instances/install-windows/checklist-use-powershell-to-verify-power-pivot-for-sharepoint)   
 [Scripts de PowerShell de Administración de SharePoint de CodePlex](https://sharepointpsscripts.codeplex.com/)   
