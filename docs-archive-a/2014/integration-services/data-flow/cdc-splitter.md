---
title: Divisor CDC | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsplitter.f1
ms.assetid: 167bc5c6-fa36-439d-987c-b20acd1a77e2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 45dd16602625b28d2ca7e16f2fa6b0d62294fe81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674240"
---
# <a name="cdc-splitter"></a>Divisor CDC
  El divisor CDC divide un único flujo de filas de un flujo de datos de origen de CDC en varios flujos de datos para las operaciones de inserción, actualización y eliminación. El flujo de datos se divide según la columna obligatoria `__$operation` y sus valores estándar en las tablas de cambios de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
|Valor de la operación|Output|Descripción|  
|------------------------|------------|-----------------|  
|1|Eliminar|Fila eliminada|  
|2|Insertar|Fila insertada (no está disponible cuando se usa el modo CDC **Neto con combinación** )|  
|3|Actualizar|Fila antes de la actualización (disponible solo cuando se usa el modo CDC **Todo con los valores antiguos** )|  
|4|Actualizar|Fila después de la actualización (sigue a la de antes de la actualización)|  
|5|Actualizar|Fila de mezcla (solo disponible cuando se usa el modo CDC **Neto con combinación** )|  
|Otros|Error||  
  
 Puede usar el divisor para conectarse a los resultados predefinidos de INSERT, UPDATE, DELETE y UPDATE para un procesamiento posterior.  
  
 La transformación divisor CDC tiene una entrada normal y una salida de error.  
  
## <a name="error-handling"></a>Tratamiento de errores  
 La transformación divisor CDC tiene una salida de error. Las filas de entrada con un valor no válido de la columna $operation se consideran erróneas y se administran según la propiedad **ErrorRowDisposition** de la entrada.  
  
 La salida de error del componente incluye las columnas de salida siguientes:  
  
-   **Código de error**: se establece en 1.  
  
-   **Columna de error**: columna de origen que produce el error (para los errores de conversión).  
  
-   **Columnas de fila de error**: las columnas de entrada de la fila que produjo el error.  
  
## <a name="configuring-the-cdc-splitter"></a>Configuración del divisor CDC  
 No hay propiedades configurables del divisor CDC.  
  
 Para obtener más información sobre cómo usar el divisor CDC, vea Componentes CDC para Microsoft SQL Server Integration Services.  
  
 El cuadro de diálogo **Editor avanzado** contiene las propiedades que se pueden establecer mediante programación.  
  
 Para abrir el cuadro de diálogo **Editor avanzado** :  
  
-   En la pantalla **Flujo de datos** del proyecto de [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] , haga clic con el botón secundario en el divisor CDC y seleccione **Mostrar editor avanzado**.  
  
## <a name="see-also"></a>Consulte también  
 [Dirigir el flujo CDC según el tipo de cambio](direct-the-cdc-stream-according-to-the-type-of-change.md)  
  
  
