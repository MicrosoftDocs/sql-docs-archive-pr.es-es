---
title: Proporcionar una consulta de origen (Asistente para importación y exportación de SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.providesourcequery.f1
ms.assetid: c8cbd07e-b9c3-422f-94b8-d6fc8cf31cf5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b21100f51c279e9ba764c8f82565af9d6e391ef3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674919"
---
# <a name="provide-a-source-query-sql-server-import-and-export-wizard"></a>Proporcionar una consulta de origen (Asistente para importación y exportación de SQL Server)
  Use la página **proporcionar una consulta de origen** para escribir la instrucción SQL que generará los datos que se van a copiar del origen de datos al destino.  
  
 Para obtener más información acerca de este asistente, vea [Asistente para importación y exportación de SQL Server](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Para obtener información sobre las opciones para iniciar el asistente, así como los permisos necesarios para ejecutar el asistente correctamente, vea [ejecutar el Asistente para importación y exportación de SQL Server](start-the-sql-server-import-and-export-wizard.md).  
  
 La finalidad del Asistente para importación y exportación de SQL Server es copiar datos desde un origen a un destino. El asistente también puede crear una base de datos y tablas de destino. Sin embargo, si tiene que copiar diversas bases de datos o tablas, u otros tipos de objetos de bases de datos, debe utilizar el Asistente para copiar bases de datos. Para más información, consulte [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Opciones  
 **Instrucción SQL**  
 Escriba una instrucción de consulta para recuperar las filas de datos seleccionadas de la base de datos de origen. Por ejemplo, la siguiente instrucción de consulta recupera **SalesPersonID**, **SalesQuota**y **SalesYTD** de la base de datos AdventureWorks para los vendedores con un porcentaje de comisión superior al 1,5%.  
  
```  
SELECT SalesPersonID, SalesQuota, SalesYTD  
FROM Sales.SalesPerson  
WHERE CommissionPct > 0.015  
```  
  
 **Parse**  
 Comprueba la sintaxis de la instrucción SQL en el cuadro de texto **Instrucción SQL**.  
  
> [!NOTE]  
>  Si el tiempo necesario para comprobar la sintaxis de la instrucción supera el valor de tiempo de espera de 30 segundos, el análisis se detiene y se genera un error. No podrá pasar esta página del asistente hasta que el análisis se realice correctamente. Una solución es crear una vista de base de datos basada en la consulta y consultar la vista del asistente, en lugar de escribir directamente el texto de la consulta.  
  
 **Browse**  
 Seleccione un archivo que contenga una instrucción SQL mediante el cuadro de diálogo **abrir** . Al seleccionar un archivo se copiará el texto del archivo en el cuadro de texto **Instrucción de consulta** .  
  
  
