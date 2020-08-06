---
title: Apertura del visor de archivos de registro | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Log File Viewer, opening
ms.assetid: a86b89cb-0432-4648-895a-05ecc5450e45
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 269ff10275f7463a8a85249a2a0f06fe9bde364a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87671528"
---
# <a name="open-log-file-viewer"></a>Abrir el Visor de archivos de registro
  Puede usar el Visor del archivo de registros de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] para obtener acceso a la información sobre los errores y eventos capturados en los registros siguientes:  
  
-   Recopilación de auditoría  
  
-   Recopilación de datos  
  
-   Correo electrónico de base de datos  
  
-   Historial de trabajos  
  
-   SQL Server  
  
-   Agente SQL Server  
  
-   Eventos de Windows (también se puede obtener acceso a los eventos de Windows desde el Visor de eventos).  
  
 A partir de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], puede utilizar Servidores registrados para ver los archivos de registro de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de instancias locales o remotas de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Mediante Servidores registrados, puede ver los archivos de registro con o sin las instancias en línea. Para obtener más información acerca del acceso en línea, vea el procedimiento “Ver archivos de registro en línea desde servidores registrados” más adelante en este tema. Para obtener más información sobre el acceso sin conexión a los archivos de registros de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vea [Ver archivos del registro sin conexión](view-offline-log-files.md).  
  
 El Visor del archivo de registros se puede abrir de varias maneras, dependiendo de la información que se desee ver.  
  
##  <a name="permissions"></a><a name="BeforeYouBegin"></a> Permisos  
 Para tener acceso a los archivos de registro en instancias de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en línea, se requiere pertenecer al rol fijo de servidor securityadmin.  
  
 Para tener acceso a los archivos de registro en instancias de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sin conexión, se debe tener acceso de lectura tanto al espacio de nombres WMI **Root\Microsoft\SqlServer\ComputerManagement10** como a la carpeta donde están almacenados los archivos de registro. Para obtener más información, vea la sección Seguridad del tema [Ver archivos del registro sin conexión](view-offline-log-files.md).  
  
### <a name="security"></a>Seguridad  
 Debe pertenecer al rol fijo de servidor securityadmin.  
  
### <a name="view-log-files"></a>Ver archivos de registro  
  
##### <a name="to-view-logs-that-are-related-to-general-sql-server-activity"></a>Para ver los registros relacionados con la actividad general de SQL Server  
  
1.  En el Explorador de objetos, expanda **Administración**.  
  
2.  Realice cualquiera de las siguientes acciones:  
  
    -   Haga clic con el botón derecho en **Registros de SQL Server**, seleccione **Ver**y, después, haga clic en **Registro de SQL Server** o **Registro de Windows y SQL Server**.  
  
    -   Expanda **Registros de SQL Server**, haga clic con el botón derecho en cualquier archivo de registro y, después, haga clic en **Ver registro de SQL Server**. También puede hacer doble clic en cualquier archivo de registro.  
  
     Los registros son **Correo electrónico de base de datos**, **SQL Server**, **Agente SQL Server**y **Windows NT**.  
  
##### <a name="to-view-logs-that-are-related-to-jobs"></a>Para ver los registros relacionados con los trabajos  
  
-   En el Explorador de objetos, expanda **Agente SQL Server**, haga clic con el botón derecho en **Trabajos**y, después, haga clic en **Ver historial**.  
  
     Los registros son **Correo electrónico de base de datos**, **Historial de trabajos**y **Agente SQL Server**.  
  
##### <a name="to-view-logs-that-are-related-to-maintenance-plans"></a>Para ver los registros relacionados con los planes de mantenimiento  
  
-   En el Explorador de objetos, expanda **Administración**, haga clic con el botón derecho en **Planes de mantenimiento**y, después, haga clic en **Ver historial**.  
  
     Los registros son **Correo electrónico de base de datos**, **Historial de trabajos**, **Planes de mantenimiento**, **Planes de mantenimiento remotos**y **Agente SQL Server**.  
  
##### <a name="to-view-logs-that-are-related-to-data-collection"></a>Para ver los registros relacionados con la recopilación de datos  
  
-   En el Explorador de objetos, expanda **Administración**, haga clic con el botón derecho en **Recopilación de datos**y, después, haga clic en **Ver registros**.  
  
     Los registros son **Recopilación de datos**, **Historial de trabajos**y **Agente SQL Server**.  
  
##### <a name="to-view-logs-that-are-related-to-database-mail"></a>Para ver los registros relacionados con Correo electrónico de base de datos  
  
-   En el Explorador de objetos, expanda **Administración**, haga clic con el botón derecho en **Correo electrónico de base de datos**y, después, haga clic en **Ver registro de Correo electrónico de base de datos**.  
  
     Los registros son **Correo electrónico de base de datos, Historial de trabajos**, **Planes de mantenimiento**, **Planes de mantenimiento remotos**, **SQL Server**, **Agente SQL Server**y **Windows NT**.  
  
##### <a name="to-view-logs-that-are-related-to-audits-collections"></a>Para ver los registros relacionados con las recopilaciones de auditorías  
  
-   En el Explorador de objetos, expanda **Seguridad**, expanda **Auditorías**, haga clic con el botón derecho en una auditoría y, después, haga clic en **Ver registros de auditoría**.  
  
     Los registros son **Recopilación de auditoría** y **Windows NT**.  
  
##### <a name="to-view-logs-that-are-related-to-audits-collections"></a>Para ver los registros relacionados con las recopilaciones de auditorías  
  
-   En el Explorador de objetos, expanda **Seguridad**, expanda **Auditorías**, haga clic con el botón derecho en una auditoría y, después, haga clic en **Ver registros de auditoría**.  
  
     Los registros son **Recopilación de auditoría** y **Windows NT**.  
  
## <a name="see-also"></a>Consulte también  
 [Visor de archivos de registro](log-file-viewer.md)   
 [SQL Server Audit &#40;motor de base de datos&#41;](../security/auditing/sql-server-audit-database-engine.md)   
 [Ver archivos del registro sin conexión](view-offline-log-files.md)  
  
  
