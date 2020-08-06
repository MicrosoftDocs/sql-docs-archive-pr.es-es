---
title: Creación de procedimientos almacenados compilados de forma nativa | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e6b34010-cf62-4f65-bbdf-117f291cde7b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3e8e8139427c7f2ad92eea856be8da542f65e344
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87670383"
---
# <a name="creating-natively-compiled-stored-procedures"></a>Crear procedimientos almacenados compilados de forma nativa
  Los procedimientos almacenados compilados de forma nativa no implementan el área expuesta completa de programación y consulta de [!INCLUDE[tsql](../../includes/tsql-md.md)] . Hay ciertas construcciones de [!INCLUDE[tsql](../../includes/tsql-md.md)] que no se pueden usar en los procedimientos almacenados compilados de forma nativa. Para obtener más información, vea [construcciones admitidas en procedimientos almacenados compilados de forma nativa](../in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md).  
  
 Sin embargo, hay varias características de [!INCLUDE[tsql](../../includes/tsql-md.md)] que se admiten solo para los procedimientos almacenados compilados de forma nativa:  
  
-   Bloques atomic. Para obtener más información, consulte [Atomic Blocks](atomic-blocks-in-native-procedures.md).  
  
-   Restricciones `NOT NULL` en los parámetros y variables de los procedimientos almacenados compilados de forma nativa. No se pueden asignar valores `NULL` a los parámetros o variables declarados como `NOT NULL`. Para obtener más información, vea [DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql).  
  
-   Enlace de esquema de los procedimientos almacenados compilados de forma nativa.  
  
 Los procedimientos almacenados compilados de forma nativa se crean por medio de [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql). En el ejemplo siguiente se muestra una tabla optimizada para memoria y un procedimiento almacenado compilado de nativa que se usa para insertar filas en la tabla.  
  
```sql  
create table dbo.Ord  
(OrdNo integer not null primary key nonclustered,   
 OrdDate datetime not null,   
 CustCode nvarchar(5) not null)   
 with (memory_optimized=on)  
go  
  
create procedure dbo.OrderInsert(@OrdNo integer, @CustCode nvarchar(5))  
with native_compilation, schemabinding, execute as owner  
as   
begin atomic with  
(transaction isolation level = snapshot,  
language = N'English')  
  
  declare @OrdDate datetime = getdate();  
  insert into dbo.Ord (OrdNo, CustCode, OrdDate) values (@OrdNo, @CustCode, @OrdDate);  
end  
go  
```  
  
 En el ejemplo de código, `NATIVE_COMPILATION` indica que este procedimiento almacenado de [!INCLUDE[tsql](../../includes/tsql-md.md)] es un procedimiento almacenado compilado de forma nativa. Se requieren las siguientes opciones:  
  
|Opción|Descripción|  
|------------|-----------------|  
|`SCHEMABINDING`|Los procedimientos almacenados compilados de forma nativa se debe enlazar al esquema de objetos al que hacen referencia. Esto significa que no se puede anular la tabla a la que hace referencia el procedimiento. Las tablas a las que se hace referencia en el procedimiento deben incluir el nombre de esquema y \* no se permiten caracteres comodín () en las consultas. `SCHEMABINDING` solo se admite para los procedimientos almacenados compilados de forma nativa en esta versión de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`EXECUTE AS`|Los procedimientos almacenados compilados de forma nativa no admiten `EXECUTE AS CALLER`, que es el contexto de ejecución predeterminado. Por tanto, se deberá especificar el contexto de ejecución. `EXECUTE AS OWNER`Se admiten las opciones, el `EXECUTE AS` *usuario*y `EXECUTE AS SELF` .|  
|`BEGIN ATOMIC`|El cuerpo de un procedimiento almacenado compilado de forma nativa debe constar exactamente de un solo bloque atomic. Los bloques atomic garantizan la ejecución atómica del procedimiento almacenado. Si se invoca el procedimiento fuera del contexto de una transacción activa, iniciará una nueva transacción, que se confirma al final del bloque atomic. Los bloques atomic de los procedimientos almacenados compilados de forma nativa tienen dos opciones obligatorias:<br /><br /> `TRANSACTION ISOLATION LEVEL`. Vea [niveles](../../database-engine/transaction-isolation-levels.md) de aislamiento de transacción para los niveles de aislamiento admitidos.<br /><br /> `LANGUAGE`. El lenguaje del procedimiento almacenado se debe establecer en uno de los lenguajes o de alias de lenguaje disponibles.|  
  
 En relación con `EXECUTE AS` y los inicios de sesión de Windows, puede aparecer un error debido a la suplantación realizada con `EXECUTE AS`. Si una cuenta de usuario usa la autenticación de Windows, debe haber plena confianza entre la cuenta de servicio utilizada para la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] y el dominio del inicio de sesión de Windows. Si no hay plena confianza, se devuelve el siguiente mensaje de error al crear un procedimiento almacenado compilado de forma nativa: mensaje 15404, no se pudo obtener información acerca del grupo o usuario de Windows NT ' nombredeusuario '; código de error 0X5.  
  
 Para resolver este error, utilice uno de los siguientes:  
  
