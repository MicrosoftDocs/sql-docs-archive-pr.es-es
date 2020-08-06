---
title: Usar el acceso URL en una aplicación de Windows | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Windows applications [Reporting Services]
- Web Browser controls [Reporting Services]
- Windows Forms [Reporting Services]
- browser controls [Reporting Services]
- URL access [Reporting Services], Windows applications
ms.assetid: a4b222e5-0cbd-409c-92c4-046a674db8ac
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8f8b901481b1d6fcc3cdd8626b43cd3a69174c1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87747522"
---
# <a name="using-url-access-in-a-windows-application"></a>Usar el acceso URL en una aplicación para Windows
  Aunque el acceso URL a un servidor de informes se optimiza para un entorno web, también puede utilizar el acceso URL para incrustar informes de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en una aplicación para [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Sin embargo, el acceso URL que implica formularios Windows Forms todavía requiere que use la tecnología del explorador web. Puede utilizar los escenarios de integración siguientes con el acceso URL y los formularios Windows Forms:  
  
-   Mostrar un informe de una aplicación de formulario Windows Forms iniciando mediante programación un explorador web.  
  
-   Usar el control <xref:System.Windows.Forms.WebBrowser> en un formulario Windows Forms para mostrar un informe.  
  
## <a name="starting-internet-explorer-from-a-windows-form"></a>Iniciar Internet Explorer desde un formulario Windows Forms  
 Puede utilizar la clase <xref:System.Diagnostics.Process> para tener acceso a un proceso que se está ejecutando en un equipo. La <xref:System.Diagnostics.Process> clase es una [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] construcción útil para iniciar, detener, controlar y supervisar aplicaciones. Para ver un informe concreto en la base de datos del servidor de informes, puede iniciar el proceso **IExplore** y pasarle la dirección URL al informe. El ejemplo de código siguiente se puede utilizar para iniciar [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer y una dirección URL de un informe concreto cuando el usuario hace clic en un botón de un formulario Windows Forms.  
  
```vb  
Private Sub viewReportButton_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles viewReportButton.Click  
   ' Build the URL access string based on values supplied by a user  
   Dim url As String = serverUrlTextBox.Text + "?" & reportPathTextBox.Text & _  
   "&rs:Command=Render" & "&rs:Format=HTML4.0"  
  
   ' If the user does not select the toolbar check box,  
   ' turn the toolbar off in the HTML Viewer  
   If toolbarCheckBox.Checked = False Then  
      url += "&rc:Toolbar=False"  
   End If  
   ' load report in the Web browser  
   Try  
      System.Diagnostics.Process.Start("IExplore", url)  
   Catch  
      MessageBox.Show("The system could not start the specified report using Internet Explorer.", _  
      "An error has occurred", MessageBoxButtons.OK, MessageBoxIcon.Error)  
   End Try  
End Sub 'viewReportButton_Click  
```  
  
```csharp  
// Sample click event for a Button control on a Windows Form  
private void viewReportButton_Click(object sender, System.EventArgs e)  
{  
   // Build the URL access string based on values supplied by a user  
   string url = serverUrlTextBox.Text + "?" + reportPathTextBox.Text +  
      "&rs:Command=Render" + "&rs:Format=HTML4.0";  
  
   // If the user does not check the toolbar check box,  
   // turn the toolbar off in the HTML Viewer  
   if (toolbarCheckBox.Checked == false)  
      url += "&rc:Toolbar=False";  
  
   // load report in the Web browser  
   try  
   {  
      System.Diagnostics.Process.Start("IExplore", url);  
   }  
  
   catch (Exception)  
   {  
      MessageBox.Show(  
         "The system could not open the specified report using Internet Explorer.",   
         "An error has occurred", MessageBoxButtons.OK, MessageBoxIcon.Error);  
   }  
}  
```  
  
## <a name="embedding-a-browser-control-on-a-windows-form"></a>Incrustar un control de explorador en un formulario Windows Forms  
 Si no desea ver un informe en un explorador web externo, puede incrustar un explorador web fácilmente como parte de un formulario Windows Forms utilizando el control <xref:System.Windows.Forms.WebBrowser>.  
  
###### <a name="to-add-the-webbrowser-control-to-your-windows-form"></a>Para agregar el control WebBrowser al formulario Windows Forms  
  
1.  Cree una nueva aplicación Windows en [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] o [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .  
  
2.  Busque el control <xref:System.Windows.Forms.WebBrowser> en el cuadro de diálogo **Cuadro de herramientas**.  
  
     Si el **cuadro de herramientas** no está visible, puede obtener acceso a él haciendo clic en el elemento del menú **Ver** y seleccionando **Cuadro de herramientas**.  
  
3.  Arrastre el control <xref:System.Windows.Forms.WebBrowser> a la superficie de diseño del formulario Windows Forms.  
  
     El control <xref:System.Windows.Forms.WebBrowser> denominado webBrowser1 se agrega al formulario  
  
 Al llamar al método del control <xref:System.Windows.Forms.WebBrowser>**Navigate**, dirige el control a una dirección URL. Puede asignar una cadena de acceso URL concreta al control <xref:System.Windows.Forms.WebBrowser> en tiempo de ejecución como se muestra en el ejemplo siguiente.  
  
```vb  
Dim url As String = "http://localhost/reportserver?/" & _  
                    "AdventureWorks2012 Sample Reports/" & _  
                    "Company Sales&rs:Command=Render"  
WebBrowser1.Navigate(url)  
```  
  
```csharp  
string url = "http://localhost/reportserver?/" +  
             "AdventureWorks2012 Sample Reports/" +  
             "Company Sales&rs:Command=Render";  
webBrowser1.Navigate(url);  
```  
  
## <a name="see-also"></a>Consulte también  
 [Integración de Reporting Services en aplicaciones](../application-integration/integrating-reporting-services-into-applications.md)   
 [Integración de Reporting Services mediante el acceso URL](integrating-reporting-services-using-url-access.md)   
 [Integración de Reporting Services mediante SOAP](integrating-reporting-services-using-soap.md)   
 [Integrar Reporting Services mediante los controles ReportViewer](integrating-reporting-services-using-reportviewer-controls.md)   
 [Acceso URL &#40;SSRS&#41;](../url-access-ssrs.md)  
  
  
