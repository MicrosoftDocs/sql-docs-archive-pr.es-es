---
title: Implementar una extensión de entrega | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: 4436ce48-397d-42c7-9b5d-2a267e2a1b2c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f4a4e33266c8d3a27ce2a4ab5f568bdee349720f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87678085"
---
# <a name="deploying-a-delivery-extension"></a>Implementar una extensión de entrega
  Las extensiones de entrega proporcionan su información de configuración en forma de archivo de configuración XML. El archivo XML cumple el esquema XML definido para las extensiones de entrega. Las extensiones de entrega proporcionan la infraestructura para establecer y modificar el archivo de configuración.  
  
 Si una extensión de entrega se reemplaza o actualiza, todas las suscripciones que hacen referencia a la misma siguen siendo válidas.  
  
 Una vez escrita y compilada la extensión de entrega de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] en una biblioteca de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], debe copiar la extensión en el directorio adecuado y agregar una entrada al archivo de configuración de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] correcto de modo que el servidor de informes pueda localizarla.  
  
## <a name="configuration-file-extension-element"></a>Elemento de extension de archivos de configuración  
 Las extensiones de entrega que implemente para el servidor de informes tienen que escribirse como elementos `Extension` en el archivo de configuración. El archivo de configuración para el servidor de informes es RSReportServer.config.  
  
 En la tabla siguiente se describen los atributos para el elemento `Extension` correspondiente a las extensiones de entrega.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Name`|Un nombre único para la extensión (por ejemplo, "Correo electrónico del servidor de informes", para la extensión de entrega por correo electrónico, o "Recurso compartido de archivos del servidor de informes", para la extensión de entrega en recursos compartidos de archivos). La longitud máxima para el atributo `Name` es de 255 caracteres. El nombre debe ser único entre todas las entradas en el elemento `Extension` del archivo de configuración. Si hay un nombre duplicado, el servidor de informes devuelve un error.|  
|`Type`|Lista separada por comas que incluye el espacio de nombres completo junto con el nombre del ensamblado.|  
|`Visible`|El valor `false` indica que la extensión de entrega no debería estar visible en las interfaces de usuario. Si el atributo no está incluido, el valor predeterminado es `true`.|  
  
 Para más información sobre el archivo RSReportServer.config, vea [Archivos de configuración de Reporting Services](../../report-server/reporting-services-configuration-files.md).  
  
## <a name="deploying-the-extension-to-the-report-server"></a>Implementar la extensión para el servidor de informes  
 El servidor de informes utiliza las extensiones de entrega para procesar y entregar notificaciones o informes. Debería implementar el ensamblado de extensión de entrega para el servidor de informes como un ensamblado privado. También tiene que realizar una entrada en el archivo de configuración del servidor de informes, RSReportServer.config.  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-a-report-server"></a>Para implementar un ensamblado de extensión de entrega en un servidor de informes  
  
1.  Copie el ensamblado desde la ubicación provisional al directorio bin del servidor de informes en el que desea utilizar la extensión de entrega. La ubicación predeterminada del directorio bin del servidor de informes es%ProgramFiles%\Microsoft SQL Server \ MSRS10_50. \<InstanceName> \Reporting Services\ReportServer\bin.  
  
    > [!IMPORTANT]  
    >  Si está intentando sobrescribir un ensamblado de extensión de entrega existente, primero debe detener el servicio del servidor de informes antes de copiar el ensamblado actualizado. Reinicie el servicio después de que el ensamblado termine la copia.  
  
2.  Una vez copiado el archivo de ensamblado, abra el archivo RSReportServer.config. El archivo de RSReportServer.config se encuentra en la carpeta% archivos de programa%\Microsoft SQL Server \ MSRS10_50. \<InstanceName> Directorio \Reporting Services\ReportServer Tiene que realizar una entrada en el archivo de configuración para el archivo de ensamblado de extensión de entrega. Puede abrir el archivo de configuración con [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] o con un editor de texto simple, como el Bloc de notas.  
  
3.  Busque el elemento `Delivery` en el archivo RSReportServer.config. En la ubicación siguiente se debería realizar una extensión de entrega creada recientemente:  
  
    ```  
    <Extensions>  
       <Delivery>  
          <Your extension configuration information goes here>  
       </Delivery>  
    </Extensions>  
    ```  
  
4.  Agregue una entrada para la extensión de entrega. La entrada debería incluir un elemento `Extension` con valores para `Name` y `Type`, y podría ser similar a la siguiente:  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryExtensionClass, AssemblyName" />  
    ```  
  
     El valor de `Name` es el nombre único de la extensión de entrega. El valor de `Type` es una lista separada por comas que incluye una entrada para el espacio de nombres completo de la clase que implementa la interfaz <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension>, seguido del nombre del ensamblado (sin incluir la extensión de archivo .dll). De forma predeterminada, las extensiones de entrega están visibles. Para ocultar una extensión de las interfaces de usuario, como el Administrador de informes, agregue un atributo `Visible` al elemento `Extension` y establézcalo en `false`.  
  
