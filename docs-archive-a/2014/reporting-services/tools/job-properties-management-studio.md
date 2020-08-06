---
title: Propiedades del trabajo (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.jobproperties.f1
ms.assetid: 807ffd0e-9363-4f8f-9c36-c5d746ad19fd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c4d309ba78a21114cf51c48f0a5c5b3b2f7c2500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746131"
---
# <a name="job-properties-management-studio"></a>Propiedades del trabajo (Management Studio)
  Use la página **Propiedades del trabajo** para ver información sobre una suscripción o un informe en curso antes de cancelarlo.  
  
 Para abrir esta página, inicie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], conéctese a un servidor de informes y abra la carpeta **Trabajos** . Haga clic con el botón derecho en un trabajo que se está ejecutando y luego haga clic en **Propiedades**.  
  
> [!NOTE]  
>  Esta característica no se admite en [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] con Advanced Services. La página no aparece cuando se ejecuta [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].  
  
## <a name="tasks"></a>Tareas  
 Para poder ver información acerca de un trabajo, actualice la página para recuperar información sobre los trabajos que se están ejecutando actualmente en el servidor de informes:  
  
1.  Abra la carpeta del servidor de informes.  
  
2.  Haga clic con el botón derecho en **Trabajos**y luego haga clic en **Actualizar**.  
  
3.  Si un trabajo aparece en una lista, haga clic con el botón derecho en él y luego haga clic en **Propiedades**.  
  
## <a name="options"></a>Opciones  
 **Id. del trabajo**  
 Un GUID que se asigna a un trabajo mientras se está procesando. El valor se genera de forma aleatoria cada vez que se ejecuta un informe o suscripción.  
  
 **Estado del trabajo**  
 Los valores válidos son **Nuevo** y **En ejecución**. Estado siempre es **Nuevo** cuando comienza el trabajo. Después de 60 segundos, el estado cambia a **En ejecución**. Debe actualizar la página para que se refleje el cambio.  
  
 **Tipo de trabajo**  
 Los valores válidos son **Usuario** y **Sistema**. Un trabajo de usuario es cualquier trabajo que haya iniciado un usuario individual; por ejemplo, ejecutar un informe a petición, generar manualmente una instantánea del historial de informes o crear manualmente una instantánea de ejecución de informe. Una suscripción estándar en curso es también un trabajo de usuario. Un trabajo del sistema es un trabajo iniciado por el servidor de informes; Los trabajos del sistema incluyen el procesamiento de informes que se desencadena por una programación.  
  
 **Acción del trabajo**  
 Para los informes, esta columna muestra qué procesos de ejecución de informe están en curso. Este valor siempre es **Representar**.  
  
 **Descripción del trabajo**  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] no proporciona descripciones de trabajo de forma predeterminada.  
  
 **Nombre de servidor**  
 Muestra el nombre del servidor de informes que está procesando el trabajo. Si configurara una implementación escalada, este valor mostrará qué servidor está procesando el trabajo.  
  
 **Nombre del informe**  
 Muestra el nombre del informe. Las suscripciones se identifican con su descripción.  
  
 **Ruta de acceso del informe**  
 Muestra la ruta de acceso del informe en la jerarquía de carpetas del servidor de informes.  
  
 **Start Time**  
 Muestra cuándo se inició el proceso.  
  
 **Nombre de usuario**  
 Para los procesos iniciados por un usuario, esta columna muestra el nombre del usuario. Para los trabajos del sistema, éste es el nombre del servidor de informes.  
  
## <a name="see-also"></a>Consulte también  
 [Servidor de informes en Management Studio ayuda F1](report-server-in-management-studio-f1-help.md)   
 [Conectar con un servidor de informes en Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Administración de un proceso en ejecución](../subscriptions/manage-a-running-process.md)  
  
  
