---
title: Informes personalizados en Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.summary.new.custom.report.f1
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 1ba3f758-f39b-4f5f-91ca-516cedc78979
author: stevestein
ms.author: sstein
ms.openlocfilehash: bc93157100738610c8576f0af40e75613c3cff62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661779"
---
# <a name="custom-reports-in-management-studio"></a>Informes personalizados en Management Studio
  En [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], muchos nodos del Explorador de objetos muestran un conjunto de informes estándar creados por [!INCLUDE[msCoName](../../includes/msconame-md.md)]. Estos informes incluyen un resumen de la información que se suele solicitar al servidor. A partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2, los administradores pueden ejecutar los informes personalizados que se crearon en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] desde [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
## <a name="implementation"></a>Implementación  
 Los informes personalizados se almacenan como archivos de definición de informe (.rdl) y se crean mediante el lenguaje RDL (Report Definition Language). RDL contiene información en formato XML acerca de la recuperación y el diseño de los datos de un informe. RDL es un esquema abierto. Los desarrolladores pueden extender RDL con atributos y elementos adicionales. Los informes pueden ejecutar cualquier instrucción [!INCLUDE[tsql](../../includes/tsql-md.md)] válida presente en el informe.  
  
 Si el Explorador de objetos está conectado a un servidor, los informes personalizados pueden ejecutarse en el contexto de la selección actual del Explorador de objetos si los informes hacen referencia a parámetros de informe de dicho nodo. Esto hace posible que un informe use el contexto actual, por ejemplo la base de datos actual, o bien un contexto coherente, como puede ser especificar una base de datos designada como parte de la instrucción [!INCLUDE[tsql](../../includes/tsql-md.md)] incluida en el informe personalizado.  
  
## <a name="running-a-custom-report"></a>Ejecutar un informe personalizado  
 Un informe personalizado se puede ejecutar en [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] de las siguientes maneras:  
  
-   Haga clic con el botón derecho en un nodo del Explorador de objetos, seleccione **Informes** y haga clic con el botón primario en **Informes personalizados**. En el cuadro de diálogo **Abrir archivo** , busque una carpeta que contenga archivos .rdl y, a continuación, abra el archivo de informes correspondiente.  
  
-   Haga clic con el botón derecho en un nodo del Explorador de objetos, seleccione **Informes**, **Informes personalizados**y, luego, seleccione un informe personalizado de la lista de archivos más usados recientemente.  
  
## <a name="limitations"></a>Limitaciones  
 Cuando trabaje con informes personalizados, tenga en cuenta las siguientes limitaciones:  
  
-   Para evitar la ejecución accidental de código malintencionado, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] no se puede configurar para que ejecute automáticamente un informe, aunque el sistema de archivos esté configurado para asociar los archivos .rdl con [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Los informes se pueden ejecutar mediante programación en [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] y no se pueden ejecutar desde la línea de comandos mediante [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
-   Puede ejecutar informes personalizados en un contexto que no genere los valores esperados. Por ejemplo, puede ejecutar un informe acerca de la replicación en el contexto de una base de datos que no esté involucrada en la replicación o bien ejecutar un informe como un usuario que no tiene permiso para obtener acceso a la información necesaria para generar un informe preciso. El creador del informe personalizado es el responsable de la validez de la estructura del informe y de su contexto.  
  
-   No puede agregar un informe personalizado a la lista de informes estándar.  
  
-   El código procesado por el informe puede afectar al rendimiento del servidor.  
  
-   Los informes personalizados no admiten subinformes.  
  
-   El texto de comando de cada consulta de un informe no se puede definir mediante una expresión.  
  
-   Cualquier parámetro de consulta usado en un comando (consulta) solamente puede hacer referencia a un único parámetro del informe y no puede usar ningún operador de expresión.  
  
-   Tan solo se admiten los tipos de comando de texto y de procedimiento almacenado para los comandos de informe (consultas).  
  
-   El marco de informes no proporciona ninguna secuencia de escape de parámetros para las consultas. Los autores de las consultas deben asegurarse de que sus consultas no recibirán ataques por inyección de código SQL.  
  
## <a name="managing-custom-reports"></a>Administrar informes personalizados  
 Se recomienda que los usuarios que disponen de varios informes personalizados los organicen en carpetas del sistema de archivos que dispongan de los permisos del sistema de archivos NTFS adecuados.  
  
## <a name="permissions"></a>Permisos  
 Los informes personalizados se ejecutan con los permisos del usuario actual. Para evitar que un usuario malintencionado cambie las consultas ejecutadas por el informe, se deben establecer los permisos de la carpeta del sistema de archivos que contiene los archivos de informe para restringir el acceso.  
  
 Tanto el usuario como la cuenta usados por el servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requieren acceso de lectura en la carpeta del sistema de archivos que contiene los archivos de informe.  
  
 Cualquier comando de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] válido puede incrustarse en un informe, pero el comando no se ejecutará.  
  
> [!CAUTION]  
>  Cualquier instrucción [!INCLUDE[tsql](../../includes/tsql-md.md)] válida se puede incrustar y ejecutar en un informe. La ejecución de un informe en una cuenta de usuario con privilegios elevados permite ejecutar sin problemas cualquiera de estas instrucciones incrustadas.  
  

  
## <a name="see-also"></a>Consulte también  
 [Agregar un informe personalizado a Management Studio](add-a-custom-report-to-management-studio.md)   
 [No suprimir advertencias de ejecutar informe personalizado](unsuppress-run-custom-report-warnings.md)   
 [Usar informes personalizados con las propiedades de nodo del Explorador de objetos](use-custom-reports-with-object-explorer-node-properties.md)  
  
  
