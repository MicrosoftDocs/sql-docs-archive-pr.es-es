---
title: SQL Server Native Client orígenes de datos ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, about data sources
- ODBC data sources, names
- data sources [SQL Server Native Client]
- names [ODBC]
- ODBC applications, data sources
- SQL Server Native Client ODBC driver, data sources
- ODBC data sources
ms.assetid: a6a50fd0-d439-43fd-b76f-16ec02f478c5
author: rothja
ms.author: jroth
ms.openlocfilehash: 6960118e13f0843640b18056bda655726cbbbd29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672938"
---
# <a name="sql-server-native-client-odbc-data-sources"></a>Orígenes de datos de ODBC para SQL Server Native Client
  Un nombre del origen de datos (DSN) de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identifica un origen de datos ODBC que contiene toda la información que una aplicación ODBC necesita para conectar a una base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en un servidor concreto. Existen dos métodos que puede utilizar para definir un nombre del origen de datos ODBC:  
  
-   En un equipo cliente, abra herramientas administrativas en el panel de control y haga doble clic en **orígenes de datos (ODBC)**. Así abrirá el Administrador de orígenes de datos ODBC, que puede utilizar para crear un DSN.  
  
-   En una aplicación ODBC, llame a [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md).  
  
 Un origen de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contiene:  
  
-   El nombre del origen de datos.  
  
-   Cualquier información necesaria para conectar a una instancia concreta de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   La base de datos predeterminada que se utilizará en una instancia concreta de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (opcional).  
  
-   Valores como las opciones ANSI que se van a utilizar, si se registran estadísticas de rendimiento, etc. (opcional).  
  
 No es necesario contar con una aplicación ODBC para conectar a través de un origen de datos. Sin embargo, la aplicación debe proporcionar la misma información de conectividad a una función de conexión de ODBC que el controlador encontraría en un DSN.  
  
## <a name="see-also"></a>Consulte también  
 [Comunicarse con SQL Server &#40;ODBC&#41;](communicating-with-sql-server-odbc.md)  
  
  
