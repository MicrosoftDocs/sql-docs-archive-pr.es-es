---
title: Extensiones
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.prod_service: reporting-services-native, reporting-services-sharepoint
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: 68e81b3554ed3a77e950d5da2a25cc0510322f77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87671946"
---
# <a name="extensions-for-sql-server-reporting-services-ssrs"></a>Extensiones para SQL Server Reporting Services (SSRS)

  El servidor de informes de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] usa extensiones para modular los tipos de entrada y salida que acepta para la autenticación, el proceso de datos, la representación de informes y la entrega de informes. Esto hace que sea más fácil que las instalaciones existentes de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] utilicen los nuevos estándares de software del sector, como un esquema de autenticación o un tipo de origen de datos personalizado. El servidor de informes admite extensiones de autenticación personalizadas, extensiones de procesamiento de datos, extensiones de procesamiento de informes, extensiones de representación y extensiones de entrega, y las extensiones disponibles para los usuarios se pueden configurar en el archivo de configuración RSReportServer.config. Por ejemplo, puede limitar los formatos de exportación que el visor de informes puede usar. Un servidor de informes requiere al menos una extensión de autenticación, una extensión de procesamiento de datos y una extensión de representación. Las extensiones de procesamiento de informes y de entrega son opcionales, pero necesarias si desea admitir controles personalizados o de distribución de informes.  
  
 En este tema se describen las extensiones que están inmediatamente disponibles en [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
## <a name="security-extensions"></a>Extensiones de seguridad

 Las extensiones de seguridad se usan para autenticar y autorizar a los usuarios y los grupos para un servidor de informes. La extensión de seguridad predeterminada se basa en la autenticación de Windows. También puede crearse una extensión de seguridad personalizada para reemplazar la seguridad predeterminada si el modelo de implementación requiere un enfoque de autenticación diferente (por ejemplo, si se requiere una autenticación basada en formularios para la implementación de Internet o extranet). Solo puede utilizarse una extensión de seguridad en una única instalación de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Es posible reemplazar la extensión de seguridad de la autenticación de Windows predeterminada, pero no puede utilizarse junto con una extensión de seguridad personalizada.  
  
## <a name="data-processing-extensions"></a>Extensiones de procesamiento de datos

 Las extensiones de procesamiento de datos se usan para consultar un origen de datos y devolver un conjunto de filas planas. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] usa las diferentes extensiones para interactuar con distintos tipos de orígenes de datos. Puede utilizar las extensiones que se incluyen en [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]o desarrollar sus propias extensiones. Se proporcionan extensiones de procesamiento de datos para los orígenes datos [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], Oracle, [!INCLUDE[SAP_DPE_BW_1](../includes/sap-dpe-bw-1-md.md)], Hyperion Essbase, Teradata, OLE DB y ODBC. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] también puede usar cualquier proveedor de datos [!INCLUDE[vstecado](../includes/vstecado-md.md)] . Las extensiones de procesamiento de datos procesan las solicitudes de consulta del componente del procesador de informes por medio de las siguientes tareas:  
  
- Abrir una conexión con un origen de datos.  
  
- Analizar una consulta y devolver una lista de nombres de campo.  
  
- Ejecutar una consulta en el origen de datos y devolver un conjunto de filas.  
  
- Pasar parámetros a una consulta, si es necesario.  
  
- Establecer una iteración en el conjunto de filas y recuperar datos.  
  
Algunas extensiones también pueden realizar las siguientes tareas:  
  
- Analizar una consulta y devolver una lista de los nombres de parámetro utilizados en la consulta.  
  
- Analizar una consulta y devolver la lista de campos utilizados para la agrupación.  
  
- Analizar una consulta y devolver la lista de campos utilizados para la ordenación.  
  
- Proporcionar un nombre de usuario y una contraseña para conectar con el origen de datos.  
  
- Pasar parámetros con varios valores a una consulta.  
  
- Establecer iteraciones en las filas y recuperar metadatos auxiliares.  
  
## <a name="rendering-extensions"></a>Extensiones de representación

 Las extensiones de representación transforman los datos y la información de diseño del procesador de informes en un formato específico del dispositivo. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] incluye siete extensiones de representación: HTML, Excel, CSV, XML, Image, PDF y [!INCLUDE[msCoName](../includes/msconame-md.md)] Word.  
  
