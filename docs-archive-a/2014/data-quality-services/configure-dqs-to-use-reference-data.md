---
title: Configurar DQS para usar datos de referencia | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.admin.config.rds.f1
- sql12.dqs.administration.rdsconfiguration.f1
- sql12.dqs.administration.configuration.createDirectRDS.f1
ms.assetid: fae745e7-57a7-4cbc-8979-56ea8e392e4e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 670e984c2afabb70dece75d94701d7a3a03c95bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744324"
---
# <a name="configure-dqs-to-use-reference-data"></a>Configurar DQS para utilizar datos de referencia
  En este tema se describe cómo configurar [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) con el fin de utilizar datos de referencia para limpiar los datos. Puede usar datos de referencia de Azure Marketplace o de proveedores directos de datos de referencia de terceros en línea.  
  
## <a name="before-you-begin"></a>Antes de empezar  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Requisitos previos  
 Para utilizar datos de referencia de Marketplace, es necesario tener una clave de cuenta de Marketplace válida. Para obtener información detallada sobre cómo crear una clave de cuenta de Marketplace, vea [crear su cuenta](https://go.microsoft.com/fwlink/?LinkId=212936) ( https://go.microsoft.com/fwlink/?LinkId=212936) . También es posible crear una clave de cuenta de Marketplace desde [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] ; para ello, haga clic en **Configuración** en el área **Administración** de la página de inicio de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] y, a continuación, haga clic en **Crear un id. de cuenta de DataMarket** en la pestaña **Datos de referencia** .  
  
###  <a name="security"></a><a name="Security"></a> Seguridad  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permisos  
 Para configurar servicios de datos de referencia en DQS, debe disponer del rol dqs_administrator en la base de datos DQS_MAIN.  
  
##  <a name="configure-dqs-to-use-reference-data-from-marketplace"></a><a name="Marketplace"></a> Configurar DQS para utilizar datos de referencia de Marketplace  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Ejecute la aplicación Data Quality Client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  En la página de inicio de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , en **Administración**, haga clic en **Configuración**.  
  
3.  En la pestaña **Datos de referencia** , en el área **Configuración de red** , escriba los valores apropiados en los cuadros **Servidor proxy** y **Puerto** si utiliza un servidor proxy para conectarse a Internet.  
  
4.  Especifique la clave de cuenta de Marketplace en el cuadro **Id. de cuenta de DataMarket** y haga clic en el icono **Validar el id. de cuenta de DataMarket** para validarla. Aparecerá un mensaje que indicará si la clave de cuenta de Marketplace especificada es válida.  
  
 Ahora ya está preparado para utilizar en DQS los servicios de datos de referencia de Marketplace a los que está suscrita la clave de cuenta de Marketplace especificada.  
  
##  <a name="configure-dqs-to-use-reference-data-from-direct-online-third-party-reference-data-providers"></a><a name="ThirdParty"></a> Configurar DQS para utilizar datos de referencia de proveedores directos de datos de referencia de terceros en línea  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Ejecute la aplicación Data Quality Client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  En la página de inicio de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , en **Administración**, haga clic en **Configuración**.  
  
3.  En la pestaña **Datos de referencia** , en el área **Configuración de red** , escriba los valores apropiados en los cuadros **Servidor proxy** y **Puerto** si utiliza un servidor proxy para conectarse a Internet.  
  
4.  En el área **Configuración del servicio directo de datos de referencia de terceros en línea** , haga clic en el icono **Agregar un nuevo proveedor de servicios de datos de referencia** .  
  
5.  En el cuadro de diálogo **Crear un nuevo proveedor de servicios directos de datos de referencia de terceros en línea** , especifique los detalles siguientes:  
  
    1.  En el cuadro **Nombre** , escriba el nombre del nuevo proveedor de servicios directos de datos de referencia.  
  
    2.  (Opcional) en el cuadro **Descripción** , escriba una descripción para el nuevo proveedor de servicios directos de datos de referencia.  
  
    3.  En el cuadro **Categoría** , escriba la categoría de los datos proporcionados por el nuevo proveedor de servicios directos de datos de referencia.  
  
    4.  En el cuadro Esquema, especifique el esquema que define la cadena de los campos (nombres de columna) que se van a utilizar del proveedor de servicios directos de datos de referencia. Los nombres de campo no pueden incluir espacios, y los campos deben ir separados con comas. Por ejemplo: `FirstName, LastName, City, State`.  
  
    5.  En el cuadro **URI** , escriba el URI del proveedor de servicios directos de datos de referencia. Solo se permiten URI seguros (aquellos cuya dirección empieza por "https://") en DQS.  
  
    6.  En el cuadro **Tamaño máximo de lote**, escriba el número máximo de registros por lote que se enviarán al proveedor de servicios de datos de referencia para la limpieza. Se puede especificar un máximo de 100 registros por lote para la actividad de limpieza.  
  
    7.  En el cuadro **Id. de cuenta** , escriba el identificador de cuenta del suscriptor al proveedor de servicios de datos de referencia.  
  
6.  Haga clic en **Aceptar** para guardar los datos y cerrar el cuadro de diálogo **Crear un nuevo proveedor de servicios directos de datos de referencia de terceros en línea** . El proveedor directo de datos de referencia de terceros en línea recién agregado estará disponible en la cuadrícula **Proveedores de servicios directos de datos de referencia** en DQS.  
  
 Ahora ya puede utilizar los servicios de datos de referencia del proveedor de servicios directos de datos de referencia de terceros en línea que se acaba de configurar en DQS.  
  
##  <a name="follow-up-after-configuring-dqs-to-use-reference-data"></a><a name="FollowUp"></a>Seguimiento: después de configurar DQS para usar datos de referencia  
 A continuación, debe asignar los dominios de la base de conocimiento necesarios a los datos de referencia disponibles en los proveedores de datos que acaba de configurar. Para ello, vea [adjuntar un dominio o un dominio compuesto a datos de referencia](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md).  
  
  
