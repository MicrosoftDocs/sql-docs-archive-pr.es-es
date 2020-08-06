---
title: 'Tarea 9: configuración de un servicio de datos de referencia | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: d0535fce-2bf5-4f6d-b517-ffe6fa13738d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1e7c685de13a2f5c495482f816818ff6b838fc7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751542"
---
# <a name="task-9-configuring-a-reference-data-service"></a>Tarea 9: Configuración de un servicio de datos de referencia
  En esta tarea, se configura DQS para usar un servicio de datos de referencia en Azure Marketplace. En la tarea siguiente, configurará el dominio de **validación de direcciones** para utilizar este servicio. En tiempo de ejecución, durante la actividad de limpieza, DQS pasa los valores de los dominios del dominio de **validación de direcciones** al servicio para su limpieza. Vea [configurar DQS para usar datos de referencia](https://msdn.microsoft.com/library/hh213070.aspx) para obtener más detalles.  
  
1.  En la Página principal del **cliente DQS**, en el panel **Administración** , haga clic en **configuración**.  
  
2.  Asegúrese de que la pestaña **datos de referencia** está activa.  
  
3.  En el área **configuración de red** , escriba los valores adecuados en los campos **servidor proxy** y **Puerto** si necesita usar un servidor proxy para conectarse a Internet.  
  
4.  Escriba la **clave de la cuenta de Azure Marketplace** para el campo ID. de **cuenta de datamarket** .  
  
     ![Cuenta de servicio de datos de referencia de Azure Data Market](../../2014/tutorials/media/et-configuringareferencedataservice.jpg "Cuenta de servicio de datos de referencia de Azure Data Market")  
  
5.  Haga clic en el botón **validar** junto al cuadro de texto para validar el identificador de la cuenta.  
  
6.  Haga clic en **Aceptar** en el cuadro de mensaje.  
  
7.  Haga clic en **cerrar** en la parte inferior de la página para cambiar a la Página principal del cliente DQS.  
  
## <a name="next-task"></a>Tarea siguiente  
 [Tarea 10: Configuración de un dominio compuesto para usar un servicio de datos de referencia](../../2014/tutorials/task-10-configuring-composite-domain-to-use-reference-data-service.md)  
  
  
