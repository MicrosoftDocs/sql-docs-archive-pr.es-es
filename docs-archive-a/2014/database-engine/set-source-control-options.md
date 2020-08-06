---
title: Establecer opciones de control de código fuente | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Source_Control.Visual_SourceSafe
- VS.ToolsOptionsPages.Source_Control.General
- VS.ToolsOptionsPages.Source_Control.Environment
helpviewer_keywords:
- source controls [SQL Server Management Studio], options
ms.assetid: b2c6ca00-46f0-4f86-b067-07bae779c147
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d4ca19180a7291763780f300172bb2292a98c8c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663090"
---
# <a name="set-source-control-options"></a>Establecer las opciones de control de código fuente
  Antes de aprovechar las características de control de código fuente integradas en [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], es necesario configurar las opciones de control de código fuente de los diversos entornos en los que trabaje.  
  
 Las opciones de control de código fuente se configuran mediante el cuadro de diálogo **Opciones** para configurar uno o varios roles de control de código fuente. Un rol se compone de una descripción general de la configuración en la que se utiliza [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] y las opciones de control de código fuente asociadas a esa configuración.  
  
 Por ejemplo, si es desarrollador de software de bases de datos independiente, normalmente no crea conflictos con otros usuarios al conservar los archivos desprotegidos después de haberlos protegido. En consecuencia, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] define un rol de desarrollador de software independiente. Para este rol, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] selecciona automáticamente la opción **mantener los elementos desprotegidos al proteger** .  
  
 Puesto que puede definir y personalizar roles, puede trabajar en diversas configuraciones de desarrollo sin necesidad de volver a configurar completamente el control de código fuente cada vez que pasa de una configuración a otra.  
  
### <a name="to-set-source-control-options"></a>Para establecer las opciones de control de código fuente  
  
1.  En el menú **Herramientas** , haga clic en **Opciones**.  
  
2.  En el cuadro de diálogo **Opciones** , expanda **control de código fuente**y, a continuación, haga clic en la página **selección de complemento** .  
  
     **Complemento de control de código fuente actual**  
     Seleccione en esta lista el control de código fuente que desee utilizar. El cliente del producto de control de código fuente deberá estar instalado en este equipo para que aparezca en la lista. Si no hay ningún cliente de control de código fuente instalado en el equipo, la única selección disponible será Ninguno. Si ha instalado Microsoft Source Safe, los siguientes complementos se mostrarán a continuación:  
  
    -   Microsoft Visual SourceSafe  
  
    -   Microsoft Visual SourceSafe (Internet)  
  
3.  Establezca las credenciales de inicio de sesión de cada rol de control de código fuente que desee usar. Esta página solo está disponible si está instalado un complemento de control de código fuente.  
  
     **Descripción de rol**  
     La selección de uno de estos roles hace que las opciones de control de código fuente correspondientes se seleccionen automáticamente.  
  
    |Role|Descripción|  
    |----------|-----------------|  
    |**Visual SourceSafe**|Especifica que desea usar la configuración que usan normalmente [!INCLUDE[msCoName](../includes/msconame-md.md)] los usuarios de Visual SourceSafe.|  
    |**Programador independiente**|Especifica que el usuario está realizando su trabajo de forma independiente.|  
    |**Custom**|Especifica que el usuario ha modificado la configuración de un rol.|  
  
     **Realizar en segundo plano las actualizaciones de estado**  
     Actualiza automáticamente los iconos de señal del control de código fuente en el Explorador de soluciones cuando cambia el estado de un elemento. Si se producen retrasos al realizar operaciones que consumen muchos recursos del servidor, en especial cuando abre una solución o un proyecto desde el control de código fuente, la desactivación de esta casilla puede mejorar el rendimiento.  
  
     **Id. de inicio de sesión**  
     Especifica el nombre de usuario que se va a utilizar para iniciar la sesión en el proveedor del control de código fuente. Si el proveedor de control de código fuente lo admite, este nombre se rellenará automáticamente en el cuadro de diálogo de **Inicio de sesión** para llegar al servidor de control de código fuente. Para activar esta opción, utilice el programa de administrador del proveedor del control de código fuente para deshabilitar los inicios de sesión automáticos y reinicie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
     **Avanzadas**  
     Muestra opciones adicionales para agregar elementos al control de código fuente. Estas opciones dependen del proveedor del control de código fuente. En el programa del control de código fuente dispone de ayuda para estas opciones.  
  
