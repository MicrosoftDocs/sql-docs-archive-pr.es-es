---
title: Generar automáticamente un conjunto de filtros de combinación entre artículos de mezcla (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- automatic join filter generation
- join filters
ms.assetid: 7ef419f4-c17f-42a5-9068-174a3ec08941
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4bfdbf93aad134e4da873a6aade307754a2637e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661908"
---
# <a name="automatically-generate-a-set-of-join-filters-between-merge-articles-sql-server-management-studio"></a>Generar automáticamente un conjunto de filtros de combinación entre artículos de mezcla (SQL Server Management Studio)
  Genere automáticamente un conjunto de filtros de combinación en la página **Filtrar filas de tabla** del Asistente para nueva publicación o en la página **Filtrar filas** del cuadro de diálogo **Propiedades de la publicación: \<Publication>** . Para obtener más información sobre el uso del asistente y el acceso al cuadro de diálogo, consulte [Create a Publication](create-a-publication.md) (Crear una publicación) y [Ver y modificar propiedades de publicación](view-and-modify-publication-properties.md).  
  
> [!NOTE]  
>  Si genera automáticamente un conjunto de filtros de combinación en el cuadro de diálogo **Propiedades de la publicación: \<Publication>** después de haber inicializado las suscripciones para la publicación, deberá generar una nueva instantánea y volver a inicializar todas las suscripciones una vez realizado el cambio. Para obtener más información sobre los requisitos para los cambios de propiedad, consulte [Cambiar las propiedades de la publicación y de los artículos](change-publication-and-article-properties.md) (Cambiar las propiedades de la publicación y de los artículos).  
  
 Es posible crear filtros de combinación para un conjunto de tablas de forma manual, o bien la replicación puede generar los filtros de forma automática en función de las relaciones de clave clave externa a clave principal definidas en las tablas. Para obtener más información sobre cómo crear filtros de combinación manualmente, consulte [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md) (Definir y modificar un filtro de combinación entre artículos de mezcla).  
  
### <a name="to-automatically-generate-a-set-of-join-filters-between-merge-articles"></a>Para generar automáticamente un conjunto de filtros de combinación entre artículos de mezcla  
  
1.  En la página **Filtrar filas de tabla** del Asistente para nueva publicación o la página **Filtrar filas** del cuadro de diálogo **Propiedades de la publicación: \<Publication>** , haga clic en **Agregar** y luego en **Generar filtros automáticamente**.  
  
    > [!NOTE]  
    >  Al generar filtros automáticamente, se eliminan los filtros de fila o los filtros de combinación existentes en la publicación. Es posible agregar filtros después de haber generado automáticamente un conjunto de filtros.  
  
2.  Siga el proceso del cuadro de diálogo **Generar filtros** para crear un filtro de fila. A continuación, el filtro de fila se amplía a las tablas relacionadas con la tabla filtrada por medio de las relaciones de clave principal y clave externa.  
  
    1.  Seleccione una tabla para filtrar en la lista desplegable.  
  
    2.  Cree una instrucción para el filtro en el cuadro de texto **Instrucción de filtro** . Puede escribir directamente en el área de texto o puede arrastrar y colocar columnas del cuadro de lista **Columnas** .  
  
         El área de texto **Instrucción de filtro** incluye el texto predeterminado, que tiene este formato:  
  
        ```  
        SELECT <published_columns> FROM [tableowner].[tablename] WHERE  
        ```  
  
         El texto predeterminado no se puede modificar; escriba la cláusula de filtro para un filtro de fila estático o un filtro de fila con parámetros después de la palabra clave WHERE mediante la sintaxis SQL estándar. La cláusula de filtro completa para un filtro de fila con parámetros sería similar a la siguiente:  
  
        ```  
        SELECT <published_columns> FROM [HumanResources].[Employee] WHERE LoginID = SUSER_SNAME()  
        ```  
  
         La cláusula WHERE debe usar nombres de dos partes; los nombres de tres y cuatro partes no se admiten.  
  
    3.  Especifique las opciones del filtro.  
  
         Seleccione la opción que indique cómo se van a compartir los datos entre los suscriptores: **Una fila de esta tabla irá a varias suscripciones** o **Una fila de esta tabla irá a una sola suscripción**. Si selecciona **Una fila de esta tabla irá a una sola suscripción**, la replicación de mezcla puede optimizar el rendimiento almacenando y procesando menos metadatos. No obstante, debe asegurarse de que los datos se particionan de forma que una fila no se pueda replicar en más de un suscriptor. Para obtener más información, vea la sección sobre cómo configurar opciones de partición en el tema [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     El filtro que ha especificado se analiza y se ejecuta según la tabla de la cláusula SELECT. Si la instrucción de filtro contiene errores de sintaxis u otros problemas, se le notificará y podrá modificar dicha instrucción.  
  
     Una vez analizada la instrucción, la replicación crea los filtros de combinación necesarios y los muestra en el panel **Tablas filtradas** de la página **Filtrar filas de tabla** o **Filtrar filas** . Si genera filtros desde el Asistente para nueva publicación y aún no ha configurado el distribuidor para el publicador en el que se ejecuta este asistente, se le pedirá que lo haga.  
  
4.  Si está en el cuadro de diálogo **Propiedades de la publicación: \<Publication>** , haga clic en **Aceptar** para guardar y cerrar el cuadro de diálogo.  
  
### <a name="to-modify-a-filter-that-was-automatically-generated"></a>Para modificar un filtro generado automáticamente  
  
1.  En la página **Filtrar filas de tabla** del Asistente para nueva publicación o en la página **Filtrar filas** de **Propiedades de la publicación: \<Publication>** , seleccione un filtro en el panel **Tablas filtradas** y luego haga clic en **Editar**.  
  
2.  En el cuadro de diálogo **Editar filtro** o **Editar combinación** , modifique el filtro.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-filter-that-was-automatically-generated"></a>Para eliminar un filtro generado automáticamente  
  
1.  En la página **Filtrar filas de tabla** del Asistente para nueva publicación o en la página **Filtrar filas** de **Propiedades de la publicación: \<Publication>** , seleccione un filtro en el panel **Tablas filtradas** y luego haga clic en **Eliminar**.  
  
## <a name="see-also"></a>Consulte también  
 [Join Filters](../merge/join-filters.md)   
 [Filtros de fila con parámetros](../merge/parameterized-filters-parameterized-row-filters.md)  
  
  
