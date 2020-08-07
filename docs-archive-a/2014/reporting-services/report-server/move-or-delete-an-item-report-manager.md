---
title: Mover o eliminar un elemento (Administrador de informes) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- moving items
- items [Reporting Services], moving
ms.assetid: 980a66c7-a18b-4af7-8954-45726fa517d6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3a61ad56ea9e20e7fdf38d5acf05529b685ee896
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743920"
---
# <a name="move-or-delete-an-item-report-manager"></a>Mover o eliminar un elemento (Administrador de informes)
  Los informes y los elementos relacionados con los informes que se publican en un servidor de informes se almacenan en carpetas. Puede mover los elementos a una carpeta diferente, y el servidor de informes se ocupará de mantener las referencias a ellos automáticamente. Antes de eliminar un elemento, piense si otros elementos dependen de él.  
  
## <a name="move-an-item"></a>Mover un elemento  
 Puede mover elementos del servidor de informes a diversas ubicaciones de carpeta en la jerarquía de carpetas del servidor de informes. Al mover un elemento, también se mueven todas las propiedades (incluida la configuración de seguridad) a la nueva ubicación. Cuando mueve una carpeta, se mueven todos los elementos de la carpeta.  
  
 En el Administrador de informes, los elementos que se pueden mover aparecen indicados en la jerarquía de carpetas. La siguiente tabla muestra el icono correspondiente a cada uno de los elementos que se pueden mover.  
  
|Icono|Elemento que puede moverse|  
|----------|-------------------|  
|![Report icon](../media/hlp-16doc.gif "Icono de informe")|Informe|  
|![Icono de informe vinculado](../media/hlp-16linked.gif "Icono de informe vinculado")|Informe vinculado|  
|![Icono de carpeta](../media/hlp-16folder.gif "Icono de carpeta")|Carpeta|  
|![Icono de recurso genérico](../media/hlp-16file.gif "Icono de recurso genérico")|Recurso genérico|  
|![Shared data source icon](../media/hlp-16datasource.png "Icono de origen de datos compartido")|Origen de datos compartido|  
||Conjunto de datos compartidos|  
  
 No todos los elementos se pueden mover. Por ejemplo, los elementos asociados a un informe, tales como las suscripciones o el historial del informe, no pueden moverse. Estos elementos se mueven con los informes asociados. Asimismo, tampoco pueden moverse elementos como las programaciones compartidas que existen fuera de la jerarquía de carpetas. No pueden moverse elementos para los que no se tienen los permisos adecuados. Este permiso se concede mediante la selección de las siguientes tareas durante la asignación de roles del elemento en cuestión: "Administrar informes", "Administrar modelos", "Administrar carpetas" y "Administrar orígenes de datos".  
  
#### <a name="to-move-an-item-from-within-the-contents-page"></a>Para mover un elemento de la página Contenido  
  
1.  Iniciar [Administrador de informes &#40;modo nativo de SSRS&#41;].. /report-manager-ssrs-native-mode.md).  
  
2.  En el Administrador de informes, navegue a la página **Contenido** y localice el elemento que desee mover.  
  
3.  Mantenga el mouse sobre el elemento y haga clic en la flecha de lista desplegable.  
  
4.  En el menú desplegable, haga clic en **Mover**.  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  Para **Ubicación**, especifique la carpeta a la que desea mover el elemento. Puede escribir el nombre completo de la carpeta o utilizar el control de árbol para navegar hasta la carpeta.  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 O bien puede navegar hasta el objeto que desea mover, hacer clic en **Propiedades**y, a continuación, en **Mover** al principio de la página.  
  
## <a name="delete-an-item"></a>Eliminación de un elemento  
 Antes de eliminar un elemento, piense si lo utilizan otros elementos. Por ejemplo, si elimina un origen de datos compartido, ya no se ejecutarán los informes y los modelos que usan dicho origen de datos. Si elimina un informe, también se eliminarán las suscripciones y el historial de informes asociado a dicho informe. Para buscar elementos dependientes de un elemento, vea [Página de elementos dependientes &#40;Administrador de informes&#41;].. /dependent-items-page-report-manager.md).  
  
#### <a name="to-delete-a-report-or-item"></a>Para eliminar un informe o un elemento  
  
1.  Iniciar [Administrador de informes &#40;modo nativo de SSRS&#41;].. /report-manager-ssrs-native-mode.md).  
  
2.  En el Administrador de informes, navegue a la página **Contenido** y localice el elemento que desee eliminar.  
  
3.  Mantenga el mouse sobre el elemento y haga clic en la flecha de lista desplegable.  
  
4.  En el menú desplegable, haga clic en **Eliminar**.  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Consulte también  
 [Página de contenido &#40;Administrador de informes&#41;].. /contents-page-report-manager.md)   
 [Buscar, ver y administrar informes &#40;Generador de informes y SSRS&#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
