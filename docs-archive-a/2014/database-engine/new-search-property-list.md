---
title: Nueva lista de propiedades de búsqueda | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.spl.newsearchpropertylist.f1
ms.assetid: ffca78e9-8608-4b15-bd38-b2d78da4247a
author: rothja
ms.author: jroth
ms.openlocfilehash: 48c9e475b380d5f0c7310e33717f261c38acbbd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676648"
---
# <a name="new-search-property-list"></a>Nueva lista de propiedades de búsqueda
  Utilice este cuadro de diálogo para crear una lista de propiedades de búsqueda.  
  
## <a name="options"></a>Opciones  
 **Nombre de lista de propiedades de búsqueda**  
 Escriba el nombre de la lista de propiedades de búsqueda.  
  
 **Propietario**  
 Especifique el propietario de la lista de propiedades de búsqueda. Si desea que la propiedad se asigne a usted, es decir, al usuario actual, deje vacío este campo. Para especificar un usuario diferente, haga clic en el botón para examinar.  
  
### <a name="create-search-property-list-options"></a>Opciones de creación de listas de propiedades de búsqueda  
 Haga clic en una de las opciones siguientes:  
  
 **Crear una lista de propiedades de búsqueda vacía**  
 Crea una lista de propiedades de búsqueda sin ninguna propiedad.  
  
 **Crear a partir de una lista de propiedades de búsqueda existente**  
 Copia las propiedades de una lista de propiedades de búsqueda existente en otra lista nueva. Las listas de propiedades de búsqueda son objetos de base de datos, por lo que debe especificar la base de datos que contiene la lista de propiedades que desea copiar.  
  
 **Base de datos de origen**  
 Especifique el nombre de la base de datos a la que pertenece la lista de palabras de búsqueda existente. De manera predeterminada, se selecciona la base de datos actual. Si lo desea, puede usar el cuadro de lista para seleccionar otra base de datos, siempre y cuando la conexión actual esté asociada con un identificador de usuario de esa base de datos.  
  
 **Lista de propiedades de búsqueda de origen**  
 Seleccione el nombre de una de las listas de propiedades de búsqueda existentes que pertenecen a la base de datos seleccionada.  
  
## <a name="permissions"></a>Permisos  
 Vea [Create Search Property LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql).  
  
## <a name="to-use-sql-server-management-studio-to-manage-search-property-lists"></a>Para usar SQL Server Management Studio con el fin de administrar listas de propiedades de búsqueda  
 Para obtener información sobre cómo crear, ver, cambiar o eliminar una lista de propiedades de búsqueda, y sobre cómo configurar un índice de texto completo para la búsqueda de propiedades, vea [Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
## <a name="see-also"></a>Consulte también  
 [CREAR lista de propiedades de búsqueda &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql)   
 [Buscar propiedades de documento con listas de propiedades de búsqueda](../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [sys.registered_search_property_lists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql)  
  
  
