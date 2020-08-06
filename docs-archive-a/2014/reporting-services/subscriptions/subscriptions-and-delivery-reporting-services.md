---
title: Suscripciones y entrega (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], report distribution
- reports [Reporting Services], distributing
- distributing reports [Reporting Services]
- published reports [Reporting Services], distributing
- sending reports
- sharing reports
- delivering reports [Reporting Services]
- distributing reports [Reporting Services], subscriptions
- subscriptions [Reporting Services], about subscriptions
- subscriptions [Reporting Services]
ms.assetid: be7ec052-28e2-4558-bc09-8479e5082926
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ace7978af1d8a400e4353a64c2541d8a0a029004
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87749027"
---
# <a name="subscriptions-and-delivery-reporting-services"></a>Suscripciones y entrega (Reporting Services)
  Una suscripción [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] es una configuración que entrega un informe a una hora concreta o a raíz de un evento. Lo hace en el formato de archivo que se especifique. Por ejemplo, todos los miércoles, se guarda el informe VentasMensuales en formato de documento Microsoft Word en un recurso compartido de archivos. Las suscripciones se pueden utilizar para programar y automatizar la entrega de un informe con un conjunto concreto de valores de parámetros de informes.

 Puede crear varias suscripciones para un único informe a fin de cambiar las opciones de suscripción; por ejemplo, puede especificar diferentes valores de parámetros para producir tres versiones de un informe: un informe de ventas para la región occidental, otro para la región oriental y otro de todas las ventas.

 ![ejemplo de flujo de suscripción de SSRS](../media/ssrs-subscription-example-flow.png "ejemplo de flujo de suscripción de SSRS")

 Las suscripciones no están disponibles en todas las ediciones de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Para obtener una lista de las características admitidas por las ediciones de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vea [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).

> [!NOTE]
>  A partir de [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] , puede transferir la propiedad de una suscripción mediante programación. No hay ninguna interfaz de usuario que pueda utilizar para transferir la propiedad de las suscripciones. Para obtener más información, vea <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A> y [uso de PowerShell para cambiar y enumerar Reporting Services propietarios de suscripciones y ejecutar una suscripción](manage-subscription-owners-and-run-subscription-powershell.md).

 **En este tema:**

