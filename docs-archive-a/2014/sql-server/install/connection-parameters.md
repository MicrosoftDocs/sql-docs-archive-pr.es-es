---
title: Parámetros de conexión | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], connections
- authentication [Upgrade Advisor]
- SQL Server Upgrade Advisor, connections
- connections [Upgrade Advisor]
- server instances [Upgrade Advisor]
- default server instances
- analyzing system [Upgrade Advisor], connections
ms.assetid: f754d038-637a-4d8e-85b0-b242e6499d26
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 27eb69dfd2c41710a47861e0992486267f692a3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87670778"
---
# <a name="connection-parameters"></a>Parámetros de conexión
  Para analizar ciertos tipos de servidor, como [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], debe seleccionar una instancia concreta de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La instancia predeterminada de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] está seleccionada automáticamente. Puede cambiar la selección o seleccionar una instancia única a la vez para el análisis del Asesor de actualizaciones. Si ha incluido un tipo de servidor que requiere autenticación, debe escribir el modo de autenticación y las credenciales.  
  
## <a name="options"></a>Opciones  
 **Nombre del servidor**  
 Se rellena previamente con el nombre de equipo que escribió en el panel Componentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Nombre de instancia**  
 Seleccione una de las instancias de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que están disponibles en el equipo. Si no aparece una lista de instancias, use MSSQLSERVER para examinar la instancia predeterminada. Esto es especialmente interesante para equipos remotos. También puede utilizar la palabra "predeterminado" para examinar la instancia predeterminada.  
  
 **Autenticación**  
 Seleccione un modo de autenticación de la lista de modos de autenticación disponibles en este equipo. De forma predeterminada, el modo de autenticación es Autenticación de Windows.  
  
 **Nombre de usuario**  
 Si usa la autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], escriba un nombre de usuario en el cuadro. Es recomendable que el nombre de usuario tenga credenciales administrativas en este equipo.  
  
> [!NOTE]  
>  Si selecciona autenticación de Windows, el nombre de usuario del usuario que ha iniciado la sesión actual se rellena en el cuadro de texto **nombre de usuario** .  
  
 **Contraseña**  
 Escriba la contraseña del usuario especificado.  
  
## <a name="see-also"></a>Consulte también  
 [Trabajar con el asesor de actualizaciones](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Referencia de la interfaz de usuario del Asesor de actualizaciones](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
