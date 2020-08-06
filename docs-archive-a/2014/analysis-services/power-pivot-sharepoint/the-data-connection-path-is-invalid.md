---
title: 'La ruta de acceso de la conexión de datos en el libro señala a un archivo en la unidad local o es un URI no válido. No se pudieron actualizar las siguientes conexiones: datos PowerPivot | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: bd22e41a-0931-4d32-888a-633a3046fc5e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3349af08290e2ff659db1441d849b2afef51e95b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672304"
---
# <a name="the-data-connection-path-in-the-workbook-points-to-a-file-on-the-local-drive-or-is-an-invalid-uri-the-following-connections-failed-to-refresh-powerpivot-data"></a>La ruta de acceso de la conexión de datos en el libro señala a un archivo en la unidad local o es un URI no válido. No se pudieron actualizar las siguientes conexiones: datos PowerPivot
  En los libros de Excel que contienen los datos PowerPivot, Excel Services devuelve este error si no puede conectarse a orígenes de datos incrustados.  
  
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Se aplica a|PowerPivot para SharePoint|  
|Versión del producto|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Causa|Excel Services se configura para permitir únicamente las conexiones de datos de archivos .odc que estén en una biblioteca de conexiones de datos de confianza.|  
|Texto del mensaje|La ruta de acceso de la conexión de datos en el libro señala a un archivo en la unidad local o es un URI no válido. No se pudieron actualizar las siguientes conexiones: datos PowerPivot|  
  
## <a name="explanation"></a>Explicación  
 Los libros PowerPivot contienen conexiones de datos incrustados. Para admitir la interacción de los libros a través de segmentaciones y filtros, Servicios de Excel se debe configurar para permitir el acceso de datos externos a través de la información de las conexiones incrustadas. Se requiere acceso a los datos externos para recuperar los datos PowerPivot que se cargan en los servidores de PowerPivot de la granja.  
  
## <a name="user-action"></a>Acción del usuario  
 Cambie la configuración para permitir conexiones a orígenes de datos incrustados.  
  
1.  En Administración central, en Administración de aplicaciones, haga clic en **Administrar aplicaciones de servicio**.  
  
2.  Haga clic en **Aplicación de Servicios de Excel**.  
  
3.  Haga clic en **Ubicación de archivo de confianza**.  
  
4.  Haga clic en **http://** o en la ubicación que quiera configurar.  
  
5.  En Datos externos, en Permitir datos externos, haga clic en **Bibliotecas de conexiones de datos de confianza e incrustadas**.  
  
6.  Haga clic en **OK**.  
  
 O bien, puede crear una nueva ubicación de confianza para los sitios que contienen los libros PowerPivot y, a continuación, modificar la configuración solo para ese sitio. Para obtener más información, consulte [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
  
