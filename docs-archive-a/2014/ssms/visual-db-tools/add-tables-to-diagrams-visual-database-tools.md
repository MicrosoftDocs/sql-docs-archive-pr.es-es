---
title: Agregar tablas a diagramas (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting tables
- adding tables
ms.assetid: 5440fdf7-ac04-4325-9f32-181f4cd402e5
author: stevestein
ms.author: sstein
ms.openlocfilehash: fe5c1274ac390f4834bd8ac1088258061fc0406d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673430"
---
# <a name="add-tables-to-diagrams-visual-database-tools"></a>Agregar tablas a diagramas (Visual Database Tools)
  Puede agregar una tabla al diagrama de base de datos para editar su estructura o para relacionarla con otras tablas del diagrama. Puede agregar tablas de base de datos existentes a un diagrama o insertar una tabla nueva aún no definida en la base de datos.  
  
### <a name="to-insert-a-new-table-into-a-diagram"></a>Para insertar una tabla nueva en un diagrama  
  
1.  Asegúrese de que está conectado a la base de datos en la que desea crear la tabla.  
  
     Para crear una tabla en el diagrama actual, haga clic en el botón **Nueva tabla** de la barra de herramientas.  
  
     O bien  
  
     Haga clic con el botón derecho en el diagrama y seleccione **Nueva tabla**.  
  
2.  Modifique o acepte el nombre de tabla asignado por el sistema en el cuadro de diálogo **Elegir nombre** y, luego, elija **Aceptar**.  
  
     Aparecerá una tabla nueva en el diagrama, en la vista Estándar.  
  
3.  Escriba en la primera celda de la tabla nueva un nombre de columna. A continuación, presione la tecla TAB para pasar a la celda siguiente.  
  
4.  En **Tipo de datos**, seleccione el tipo de datos de la columna. Todas las columnas deben tener nombre y tipo de datos.  
  
     Puede definir otras propiedades de la columna en el Diseñador de tablas.  
  
5.  Repita los pasos 3 y 4 para cada columna que desee agregar a la tabla.  
  
> [!NOTE]  
>  Cuando guarde el diagrama de base de datos, se agregará la nueva tabla a la base de datos.  
  
### <a name="to-add-an-existing-table-to-a-diagram"></a>Para agregar una tabla existente a un diagrama  
  
1.  Asegúrese de que está conectado a la base de datos cuyas tablas desea editar.  
  
2.  Seleccione una tabla de la carpeta **Tablas** .  
  
3.  Arrastre la tabla al diagrama de la base de datos.  
  
4.  Suelte el botón del mouse (ratón).  
  
> [!NOTE]  
>  Si hay relaciones entre la tabla seleccionada y otras tablas del diagrama, se dibujarán automáticamente las líneas de las relaciones.  
  
### <a name="to-add-related-tables-to-a-diagram"></a>Para agregar tablas relacionadas a un diagrama  
  
1.  Seleccione una o más tablas con restricciones FOREIGN KEY en el diagrama de base de datos.  
  
2.  Haga clic con el botón derecho en cualquiera de las tablas seleccionadas y elija **Agregar tablas relacionadas**.  
  
> [!NOTE]  
>  Se agregan al diagrama tanto las tablas a las que hace referencia una restricción FOREIGN KEY de las tablas seleccionadas como las que hacen referencia a las tablas seleccionadas mediante una restricción FOREIGN KEY.  
  
## <a name="see-also"></a>Consulte también  
 [Trabajar con diagramas de base de datos &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Trabajar con tablas en diagramas de base de datos &#40;Visual Database Tools&#41;](work-with-tables-in-database-diagram-visual-database-tools.md)  
  
  
