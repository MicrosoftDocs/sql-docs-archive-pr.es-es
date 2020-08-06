---
title: Índices en columnas calculadas | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- computed columns, index creation
- index creation [SQL Server], computed columns
- imprecise columns
- persisted computed columns
- precise [SQL Server]
ms.assetid: 8d17ac9c-f3af-4bbb-9cc1-5cf647e994c4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2ecbca9e7838c4c9395a8bcb6e11351c40f7037f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750958"
---
# <a name="indexes-on-computed-columns"></a>Índices en columnas calculadas
  Los índices se pueden definir en columnas calculadas si se cumplen estos requisitos:  
  
-   Requisitos de propiedad  
  
-   Requisitos de determinismo  
  
-   Requisitos de precisión  
  
-   Requisitos de tipo de datos  
  
-   Requisitos de la opción SET  
  
 **Ownership Requirements**  
  
 Todas las referencias a funciones de la columna calculada deben tener el mismo propietario que la tabla.  
  
 **Determinism Requirements**  
  
> [!IMPORTANT]  
>  Las expresiones son deterministas si siempre devuelven el mismo resultado para un conjunto de entradas específico. La propiedad **IsDeterministic** de la función [COLUMNPROPERTY](/sql/t-sql/functions/columnproperty-transact-sql) informa de si una expresión *computed_column_expression* es determinista.  
  
 La expresión *computed_column_expression* debe ser determinista. Una expresión *computed_column_expression* es determinista si se cumplen una o varias de las condiciones siguientes:  
  
-   Todas las funciones a las que hace referencia la expresión son deterministas y precisas. Esto incluye las funciones definidas por el usuario y las funciones integradas. Para obtener más información, consulte [Deterministic and Nondeterministic Functions](../user-defined-functions/deterministic-and-nondeterministic-functions.md). Puede que las funciones sean imprecisas si el valor de la columna calculada es PERSISTED. Para obtener más información, vea [Crear índices en columnas calculadas persistentes](#BKMK_persisted) más adelante en este tema.  
  
-   Todas las columnas a las que hace referencia la expresión pertenecen a la tabla que contiene la columna calculada.  
  
-   Ninguna referencia a las columnas extrae datos de varias filas. Por ejemplo, las funciones de agregado como SUM o AVG dependen de datos de varias filas y convertirán a *computed_column_expression* en una expresión no determinista.  
  
-   La expresión *computed_column_expression* no tiene acceso a los datos del sistema o de usuario.  
  
 Cualquier columna calculada que contenga una expresión CLR (Common Language Runtime) debe ser determinista y se debe marcar como PERSISTED para poder indizarla. Las expresiones con el tipo definido por el usuario CLR se pueden utilizar en las definiciones de columnas calculadas. Las columnas calculadas con el tipo definido por el usuario CLR se podrán indizar siempre que el tipo sea comparable. Para obtener más información, vea [Tipos definidos por el usuario de CLR](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).  
  
> [!NOTE]  
>  Cuando haga referencia a los literales de cadena del tipo de datos de fecha en las columnas calculadas indizadas de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], se recomienda convertir explícitamente el literal al tipo de datos deseado mediante un estilo de formato de fecha determinista. Para obtener una lista de los estilos de formato de fecha deterministas, vea [CAST y CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql). Las expresiones que impliquen la conversión implícita de cadenas de caracteres en tipos de datos de fecha se consideran no deterministas, a menos que el nivel de compatibilidad de la base de datos se establezca en 80 o menos. Esto es así porque los resultados dependen de la configuración de [LANGUAGE](/sql/t-sql/statements/set-language-transact-sql) y [DATEFORMAT](/sql/t-sql/statements/set-dateformat-transact-sql) de la sesión del servidor. Por ejemplo, los resultados de la expresión `CONVERT (datetime, '30 listopad 1996', 113)` dependen del valor de LANGUAGE porque la cadena '`30 listopad 1996`' significa distintos meses en distintos idiomas. De forma similar, en la expresión `DATEADD(mm,3,'2000-12-01')`, el [!INCLUDE[ssDE](../../../includes/ssde-md.md)] interpretará la cadena `'2000-12-01'` en función del valor de DATEFORMAT.  
>   
>  La conversión implícita de datos de caracteres no Unicode entre intercalaciones también se considera no determinista, a menos que el nivel de compatibilidad se establezca en 80 o menos.  
>   
>  Cuando el valor del nivel de compatibilidad de la base de datos es 90, no se pueden crear índices en columnas calculadas que incluyan estas expresiones. Sin embargo, se pueden mantener las columnas calculadas existentes que contengan estas expresiones procedentes de una base de datos actualizada. Si utiliza columnas calculadas indizadas que contienen conversiones implícitas de cadena a fecha, para evitar posibles daños en las vistas indizadas, asegúrese de que las opciones LANGUAGE y DATEFORMAT son coherentes en las bases de datos y las aplicaciones.  
  
 **Precision Requirements**  
  
 La expresión *computed_column_expression* debe ser precisa. Una expresión *computed_column_expression* es precisa si se cumplen una o varias de las condiciones siguientes:  
  
