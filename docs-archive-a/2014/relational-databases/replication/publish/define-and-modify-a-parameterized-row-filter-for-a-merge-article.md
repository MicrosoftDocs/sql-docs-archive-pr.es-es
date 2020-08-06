---
title: Definición y modificación de un filtro de fila con parámetros para un artículo de mezcla | Microsoft Docs
ms.custom: ''
ms.date: 06/02/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- parameterized filters [SQL Server replication], defining
- parameterized filters [SQL Server replication], modifying
- merge replication [SQL Server replication], dynamic filters
- merge replication parameterized filters [SQL Server replication]
- filters [SQL Server replication], parameterized
- modifying filters, parameterized row
- dynamic filters [SQL Server replication]
ms.assetid: de0482a2-3cc8-4030-8a4a-14364549ac9f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d80ad53661aced22795220507398e2fcc510edd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748041"
---
# <a name="define-and-modify-a-parameterized-row-filter-for-a-merge-article"></a>Definir y modificar un filtro de fila con parámetros para un artículo de mezcla
  En este tema se describe cómo definir y modificar un filtro de fila con parámetros en [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 Al crear los artículos de la tabla, puede usar filtros de fila con parámetros. Estos filtros usan una cláusula [WHERE](/sql/t-sql/queries/where-transact-sql) para seleccionar los datos adecuados que se van a publicar. En vez de especificar un valor literal en la cláusula (como ocurre con un filtro de fila estático), se especifica una o las dos funciones del sistema siguientes: [SUSER_SNAME](/sql/t-sql/functions/suser-sname-transact-sql) y [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql). Para obtener más información, consulte [Filtros de fila con parámetros](../merge/parameterized-filters-parameterized-row-filters.md).  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitaciones y restricciones  
  
-   Si agrega, modifica o elimina un filtro de fila con parámetros una vez inicializadas las suscripciones a la publicación, deberá generar una instantánea nueva y reinicializar todas las suscripciones después de realizar el cambio. Para obtener más información sobre los requisitos para los cambios de propiedad, consulte [Cambiar las propiedades de la publicación y de los artículos](change-publication-and-article-properties.md) (Cambiar las propiedades de la publicación y de los artículos).  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Recomendaciones  
  
-   Por motivos de rendimiento, se recomienda no aplicar funciones a los nombres de columna en las cláusulas de filtro de fila con parámetros, como `LEFT([MyColumn]) = SUSER_SNAME()`. Si utiliza HOST_NAME en una cláusula de filtro y reemplaza el valor HOST_NAME, puede que sea necesario convertir los tipos de datos utilizando CONVERT. Para obtener más información acerca de las prácticas recomendadas para este caso, vea la sección "Reemplazar el valor de HOST_NAME()" del tema [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Uso de SQL Server Management Studio  
 Defina, modifique y elimine filtros de fila con parámetros en la página **Filtrar filas de tabla** del Asistente para nueva publicación o en la página **Filtrar filas** del cuadro de diálogo **Propiedades de la publicación: \<Publication>** . Para obtener más información sobre el uso del asistente y el acceso al cuadro de diálogo, consulte [Create a Publication](create-a-publication.md) (Crear una publicación) y [Ver y modificar propiedades de publicación](view-and-modify-publication-properties.md).  
  
#### <a name="to-define-a-parameterized-row-filter"></a>Para definir un filtro de fila con parámetros  
  
1.  En la página **Filtrar filas de tabla** del Asistente para nueva publicación o la página **Filtrar filas** de **Propiedades de la publicación: \<Publication>** , haga clic en **Agregar** y en **Agregar filtro**.  
  
2.  En el cuadro de diálogo **Agregar filtro** , seleccione la tabla que va a filtrar en el cuadro de lista desplegable.  
  
3.  Cree una instrucción para el filtro en el cuadro de texto **Instrucción de filtro** . Puede escribir directamente en el área de texto o puede arrastrar y colocar columnas del cuadro de lista **Columnas** .  
  
    -   El área de texto **Instrucción de filtro** incluye el texto predeterminado, que tiene este formato:  
  
        ```  
        SELECT <published_columns> FROM [tableowner].[tablename] WHERE  
        ```  
  
    -   El texto predeterminado no se puede cambiar. Escriba la cláusula del filtro después de la palabra clave WHERE utilizando la sintaxis SQL estándar. Un filtro con parámetros incluye una llamada a la función del sistema `HOST_NAME()` y/o `SUSER_SNAME()`, o una función definida por el usuario que hace referencia a una de estas funciones o a las dos. La línea siguiente es un ejemplo de una cláusula de filtro completa de un filtro de fila con parámetros:  
  
        ```  
        SELECT <published_columns> FROM [HumanResources].[Employee] WHERE LoginID = SUSER_SNAME()  
        ```  
  
         La cláusula WHERE debe usar nombres de dos partes; los nombres de tres y cuatro partes no se admiten.  
  
4.  Seleccione la opción que indique cómo se van a compartir los datos entre los suscriptores:  
  
    -   **Una fila de esta tabla irá a varias suscripciones**  
  
    -   **Una fila de esta tabla irá a una sola suscripción**  
  
     Si selecciona **Una fila de esta tabla irá a una sola suscripción**, la replicación de mezcla puede optimizar el rendimiento almacenando y procesando menos metadatos. No obstante, debe asegurarse de que los datos se particionan de forma que una fila no se pueda replicar en más de un suscriptor. Para obtener más información, vea la sección sobre cómo configurar opciones de partición en el tema [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  Si está en el cuadro de diálogo **Propiedades de la publicación: \<Publication>** , haga clic en **Aceptar** para guardar y cerrar el cuadro de diálogo.  
  
#### <a name="to-modify-a-parameterized-row-filter"></a>Para modificar un filtro de fila con parámetros  
  
1.  En la página **Filtrar filas de tabla** del Asistente para nueva publicación o la página **Filtrar filas** de **Propiedades de la publicación: \<Publication>** , seleccione un filtro en el panel **Tablas filtradas** y haga clic en **Editar**.  
  
2.  Modifique el filtro en el cuadro de diálogo **Editar filtro** .  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-delete-a-parameterized-row-filter"></a>Para eliminar un filtro de fila con parámetros  
  
1.  En la página **Filtrar filas de tabla** del Asistente para nueva publicación o la página **Filtrar filas** de **Propiedades de la publicación: \<Publication>** , seleccione un filtro en el panel **Tablas filtradas** y haga clic en **Eliminar**.  
  

  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Usar Transact-SQL  
 Los filtros de fila con parámetros se pueden crear y modificar mediante programación con los procedimientos almacenados de la replicación.  
  
#### <a name="to-define-a-parameterized-row-filter-for-an-article-in-a-merge-publication"></a>Para definir un filtro de fila con parámetros para un artículo en una publicación de combinación  
  
1.  En la base de datos de publicación del publicador, ejecute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql). Especifique **@publication** un nombre para el artículo para **@article** , la tabla que se va a publicar para **@source_object** , la cláusula WHERE que define el filtro con parámetros para **@subset_filterclause** (sin incluir `WHERE` ) y uno de los siguientes valores para **@partition_options** , que describe el tipo de particionamiento que será el resultado del filtro de fila con parámetros:  
  
    -   **0** : El filtro del artículo es estático o no produce un subconjunto de datos único para cada partición (una partición "superpuesta").  
  
    -   **1** : Las particiones resultantes son superpuestas y las actualizaciones realizadas en el suscriptor no pueden cambiar la partición a la que pertenece la fila.  
  
    -   **2** : El filtro del artículo produce particiones no superpuestas, pero varios suscriptores pueden recibir la misma partición.  
  
    -   **3** : El filtro del artículo produce particiones no superpuestas que son únicas para cada suscripción.  
  
#### <a name="to-change-a-parameterized-row-filter-for-an-article-in-a-merge-publication"></a>Para cambiar un filtro de fila con parámetros para un artículo en una publicación de combinación  
  
1.  En la base de datos de publicación del publicador, ejecute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql). Especifique **@publication** , **@article** , un valor de `subset_filterclause` para **@property** , la expresión que define el filtro con parámetros para **@value** (sin incluir `WHERE` ) y un valor de **1** para **@force_invalidate_snapshot** y **@force_reinit_subscription** .  
  
2.  Si este cambio produce un comportamiento de particionamiento diferente, a continuación, ejecute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) de nuevo. Especifique **@publication** , **@article** , un valor de `partition_options` para **@property** y la opción de particionamiento más adecuada para **@value** , que puede ser una de las siguientes:  
  
    -   **0** : El filtro del artículo es estático o no produce un subconjunto de datos único para cada partición (una partición "superpuesta").  
  
    -   **1** : Las particiones resultantes son superpuestas y las actualizaciones realizadas en el suscriptor no pueden cambiar la partición a la que pertenece la fila.  
  
    -   **2** : El filtro del artículo produce particiones no superpuestas, pero varios suscriptores pueden recibir la misma partición.  
  
    -   **3** : El filtro del artículo produce particiones no superpuestas que son únicas para cada suscripción.  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> Ejemplo (Transact-SQL)  
 En este ejemplo se define un grupo de artículos en una publicación de mezcla, donde los artículos se filtran con una serie de filtros de combinación con la tabla `Employee` que a su vez se filtra mediante un filtro de fila con parámetros en la columna **LoginID** . Durante la sincronización, el valor devuelto por la función [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql) se invalida. Para obtener más información, vea Invalidar el valor de HOST_NAME() en el tema [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).  
  
 [!code-sql[HowTo#sp_MergeDynamicPub1](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubdynamic1.sql#sp_mergedynamicpub1)]  
  
  
## <a name="see-also"></a>Consulte también  
 [Definir y modificar un filtro de combinación entre artículos de mezcla](define-and-modify-a-join-filter-between-merge-articles.md)   
 [Cambiar las propiedades de la publicación y de los artículos](change-publication-and-article-properties.md)   
 [Join Filters](../merge/join-filters.md)   
 [Filtros de fila con parámetros](../merge/parameterized-filters-parameterized-row-filters.md)  
  
  
