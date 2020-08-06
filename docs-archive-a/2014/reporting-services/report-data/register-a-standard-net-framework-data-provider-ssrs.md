---
title: Registrar un proveedor de datos estándar de .NET Framework (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], data
- .NET Framework data providers for Reporting Services
- data processing extensions [Reporting Services]
- data providers [Reporting Services]
- data retrieval [Reporting Services]
- Reporting Services, data sources
ms.assetid: d92add64-e93c-4598-8508-55d1bc46acf6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5fd26f9c7fa163d9e6005d42e24c7b1483987f3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744504"
---
# <a name="register-a-standard-net-framework-data-provider-ssrs"></a>Registrar un proveedor de datos estándar de .NET Framework (SSRS)
  Para usar un proveedor de datos de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] de terceros para recuperar datos de un conjunto de datos de informe de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , es necesario implementar y registrar el ensamblado del proveedor de datos de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] en dos ubicaciones: en el cliente de creación de informes y en el servidor de informes. En el cliente de creación de informes, debe registrar el proveedor de datos como un tipo de origen de datos y asociarlo a un diseñador de consultas. A continuación, puede seleccionar este proveedor de datos como un tipo de origen de datos al crear un conjunto de datos de informe. El diseñador de consultas asociado se abre para ayudarle a crear consultas para este tipo de origen de datos. En el servidor de informes, debe registrar el proveedor de datos como un tipo de origen de datos. A continuación, puede procesar los informes publicados que recuperan datos de un origen de datos con este proveedor de datos.  
  
 Los proveedores de datos de terceros no proporcionan necesariamente todas las funciones disponibles con las extensiones de procesamiento de datos de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Para más información, vea [Orígenes de datos admitidos por Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md). Para obtener más información acerca de cómo ampliar la funcionalidad de un proveedor de datos de .[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] , vea [Implementación de una extensión de procesamiento de datos](../extensions/data-processing/implementing-a-data-processing-extension.md).  
  
 Necesita credenciales de administrador para instalar y registrar proveedores de datos.  
  
## <a name="registering-a-net-framework-data-provider-on-the-report-server"></a>Registrar un proveedor de datos de .NET Framework en el servidor de informes  
 Para procesar los informes publicados que usan este proveedor de datos de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] en el servidor de informes, debe instalar el ensamblado en el servidor de informes. Debe modificar dos archivos de configuración. Modifique rsreportserver.config para registrar el proveedor de datos. Modifique rssrvpolicy.config para conceder permisos de seguridad de acceso del código para el ensamblado.  
  
#### <a name="to-install-a-data-provider-assembly-on-the-report-server"></a>Para instalar un ensamblado del proveedor de datos en el servidor de informes  
  
1.  Navegue hasta la ubicación predeterminada del directorio bin del servidor de informes donde desea usar el proveedor de datos de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] . La ubicación predeterminada del directorio bin del servidor de informes es *\<drive>* : \Archivos de programa\microsoft SQL Server \ MSRS10_50. MSSQLSERVER\Reporting Services\ReportServer\bin.  
  
2.  Copie el ensamblado desde la ubicación de almacenamiento provisional en el directorio bin del servidor de informes. Otra opción es cargar el ensamblado en la caché de ensamblados global (GAC). Para obtener más información, vea [Trabajar con ensamblados y la Caché de ensamblados global](https://go.microsoft.com/fwlink/?linkid=63912) en la documentación del SDK de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] en MSDN.  
  
#### <a name="to-register-a-net-data-provider-on-the-report-server"></a>Para registrar un proveedor de datos de .NET en el servidor de informes  
  
1.  Haga una copia de seguridad del archivo RSReportServer.config en el directorio principal ReportServer para bin.  
  
2.  Abra RSReportServer.config. Puede abrir el archivo de configuración con [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] o con un editor de texto simple como el Bloc de notas.  
  
3.  Busque el elemento `Data` en el archivo RSReportServer.config. Se debe crear una entrada para el proveedor de datos de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] en la siguiente ubicación:  
  
    ```  
    <Extensions>  
       <Data>  
          <Extension Your data provider configuration information goes here />  
       </Data>  
    </Extensions>  
    ```  
  
4.  Agregue una entrada para el proveedor de datos de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] .  
  
    |Atributo|Descripción|  
    |---------------|-----------------|  
    |`Name`|Proporcione un nombre único para el proveedor de datos (por ejemplo, **miProveedorDeDatosDeNET**). La longitud máxima para el atributo `Name` es de 255 caracteres. El nombre debe ser único entre todas las entradas en el elemento `Extension` del archivo de configuración. El valor incluido aquí aparece en la lista desplegable de tipos de orígenes de datos al crear un origen de datos.|  
    |`Type`|Escriba una lista separada por comas donde se incluya el espacio de nombres completo de la clase que implementa la interfaz <xref:System.Data.IDbConnection> , seguido del nombre del ensamblado del proveedor de datos de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] (sin incluir la extensión de nombre de archivo .dll).|  
  
     Por ejemplo, la entrada puede ser similar a la siguiente para una DLL implementada en el directorio bin del servidor de informes:  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly" />   
    ```  
  
     Si carga el ensamblado en la caché de ensamblados global (GAC), debe proporcionar las propiedades de nombre seguro. Por ejemplo:  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly,Version=1.0.0.0, Culture=neutral, PublicKeyToken=MyPublicToken"/>  
    ```  
  
