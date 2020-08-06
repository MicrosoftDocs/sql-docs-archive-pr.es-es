---
title: Editor de destino de archivos sin formato (página Administrador de conexiones) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfiledestinationconnectionmanager.f1
ms.assetid: a0ec9643-3b44-4467-b855-f45ae4794f7f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a693591921a5669eb9bc8160f0be076ab4d6869b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744754"
---
# <a name="raw-file-destination-editor-connection-manager-page"></a>Editor de destino de archivos sin formato (página Administrador de conexiones)
  Use el editor de destino de archivos sin formato para configurar el destino de archivo sin formato con el fin de escribir datos sin formato en un archivo.  
  
 **¿Qué desea hacer?**  
  
-   [Abrir el editor de destino de archivos sin formato](#open)  
  
-   [Establecer opciones en la pestaña administrador de conexiones](#connection)  
  
-   [Establecer las opciones de la pestaña Columnas](#mapping)  
  
##  <a name="open-the-raw-file-destination-editor"></a><a name="open"></a> Abra el editor de destino de archivos sin formato  
  
1.  Agregue el destino de archivo sin formato a un paquete de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , en [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
2.  Haga clic con el botón derecho en el componente y, después, haga clic en **Editar**.  
  
##  <a name="set-options-on-the-connection-manager-tab"></a><a name="connection"></a> Establecer opciones en la pestaña Administrador de conexiones  
 **Modo de acceso**  
 Seleccione cómo se especifica el nombre de archivo. Seleccione **Nombre de archivo** para escribir el nombre de archivo y la ruta de acceso directamente o **Nombre de archivo de la variable** para especificar una variable que contiene el nombre de archivo.  
  
 **Nombre de archivo** o **Nombre de variable**  
 Escriba el nombre y la ruta de acceso del archivo sin formato o seleccione la variable que contiene el nombre de archivo.  
  
 **Opción de escritura**  
 Seleccione el método que va a utilizar para crear y escribir en el archivo.  
  
 **Generar un archivo sin formato inicial**  
 Haga clic en el botón para generar un archivo sin formato vacío que contenga solo las columnas (solo archivos de metadatos), sin tener que ejecutar el paquete. El archivo contiene las columnas seleccionadas en la página **Columnas:** del **Editor de destino de archivos sin formato**. Puede designar el origen de archivo sin formato para este archivo que solo tiene metadatos.  
  
 Al hacer clic en **Generar archivo sin formato inicial**, aparece un cuadro de mensaje. Haga clic en **Aceptar** para continuar con la creación del archivo. Haga clic en **Cancelar** para seleccionar otra lista de columnas en la página **Columnas:** .  
  
##  <a name="set-options-on-the-columns-tab"></a><a name="mapping"></a>Establecer las opciones de la pestaña columnas  
 **Columnas de entrada disponibles**  
 Seleccione una o varias columnas de entrada para escribir en el archivo sin formato.  
  
 **Columna de entrada**  
 Una columna de entrada se agrega automáticamente a esta tabla cuando se selecciona en **Columnas de entrada disponibles**, o puede seleccionar la columna de entrada directamente en esta tabla.  
  
 **Alias de salida**  
 Especifique un nombre alternativo para usarlo en la columna de salida.  
  
## <a name="see-also"></a>Consulte también  
 [Destino de archivo sin formato](data-flow/raw-file-destination.md)  
  
  
