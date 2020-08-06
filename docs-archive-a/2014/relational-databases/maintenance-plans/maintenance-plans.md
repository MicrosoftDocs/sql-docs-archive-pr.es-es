---
title: Planes de mantenimiento | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- SQL12.AG.MAINTPLAN.LEGACY.F1
helpviewer_keywords:
- maintenance plans [SQL Server], about database maintenance plans
- maintenance plans [SQL Server], database compatibility level displayed in designer
- maintenance plans [SQL Server]
ms.assetid: 5982ca65-74fe-44e3-aef9-00a65a0db169
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2f614e2cfad78cb1efddc49cc897ca57087fec68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662019"
---
# <a name="maintenance-plans"></a>Planes de mantenimiento
  Los planes de mantenimiento crean un flujo de trabajo de las tareas necesarias para asegurarse de que la base de datos está optimizada, se realizan copias de seguridad de la misma con regularidad y no tiene incoherencias. El Asistente para planes de mantenimiento también crea planes de mantenimiento principales, pero la creación manual de planes le da mucha más flexibilidad.  
  
## <a name="benefits-of-maintenance-plans"></a>Ventajas de los planes de mantenimiento  
 En [!INCLUDE[ssDECurrent](../../includes/ssdecurrent-md.md)], los planes de mantenimiento crean un paquete de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , que ejecuta un trabajo del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Los planes de mantenimiento se pueden ejecutar manual o automáticamente a intervalos programados.  
  
 Los planes de mantenimiento de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] proporcionan las características siguientes:  
  
-   Creación de flujos de trabajo con diferentes tareas de mantenimiento típicas. También puede crear sus propios scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] personalizados.  
  
-   Jerarquías conceptuales. Cada plan le permite crear o editar flujos de trabajo de tareas. Las tareas de cada plan se pueden agrupar en subplanes, que se pueden programar para ejecutarse a horas diferentes.  
  
-   Compatibilidad con planes multiservidor que se pueden utilizar en entornos de servidor maestro o servidor de destino.  
  
-   Compatibilidad con el historial de planes de registro en los servidores remotos.  
  
-   Compatibilidad con la autenticación de Windows y la autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
## <a name="maintenace-plan-functionality"></a>Funcionalidad de plan de mantenimiento  
 Los planes de mantenimiento se pueden crear para realizar las tareas siguientes:  
  
-   Reorganizar los datos de las páginas de datos y de índices mediante una nueva generación de los índices con un nuevo factor de relleno. Al volver a crear índices con un nuevo factor de relleno se asegura que las páginas de la base de datos contienen una cantidad de datos y espacio disponible distribuidos por igual. También permite un crecimiento más rápido en el futuro. Para obtener más información, vea [Especificar el factor de relleno para un índice](../indexes/specify-fill-factor-for-an-index.md).  
  
-   Comprimir archivos de datos mediante la eliminación de las páginas de base de datos que estén vacías.  
  
-   Actualizar las estadísticas de los índices para asegurarse de que el optimizador de consultas dispone de información actualizada acerca de la distribución de los valores de los datos en las tablas. Esto permite al optimizador de consultas elegir el método más adecuado para obtener acceso a los datos, ya que dispone de más información acerca de los datos almacenados en la base de datos. Aunque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] actualiza periódicamente las estadísticas de los índices de forma automática, esta opción puede obligar a que se actualicen inmediatamente.  
  
-   Realizar comprobaciones de coherencia interna de los datos y de las páginas de datos de la base de datos para asegurarse de que no se han dañado debido a un problema de software o del sistema.  
  
-   Realizar copias de seguridad de la base de datos y de los archivos de registro de transacciones. Las copias de seguridad de la base de datos y del registro pueden mantenerse durante un período especificado. Esto le permite crear un historial de copias de seguridad para utilizarlo si tiene que restaurar la base de datos a una fecha anterior a la de la última copia de seguridad de la base de datos. También puede realizar copias de seguridad diferenciales.  
  
-   Ejecutar trabajos del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Se puede usar para crear trabajos que realicen diversas acciones y los planes de mantenimiento para ejecutar esos trabajos.  
  
 Los resultados generados por las tareas de mantenimiento se pueden escribir como informe en un archivo de texto en las tablas del plan de mantenimiento (`sysmaintplan_log` y `sysmaintplan_logdetail`) en `msdb`. Para ver los resultados en el visor de archivos de registro, haga clic con el botón derecho en **Planes de mantenimiento** y, luego, haga clic en **Ver historial**.  
  
## <a name="related-tasks"></a>Related Tasks  
 Use los temas siguientes para empezar a trabajar con planes de mantenimiento.  
  
|||  
|-|-|  
|**Descripción**|**Tema.**|  
|Describe cómo crear un plan de mantenimiento mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].|[Crear un plan de mantenimiento](create-a-maintenance-plan.md)|  
|Describe cómo crear un plan de mantenimiento mediante la superficie de diseño Plan de mantenimiento.|[Crear un plan de mantenimiento &#40;superficie de diseño del plan de mantenimiento&#41;](create-a-maintenance-plan-maintenance-plan-design-surface.md)|  
|Documenta la funcionalidad de los planes de mantenimiento disponible en el Explorador de objetos.|[Planes de mantenimiento &#40;nodo del Explorador de objetos&#41;](../../ssms/object/object-explorer.md)|  
  
  
