---
title: Migrar scripts a VSTA | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SSIS Script task, converting scripts
- Script component [Integration Services], converting scripts
- Script task [Integration Services], converting scripts
- SSIS Script component, converting scripts
ms.assetid: d685098b-86a1-46bf-939a-63d56951e009
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: afbc19c35f99a5abc5a6ebd92024e42baa6a9237
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87749598"
---
# <a name="migrate-scripts-to-vsta"></a>Migrar scripts a VSTA
  Al actualizar [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] paquetes a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] migra los scripts de las tareas script o los componentes script a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA). VSTA es el entorno de script que [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usa. En [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , el entorno de scripting para [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] es [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para aplicaciones (VSA).  
  
 Si los scripts en las tareas Script o los componentes Script hacen referencia a las interfaces, podría tener que modificar esas referencias antes de actualizar el paquete. De lo contrario, el paquete no se podrá actualizar o los scripts no se podrán validar, dependiendo del método de actualización que use. Para modificar estas referencias, reemplace las referencias a las interfaces IDTS*xxx*90 por referencias a las interfaces IDTS*XXX*100 correspondientes.  
  
 Para obtener más información sobre cómo migrar scripts y actualizar paquetes, vea [actualizar paquetes de Integration Services](../../integration-services/install-windows/upgrade-integration-services-packages.md).  
  
## <a name="understanding-migration-failures"></a>Descripción de los errores de migración  
 Al migrar los scripts, se puede producir un error en la migración debido a una de las razones siguientes:  
  
-   Se cambió el nombre del punto de entrada para el script de VSA.  
  
     El punto de entrada especifica el método en la clase `ScriptMain` en el proyecto de VSTA que el tiempo de ejecución de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] llama como punto de entrada al código de la tarea Script. La clase `ScriptMain` es la clase predeterminada que las plantillas de script generan.  
  
-   No hay ningún punto de entrada o hay varios en el script de VSA.  
  
-   No se pudieron agregar referencias de ensamblado.  
  
-   Se modificó la clase `ScriptMain` para heredar de otras clases además de la clase `ScriptObjectModelSSIS`. [!INCLUDE[msCoName](../../includes/msconame-md.md)]no [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] admite la herencia múltiple.  
  
 No se puede convertir un script de VSA que use [!INCLUDE[vbprvblong](../../includes/vbprvblong-md.md)] en un script de VSTA que use [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)] . Sin embargo, puede crear un nuevo script de VSTA que use [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)] . Para obtener más información, consulte [Codificar y depurar la tarea Script](../../integration-services/control-flow/script-task.md) y [Codificar y depurar el componente de script](../../integration-services/data-flow/transformations/script-component.md).  
  
## <a name="see-also"></a>Consulte también  
 [Ampliar paquetes con scripting](../../relational-databases/server-management-objects-smo/tasks/scripting.md)  
  
  
