---
title: Página historial de informes (Administrador de informes) | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: reporting-services-native
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 06/13/2017
ms.openlocfilehash: 4070be8c1d6b0633131e96c665d4551c1b676a9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672639"
---
# <a name="report-history-page-report-manager"></a>Historial del informe (página del Administrador de informes)

Use la página Historial de informes para ver las instantáneas de informe que se generan y almacenan a lo largo del tiempo. Dependiendo de las opciones que se configuren en el servidor de informes, es posible que el historial de informe solamente contenga las instantáneas más recientes.  
  

El historial del informe siempre se ve en el contexto del informe desde el que se origina. No se puede ver el historial de todos los informes de un servidor de informes en un solo lugar.  
  
Para generar el historial de un informe, el informe debe poder ejecutarse en modo desatendido, es decir, debe utilizar credenciales almacenadas; los informes parametrizados deben contener valores predeterminados para todos los parámetros. Un historial de informe se puede generar manualmente o como una operación programada. Las propiedades del historial en el informe determinan las formas en que se puede crear el historial.  
  
Puede hacer clic en una instantánea del historial de un informe para verla. Las instantáneas que aparecen en un historial de informe solamente se distinguen por la fecha y la hora en que fueron creadas. No hay manera de distinguir visualmente si una instantánea se generó como respuesta a una operación programada o manual.  
  
> [!NOTE]  
>  Esta característica no está disponible en todas las ediciones de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Para obtener una lista de las características admitidas por las ediciones de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], vea [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="navigation"></a>Navegación  
 Utilice el procedimiento siguiente para navegar hasta esta ubicación en la interfaz de usuario (IU).  
  
### <a name="to-open-the-report-history-page"></a>Para abrir la página Historial del informe  
  
1.  Abra el Administrador de informes y busque el informe para el que desea ver las instantáneas de informe.  
  
2.  Mantenga el mouse sobre el informe y haga clic en la flecha de lista desplegable.  
  
3.  En el menú desplegable, haga clic en **Ver historial de informes**.  
  
## <a name="options"></a>Opciones  
 **Eliminar**  
 Haga clic para eliminar una o varias instantáneas. Antes de hacer clic en **Eliminar**, active la casilla situada junto a la instantánea que desee eliminar.  
  
 **Nueva instantánea**  
 Haga clic para agregar una instantánea al historial de informes Este botón está disponible cuando se elige la opción **Permitir que el historial se cree manualmente** en la página de propiedades Historial del informe.  
  
 **Última ejecución**  
 Muestra la fecha y la hora en que se creó la instantánea. Haga clic en una descripción para ver una instantánea determinada.  
  
 **Tamaño**  
 Muestra el tamaño de la definición del informe y los datos que contiene. Este valor indica el espacio que ocupan la definición y los datos del informe en la base de datos del servidor de informes. En realidad, el informe representado, que incluye el formato, tiene un tamaño mayor. El tamaño total, indicado entre paréntesis, suma los tamaños de todas las instantáneas del historial del informe actual.  
  
## <a name="see-also"></a>Consulte también  
 [Ver o eliminar el historial de informes &#40;Administrador de informes&#41;](../../2014/reporting-services/view-or-delete-report-history-report-manager.md)   
 [Agregar una instantánea al historial de informes &#40;Administrador de informes&#41;](report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [Página de propiedades generales, informes &#40;Administrador de informes&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md)   
 [Administrador de informes la ayuda F1](../../2014/reporting-services/report-manager-f1-help.md)   
 [Página de propiedades opciones de instantánea &#40;Administrador de informes&#41;](../../2014/reporting-services/snapshot-options-properties-page-report-manager.md)