---
title: Referencia de parámetros de acceso URL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], display options
- URL access [Reporting Services], report display parameters
ms.assetid: 1c3e680a-83ea-4979-8e79-fa2337ae12a3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c33fdd163ed2bfb02daffee6f938a7f85e025fc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87671353"
---
# <a name="url-access-parameter-reference"></a>Referencia de parámetros de acceso URL
  Puede utilizar los parámetros siguientes como parte de una dirección URL para configurar la apariencia de los informes. En esta sección se enumeran los parámetros más comunes. Los parámetros distinguen entre mayúsculas y minúsculas y empiezan con el prefijo de parámetro *rs:* si se dirige al servidor de informes y *rc:* si se dirige a un Visor HTML. También puede especificar parámetros que son específicos de dispositivos o extensiones de representación. Para obtener más información sobre parámetros específicos del dispositivo, vea [Especificar la configuración de la información del dispositivo en una dirección URL](specify-device-information-settings-in-a-url.md).  
  
> [!IMPORTANT]  
>  Es importante que la dirección URL incluya la sintaxis de proxy de `_vti_bin` para enrutar la solicitud a través de SharePoint y el proxy HTTP de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . El proxy agrega algún contexto a la solicitud HTTP, contexto que es necesario para garantizar la correcta ejecución del informe para los servidores de informes de modo de SharePoint. Para obtener ejemplos, vea [Access Report Server Items Using URL Access](access-report-server-items-using-url-access.md).  
>   
>  Para obtener información sobre cómo incluir parámetros de informe en una dirección URL y algunos ejemplos, vea [Pass a Report Parameter Within a URL](pass-a-report-parameter-within-a-url.md).  
  
## <a name="html-viewer-commands-rc"></a>Comandos del Visor HTML (rc:)  
 En la tabla siguiente se describen los parámetros de acceso URL que tienen el prefijo *RC:* y que se usan para tener como destino el visor HTML.  
  
