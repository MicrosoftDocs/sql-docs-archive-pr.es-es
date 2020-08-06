---
title: Cambiar control de código fuente | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- IDD_SCC_CONNECTION_DIALOG
helpviewer_keywords:
- Change Source Control dialog box
ms.assetid: e6a5d83c-5809-4c56-907a-73d0c7ccdd7a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 55831529243608e8c71972a31009e5672fb0234f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674361"
---
# <a name="change-source-control"></a>Cambiar el control de código fuente
  Crea y administra las conexiones y los enlaces que vinculan una solución o un proyecto guardados localmente con una carpeta de la base de datos de control de código fuente.  
  
## <a name="dialog-box-access"></a>Acceso al cuadro de diálogo  
 En [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], seleccione un elemento en el Explorador de soluciones. En el menú **Archivo** , haga clic en **Control de código fuente**y en **Cambiar control de código fuente**.  
  
> [!NOTE]  
>  También se puede obtener acceso a este cuadro de diálogo haciendo clic con el botón secundario en el elemento, en el Explorador de soluciones.  
  
## <a name="options"></a>Opciones  
 **Volver**  
 Asocie elementos seleccionados con una ubicación del servidor de control de código fuente. Por ejemplo, puede utilizar este botón para enlazar con las últimas carpetas y bases de datos conocidas del servidor de control de código fuente. Si no encuentra una base de datos o una carpeta del servidor recientes, se le indicará que especifique otras.  
  
 **Browse**  
 Navegue a una nueva ubicación del servidor de control de código fuente del elemento especificado.  
  
 **Columnas**  
 Identifique las columnas que se mostrarán y el orden en el que deben aparecer.  
  
 **Conexión**  
 Cree una conexión entre los elementos seleccionados y el servidor de control de código fuente.  
  
 **Conectada**  
 Muestra el estado de conexión de una solución o un proyecto seleccionados.  
  
 **Desconexión**  
 Desconecte la copia local de una solución o un proyecto del equipo de su copia maestra en la base de datos. Utilice este comando antes de dejar sin conexión el equipo del servidor de control de código fuente, por ejemplo, al trabajar sin conexión en su equipo portátil.  
  
 **OK (CORRECTO)**  
 Acepta los cambios realizados en el cuadro de diálogo.  
  
 **Proveedor**  
 Muestra el nombre del complemento de control de código fuente.  
  
 **Actualizar**  
 Actualiza la información de conexión de todos los proyectos que aparecen en este cuadro de diálogo.  
  
 **Enlace del servidor**  
 Indica el enlace del elemento con un servidor de control de código fuente.  
  
 **Nombre de servidor**  
 Muestra el nombre del servidor de control de código fuente con el que están enlazados el proyecto o la solución correspondientes.  
  
 **Solución/Proyecto**  
 Muestra el nombre de cada solución y proyecto de la selección actual.  
  
 **Sort**  
 Ordena las columnas mostradas.  
  
 **Estado**  
 Identifica el estado de conexión y enlace de un elemento. Las opciones posibles son:  
  
|**Opción**|**Descripción**|  
|----------------|---------------------|  
|Válido|El elemento está correctamente enlazado y conectado con la carpeta de servidor a la que pertenece.|  
|No válida|El elemento no está correctamente enlazado o está desconectado de la carpeta a la que pertenece. Utilice el comando **Agregar a control de código fuente** en lugar de **Enlazar** para este elemento.|  
|Desconocido|El estado del elemento en el control de código fuente no se ha determinado todavía.|  
|No controlado|El elemento no se ha colocado en el control de código fuente.|  
  
 **Desenlace**  
 Muestra el cuadro de diálogo **Control de código fuente** para permitirle eliminar los elementos seleccionados del control de código fuente y anular definitivamente la asociación de los elementos con sus carpetas actuales.  
  
## <a name="see-also"></a>Consulte también  
 [Control de código fuente del Explorador de soluciones](../../2014/database-engine/solution-explorer-source-control.md)  
  
  
