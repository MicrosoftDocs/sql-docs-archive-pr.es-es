---
title: Clase de eventos Broker:Connection | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Broker:Connection event class
ms.assetid: d3e505f2-0a43-486f-aa92-9c8e49b2dfea
author: stevestein
ms.author: sstein
ms.openlocfilehash: 52c0755d7547d85cfa041080518429d20165f251
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672009"
---
# <a name="brokerconnection-event-class"></a>Broker:Connection, clase de eventos
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] genera un evento **Broker:Connection** para informar del estado de una conexión de transporte administrada por Service Broker.  
  
## <a name="brokerconnection-event-class-data-columns"></a>Columnas de datos de la clase de evento Broker:Connection  
  
|Columna de datos|Tipo|Descripción|Número de columna|Filtrable|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ApplicationName**|`nvarchar`|Nombre de la aplicación cliente que ha creado la conexión a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Esta columna se rellena con los valores que pasa la aplicación, en lugar de con el nombre que se muestra para el programa.|10|Sí|  
|**ClientProcessID**|`int`|Id. que el equipo host asigna al proceso en el que se ejecuta la aplicación cliente. Esta columna de datos se rellena si el cliente proporciona su identificador de proceso.|9|Sí|  
|**DatabaseID**|`int`|Identificador de la base de datos especificada mediante la instrucción USE *database* o identificador de la base de datos predeterminada si no se ha emitido la instrucción USE *database*para una instancia determinada. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] muestra el nombre de la base de datos si se captura la columna de datos **ServerName** en el seguimiento y el servidor está disponible. Determine el valor de una base de datos mediante la función **DB_ID** .|3|Sí|  
|**Error**|`int`|El número de identificación del mensaje en **Sys.** messages para el texto del evento. Si este evento informa de un error, éste es el número de error de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|31|No|  
|**EventClass**|`int`|Tipo de clase de eventos capturado. Siempre **138** para **Broker:Connection**.|27|No|  
|**EventSequence**|`int`|Número de secuencia de este evento.|51|No|  
|**EventSubClass**|`nvarchar`|Estado de esta conexión. En el caso de este evento, la subclase es uno de los valores siguientes:<br /><br /> **Conectando**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] está iniciando una conexión de transporte.<br /><br /> **Conectado**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha establecido una conexión de transporte.<br /><br /> **Connect Failed**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no ha podido establecer una conexión de transporte.<br /><br /> **Cierre**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] está cerrando la conexión de transporte.<br /><br /> **Cerrada**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha cerrado la conexión de transporte.<br /><br /> **Acepte**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha aceptado una conexión de transporte de otra instancia.<br /><br /> **Send IO Error**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] detectó un error de transporte al enviar un mensaje.<br /><br /> **Receive IO Error**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] detectó un error de transporte al recibir un mensaje.|21|Sí|  
|**GUID**|`uniqueidentifier`|Id. de extremo de esta conexión.|54|No|  
|**HostName**|`nvarchar`|Nombre del equipo en el que se está ejecutando el cliente. Esta columna de datos se rellena si el cliente proporciona el nombre del host. Para determinar el nombre de host, utilice la función **host_name** .|8|Sí|  
|**IntegerData**|`int`|Número de veces que se ha cerrado esta conexión.|25|Sí|  
|**IsSystem**|`int`|Indica si el evento ha ocurrido en un proceso del sistema o en un proceso de usuario.<br /><br /> 0 = usuario<br /><br /> 1 = sistema|60|No|  
|**LoginSid**|`image`|SID (número de identificación de seguridad) del usuario que ha iniciado la sesión. Cada SID es único para cada inicio de sesión en el servidor.|41|Sí|  
|**NTDomainName**|`nvarchar`|Dominio de Windows al que pertenece el usuario.|7|Sí|  
|**NTUserName**|`nvarchar`|Nombre del usuario al que pertenece la conexión que generó este evento.|6|Sí|  
|**ObjectName**|`nvarchar`|Identificador de conversación del diálogo.|34|No|  
|**ServerName**|`nvarchar`|Nombre de la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de la que se realiza un seguimiento.|26|No|  
|**SPID**|`int`|Identificador de proceso del servidor que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] asigna al proceso asociado al cliente.|12|Sí|  
|**StartTime**|`datetime`|Hora a la que se inició el evento, si está disponible.|14|Sí|  
|**TextData**|`ntext`|Texto del mensaje de error relacionado con el evento. En el caso de los eventos que no informan de un error, este campo está vacío. El mensaje de error puede ser de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o de Windows.|1|Sí|  
|**TransactionID**|`bigint`|Identificador de la transacción asignado por el sistema.|4|No|  
  
## <a name="see-also"></a>Consulte también  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