|Parámetro|Descripción|Valores|  
|---------------|-----------------|------------|  
|*Barra de herramientas*|Muestra u oculta la barra de herramientas.<br /><br /> ** \* \* Importante \* RC \* ** *: la barra de herramientas* no = `false` funciona para las cadenas de acceso URL que usan una dirección IP, en lugar de un nombre de dominio, para el destino de un informe hospedado en un sitio de SharePoint.|Si el valor de este parámetro es `false`, se omiten todas las opciones restantes. Si omite este parámetro, la barra de herramientas se muestra automáticamente para los formatos de representación que lo admiten. El valor predeterminado de este parámetro es `true`.<br /><br /> `true` <br /> `false`|  
|*Parámetros*|Muestra u oculta el área de parámetros de la barra de herramientas.<br /><br /> `Native`ejemplo de modo:<br /><br /> `http://myrshost/reportserver?/Sales&rc:Parameters=Collapsed`<br /><br /> `SharePoint`ejemplo de modo:<br /><br /> `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales&rc:Parameters=Collapsed`|Si establece este parámetro en `true` , se muestra el área de parámetros de la barra de herramientas. Si establece este parámetro en `false`, el área de parámetros no se muestra y no puede ser mostrada por el usuario. Si establece este parámetro en un valor de `Collapsed`, no se mostrará el área de parámetros, pero el usuario final puede alternarla. El valor predeterminado de este parámetro es `true`. Los valores válidos son:<br /><br /> `true` <br /> `false` <br /> `Collapsed`|  
|*Zoom*|Establece el valor de ampliación del informe como porcentaje entero o una constante de cadena.<br /><br /> `Native`ejemplo de modo:<br /><br /> `http://myrshost/reportserver?/Sales&rc:Zoom=Page Width`<br /><br /> `SharePoint`ejemplo de modo:<br /><br /> `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales&rc:Zoom=Page Width`|Los valores de cadena estándar incluyen `Page Width` y `Whole Page`. Las versiones de Internet Explorer anteriores a Internet Explorer 5.0 y todos los exploradores que no son de[!INCLUDE[msCoName](../includes/msconame-md.md)] omiten este parámetro. El valor predeterminado de este parámetro es `100`.|  
|*Sección*|Establece la página del informe que se mostrará.<br /><br /> `Native`ejemplo de modo para mostrar la página 2 del informe:<br /><br /> `http://myrshost/reportserver?/Sales&rc:Section=2`<br /><br /> `SharePoint`ejemplo de modo para mostrar la página 2 del informe:<br /><br /> `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales&rc:Section=2`|Cualquier valor que sea mayor que el número de páginas en el informe muestra la última página. Cualquier valor que sea menor que `0` muestra la página 1 del informe. El valor predeterminado de este parámetro es `1`.|  
|*FindString*|Busca en un informe un conjunto específico de texto.<br /><br /> `Native`ejemplo de modo:<br /><br /> `http://myrshost/reportserver?/Sales&rc:FindString=Mountain-400`<br /><br /> `SharePoint`ejemplo de modo:<br /><br /> `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales&rc:FindString=Mountain-400`||  
|*StartFind*|Especifica la última sección en que se buscará.<br /><br /> `Native`ejemplo de modo que busca la primera aparición del texto "Mountain-400" en el informe de ejemplo Product catalog, empezando por la página uno y terminando por la página cinco:<br /><br /> `http://server/Reportserver?/SampleReports/Product Catalog&rs:Command=Render&rc:StartFind=1&rc:EndFind=5&rc:FindString=Mountain-400`|El valor predeterminado de este parámetro es la última página del informe.|  
|*EndFind*|Establece el número de la última página que se utilizará en la búsqueda. Por ejemplo, un valor de `5` indica que la última página que se va a buscar es la página 5 del informe. Utilice este parámetro junto con el parámetro *StartFind* . Vea el ejemplo anterior para *StartFind* .|El valor predeterminado es el número de la página actual.|  
|*FallbackPage*|Establece el número de la página que se mostrará si se produce un error en una búsqueda o en una selección de mapa del documento.|El valor predeterminado es el número de la página actual.|  
|*GetImage*|Obtiene un icono determinado para la interfaz de usuario del Visor HTML.||  
|*Iconos*|Obtiene el icono de una extensión de representación determinada.||  
|*Hoja de estilos*|Especifica una hoja de estilos que se va a aplicar al Visor HTML.||  
|Configuración de la información del dispositivo|especifica una configuración de información del dispositivo en forma de `rc:tag=value`, donde *tag* es el nombre de la configuración de información de un dispositivo concreto para la extensión de representación que se usa actualmente (consulte la descripción del parámetro *Format*). Por ejemplo, puede usar la configuración de información del dispositivo *OutputFormat* para que la extensión de representación IMAGE represente el informe en imágenes JPEG con los siguientes parámetros en la cadena de acceso URL: `...&rs:Format=IMAGE&rc:OutputFormat=JPEG`. Para obtener más información sobre toda la configuración de información del dispositivo específica de la extensión, vea [Configuración de información de dispositivos para las extensiones de representación &#40;Reporting Services&#41;](device-information-settings-for-rendering-extensions-reporting-services.md).||  
  
## <a name="report-server-commands-rs"></a>Comandos del servidor de informes (rs:)  
 En la tabla siguiente se describen los parámetros de acceso URL que tienen el prefijo *RS:* y que se usan para establecer como destino el servidor de informes.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|*Comando*|Realiza una acción en un elemento de catálogo, según el tipo de elemento. El valor predeterminado se determina mediante el tipo de elemento de catálogo al que se hace referencia en la cadena de acceso URL. Los valores válidos son:<br /><br /> `ListChildren`y `GetChildren` muestra el contenido de una carpeta. Los elementos de carpeta se muestran dentro de una página genérica de navegación por elementos.<br /><br /> `Native`ejemplo de modo:<br /><br /> `http://myrshost/reportserver?/Sales&rs:Command=GetChildren`<br /><br /> `SharePoint`ejemplo de modo:<br /><br /> `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales&rs:Command=GetChildren`|  
||`Render`Representa el informe especificado.<br /><br /> `Native`ejemplo de modo:<br /><br /> `http://myrshost/reportserver?/Sales/YearlySalesByCategory&rs:Command=Render`<br /><br /> `SharePoint`ejemplo de modo:<br /><br /> `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/YearlySalesByCategory&rs:Command=Render`|  
||`GetSharedDatasetDefinition`Muestra la definición XML asociada a un conjunto de DataSet compartido. Las propiedades del conjunto de datos compartido, incluidos la consulta, los parámetros del conjunto de datos, los valores predeterminados, los filtros del conjunto de datos y opciones de datos como la intercalación y la distinción entre mayúsculas y minúsculas, se guardan en la definición. Para usar este valor, debe tener el permiso para **leer definición de informe** en un conjunto de datos compartido.<br /><br /> `Native`ejemplo de modo:<br /><br /> `http://localhost/reportserver/?/DataSet1&rs:command=GetShareddatasetDefinition`|  
||`GetDataSourceContents`Muestra las propiedades de un origen de datos compartido determinado como XML. Si el explorador admite código XML y es un usuario autenticado con el permiso `Read Contents` en el origen de datos, se muestra la definición del origen de datos.<br /><br /> `Native`ejemplo de modo:<br /><br /> `http://myrshost/reportserver?/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`<br /><br /> `SharePoint`ejemplo de modo:<br /><br /> `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`|  
||`GetResourceContents`Representa un recurso y lo muestra en una página HTML si el recurso es compatible con el explorador. De lo contrario, le preguntarán si desea abrir o guardar el archivo o recurso en el disco.<br /><br /> `Native`ejemplo de modo:<br /><br /> `http://myrshost/reportserver?/Sales/StorePicture&rs:Command=GetResourceContents`<br /><br /> `SharePoint`ejemplo de modo:<br /><br /> `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/StorePicture.jpg&rs:Command=GetResourceContents`|  
||`GetComponentDefinition`Muestra la definición XML asociada a un elemento de informe publicado. `Read Contents`Para usar este valor, debe tener el permiso en un elemento de informe publicado.|  
|*Formato*|Especifica el formato en el que se representará un informe. Los valores habituales son `ATOM`, `HTML4.0`, `MHTML`, `IMAGE`, `EXCEL`, `WORD`, `CSV`, `PDF`, `XML`. El valor predeterminado es `HTML4.0`. Para obtener más información, consulte [Export a Report Using URL Access](export-a-report-using-url-access.md).<br /><br /> Por ejemplo, para obtener una copia PDF de un informe directamente desde un servidor de informes en modo `Native`.<br /><br /> `http://myrshost/ReportServer?/myreport&rs:Format=PDF`<br /><br /> Por ejemplo, en `SharePoint` modo.<br /><br /> `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/myrereport.rdl&rs:Format=PDF`|  
|*ParameterLanguage*|Proporciona un idioma para los parámetros pasados en una dirección URL que es independiente del idioma del explorador. El valor predeterminado es el idioma del explorador. El valor puede ser un valor de referencia cultural, como `en-us` o `de-de.`<br /><br /> Por ejemplo en modo `Native`, para invalidar el idioma del explorador y especificar un valor de referencia cultural de-DE.<br /><br /> `http://myrshost/Reportserver?/SampleReports/Product+Line+Sales&rs:Command=Render&StartDate=4/10/2008&EndDate=11/10/2008&rs:ParameterLanguage=de-DE`|  
|*Instantánea*|Representa un informe basándose en una instantánea del historial de informes. Para obtener más información, vea [Representar instantáneas del historial de informes mediante acceso URL](render-a-report-history-snapshot-using-url-access.md).<br /><br /> Por ejemplo en modo `Native`, recupera una instantánea del historial de informes con fecha 2003-04-07 con una marca de tiempo de 13:40: 02.<br /><br /> `http://myrshost/reportserver?/SampleReports/Company Sales&rs:Snapshot=2003-04-07T13:40:02`|  
|*PersistStreams*|Representa un informe en un flujo almacenado único. El procesador de imagen utiliza este parámetro para transmitir el informe representado fragmento por fragmento. Después de utilizar este parámetro en una cadena de acceso de dirección URL, utilice la misma cadena de acceso de dirección URL con el parámetro *GetNextStream* en lugar del parámetro *PersistStreams* para obtener el fragmento siguiente en el flujo almacenado. Este comando de dirección URL devolverá a la larga un flujo de cero bytes para indicar el fin del flujo almacenado. El valor predeterminado es `false`.|  
|*GetNextStream*|Obtiene el siguiente grupo de datos en una transmisión persistente a la que se tiene acceso con el parámetro *PersistStreams* . Para obtener más información, vea la descripción de *PersistStreams*. El valor predeterminado es `false`.|  
|*SessionID*|Especifica una sesión de informe activa establecida entre la aplicación cliente y el servidor de informes. El valor de este parámetro se establece en el identificador de la sesión.<br /><br /> Puede especificar el identificador de sesión como una cookie o como parte de la dirección URL. Cuando el servidor de informes se ha configurado para no usar las cookies de sesión, la primera solicitud sin un identificador de sesión especificado resulta en una redirección con un identificador de sesión. Para obtener más información sobre las sesiones del servidor de informes, vea [Identifying Execution State](report-server-web-service-net-framework-soap-headers/identifying-execution-state.md).|  
|*ClearSession*|Un valor de `true` indica al servidor de informes que quite un informe de la sesión de informe. Todas las instancias del informe asociadas a un usuario autenticado se quitan de la sesión de informe. (Una instancia de informe se define como el mismo informe ejecutado varias veces con diferentes valores de parámetro de informe). El valor predeterminado es `false` .|  
|*ResetSession*|Un valor de `true` indica al servidor de informes que restablezca la sesión del informe y que quite la asociación de la sesión del informe con todas las instantáneas de informe. El valor predeterminado es `false`.|  
|*ShowHideToggle*|Alterna el estado de mostrar u ocultar de una sección del informe. Especifique un entero positivo para representar la sección que desea alternar.|  
  
## <a name="report-viewer-web-part-commands-rv"></a>Comandos de elemento web del visor de informes (rv:)  
 En la tabla siguiente se describen los nombres de parámetros de informes reservados de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] que se usan para tener como destino el elemento web del visor de informes cuando se integra con SharePoint. Estos nombres de parámetro tienen como prefijo *rv:*. El elemento web del visor de informes también acepta el parámetro *rs:ParameterLanguage* .  
  
