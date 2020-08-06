---
title: Clase de eventos FT:Crawl Aborted | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Crawl Aborted event class
ms.assetid: eead8ea6-5051-4689-ab30-4dfbfda01fb9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 843e15f6f4cc0e683bb24a9a4709d66707111737
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748104"
---
# <a name="ftcrawl-aborted-event-class"></a>FT:Crawl Aborted (clase de eventos)
  La clase de eventos **FT:Crawl Aborted** indica que se ha encontrado una excepción durante un rastreo de texto completo. El error suele hacer que se detenga el rastreo de texto completo. Consulte el registro de eventos de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows o el registro de rastreo para obtener información detallada del error.  
  
## <a name="ftcrawl-aborted-event-class-data-columns"></a>Columnas de datos de la clase de eventos FT:Crawl Aborted  
  
|Nombre de columna de datos|Tipo de datos|Descripción|Identificador de columna|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|Id. de la base de datos en la que se ejecuta el rastreo de texto completo. Determina el valor de una base de datos mediante la función DB_ID.|3|Sí|  
|**Error**|**int**|Número de error de un evento dado. Con frecuencia, es el número de error almacenado en la tabla **sysmessages** .|31|Sí|  
|**EventClass**|**int**|Tipo de evento = 157.|27|No|  
|**EventSequence**|**int**|Secuencia de un evento determinado de la solicitud.|51|No|  
|**IsSystem**|**int**|Indica si el evento ha ocurrido en un proceso del sistema o en un proceso de usuario. 1 = sistema, 0 = usuario.|60|Sí|  
|**ObjectID**|**int**|Id. asignado por el sistema del objeto en el que se está ejecutando el rastreo de texto completo cuando se produce el error.|22|Sí|  
|**SessionLoginName**|**nvarchar**|Nombre de inicio de sesión del usuario que originó la sesión. Por ejemplo, si se conecta a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando inicioDeSesión1 y ejecuta una instrucción como inicioDeSesión2, **SessionLoginName** muestra inicioDeSesión1 y **LoginName** muestra inicioDeSesión2. En esta columna se muestran los inicios de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y de Windows.|64|Sí|  
|**SPID**|**int**|Identificador de la sesión en la que se produjo el evento.|12|Sí|  
|**StartTime**|**datetime**|Hora a la que se inició el evento, si está disponible.|14|Sí|  
|**State**|**int**|Equivalente a un código de estado de error.|30|Sí|  
|**TransactionID**|**bigint**|Id. de la transacción asignado por el sistema.|4|Sí|  
  
## <a name="see-also"></a>Consulte también  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