-   No es una expresión del tipo de datos `float` o `real`.  
  
-   No utiliza en su definición un tipo de datos `float` o `real`. Por ejemplo, en la instrucción siguiente, la columna `y` es `int` y determinista, pero no precisa.  
  
    ```  
    CREATE TABLE t2 (a int, b int, c int, x float,   
       y AS CASE x   
             WHEN 0 THEN a   
             WHEN 1 THEN b   
             ELSE c   
          END);  
    ```  
  
> [!NOTE]  
>  Las expresiones `float` o `real` se consideran imprecisas y no pueden ser la clave de un índice; una expresión `float` o `real` puede utilizarse en una vista indizada, pero no como clave. Esto también se aplica a las columnas calculadas. Las funciones, expresiones o funciones definidas por el usuario se considerarán imprecisas si incluyen expresiones `float` o `real`. Esto incluye a las lógicas (comparaciones).  
  
 La propiedad **IsPrecise** de la función COLUMNPROPERTY informa de si una expresión *computed_column_expression* es precisa.  
  
 **Data Type Requirements**  
  
-   Los *computed_column_expression* definidos para la columna calculada no se pueden evaluar `text` como `ntext` tipos de `image` datos, o.  
  
-   Las columnas calculadas derivadas de los tipos de datos `image`, `ntext`, `text`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)` y `xml` se pueden indizar, siempre que el tipo de datos esté disponible como una columna de clave de índice.  
  
-   Las columnas calculadas derivadas de los tipos de datos `image`, `ntext` y `text` pueden ser columnas sin clave (incluidas) en un índice no clúster, siempre que el tipo de datos esté disponible como una columna de índice sin clave.  
  
 **Requisitos de la opción SET**  
  
-   La opción de nivel de conexión ANSI_NULLS debe estar establecida en ON si se ejecuta la instrucción CREATE TABLE o ALTER TABLE que define la columna calculada. La función [OBJECTPROPERTY](/sql/t-sql/functions/objectpropertyex-transact-sql) informa de si la opción está activada a través de la propiedad **IsAnsiNullsOn** .  
  
-   La conexión en la que se crea el índice y todos los intentos de conexión de las instrucciones INSERT, UPDATE o DELETE que cambiarán los valores del índice deben tener seis opciones SET con el valor ON y una con el valor OFF. El optimizador omitirá un índice de una columna calculada para cualquier instrucción SELECT que se ejecute mediante una conexión que no tenga la misma configuración de las opciones.  
  
    -   El valor de la opción NUMERIC_ROUNDABORT debe ser OFF y el de las opciones siguientes debe ser ON:  
  
    -   ANSI_NULLS  
  
    -   ANSI_PADDING  
  
    -   ANSI_WARNINGS  
  
    -   ARITHABORT  
  
    -   CONCAT_NULL_YIELDS_NULL  
  
    -   QUOTED_IDENTIFIER  
  
     Al establecer ANSI_WARNINGS en ON, ARITHABORT se establece de forma implícita en ON cuando el nivel de compatibilidad de base de datos está establecido en 90 o un valor superior.  
  
##  <a name="creating-indexes-on-persisted-computed-columns"></a><a name="BKMK_persisted"></a> Crear índices en columnas calculadas persistentes  
 Puede crear un índice en una columna calculada definida con una expresión determinista pero imprecisa si se marca la columna como PERSISTED en la instrucción CREATE TABLE o ALTER TABLE. Esto significa que [!INCLUDE[ssDE](../../../includes/ssde-md.md)] utiliza estos valores persistentes cuando crea un índice en la columna y cuando se hace referencia al índice en una consulta. Esta opción permite crear un índice en una columna calculada cuando [!INCLUDE[ssDE](../../../includes/dnprdnshort-md.md)] es determinista y precisa.  
  
## <a name="related-content"></a>Contenido relacionado  
 [COLUMNPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/columnproperty-transact-sql)  
  
  
