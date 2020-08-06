---
title: Agregar dirección IP (cuadro de diálogo - SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygrouplistener.addipaddress.f1
ms.assetid: 98c9ad3b-ff3c-4c1d-b344-59a72fca137c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5192e6414b34bee6de09d45a7284f25404235dc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663724"
---
# <a name="add-ip-address-dialog-box-sql-server-management-studio"></a>Agregar dirección IP (cuadro de diálogo - SQL Server Management Studio)
   En este tema de Ayuda F1 se describen las opciones del cuadro de diálogo **Agregar dirección IP**. Se accede a este cuadro de diálogo desde el cuadro de diálogo **Nuevo agente de escucha del grupo de disponibilidad** y la pestaña **Escucha** de la página **Especificar réplicas** de [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] o [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
## <a name="prerequisites"></a>Requisitos previos  
 Antes de empezar a agregar subredes un agente de escucha del grupo de disponibilidad, asegúrese de que conoce la dirección IP para cada subred y, para una dirección IPv4, la máscara de subred.  
  
##  <a name="add-ip-address-options"></a><a name="PageOptions"></a> Agregar las opciones de la dirección IP  
 **Subred**  
 Utilice la lista desplegable para seleccionar una dirección de la subred que va a agregar al agente de escucha del grupo de disponibilidad. De forma predeterminada, una subred posee una dirección IPv4 como una dirección IPv6. La primera vez que use el cuadro de diálogo **Agregar dirección IP** , la lista desplegable **Subred** mostrará las dos direcciones de subred para cada subred que hospeda una réplica para el grupo de disponibilidad. Para agregar una subred dada al agente de escucha, seleccione una de sus direcciones de subred.  
  
 Después de completar el cuadro de diálogo **Agregar dirección IP** y hacer clic en **Aceptar** para agregar una dirección de subred seleccionada al agente de escucha, la lista desplegable **Subred** filtrará la dirección de subred. Todas las direcciones de subred no seleccionadas permanecerán en la lista desplegable. Asegúrese de agregar una y solo una dirección de subred por subred al agente de escucha; de lo contrario, la creación del agente de escucha producirá un error.  
  
 **Direcciones**  
 Utilice este campo para escribir una dirección IP estática para la dirección de subred seleccionada. Póngase en contacto con su administrador de red para esta dirección IP. Asegúrese de escribir una dirección válida para la dirección de subred seleccionada; de lo contrario, la creación del agente de escucha producirá un error.  
  
 **Dirección IPv4**  
 Si ha seleccionado una dirección IPv4 de una subred, escriba aquí una dirección estática IPv4 válida.  
  
 **Máscara de subred**  
 Para una dirección IPv4, este campo de solo lectura muestra la máscara de subred de la subred seleccionada.  
  
 **Dirección IPv6**  
 Si ha seleccionado una dirección IPv6 de una subred, escriba aquí una dirección estática IPv6 válida.  
  
 **OK (CORRECTO)**  
 Haga clic para agregar la subred cuya dirección ha seleccionado, junto con la dirección IP estática que ha especificado. Una fila con estos valores se agregará a la cuadrícula de subred del cuadro de diálogo **Nuevo agente de escucha del grupo de disponibilidad** o **Especificar réplicas** .  
  
> [!IMPORTANT]  
>  El cuadro de diálogo de **Agregar dirección IP** no comprueba la dirección IP. Tampoco impide agregar la segunda dirección de subred para una subred ya agregada al agente de escucha del grupo de disponibilidad.  
  
 **Cancelar**  
 Haga clic para cancelar las selecciones y volver al cuadro de diálogo **Nuevo agente de escucha de grupo de disponibilidad** o en la pestaña **Escucha** sin agregar una dirección IP estática para una subred.  
  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tareas relacionadas  
  
-   [Crear o configurar un agente de escucha de grupo de disponibilidad &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Usar el cuadro de diálogo Nuevo grupo de disponibilidad &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Usar el Asistente para agregar una réplica al grupo de disponibilidad &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
  
## <a name="see-also"></a>Consulte también  
 [Información general de Grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Agentes de escucha de grupo de disponibilidad, conectividad de cliente y conmutación por error de una aplicación &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)   
 [Conectividad de cliente de AlwaysOn (SQL Server)](always-on-client-connectivity-sql-server.md)  
  
  