5.  Finalmente, agregue un grupo de código para el ensamblado personalizado que conceda el permiso  `FullTrust` para la extensión de entrega. Para ello, agregue el grupo de código al archivo rssrvpolicy.config que se encuentra de forma predeterminada en%ProgramFiles%\Microsoft SQL Server \ MSRS10_50. \<InstanceName> \Reporting Services\ReportServer. El grupo de código podría tener la apariencia siguiente:  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my delivery extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<InstanceName>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
     La pertenencia de dirección URL es solo una de las muchas condiciones de pertenencia que podría elegir para la extensión de entrega. Para más información sobre la seguridad de acceso del código de [!INCLUDE[ssRS](../../../includes/ssrs.md)], vea [Desarrollo seguro &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md).  
  
## <a name="deploying-the-extension-to-report-manager"></a>Implementar la extensión en el Administrador de informes  
 Si la extensión de entrega implementa la interfaz <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl>, se puede utilizar con la página de Suscripción del Administrador de informes. Si desea que la interfaz de usuario de la suscripción esté disponible, necesita implementar la extensión para el Administrador de informes.  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-report-manager"></a>Para implementar un ensamblado de extensión de entrega en el Administrador de informes  
  
1.  Copie el ensamblado desde la ubicación de almacenamiento provisional al directorio bin del Administrador de informes. La ubicación predeterminada del directorio Administrador de informes bin es%ProgramFiles%\Microsoft SQL Server \ MSRS10_50. \<InstanceName> \Reporting Services\ReportManager\bin.  
  
2.  Una vez copiado el archivo de ensamblado, abra el archivo RSReportServer.config. El archivo de RSReportServer.config se encuentra en la carpeta% archivos de programa%\Microsoft SQL Server \ MSRS10_50. \<InstanceName> Directorio \Reporting Services\ReportServer Tiene que realizar una entrada en el archivo de configuración para el archivo de ensamblado de extensión de entrega. Puede abrir el archivo de configuración con Visual Studio .NET o con un procesador de texto sencillo como el Bloc de notas.  
  
3.  Busque el elemento `DeliveryUI` en el archivo RSReportServer.config. En la ubicación siguiente se debería realizar una extensión de entrega creada recientemente:  
  
    ```  
    <Extensions>  
       <DeliveryUI>  
          <Your extension configuration information goes here>  
       </DeliveryUI>  
    </Extensions>  
    ```  
  
4.  Agregue una entrada para la extensión de entrega. La entrada debe incluir un `Extension` elemento con valores para `Name` y `Type` y podría ser similar al siguiente:  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryUIExtensionClass, AssemblyName" />  
    ```  
  
     El valor de `Name` es el nombre único de la extensión de entrega. El valor de `Type` es una lista separada por comas que incluye una entrada para el espacio de nombres completo de la clase que implementa la interfaz <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl>, seguido del nombre del ensamblado (sin incluir la extensión de archivo .dll).  
  
    > [!IMPORTANT]  
    >  El valor del atributo `Name` debe ser idéntico para el servidor de informes y para las entradas de los archivos de configuración del Administrador de informes. Si no son idénticos, la configuración del servidor no es válida.  
  
     Finalmente, agregue un grupo de código para el ensamblado personalizado que conceda el permiso  `FullTrust` para la extensión de entrega. Para ello, agregue el grupo de código al archivo RSmgrpolicy.config que se encuentra de forma predeterminada en C:\Archivos de Programa\microsoft SQL Server \ MSRS10_50. \<InstanceName> \Reporting Services\ReportManager. El grupo de código podría tener la apariencia siguiente:  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my delivery UI extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<InstanceName>\Reporting Services\ReportManager\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
     La pertenencia de dirección URL es solo una de las muchas condiciones de pertenencia que podría elegir para la extensión de entrega. Para obtener más información sobre la seguridad de acceso del código en [!INCLUDE[ssRS](../../../includes/ssrs.md)] , vea [&#40;de desarrollo seguro Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)  
  
## <a name="verifying-the-deployment"></a>Comprobación de la implementación  
 Puede comprobar si la extensión de entrega se implementó correctamente en el servidor de informes utilizando el método <xref:ReportService2010.ReportingService2010.ListExtensions%2A> del servicio web. También puede abrir el Administrador de informes y comprobar que la extensión está incluida en la lista de extensiones de entrega disponibles para una suscripción. Para obtener más información sobre Administrador de informes y suscripciones, consulte [suscripciones y entrega &#40;Reporting Services&#41;](../../subscriptions/subscriptions-and-delivery-reporting-services.md).  
  
## <a name="see-also"></a>Consulte también  
 [Implementar una extensión de entrega](implementing-a-delivery-extension.md)   
 [Biblioteca de extensiones de Reporting Services](../reporting-services-extension-library.md)  
  
  
