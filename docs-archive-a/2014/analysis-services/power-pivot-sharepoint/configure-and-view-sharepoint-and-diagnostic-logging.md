---
title: Configurar y ver los archivos de registro de SharePoint y el registro de diagnóstico (PowerPivot para SharePoint) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 85f62d29-cdc6-45b3-be1f-ff1182939858
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5c031614b0b55560c5b03b7235a6cc0a73023807
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676209"
---
# <a name="configure-and-view-sharepoint-log-files--and-diagnostic-logging-powerpivot-for-sharepoint"></a>Configurar y ver archivos de registro de SharePoint y el registro de diagnósticos (PowerPivot para SharePoint)
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] se graban en archivos de registro de SharePoint. Use la información de este tema para configurar los niveles de registro y ver la información del archivo de registro. Puede controlar qué eventos de servidor de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] se registran en el archivo. También puede controlar la gravedad de los mensajes que se registran. Para obtener más información, consulte [configurar la recopilación de datos de uso para &#40;PowerPivot para SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md).  
  
 En este tema:  
  
-   [Ubicación del archivo de registro](#bkmk_filelocation)  
  
-   [Modificar los niveles mínimos del registro de diagnóstico para categorías de eventos individuales](#bkmk_modifyloglevels)  
  
-   [Ver archivos de registro de SharePoint](#bkmk_how2viewlogfiles)  
  
##  <a name="log-file-location"></a><a name="bkmk_filelocation"></a>Ubicación del archivo de registro  
 De manera predeterminada, los archivos de registro de SharePoint se guardan en la ubicación siguiente:  
  
 `C:\Program files\Common Files\Microsoft Shared\Web Server Extensions\14\LOGS`  
  
 La carpeta LOGS contiene archivos de registro (`.log`), archivos de datos (`.txt`) y archivos de uso (`.usage`). La convención de nomenclatura de los archivos para un registro de seguimiento de SharePoint es el nombre del servidor seguido de una fecha y una marca de tiempo. Los registros de seguimiento de SharePoint se crean a intervalos normales y siempre que hay IISRESET. Es común tener muchos registros de seguimiento dentro de un período de 24 horas.  
  
##  <a name="modify-diagnostic-logging-levels-for-individual-event-categories"></a><a name="bkmk_modifyloglevels"></a>Modificar los niveles de registro de diagnóstico para categorías de eventos individuales  
 De forma predeterminada, el registro de ULS de eventos de PowerPivot se establece en *Mediano*. Este valor es nuevo en SQL Server 2012. Si actualizó un servidor de la versión anterior, el nivel de registro podría seguir establecido en *Detallado*, que es el predeterminado en SQL Server 2008 R2. Si está acostumbrado a revisar los registros de ULS para obtener información de uso del servidor PowerPivot, observará que, como resultado de este cambio, hay menos información sobre las operaciones del servidor PowerPivot.  
  
 Salvo por las excepciones, que son de tipo *Alta*, todos los mensajes de PowerPivot pertenecen a la categoría Detallado. Si desea registrar entradas para las operaciones rutinarias de servidor como las conexiones, solicitudes o informes de consulta, debe cambiar el nivel de registro a Detallado.  
  
 Para modificar los niveles mínimos del registro de diagnóstico para categorías de eventos individuales:  
  
1.  En Administración central de SharePoint, haga clic en **Supervisión**.  
  
2.  Haga clic en **Configurar registro de diagnósticos**.  
  
3.  Desplácese a **Servicio PowerPivot**.  
  
4.  Expanda la categoría y seleccione categorías individuales.  
  
     **Solicitud de página de aplicación** especifica los eventos desencadenados por la aplicación de servicio al localizar un [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] para cargar un origen de datos PowerPivot y comunicarse con otros servidores de la granja.  
  
     **Procesamiento de solicitudes** especifica los eventos que desencadenan las solicitudes de consultas a un origen de datos PowerPivot cargado en un servidor de la granja.  
  
     **Uso** especifica un evento relacionado con la recopilación de datos de uso de PowerPivot.  
  
5.  En el evento menos crítico para notificar al registro de eventos, seleccione **Ninguno** para deshabilitar el registro de eventos para la categoría o **Error** para limitar el registro solo a los errores.  
  
6.  Seleccione **Detallado** para registrar todos los eventos en el registro de eventos.  
  
7.  En el evento menos crítico para notificar al registro de seguimiento, seleccione **Ninguno** para deshabilitar el seguimiento de la categoría o **Error** para limitar el seguimiento solo a los errores.  
  
8.  Seleccione **Detallado** para registrar todos los eventos en el registro de seguimiento.  
  
9. Haga clic en **OK**.  
  
##  <a name="how-to-view-sharepoint-log-files"></a><a name="bkmk_how2viewlogfiles"></a>Cómo ver los archivos de registro de SharePoint  
 Los archivos de registro son archivos de texto. Puede abrirlos en cualquier editor de texto. También puede utilizar aplicaciones de visor de registros de otros fabricantes.  
  
#### <a name="use-a-text-editor"></a>Utilizar un editor de texto  
 Si está utilizando un editor de texto para solucionar el problema de un error de servidor de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , las siguientes sugerencias pueden ayudarle a buscar la información pertinente en el archivo:  
  
-   En el caso de los errores relacionados con la publicación, visualización o actualización de un libro de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , busque el nombre del libro en el archivo de registro.  
  
-   En el caso de los errores que proporcionan un identificador de correlación, cópielo y utilícelo como término de búsqueda en el archivo de registro.  
  
-   Busque el estado del error "High" o "Exception". Busque "servicio PowerPivot".  
  
-   Si sabe cuándo se produjo el error, utilice la información de fecha y hora para restringir el ámbito de entradas por las que debe desplazarse.  
  
#### <a name="use-a-log-viewer-application"></a>Utilizar una aplicación de visor de registros  
 Aunque puede utilizar un editor de texto para ver los registros de seguimiento individualmente, una aplicación de visor de registros que le permita ver varios archivos de registro juntos puede resultar mucho más útil. Afortunadamente, hay disponibles varias aplicaciones de visor de registros de otros fabricantes para descargarse en el sitio de Codeplex que pueden ayudarle a ver varios registros de seguimiento en una sola área de trabajo.  
  
 Las siguientes instrucciones incluyen vínculos a visores de registros ULS de SharePoint frecuentes que puede descargar de Codeplex.  
  
1.  Vaya a [SharePoint LogViewer](http://sharepointlogviewer.codeplex.com) o [SharePoint ULS Log Viewer](https://go.microsoft.com/fwlink/?LinkId=150052) en el sitio de Codeplex.  
  
2.  Haga clic en la pestaña **Downloads** .  
  
3.  Haga clic en el archivo ejecutable. Será **SharePointLogViewer.exe** o **ULS Viewer 2.0 Binary**.  
  
4.  Lea y acepte las condiciones de licencia.  
  
5.  Haga clic en **Guardar** para descargar el software en el sistema local.  
  
     Si va a descargar el visor de registros ULS de SharePoint, guarde ULSViewer.zip en la carpeta Descargas.  
  
6.  En la carpeta Descargas, haga clic con el botón derecho en ULSViewer.zip y seleccione **Extraer todo**.  
  
7.  Especifique una carpeta de destino y, a continuación, haga clic en **Extraer**.  
  
8.  En la carpeta que contiene los archivos de programa extraídos, haga doble clic en **ULSViewer** y ejecute la aplicación.  
  
9. Haga clic en el icono de carpeta en la esquina superior izquierda de la ventana de la aplicación.  
  
10. Busque \Archivos de programa\Archivos comunes\Microsoft Shared\Web Server Extensions\14\Logs.  
  
11. Seleccione uno o más registros de seguimiento. De forma predeterminada, los nombres de archivo del registro de seguimiento están compuestos del nombre de equipo más información de fecha y hora. El tipo de archivo es Documento de texto.  
  
12. Haga clic en **Abrir** y espere a que los archivos se carguen.  
  
13. Utilice los filtros integrados para seleccionar los registros en función de la gravedad, proceso, categoría o un archivo de texto definido por el usuario. También puede hacer clic en los encabezados de columna para cambiar el criterio de ordenación.  
  
#### <a name="entries-for-powerpivot-services"></a>Entradas para los servicios PowerPivot  
 En la tabla siguiente se describen las entradas para las operaciones de servidor de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] que es probable que se encuentren en un archivo de registro de SharePoint.  
  
|Proceso|Área|Category|Nivel|Message|Detalles|  
|-------------|----------|--------------|-----------|-------------|-------------|  
|w3wp.exe|Servicio PowerPivot|Uso|Verbose|No hay ninguna estadística de solicitudes actuales, nada para registrar.|En los intervalos predefinidos, el servicio notifica las estadísticas de respuesta de las consultas como un evento de uso al sistema de recopilación de datos de uso. Este mensaje indica que no hubo ninguna estadística de consulta que notificar.|  
|w3wp.exe|Servicio PowerPivot|Front end web|Verbose|Empezar a buscar un servidor de aplicaciones para el origen de datos =\<*path*>|Cuando se recibe una solicitud de conexión, el servicio de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] identifica un [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] disponible para administrar la solicitud. Si hay solo un servidor en la granja, el servidor local acepta la solicitud en todos los casos.|  
|w3wp.exe|Servicio PowerPivot|Front end web|Verbose|La búsqueda del servidor de aplicaciones tuvo éxito.|La solicitud se asignó a una aplicación de servicio de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .|  
|w3wp.exe|Servicio PowerPivot|Front end web|Verbose|Redireccionar la solicitud para \<*PowerPivotdata source*> al [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] .|La solicitud se reenvió al [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)].|  
|w3wp.exe|Servicio PowerPivot|Procesamiento de solicitudes|Verbose|Redireccionar la solicitud para el nombre de usuario \<*SharePoint user*> a la base de datos|Una conexión suplantada con el origen de datos de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] se creó en nombre del usuario de SharePoint.|  
  
## <a name="see-also"></a>Consulte también  
 [Recopilación de datos de uso de PowerPivot](power-pivot-usage-data-collection.md)   
 [Ver y leer los archivos de registro de instalación de SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)   
 [Configurar la recopilación de datos de uso para &#40;PowerPivot para SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)  
  
  
