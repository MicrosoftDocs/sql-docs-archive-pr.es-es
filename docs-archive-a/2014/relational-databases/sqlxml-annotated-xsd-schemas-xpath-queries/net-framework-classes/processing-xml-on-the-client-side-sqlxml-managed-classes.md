---
title: Procesar XML en el lado cliente (clases administradas de SQLXML) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- processing XML on client side [SQLXML]
- client-side XML formatting
- Managed Classes [SQLXML], client-side XML formatting
- SQLXML Managed Classes, client-side XML formatting
- ClientSideXml property
ms.assetid: 5e7ecf18-66fc-49ff-bc50-83635cd7ac0b
author: rothja
ms.author: jroth
ms.openlocfilehash: fb90f7c5c823c750b64f47d0c9df9551b9f857b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662767"
---
# <a name="processing-xml-on-the-client-side-sqlxml-managed-classes"></a><span data-ttu-id="ceb86-102">Procesar XML en el cliente (clases administradas de SQLXML)</span><span class="sxs-lookup"><span data-stu-id="ceb86-102">Processing XML on the Client Side (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="ceb86-103">En este ejemplo se muestra el uso de la propiedad Clientsidexml,.</span><span class="sxs-lookup"><span data-stu-id="ceb86-103">This example illustrates the use of the ClientSideXml property.</span></span> <span data-ttu-id="ceb86-104">La aplicación ejecuta un procedimiento almacenado en el servidor.</span><span class="sxs-lookup"><span data-stu-id="ceb86-104">The application executes a stored procedure on the server.</span></span> <span data-ttu-id="ceb86-105">El resultado del procedimiento almacenado (un conjunto de filas de dos columnas) se procesa en el cliente para generar un documento XML.</span><span class="sxs-lookup"><span data-stu-id="ceb86-105">The result of the stored procedure (a two-column rowset) is processed on the client side to produce an XML document.</span></span>  
  
 <span data-ttu-id="ceb86-106">El siguiente procedimiento almacenado GetContacts devuelve el **nombre** y el **Apellido** de los empleados de la tabla person. contact de la base de datos AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ceb86-106">The following GetContacts stored procedure returns **FirstName** and **LastName** of employees in the Person.Contact table in the AdventureWorks database.</span></span>  
  
```  
USE AdventureWorks  
CREATE PROCEDURE GetContacts @LastName varchar(20)  
AS  
SELECT FirstName, LastName  
FROM   Person.Contact  
WHERE LastName = @LastName  
Go  
```  
  
 <span data-ttu-id="ceb86-107">Esta aplicación de C# ejecuta el procedimiento almacenado y especifica la opción FOR XML AUTO en la especificación del valor CommandText.</span><span class="sxs-lookup"><span data-stu-id="ceb86-107">This C# application executes the stored procedure and specifies the FOR XML AUTO option in specifying the CommandText value.</span></span> <span data-ttu-id="ceb86-108">En la aplicación, la propiedad Clientsidexml, del objeto SqlXmlCommand se establece en true.</span><span class="sxs-lookup"><span data-stu-id="ceb86-108">In the application, the ClientSideXml property of the SqlXmlCommand object is set to true.</span></span> <span data-ttu-id="ceb86-109">Esto le permite ejecutar procedimientos almacenados preexistentes que devuelven un conjunto de filas y aplican a este último una transformación XML en el cliente.</span><span class="sxs-lookup"><span data-stu-id="ceb86-109">This allows you to execute preexisting stored procedures that return a rowset and apply an XML transformation to it on the client.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ceb86-110">En el código, debe proporcionar el nombre de la instancia de Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en la cadena de conexión.</span><span class="sxs-lookup"><span data-stu-id="ceb86-110">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
    static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         //Stream strm;  
         SqlXmlParameter p;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.ClientSideXml = true;  
         cmd.CommandText = "EXEC GetContacts ? FOR XML NESTED";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         using (Stream strm = cmd.ExecuteStream())   
         {  
            using (StreamReader sr = new StreamReader(strm))  
                  {  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         return 0;  
      }  
  
public static int Main(String[] args)  
{  
    testParams();  
    return 0;  
}  
}  
```  
  
 <span data-ttu-id="ceb86-111">Para probar este ejemplo, debe tener instalado [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework en el equipo.</span><span class="sxs-lookup"><span data-stu-id="ceb86-111">To test this example, you must have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="ceb86-112">Para probar la aplicación</span><span class="sxs-lookup"><span data-stu-id="ceb86-112">To test the application</span></span>  
  
1.  <span data-ttu-id="ceb86-113">Cree el procedimiento almacenado.</span><span class="sxs-lookup"><span data-stu-id="ceb86-113">Create the stored procedure.</span></span>  
  
2.  <span data-ttu-id="ceb86-114">Guarde el código (DocSample.cs) de C# que se proporciona en este ejemplo en una carpeta.</span><span class="sxs-lookup"><span data-stu-id="ceb86-114">Save the C# code (DocSample.cs) that is provided in this example in a folder.</span></span> <span data-ttu-id="ceb86-115">Modifique el código para especificar la información adecuada de inicio de sesión y contraseña.</span><span class="sxs-lookup"><span data-stu-id="ceb86-115">Edit the code to specify appropriate login and password information.</span></span>  
  
3.  <span data-ttu-id="ceb86-116">Compile el código.</span><span class="sxs-lookup"><span data-stu-id="ceb86-116">Compile the code.</span></span> <span data-ttu-id="ceb86-117">Para compilar el código en el símbolo del sistema, use:</span><span class="sxs-lookup"><span data-stu-id="ceb86-117">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="ceb86-118">Esto crea una aplicación ejecutable (DocSample.exe).</span><span class="sxs-lookup"><span data-stu-id="ceb86-118">This creates an executable (DocSample.exe).</span></span>  
  
4.  <span data-ttu-id="ceb86-119">En el símbolo del sistema, ejecute DocSample.exe.</span><span class="sxs-lookup"><span data-stu-id="ceb86-119">At the command prompt, execute DocSample.exe.</span></span>  
  
  