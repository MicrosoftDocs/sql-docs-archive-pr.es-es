---
title: Tablas | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- tables [SQL Server]
- table components [SQL Server]
ms.assetid: 82d7819c-b801-4309-a849-baa63083e83f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 22e417a535454f88d6475a97d2d17ad794404175
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87670910"
---
# <a name="tables"></a>Tablas
  Las tablas son objetos de base de datos que contienen todos sus datos. En las tablas, los datos se organizan con arreglo a un formato de filas y columnas, similar al de una hoja de cálculo. Cada fila representa un registro único y cada columna un campo dentro del registro. Por ejemplo, en una tabla que contiene los datos de los empleados de una compañía puede haber una fila para cada empleado y distintas columnas en las que figuren detalles de los mismos, como el número de empleado, el nombre, la dirección, el puesto que ocupa y su número de teléfono particular.  
  
-   El número de tablas de una base de datos se limita solo por el número de objetos admitidos en una base (2.147.483.647). Una tabla definida por el usuario estándar puede tener hasta 1.024 columnas. El número de filas de la tabla solo está limitado por la capacidad de almacenamiento del servidor.  
  
-   Puede asignar propiedades a la tabla y a cada columna de la tabla para controlar los datos admitidos y otras propiedades. Por ejemplo, puede crear restricciones en una columna para no permitir valores nulos o para proporcionar un valor predeterminado si no se especifica un valor, o puede asignar una restricción de clave en la tabla que exige la unicidad o definir una relación entre las tablas.  
  
-   Los datos de la tabla se pueden comprimir por filas o por página. La compresión de datos puede permitir que se almacenen más filas en una página. Para obtener más información, consulte [Data Compression](../../relational-databases/data-compression/data-compression.md).  
  
