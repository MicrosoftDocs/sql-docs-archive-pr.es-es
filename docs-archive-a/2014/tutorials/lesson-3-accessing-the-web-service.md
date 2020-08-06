---
title: 'Lección 3: acceso al servicio Web | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c3e4c198-ab35-4548-9471-1b4e6b6e5dfd
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: c69e0dbe9eef987a764686bdf84e68bd8c530628
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746644"
---
# <a name="lesson-3-accessing-the-web-service"></a>Lección 3: Acceso al servicio web
  Una vez haya agregado al proyecto una referencia del servicio web del servidor de informes, el paso siguiente consiste en crear una instancia de la clase proxy del servicio web. A continuación, puede tener acceso a los métodos del servicio web llamando a los métodos de la clase proxy. Cuando la aplicación llama a estos métodos, el código de la clase proxy generado por [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] controla las comunicaciones entre la aplicación y el servicio web.  
  
 En primer lugar, va a crear una instancia de la clase proxy del servicio web, <xref:ReportService2010.ReportingService2010>. A continuación, hará una llamada al método <xref:ReportService2010.ReportingService2010.GetProperties%2A> del servicio web utilizando la clase proxy. Utilizará la llamada para recuperar el nombre y la descripción de uno de los informes de ejemplo, Company Sales.  
  
> [!NOTE]  
>  Cuando tenga acceso a un servicio web que se ejecuta en [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] con Advanced Services, debe agregar "$SQLExpress" a la ruta de acceso de "ReportServer". Por ejemplo:  
>   
>  `http://<Server Name>/reportserver$sqlexpress/reportservice2010.asmx"`  
  
### <a name="to-access-the-web-service"></a>Para obtener acceso al servicio web  
  
1.  Primero debe agregar el espacio de nombres al archivo Program.cs (Module1.vb en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) agregando una directiva `using` (`Imports` en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) al archivo de código. Si utiliza esta directiva, no es necesario utilizar nombres completos para los tipos en el espacio de nombres.  
  
2.  Para ello, agregue el código siguiente al principio del archivo de código:  
  
    ```vb  
    Imports System  
    Imports GetPropertiesSample.ReportService2010  
    ```  
  
    ```csharp  
    using System;  
    using GetPropertiesSample.ReportService2010;  
    ```  
  
3.  Una vez indicada la directiva de espacio de nombres en el archivo de código, indique el código siguiente en el método Main de la aplicación de la consola. Asegúrese de cambiar el nombre del servidor al establecer la propiedad **Url** de la instancia del servicio web:  
  
    ```vb  
    Sub Main()  
       Dim rs As New ReportingService2010  
       rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
       rs.Url = "http://<Server Name>/reportserver/reportservice2010.asmx"  
  
       Dim name As New [Property]  
       name.Name = "Name"  
  
       Dim description As New [Property]  
       description.Name = "Description"  
  
       Dim properties(1) As [Property]  
       properties(0) = name  
       properties(1) = description  
  
       Try  
          Dim returnProperties As [Property]() = rs.GetProperties( _  
             "/AdventureWorks 2012 Sample Reports/Company Sales 2012", properties)  
  
          Dim p As [Property]  
          For Each p In returnProperties  
              Console.WriteLine((p.Name + ": " + p.Value))  
          Next p  
  
       Catch e As Exception  
          Console.WriteLine(e.Message)  
       End Try  
    End Sub  
    ```  
  
    ```csharp  
    static void Main(string[] args)  
    {  
       ReportingService2010 rs = new ReportingService2010();  
       rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
       rs.Url = "http://<Server Name>/reportserver/reportservice2010.asmx";  
  
       Property name = new Property();  
       name.Name = "Name";  
  
       Property description = new Property();  
       description.Name = "Description";  
  
       Property[] properties = new Property[2];  
       properties[0] = name;  
       properties[1] = description;  
  
       try  
       {  
          Property[] returnProperties = rs.GetProperties(  
          "/AdventureWorks 2012 Sample Reports/Company Sales 2012",properties);  
  
          foreach (Property p in returnProperties)  
          {  
             Console.WriteLine(p.Name + ": " + p.Value);  
          }  
       }  
  
       catch (Exception e)  
       {  
          Console.WriteLine(e.Message);  
       }  
    }  
    ```  
  
4.  Guarde la solución.  
  
 El código de ejemplo de la visita guiada utiliza el método <xref:ReportService2010.ReportingService2010.GetProperties%2A> del servicio web para recuperar las propiedades del informe de ejemplo, Company Sales 2012. El <xref:ReportService2010.ReportingService2010.GetProperties%2A> método toma dos argumentos: el nombre del informe para el que desea recuperar información de propiedades y una matriz de objetos **Property []** que contiene los nombres de las propiedades cuyos valores desea recuperar. El método devuelve también una matriz de objetos **Property[]** con los nombres y valores de las propiedades especificadas en el argumento de propiedades.  
  
> [!NOTE]  
>  Si proporciona una matriz **Property[]** vacía para el argumento de propiedades, se devuelven todas las propiedades disponibles.  
  
 En el ejemplo anterior, el código utiliza el método <xref:ReportService2010.ReportingService2010.GetProperties%2A> para devolver el nombre y la descripción del informe de ejemplo, Company Sales 2012. A continuación, el código utiliza un bucle `foreach` para escribir las propiedades y los valores en la consola.  
  
 Para obtener más información acerca de la creación y utilización de una clase proxy para el servicio web del servidor de informes, vea [Creating the Web Service Proxy](../reporting-services/report-server-web-service/net-framework/creating-the-web-service-proxy.md).  
  
## <a name="see-also"></a>Consulte también  
 [Lección 4: ejecutar la aplicación &#40;VB-VC&#35;&#41;](../../2014/tutorials/lesson-4-running-the-application-vb-vcsharp.md)   
 [Obtener acceso al servicio Web del servidor de informes mediante el tutorial de Visual Basic o Visual C&#35; &#40;SSRS&#41;](../../2014/tutorials/access-report-server-web-service-vb-vcsharp-ssrs-tutorial.md)  
  
  
