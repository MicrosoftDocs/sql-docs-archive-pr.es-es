---
title: Propiedades TCP/IP (pestaña protocolos) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- TCP/IP [SQL Server], configuration options
ms.assetid: 007638fc-3a24-4460-adbe-545ded5d6f88
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1d5bc28faddae9a86a6636b56b907b57a2d8711a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663260"
---
# <a name="tcp---ip-properties-protocols-tab"></a>Propiedades de TCP-IP (pestaña protocolos)
  Use el cuadro de diálogo **Propiedades de TCP/IP** para configurar las opciones para el protocolo TCP/IP. Haga clic en **TCP/IP** en el panel izquierdo para mostrar configuraciones de direcciones IP individuales en el panel de detalles.  
  
 Es necesario reiniciar Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para que se apliquen los cambios.  
  
## <a name="options"></a>Opciones  
 **Enabled**  
 Los valores posibles son **Yes** y **No**.  
  
 **Keep Alive**  
 Especifique el intervalo (en milisegundos) en el que los paquetes de mantenimiento de conexión se transmitirán para comprobar si el equipo que está en la parte remota de una conexión todavía está disponible.  
  
 **Listen All**  
 Especifique si SQL Server escuchará en todas las direcciones IP que están enlazadas a tarjetas de red en el equipo. Si se establece en **No**, configure cada dirección IP por separado con el cuadro de diálogo de propiedades de cada dirección IP. Si se establece en **Yes**, la configuración del cuadro de propiedades de **IPAll** se aplicará en todas las direcciones IP. El valor predeterminado es **Yes**.  
  
 **No Delay**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no implementa cambios en esta propiedad.  
  
## <a name="see-also"></a>Consulte también  
 [Elegir un protocolo de red](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)   
 [Crear una cadena de conexión válida con TCP/IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)  
  
  
