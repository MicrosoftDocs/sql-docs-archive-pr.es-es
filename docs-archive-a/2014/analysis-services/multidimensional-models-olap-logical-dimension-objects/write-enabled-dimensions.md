---
title: Dimensiones habilitadas para escritura | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- write-enabled dimensions [Analysis Services]
- dimensions [Analysis Services], write-enabled
- dimension writeback [Analysis Services]
- write-enabled cubes [Analysis Services]
- writeback [Analysis Services], dimensions
ms.assetid: 0bac050d-cd3b-427b-884a-65a91be89500
author: minewiskan
ms.author: owend
ms.openlocfilehash: f8f0f1c959d44b4d3e133e5676e9aca9365a628d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673933"
---
# <a name="write-enabled-dimensions"></a>Dimensiones habilitadas para escritura
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
 Los datos de una dimensión son normalmente de solo lectura. Con todo, en ciertos casos, puede interesarle habilitar una dimensión para escritura. En [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , al habilitar una dimensión para escritura, los usuarios empresariales pueden modificar el contenido de la dimensión y ver el efecto inmediato de los cambios en las jerarquías de la dimensión. Es posible habilitar para escritura cualquier dimensión basada en una sola tabla. En una dimensión habilitada para escritura, los usuarios empresariales y los administradores pueden cambiar, mover, agregar y eliminar los miembros de atributo de la dimensión. Estas actualizaciones se denominan de forma colectiva *reescritura de dimensión*.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] admite la reescritura en la dimensión en todos los atributos de dimensión y, además, cualquier miembro de una dimensión puede modificarse. En un cubo o partición habilitados para escritura, las actualizaciones se almacenan en una tabla de reescritura separada de las tablas de origen del cubo. Sin embargo, para una dimensión habilitada para escritura, las actualizaciones se registran directamente en la tabla de la dimensión. Además, si la dimensión habilitada para escritura está incluida en un cubo con varias particiones en las que algunos o todos sus orígenes de datos tienen copias de la tabla de dimensión, solo se actualizará la tabla de dimensión original durante el proceso de reescritura.  
  
 Las dimensiones y cubos habilitados para escritura tienen características distintas pero complementarias. Una dimensión habilitada para escritura permite a los usuarios empresariales actualizar miembros, mientras que un cubo habilitado para escritura les permite actualizar los valores de las celdas. Aunque son complementarias, no es necesario que utilice estas dos características conjuntamente. Para que la reescritura en la dimensión tenga lugar, no es necesario que una dimensión esté incluida en un cubo. Una dimensión habilitada para escritura también puede estar incluida en un cubo que no esté habilitado para escritura. Para habilitar las dimensiones y los cubos para escritura y para mantener su seguridad se utilizan procedimientos distintos.  
  
 La reescritura en la dimensión está sujeta a las siguientes restricciones:  
  
-   Al crear un nuevo miembro, debe incluir todos los atributos en una dimensión. No puede insertar un miembro sin especificar un valor para el atributo clave de la dimensión. Por lo tanto, la creación de miembros está sujeta a las restricciones (como los valores de clave no nulos) definidas en la tabla de la dimensión.  
  
-   La reescritura en la dimensión solo se admite para los esquemas en estrella. En otras palabras, una dimensión debe estar basada en una sola tabla de dimensión directamente relacionada con una tabla de hechos. Tras habilitar una dimensión para la escritura, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] valida este equipo cuando se implementa en una base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] existente o cuando genera un proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Todos los miembros existentes de una reescritura en la dimensión pueden modificarse o eliminarse. Cuando se elimina un miembro, la eliminación actúa en cascada en todos los miembros secundarios. Por ejemplo, en una dimensión de cliente que contiene los atributos CountryRegion, Province, City y Customer, la eliminación de un país o región eliminaría todas las provincias, ciudades y clientes que pertenecen al país o región eliminado. Si un país o región solamente tiene una provincia, la eliminación de dicha provincia también eliminaría el país o región.  
  
 Los miembros de una reescritura en la dimensión solo se pueden mover dentro del mismo nivel. Por ejemplo, una ciudad puede moverse al nivel City de un país, región o provincia diferentes, pero no al nivel Province o CountryRegion. En una jerarquía de elementos primarios y secundarios, todos los miembros son miembros hoja y, por lo tanto, un miembro puede moverse a cualquier otro nivel que no sea el nivel `(All)`.  
  
 Si se elimina un miembro de una jerarquía de elementos primarios y secundarios, los elementos secundarios del miembro se mueven al elemento primario. Se necesitan permisos de actualización para la tabla relacional en el miembro eliminado, pero no en los miembros que se han movido. Cuando una aplicación mueve un miembro en una jerarquía de elementos primarios y secundarios, la aplicación puede especificar en la operación UPDATE si los descendientes del miembro se mueven con el miembro o se mueven hacia los elementos primarios del miembro. Para eliminar recursivamente un miembro de una jerarquía de elementos primarios y secundarios, el usuario debe disponer de permisos de actualización en la tabla relacional para el miembro y todos los descendientes del mismo.  
  
> [!NOTE]  
>  Las actualizaciones en un atributo primario en una jerarquía de elementos primarios y secundarios no deben incluir las actualizaciones de cualquier otra propiedad o atributo.  
  
 Todos los cambios realizados en una dimensión provocan la modificación de la estructura de la dimensión. Cada cambio en una dimensión se considera una sola transacción que requiere un procesamiento incremental para actualizar la estructura de la dimensión. Las dimensiones habilitadas para escritura tienen los mismos requisitos de procesamiento que cualquier otra dimensión.  
  
> [!NOTE]  
>  Las dimensiones vinculadas no admiten la reescritura en la dimensión.  
  
## <a name="security"></a>Seguridad  
 Los únicos usuarios empresariales que pueden actualizar una dimensión habilitada para escritura son los usuarios de los roles de base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] a los que se les ha otorgado permiso de lectura/escritura para la dimensión. En cada rol, puede controlar los miembros que pueden o no actualizarse. Para que los usuarios empresariales puedan actualizar las dimensiones habilitadas para escritura, la aplicación cliente debe admitir esta capacidad. Para estos usuarios es preciso que la dimensión habilitada para escritura esté incluida en un cubo que se haya procesado desde la última vez que se cambió la dimensión. Para obtener más información, vea [Cómo autorizar el acceso a objetos y operaciones &#40;Analysis Services&#41;](../multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md).  
  
 Los usuarios y los grupos incluidos en el rol Administrador pueden actualizar los miembros de atributo de una dimensión habilitada para escritura aunque la dimensión no esté incluida en un cubo.  
  
## <a name="see-also"></a>Consulte también  
 [Propiedades de la dimensión de base de datos](database-dimension-properties.md)   
 [Particiones habilitadas para escritura](../multidimensional-models-olap-logical-cube-objects/partitions-write-enabled-partitions.md)   
 [Dimensiones &#40;Analysis Services - Datos multidimensionales&#41;](dimensions-analysis-services-multidimensional-data.md)  
  
  
