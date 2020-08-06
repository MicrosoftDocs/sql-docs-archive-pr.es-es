---
title: Ver informes de optimización | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- tuning reports [SQL Server]
ms.assetid: daee6143-269f-428b-8458-9a3e726d586c
author: stevestein
ms.author: sstein
ms.openlocfilehash: b873175068daaba5a269af63a8c8ce1f4e1347a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87747348"
---
# <a name="viewing-tuning-reports"></a>Ver informes de optimización
  En la práctica anterior de esta lección, ha visto los scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] que crean o colocan objetos de bases de datos en las recomendaciones del Asistente para la optimización de motor de base de datos generadas como resultado de la sesión de optimización MySession. La sesión MySession se creó en [Tuning a Workload](lesson-1-1-tuning-a-workload.md).  
  
 Aunque es muy útil ver los scripts que pueden utilizarse para implementar los resultados de optimización, el Asistente para la optimización de motor de base de datos también ofrece varios informes muy útiles que podrá ver. Estos informes proporcionan información acerca de las estructuras de diseño físico existentes en la base de datos que está optimizando y acerca de las estructuras recomendadas. Los informes de optimización pueden verse haciendo clic en la pestaña **Informes** , tal y como se describe en la práctica siguiente. Esta práctica utiliza las sesiones de optimización MySession y EvaluateMySession que ha creado en [Tuning a Workload](lesson-1-1-tuning-a-workload.md) y [Viewing Tuning Recommendations](lesson-1-2-viewing-tuning-recommendations.md).  
  
### <a name="view-tuning-reports"></a>Ver informes de optimización  
  
1.  Inicie el Asistente para la optimización de motor de base de datos. Consulte [Iniciar el Asistente para la optimización de motor de base de datos](../../relational-databases/performance/database-engine-tuning-advisor.md). Asegúrese de que se conecta a la misma instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que utilizó en las prácticas anteriores de esta lección.  
  
     Haga doble clic en **MySession** en el panel **Monitor de sesión** . El Asistente para la optimización de motor de base de datos carga la información de sesión para la sesión actual.  
  
2.  Haga clic en la pestaña **Informes** .  
  
3.  En el panel **Resumen de la optimización** , puede ver información acerca de esta sesión de optimización. Utilice la barra de desplazamiento para ver todo el contenido del panel. Observe las opciones **Porcentaje de mejora esperada** y **Espacio usado por la recomendación**. Es posible limitar el espacio utilizado por la recomendación al establecer las opciones de optimización. En la pestaña **Opciones de optimización** , seleccione **Opciones avanzadas**. Active **Definir espacio máximo para recomendaciones** y especifique el espacio máximo, en megabytes, que una configuración de recomendación puede usar. Use el botón **Atrás** del explorador de la Ayuda para volver a este tutorial.  
  
4.  En el panel **Informes de optimización** , haga clic en **Informe de costo de instrucciones** en la lista **Seleccionar informe** . Si necesita más espacio para ver el informe, arrastre el borde del panel del **Monitor de sesión** hacia la izquierda. Cada instrucción [!INCLUDE[tsql](../../includes/tsql-md.md)] que se ejecuta para una tabla en la base de datos tiene un costo de rendimiento asociado. Este costo de rendimiento puede reducirse creando índices efectivos en las columnas que se consultan frecuentemente en una tabla. Este informe muestra el porcentaje estimado de mejora entre el costo original que resulta de ejecutar una instrucción en la carga de trabajo y el costo que resultaría de implementar la recomendación de optimización. Observe que la cantidad de información que contiene el informe se basa en la longitud y complejidad de la carga de trabajo.  
  
5.  Haga clic con el botón derecho en el panel **Informe de costo de instrucciones** del área de la cuadrícula y haga clic en **Exportar a archivo**. Guarde el informe como `MyReport` . Automáticamente se anexará la extensión .xml al nombre del archivo. Puede abrir el archivo MyReport.xml en el editor XML que prefiera o en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] para ver el contenido del informe.  
  
6.  Vuelva a la pestaña **Informes** del Asistente para la optimización de motor de base de datos y vuelva a hacer clic con el botón derecho en **Informe de costo de instrucciones** . Revise las otras opciones disponibles. Tenga en cuenta que puede cambiar la fuente del informe que está viendo. Al cambiar la fuente aquí, también se cambiará en las demás páginas con pestañas.  
  
7.  Haga clic en otros informes de la lista **Seleccionar informe** para familiarizarse con ellos.  
  
## <a name="summary"></a>Resumen  
 Ha explorado la pestaña **Informes** de la GUI del Asistente para la optimización de motor de base de datos para la sesión de optimización MySession. Puede utilizar estos mismos pasos para explorar los informes que se generaron para la sesión de optimización EvaluateMySession. Haga doble clic en **EvaluateMySession** en el panel **Monitor de sesión** para comenzar.  
  
## <a name="next-lesson"></a>Lección siguiente  
 [Lección 3: Uso de la utilidad del símbolo del sistema DTA](lesson-3-using-the-dta-command-prompt-utility.md)  
  
  
