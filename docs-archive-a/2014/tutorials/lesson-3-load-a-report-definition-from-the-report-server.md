---
title: 'Lección 3: cargar una definición de informe desde el servidor de informes | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ad8b31c-43b0-4481-a31b-090cbed4a438
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: dc6ed26703599792b9c739f8d185ae4f190fc8be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87671875"
---
# <a name="lesson-3-load-a-report-definition-from-the-report-server"></a>Lección 3: Carga de una definición de informe desde el servidor de informes
  Una vez que haya creado el proyecto y generado las clases con el esquema RDL, estará listo para cargar una definición de informe desde el servidor de informes.  
  
### <a name="to-load-a-report-definition"></a>Para cargar una definición de informe  
  
1.  Agregue un campo privado en la parte superior de la `ReportUpdater` clase (módulo si está usando [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) para la `Report` clase. Este campo se utilizará para mantener una referencia al informe que se ha cargado desde el servidor de informes para la duración de la aplicación.  
  
    ```csharp  
    private Report _report;  
    ```  
  
    ```vb  
    Private m_report As Report  
    ```  
  
2.  Reemplace el código del método `LoadReportDefinition()` en el archivo Program.cs (Module1.vb para [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) por el siguiente código:  
  
    ```csharp  
    private void LoadReportDefinition()  
    {  
        System.Console.WriteLine("Loading Report Definition");  
  
        string reportPath =   
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012";  
  
        // Retrieve the report definition   
        // from the report server  
        byte[] bytes =   
            _reportService.GetItemDefinition(reportPath);  
  
        if (bytes != null)  
        {  
            XmlSerializer serializer =   
                new XmlSerializer(typeof(Report));  
  
            // Load the report bytes into a memory stream  
            using (MemoryStream stream = new MemoryStream(bytes))  
            {  
                // Deserialize the report stream to an   
                // instance of the Report class  
                _report = (Report)serializer.Deserialize(stream);  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub LoadReportDefinition()  
  
        System.Console.WriteLine("Loading Report Definition")  
  
        Dim reportPath As String = _  
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012"  
  
        'Retrieve the report definition   
        'from the report server  
        Dim bytes As Byte() = _  
            m_reportService.GetItemDefinition(reportPath)  
  
        If Not (bytes Is Nothing) Then  
  
            Dim serializer As XmlSerializer = _  
                New XmlSerializer(GetType(Report))  
  
            'Load the report bytes into a memory stream  
            Using stream As MemoryStream = New MemoryStream(bytes)  
  
                'Deserialize the report stream to an   
                'instance of the Report class  
                m_report = CType(serializer.Deserialize(stream), _  
                                 Report)  
  
            End Using  
  
        End If  
  
    End Sub  
    ```  
  
## <a name="next-lesson"></a>Lección siguiente  
 En la siguiente lección escribirá el código para actualizar la definición de informe que se cargó desde el servidor de informes. Vea [la lección 4: actualizar la definición de informe mediante programación](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md).  
  
## <a name="see-also"></a>Consulte también  
 [Actualizar informes con clases generadas a partir del esquema RDL &#40;tutorial de SSRS&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)   
 [Lenguaje RDL (Report Definition Language) &#40;SSRS&#41;](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