|Parámetro|Acción|  
|---------------|------------|  
|*Barra de herramientas*|Controla la presentación de la barra de herramientas para el elemento web del visor de informes. El valor predeterminado es `Full`. Los valores pueden ser:<br /><br /> `Full`: muestra la barra de herramientas completa.<br /><br /> `Navigation`: solamente muestra la paginación en la barra de herramientas.<br /><br /> `None`: no muestra la barra de herramientas.<br /><br /> <br /><br /> Por ejemplo, en modo de `SharePoint`, para mostrar solamente la paginación en la barra de herramientas.<br /><br /> `http://myspsite/_vti_bin/reportserver?http://myspsite002%fShared+Documents%2fmyreport.rdl&rv:DocMapMode=Displayed&rv:Toolbar=Navigation`|  
|*HeaderArea*|Controla la presentación del encabezado para el elemento web del visor de informes. El valor predeterminado es `Full`. Los valores pueden ser:<br /><br /> `Full`: muestra el encabezado completo.<br /><br /> `BreadCrumbsOnly`: muestra solamente la navegación detallada en el encabezado para informar al usuario de dónde se encuentra en la aplicación.<br /><br /> `None`: no muestra el encabezado.<br /><br /> <br /><br /> Por ejemplo, en modo de `SharePoint`, para mostrar solamente la navegación detallada en el encabezado.<br /><br /> `http://myspsite/_vti_bin/reportserver?http://myspsite002%fShared+Documents%2fmyreport.rdl&rv:DocMapMode=Displayed&rv:HeaderArea=BreadCrumbsOnly`|  
|*DocMapAreaWidth*|Controla el ancho de la presentación, en píxeles, del área de parámetro en el elemento web del visor de informes. El valor predeterminado es igual que el valor predeterminado del elemento web del visor de informes. Debe ser un número entero no negativo.|  
|*AsyncRender*|Controla si se representa un informe de forma asincrónica. El valor predeterminado es `true`, que especifica que un informe se representa de forma asincrónica. El valor debe ser un valor booleano de `true` o `false`.|  
|*ParamMode*|controla cómo se muestra el área de mensajes de parámetros del elemento web del Visor de informes en la vista de página completa.  El valor predeterminado es `Full`. Los valores válidos son:<br /><br /> `Full`: muestra el área de mensajes de parámetros.<br /><br /> `Collapsed`: contrae el área de mensajes de parámetros.<br /><br /> `Hidden`: oculta el área de mensajes de parámetros.<br /><br /> Por ejemplo, en modo de `SharePoint`, para ocultar el área de mensajes de parámetros.<br /><br /> `http://myspsite/_vti_bin/reportserver?http://myspsite002%fShared+Documents%2fmyreport.rdl&rv:DocMapMode=Displayed&rv:ParamMode=Collapsed`|  
|*DocMapMode*|controla cómo se muestra el área de mapa de documento del elemento web del Visor de informes en la vista de página completa. El valor predeterminado es `Full`. Los valores válidos son:<br /><br /> `Full`: muestra el área de mapa del documento.<br /><br /> `Collapsed`: contrae el área de mapa del documento.<br /><br /> `Hidden`: oculta el área de mapa del documento.|  
|*DockToolBar*|controla si la barra de herramientas del elemento web del Visor de informes está acoplada a la parte superior o inferior. Los valores válidos son `Top` y `Bottom`. El valor predeterminado es `Top`.<br /><br /> <br /><br /> Por ejemplo, en modo de `SharePoint`, para acoplar la barra de herramientas a la parte inferior.<br /><br /> `http://myspsite/_vti_bin/reportserver?http://myspsite002%fShared+Documents%2fmyreport.rdl&rv:DocMapMode=Displayed&rv:DockToolBar=Bottom`|  
|*ToolBarItemsDisplayMode*|Controla qué elementos de la barra de herramientas se muestran. Es un valor de enumeración bit a bit. Para incluir un elemento de la barra de herramientas, agregue el valor del elemento al valor total. Por ejemplo: para un menú Acciones, use rv:ToolBarItemsDisplayMode=63 (o 0x3F), que es 1+2+4+8+16+32; solo para los elementos del menú Acciones, use rv:ToolBarItemsDisplayMode=960 (o 0x3C0).  El valor predeterminado es `-1`, que incluye todos los elementos de la barra de herramientas. Los valores válidos son:<br /><br /> 1 (0x1): el botón **Atrás**<br /><br /> 2 (0x2): los controles de búsqueda de texto<br /><br /> 4 (0x4): los controles de navegación de páginas<br /><br /> 8 (0x8): el botón **Actualizar**<br /><br /> 16 (0x10): el cuadro de lista **Zoom**<br /><br /> 32 (0x20): el botón **Fuente Atom**<br /><br /> 64 (0x40): la opción de menú **Imprimir** del menú **Acciones**<br /><br /> 128 (0x80): el submenú **Exportar** del menú **Acciones**<br /><br /> 256 (0x100: la opción de menú **Abrir con el Generador de informes** del menú **Acciones**<br /><br /> 512 (0x200: la opción de menú **Suscribir** del menú **Acciones**<br /><br /> 1024 (0x400: la opción de menú **Nueva alerta de datos** del menú **Acciones**<br /><br /> Por ejemplo, en `SharePoint` modo para mostrar solo el botón **atrás** , controles de búsqueda de texto, controles de navegación de páginas y el botón **Actualizar** .<br /><br /> `http://myspsite/_vti_bin/reportserver?http://myspsite002%fShared+Documents%2fmyreport.rdl&rv:DocMapMode=Displayed&rv:ToolBarItemsDisplayMode=15`|  
  
## <a name="see-also"></a>Consulte también  
 [Acceso URL &#40;SSRS&#41;](url-access-ssrs.md)  
  
  