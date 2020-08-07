---
title: Determinar el modo de servidor de una instancia de Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9e556fb1-ca37-4f06-8f8f-f187cb0fdb37
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1ec68383d00441e4b1212c2fc03d07f1aa143313
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745495"
---
# <a name="determine-the-server-mode-of-an-analysis-services-instance"></a>Determinar el modo de servidor de una instancia de Analysis Services
  Analysis Services se puede instalar en uno de estos tres modos de servidor: multidimensional y de minería de datos (valor predeterminado), PowerPivot para SharePoint, y tabular. El modo de servidor de una instancia de Analysis Services se determina durante la instalación al elegir las opciones para instalar el servidor.  
  
 El modo de servidor determina el tipo de solución que se crea e implementa. Si no ha instalado el software de servidor y desea saber en qué modo se instaló el servidor, puede utilizar la información de este tema para determinar el modo. Para obtener más información sobre las características disponibles en un modo específico, vea [Comparar soluciones tabulares y multidimensionales &#40;SSAS&#41;](../comparing-tabular-and-multidimensional-solutions-ssas.md).  
  
 Si no desea utilizar el modo de servidor que instaló, debe desinstalar y volver a instalar el software, seleccionando el modo que prefiera. También puede instalar una instancia adicional de Analysis Services en el mismo equipo para tener varias instancias ejecutándose en distintos modos.  
  
## <a name="server-icons-in-object-explorer"></a>Iconos de servidor en el Explorador de objetos  
 La manera más fácil de determinar el modo del servidor es conectar con el servidor de SQL Server Management Studio y observar el icono situado junto al nombre del servidor en el Explorador de objetos. La ilustración siguiente muestra tres instancias de Analysis Services implementadas en los modos multidimensional, tabular, y PowerPivot:  
  
 ![Iconos del Explorador de objetos por cada modo de servidor](../media/ssas-ssms-servermodes.gif "Iconos del Explorador de objetos por cada modo de servidor")  
  
## <a name="viewing-deploymentmode-property-in-msmdsrvini-file"></a>Ver la propiedad DeploymentMode en el archivo MSMDSRV.INI  
 También puede comprobar la propiedad de `DeploymentMode` en el archivo msmdsrv.ini que se incluye en cada instancia de Analysis Services. El valor de esta propiedad identifica el modo del servidor. Los valores válidos son 0 (Multidimensional), 1 (SharePoint), o 2 (Tabular). Debe ser administrador de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (es decir, miembro del rol de servidor) para abrir el archivo msmdsrv.ini. Este archivo contiene XML estructurado. Puede utilizar el Bloc de notas u otro editor de texto para ver el archivo.  
  
> [!CAUTION]  
>  No cambie el valor de la propiedad `DeploymentMode`. No se puede cambiar la propiedad de forma manual una vez instalado el servidor.  
  
## <a name="about-the-deploymentmode-property"></a>Acerca de la propiedad DeploymentMode  
 La propiedad `DeploymentMode` determina el contexto operativo de una instancia de servidor de Analysis Services. Esta propiedad se denomina ' modo de servidor ' en los cuadros de diálogo, los mensajes y la documentación. El programa de instalación inicializa esta propiedad en función de cómo se instale Analysis Services. Esta propiedad debe considerarse interna únicamente y siempre se usa el valor especificado por el programa de instalación.  
  
 Los valores válidos de esta propiedad incluyen los siguientes:  
  
|Value|Descripción|  
|-----------|-----------------|  
|0|Este es el valor predeterminado. Especifica el modo multidimensional, utilizado para dar servicio a las bases de datos multidimensionales que usan el almacenamiento MOLAP, HOLAP y ROLAP, así como a los modelos de minería de datos.|  
|1|Especifica las instancias de Analysis Services que se instalaron como parte de una implementación de PowerPivot para SharePoint. No cambie la propiedad del modo de implementación de la instancia de Analysis Services que forma parte de una instalación de PowerPivot para SharePoint. Los datos PowerPivot dejarán de ejecutarse en el servidor si cambia el modo.|  
|2|Especifica el modo tabular empleado para hospedar las bases de datos de modelos tabulares que utilizan el almacenamiento en memoria o el almacenamiento DirectQuery.|  
  
 Cada modo excluye a los demás. Un servidor configurado para el modo tabular no podrá ejecutar las bases de datos de Analysis Services que contengan cubos y dimensiones. Si el hardware del equipo subyacente puede admitirlo, puede instalar varias instancias de Analysis Services en el mismo equipo y configurar cada instancia para utilizar otro modo. Recuerde que Analysis Services es una aplicación que usa muchos recursos. La implementación de varias instancias en el mismo sistema solo se recomienda para los servidores de tecnología avanzada.  
  
## <a name="see-also"></a>Consulte también  
 [Instalar Analysis Services en modo tabular](install-windows/install-analysis-services.md)   
 [Instalar Analysis Services en modo multidimensional y de minería de datos](../../sql-server/install/install-analysis-services-in-multidimensional-and-data-mining-mode.md)   
 [Instalación de PowerPivot para SharePoint 2010](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)   
 [Conectarse a Analysis Services](connect-to-analysis-services.md)   
 [Soluciones de modelos tabulares &#40;&#41;tabular de SSAS](../tabular-model-solutions-ssas-tabular.md)   
 [Soluciones de modelos multidimensionales &#40;SSAS&#41;](../multidimensional-models/multidimensional-model-solutions-ssas.md)   
 [Modelos de minería de datos &#40;Analysis Services - Minería de datos&#41;](../data-mining/mining-models-analysis-services-data-mining.md)  
  
  
