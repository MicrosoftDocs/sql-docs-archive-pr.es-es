---
title: Propiedades de SQL Server (pestaña Iniciar sesión) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 405073fc-eaa3-43c6-bf82-2cd58cacc1c3
author: stevestein
ms.author: sstein
ms.openlocfilehash: adec9ed7c69023218baa96ab8f8edbb6f2b365bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673404"
---
# <a name="sql-server-properties-log-on-tab"></a>Propiedades de SQL Server (pestaña Iniciar sesión)
  Utilice la pestaña **Iniciar sesión** del cuadro de diálogo **Propiedades de SQL Server** para especificar la cuenta que utiliza el servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , cambiar la contraseña de una cuenta e iniciar y detener el servicio. Cambiar la contraseña de una cuenta surte efecto inmediato.  
  
> [!NOTE]  
>  Cuando cambie el nombre de cuenta utilizado por un servicio en una instancia en clúster, la nueva cuenta debe formar parte del grupo de dominios que haya especificado durante la instalación para el servicio modificado, o bien debe tener permiso para agregar miembros a ese grupo. Si no tiene permisos para modificar la pertenencia al grupo, póngase en contacto con el administrador del dominio.  
>   
>  Para obtener información acerca de cómo seleccionar una cuenta para ejecutar el servicio, vea el tema sobre la configuración de cuentas de servicios de Windows en los Libros en pantalla de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="options"></a>Opciones  
 **Cuenta integrada**  
 **Sistema local**  
 -   Especifique la cuenta de sistema local. Esta cuenta no requiere ninguna contraseña. No obstante, la cuenta del sistema local puede impedir la interacción del servicio con otros servidores, en función de los privilegios que se hayan concedido a la cuenta.  
  
 **Servicio local**  
 -   Especifique la cuenta de servicio local. Esta cuenta no requiere ninguna contraseña. No obstante, la cuenta de servicio local puede impedir la interacción del servicio con otros servidores, en función de los privilegios que se hayan concedido a la cuenta.  
  
 **Servicio de red**  
 -   Se recomienda no utilizar la cuenta de servicio de red para los servicios de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Las cuentas de usuario local o de usuario de dominio son más adecuadas para estos servicios.  
  
 **Esta cuenta**  
 Especifique una cuenta de usuario local o de dominio que utilice la autenticación de Windows. Se recomienda utilizar una cuenta de usuario de dominio que tenga derechos mínimos para los servicios.  
  
 **Nombre de cuenta**  
 Escriba el nombre de la cuenta de usuario local o de dominio.  
  
 **Contraseña**  
 Escriba la contraseña de la cuenta.  
  
 **Confirmar contraseña**  
 Escriba de nuevo la contraseña de la cuenta.  
  
 **Iniciar**  
 Inicie el servicio.  
  
 **Detención**  
 Detenga el servicio.  
  
 **Pausar**  
 Pause el servicio.  
  
 **Reanudar**  
 Reanude un servicio en pausa.  
  
> [!IMPORTANT]  
>  De forma predeterminada, solo los miembros del grupo local de administradores pueden iniciar, detener, pausar, reanudar o reiniciar un servicio. Para conceder la capacidad de administrar servicios a usuarios que no son administradores, vea [CÓMO: Conceder a los usuarios derechos para administrar servicios en la familia Windows Server 2003](https://support.microsoft.com/kb/325349). El proceso es similar en las demás versiones de Windows.  
  
> [!NOTE]  
>  Si al iniciar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], aparece el error de WMI "no implementado [0x80004001]", podría indicar que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no está instalado en el equipo de destino.  
  
  
