---
title: Destino de búfer en anillo | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- targets [SQL Server extended events], ring buffer target
- ring buffer target [SQL Server extended events]
ms.assetid: 54494e11-b56b-43b7-aa5e-c8724e56b251
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 186e847bb9f9b621543119c25510dc5d6107e274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676150"
---
# <a name="ring-buffer-target"></a>Destino de búfer de anillo
  El destino de búfer de anillo guarda datos de eventos en la memoria durante un corto espacio de tiempo. Este destino puede administrar los eventos de uno de los dos modos siguientes.  
  
-   El primer modo es un orden FIFO (First In, First Out; primero en entrar, primero en salir) estricto, en el que el evento más antiguo se descarta cuando se usa toda la memoria asignada al destino. En este modo (valor predeterminado), la opción occurrence_number se establece en 0.  
  
-   El segundo modo es un orden FIFO por evento, en el que se conserva un número determinado de eventos de cada tipo. En este modo, los eventos más antiguos de cada tipo se descartan cuando se usa toda la memoria asignada al destino. Puede configurar la opción occurrence_number para especificar el número de eventos de cada tipo que se desea conservar.  
  
 En la tabla siguiente se describen las opciones disponibles para configurar el destino de búfer de anillo.  
  
|Opción|Valores permitidos|Descripción|  
|------------|--------------------|-----------------|  
|max_memory|Cualquier entero de 32 bits. Este valor es opcional.|La cantidad de memoria máxima en kilobytes (kB) que se va a usar. Los eventos existentes se quitan en función del límite que se alcance primero: max_event_limit o max_memory. El valor máximo es 4194303 KB. Antes de establecer el tamaño del búfer de anillo en límites en el intervalo de GB, se debe tener en cuenta una consideración cuidadosa, ya que puede afectar a otros consumidores de memoria en SQL Server|  
|max_event_limit|Cualquier entero de 32 bits. Este valor es opcional.|El número máximo de eventos que se mantiene en el búfer en anillo. Los eventos existentes se quitan en función del límite que se alcance primero: max_event_limit o max_memory. Valor predeterminado = 1000.|  
|occurrence_number|Uno de los siguientes valores:<br /><br /> 0 (valor predeterminado) = El evento más antiguo se descarta cuando se usa toda la memoria asignada al destino.<br /><br /> Cualquier entero de 32 bits = el número de eventos de cada tipo que se conservarán antes de que se descarten por cada FIFO.<br /><br /> <br /><br /> Este valor es opcional.|Modo FIFO que se va a usar y, si se establece en un valor mayor que 0, el número preferido de eventos de cada tipo que se desea conservar en el búfer.|
| &nbsp; | &nbsp; | &nbsp; |
  
## <a name="adding-the-target-to-a-session"></a>Agregar el destino a una sesión  
 Para agregar el destino del búfer de anillo a una sesión de eventos extendidos, debe incluir la siguiente instrucción al crear o modificar una sesión de eventos:  
  
```sql
ADD TARGET package0.ring_buffer  
```  
  
## <a name="reviewing-the-target-output"></a>Revisar la salida del destino  
 Para revisar la salida del destino de búfer de anillo, puede usar la siguiente consulta, reemplazando *session_name* por el nombre de la sesión de eventos.  
  
```sql
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 En el siguiente ejemplo se muestra el formato de salida del destino de búfer de anillo.  
  
```  
<RingBufferTarget eventsPerSec="" processingTime="" totalEventsProcessed="" eventCount="" droppedCount="" memoryUsed="">  
 <event name="" package="" id="" version="" timestamp="">  
    <data name="">  
      <type name="" package="" />  
      <value></value>  
      <text></text>  
    </data>  
    <action name="" package="">  
      <type name="" package="" />  
      <value></value>  
      <text></text>  
    </action>  
  </event>  
</RingBufferTarget>  
```


## <a name="see-also"></a>Consulte también

- [Destinos de SQL Server Extended Events](../../2014/database-engine/sql-server-extended-events-targets.md)
- [sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql?view=sql-server-2016)
- [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql?view=sql-server-2016)
- [ALTER EVENT SESSION &#40;Transact-SQL&#41;](https://docs.microsoft.com/sql/t-sql/statements/alter-event-session-transact-sql?view=sql-server-2016)

