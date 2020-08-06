---
title: Página validación (asistentes para grupos de disponibilidad AlwaysOn) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.newagwizard.validation.f1
- sql12.swb.addreplicawizard.validation.f1
- sql12.swb.adddatabasewizard.validation.f1
helpviewer_keywords:
- ', listeners'
ms.assetid: c8971556-240c-491a-bc86-9cc72f71a3dd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f2010074a357932f8af7358a05ee6ed16f5c0881
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663128"
---
# <a name="validation-page-alwayson-availability-group-wizards"></a>Página Validación (asistentes para grupos de disponibilidad AlwaysOn)
  En este tema de Ayuda se describen las opciones de la página **Validación** . Esta tema se aplica a [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)], [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)]y [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Utilice esta página para validar que el entorno admite todas las opciones de configuración realizada en las páginas anteriores del asistente.  
  
##  <a name="validation-page-options"></a><a name="PageOptions"></a>Opciones de la página validación  
 **Resultados de la validación de grupos de disponibilidad.**  
 Esta cuadrícula muestra los resultados de cada paso de la validación completado. Las columnas de la cuadrícula son las siguientes:  
  
 **Nombre**  
 Muestra una frase que describe un paso concreto.  
  
 **Resultado**  
 Muestra uno de los siguientes texto de hipervínculo. Para obtener más información sobre el resultado del paso de la validación determinado, haga clic en el hipervínculo.  
  
|Resultado|Descripción|  
|------------|-----------------|  
|**Error**|Indica que se produjo un error en el paso de la validación. Haga clic en el vínculo para ver el mensaje de error.|  
|**Omitido**|Indica que el paso de la validación se omite porque no lo requieren las opciones seleccionadas. Haga clic en el vínculo para ver el motivo por el que un paso se ha omitido.|  
|**Success**|Indica que el paso de la validación se completó correctamente|  
|**Advertencia**|Indica un problema potencial con la configuración del grupo de disponibilidad.  Haga clic en el vínculo para ver el mensaje de advertencia.|  
  
 **Volver a ejecutar la validación**  
 Haga clic para repetir los pasos de la validación si realiza un cambio fuera del asistente en respuesta a un error de validación.  
  

  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tareas relacionadas  
  
-   [Usar el cuadro de diálogo Nuevo grupo de disponibilidad &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Usar el Asistente para agregar una réplica al grupo de disponibilidad &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Usar el Asistente para agregar una base de datos al grupo de disponibilidad &#40;SQL Server Management Studio&#41;](availability-group-add-database-to-group-wizard.md)  
  
 
  
## <a name="see-also"></a>Consulte también  
 [Información general de Grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
  