-   Use una cuenta del mismo dominio que el usuario de Windows para el servicio de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Si [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utiliza una cuenta de equipo, como servicio de red o sistema local, el equipo debe ser de confianza para el dominio que contiene el usuario de Windows.  
  
-   Use la autenticación de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 También puede ver el error 15517 al crear un procedimiento almacenado compilado de forma nativa. Para obtener más información, vea [MSSQLSERVER_15517](../errors-events/mssqlserver-15517-database-engine-error.md).  
  
## <a name="updating-a-natively-compiled-stored-procedure"></a>Actualizar un procedimiento almacenado compilado de forma nativa  
 No se permite la realización de operaciones de modificación en procedimientos almacenados compilados de forma nativa. Una manera de modificar un procedimiento almacenado compilado de forma nativa es quitar y volver a crear el procedimiento almacenado:  
  
1.  Genere el script para los permisos en el procedimiento almacenado.  
  
2.  También puede generar el script para el procedimiento almacenado y guardarlo como copia de seguridad.  
  
3.  Quite el procedimiento almacenado.  
  
4.  Cree el procedimiento almacenado con las modificaciones.  
  
5.  Vuelva a aplicar los permisos del script al procedimiento almacenado.  
  
 El inconveniente de este procedimiento es que la aplicación estará sin conexión desde el inicio del paso 3 hasta la finalización del paso 5. Esto puede tardar unos segundos y es posible que el cliente que utiliza la aplicación vea mensajes de error.  
  
 Otra manera de modificar (eficazmente) un procedimiento almacenado compilado de forma nativa consiste en crear una nueva versión del procedimiento almacenado. Aquí, el procedimiento almacenado compilado de forma nativa tiene un número de versión asociado. Llamaremos a la versión anterior SP_Vold y a la nueva versión SP_Vnew.  
  
1.  Genere el script para los permisos en SP_Vold.  
  
2.  Cree SP_Vnew.  
  
3.  Aplique los permisos de SP_Vold a SP_Vnew.  
  
4.  Actualice las referencias a SP_Vold para que señalen a SP_Vnew. Esto puede llevarse a cabo de diferentes formas, por ejemplo:  
  
     Utilice un procedimiento almacenado de contenedor (basado en disco), y modifíquelo para que señale a SP_Vnew. El inconveniente de este método es el impacto sobre el rendimiento del direccionamiento indirecto.  
  
    ```sql  
    ALTER PROCEDURE dbo.SP p1,...,pn  
    AS  
      EXEC dbo.SP_Vnew p1,...,pn  
    GO  
    ```  
  
5.  Si lo desea, quite SP_Vold.  
  
 La ventaja de este método es que la aplicación no se queda sin conexión. Sin embargo, es necesario más trabajo para mantener las referencias y asegurarse de que siempre señalan a la última versión del procedimiento almacenado.  
  
## <a name="see-also"></a>Consulte también  
 [Procedimientos almacenados compilados de forma nativa](natively-compiled-stored-procedures.md)  
  
  
