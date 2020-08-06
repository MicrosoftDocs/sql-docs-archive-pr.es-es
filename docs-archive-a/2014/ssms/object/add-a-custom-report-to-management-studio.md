---
title: Agregar un informe personalizado a Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 3cf8d726-0a90-4f80-98d0-352a2a59be0f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 07263edfb9b255257e0c79733c2c34b279b61cd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661783"
---
# <a name="add-a-custom-report-to-management-studio"></a>agregar un informe personalizado a Management Studio
  En este tema se describe cómo se crea un informe sencillo de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] que se guarda como archivo .rdl y, a continuación, cómo se agrega dicho archivo a [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] como informe personalizado. [!INCLUDE[ssRS](../../includes/ssrs.md)] puede crear una gran variedad de informes complejos. Para crear un informe siguiendo las instrucciones de este tema, debe tener instalado [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] en el equipo. No es necesario instalar [!INCLUDE[ssRS](../../includes/ssrs.md)] en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para ejecutar un informe personalizado mediante [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
  
### <a name="to-create-a-simple-report-saved-as-an-rdl-file"></a>Para crear un informe simple guardado como un archivo .rdl  
  
1.  Haga clic en **Inicio**, seleccione **Programas**, **Microsoft SQL Server**y, luego, haga clic en **SQL Server Data Tools**.  
  
2.  En el menú **Archivo** , seleccione **Nuevo**y haga clic en **Proyecto**.  
  
3.  En la lista **Tipos de proyecto** , haga clic en **Proyectos de Business Intelligence**.  
  
4.  En la lista **Plantillas** , haga clic en **Asistente de proyectos de servidor de informes**.  
  
5.  En **Nombre**, escriba **ConnectionsReport**y, a continuación, haga clic en **Aceptar**.  
  
6.  En la página de introducción del **Asistente para informes** , haga clic en **Siguiente**.  
  
7.  En la página **Seleccionar el origen de datos** , en el cuadro Nombre, escriba un nombre para esta conexión a [!INCLUDE[ssDE](../../includes/ssde-md.md)]y, a continuación, haga clic en **Editar**.  
  
8.  En el cuadro de diálogo **Propiedades de conexión** , en el cuadro **Nombre del servidor** , escriba el nombre de la instancia de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
9. En el cuadro **Seleccione o escriba un nombre de base de datos** , escriba el nombre de cualquier base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], como [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], y haga clic en **Aceptar**.  
  
10. En la página **Seleccionar el origen de datos** , haga clic en **Siguiente**.  
  
11. En la página **Diseñar la consulta** , en el cuadro **Cadena de consulta** , escriba la siguiente instrucción [!INCLUDE[tsql](../../includes/tsql-md.md)] que muestra las conexiones actuales a [!INCLUDE[ssDE](../../includes/ssde-md.md)]y, a continuación, haga clic en **Siguiente**. El cuadro Cadena de consulta del Asistente para informes no aceptará parámetros de informe. Los informes personalizados más complejos deben crearse manualmente.  
  
     `SELECT session_id, net_transport FROM sys.dm_exec_connections;`  
  
12. En la página **Seleccionar el tipo de informe** , seleccione **Tabular**y, a continuación, haga clic en **Finalizar**.  
  
13. En la página **Finalización del asistente** , en el cuadro **Nombre del informe** , escriba **ConnectionsReport**y, a continuación, haga clic en **Finalizar** para crear y guardar el informe.  
  
14. Cierre [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
15. Copie **ConnectionsReport.rdl** en una carpeta que haya creado en el servidor de bases de datos para los informes personalizados.  
  
### <a name="to-add-a-report-to-management-studio"></a>Para agregar un informe a Management Studio  
  
-   En [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], haga clic con el botón derecho en un nodo del Explorador de objetos, seleccione **Informes**y haga clic en **Informes personalizados**. En el cuadro de diálogo **Abrir archivo** , busque la carpeta de informes personalizados, seleccione el archivo **ConnectionsReport.rdl** y, a continuación, haga clic en **Abrir**.  
  
     La primera vez que se abre un nuevo informe personalizado desde un nodo del Explorador de objetos, el informe personalizado se agrega a la lista de **Informes personalizados** usados más recientemente en el menú contextual de dicho nodo. Al abrir un informe estándar por primera vez, aparece además en la lista de informes usados más recientemente en **Informes personalizados**. Si se elimina un archivo de informe personalizado, la próxima vez que se seleccione el elemento aparecerá un mensaje que le indicará que elimine el elemento de la lista de informes usados más recientemente.  
  
    1.  Para cambiar el número de archivos que se muestran en esta lista, en el menú **Herramientas** , haga clic en **Opciones** , expanda la carpeta **Entorno** y, a continuación, haga clic en **General**.  
  
    2.  Ajuste el número de **Mostrar archivos de la lista de archivos recientes**.  
  
## <a name="see-also"></a>Consulte también  
 [Informes personalizados en Management Studio](custom-reports-in-management-studio.md)   
 [Usar informes personalizados con propiedades de nodo de Explorador de objetos](use-custom-reports-with-object-explorer-node-properties.md)   
 [No suprimir advertencias de ejecutar informe personalizado](unsuppress-run-custom-report-warnings.md)   
 [Reporting Services &#40;SSRS&#41;](../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
