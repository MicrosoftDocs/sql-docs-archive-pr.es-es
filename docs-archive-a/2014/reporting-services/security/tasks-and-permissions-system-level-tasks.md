---
title: Tareas de nivel de sistema | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- system-level tasks [Reporting Services]
ms.assetid: 7023b388-40b2-4590-b227-115cf380a1e7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 98f9390664064cd293b80d094d65c903869bc709
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87749049"
---
# <a name="system-level-tasks"></a>Tareas de nivel de sistema
  Una tarea de nivel de sistema es una colección de permisos relativos a las operaciones correspondientes al sitio del servidor de informes en general. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] también incluye tareas de nivel de elemento que corresponden a elementos específicos. Para obtener más información, vea [Tareas de nivel de elemento](tasks-and-permissions-item-level-tasks.md). Para obtener más información acerca de tareas y permisos en general, vea [Tasks and Permissions](tasks-and-permissions.md).  
  
> [!NOTE]  
>  Si trabaja con estas tareas mediante programación, debe utilizar métodos que admitan tareas de nivel de sistema. Para más información, vea <xref:ReportService2010.ReportingService2010.ListTasks%2A> y <xref:ReportService2010.ReportingService2010.ListRoles%2A>.  
  
## <a name="permissions-in-system-level-tasks"></a>Permisos en tareas de nivel de sistema  
 La siguiente tabla identifica la colección de permisos para cada tarea del sistema. Los permisos se incluyen con fin informativo únicamente, para proporcionar una descripción más exacta de la funcionalidad disponible con cada tarea.  
  
|Tarea|Permisos|  
|----------|-----------------|  
|Ejecutar definiciones de informe|Ejecutar definiciones de informe (el nombre del permiso y la tarea es el mismo)|  
|Generación de eventos|Generar eventos|  
|Trabajos de administración|Leer propiedades del sistema<br /><br /> Actualizar propiedades del sistema|  
|Administrar propiedades del servidor de informes|Leer propiedades del sistema<br /><br /> Actualizar propiedades del sistema|  
|Administrar roles|Crear roles<br /><br /> Eliminar roles<br /><br /> Leer propiedades de roles<br /><br /> Actualizar propiedades de roles|  
|Administrar programaciones compartidas|Crear programaciones|  
|Administrar la seguridad del servidor de informes|Leer directivas de seguridad del sistema<br /><br /> Actualizar directivas de seguridad del sistema|  
|Ver propiedades del servidor de informes|Leer propiedades del sistema|  
|Ver programaciones compartidas|Leer programaciones|  
  
## <a name="see-also"></a>Consulte también  
 [Concesión de permisos en un servidor de informes en modo nativo](granting-permissions-on-a-native-mode-report-server.md)  
  
  
