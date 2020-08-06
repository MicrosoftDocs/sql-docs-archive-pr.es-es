---
title: Crear parámetros | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.parameterwindow.f1
ms.assetid: cd5d675b-dd5d-49cc-8b1f-dc717a973f99
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a26ae08c08a32b0593be8c9a2777b7cfe9c884fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669784"
---
# <a name="create-parameters"></a>Creación de parámetros
  Puede usar [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] para crear parámetros de proyecto y parámetros de paquete. Los procedimientos siguientes proporcionan instrucciones paso a paso para crear parámetros de paquete o proyecto.  
  
> [!NOTE]  
>  Si va a convertir un proyecto que creó utilizando una versión anterior de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] al modelo de implementación de proyectos, puede utilizar el **Asistente para conversión de proyectos de Integration Services** para crear parámetros de acuerdo con las configuraciones. Para más información, consulte [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).  
  
### <a name="to-create-package-parameters"></a>Para crear parámetros de paquete  
  
1.  Abra el paquete en [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]y después haga clic en la pestaña **Parámetros** del Diseñador SSIS.  
  
     ![Pestaña Parámetros de paquete](media/denali-package-parameters.gif "Pestaña Parámetros de paquete")  
  
2.  Haga clic en el botón **Agregar parámetro** de la barra de herramientas.  
  
     ![Botón Agregar barra de herramientas](media/denali-parameter-add.gif "Agregar botón de la barra de herramientas")  
  
3.  Escriba valores para las propiedades **Nombre**, **Tipo de datos**, **Valor**, **Con distinción**y **Obligatorio** en la propia lista o en la ventana **Propiedades** . Estas propiedades se describen en la tabla siguiente.  
  
    |Propiedad|Descripción|  
    |--------------|-----------------|  
    |Nombre|Nombre del parámetro.|  
    |Tipo de datos|El tipo de datos del parámetro.|  
    |Valor predeterminado|Valor predeterminado para el parámetro asignado en tiempo de diseño. También se conoce como valor predeterminado de diseño.|  
    |Sensible|Los valores de parámetros con distinción se cifran en el catálogo y aparecen como valor NULL cuando se ven con Transact-SQL o SQL Server Management Studio.|  
    |Obligatorio|Requiere que un valor, distinto del valor predeterminado de diseño, se especifique antes de que el paquete se ejecute.|  
    |Descripción|Descripción del parámetro en cuanto a capacidad de mantenimiento. En [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], establezca la descripción del parámetro en la ventana Propiedades de Visual Studio cuando el parámetro esté seleccionado en la ventana de parámetros aplicable.|  
  
    > [!NOTE]  
    >  Cuando se implementa un proyecto en el catálogo, algunas propiedades más se asocian al proyecto. Para ver todas las propiedades de todos los parámetros del catálogo, use la vista [catalog.object_parameters &#40;base de datos de SSISDB&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database).  
  
4.  Guarde el proyecto para guardar los cambios realizados en los parámetros. Los valores de parámetro se almacenan en el archivo de proyecto.  
  
    > [!WARNING]  
    >  Puede realizar modificaciones en contexto en la lista o utilizar la ventana **Propiedades** para modificar los valores de las propiedades de parámetro. Puede eliminar un parámetro con el botón de la barra de herramientas **Eliminar (x)** . Con el último botón de la barra de herramientas, puede especificar un valor para un parámetro que se utilice solo cuando se ejecute el paquete en [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
    > [!NOTE]  
    >  Si abre de nuevo el archivo del paquete sin abrir el proyecto en [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], la pestaña **Parámetros** estará vacía y deshabilitada.  
  
### <a name="to-create-project-parameters"></a>Para crear parámetros del proyecto  
  
1.  Abra el proyecto en [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
2.  En el Explorador de soluciones, haga clic con el botón secundario en **Project.params** y, a continuación, haga clic en **Abrir** , o haga doble clic en **Project.params** para abrirlo.  
  
     ![Ventana Parámetros del proyecto](media/denali-project-parameters.gif "Ventana Parámetros del proyecto")  
  
3.  Haga clic en el botón **Agregar parámetro** de la barra de herramientas.  
  
     ![Botón Agregar barra de herramientas](media/denali-parameter-add.gif "Agregar botón de la barra de herramientas")  
  
4.  Escriba valores para las propiedades **Nombre**, **Tipo de datos**, **Valor**, **Con distinción**y **Obligatorio** .  
  
    |Propiedad|Descripción|  
    |--------------|-----------------|  
    |Nombre|Nombre del parámetro.|  
    |Tipo de datos|El tipo de datos del parámetro.|  
    |Valor predeterminado|Valor predeterminado para el parámetro asignado en tiempo de diseño. También se conoce como valor predeterminado de diseño.|  
    |Sensible|Los valores de parámetros con distinción se cifran en el catálogo y aparecen como valor NULL cuando se ven con Transact-SQL o SQL Server Management Studio.|  
    |Obligatorio|Requiere que un valor, distinto del valor predeterminado de diseño, se especifique antes de que el paquete se ejecute.|  
    |Descripción|Descripción del parámetro en cuanto a capacidad de mantenimiento. En [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], establezca la descripción del parámetro en la ventana Propiedades de Visual Studio cuando el parámetro esté seleccionado en la ventana de parámetros aplicable.|  
  
5.  Guarde el proyecto para guardar los cambios realizados en los parámetros. Los valores de parámetro se almacenan en configuraciones en el archivo de proyecto. Guarde el archivo de proyecto para confirmar en el disco los cambios en los valores de parámetro.  
  
    > [!WARNING]  
    >  Puede realizar modificaciones en contexto en la lista o utilizar la ventana **Propiedades** para modificar los valores de las propiedades de parámetro. Puede eliminar un parámetro con el botón de la barra de herramientas **Eliminar (x)** . Con el último botón de la barra de herramientas que es para abrir el cuadro de diálogo **Administrar valores de parámetro** , puede especificar un valor para un parámetro que se use solamente cuando se ejecuta el paquete en [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
## <a name="see-also"></a>Consulte también  
 [Integration Services &#40;los parámetros de&#41; SSIS](integration-services-ssis-package-and-project-parameters.md)  
  
  
