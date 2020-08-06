---
title: Puntos de conexión de servicios web del servidor de informes | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- management endpoints [Reporting Services]
- Web service [Reporting Services], endpoints
- endpoints [Reporting Services]
- execution endpoints [Reporting Services]
- Report Server Web service, endpoints
ms.assetid: f3f5d85f-9359-4508-bc5a-7f78a3cf7421
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 70281c5171eb37d9888d663542a7850820c81bea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746732"
---
# <a name="report-server-web-service-endpoints"></a>Extremos de servicios web del servidor de informes
  El servicio web del servidor de informes proporciona varios extremos para administrar un servidor de informes además de ejecutar los informes y navegar por ellos.  
  
## <a name="the-management-endpoints"></a>Extremos de administración  
 Hay tres extremos disponibles para administrar objetos en un servidor de informes: <xref:ReportService2005>, <xref:ReportService2006> y <xref:ReportService2010>. El extremo <xref:ReportService2005> se utiliza para administrar los objetos en un servidor de informes que esté configurado para el modo nativo. El extremo <xref:ReportService2006> se utiliza para administrar los objetos en un servidor de informes que esté configurado para el modo integrado de SharePoint. El punto de conexión <xref:ReportService2010> combina las funcionalidades de <xref:ReportService2005> y <xref:ReportService2006>, y puede administrar los objetos en un servidor de informes que esté configurado para el modo nativo o para el modo integrado de SharePoint.  
  
> [!IMPORTANT]  
>  Cuando un servidor de informes se configura para el modo integrado de SharePoint, las API <xref:ReportService2005> devuelven un error `rsOperationNotSupportedSharePointMode`. Si el servidor de informes se configura para el modo nativo, las API de <xref:ReportService2006> devolverán un error `rsOperationNotSupportedNativeMode`. De igual forma, cuando las API específicas del modo en <xref:ReportService2010> se utilizan en modos imprevistos, las API devolverán los errores respectivos.  
  
> [!NOTE]  
>  Los tipos de datos <xref:ReportService2005> y <xref:ReportService2006> están desusados en [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]. El extremo <xref:ReportService2010> incluye las funcionalidades de ambos extremos y contiene características de administración adicionales.  
  
 Si el servidor de informes está configurado para el modo nativo o para el modo integrado de SharePoint, se puede tener acceso al WSDL para el extremo de administración utilizando una de las direcciones URL siguientes:  
  
```  
http://<Server Name>/ReportServer/ReportService2010.asmx?wsdl  
```  
  
 Para más información, vea [Acceso a la API de SOAP](../accessing-the-soap-api.md).  
  
## <a name="the-execution-endpoint"></a>Extremo de ejecución  
 El extremo <xref:ReportExecution2005> facilita a los programadores la personalización del procesamiento y la representación de los informes desde un servidor de informes tanto en modo nativo como en modo integrado de SharePoint. El extremo incluye las clases y métodos que existían en las versiones anteriores del servicio web del servidor de informes. Además, se han agregado muchas clases y métodos nuevos al servicio web del servidor de informes que se exponen a través del extremo de ejecución.  
  
 Se puede tener acceso al WSDL para el extremo de administración utilizando la dirección URL siguiente:  
  
```  
http://<Server Name>/ReportServer/ReportExecution2005.asmx?wsdl  
```  
  
 Si el servidor de informes está configurado para el modo integrado de SharePoint, se puede tener acceso al WSDL utilizando la dirección URL siguiente:  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportExecution2005.asmx?wsdl  
```  
  
 Para más información, vea [Acceso a la API de SOAP](../accessing-the-soap-api.md).  
  
## <a name="sharepoint-proxy-endpoints"></a>Extremos proxy de SharePoint  
 Cuando un servidor de informes se configura para el modo integrado de SharePoint y se ha instalado el Complemento de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], un conjunto de extremos proxy se instala en el servidor de SharePoint. Los extremos proxy constituyen la API principal para desarrollar soluciones de informe cuando un servidor de informes se configura en el modo integrado de SharePoint. Al desarrollar con los extremos del proxy, el Complemento de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] administra el intercambio de las credenciales entre el servidor de SharePoint y el servidor de informes en el modo de autenticación de cuentas de confianza. Al desarrollar con los extremos del servidor de informes, la aplicación que realiza la llamada tendrá que administrar el intercambio de credenciales en el modo de autenticación de cuentas de confianza. En la tabla siguiente se enumeran los extremos que se instalan con el Complemento de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
|Extremo proxy|Descripción|  
|--------------------|-----------------|  
|<xref:ReportService2006>|Proporciona las API para administrar un servidor de informes que se configura para el modo integrado de SharePoint. **Nota:**  Este punto de conexión está en desuso en [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] .|  
|<xref:ReportService2010>|Proporciona las API para administrar un servidor de informes que se configura para el modo nativo o para el modo integrado de SharePoint.|  
|<xref:ReportExecution2005>|Proporciona las API para ejecutar los informes y navegar por ellos.|  
|<xref:ReportServiceAuthentication>|Proporciona las API para autenticar a los usuarios con un servidor de informes cuando la aplicación web de SharePoint se configura para la autenticación de formularios.|  
  
 Las siguientes son direcciones URL de ejemplo para hacer referencia a los extremos proxy en un sitio de SharePoint.  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportService2010.asmx  
```  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportExecution2005.asmx  
```  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportServiceAuthentication.asmx  
```  
  
## <a name="see-also"></a>Consulte también  
 [Creación de aplicaciones con el servicio web y .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
