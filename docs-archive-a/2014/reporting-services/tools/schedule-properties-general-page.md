---
title: Propiedades de la programación (página General) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.scheduleproperties.general.f1
ms.assetid: 20e43966-6caf-4972-a2e2-0d9131ac8f51
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a61837cd977526021be948d8c74a93eba6506e67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87671361"
---
# <a name="schedule-properties-general-page"></a>Propiedades de la programación (página General)
  Utilice esta página para ver o modificar una programación compartida. Las programaciones compartidas se pueden utilizar en lugar de las programaciones específicas del informe o de la suscripción. Los cambios a la programación se aplican después de guardarla. La edición de una programación no tiene ningún efecto en los trabajos que se encuentran actualmente en curso. Si edita una programación mientras se usa, todas las suscripciones y los informes de procesamiento actualmente desencadenados de dicha programación podrán terminar.  
  
 Una sola programación no admite todas las combinaciones de frecuencias. Por ejemplo, si desea ejecutar un informe todos los viernes a las 12:00 p. m. y a las 4:00 p. m. debe crear dos programaciones diarias que especifiquen una fecha de ejecución en viernes, una con las 12:00 p. m. como hora de inicio y otra con las 4:00 p. m. como hora de inicio.  
  
 El procesamiento de programaciones se basa en la hora local del servidor de informes que hospeda y procesa la programación.  
  
 Para abrir esta página, inicie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], conéctese a un servidor de informes, abra la carpeta **Programaciones compartidas** , haga clic con el botón secundario en una programación compartida y seleccione **Propiedades**.  
  
> [!NOTE]  
>  Esta característica no está disponible en todas las ediciones de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y esta página no aparece cuando se ejecuta una edición que no tiene esta característica. Para obtener una lista de las características admitidas por las ediciones de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vea [características compatibles con las ediciones de SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) ( https://go.microsoft.com/fwlink/?linkid=232473) .  
  
## <a name="options"></a>Opciones  
 **Nombre**  
 Especifica el nombre de la programación compartida.  
  
 **Empezar a ejecutar esta programación el**  
 Especifica una fecha de inicio para esta programación.  
  
 **Detener esta programación el**  
 Especifica una fecha de expiración para esta programación.  
  
 **Tipo**  
 Especifica si el patrón de periodicidad está basado principalmente en las horas, los días, las semanas, los meses o solo se ejecuta una vez.  
  
 **Hora (patrón de periodicidad)**  
 Especifica opciones para ejecutar una operación de programación en intervalos de una hora (por ejemplo, para ejecutar un informe cada 6 horas). Puede especificar el intervalo en horas y minutos.  
  
 **Día (patrón de periodicidad)**  
 Especifica opciones para ejecutar una operación de programación en intervalos de días (por ejemplo, para ejecutar un informe cada 2 días). Puede especificar el intervalo en días y a la hora y minutos en los que desea que se ejecute la programación.  
  
 **Semana (patrón de periodicidad)**  
 Especifica opciones para ejecutar una operación de programación en intervalos de una semana o cuando el patrón que desea repetir se basa en semanas (por ejemplo, para ejecutar un informe una semana sí y otra no). Puede especificar una programación semanal para el día, hora y minuto en los que desea que se ejecute la programación.  
  
 **Mes (patrón de periodicidad)**  
 Especifica opciones para ejecutar una operación de programación en intervalos de un mes o cuando el patrón que desea repetir se basa en meses. Puede especificar una programación mensual para el día, hora y minuto en los que desea que se ejecute la programación. Puede quitar meses específicos de la programación.  
  
 **Una sola vez**  
 Especifica una programación que se ejecuta solamente una vez, en una fecha y hora específicas.  
  
## <a name="see-also"></a>Consulte también  
 [Servidor de informes en Management Studio ayuda de F1](report-server-in-management-studio-f1-help.md)   
 [Conectarse a un servidor de informes en Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Crear, modificar y eliminar programaciones](../subscriptions/create-modify-and-delete-schedules.md)   
 [Programaciones](../subscriptions/schedules.md)  
  
  