## <a name="types-of-tables"></a>Tipos de tablas  
 Además del rol estándar de las tablas básicas definidas por el usuario, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proporciona los siguientes tipos de tabla que permiten llevar a cabo objetivos especiales en una base de datos:  
  
 Tablas con particiones  
 Las tablas con particiones son tablas cuyos datos se han dividido horizontalmente entre unidades que pueden repartirse por más de un grupo de archivos de una base de datos. Las particiones facilitan la administración de índices y tablas grandes al permitir el acceso y la administración de subconjuntos de datos rápidamente y con eficacia, mientras se mantiene la integridad de la colección global. De forma predeterminada, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] admite hasta 15.000 particiones. Para obtener más información, vea [Partitioned Tables and Indexes](../../relational-databases/partitions/partitioned-tables-and-indexes.md).  
  
 Tablas temporales  
 Las tablas temporales se almacenan en `tempdb` . Hay dos tipos de tablas temporales: locales y globales. Se diferencian entre sí por los nombres, la visibilidad y la disponibilidad. Las tablas temporales locales tienen como primer carácter de sus nombres un solo signo de número (#); solo son visibles para el usuario de la conexión actual y se eliminan cuando el usuario se desconecta de la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Las tablas temporales globales presentan dos signos de número (##) antes del nombre; son visibles para cualquier usuario después de su creación y se eliminan cuando todos los usuarios que hacen referencia a la tabla se desconectan de la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Tablas del sistema  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] almacena los datos que definen la configuración del servidor y de todas sus tablas en un conjunto de tablas especial, conocido como tablas del sistema. Los usuarios no pueden consultar o actualizar directamente las tablas del sistema. La información de las tablas del sistema está disponible a través de las vistas del sistema. Para obtener más información, vea [Vistas del sistema &#40;Transact-SQL&#41;](/sql/t-sql/language-reference).  
  
 Tablas anchas  
 Las tablas anchas usan las [columnas dispersas](use-sparse-columns.md) para aumentar hasta 30 000 el número total de columnas permitidas. Las columnas dispersas son columnas normales que disponen de un almacenamiento optimizado para los valores NULL. Este tipo de columnas reducen los requisitos de espacio de los valores NULL a costa de una mayor sobrecarga a la hora de recuperar valores no NULL. Una tabla ancha ha definido un [conjunto de columnas](use-column-sets.md), que es una representación XML sin tipo que combina todas las columnas dispersas de una tabla en una salida estructurada. El número de índices y estadísticas también se aumenta hasta 1.000 y 30.000, respectivamente. El tamaño máximo de una fila de una tabla ancha es de 8.019 bytes. Por consiguiente, la mayoría de los datos de cualquier fila deben ser NULL. El número máximo de columnas no dispersas más las columnas calculadas de una tabla ancha sigue siendo 1.024.  
  
 Las tablas anchas tienen las siguientes implicaciones de rendimiento.  
  
-   Las tablas anchas pueden aumentar el costo de mantenimiento de los índices de la tabla. Se recomienda que el número de índices de una tabla ancha se limite a los índices necesarios para la lógica de negocios. Si el número de índices aumenta, también lo harán el tiempo de compilación de DML y los requisitos de memoria. Los índices no clúster deben ser índices filtrados que se aplican a subconjuntos de datos. Para obtener más información, consulte [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md).  
  
-   Las aplicaciones pueden agregar y quitar columnas de las tablas anchas de forma dinámica. Cuando se agregan o se quitan columnas, también se invalidan los planes de consulta compilados. Se recomienda diseñar una aplicación que se corresponda con la carga de trabajo prevista para minimizar los cambios de esquema.  
  
-   Cuando se agregan y se quitan datos de una tabla ancha, el rendimiento puede verse afectado. El diseño de las aplicaciones debe corresponderse con la carga de trabajo prevista para minimizar los cambios llevados a cabo en los datos de la tabla.  
  
-   Limite la ejecución de instrucciones DML en una tabla ancha destinadas a actualizar varias filas de una clave de agrupación en clústeres. La compilación y la ejecución de estas instrucciones pueden requerir recursos de memoria considerables.  
  
-   Las operaciones de cambio de partición en las tablas anchas pueden resultar lentas, y su procesamiento podría requerir grandes cantidades de memoria. Los requisitos de rendimiento y de memoria son proporcionales al número total de columnas existentes en las particiones de origen y de destino.  
  
-   Los cursores de actualización que actualizan columnas concretas de una tabla ancha deben enumerar las columnas de manera explícita en la cláusula FOR UPDATE. Esto ayudará a optimizar el rendimiento mientras se usan cursores.  
  
## <a name="common-table-tasks"></a>Tareas de tabla comunes  
 En la tabla siguiente se proporcionan vínculos a las tareas comunes asociadas con la creación o modificación de una tabla.  
  
|Tareas de tabla|Tema|  
|-----------------|-----------|  
|Describe cómo crear una tabla.|[Crear tablas &#40;motor de base de datos&#41;](create-tables-database-engine.md)|  
|Describe cómo eliminar una tabla.|[Eliminar tablas &#40;motor de base de datos&#41;](delete-tables-database-engine.md)|  
|Describe cómo crear una nueva tabla que contenga algunas o todas las columnas de una tabla existente.|[Duplicar tablas](duplicate-tables.md)|  
|Describe cómo cambiar el nombre de una tabla.|[Cambiar el nombre a las tablas &#40;motor de base de datos&#41;](rename-tables-database-engine.md)|  
|Describe cómo ver las propiedades de la tabla.|[Ver la definición de tabla](view-the-table-definition.md)|  
|Describe cómo determinar si otros objetos como una vista o un procedimiento almacenado dependen de una tabla.|[Ver las dependencias de una tabla](view-the-dependencies-of-a-table.md)|  
  
 En la tabla siguiente se proporcionan vínculos a las tareas comunes asociadas con la creación o modificación de columnas en una tabla.  
  
|Tareas de columna|Tema|  
|------------------|-----------|  
|Describe cómo agregar columnas a una tabla existente.|[Agregar columnas a una tabla &#40;motor de base de datos&#41;](add-columns-to-a-table-database-engine.md)|  
|Describe cómo eliminar columnas de una tabla.|[Eliminar columnas de una tabla](delete-columns-from-a-table.md)|  
|Describe cómo cambiar el nombre de una columna.|[Cambiar el nombre a las columnas &#40;motor de base de datos&#41;](rename-columns-database-engine.md)|  
|Describe cómo copiar columnas de una tabla a otra, copiar solo la definición de la columna o copiar la definición y los datos.|[Copiar columnas de una tabla a otra &#40;motor de base de datos&#41;](copy-columns-from-one-table-to-another-database-engine.md)|  
|Describe cómo modificar una definición de columna mediante el cambio del tipo de datos u otra propiedad.|[Modificar columnas &#40;motor de base de datos&#41;](modify-columns-database-engine.md)|  
|Describe cómo cambiar el orden en el que aparecen las columnas.|[Cambiar el orden de las columnas de una tabla](change-column-order-in-a-table.md)|  
|Describe cómo crear una columna calculada en una tabla.|[Especificar columnas calculadas en una tabla](specify-computed-columns-in-a-table.md)|  
|Describe cómo especificar un valor predeterminado de una columna. Este valor se usa si no se proporciona otro.|[Especificar valores predeterminados para las columnas](specify-default-values-for-columns.md)|  
  
## <a name="see-also"></a>Consulte también  
 [Restricciones de clave principal y externa](primary-and-foreign-key-constraints.md)   
 [Restricciones UNIQUE y restricciones CHECK](unique-constraints-and-check-constraints.md)  
  
  
