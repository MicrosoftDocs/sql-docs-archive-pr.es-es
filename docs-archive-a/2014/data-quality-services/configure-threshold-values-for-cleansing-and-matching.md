---
title: Configurar los valores de umbral para la limpieza y la coincidencia | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.admin.config.general.f1
helpviewer_keywords:
- cleansing,threshold value
- cleansing threshold values
- matching,threshold value
ms.assetid: d2305409-7115-45a4-8f60-1213c0a47368
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0faf64e96468a3a9aac0de12d3ec3acbb1e1ed85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744319"
---
# <a name="configure-threshold-values-for-cleansing-and-matching"></a>Configurar los valores de umbral para la limpieza y coincidencia
  En este tema se describe cómo configurar los valores de umbral que se utilizarán durante las actividades de limpieza y búsqueda de coincidencias asistidas por PC en [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="security"></a><a name="Security"></a> Seguridad  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permisos  
 Para configurar estos valores de umbral, debe disponer del rol dqs_administrator en la base de datos DQS_MAIN.  
  
##  <a name="configuring-the-threshold-values"></a><a name="Configure"></a> Configurar los valores de umbral  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Ejecute la aplicación Data Quality Client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  En la página de inicio de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , haga clic en **Configuración**.  
  
3.  A continuación, haga clic en la pestaña **Configuración general** . Esta pestaña le permite especificar los valores de umbral para la limpieza y las actividades coincidentes.  
  
4.  Para establecer los valores de umbral para la actividad de limpieza, especifique los valores adecuados en los cuadros siguientes del área **Limpieza interactiva** :  
  
    -   **Puntuación mínima para sugerencias**: la puntuación mínima o el nivel de confianza que utilizará DQS para sugerir reemplazos para un valor durante el proceso de limpieza asistida por PC. Escriba un valor en la notación decimal del valor de porcentaje correspondiente. Por ejemplo, escriba 0,75 para un porcentaje del 75%. Este valor debe ser menor o igual que el valor especificado en el cuadro **Puntuación mínima de correcciones automáticas** . El valor predeterminado es 0,7.  
  
    -   **Puntuación mínima de correcciones automáticas**: la puntuación mínima o el nivel de confianza que utilizará DQS para corregir automáticamente un valor durante el proceso de limpieza asistida por PC. Escriba un valor en la notación decimal del valor de porcentaje correspondiente. Por ejemplo, escriba 0,9 para un porcentaje del 90%. El valor predeterminado es 0,8.  
  
5.  Para establecer el valor de umbral para la actividad de búsqueda de coincidencias, especifique un valor en el cuadro **Puntuación de registro mínima** en el área **Coincidencia** . Este valor indica la puntuación mínima necesaria para que un registro se considere como una coincidencia de otro. El valor predeterminado es 80 %.  
  
6.  Haga clic en **Cerrar**.  
  
  