- **Extensión de representación en HTML** Cuando se solicita un informe del servidor de informes a través de un explorador web, el servidor de informes utiliza la extensión de representación en HTML para representar el informe. La extensión de representación en HTML genera todo el lenguaje HTML mediante codificación UTF-8. Para obtener más información, vea [representar en HTML &#40;generador de informes y SSRS&#41;](report-builder/rendering-to-html-report-builder-and-ssrs.md) y [planear la compatibilidad del explorador Reporting Services y Power View ](../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md)&#40;Reporting Services 2014&#41;.  
  
- **Extensión de representación en Excel** La extensión de representación en Excel representa informes que pueden verse y modificarse en [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 97 o posterior. Esta extensión de representación crea archivos BIFF (Formato de archivo de intercambio binario). BIFF es el formato de archivo nativo para datos de Excel. Los informes que se representan en [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] admiten todas las características disponibles para una hoja de cálculo. Para obtener más información, vea [Exportar a Microsoft Excel &#40;Generador de informes y SSRS&#41;](report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md).  
  
- **Extensión de representación en CSV** La extensión de representación en CSV (valores separados por comas) representa informes como archivos de texto simple delimitados por comas. Los usuarios pueden abrir estos archivos en una aplicación de hoja de cálculo, como [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)], o en cualquier otro programa que pueda leer archivos de texto. Para obtener más información, vea [Exportar a Microsoft Excel &#40;Generador de informes y SSRS&#41;](report-builder/exporting-to-a-csv-file-report-builder-and-ssrs.md).  
  
- **Extensión de representación en XML** La extensión de representación en XML representa informes en archivos XML. Otros programas pueden almacenar o leer estos archivos XML. También se puede utilizar una transformación XSLT para convertir el informe en otro esquema XML y poder utilizarlo con otra aplicación. El lenguaje XML que genera la extensión de representación en XML tiene la codificación UTF-8. Para obtener más información, vea [Exportar a Microsoft Excel &#40;Generador de informes y SSRS&#41;](report-builder/exporting-to-xml-report-builder-and-ssrs.md).  
  
-   **Extensión de representación en imágenes** La extensión de representación en imágenes representa informes en mapas de bits o metarchivos. Esta extensión puede representar los informes en los formatos siguientes: BMP, EMF, GIF, JPEG, PNG, TIFF y WMF. De forma predeterminada, la imagen se representa en formato TIFF, que se puede mostrar en el visor de imágenes predeterminado del sistema operativo (por ejemplo, Visor de imágenes y fax de Windows). Desde el visor, puede enviar la imagen a una impresora. Al usar la extensión de representación en imágenes para representar informes se asegura de que el informe tenga la misma apariencia en todos los clientes. Si un usuario ve un informe en HTML, su apariencia puede variar dependiendo de la versión del explorador de la que disponga el usuario, la configuración del explorador y las fuentes disponibles. La extensión de representación de imágenes representa el informe en el servidor, de forma que todos los usuarios vean la misma imagen. Puesto que el informe se representa en el servidor, todas las fuentes utilizadas en el informe tienen que estar instaladas en el servidor. Para obtener más información, vea [Exportar a Microsoft Excel &#40;Generador de informes y SSRS&#41;](report-builder/exporting-to-an-image-file-report-builder-and-ssrs.md).  
  
- **Extensión de representación en PDF** La extensión de representación en PDF representa informes en archivos PDF que pueden abrirse y visualizarse con Adobe Acrobat 6.0 o posterior. Para obtener más información, vea [Exportar a un archivo PDF &#40;Generador de informes y SSRS&#41;](report-builder/exporting-to-a-pdf-file-report-builder-and-ssrs.md).  
  
- **Extensión de representación en Microsoft Word** La extensión de representación en [!INCLUDE[msCoName](../includes/msconame-md.md)] Word representa un informe como un documento de Word compatible con [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Word 2000 o posterior. Para obtener más información, vea [Exportar a Microsoft Word &#40;Generador de informes y SSRS&#41;](report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md).  
  
## <a name="report-processing-extensions"></a>Extensiones de procesamiento de informes

 Pueden agregarse extensiones de procesamiento de informes para proporcionar un procesamiento de informes personalizado para los elementos de informe que no se incluyen en [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. De forma predeterminada, un servidor de informes puede procesar tablas, gráficos, matrices, listas, cuadros de texto, imágenes y todos los demás elementos de informe. Si quiere agregar características especiales a un informe que requiere un procesamiento personalizado durante la ejecución de informe (por ejemplo, si quiere incrustar una asignación de [!INCLUDE[msCoName](../includes/msconame-md.md)] MapPoint), puede crear una extensión de procesamiento de informes para hacerlo.  
  
## <a name="delivery-extensions"></a>Extensiones de entrega

 La aplicación de procesamiento en segundo plano usa las extensiones de entrega para enviar los informes a diversas ubicaciones. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] contiene una extensión de entrega por correo electrónico y una extensión de entrega a recursos compartidos de archivos. La extensión de entrega por correo electrónico envía un mensaje de correo electrónico mediante el Protocolo simple de transferencia de correo (SMTP) que contiene el informe o un vínculo de dirección URL al informe. También se pueden enviar avisos cortos sin el vínculo a una dirección URL ni el informe a buscapersonas, teléfonos u otros dispositivos. La extensión de entrega a recursos compartidos de archivos guarda los informes en una carpeta compartida de la red. Se puede especificar la ubicación, el formato de representación, el nombre de archivo y las opciones de sobrescritura del archivo que se crea. También puede utilizar la entrega a recursos compartidos de archivos para archivar los informes representados y como parte de una estrategia para trabajar con informes de gran tamaño. Las extensiones de entrega funcionan conjuntamente con las suscripciones. Cuando un usuario crea una suscripción, elige una de las extensiones de entrega disponibles para determinar cómo se entrega el informe.