#### <a name="to-set-the-code-group-policy-for-a-net-data-provider"></a>Para establecer la directiva de grupo de código para un proveedor de datos de .NET  
  
1.  Haga una copia de seguridad del archivo rssrvpolicy.config en el directorio principal ReportServer para bin.  
  
2.  Abra rssrvpolicy.config. Puede abrir el archivo de configuración con [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] o con un editor de texto simple como el Bloc de notas.  
  
3.  Busque el elemento `CodeGroup` en el archivo rssrvpolicy.config.  
  
4.  Agregue un grupo de códigos para el ensamblado del proveedor de datos que concede el permiso `FullTrust`. El grupo de códigos puede ser similar al siguiente:  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="ThisDataProviderCodeGroup"  
       Description="Code group for the .NET data provider">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url=  
    "C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\DataProviderAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 La pertenencia de dirección URL es solo una de las muchas condiciones de pertenencia que puede seleccionar para el proveedor de datos.  
  
### <a name="verifying-the-deployment-and-registration"></a>Comprobar la implementación y el registro  
 Puede comprobar si el proveedor de datos se implementó correctamente para el servidor de informes si abre el Administrador de informes y comprueba si el proveedor de datos está incluido en la lista de orígenes de datos disponibles. Para más información sobre el Administrador de informes y los orígenes de datos, vea [Crear, modificar y eliminar orígenes de datos compartidos &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md).  
  
## <a name="registering-a-net-framework-data-provider-on-the-report-designer-client"></a>Registrar un proveedor de datos de .NET Framework en el cliente del Diseñador de informes  
 Para crear informes que usen este proveedor de datos de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] para un origen de datos, debe instalar el ensamblado en el equipo cliente que ejecuta el Diseñador de informes. Debe modificar dos archivos de configuración. Modifique RSReportDesigner.config para registrar el proveedor de datos como un origen de datos y para usar el diseñador de consultas genérico. Modifique RSPreviewPolicy.config para conceder permisos de seguridad de acceso del código para el ensamblado del proveedor de datos.  
  
#### <a name="to-install-a-data-provider-assembly-on-the-report-designer-client"></a>Para instalar un ensamblado del proveedor de datos en el cliente del Diseñador de informes  
  
1.  Navegue hasta la ubicación predeterminada del directorio PrivateAssemblies del cliente del Diseñador de informes donde desea usar el proveedor de datos de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] . La ubicación predeterminada del directorio PrivateAssemblies es *\<drive>* : \Archivos de Programa\microsoft Visual Studio 9.0 \ Common7\IDE\PrivateAssemblies.  
  
2.  Copie el ensamblado desde la ubicación de almacenamiento provisional en el directorio PrivateAssemblies del cliente del Diseñador de informes. Otra opción es cargar el ensamblado en la caché de ensamblados global (GAC). Para obtener más información, vea [Trabajar con ensamblados y la Caché de ensamblados global](https://go.microsoft.com/fwlink/?linkid=63912) en la documentación del SDK de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] en MSDN.  
  
#### <a name="to-register-a-net-data-provider-on-the-report-designer-client"></a>Para registrar un proveedor de datos de .NET en el cliente del Diseñador de informes  
  
1.  Haga una copia de seguridad del archivo RSReportDesigner.config en el directorio PrivateAssemblies.  
  
2.  Abra RSReportDesigner.config con [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] o con un editor de texto simple como el Bloc de notas.  
  
3.  Busque el elemento `Data` en el archivo RSReportDesigner.config. Se debe crear una entrada para el proveedor de datos en la siguiente ubicación:  
  
    ```  
    <Extensions>  
       <Data>  
          <Extension Your data provider configuration information goes here />  
       </Data>  
    </Extensions>  
    ```  
  
4.  Agregue una entrada para el proveedor de datos.  
  
    |Atributo|Descripción|  
    |---------------|-----------------|  
    |`Name`|Proporcione un nombre único para el proveedor de datos (por ejemplo, **miProveedorDeDatosDeNET**). La longitud máxima para el atributo `Name` es de 255 caracteres. El nombre debe ser único entre todas las entradas en el elemento `Extension` del archivo de configuración. El valor incluido aquí aparece en la lista desplegable de tipos de orígenes de datos al crear un origen de datos nuevo.|  
    |`Type`|Escriba una lista separada por comas donde se incluya el espacio de nombres completo de la clase que implementa la interfaz <xref:System.Data.IDbConnection> , seguido del nombre del ensamblado del proveedor de datos de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] (sin incluir la extensión de nombre de archivo .dll).|  
  
     Por ejemplo, la entrada puede ser similar a la siguiente para una DLL implementada en el directorio PrivateAssemblies de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] :  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly" />   
    ```  
  
     Si carga el ensamblado en la GAC, debe proporcionar las propiedades de nombre seguro. Por ejemplo:  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly, Version=1.0.0.0, Culture=neutral, PublicKeyToken=MyPublicToken"/>  
    ```  
  
