---
title: Novedades de&#39;s en Analysis Services y Business Intelligence | Microsoft Docs
ms.custom: ''
ms.date: 06/07/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: aa69c299-b8f4-4969-86d8-b3292fe13f08
author: minewiskan
ms.author: owend
ms.openlocfilehash: 18863a565b63ccc1a9bd2eb0e7619d4d133c5d33
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669880"
---
# <a name="what39s-new-in-sql-server-2014-analysis-services"></a>Novedades de&#39;s en SQL Server 2014 Analysis Services
  Con la excepción de la funcionalidad agregada que admite Power View informes en modelos multidimensionales, [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] no ha cambiado respecto a la versión anterior.

 Para obtener información sobre otros [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] productos y tecnologías que son diferentes en esta versión, consulte [novedades de SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).

## <a name="updates-to-design-tool-installation"></a>Actualizaciones a la instalación de las herramientas de diseño
 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] para Business Intelligence (SSDT-BI), conocido anteriormente como Business Intelligence Development Studio (BIDS), se emplea para crear modelos de Analysis Services, informes de Reporting Services y paquetes de Integration Services. Puede descargar SSDT-BI desde las ubicaciones siguientes:

-   [Descargar SSDT-BI para Visual Studio 2013](https://go.microsoft.com/fwlink/p/?LinkId=396526)

-   [Descargar SSDT-BI para Visual Studio 2012](https://go.microsoft.com/fwlink/p/?LinkID=273673)

 Si tiene instalada en el equipo una versión anterior de SSDT-BI o BIDS, la versión más reciente se instala en paralelo con la versión anterior. Es frecuente ejecutar versiones más recientes y versiones anteriores de las herramientas de diseño en una misma estación de trabajo para poder modificar soluciones y proyectos vinculados a determinadas versiones del servidor.

> [!NOTE]
>  Hay varios sitios de descarga para las versiones de Visual Studio 2012 y Visual Studio 2013 de SSDT. La mayoría no incluyen las plantillas de proyecto BI. En los vínculos anteriores obtendrá la versión correcta. Sabrá que tiene la versión correcta de SSDT-BI si ve la carpeta de plantillas de proyecto de Business Intelligence. Esta carpeta contiene las plantillas de proyecto para Analysis Services, Reporting Services e Integration Services. Según cómo haya instalado SSDT-BI, es posible que vea también una plantilla de proyecto adicional para bases de datos de SQL Server.

 ![Nuevas plantillas de proyecto de SSDT](media/ssdt-biprojects.png "Nuevas plantillas de proyecto de SSDT")

## <a name="features-recently-added-power-view-for-multidimensional-models"></a>Características agregadas recientemente: Power View para modelos multidimensionales
 La posibilidad de crear informes de Power View en modelos multidimensionales se presentó por primera vez en la Actualización acumulativa 4 de [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 1. La funcionalidad Power View para modelos multidimensionales se incluye ahora como parte de [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].

 **Informe de Power View para un modelo multidimensional**

 ![Informe de Power View](media/powerviewreport-wn.gif "Informe de Power View")

 Esta funcionalidad ayuda a las organizaciones a maximizar sus inversiones existentes de BI ya que permite usar modelos multidimensionales (también conocidos como cubos OLAP) con las últimas herramientas de generación de informes cliente. En función de los tipos de datos del modelo multidimensional, los usuarios pueden crear fácilmente diversas visualizaciones dinámicas desde tablas y matrices hasta gráficos de burbujas y mapas geográficos. Los modelos multidimensionales también admiten ahora consultas mediante el Lenguaje de expresiones de análisis de datos (DAX).

 Power View para modelos multidimensionales requiere la capacidad integrada de informes de Power View de [!INCLUDE[ssSQL14](../includes/sssql14-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (en modo de SharePoint). Otras versiones de Power View, en concreto el complemento Power View de Excel 2013, no admiten modelos multidimensionales.

 Para obtener más información, vea [Power View para modelos multidimensionales](https://msdn.microsoft.com/library/dn140246.aspx).


