---
title: Objetos de base de datos (Analysis Services-datos multidimensionales) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Services], about objects
- SQL Server Analysis Services, objects
- Analysis Services objects, about Analysis Services objects
- SSAS, objects
- Analysis Services objects
- objects [Analysis Services]
ms.assetid: f76d869b-fc1d-4807-9f28-da09c7be382d
author: minewiskan
ms.author: owend
ms.openlocfilehash: d61e3213356146e1cf9e452e0b62e02c96bd4902
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87752465"
---
# <a name="database-objects-analysis-services---multidimensional-data"></a>Objetos de base de datos (Analysis Services - Datos multidimensionales)
  Una [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instancia de contiene objetos y ensamblados de base de datos para su uso con el procesamiento analítico en línea (OLAP) y la minería de datos.  
  
-   Las bases de datos contienen objetos OLAP y de minería de datos como orígenes de datos, vistas del origen de datos, cubos, medidas, grupos de medida, dimensiones, atributos, jerarquías, estructuras de minería de datos, modelos de minería de datos y roles.  
  
-   Los ensamblados contienen funciones definidas por el usuario que amplían la funcionalidad de las funciones intrínsecas suministradas por los lenguajes Expresiones multidimensionales (MDX) y Extensiones de minería de datos (DMX).  
  
 El objeto <xref:Microsoft.AnalysisServices.Database> es el contenedor para todos los objetos de datos que se necesitan para un proyecto de Business Intelligence (como cubos OLAP, dimensiones y estructuras de minería de datos) y sus objetos de ayuda (como <xref:Microsoft.AnalysisServices.DataSource>, <xref:Microsoft.AnalysisServices.Account> y <xref:Microsoft.AnalysisServices.Role>).  
  
 Un objeto <xref:Microsoft.AnalysisServices.Database> proporciona acceso a los objetos y atributos que incluyen lo siguiente:  
  
-   Todos los cubos a los que puede tener acceso, como una colección.  
  
-   Todas las dimensiones a las que puede tener acceso, como una colección.  
  
-   Todas las estructuras de minería de datos a las que puede tener acceso, como una colección.  
  
-   Todos los orígenes de datos y vistas del origen de datos, como dos colecciones.  
  
-   Todos los roles y permisos de base de datos, como dos colecciones.  
  
-   El valor de intercalación para la base de datos.  
  
-   El tamaño estimado de la base de datos  
  
-   El valor de lenguaje de la base de datos.  
  
-   El valor visible para la base de datos.  
  
## <a name="in-this-section"></a>En esta sección  
 En los siguientes temas se describen los objetos compartidos por características de OLAP y de minería de datos de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Tema|Descripción|  
|-----------|-----------------|  
|[Orígenes de datos en modelos multidimensionales](../data-sources-in-multidimensional-models.md)|Describe un origen de datos en [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Vistas del origen de datos en modelos multidimensionales](../data-source-views-in-multidimensional-models.md)|Describe un modelo de datos lógico basado en uno o varios orígenes de datos, en [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Cubos en modelos multidimensionales](../cubes-in-multidimensional-models.md)|Describe cubos y objetos de cubo, lo que incluye medidas, grupos de medida, relaciones de uso de dimensiones, cálculos, indicadores clave de rendimiento, acciones, traducciones, particiones y perspectivas.|  
|[Dimensiones &#40;Analysis Services - Datos multidimensionales&#41;](../../multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)|Describe dimensiones y objetos de dimensiones, incluidos atributos, relaciones de atributo, jerarquías, niveles y miembros.|  
|[Estructuras de minería de datos &#40;Analysis Services - Minería de datos&#41;](../../data-mining/mining-structures-analysis-services-data-mining.md)|Describe estructuras y objetos de minería de datos, incluidos modelos de minería de datos.|  
|[Roles de seguridad &#40;Analysis Services - Datos multidimensionales&#41;](security-roles-analysis-services-multidimensional-data.md)|Describe un rol, el mecanismo de seguridad utilizado para controlar el acceso a objetos de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Administración de ensamblados de modelos multidimensionales](../multidimensional-model-assemblies-management.md)|Describe un ensamblado, una colección de funciones definidas por el usuario utilizadas para ampliar los lenguajes MDX y DMX, en [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
  
## <a name="see-also"></a>Consulte también  
 [Orígenes de datos admitidos &#40;&#41;de SSAS multidimensionales](../supported-data-sources-ssas-multidimensional.md)   
 [Soluciones de modelos multidimensionales &#40;SSAS&#41;](../multidimensional-model-solutions-ssas.md)   
 [Soluciones de minería de datos](../../data-mining/data-mining-solutions.md)  
  
  
