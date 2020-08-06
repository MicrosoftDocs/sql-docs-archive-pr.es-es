---
title: Crear plantillas personalizadas | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- tql
- templates [Transact-SQL], creating
- templates [Transact-SQL]
ms.assetid: 41098e78-b482-410e-bfe8-2ac10769ac4a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 771547b9c47672d2c075b5e7215d78744fe5f18e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746659"
---
# <a name="create-custom-templates"></a>Crear plantillas personalizadas
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] incorpora plantillas para muchas tareas comunes, pero el auténtico valor reside en la posibilidad de crear una plantilla personalizada para un script complejo que tenga que crear con frecuencia. En esta práctica, creará un script sencillo con unos pocos parámetros; pero las plantillas también son útiles para scripts largos y repetitivos.  
  
## <a name="using-custom-templates"></a>Usar plantillas personalizadas  
  
#### <a name="to-create-a-custom-template"></a>Para crear una plantilla personalizada  
  
1.  En el Explorador de plantillas, expanda **Plantillas de SQL Server**, haga clic con el botón derecho en **Procedimiento almacenado**, seleccione **Nueva**y, después, haga clic en **Carpeta**.  
  
2.  Escriba **Custom** como nombre de la nueva carpeta de plantillas y, después, pulse ENTRAR.  
  
3.  Haga clic con el botón derecho en **Custom**, seleccione **Nueva**y después haga clic en **Plantilla**.  
  
4.  Escriba **WorkOrdersProc** como nombre de la plantilla nueva y, después, pulse **Entrar**.  
  
5.  Haga clic con el botón derecho en **WorkOrdersProc**y, después, haga clic en **Editar**.  
  
6.  En el cuadro de diálogo **Conectar al motor de base de datos** compruebe la información de conexión y, después, haga clic en **Conectar**.  
  
7.  En el Editor de consultas, escriba el siguiente script para crear un procedimiento almacenado que busque pedidos de una pieza concreta, en este caso, una cuchilla (Blade). Puede copiar y pegar el código de la ventana del tutorial.  
  
    ```  
    USE AdventureWorks20012;  
    GO  
    IF EXISTS (  
    SELECT *   
       FROM INFORMATION_SCHEMA.ROUTINES   
       WHERE SPECIFIC_NAME = 'WorkOrdersForBlade')  
       DROP PROCEDURE dbo.WorkOrdersForBlade;  
    GO  
    CREATE PROCEDURE dbo.WorkOrdersForBlade  
    AS  
    SELECT Name, WorkOrderID   
    FROM Production.WorkOrder AS WO  
    JOIN Production.Product AS Prod  
    ON WO.ProductID = Prod.ProductID  
    WHERE Name = 'Blade';  
    GO  
    ```  
  
8.  Pulse F5 para ejecutar este script y crear el procedimiento **WorkOrdersForBlade** .  
  
9. En el Explorador de objetos, haga clic con el botón derecho en el servidor y, después, en **Nueva consulta**. Se abrirá una ventana nueva del Editor de consultas.  
  
10. En el Editor de consultas, escriba **EXECUTE dbo.WorkOrdersForBlade**y, después, pulse F5 para ejecutar la consulta. Confirme que el panel **Resultados** devuelve una lista de los pedidos de trabajo relativos a cuchillas.  
  
11. Edite el script de la plantilla (el script del paso 7) y reemplace el nombre del producto hoja por el parámetro <strong> *<* PRODUCT_NAME</strong>, `nvarchar(50)` , <strong> *>* nombre</strong>, en cuatro lugares.  
  
    > [!NOTE]  
    >  Los parámetros requieren tres elementos: el nombre del parámetro que desea reemplazar, el tipo de datos del parámetro y un valor predeterminado para el parámetro.  
  
12. Ahora, el script debe tener el aspecto siguiente:  
  
    ```  
    USE AdventureWorks20012;  
    GO  
    IF EXISTS (  
    SELECT *   
       FROM INFORMATION_SCHEMA.ROUTINES   
       WHERE SPECIFIC_NAME = 'WorkOrdersFor<product_name, nvarchar(50), name>')  
       DROP PROCEDURE dbo.WorkOrdersFor<product_name, nvarchar(50), name>;  
    GO  
    CREATE PROCEDURE dbo.WorkOrdersFor<product_name, nvarchar(50), name>  
    AS  
    SELECT Name, WorkOrderID   
    FROM Production.WorkOrder AS WO  
    JOIN Production.Product AS Prod  
    ON WO.ProductID = Prod.ProductID  
    WHERE Name = '<product_name, nvarchar(50), name>';  
    GO  
    ```  
  
13. En el menú **Archivo** , haga clic en **Guardar WorkOrdersProc.sql** para guardar la plantilla.  
  
#### <a name="to-test-the-custom-template"></a>Para probar la plantilla personalizada  
  
1.  En el Explorador de plantillas, expanda **Procedimiento almacenado**y **Custom**y, después, haga doble clic en **WorkOrderProc**.  
  
2.  En el cuadro de diálogo **Conectarse al motor de base de datos** , rellene la información de conexión y luego haga clic en **Conectar**. Se abrirá una ventana nueva del Editor de consultas, que incluye el contenido de la plantilla **WorkOrderProc** .  
  
3.  En el menú **Consulta** , haga clic en **Especificar valores para parámetros de plantilla**.  
  
4.  En el cuadro de diálogo **reemplazar parámetros de plantilla** , para el `product_name` valor, escriba **Freewheel** (sobrescribiendo el contenido predeterminado) y, a continuación, haga clic en **Aceptar** para cerrar el cuadro de diálogo **reemplazar parámetros de plantilla** y modificar el script en el editor de consultas.  
  
5.  Presione F5 para ejecutar la consulta y crear el procedimiento.  
  
## <a name="next-task-in-lesson"></a>Siguiente tarea de la lección  
 [Guardar scripts como proyectos o soluciones](lesson-3-3-save-scripts-as-projects-or-solutions.md)  
  
  
