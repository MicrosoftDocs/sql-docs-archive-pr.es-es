---
title: Usar la propiedad Detail para administrar errores concretos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], Detail property
- Detail property
- InnerText property
ms.assetid: 4392633d-b46b-41e6-bc12-efb64e166704
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4f8ac62dc381d8f665a44fc0897ba1f4215aa8e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87747458"
---
# <a name="using-the-detail-property-to-handle-specific-errors"></a>Usar la propiedad Detail para administrar errores concretos
  Para clasificar más las excepciones, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] devuelve información de error adicional en la propiedad **InnerText** de los elementos secundarios en la propiedad **Detail** de la excepción SOAP. Dado que la propiedad **Detail** es un objeto **XmlNode**, puede tener acceso al texto interno del elemento secundario **Message** utilizando el código siguiente.  
  
 Para obtener una lista de todos los elementos secundarios disponibles contenidos en la propiedad **Detail**, vea [Propiedad Detail](../soapexception-class/detail-property.md). Para obtener más información, vea "propiedad detail" en la [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] documentación del SDK.  
  
```vb  
Try  
' Code for accessing the report server  
Catch ex As SoapException  
   ' The exception is a SOAP exception, so use  
   ' the Detail property's Message element.  
   Console.WriteLine(ex.Detail("Message").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   // Code for accessing the report server  
}  
catch (SoapException ex)  
{  
   // The exception is a SOAP exception, so use  
   // the Detail property's Message element.  
   Console.WriteLine(ex.Detail["Message"].InnerXml);  
}  
```  
  
```vb  
Try  
' Code for accessing the report server  
Catch ex As SoapException  
   If ex.Detail("ErrorCode").InnerXml = "rsInvalidItemName" Then  
   End If ' Perform an action based on the specific error code  
End Try  
```  
  
```csharp  
try  
{  
   // Code for accessing the report server  
}  
catch (SoapException ex)  
{  
   if (ex.Detail["ErrorCode"].InnerXml == "rsInvalidItemName")  
   {  
      // Perform an action based on the specific error code  
   }  
}  
```  
  
 La línea de código siguiente escribe el código de error concreto que se va a devolver en la excepción SOAP para la consola. Podría evaluar también el código de error y realizar acciones específicas.  
  
```vb  
Console.WriteLine(ex.Detail("ErrorCode").InnerXml)  
```  
  
```csharp  
Console.WriteLine(ex.Detail["ErrorCode"].InnerXml);  
```  
  
## <a name="see-also"></a>Consulte también  
 [Introducción al control de excepciones en Reporting Services](../introducing-exception-handling-in-reporting-services.md)   
 [Reporting Services (clase SoapException)](../soapexception-class/reporting-services-soapexception-class.md)   
 [Tabla de errores de SoapException](../soapexception-class/soapexception-errors-table.md)  
  
  
