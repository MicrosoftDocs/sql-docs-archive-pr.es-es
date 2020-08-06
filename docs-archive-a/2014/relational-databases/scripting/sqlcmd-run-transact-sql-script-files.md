---
title: Ejecutar archivos de scripts Transact-SQL mediante sqlcmd
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- transact sql scripts
ms.assetid: 90067eb8-ca3e-44e8-bb1a-bf7d1a359423
author: rothja
ms.author: jroth
ms.openlocfilehash: cd34b089fc4e971cac9e5713cbe303192a7a48c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669581"
---
# <a name="run-transact-sql-script-files-using-sqlcmd"></a>Ejecutar archivos de scripts Transact-SQL mediante sqlcmd
  Puede utilizar `sqlcmd` para ejecutar un archivo de script de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Un archivo de script de [!INCLUDE[tsql](../../includes/tsql-md.md)] es un archivo de texto que puede incluir una combinación de instrucciones [!INCLUDE[tsql](../../includes/tsql-md.md)], comandos `sqlcmd` y variables de scripting.  
  
 Para crear un archivo sencillo de script de [!INCLUDE[tsql](../../includes/tsql-md.md)] mediante el Bloc de notas, siga estos pasos:  
  
1.  Haga clic en **Inicio**, seleccione **Todos los programas**, **Accesorios**y, a continuación, haga clic en **Bloc de notas**.  
  
2.  Copie y pegue el siguiente código [!INCLUDE[tsql](../../includes/tsql-md.md)] en el Bloc de notas:  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT p.FirstName + ' ' + p.LastName AS 'Employee Name',  
    a.AddressLine1, a.AddressLine2 , a.City, a.PostalCode   
    FROM Person.Person AS p   
       INNER JOIN HumanResources.Employee AS e   
            ON p.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.BusinessEntityAddress bea   
            ON bea.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.Address AS a   
            ON a.AddressID = bea.AddressID;  
    GO  
    ```  
  
3.  Guarde el archivo como **myScript.sql** en la unidad C.  
  
### <a name="to-run-the-script-file"></a>Para ejecutar el archivo de script  
  
1.  Abra una ventana de símbolo del sistema.  
  
2.  En la ventana de símbolo del sistema, escriba: `sqlcmd -S myServer\instanceName -i C:\myScript.sql`  
  
3.  Presione ENTRAR.  
  
 En la ventana del símbolo del sistema se escribe una lista con las direcciones y los nombres de los empleados que figuran en [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] .  
  
### <a name="to-save-this-output-to-a-text-file"></a>Para guardar los resultados en un archivo de texto  
  
1.  Abra una ventana de símbolo del sistema.  
  
2.  En la ventana de símbolo del sistema, escriba: `sqlcmd -S myServer\instanceName -i C:\myScript.sql -o C:\EmpAdds.txt`  
  
3.  Presione ENTRAR.  
  
 La ventana del símbolo del sistema no devuelve resultados. En su lugar, los resultados se envían al archivo EmpAdds.txt. Para comprobar los resultados, abra el archivo EmpAdds.txt.  
  
## <a name="see-also"></a>Consulte también  
 [Iniciar la utilidad sqlcmd](sqlcmd-start-the-utility.md)   
 [Utilidad sqlcmd](../../tools/sqlcmd-utility.md)  
  
  
