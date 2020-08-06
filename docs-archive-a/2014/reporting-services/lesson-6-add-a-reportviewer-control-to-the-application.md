---
title: 'Lección 6: Agregar un control ReportViewer a la aplicación | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f9492a97-5609-4059-ae76-0fba111d4968
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bb04008fa47801f0500de711592a3cec45ca3dd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676872"
---
# <a name="lesson-6-add-a-reportviewer-control-to-the-application"></a>Lección 6: agregar un control ReportViewer a la aplicación
  Después de diseñar el informe secundario con el Asistente de informes, el paso siguiente consiste en agregar un control ReportViewer a la aplicación del sitio Web.  
  
### <a name="to-add-a-reportviewer-control-to-the-application"></a>Para agregar un control ReportViewer a la aplicación  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en **Default.aspx**y, después, haga clic en **Diseñador de vistas**.  
  
2.  En el grupo **Extensiones AJAX** , en la ventana **Cuadro de herramientas** , arrastre un control **ScriptManager** a la superficie de diseño.  
  
3.  En el grupo **Reporting** , arrastre un control **ReportViewer** a la superficie de diseño debajo del control **ScriptManager** .  
  
4.  Haga clic en la flecha de la esquina superior derecha del control **ReportViewer** para abrir la ventana **Tareas de ReportViewer** .  
  
5.  En el cuadro **Elegir informe** , seleccione el informe primario que creó.  
  
     Al seleccionar un informe, las instancias de los orígenes de datos usados en el informe se crean automáticamente. El código se genera para crear una instancia de cada DataTable (y el contenedor [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) ). Un control [ObjectDataSource](https://msdn.microsoft.com/library/system.web.ui.webcontrols.objectdatasource\(v=vs.100\).aspx) se agrega a la superficie de diseño, correspondiente a cada origen de datos usado en el informe. Este control de origen de datos se configura automáticamente.  
  
     Si utiliza Microsoft Visual Studio 2012, asegúrese de que el control ObjectDataSource está enlazado a DataSet1 que está completo con el espacio de nombres del proyecto, si el nombre completo se muestra en el cuadro de lista desplegable **Elija el objeto comercial** (por ejemplo, Projectnamespace. DataSet1TableAdapters. ProductTableAdapter). Tiene acceso al cuadro de lista haciendo clic con el botón secundario en ObjectDataSource y, después, haciendo clic en **Configurar origen de datos**.  
  
6.  En el menú Compilar, haga clic en Compilar sitio Web.  
  
     Se compila el informe y errores como un error de sintaxis en una expresión de informe aparecen en el área de **Lista de errores** . Haga clic en **Lista de errores** en la parte inferior de la ventana de Visual Studio para mostrar el área de **Lista de errores** .  
  
## <a name="next-task"></a>Tarea siguiente  
 Ha agregado correctamente un control ReportViewer a la aplicación del sitio Web. Después, agregará una acción de obtención de detalles en el informe primario.  
  
  
