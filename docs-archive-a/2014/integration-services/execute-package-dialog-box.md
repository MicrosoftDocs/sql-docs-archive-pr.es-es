---
title: Cuadro de diálogo Ejecutar paquete | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.ispackageexecute.f1
- sql12.ssis.ssms.executepackage.f1
ms.assetid: 4f7a806d-4867-4d1f-bc65-b00c1caee7b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1b60381054c781cd59f0a9d434710663b72d616c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673793"
---
# <a name="execute-package-dialog-box"></a>Execute Package Dialog Box
  Use el cuadro de diálogo **Ejecutar paquete** para ejecutar un paquete que está almacenado en el servidor de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
 Un paquete de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] puede contener parámetros que hagan referencia a valores almacenados en variables de entorno. Antes de ejecutar este tipo de paquete, debe especificar qué referencia del entorno se utilizará para proporcionar los valores de la variable de entorno. Un proyecto puede contener varios entornos, pero se puede utilizar solo un entorno para enlazar los valores de variable de entorno en el momento de la ejecución. Si no se usan variables de entorno en el paquete, no se requiere un entorno.  
  
 ¿Qué desea hacer?  
  
-   [Abrir el cuadro de diálogo Ejecutar paquete](#open_dialog)  
  
-   [Establecer las opciones de la página General](#general)  
  
-   [Establecer las opciones de la pestaña Parámetros](#parameters)  
  
-   [Establecer las opciones de la pestaña Administradores de conexiones](#connection)  
  
-   [Establecer las opciones de la pestaña Avanzadas](#advanced)  
  
-   [Scripting de las opciones del cuadro de diálogo Ejecutar paquete](#script)  
  
##  <a name="open-the-execute-package-dialog-box"></a><a name="open_dialog"></a> Abrir el cuadro de diálogo Ejecutar paquete  
  
1.  En [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], conéctese al servidor de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
     Se conectará a la instancia del [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] que hospeda la base de datos SSISDB.  
  
2.  En el Explorador de objetos, expanda el árbol para que se muestre el nodo **Catálogos de Integration Services** .  
  
3.  Expanda el nodo **SSISDB** .  
  
4.  Expanda la carpeta que contiene el paquete que desea ejecutar.  
  
5.  Haga clic con el botón derecho en el paquete y, después, haga clic en **Ejecutar**.  
  
##  <a name="set-the-options-on-the-general-page"></a><a name="general"></a> Establecer las opciones de la página General  
 Seleccione **Entorno** para especificar el entorno que se aplica cuando se ejecuta el paquete.  
  
##  <a name="set-the-options-on-the-parameters-tab"></a><a name="parameters"></a> Establecer las opciones de la pestaña Parámetros  
 Utilice la pestaña **Parámetros** para modificar los valores de parámetro que se utilizan cuando se ejecuta el paquete.  
  
##  <a name="set-the-options-on-the-connection-managers-tab"></a><a name="connection"></a> Establecer las opciones de la pestaña Administradores de conexiones  
 Utilice la pestaña Administradores de conexiones para establecer las propiedades de los administradores de conexiones del paquete.  
  
##  <a name="set-the-options-on-the-advanced-tab"></a><a name="advanced"></a> Establecer las opciones de la pestaña Avanzadas  
 Utilice la pestaña Avanzadas para administrar propiedades y otra configuración del paquete.  
  
 **Agregar**, **Editar**, **Quitar**  
 Haga clic para agregar, editar o quitar una propiedad.  
  
 **Nivel de registro**  
 Seleccione el nivel de registro de la ejecución del paquete. Para más información, vea [catalog.set_execution_parameter_value &#40;base de datos de SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database).  
  
 **Volcado de errores**  
 Especifique si se crea un archivo de volcado cuando se producen errores durante la ejecución del paquete. Para obtener más información, consulte [Generating Dump Files for Package Execution](troubleshooting/generating-dump-files-for-package-execution.md).  
  
 **Tiempo de ejecución de 32 bits**  
 Especifique que el paquete se ejecutará en un sistema de 32 bits.  
  
##  <a name="scripting-the-options-in-the-execute-package-dialog-box"></a><a name="script"></a> Scripting de las opciones del cuadro de diálogo Ejecutar paquete  
 Mientras está en el cuadro de diálogo **Ejecutar paquete** , también puede utilizar el botón **Script** de la barra de herramientas para escribir código de [!INCLUDE[tsql](../includes/tsql-md.md)] . El script generado realiza una llamada a los procedimientos almacenados [catalog.start_execution &#40;base de datos de SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) con las mismas opciones que ha seleccionado en el cuadro de diálogo **Ejecutar paquete**. El script aparece en una nueva ventana de script en [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
  
