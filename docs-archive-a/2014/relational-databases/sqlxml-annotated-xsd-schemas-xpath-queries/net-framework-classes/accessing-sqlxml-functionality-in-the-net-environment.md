---
title: Obtener acceso a la funcionalidad SQLXML en el entorno de .NET | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- Managed Classes [SQLXML], accessing SQLXML functionality
- SQLXML Managed Classes, accessing SQLXML functionality
- DiffGrams [SQLXML], accessing SQLXML functionality
- .NET Framework [SQLXML], accessing SQLXML functionality
ms.assetid: 74744535-2945-414d-9a5b-7e8cc363953a
author: rothja
ms.author: jroth
ms.openlocfilehash: a2ba0a54310833c0a1a1315aa94d78fe5650d480
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673584"
---
# <a name="accessing-sqlxml-functionality-in-the-net-environment"></a>Acceso a la funcionalidad de SQLXML en el entorno .NET
  En este ejemplo se muestra lo siguiente:  
  
-   Cómo usar [!INCLUDE[msCoName](../../../includes/msconame-md.md)] las clases administradas de SQLXML (Microsoft. Data. SqlXml) para tener acceso a Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en el [!INCLUDE[msCoName](../../../includes/msconame-md.md)] entorno de .NET Framework.  
  
-   Cómo pueden aplicar actualizaciones de datos a tablas los DiffGrams que se generan en el entorno de .NET Framework [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 En esta aplicación se ejecuta una consulta XPath para un esquema XSD. La ejecución de la consulta XPath devuelve un documento XML que consta de datos de contacto (**FirstName**, **LastName**). La aplicación carga el documento XML en el conjunto de datos en el entorno de .NET Framework. Se modifican los datos del conjunto de datos: el nombre del primer contacto del conjunto de datos cambia a "Susan". El DiffGram se genera a partir del conjunto de datos y después se aplica la actualización especificada en el DiffGram (el cambio en el nombre del empleado) a la tabla Person.Contact.   
  
> [!NOTE]  
>  En el código, debe suministrarse el nombre de la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en la cadena de conexión.  
  
```  
using System;  
using System.Data;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
   static string ConnString = "Provider=SQLOLEDB;Server=SqlServerName;database=AdventureWorks;Integrated Security=SSPI;";  
   public static int testParams()  
   {  
      DataRow row;  
      SqlXmlAdapter ad;  
      //need a memory stream to hold diff gram temporarily  
      MemoryStream ms = new MemoryStream();  
      SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
      cmd.RootTag = "ROOT";  
      cmd.CommandText = "Con";  
      cmd.CommandType = SqlXmlCommandType.XPath;  
      cmd.SchemaPath = "MySchema.xml";  
      //load data set  
      DataSet ds = new DataSet();  
      ad = new SqlXmlAdapter(cmd);  
      ad.Fill(ds);  
      row = ds.Tables["Con"].Rows[0];  
      row["FName"] = "Susan";  
      ad.Update(ds);  
      return 0;  
   }  
   public static int Main(String[] args)  
   {  
      testParams();  
      return 0;  
   }  
}  
```  
  
 **Para probar el ejemplo:**  
  
 Para probar este ejemplo, debe tener instalado [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework en el equipo.  
  
1.  Guarde este esquema XSD (MySchema.xml) en una carpeta:  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
      <xsd:element name="Con" sql:relation="Person.Contact" >  
       <xsd:complexType>  
         <xsd:sequence>  
            <xsd:element name="FName"    
                         sql:field="FirstName"   
                         type="xsd:string" />   
            <xsd:element name="LName"    
                         sql:field="LastName"    
                         type="xsd:string" />  
         </xsd:sequence>  
         <xsd:attribute name="ContactID" type="xsd:integer" />  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
2.  Guarde el código C# (DocSample.cs) que se proporciona en este ejemplo en la misma carpeta en la que está almacenado el esquema. (Si almacena los archivos en otra carpeta, tendrá que modificar el código y especificar la ruta de acceso al directorio adecuada para el esquema de asignación).  
  
3.  Compile el código. Para compilar el código en el símbolo del sistema, use:  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     Esto crea una aplicación ejecutable (DocSample.exe).  
  
 En el símbolo del sistema, ejecute DocSample.exe.  
  
  
