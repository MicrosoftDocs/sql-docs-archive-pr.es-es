---
title: Crear un componente de tiempo de ejecución de elemento de informe personalizado | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, creating
ms.assetid: b3e15a4a-98f8-4dbb-b847-bbcb20327051
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 50c5c0211bc5cd1359af9d1493782bd9d96c2b3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662677"
---
# <a name="creating-a-custom-report-item-run-time-component"></a>Crear un componente de tiempo de ejecución de elemento de informe personalizado
  El componente de tiempo de ejecución del elemento de informe personalizado se implementa como un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] componente de mediante cualquier lenguaje conforme a CLS y el procesador de informes lo llama en tiempo de ejecución. Las propiedades para el componente de tiempo de ejecución en el entorno de diseño se definen modificando el componente de tiempo de diseño correspondiente del elemento de informe personalizado.  

<!--
Replacing the following multiValue.....

ms.technology: 
  - "docset-sql-devref"
  - "reporting-services-native"

.....with the following single value.....

ms.technology: reporting-services
.

(GeneMi = MightyPen  ,  2019-04-20  ,  DevO= 1515083)
-->

 Para obtener un ejemplo de un elemento de informe personalizado totalmente implementado, vea [Ejemplos del producto SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="definition-and-instance-objects"></a>Objetos de definición e instancia  
 Antes de implementar un elemento de informe personalizado, es importante entender la diferencia entre *objetos de definición* y *objetos de instancia*. Los objetos de definición proporcionan la representación RDL del elemento de informe personalizado mientras que objetos de instancia son las versiones evaluadas de los objetos de definición. Hay solo un objeto de definición para cada elemento en el informe. Al tener acceso a las propiedades en un objeto de definición que contiene expresiones, obtendrá una cadena de expresión no evaluada. Los objetos de instancia contienen las versiones evaluadas de los objetos de definición y pueden tener una relación uno a varios con el objeto de definición de un elemento. Por ejemplo, si un informe tiene una región de datos <xref:Microsoft.ReportingServices.OnDemandReportRendering.Tablix> que contiene un <xref:Microsoft.ReportingServices.OnDemandReportRendering.CustomReportItem> en una fila de detalle, solo habrá un objeto de definición, pero habrá un objeto de instancia para cada fila en la región de datos.  
  
## <a name="implementing-the-icustomreportitem-interface"></a>Implementar la interfaz ICustomReportItem  
 Para crear un componente de tiempo de ejecución `CustomReportItem`, necesitará implementar la interfaz <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem> que se define en Microsoft.ReportingServices.ProcessingCore.dll:  
  
```csharp  
namespace Microsoft.ReportingServices.OnDemandReportRendering  
{  
    public interface ICustomReportItem  
    {  
        void GenerateReportItemDefinition(CustomReportItem customReportItem);  
void EvaluateReportItemInstance(CustomReportItem customReportItem);  
    }  
}  
```  
  
 Después de haber implementado la interfaz <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem>, se generarán dos códigos auxiliares de método: <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.GenerateReportItemDefinition%2A> y <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.EvaluateReportItemInstance%2A>. El método <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.GenerateReportItemDefinition%2A> se llama primero y se utiliza para establecer las propiedades de definición y crear el objeto <xref:Microsoft.ReportingServices.OnDemandReportRendering.Image> que contendrá las propiedades de instancia y definición que se utilizan para representar el elemento. Se llama al método <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.EvaluateReportItemInstance%2A> una vez evaluados los objetos de definición, y este método proporciona los objetos de instancia que se utilizarán para representar el elemento.  
  
 La siguiente es una implementación de ejemplo de un elemento de informe personalizado que representa el nombre del control como una imagen.  
  
```csharp  
namespace Microsoft.Samples.ReportingServices  
{  
    using System;  
    using System.Collections.Generic;  
    using System.Collections.Specialized;  
    using System.Drawing.Imaging;  
    using System.IO;  
    using System.Text;  
    using Microsoft.ReportingServices.OnDemandReportRendering;  
  
    public class PolygonsCustomReportItem : ICustomReportItem  
    {  
        #region ICustomReportItem Members  
  
        public void GenerateReportItemDefinition(CustomReportItem cri)  
        {  
            // Create the Image object that will be   
            // used to render the custom report item  
            cri.CreateCriImageDefinition();  
            Image polygonImage = (Image)cri.GeneratedReportItem;  
        }  
  
        public void EvaluateReportItemInstance(CustomReportItem cri)  
        {  
            // Get the Image definition  
            Image polygonImage = (Image)cri.GeneratedReportItem;  
  
            // Create the image for the custom report item  
            polygonImage.ImageInstance.ImageData = DrawImage(cri);  
        }  
  
        #endregion  
  
        /// <summary>  
        /// Creates an image of the CustomReportItem's name  
        /// </summary>  
        private byte[] DrawImage(CustomReportItem customReportItem)  
        {  
            int width = 1;          // pixels  
            int height = 1;         // pixels  
            int resolution = 75;    // dpi  
  
            System.Drawing.Bitmap bitmap = new System.Drawing.Bitmap(width, height);  
            bitmap.SetResolution(resolution, resolution);  
  
            System.Drawing.Graphics graphics = System.Drawing.Graphics.FromImage(bitmap);  
            graphics.PageUnit = System.Drawing.GraphicsUnit.Pixel;  
  
            // Get the Font for the Text  
            System.Drawing.Font font = new System.Drawing.Font(System.Drawing.FontFamily.GenericMonospace,  
                12, System.Drawing.FontStyle.Regular);  
  
            // Get the Brush for drawing the Text  
            System.Drawing.Brush brush = new System.Drawing.SolidBrush(System.Drawing.Color.LightGreen);  
  
            // Get the measurements for the image  
            System.Drawing.SizeF maxStringSize = graphics.MeasureString(customReportItem.Name, font);  
            width = (int)(maxStringSize.Width + 2 * font.GetHeight(resolution));  
            height = (int)(maxStringSize.Height + 2 * font.GetHeight(resolution));  
  
            bitmap.Dispose();  
            bitmap = new System.Drawing.Bitmap(width, height);  
            bitmap.SetResolution(resolution, resolution);  
  
            graphics.Dispose();  
            graphics = System.Drawing.Graphics.FromImage(bitmap);  
            graphics.PageUnit = System.Drawing.GraphicsUnit.Pixel;  
  
            // Draw the text  
            graphics.DrawString(customReportItem.Name, font, brush, font.GetHeight(resolution),   
                font.GetHeight(resolution));  
  
            // Create the byte array of the image data  
            MemoryStream memoryStream = new MemoryStream();  
            bitmap.Save(memoryStream, ImageFormat.Bmp);  
            memoryStream.Position = 0;  
            byte[] imageData = new byte[memoryStream.Length];  
            memoryStream.Read(imageData, 0, imageData.Length);  
  
            return imageData;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte también  
 [Arquitectura de elementos de informe personalizados](custom-report-item-architecture.md)   
 [Crear un componente de tiempo de diseño de elemento de informe personalizado](creating-a-custom-report-item-design-time-component.md)   
 [Bibliotecas de clases de elementos de informe personalizadas](custom-report-item-class-libraries.md)   
 [Cómo: Implementar un elemento de informe personalizado](how-to-deploy-a-custom-report-item.md)  
  
  
