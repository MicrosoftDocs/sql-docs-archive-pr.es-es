---
title: Activar o desactivar las características de Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, configuration
- security [Reporting Services], strategies
ms.assetid: b69db02a-43a7-4fdc-ad9b-438d817a7f83
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f56f9984b5b02431db23b782652e5575af557bdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672615"
---
# <a name="turn-reporting-services-features-on-or-off"></a>Activar o desactivar las características de Reporting Services
  Puede desactivar características del servidor de informes que no use como parte de una estrategia de bloqueo para reducir la superficie de ataque de un servidor de informes de producción. En la mayoría de los casos, le interesará ejecutar las características de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] simultáneamente para poder hacer uso de toda la funcionalidad de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Sin embargo, dependiendo del modelo de implementación, puede deshabilitar aquellas características que no necesite. Por ejemplo, si todo el procesamiento de informes está configurado como operaciones programadas, puede habilitar solo el procesamiento en segundo plano. Del mismo modo, puede ejecutar simplemente el servicio web del servidor de informes si solo desea informes a petición e interactivos.  
  
 En los procedimientos de este tema, se muestra cómo desactivar características de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en modo nativo. Las características se pueden configurar de varias maneras: editando directamente el archivo `RsReportServer.config` o con la faceta **Configuración de área expuesta para Reporting Services** de la administración basada en directivas de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Use los vínculos para buscar el procedimiento o los procedimientos en los que se explica cómo activar o desactivar una característica:  
  
