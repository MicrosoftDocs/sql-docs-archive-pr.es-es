---
title: Publicar un informe en una biblioteca de SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- deploying [Reporting Services], reports in SharePoint integrated mode
- SharePoint integration [Reporting Services], publishing to a library
- publishing reports [Reporting Services], to a SharePoint library
ms.assetid: 3f6dfc28-50d8-4231-bd25-871b5f77cce6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 23b74ffb04bf1e13523dcf6ec5d774089d80f73b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744481"
---
# <a name="publish-a-report-to-a-sharepoint-library"></a>Publicar un informe en una biblioteca de SharePoint
  Para publicar un informe en un sitio de SharePoint configurado para la integración de SharePoint, debe establecer las propiedades del proyecto en el Diseñador de informes. En las propiedades de proyecto, todas las referencias a servidores, informes y orígenes de datos compartidos deben ser direcciones URL completas. En la definición de informe, todas las referencias a subinformes, informes detallados y recursos, como imágenes basadas en web, deben ser direcciones URL completas.  
  
 Debe disponer del permiso **Miembro** o **Propietario** en el sitio de SharePoint para establecer las propiedades en el proyecto. Para obtener más información, vea [Ejemplos de dirección URL para los elementos de informe publicados en un servidor de informes en modo de SharePoint &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md).  
  
### <a name="to-publish-a-report-to-a-sharepoint-site"></a>Para publicar un informe en un sitio de SharePoint  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], abra un nuevo proyecto de servidor de informes o uno existente.  
  
2.  En el menú **Proyecto** , haga clic en **Propiedades**. _\<project>_ Se abrirá el cuadro de diálogo **páginas de propiedades** .  
  
3.  En la lista **Configuración** , seleccione el nombre de una configuración de generación de soluciones para usarla en la generación y publicación del informe. La configuración actual aparece como **Active**( *\<configuration>* ).  
  
4.  Si desea publicar los orígenes de datos compartidos del proyecto y sobrescribir los publicados anteriormente, establezca **OverwriteDataSources** en **True**.  
  
5.  Opta En el caso de **TargetDataSourceFolder**, escriba una dirección URL a una biblioteca de SharePoint o una carpeta de biblioteca (por ejemplo, *http://TestServer/TestSite/Documents/DataSources)* .  
  
     Si no se especifica ningún valor, se usa el valor **TargetReportFolder** .  
  
6.  En el caso de **TargetReportFolder**, escriba una dirección URL a una biblioteca o una carpeta de biblioteca (por ejemplo, *http://TestServer/TestSite/Documents/Reports)* .  
  
7.  Para **TargetServerURL**, escriba una dirección URL a un sitio de nivel superior o a un subsitio de SharePoint. Si no especifica un sitio, se usa el sitio de nivel superior predeterminado (por ejemplo,, *http://servername* *http://servername/site* o *http://servername/site/subsite* ).  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. En el Explorador de soluciones, haga clic con el botón derecho en el informe que quiera publicar y haga clic en **Implementar**. El informe se publicará en la ubicación especificada en **TargetReportFolder**. Los errores de implementación se mostrarán en la ventana de resultados.  
  
## <a name="see-also"></a>Consulte también  
 [Cuadro de diálogo páginas de propiedades del proyecto](../tools/project-property-pages-dialog-box.md)   
 [Establecer las propiedades de implementación &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md)   
 [Publicar informes en un servidor de informes](publishing-reports-to-a-report-server.md)   
 [Ejemplos de dirección URL para los elementos de informe publicados en un servidor de informes en modo de SharePoint &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)   
 [Usar una conexión de datos de Office &#40;.odc&#41; con informes &#40;Reporting Services en el modo integrado de SharePoint&#41;](../report-data/use-an-office-data-connection-odc-with-reports.md)  
  
  
