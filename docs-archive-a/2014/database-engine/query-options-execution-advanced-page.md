---
title: Ejecución de opciones de consulta (página avanzadas) | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.advanced.f1
ms.assetid: 661595ce-99b9-4316-ad80-ed04002d04d5
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: ''
ms.date: 09/03/2019
ms.openlocfilehash: 5b6ab8cc3c788e27946ddb68a3c926e8f926ebd7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748243"
---
# <a name="query-options-execution-advanced-page"></a>Opciones de ejecución de consulta (página Avanzadas)

  Al utilizar la instrucción **SET** están disponibles una variedad de opciones. Utilice esta página para especificar una opción **set** para ejecutar consultas de Microsoft SQL Server. Para obtener información detallada de cada una de estas opciones, vea los Libros en pantalla de SQL Server.
  
**establecer NOcount** No devuelve el recuento del número de filas, como un mensaje con el conjunto de resultados. Esta opción está desactivada de forma predeterminada.

**establecer NOexec** No ejecuta la consulta. Esta opción está desactivada de forma predeterminada.

**establecer PARSEONLY** Comprueba la sintaxis de cada consulta, pero no ejecuta las consultas. Esta opción está desactivada de forma predeterminada.  

**establecer CONCAT_NULL_YIELDS_NULL** Cuando se activa esta casilla, las consultas que concatenan un valor existente con un `NULL` , siempre devuelven `NULL` como resultado. Cuando se desactiva esta casilla, un valor existente concatenado con un valor `NULL`, devuelve el valor existente. Esta opción está activada de forma predeterminada.

**establecer ARITHABORT** Cuando se activa esta casilla, cuando una `INSERT` instrucción, `DELETE` o encuentra `UPDATE` un error aritmético (desbordamiento, división por cero o error de dominio) durante la evaluación de la expresión, se finaliza la consulta o el lote. Cuando se desactiva esta casilla, se proporciona un valor `NULL` para ese valor si es posible, la consulta continúa y se incluye un mensaje con el resultado. Vea los Libros en pantalla para una descripción más detallada de este comportamiento. Esta opción está activada de forma predeterminada.
  
**establecer SHOWPLAN_TEXT** Cuando se activa esta casilla, el plan de consulta se devuelve en formato de texto con cada consulta. Esta opción está desactivada de forma predeterminada.
  
**SET STATISTICS TIME** Cuando se activa esta casilla, las estadísticas de tiempo se devuelven con cada consulta. Esta opción está desactivada de forma predeterminada.
  
**establecer e/s de estadísticas** Cuando se activa esta casilla, las estadísticas relacionadas con la entrada/salida (e/s) se devuelven con cada consulta. Esta opción está desactivada de forma predeterminada.
  
**SET TRANSACTION ISOLATION LEVEL** Se ha establecido de forma predeterminada el nivel de aislamiento de transacción READ COMMITTED. Para obtener más información, vea [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql). El nivel de aislamiento de transacción de instantánea no está disponible. Para utilizar el aislamiento SNAPSHOT, agregue la instrucción [!INCLUDE[tsql](../includes/tsql-md.md)] siguiente:
  
  ```sql
  SET TRANSACTION ISOLATION LEVEL SNAPSHOT;
  GO
  ```

**SET DEADLOCK PRIORITY** El valor predeterminado de **Normal** permite que cada consulta tenga la misma prioridad cuando tiene lugar un interbloqueo. Seleccione la prioridad Baja en la lista desplegable si desea que esta consulta pierda los conflictos de interbloqueo y se seleccione cuando la consulta haya finalizado.

**establecer tiempo de espera de bloqueo** El valor predeterminado-1 indica que los bloqueos se mantienen hasta que se completen las transacciones. El valor de 0 significa no esperar en absoluto y devolver un mensaje en cuanto se encuentre un bloqueo. Proporcione un valor mayor que 0 milisegundos para finalizar una transacción si los bloqueos para transacción deben mantenerse durante un intervalo mayor.

**establecer QUERY_GOVERNOR_COST_LIMIT** Use la opción **query Governor cost Limit** para especificar un límite superior en el período de tiempo en el que se puede ejecutar una consulta. El costo de la consulta se refiere al tiempo transcurrido estimado, en segundos, necesario para finalizar una consulta en una configuración específica de hardware. La configuración predeterminada de 0 indica que no hay límite para el periodo de tiempo en que se ejecutará una consulta.

**Suprimir encabezados de mensaje de proveedor** Cuando se activa esta casilla, no se muestran los mensajes de estado del proveedor (como el proveedor de OLE DB). Esta casilla está activada de forma predeterminada. Desactive esta casilla para ver los mensajes del proveedor cuando la solución de las consultas presente errores en el nivel del proveedor.

**Desconectar tras la ejecución de la consulta** Cuando se activa esta casilla, la conexión a SQL Server finaliza una vez que termina la consulta. Esta opción está desactivada de forma predeterminada.

**Mostrar la hora de finalización** Permite imprimir la hora en que se completó la ejecución de la consulta después de los resultados de la consulta o en la pestaña mensajes.

**Protocolo de atestación de VBS enclaves para Always Encrypted** Permite establecer un protocolo de atestación para la seguridad basada en la virtualización (VBS) enclaves que usa Always Encrypted con enclaves seguro.

Los protocolos de atestación admitidos actualmente son:

* Servicio de protección de host: un protocolo de atestación que usa el servicio de protección de host de Windows (HGS).

Para obtener más información, consulte [Always Encrypted con seguridad enclaves](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-enclaves?view=sqlallproducts-allversions) y la [atestación de enclave segura](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-enclaves?view=sqlallproducts-allversions#secure-enclave-attestation).

**Valores predeterminados** Restablece todos los valores de esta página a los valores predeterminados originales.
