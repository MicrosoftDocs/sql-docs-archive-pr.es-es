---
title: Uso de los bloques Try y Catch | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], try/catch blocks
- try/catch blocks [Reporting Services]
ms.assetid: a7a9ef53-e3b6-4bf7-81f3-d85615954e6f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a6aadb392fa4117484f3373ae232c3ed9c4b1d63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87749068"
---
# <a name="using-try-and-catch-blocks"></a>Uso de los bloques Try y Catch
  Después de limitar las solicitudes no válidas al servidor de informes agregando instrucciones condicionales al código, debería proporcionar un sistema de administración de excepciones adecuado a través del uso de bloques try/catch. Esta técnica proporciona otro nivel de protección con las solicitudes que no son válidas. Si una solicitud al servidor de informes se incluye en un bloque try y esa solicitud hace que el servidor de informes inicie una excepción, esta se detecta en el bloque catch, evitando así que la aplicación finalice inesperadamente. Una vez detectada la excepción, puede utilizarla para indicar al usuario que haga algo de manera diferente o simplemente le permita saber, de una manera descriptiva, que se ha producido un error. A continuación, puede utilizar un bloque finally para limpiar los recursos. Lo mejor sería generar un plan de administración de excepciones general para evitar la duplicación innecesaria de bloques try/catch.  
  
 En el ejemplo siguiente se utilizan bloques try/catch para mejorar la confiabilidad del código de administración de excepciones.  
  
```  
// C#  
private void PublishReport()  
{  
   int index;  
   string reservedChar;  
   string message;  
  
   // Check the text value of the name text box for "/",  
   // a reserved character  
   index = nameTextBox.Text.IndexOf(@"/");  
  
   if ( index != -1) // The text contains the character  
   {  
      reservedChar = nameTextBox.Text.Substring(index, 1);  
      // Build a user-friendly error message  
      message = "The name of the report cannot contain the reserved character " +  
         "\"" + reservedChar + "\". " +  
         "Please enter a valid name for the report. " +  
         "For more information about reserved characters, " +  
         "consult the online documentation";  
  
      MessageBox.Show(message, "Invalid Input Error");  
   }  
   else // Publish the report  
   {  
      Byte[] definition = null;  
      Warning[] warnings = {};  
      string name = nameTextBox.Text;  
  
      try  
      {  
         FileStream stream = File.OpenRead("MyReport.rdl");  
         definition = new Byte[stream.Length];  
         stream.Read(definition, 0, (int) stream.Length);  
         stream.Close();  
         // Create report with user-defined name  
         rs.CreateCatalogItem("Report", name, "/Samples", false, definition, null, out warnings);  
         MessageBox.Show("Report: {0} created successfully", name);  
      }  
  
      // Catch expected exceptions beginning with the most specific,  
      // moving to the least specific  
      catch(IOException ex)  
      {  
         MessageBox.Show(ex.Message, "File IO Exception");  
      }  
  
      catch (SoapException ex)  
      {  
         // The exception is a SOAP exception, so use  
         // the Detail property's Message element.  
         MessageBox.Show(ex.Detail["Message"].InnerXml, "SOAP Exception");   
      }  
  
      catch (Exception ex)  
      {  
         MessageBox.Show(ex.Message, "General Exception");  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>Consulte también  
 [Introducción al control de excepciones en Reporting Services](../introducing-exception-handling-in-reporting-services.md)   
 [Clase SoapException de Reporting Services](../soapexception-class/reporting-services-soapexception-class.md)  
  
  
