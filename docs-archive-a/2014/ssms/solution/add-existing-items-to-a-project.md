---
title: Agregar elementos existentes a un proyecto | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], item additions
- adding project items
ms.assetid: 084b3879-e96b-45a7-b421-6a4b0db2b92b
author: stevestein
ms.author: sstein
ms.openlocfilehash: cffa683bfa2a2c81c059d887231531f03d5c892b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87677324"
---
# <a name="add-existing-items-to-a-project"></a>Agregar elementos existentes a un proyecto
  Agregue elementos nuevos a un proyecto para ampliar la funcionalidad de la aplicación. Un elemento existente puede ser una consulta o un archivo del tipo varios. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] tiene dos tipos de proyectos: proyecto de script de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y proyecto de script de Analysis Services. El tipo de proyecto determina los archivos de consulta que se pueden agregar al proyecto. Por ejemplo, se puede agregar una consulta [!INCLUDE[tsql](../../includes/tsql-md.md)] (un archivo con una extensión .sql) a un proyecto de script de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , pero no a un proyecto de script de Analysis Services. Para asociar extensiones de archivo adicionales a un tipo de proyecto, vea [asociar extensiones de archivo a un editor de código](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md).  
  
### <a name="to-add-an-existing-query-or-a-miscellaneous-file-to-a-project"></a>Para agregar una consulta existente o un archivo del tipo archivos varios a un proyecto  
  
1.  En el Explorador de soluciones, seleccione el proyecto de destino.  
  
2.  En el menú **Proyecto** , haga clic en **Agregar elemento existente**.  
  
     **Look in**  
     Busque en esta lista los archivos o las carpetas que se agregarán al proyecto. En el caso de servicios web XML y aplicaciones Web ASP.NET, los archivos se encuentran en el servidor web.  
  
     **Escritorio**  
     Muestra los archivos y las carpetas del escritorio.  
  
     **Mis proyectos**  
     Muestra los archivos y las carpetas de la ubicación predeterminada **Mis proyectos** .  
  
     **Mi PC**  
     Muestra el contenido de la carpeta **Mi PC** .  
  
     **Nombre de archivo**  
     Utilice esta opción para filtrar los archivos y las carpetas mostrados. Especifique el nombre de archivo completo o parcial que se filtrará, utilice un asterisco (`*`) como comodín.  
  
    > [!NOTE]  
    >  Navegue a las ubicaciones web o de red especificando la dirección URL o la ruta de red en el cuadro **Nombre de archivo** . Por ejemplo, **http://mywebsite** muestra los archivos disponibles en la ubicación web miSitioWeb y **\\\miServidor\miRecursoCompartido** muestra los archivos disponibles en la ubicación miRecursoCompartido en miServidor.  
  
     **Archivos de tipo**  
     Utilice esta opción para filtrar archivos según la extensión de archivo. Cada producto muestra los filtros predeterminados de los tipos de archivo más comunes.  
  
     **Add (Agregar)**  
     Utilice este botón desplegable para agregar el elemento al proyecto y abrirlo en el editor predeterminado.  
  
    -   **Add (Agregar)**  
  
         Copia el elemento existente en la carpeta de proyecto del disco y agrega el elemento del proyecto seleccionado en el Explorador de soluciones. Los cambios realizados en el elemento no se reflejarán en el elemento de la ubicación original. Es el editor predeterminado para el tipo de archivo.  
  
    -   **Agregar como vínculo**  
  
         Agrega el archivo seleccionado al proyecto y lo abre con el editor predeterminado para el tipo de archivo. Con esta opción se abre el archivo seleccionado inicialmente y no se copia en la carpeta del proyecto.  
  
3.  Si va a agregar archivos de consulta, el cuadro de diálogo de conexión le pedirá que especifique una conexión para la consulta. Si no desea asociar una conexión a la consulta, puede hacer clic en **Cancelar** en el cuadro de diálogo de conexión.  
  
4.  El archivo se agregará a la carpeta **Consultas** o **Archivos varios** del proyecto.  
  
## <a name="see-also"></a>Consulte también  
 [Explorador de soluciones](solution-explorer.md)   
 [Agregar nuevos elementos a un proyecto](add-new-items-to-a-project.md)   
 [Quitar o eliminar un elemento o un proyecto](remove-or-delete-an-item-or-project.md)  
  
  