4.  Seleccione la página **entorno** .  
  
5.  En el cuadro **configuración del entorno de control de código fuente** , seleccione el rol en el que desea establecer las opciones de control de código fuente.  
  
     [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] activa automáticamente las opciones de control de código fuente del rol que ha seleccionado. Si desactiva cualquiera de las opciones predeterminadas, el cuadro **configuración del entorno de control de código fuente** muestra la opción **personalizada** para indicar que ha personalizado el rol seleccionado originalmente.  
  
     **Configuración del entorno de control de código fuente**  
     Especifica el rol que se desea utilizar. [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] define los siguientes roles.  
  
    |Role|Descripción|  
    |----------|-----------------|  
    |**Visual SourceSafe**|Especifica que desea usar la configuración que usan normalmente [!INCLUDE[msCoName](../includes/msconame-md.md)] los usuarios de Visual SourceSafe.|  
    |**Programador independiente**|Especifica que el usuario está realizando su trabajo de forma independiente.|  
    |**Custom**|Especifica que el usuario ha modificado la configuración de un rol.|  
  
     La selección de uno de estos roles hace que las opciones de control de código fuente correspondientes se seleccionen automáticamente.  
  
     **Mantener elementos desprotegidos cuando se protejan**  
     Especifica que cuando el usuario proteja elementos para actualizar el almacén de control de código fuente, los elementos deben permanecer desprotegidos para el usuario. Si desea cambiar esta opción para una protección específica, haga clic en la flecha **Opciones** del cuadro de diálogo **proteger** y desactive la casilla **Mantener desprotegido** .  
  
     **Elementos protegidos**  
     Muestra una lista de opciones que especifican cómo [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] debe comportarse al intentar editar un elemento que no está desprotegido. En las tablas siguientes se describen las opciones disponibles.  
  
     **Guardando**  
  
    |Acción|Descripción|  
    |------------|-----------------|  
    |**Preguntar para desproteger**|Muestra el cuadro de diálogo **Desproteger** .|  
    |**Desproteger automáticamente**|Desprotege el elemento sin mostrar el cuadro de diálogo **Desproteger** . Ésta es la opción predeterminada.|  
    |**Guardar como**|Guarda como un nuevo archivo.|  
  
     **Edición**  
  
    |Acción|Descripción|  
    |------------|-----------------|  
    |**Preguntar para desproteger**|Muestra el cuadro de diálogo **Desproteger** .|  
    |**Solicitar desprotecciones exclusivas**|Muestra el cuadro de diálogo **Desproteger** .|  
    |**Desproteger automáticamente**|Desprotege el elemento sin mostrar el cuadro de diálogo **Desproteger** . Ésta es la opción predeterminada.|  
    |**No hacer nada**|No desprotege el archivo.|  
  
     **Permitir que los elementos protegidos se puedan editar**  
     Especifica que los elementos que están protegidos puedan editarse en la memoria. Si activa esta casilla, aparece un botón **Editar** en el cuadro de diálogo **Desproteger** al intentar editar un elemento protegido. Después de hacer clic en este botón, podrá editar el elemento. Si intenta guardar el elemento, deberá desprotegerlo o guardarlo en una ubicación distinta.  
  
     **Reset**  
     Restablece los cuadros de diálogo de confirmación de control de código fuente a sus valores predeterminados. Por ejemplo, si ha seleccionado la casilla **no volver a mostrar este** cuadro de diálogo en un cuadro de diálogo de control de código fuente, al seleccionar la opción **restablecer** se invierte esa acción.  
  
## <a name="see-also"></a>Consulte también  
 [Aspectos básicos del control de código fuente](../../2014/database-engine/source-control-basics.md)   
 [Cambiar las conexiones del control de código fuente](../../2014/database-engine/change-source-control-connections.md)   
 [Excluir archivos desde el control de código fuente](../../2014/database-engine/exclude-files-from-source-control.md)  
  
  
