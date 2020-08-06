---
title: Generar aplicaciones mediante el servicio web y .NET Framework | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, application building
- .NET Framework [Reporting Services]
- XML Web service [Reporting Services], client creation
- reports [Reporting Services], building
- Web service [Reporting Services], application building
- Report Server Web service, client creation
- client configuration [Reporting Services]
- XML Web service [Reporting Services], application building
- Web service [Reporting Services], client creation
ms.assetid: 92a9678c-bc4f-4d7a-ba44-85989bfe27ca
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5f14a0f2d231d54d12129852b6226c02afd211d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745028"
---
# <a name="building-applications-using-the-web-service-and-the-net-framework"></a>Generar aplicaciones utilizando el servicio web y .NET Framework
  Con [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] , puede usar construcciones de programación familiares, como métodos, tipos primitivos y tipos complejos definidos por el usuario para trabajar con servicios Web. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] contiene una infraestructura y herramientas que puede utilizar para crear clientes de servicios web que pueden llamar a cualquier servicio web que cumpla los estándares del World Wide Web Consortium (W3C).  
  
 Un cliente del servicio web del servidor de informes es cualquier componente o aplicación que se comunica con un servidor de informes utilizando los mensajes del Protocolo simple de acceso a objetos (SOAP).  
  
 **Para crear un cliente del servicio web del servidor de informes mediante .NET Framework, siga estos pasos básicos:**  
  
1.  Cree una clase de proxy para el servicio web.  
  
     Para ello, agregue una clase de proxy o referencia web al proyecto de desarrollo, haga referencia a la clase de proxy en el código de cliente y cree una instancia de ese proxy. Para más información, vea [Creación del proxy del servicio web](creating-the-web-service-proxy.md).  
  
2.  Autentique al cliente de servicios web con el servidor de informes.  
  
     Para ello, establezca la propiedad <xref:System.Web.Services.Protocols.WebClientProtocol.Credentials%2A> del objeto de servicio igual a las credenciales de un usuario autenticado en el servidor de informes. Para más información, vea [Autenticación del servicio web](web-service-authentication.md).  
  
3.  Llame al método de la clase de proxy que corresponde a la operación del servicio web que desea invocar.  
  
     Para ello, llame a un método de servicio web y proporcione los argumentos necesarios. Para más información sobre los métodos de servicio web, vea [Métodos de servicio web del servidor de informes](../methods/report-server-web-service-methods.md). Para más información sobre las llamadas, vea [Llamadas a métodos de servicio web](calling-web-service-methods.md).  
  
## <a name="in-this-section"></a>En esta sección  
  
|Tema|Descripción|  
|-----------|-----------------|  
|[Creación del proxy del servicio web](creating-the-web-service-proxy.md)|Describe las maneras de agregar una clase de proxy al proyecto mediante [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] .|  
|[Autenticación de servicio Web](web-service-authentication.md)|Describe cómo se autentican las llamadas al servicio web del servidor de informes.|  
|[Llamar a métodos de servicio web](calling-web-service-methods.md)|Describe cómo utilizar la API SOAP para llamar a métodos de servicio Web en [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] .|  
|[Establecer la propiedad Url del servicio web](setting-the-url-property-of-the-web-service.md)|Explica cómo dirigir mediante programación el proxy del servicio web a una dirección URL de un servidor nuevo después de haber creado su referencia web.|  
|[Proporcionar argumentos de métodos de servicio web](supplying-web-service-method-arguments.md)|Describe cómo invocar un método de servicio web y proporcionar los argumentos del método.|  
|[Omitir valores para objetos de servicio web opcionales](omitting-values-for-optional-web-service-objects.md)|Describe cómo omitir los valores para los objetos de servicio web opcionales.|  
|[Usar métodos de servicio web seguros](using-secure-web-service-methods.md)|Describe el valor **SecureConnectionLevel** y la forma en la que afecta al uso de la API de SOAP de Reporting Services.|  
|[Pasar la configuración de información de dispositivo a las extensiones de representación](passing-device-information-settings-to-rendering-extensions.md)|Describe la configuración de la información de dispositivos que se utiliza para representar los informes en formatos diferentes.|  
|[Configuración de la extensión de entrega de Reporting Services](reporting-services-delivery-extension-settings.md)|Describe la configuración que se utiliza para entregar informes mediante el correo electrónico del servidor de informes.|  
|[Utilizar los encabezados SOAP de Reporting Services](../../report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)|Explica el uso de encabezados SOAP en [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Introducción a la administración de excepciones en Reporting Services](../../report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)|Proporciona información sobre la manera en la que [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] administra los errores.|  
  
## <a name="see-also"></a>Consulte también  
 [Servicio web del servidor de informes](../report-server-web-service.md)   
 [Referencia técnica &#40;SSRS&#41;](../../technical-reference-ssrs.md)  
  
  
