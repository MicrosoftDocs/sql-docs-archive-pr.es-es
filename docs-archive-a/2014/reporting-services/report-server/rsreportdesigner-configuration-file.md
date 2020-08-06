---
title: Archivo de configuración RSReportDesigner | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Designer [Reporting Services], configuration file
- RSReportDesigner configuration file
ms.assetid: fdcc9c58-3bad-45b3-ba8e-c7816d64f14c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 563c5ea602eef3af2400057f3da41a5850a31cec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673480"
---
# <a name="rsreportdesigner-configuration-file"></a>archivo de configuración RSReportDesigner
  En el archivo RSReportDesigner.config se almacenan las configuraciones de las extensiones de representación y procesamiento de datos disponibles para el Diseñador de informes. La información de la extensión de procesamiento de datos se almacena en el elemento `Data`. La información de la extensión de representación se almacena en el elemento `Render`. El elemento `Designer` enumera los generadores de consultas que se utilizan en el Diseñador de informes.  
  
 El Diseñador de informes utiliza funcionalidad incrustada del servidor de informes para obtener una vista previa de los informes. La configuración relacionada con el servidor puede especificarse para admitir el procesamiento en el servidor local de las operaciones de vista previa. Para obtener más información sobre las opciones de configuración del servidor de informes, vea [RSReportServer Configuration File](rsreportserver-config-configuration-file.md).  
  
## <a name="file-location"></a>Ubicación del archivo  
 Este archivo se encuentra en \Archivos de programa\Microsoft Visual Studio 8\Common7\IDE\PrivateAssemblies.  
  
## <a name="editing-guidelines"></a>Directrices para editar  
 No modifique la configuración de este archivo, a no ser que vaya a implementar o a quitar una extensión personalizada, a deshabilitar el almacenamiento en caché durante la vista previa o a registrar una nueva extensión de procesamiento de datos después de una actualización de Service Pack.  
  
 Las instrucciones concretas para editar archivos de configuración están disponibles cuando se está personalizando la configuración de la extensión de representación. Para más información, vea [Personalizar los parámetros de extensión de representación en RSReportServer.Config](../customize-rendering-extension-parameters-in-rsreportserver-config.md).  
  
 Para obtener instrucciones generales sobre cómo editar archivos de configuración, vea [Modificar un archivo de configuración de Reporting Services &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md).  
  
## <a name="example-configuration-file"></a>Archivo de configuración de ejemplo  
 El siguiente ejemplo muestra el formato del archivo RSReportDesigner.config.  
  
```  
<Configuration>  
  <Add Key="SecureConnectionLevel" Value="0" />  
  <Add Key="InstanceName" Value="Microsoft.ReportingServices.PreviewServer" />  
  <Add Key="SessionCookies" Value="true" />  
  <Add Key="SessionTimeoutMinutes" Value="3" />  
  <Add Key="PolicyLevel" Value="rspreviewpolicy.config" />  
  <Add Key="CacheDataForPreview" Value="true" />  
  <Extensions>  
    <Render> . . . </Render>  
    <Data> . . . </Data>  
    <Designer> . . . </Designer>  
```  
  
## <a name="configuration-settings"></a>Valores de configuración  
  
|Configuración|Descripción|  
|-------------|-----------------|  
|`SecureConnectionLevel`|Especifica el grado de seguridad de la conexión al servicio web. El intervalo de valores válidos es de 0 a 3, donde 0 es el menos seguro. Para más información, consulte [Using Secure Web Service Methods](../report-server-web-service/net-framework/using-secure-web-service-methods.md).|  
|`InstanceName`|Identificador del servidor de vista previa. No modifique este valor.|  
|`SessionCookies`|Especifica si el servidor de informes utiliza cookies del explorador para mantener información de la sesión. Entre los valores válidos se incluyen `true` y `false`. El valor predeterminado es `true`. Si este valor se establece en false, los datos de la sesión se almacenan en la base de datos **reportservertempdb** .|  
|`SessionTimeoutMinutes`|Especifica el período durante el cual una cookie de sesión es válida. El valor predeterminado es 3 minutos.|  
|`PolicyLevel`|Especifica el archivo de configuración de la directiva de seguridad. El valor válido es Rspreviewpolicy.config. Para obtener más información, consulte [uso de archivos de directiva de seguridad de Reporting Services](../extensions/secure-development/using-reporting-services-security-policy-files.md).|  
|`CacheDataForPreview`|Cuando se establece en `True`, el Diseñador de informes almacena los datos en un archivo caché en el equipo local. Los valores válidos son `True` (predeterminado) y `False`. Para más información, consulte [Previewing Reports](../reports/previewing-reports.md).|  
|`Render`|Enumera las extensiones de representación que están disponibles en el Diseñador de informes para obtener vistas previas. Las extensiones de representación que se utilicen para la vista previa deberían ser idénticas a las instaladas con el servidor de informes.<br /><br /> `Name` especifica la extensión de representación. Si va a invocar una extensión de representación mediante código, utilice este valor para llamar una extensión específica.<br /><br /> `Type` especifica el nombre completo de clase de la extensión, junto con el nombre de la biblioteca, separados por comas.<br /><br /> `Visible` especifica si el nombre aparece en una interfaz de usuario. Este valor puede ser `True` (predeterminado) o `False`. Si es `True`, aparece en las interfaces de usuario.|  
|`Data`|Enumera las extensiones de procesamiento de datos que están disponibles en el Diseñador de informes para conectarse a orígenes de datos que proporcionan información a los informes. Las extensiones de procesamiento de datos utilizadas en el Diseñador de informes pueden ser idénticas a las instaladas con el servidor de informes. Si agrega o quita extensiones personalizadas, vea [Deploying a Data Processing Extension](../extensions/data-processing/deploying-a-data-processing-extension.md).<br /><br /> `Name` especifica la extensión de procesamiento de datos.<br /><br /> `Type` especifica el nombre completo de clase de la extensión, junto con el nombre de la biblioteca, separados por comas.|  
|`Designer`|Enumera los generadores de consultas que están disponibles para el Diseñador de informes. Los generadores de consultas proporcionan una interfaz de usuario para crear consultas que recuperan los datos utilizados en los informes. Los generadores de consultas pueden variar entre las diferentes extensiones de procesamiento de datos. De forma predeterminada, Reporting Services proporciona una interfaz de usuario de herramienta de datos visual para todas las extensiones de procesamiento de datos que se incluyen en el producto. Sin embargo, si genera o utiliza extensiones de procesamiento de datos de otros fabricantes, es posible que se apliquen otras interfaces de generador de consultas.|  
|`PreviewProcessingServiceStartupTimeoutSeconds`|Especifica el período que el servicio de procesamiento de vista previa debe esperar para iniciarse antes de mostrar un mensaje de error. El valor predeterminado es 15 segundos.|  
  
## <a name="see-also"></a>Consulte también  
 [Archivos de configuración de Reporting Services](reporting-services-configuration-files.md)   
 [Herramientas de diseño de consultas en Diseñador de informes SQL Server Data Tools &#40;SSRS&#41;](../report-data/query-design-tools-ssrs.md)  
  
  
