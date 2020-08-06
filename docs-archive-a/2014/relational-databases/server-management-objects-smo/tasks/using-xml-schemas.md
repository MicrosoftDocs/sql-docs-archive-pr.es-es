---
title: Usar esquemas XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- XML [SMO]
ms.assetid: 9d04de01-efeb-4b2d-8c28-3234bc7ff2f3
author: stevestein
ms.author: sstein
ms.openlocfilehash: a0e5c58bb05da7025651a4e55e29541d694ba1ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750574"
---
# <a name="using-xml-schemas"></a>Utilizar esquemas XML
  La programación XML en SMO se limita a proporcionar tipos de datos XML, espacios de nombres XML y la indización simple en columnas de tipo de datos XML.  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]proporciona almacenamiento nativo para las instancias de documentos XML. Los esquemas XML le permiten definir tipos de datos XML complejos, que se pueden utilizar para validar los documentos XML para asegurar la integridad de los datos. El esquema XML se define en el objeto <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection>.  
  
## <a name="example"></a>Ejemplo  
 Para utilizar cualquier ejemplo de código que se proporcione, deberá elegir el entorno de programación, la plantilla de programación y el lenguaje de programación con los que crear su aplicación. Para obtener más información, vea [crear un proyecto de Visual Basic SMO en Visual Studio .net](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) o [crear un proyecto de Visual C&#35; SMO en Visual Studio .net](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-an-xml-schema-in-visual-basic"></a>Crear un esquema XML en Visual Basic  
 En este ejemplo de código se muestra cómo crear un esquema XML utilizando el objeto <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection>. La propiedad <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A>, que define la colección de esquemas XML, contiene varias comillas dobles. Estas comillas se reemplazan por la cadena `chr(34)`.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBXMLSchema1](SMO How to#SMO_VBXMLSchema1)]  -->  
  
## <a name="creating-an-xml-schema-in-visual-c"></a>Crear un esquema XML en Visual C#  
 En este ejemplo de código se muestra cómo crear un esquema XML utilizando el objeto <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection>. La propiedad <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A>, que define la colección de esquemas XML, contiene varias comillas dobles. Estas comillas se reemplazan por la cadena `chr(34)`.  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = default(Server);  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db = default(Database);  
            db = srv.Databases["AdventureWorks2012"];  
            //Define an XmlSchemaCollection object by supplying the parent  
            // database and name arguments in the constructor.   
            XmlSchemaCollection xsc = default(XmlSchemaCollection);  
            xsc = new XmlSchemaCollection(db, "MySampleCollection");  
            xsc.Text = "<schema xmlns=" + Strings.Chr(34) + "http://www.w3.org/2001/XMLSchema" + Strings.Chr(34) + " xmlns:ns=" + Strings.Chr(34) + "http://ns" + Strings.Chr(34) + "><element name=" + Strings.Chr(34) + "e" + Strings.Chr(34) + " type=" + Strings.Chr(34) + "dateTime" + Strings.Chr(34) + "/></schema>";  
            //Create the XML schema collection on the instance of SQL Server.   
            xsc.Create();  
        }  
```  
  
## <a name="creating-an-xml-schema-in-powershell"></a>Crear un esquema XML en PowerShell  
 En este ejemplo de código se muestra cómo crear un esquema XML utilizando el objeto <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection>. La propiedad <xref:Microsoft.SqlServer.Management.Smo.XmlSchemaCollection.Text%2A>, que define la colección de esquemas XML, contiene varias comillas dobles. Estas comillas se reemplazan por la cadena `chr(34)`.  
  
```powershell
#Get a server object which corresponds to the default instance replace LocalMachine with the physical server  
cd \sql\LocalHost  
$srv = Get-Item default  
  
#Reference the AdventureWorks database.  
$db = $srv.Databases["AdventureWorks2012"]  
  
#Create a new schema collection  
$xsc = New-Object -TypeName Microsoft.SqlServer.Management.SMO.XmlSchemaCollection `  
-argumentlist $db,"MySampleCollection"  
  
#Add the xml  
$dq = '"' # the double quote character  
$xsc.Text = "<schema xmlns=" + $dq + "http://www.w3.org/2001/XMLSchema" + $dq + `  
"  xmlns:ns=" + $dq + "http://ns" + $dq + "><element name=" + $dq + "e" + $dq +`  
 " type=" + $dq + "dateTime" + $dq + "/></schema>"  
  
#Create the XML schema collection on the instance of SQL Server.  
$xsc.Create()  
```  