-   [Escenarios de suscripción y entrega](#bkmk_subscription_scenarios)

-   [Suscripciones estándar y controladas por datos](#bkmk_standard_and_datadriven)

-   [Requisitos de suscripción](#bkmk_subscription_requirements)

-   [Extensiones de entrega](#bkmk_delivery_extensions)

-   [Partes de una suscripción](#bkmk_parts_of_subscription)

-   [Cómo se procesan las suscripciones](#bkmk_subscription_processing)

-   [Cómo se procesan las suscripciones](#bkmk_subscription_processing)

 **Temas de esta sección:**

-   [Entrega por correo electrónico en Reporting Services](e-mail-delivery-in-reporting-services.md) Describe la configuración y el funcionamiento de la entrega de correo electrónico al servidor de informes.

-   [File Share Delivery in Reporting Services](file-share-delivery-in-reporting-services.md) Describe la configuración y el funcionamiento de la entrega a recursos compartidos del servidor de informes.

-   [SharePoint Library Delivery in Reporting Services](sharepoint-library-delivery-in-reporting-services.md) Describe la entrega de la suscripción a una biblioteca de SharePoint.

-   [Suscripciones controladas por datos a informes](data-driven-subscriptions.md) Ofrece información sobre el uso de suscripciones controladas por datos para personalizar la salida de informes en tiempo de ejecución.

-   [Creación y administración de suscripciones para servidores de informes en modo nativo](../create-manage-subscriptions-native-mode-report-servers.md)

-   [Creación y administración de suscripciones para servidores de informes en modo de SharePoint](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md)

-   [Supervisión de suscripciones de Reporting Services](monitor-reporting-services-subscriptions.md)

-   [Uso de PowerShell para cambiar y enumerar a los propietarios de una suscripción de Reporting Services y ejecutar una suscripción](manage-subscription-owners-and-run-subscription-powershell.md)

##  <a name="subscription-and-delivery-scenarios"></a><a name="bkmk_subscription_scenarios"></a>Escenarios de suscripción y entrega
 Para cada suscripción, se pueden configurar las opciones de entrega y las opciones disponibles dependen de la extensión de entrega que seleccione. Una extensión de entrega es un módulo que admite alguna manera de distribución. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] incluye varias extensiones de entrega y, además, la extensión de entrega puede estar disponible con proveedores de terceros.

 Si es un programador, puede crear extensiones de entrega personalizadas para admitir otros escenarios. Para más información, consulte [Implementing a Delivery Extension](../extensions/delivery-extension/implementing-a-delivery-extension.md).

 En la tabla siguiente se describen los escenarios de suscripción comunes de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] .

|Escenario|Descripción|
|--------------|-----------------|
|Informes por correo electrónico|Envíe informes por correo electrónico a usuarios individuales y grupos. Cree una suscripción y especifique un alias de grupo o de correo electrónico para recibir el informe que desea distribuir. Puede hacer que [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] determine los datos de la suscripción en tiempo de ejecución. Si desea enviar el mismo informe a un grupo que tiene una lista variable de miembros, puede usar una consulta para derivar la lista de suscripción en tiempo de ejecución.|
|Ver informes sin conexión|Los informes que desee archivar pueden enviarse directamente a una carpeta compartida de la que se hará copia de seguridad con arreglo a una programación nocturna. Los informes grandes que tardan demasiado tiempo en cargarse en un explorador se pueden enviar a una carpeta compartida en un formato que pueda verse en una aplicación de escritorio. Los usuarios pueden seleccionar uno de los formatos siguientes para la salida de la suscripción:<br /><br /> Archivo XML con datos de informe<br /><br /> CSV (delimitado por comas)<br /><br /> PDF<br /><br /> MHTML (archivo web)<br /><br /> Microsoft Excel<br /><br /> Archivo TIFF<br /><br /> Microsoft Word|
|Cargar previamente en caché|Si tiene varias instancias de un informe con parámetros o un gran número de usuarios de informes que ven los informes, puede cargar los informes previamente en caché para reducir el tiempo de procesamiento necesario para mostrar el informe.|
|Informes controlados por datos|Use las suscripciones controladas por datos para personalizar la salida de informes, las opciones de entrega y la configuración de los parámetros del informe en tiempo de ejecución. La suscripción usa una consulta para obtener los valores de entrada de un origen de datos en tiempo de ejecución. Puede usar suscripciones controladas por datos para realizar una operación de combinación de correspondencia que envíe un informe a una lista de suscriptores que se determina en el momento de la suscripción.|

##  <a name="standard-and-data-driven-subscriptions"></a><a name="bkmk_standard_and_datadriven"></a>Suscripciones estándar y controladas por datos
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] admite dos tipos de suscripciones: **estándar** y **controladas por datos**. Las suscripciones estándar se crean y se administran por usuarios individuales. La suscripción estándar consta de valores estáticos que no pueden modificarse durante su procesamiento. Para cada suscripción estándar existe un único conjunto de opciones de presentación del informe, opciones de entrega y parámetros de informe.

 Las suscripciones controladas por datos obtienen información de suscripción en tiempo de ejecución consultando un origen de datos externo que proporciona los valores usados para especificar un destinatario, parámetros de informe o un formato de aplicación. Las suscripciones controladas por datos están indicadas para listas de destinatarios extensas o para ocasiones en las que se desea cambiar el resultado del informe para cada destinatario. Este tipo de suscripciones requieren conocimientos sobre la creación de consultas y el uso de los parámetros. Las personas que crean y administran estas suscripciones suelen ser los administradores del servidor de informes. Para obtener más información, vea lo siguiente:

-   [Suscripciones controladas por datos](data-driven-subscriptions.md)

-   [Crear una suscripción controlada por datos &#40;Tutorial de SSRS&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md)

##  <a name="subscription-requirements"></a><a name="bkmk_subscription_requirements"></a>Requisitos de suscripción
 Para poder crear una suscripción a un informe, se deben cumplir los siguiente requisitos previos:

|Requisito|Descripción|
|-----------------|-----------------|
|Permisos|Debe tener acceso al informe. Para poder suscribirse a un informe, debe tener permiso para verlo.<br /><br /> La asignación de roles debe incluir la tarea "Administrar suscripciones individuales".|
|Credenciales almacenadas|Para crear una suscripción, el informe debe utilizar credenciales almacenadas o ninguna credencial para recuperar datos en tiempo de ejecución. No puede suscribirse a un informe configurado para usar las credenciales representadas o delegadas del usuario actual para conectarse a un origen de datos externo. Las credenciales almacenadas pueden ser una cuenta de Windows o una cuenta de usuario de base de datos. Para más información, vea [Especificar información de credenciales y conexión para los orígenes de datos de informes](../report-data/specify-credential-and-connection-information-for-report-data-sources.md).<br /><br /> Debe tener el permiso para ver el informe y crear suscripciones individuales. La opción**Eventos programados y entrega de informes** debe estar habilitada en el servidor de informes. Para obtener más información, vea [Crear y administrar suscripciones para servidores de informes en modo nativo](../create-manage-subscriptions-native-mode-report-servers.md).|
|Valores dependientes de usuario en un informe|Únicamente en el caso de las suscripciones estándar, es posible crear suscripciones a informes que incluyan información de cuenta de usuario en un filtro o como texto que aparezca en el informe. En el informe, el nombre de la cuenta de usuario se especifica mediante una expresión `User!UserID` que se resuelve en el usuario actual. Cuando se crea una suscripción, se considera que el usuario actual es el que la crea.|
|Sin seguridad de elemento de modelo|No es posible suscribirse a un informe del Generador de informes que utilice como origen de datos un modelo si éste contiene una configuración de seguridad de elementos de modelo. Esta restricción solo se aplica a los informes que utilizan seguridad de elementos de modelo.|
|Valores de parámetros|Si el informe utiliza parámetros, se debe especificar un valor de parámetro con el propio informe o en la suscripción que defina. Si se han definido valores predeterminados en el informe, puede establecer el valor del parámetro para que utilice la opción predeterminada.|

##  <a name="delivery-extensions"></a><a name="bkmk_delivery_extensions"></a>Extensiones de entrega
 Las suscripciones se procesan en el servidor de informes y se distribuyen mediante las extensiones de entrega implementadas en el servidor. De forma predeterminada, puede crear suscripciones que envían informes a una biblioteca compartida o a una dirección de correo electrónico. Si el servidor de informes está configurado para el modo integrado con SharePoint, también puede enviar un informe a una biblioteca de SharePoint.

 Cuando un usuario crea una suscripción, puede elegir una de las extensiones de entrega disponibles para determinar cómo se entrega el informe. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] incluye las siguientes extensiones de entrega.

|Extensión de entrega|Descripción|
|------------------------|-----------------|
|Recurso compartido de archivos de Windows|Entrega un informe como un archivo de aplicación estática a una carpeta compartida accesible en la red.|
|Correo electrónico|Entrega una notificación o un informe como datos adjuntos de correo electrónico o como vínculo de dirección URL.|
|Biblioteca de SharePoint|Entrega un informe como un archivo de aplicación estática a una biblioteca de SharePoint accesible desde un sitio de SharePoint. El sitio se debe integrar con un servidor de informes que se ejecuta en el modo integrado con SharePoint.|
|Null|El proveedor de entrega NULL es una extensión de entrega muy especializada que se usa para cargar previamente una memoria caché con informes con parámetros listos para ver. Este método no está disponible para los usuarios en suscripciones individuales. La entrega NULL la usan los administradores en suscripciones controladas por datos para mejorar el rendimiento del servidor de informes, mediante una carga previa en la memoria caché.|

> [!NOTE]
>  La entrega de informes es una parte extensible de la arquitectura de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] . Otros fabricantes pueden crear extensiones de entrega personalizadas para enrutar informes a distintas ubicaciones o dispositivos. Para obtener más información acerca de las extensiones de entrega personalizadas, vea [Implementing a Delivery Extension](../extensions/delivery-extension/implementing-a-delivery-extension.md).

##  <a name="parts-of-a-subscription"></a><a name="bkmk_parts_of_subscription"></a>Partes de una suscripción
 Una definición de suscripción se compone de las siguientes partes:

-   Un puntero a un informe que se puede ejecutar en modo desatendido (es decir, un informe que usa credenciales almacenadas o que no usa ninguna credencial).

-   Un método de entrega (por ejemplo, correo electrónico) y una configuración para el modo de entrega (como una dirección de correo electrónico).

-   Una extensión de representación, para presentar el informe en un formato específico.

-   Condiciones para procesar la suscripción, que se expresa como un evento.

     Normalmente, las condiciones para ejecutar un informe se basan en el tiempo. Por ejemplo, puede que desee ejecutar un informe concreto todos los martes a las 3 de la tarde hora UTC. Sin embargo, si el informe se ejecuta como una instantánea, puede especificar que la suscripción se ejecute siempre que se actualice la instantánea.

-   Parámetros utilizados al ejecutar el informe.

     Los parámetros son opcionales y se especifican solo para informes que acepten valores de parámetros. Puesto que la suscripción suele ser propiedad de un usuario, los valores de parámetros que se especifiquen varían de una suscripción a otra. Por ejemplo, los directores de ventas de diferentes divisiones utilizarán parámetros que devuelvan datos para su división. Todos los parámetros deben tener un valor definido explícitamente o un valor predeterminado válido.

 La información de suscripción se almacena con informes individuales en la base de datos del servidor de informes. No puede administrar suscripciones independientemente del informe al que estén asociadas. Tenga en cuenta que las suscripciones no se pueden ampliar para incluir descripciones, otro texto personalizado u otros elementos. Las suscripciones solo pueden contener los elementos mencionados anteriormente.

##  <a name="how-subscriptions-are-processed"></a><a name="bkmk_subscription_processing"></a> Cómo se procesan las suscripciones
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] incluye el procesador de entrega y programación, que proporciona funcionalidad para programar informes y entregarlos a los usuarios. El servidor de informes responde a eventos que supervisa constantemente. Cuando se produce un evento que coincide con las condiciones definidas para una suscripción, el servidor de informes la lee para determinar cómo procesar y entregar el informe. El servidor de informes solicita la extensión de entrega que se especifica en la suscripción. Con la extensión de entrega en funcionamiento, el servidor de informes extrae la información de entrega de la suscripción y la envía a la extensión de entrega para su procesamiento.

 La extensión de entrega representa el informe en el formato definido en la suscripción y después entrega el informe o la notificación al destino especificado. Si no se puede entregar un informe, se incluye una entrada en el archivo de registro del servidor de informes. Si desea permitir los reintentos, puede configurar el servidor de informes para que vuelva a intentar la entrega si el primer intento no tiene éxito.

### <a name="processing-a-standard-subscription"></a>Procesar una suscripción estándar
 Las suscripciones estándar producen una instancia de un informe. El informe se entrega en una sola carpeta compartida o en las direcciones de correo electrónico especificadas en la suscripción. El diseño del informe y los datos no varían. Si el informe utiliza parámetros, las suscripciones estándar se procesan con un solo valor para cada parámetro del informe.

### <a name="processing-a-data-driven-subscription"></a>Procesar una suscripción controlada por datos
 Las suscripciones controladas por datos pueden producir varias instancias del informe, que se entregan a diversos destinos. El diseño del informe no cambia, pero los datos de un informe pueden variar si los valores de los parámetros se envían desde un conjunto de resultados de suscriptores. Cuando los valores se envían desde el conjunto de filas, también pueden variar de suscriptor a suscriptor las opciones de entrega que afectan a la manera en que se representa el informe o a si el informe se incluye en el mensaje de correo como un archivo adjunto o como un vínculo.

 Las suscripciones controladas por datos pueden producir un gran número de entregas. El servidor de informes crea una entrega por cada fila del conjunto de filas que devuelve la consulta de la suscripción.

### <a name="report-delivery-characteristics"></a>Características de la entrega de informes
 Los informes que se entregan mediante suscripciones estándar suelen representarse como informes estáticos. Estos informes se basan en la instantánea de ejecución de informes más reciente o se generan como informes estáticos a fin de completar una entrega. Si elige la opción **Incluir vínculo** en una suscripción a un informe que se ejecute a petición, el servidor de informes ejecutará el informe cuando haga clic en el hipervínculo.

> [!NOTE]
>  Los informes que se entregan mediante una dirección URL permanecen conectados al servidor de informes y pueden actualizarse o eliminarse entre visualizaciones. Las opciones de entrega que elija para su suscripción determinarán si el informe se entrega como dirección URL, incrustado en el cuerpo de un mensaje de correo electrónico o enviado como dato adjunto.

 Los informes que se entregan mediante una suscripción controlada por datos pueden volver a generarse mientras se procesa la suscripción. El servidor de informes no bloquea una instancia específica de un informe ni su conjunto de datos para completar una suscripción controlada por datos. Si la suscripción utiliza diferentes valores de parámetros para diferentes suscriptores, el servidor de informes vuelve a generar el informe para producir el resultado requerido. Si los datos subyacentes se actualizan después de que se haya creado y entregado la primera copia del informe, es posible que los usuarios que obtengan los informes más adelante en el proceso vean datos basados en un conjunto de resultados diferente. Puede utilizar un informe que se ejecute como instantánea para garantizar que se entrega la misma instancia del informe a todos los suscriptores. Sin embargo, si se genera una actualización programada de la instantánea mientras se procesa la suscripción, es posible que los usuarios sigan recibiendo diferentes datos en los informes.

### <a name="triggering-subscription-processing"></a>Desencadenar el procesamiento de suscripciones
 El servidor de informes utiliza dos tipos de eventos para desencadenar el procesamiento de suscripciones: un evento controlado por tiempo que se especifica en una programación o un evento de actualización de instantánea.

 El desencadenador controlado por tiempo usa una programación específica del informe o una programación compartida para especificar cuándo se ejecuta una suscripción. En los informes a petición y en memoria caché, las programaciones son la única opción de desencadenamiento.

 Un evento de actualización de instantánea utiliza la actualización programada de una instantánea de informe para desencadenar una suscripción. Puede definir una suscripción que se desencadene siempre que se actualice un informe con datos nuevos, basándose en propiedades de ejecución del informe establecidas en éste.

## <a name="see-also"></a>Consulte también
 [Crear una suscripción controlada por datos &#40;tutorial de SSRS&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md) [programa](schedules.md) [Reporting Services el servidor de informes &#40;el modo nativo&#41;](../report-server/reporting-services-report-server-native-mode.md) [crear y administrar suscripciones para servidores de informes en modo nativo](../create-manage-subscriptions-native-mode-report-servers.md) [supervisar suscripciones de Reporting Services](monitor-reporting-services-subscriptions.md)


