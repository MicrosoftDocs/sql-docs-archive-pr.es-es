---
title: Editor de destino de SAP BW (página Administrador de conexiones) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 04ae38f8-5287-45a3-826a-8aac5dd15a91
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0dd628f1a0fec09490e0d3720610d1232882ed92
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744233"
---
# <a name="sap-bw-destination-editor-connection-manager-page"></a>Editor de destino de SAP BW (página Administrador de conexiones)
  Use la página **Administrador de conexiones** del cuadro de diálogo **Editor de destino de SAP BW** para seleccionar un administrador de conexiones de SAP BW que va a usar el destino SAP BW. En esta página, puede seleccionar los parámetros para cargar los datos en el sistema SAP Netweaver BW.  
  
 Para obtener más información sobre el destino SAP BW de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, vea [Destino de SAP BW](sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  La documentación de Microsoft Connector 1.1 for SAP BW da por supuesto que se está familiarizado con el entorno SAP Netweaver BW. Para obtener más información acerca de SAP Netweaver BW, o sobre cómo configurar los objetos y los procesos de SAP Netweaver BW, vea la documentación de SAP.  
  
 **Para abrir la página Administrador de conexiones**  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], abra el paquete de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] que contiene el destino SAP BW.  
  
2.  En la pestaña **Flujo de datos** , haga doble clic en el destino de SAP BW.  
  
3.  En **Editor de destino SAP BW**, haga clic en **Administrador de conexiones** para abrir la página **Administrador de conexiones** del editor.  
  
## <a name="options"></a>Opciones  
  
> [!NOTE]  
>  Si no conoce todos los valores necesarios para configurar el destino, puede que tenga que ponerse en contacto con el administrador de SAP.  
  
 **Administrador de conexiones de SAP BW**  
 Seleccione un administrador de conexiones de la lista o cree una conexión haciendo clic en **Nuevo**.  
  
 **Nuevo**  
 Cree un administrador de conexiones con el cuadro de diálogo **Administrador de conexiones de SAP BW** .  
  
 **Probar carga**  
 Realice una prueba del proceso de carga que use los valores que haya seleccionado y cargue cero filas.  
  
### <a name="infopackageinfosource-options"></a>Opciones InfoPackage/InfoSource  
 No es necesario que conozca y especifique estos valores previamente. Utilice el botón de **Buscar** para buscar y seleccionar el InfoPackage adecuado. Después de seleccionar un InfoPackage, el componente especifica los valores adecuados para estas opciones.  
  
 **InfoPackage**  
 Escriba el nombre del InfoPackage.  
  
 **InfoSource**  
 Escriba el nombre del InfoSource.  
  
 **Tipo**  
 Escriba el carácter único que identifique el tipo del InfoSource. La tabla siguiente enumera los valores aceptables de un solo carácter.  
  
|Value|Descripción|  
|-----------|-----------------|  
|**D**|Datos de transacción|  
|**M**|Datos maestros|  
|**T**|Textos|  
|**H**|Datos de jerarquía|  
  
 **Sistema lógico**  
 Escriba el nombre del sistema lógico que esté asociado con el InfoPackage.  
  
 **Buscar**  
 Busque el InfoPackage con el cuadro de diálogo **Buscar InfoPackage** . Para obtener más información sobre este cuadro de diálogo, vea [Look Up InfoPackage](look-up-infopackage.md).  
  
### <a name="rfc-destination-options"></a>Opciones de destino RFC  
 No es necesario que conozca y especifique estos valores previamente. Utilice el botón de **Buscar** para buscar y seleccionar el destino RFC adecuado. Después de seleccionar un destino RFC, el componente especifica los valores adecuados para estas opciones.  
  
 **Host de puerta de enlace**  
 Permite escribir el nombre del servidor o la dirección IP del host de puerta de enlace. Normalmente, el nombre o la dirección IP es el mismo que el del servidor de aplicaciones SAP.  
  
 **Servicio de puerta de enlace**  
 Escriba el nombre del servicio de puerta de enlace, con el formato `sapgwNN`, donde `NN` es el número del sistema.  
  
 **Id. de programa**  
 Permite escribir el identificador de programa asociado al destino RFC.  
  
 **Buscar**  
 Permite buscar el destino RFC con el cuadro de diálogo **Buscar destino RFC** . Para obtener más información sobre este cuadro de diálogo, vea [Look Up RFC Destination](look-up-rfc-destination.md).  
  
### <a name="create-sap-bw-objects-options"></a>Crear opciones de objetos de SAP BW  
 **Seleccionar tipo de objeto**  
 Seleccione el tipo de objeto SAP Netweaver BW que desea crear. Puede seleccionar uno de los siguientes tipos:  
  
-   InfoObject  
  
-   InfoCube  
  
-   InfoSource  
  
-   InfoPackage  
  
 **Creación**  
 Cree el tipo seleccionado de objeto SAP Netweaver BW.  
  
|Tipo de objeto|Resultado|  
|-----------------|------------|  
|**InfoObject**|Cree un InfoObject nuevo con el cuadro de diálogo **Crear nuevo InfoObject** . Para obtener más información sobre este cuadro de diálogo, vea [Create New InfoObject](create-new-infoobject.md).|  
|**InfoCube**|Cree un InfoCube nuevo con el cuadro de diálogo **Crear InfoCube para los datos de transacción** . Para obtener más información sobre este cuadro de diálogo, vea [Create InfoCube for Transaction Data](create-infocube-for-transaction-data.md).|  
|**InfoSource**|Cree un InfoSource nuevo con el cuadro de diálogo **Crear InfoSource** y, a continuación, use **Crear InfoSource para datos de transacción** o el cuadro de diálogo **Crear InfoSource para datos maestros** . Para obtener más información sobre estos cuadros de diálogo, vea [Create InfoSource](create-infosource.md), [Create InfoSource for Transaction Data](create-infosource-for-transaction-data.md) y [Create InfoSource for Master Data](create-infosource-for-master-data.md).|  
|**InfoPackage**|Cree un InfoPackage nuevo con el cuadro de diálogo **Crear InfoPackage** . Para obtener más información sobre este cuadro de diálogo, vea [Create InfoPackage](create-infopackage.md).|  
  
## <a name="see-also"></a>Consulte también  
 [Editor de destino de SAP BW &#40;página Asignaciones&#41;](sap-bw-destination-editor-mappings-page.md)   
 [Editor de destino de SAP BW &#40;página Salida de error&#41;](sap-bw-destination-editor-error-output-page.md)   
 [Editor de destino de SAP BW &#40;página Opciones avanzadas&#41;](sap-bw-destination-editor-advanced-page.md)   
 [Ayuda F1 de Microsoft Connector 1.1 for SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
