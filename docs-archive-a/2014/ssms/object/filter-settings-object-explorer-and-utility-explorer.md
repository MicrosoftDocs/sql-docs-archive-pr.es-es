---
title: Configuración de filtro (Explorador de objetos y Explorador de Utilidad) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.filtersettings.f1
- sql12.swb.common.filtersettings.f1
ms.assetid: 4aab04bc-e1ab-4d4b-ab74-b287fc805bc2
author: stevestein
ms.author: sstein
ms.openlocfilehash: c31fbcbef9cbab86a7bd3ab7b2fae21e626aaa59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661767"
---
# <a name="filter-settings-object-explorer-and-utility-explorer"></a>Configuración de filtro (Explorador de objetos y Explorador de la utilidad)
  Utilice este cuadro de diálogo para especificar un filtro. Un filtro permite configurar el Explorador de objetos y el Explorador de la utilidad para mostrar únicamente los elementos que cumplen criterios específicos. Por ejemplo, puede utilizar un filtro para mostrar solo los trabajos con nombres que contienen la palabra "Mantenimiento". El encabezado del cuadro de diálogo **Configuración del filtro** contiene el nombre del servidor y puede contener el nombre de la base de datos.  
  
## <a name="ui-element-list"></a>Lista de elementos de la interfaz de usuario  
 **Propiedad**  
 Muestra la propiedad que se va filtrar.  
  
 **Operador**  
 Seleccione la forma en que el filtro va a aplicar el valor a la propiedad. Existen las siguientes opciones:  
  
-   **Es igual a**  
  
     El filtro muestra los elementos en los que la propiedad y el valor coinciden plenamente.  
  
-   **Contains**  
  
     El filtro muestra los elementos en los que la propiedad contiene el valor. La propiedad puede contener otro texto.  
  
-   **No contiene**  
  
     El filtro muestra los elementos en los que la propiedad no contiene el valor.  
  
-   **Menor que**  
  
     Disponible para fechas; este filtro muestra los elementos cuya fecha es anterior al valor proporcionado.  
  
-   **Menor que o igual a**  
  
     Disponible para fechas; este filtro muestra los elementos cuya fecha es igual o anterior al valor proporcionado.  
  
-   **Mayor que**  
  
     Disponible para fechas; este filtro muestra los elementos cuya fecha es posterior al valor proporcionado.  
  
-   **Mayor que o igual a**  
  
     Disponible para fechas; este filtro muestra los elementos cuya fecha es igual o posterior al valor proporcionado.  
  
-   **Entre**  
  
     Disponible para fechas; este filtro muestra los elementos cuya fecha se encuentra entre dos fechas proporcionadas. Seleccione **Entre** y presione la tecla TAB para agregar otra fila a fin de escribir la segunda fecha.  
  
-   **No entre**  
  
     Disponible para fechas; este filtro muestra los elementos cuya fecha es anterior o posterior a dos fechas proporcionadas. Seleccione **No entre** y salga de la columna **Operador** para agregar otra fila a fin de escribir la segunda fecha.  
  
 **Valor**  
 Escriba el valor que va a compararse con la propiedad. Para seleccionar una fecha, haga clic en la flecha abajo para que aparezca un calendario donde seleccionarla.  
  
 **Borrar filtro**  
 Elimina toda la configuración actual del filtro.  
  
## <a name="see-also"></a>Consulte también  
 [Usar SQL Server Management Studio](../sql-server-management-studio-ssms.md)   
 [Características y tareas de la utilidad de SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  
