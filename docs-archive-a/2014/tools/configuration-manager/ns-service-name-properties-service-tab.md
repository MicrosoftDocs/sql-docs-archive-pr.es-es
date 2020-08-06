---
title: Propiedades de NS $ &lt; nombre de servicio &gt; (pestaña servicio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 57c6b791-1663-4a01-9de2-cf1bdd8adb2c
author: stevestein
ms.author: sstein
ms.openlocfilehash: ddd80cf1c84e3fe7acc538e6aa65230b45870219
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748428"
---
# <a name="nsltservice-namegt-properties-service-tab"></a>Propiedades de NS$&lt;nombre de servicio&gt; (pestaña Servicio)
  Este es el servicio [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNS](../../includes/ssns-md.md)]. Los valores de propiedades en color gris claro no se pueden modificar con esta aplicación.  
  
## <a name="options"></a>Opciones  
 **Ruta de acceso binaria**  
 Muestra la ubicación de los archivos de programa utilizados por el servicio.  
  
 **Control de error**  
 1 indica `SERVICE_ERROR_NORMAL`. Si el servicio no se inicia al iniciar el equipo, el programa de inicio registra el error y muestra un cuadro de mensaje emergente pero continúa con la operación de inicio. Este valor no puede modificarse.  
  
 **Código de salida**  
 Si se produce un error, el número de error aparece en este cuadro. Utilice este número para solucionar errores buscando el número en [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base o informe del mismo al personal de soporte técnico.  
  
 **Host Name**  
 Muestra el nombre del equipo o clúster que ejecuta la búsqueda de texto completo.  
  
 **Nombre**  
 Indica el nombre para mostrar del servicio.  
  
 **Id. del proceso**  
 Muestra el Id. de proceso de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 **Tipo de servicio de SQL**  
 Tipo de servicio proporcionado a los procesos de llamada. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instala varios servicios.  
  
 **Modo de inicio**  
 Para este servicio se pueden configurar las siguientes opciones:  
  
-   Manual: el servicio no se inicia automáticamente al iniciar el equipo. Debe iniciarlo mediante el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] u otra herramienta.  
  
-   Automático: el servicio intenta iniciarse cuando se inicia el equipo.  
  
-   Deshabilitado: el servicio no se puede iniciar.  
  
 **State**  
 Indica si el servicio está en ejecución, detenido o deshabilitado.  
  
  