-   [Servicio Web del servidor de informes](#RSWebSvc)  
  
-   [Eventos y procesamiento programados](#Sched)  
  
-   [Administrador de informes](#ReportManager)  
  
-   [Generador de informes](#ReportBuilder)  
  
-   [Seguridad integrada de Windows para orígenes de datos de informe](#WinIntSec)  
  
##  <a name="report-server-web-service"></a><a name="RSWebSvc"></a>Servicio Web del servidor de informes  
  
#### <a name="to-turn-on-or-off-the-report-server-web-service-by-editing-configuration"></a>Para activar o desactivar el servicio web del servidor de informes editando la configuración  
  
1.  Abra el archivo `RsReportServer.config` en un editor de texto. Para más información, vea [Modificar un archivo de configuración de Reporting Services &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md) en los Libros en pantalla de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Para activar el servicio web del servidor de informes, establezca `IsWebServiceEnabled` en `true`:  
  
    ```  
    <IsWebServiceEnabled>true</IsWebServiceEnabled>  
    ```  
  
3.  Para desactivar el servicio web del servidor de informes, establezca `IsWebServiceEnabled` en `false`:  
  
    ```  
    <IsWebServiceEnabled>false</IsWebServiceEnabled>  
    ```  
  
4.  Guarde los cambios y, a continuación, cierre el archivo.  
  
#### <a name="to-turn-on-or-off-the-report-server-web-service-by-using-sql-server-management-studio"></a>Para activar o desactivar el servicio web del servidor de informes con SQL Server Management Studio  
  
1.  Abra [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] y conéctese a la instancia de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] que desea configurar.  
  
2.  En Explorador de objetos, haga clic con el botón secundario en el [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nodo, seleccione **directivas**y haga clic en **aspectos**.  
  
3.  En la lista **Faceta** , seleccione **Configuración de área expuesta para Reporting Services**.  
  
4.  En **Propiedades de faceta**:  
  
    -   Para activar el servicio Web del servidor de informes, establezca **WebServiceAndHTTPAccessEnabled** en `True` .  
  
    -   Para desactivar el servicio Web del servidor de informes, establezca **WebServiceAndHTTPAccessEnabled** en `False` .  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="scheduled-events-and-delivery"></a><a name="Sched"></a> Eventos programados y entrega programada  
  
#### <a name="to-turn-on-or-off-scheduled-events-and-delivery-by-editing-configuration"></a>Para activar o desactivar los eventos programados y la entrega programada editando la configuración  
  
1.  Abra el archivo RsReportServer.config en un editor de texto. Para más información, vea [Modificar un archivo de configuración de Reporting Services &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md) en los Libros en pantalla de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Para activar el procesamiento y la entrega de informes programados, establezca `IsSchedulingService`, `IsNotificationService` e `IsEventService` en `true`:  
  
    ```  
    <IsSchedulingService>true</IsSchedulingService>  
    <IsNotificationService>true</IsNotificationService>  
    <IsEventService>true</IsEventService>  
    ```  
  
3.  Para desactivar el procesamiento y la entrega de informes programados, establezca `IsSchedulingService`, `IsNotificationService` e `IsEventService` en `false`:  
  
    ```  
    <IsSchedulingService>false</IsSchedulingService>  
    <IsNotificationService>false</IsNotificationService>  
    <IsEventService>false</IsEventService>  
    ```  
  
4.  Guarde los cambios y, a continuación, cierre el archivo.  
  
> [!NOTE]  
>  No puede desactivar completamente ningún procesamiento en segundo plano porque proporciona la funcionalidad de mantenimiento de las bases de datos que se requiere para las operaciones de servidor.  
  
#### <a name="to-turn-on-or-off-scheduled-events-and-delivery-by-using-sql-server-management-studio"></a>Para activar o desactivar los eventos programados y la entrega programada con SQL Server Management Studio  
  
1.  Abra [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] y conéctese a la instancia de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] que desea configurar.  
  
2.  En Explorador de objetos, haga clic con el botón secundario en el [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nodo, seleccione **directivas**y haga clic en **aspectos**.  
  
3.  En la lista **Faceta** , seleccione **Configuración de área expuesta para Reporting Services**.  
  
4.  En **Propiedades de faceta**:  
  
    -   Para activar los eventos programados y la entrega, establezca **ScheduleEventsAndReportDeliveryEnabled** en `True` .  
  
    -   Para desactivar los eventos programados y la entrega, establezca **ScheduleEventsAndReportDeliveryEnabled** en `False` .  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  No puede desactivar completamente ningún procesamiento en segundo plano porque proporciona la funcionalidad de mantenimiento de las bases de datos que se requiere para las operaciones de servidor.  
  
##  <a name="report-manager"></a><a name="ReportManager"></a>Administrador de informes  
  
#### <a name="to-turn-on-or-off-report-manager-by-editing-configuration"></a>Para activar o desactivar el Administrador de informes editando la configuración  
  
1.  Abra el archivo RsReportServer.config en un editor de texto. Para obtener instrucciones , vea [Modificar un archivo de configuración de Reporting Services &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md) en los Libros en pantalla de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Para activar el Administrador de informes, establezca `IsReportManagerEnabled` en `true`:  
  
    ```  
    <IsReportManagerEnabled>true</IsReportManagerEnabled>  
    ```  
  
3.  Para desactivar el Administrador de informes, establezca `IsReportManagerEnabled` en `false`:  
  
    ```  
    <IsReportManagerEnabled>false</IsReportManagerEnabled>  
    ```  
  
4.  Guarde los cambios y, a continuación, cierre el archivo.  
  
#### <a name="to-turn-on-or-off-report-manager-by-using-sql-server-management-studio"></a>Para activar o desactivar el Administrador de informes con SQL Server Management Studio  
  
1.  Abra [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] y conéctese a la instancia de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] que desea configurar.  
  
2.  En el **Explorador de objetos**, haga clic con el botón derecho en el nodo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , seleccione **Directivas**y, después, haga clic en **Facetas**.  
  
3.  En la lista **Faceta** , seleccione **Configuración de área expuesta para Reporting Services**.  
  
4.  En **Propiedades de faceta**:  
  
    -   Para activar Administrador de informes, establezca **ReportManagerEnabled** en `True` .  
  
    -   Para desactivar Administrador de informes, establezca **ReportManagerEnabled** en `False` .  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="report-builder"></a>Generador de informes de <a name="ReportBuilder"></a>  
  
#### <a name="to-turn-on-or-off-report-builder-by-using-sql-server-management-studio"></a>Para activar o desactivar el Generador de informes con SQL Server Management Studio  
  
1.  Abra [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] y conéctese a la instancia de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] que desea configurar.  
  
2.  En el Explorador de objetos, haga clic con el botón derecho en el nodo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] y, después, haga clic en **Propiedades**.  
  
3.  En el cuadro de diálogo **Propiedades del servidor** , en **Seleccionar una página**, haga clic en **Seguridad**.  
  
    -   Para activar el Generador de informes, seleccione la opción **Habilitar ejecuciones de notificaciones ad hoc** .  
  
    -   Para desactivar el Generador de informes, anule la selección de la opción **Habilitar ejecuciones de notificaciones ad hoc** .  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="windows-integrated-security"></a><a name="WinIntSec"></a> Seguridad integrada de Windows  
  
#### <a name="to-turn-on-or-off-windows-integrated-security-by-using-sql-server-management-studio"></a>Para activar o desactivar la seguridad integrada de Windows con SQL Server Management Studio  
  
1.  Abra [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] y conéctese a la instancia de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] que desea configurar.  
  
2.  En el Explorador de objetos, haga clic con el botón derecho en el nodo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] y, después, haga clic en **Propiedades**.  
  
3.  En el cuadro de diálogo **Propiedades del servidor** , en **Seleccionar una página**, haga clic en **Seguridad**.  
  
    -   Para activar la seguridad integrada de Windows, seleccione la opción **Habilitar la seguridad integrada de Windows para los orígenes de datos de informes** .  
  
    -   Para desactivar la seguridad integrada de Windows, anule la selección de la opción **Habilitar la seguridad integrada de Windows para los orígenes de datos de informes** .  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Consulte también  
 [Administrador de configuración de Reporting Services &#40;modo nativo&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