5.  Busque el elemento `Designer` en el archivo RSReportDesigner.config. Se debe crear una entrada para el proveedor de datos de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] en la siguiente ubicación:  
  
    ```  
    <Extensions>  
       <Designer>  
          <Your data provider configuration information goes here>  
       </Designer>  
    </Extensions>  
    ```  
  
6.  Agregue la siguiente entrada al archivo RSReportDesigner.config en el elemento `Designer`. Debe reemplazar solamente el atributo `Name` por el nombre proporcionado en las entradas anteriores.  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="Microsoft.ReportingServices.QueryDesigners.GenericQueryDesigner,Microsoft.ReportingServices.QueryDesigners"/>  
    ```  
  
#### <a name="to-set-the-code-group-policy-for-a-net-data-provider-on-the-report-designer-client"></a>Para establecer la directiva de grupo de código para un proveedor de datos de .NET en el cliente del Diseñador de informes  
  
1.  Haga una copia de seguridad del archivo RSPreviewPolicy.config en el directorio PrivateAssemblies.  
  
2.  Abra RSPreviewPolicy.config con [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] o un editor de texto simple como el Bloc de notas.  
  
3.  Busque el elemento `CodeGroup` en el archivo RSPreviewPolicy.config.  
  
4.  Agregue un grupo de códigos para el ensamblado del proveedor de datos de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] que concede el permiso `FullTrust`. El grupo de códigos puede ser similar al siguiente:  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="ThisDataProviderCodeGroup"  
       Description="Code group for the .NET data provider">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url=  
    " C:\Program Files\Microsoft Visual Studio 9\Common7\IDE\PrivateAssemblies\DataProviderAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 La pertenencia de dirección URL es solo una de las muchas condiciones de pertenencia que puede seleccionar para el proveedor de datos.  
  
### <a name="verifying-the-deployment-and-registration-on-the-report-designer-client"></a>Comprobar la implementación y el registro en el cliente del Diseñador de informes  
 Para poder comprobar la implementación, debe cerrar todas las instancias de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] en el equipo local. Una vez que haya finalizado todas las sesiones actuales, puede comprobar si el proveedor de datos se implementó correctamente para el Diseñador de informes si crea un proyecto de informe nuevo en [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. El proveedor de datos se debe incluir en la lista de tipos de orígenes de datos disponibles al crear un conjunto de datos nuevo para el informe.  
  
## <a name="platform-considerations"></a>Consideraciones sobre las plataformas  
 En una plataforma de 64 bits (x64), [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] se ejecuta en el modo WOW de 32 bits. Si crea informes en una plataforma x64, necesita tener proveedores de datos de 32 bits instalados en el cliente de creación de informes para obtener vistas previas de los informes. Si publica el informe en el mismo sistema, necesita proveedores de datos x64 para ver el informe con el Administrador de informes.  
  
 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] no se admite para las plataformas basadas en [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)].  
  
 Las extensiones de procesamiento de datos instaladas con [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] se deben compilar de forma nativa para cada plataforma e instalar en las ubicaciones correctas. Si registra un proveedor de datos personalizado o un proveedor de datos estándar de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] , se debe compilar de forma nativa para la plataforma adecuada e instalar en las ubicaciones correctas. Si usa una plataforma de 32 bits, el proveedor de datos se debe compilar para una plataforma de 32 bits. Si usa una plataforma de 64 bits, el proveedor de datos se debe compilar para una plataforma de 64 bits. No puede usar un proveedor de datos de 32 bits incluido con interfaces de 64 bits en una plataforma de 64 bits. Compruebe el software de terceros para obtener información acerca de si el proveedor de datos funcionará en la plataforma instalada. Para más información sobre proveedores de datos y la compatibilidad con plataformas, vea [Orígenes de datos admitidos por Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md).  
  
## <a name="see-also"></a>Consulte también  
 [Configurar y administrar un servidor de informes &#40;modo nativo de SSRS&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)   
 [Implementar una extensión de procesamiento de datos](../extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Archivos de configuración de Reporting Services](../report-server/reporting-services-configuration-files.md)   
 [Seguridad de acceso del código en Reporting Services](../extensions/secure-development/code-access-security-in-reporting-services.md)  
  
  
