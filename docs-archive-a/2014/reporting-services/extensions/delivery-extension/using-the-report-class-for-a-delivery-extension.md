---
title: Usar la clase Report para una extensión de entrega | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], report information
- Report class
ms.assetid: 1145ac63-eafd-452a-82af-16f85b1676dd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a3f750c2383253636db255cbe9f1ce0ee676a9d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87678066"
---
# <a name="using-the-report-class-for-a-delivery-extension"></a>Usar la clase Report para una extensión de entrega
  La clase <xref:Microsoft.ReportingServices.Interfaces.Report> representa un informe en la base de datos del servidor de informes. Cada suscripción está asociada a un informe concreto. El informe está contenido en la notificación. La extensión de entrega puede utilizar el objeto <xref:Microsoft.ReportingServices.Interfaces.Report> que forma parte de la notificación para representar el informe. El objeto <xref:Microsoft.ReportingServices.Interfaces.Report> también contiene las propiedades específicas del informe, como la dirección URL para el informe en el servidor de informes y el nombre del informe. Todas estas propiedades se pueden utilizar como parte del proveedor de entrega.  
  
 El método <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> de la clase <xref:Microsoft.ReportingServices.Interfaces.Report> se puede utilizar para representar un informe. El método <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> devuelve una matriz de uno o más objetos <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> que comprenden un único informe representado. El primer objeto <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> es el informe representado. Cualquier otro objeto <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> son los recursos que se deben entregar junto con los datos del informe (por ejemplo, un archivo HTML e imágenes asociadas). Las extensiones de representación que son extensiones de un único flujo (IMAGE, PDF, MHTML y Excel) devuelven solo un objeto <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> en la matriz.  
  
 El objeto <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>, que contiene el flujo del informe, puede estar incluido como parte de una entrega.  
  
 Para ver un ejemplo de cómo utilizar la clase <xref:Microsoft.ReportingServices.Interfaces.Report>, vea [Muestras de productos de SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Consulte también  
 [Implementar una extensión de entrega](implementing-a-delivery-extension.md)   
 [Biblioteca de extensiones de Reporting Services](../reporting-services-extension-library.md)   
 [Uso de la clase RenderedOutputFile para una extensión de entrega](using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
  
  
