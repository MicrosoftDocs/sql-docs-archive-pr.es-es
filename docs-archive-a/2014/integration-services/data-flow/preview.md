---
title: Vista previa | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 551494c4-9e27-4592-9200-c6bf19e80c9a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5a795338122c1e7a37a23fdb6af6153f74b927e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87670462"
---
# <a name="preview"></a>Versión preliminar
  Use el cuadro de diálogo **Vista previa** para obtener una vista previa de los datos que va a extraer el origen de SAP BW.  
  
> [!IMPORTANT]  
>  La opción de **Vista previa** , que está disponible en la página de **Administrador de conexiones** del **Editor de origen de SAP BW**, extrae los datos. Si ha configurado SAP Netweaver BW para extraer solamente los datos que han cambiado desde la extracción anterior, si selecciona **Vista previa** , excluirá datos de la vista previa de la extracción siguiente.  
  
 Para obtener más información sobre el componente de origen de SAP BW de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, vea [Origen de SAP BW](sap-bw-source.md).  
  
> [!IMPORTANT]  
>  La documentación de Microsoft Connector 1.1 for SAP BW da por supuesto que se está familiarizado con el entorno SAP Netweaver BW. Para obtener más información acerca de SAP Netweaver BW, o sobre cómo configurar los objetos y los procesos de SAP Netweaver BW, vea la documentación de SAP.  
  
> [!IMPORTANT]  
>  La extracción de datos de SAP Netweaver BW requiere una licencia SAP adicional. Póngase en contacto con SAP para comprobar estos requisitos.  
  
 **Para abrir el cuadro de diálogo Vista Previa**  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], abra el paquete de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] que contiene el origen de SAP BW.  
  
2.  En la pestaña **Flujo de datos** , haga doble clic en el origen de SAP BW.  
  
3.  En **Editor de origen de SAP BW**, haga clic en **Administrador de conexiones** para abrir la página **Administrador de conexiones** del editor.  
  
4.  Configure el origen de SAP BW.  
  
5.  Después de configurar el origen de SAP BW, en la página **Administrador de conexiones** , haga clic en **Vista previa** para obtener una vista previa de los datos en el cuadro de diálogo **Vista previa** .  
  
    > [!NOTE]  
    >  Al hacer clic en **Vista previa** , también se abre el cuadro de diálogo **Registro de solicitudes** . Para obtener más información sobre este cuadro de diálogo, vea [Request Log](request-log.md).  
  
## <a name="options"></a>Opciones  
 El cuadro de diálogo **Vista previa** muestra las filas que se solicitan desde el sistema SAP Netweaver BW. Las columnas que se muestran son columnas definidas en el origen de datos.  
  
 No hay otras opciones en este cuadro de diálogo.  
  
## <a name="see-also"></a>Consulte también  
 [Editor de origen de SAP BW &#40;página Administrador de conexiones&#41;](sap-bw-source-editor-connection-manager-page.md)   
 [Ayuda F1 de Microsoft Connector 1.1 for SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
