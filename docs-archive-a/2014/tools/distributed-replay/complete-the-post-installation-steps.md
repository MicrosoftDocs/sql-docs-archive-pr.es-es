---
title: Complete los pasos posteriores a la instalación | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 0a788a2a-9b4f-4bfc-b1b5-83eeb1ea9ab2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1e9aae3dccaa409bcebc473213286f3edf19e7f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673951"
---
# <a name="complete-the-post-installation-steps"></a>Completar los pasos posteriores a la instalación
  Después de instalar Distributed Replay debe modificar las cuentas de los servicios de controlador y de cliente de Distributed Replay.  
  
### <a name="to-complete-the-post-installation-steps"></a>Para completar los pasos posteriores a la instalación  
  
1.  **Cree reglas de firewall**: en los equipos del controlador y cliente, debe permitir el tráfico entrante a través del firewall para el servicio correspondiente. Especifique las reglas de firewall para los ejecutables del servicio, ubicados en las carpetas de instalación.  
  
    1.  Para el servicio del controlador, cree una regla para **DReplayController.exe**, ubicada en la carpeta de instalación. Por ejemplo, el comando siguiente habilita esta regla, donde `%InstallPath%` es la carpeta de instalación del servicio:  
  
         `netsh advfirewall firewall add rule name="allow dreplay controller" dir=in program="%InstallPath%\DReplayController\DReplayController.exe" action=allow`  
  
    2.  Para el servicio de cliente, en cada equipo cliente, cree una regla para **DReplayClient.exe**, ubicada en la carpeta de instalación. Por ejemplo, el comando siguiente habilita esta regla, donde `%InstallPath%` es la carpeta de instalación del servicio:  
  
         `netsh advfirewall firewall add rule name="allow dreplay client" dir=in program="%InstallPath%\DReplayClient\DReplayClient.exe" action=allow`  
  
2.  **Conceda permisos a todos los clientes en el servidor de destino**: después de completar la instalación del servicio de cliente en los equipos cliente, debe agregar manualmente las cuentas del servicio de cliente al rol sysadmin en la instancia de destino de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 Debe disponer de permisos administrativos para instalar cualquiera de las características de Distributed Replay. Solo un inicio de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con permisos sysadmin puede agregar las cuentas del servicio de cliente al rol de servidor sysadmin del servidor de prueba. Para obtener más información sobre las consideraciones de seguridad de Distributed Replay, vea [Distributed Replay Security](distributed-replay-security.md).  
  
  
