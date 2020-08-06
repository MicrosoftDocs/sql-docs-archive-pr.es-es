---
title: Cuadro de diálogo de las propiedades de paquete | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.ispackageprop.general.f1
- sql12.ssis.ssms.packageproperties.f1
ms.assetid: a70acbf4-5f5c-4606-8ce4-8eb3684233de
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b386bf4e75ff784cd8d4a96363515786d242d2a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87671636"
---
# <a name="package-properties-dialog-box"></a>Propiedades del paquete, cuadro de diálogo
  Utilice el cuadro de diálogo **Propiedades del paquete** para ver las propiedades de los paquetes almacenados en el servidor de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Para obtener más información, vea [Paquetes de Integration Services &#40;SSIS&#41;](integration-services-ssis-server-and-catalog.md).  
  
 **¿Qué desea hacer?**  
  
-   [Abrir el cuadro de diálogo Propiedades del paquete](#open_dialog)  
  
-   [Configurar las opciones](#options)  
  
##  <a name="open-the-package-properties-dialog-box"></a><a name="open_dialog"></a> Abrir el cuadro de diálogo Propiedades del paquete  
  
1.  En [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], conéctese al servidor de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
     Se conectará a la instancia del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] que hospeda la base de datos SSISDB.  
  
2.  En el Explorador de objetos, expanda el árbol para que se muestre el nodo **Catálogos de Integration Services** .  
  
3.  Expanda el nodo **SSISDB** .  
  
4.  Expanda la carpeta que contiene el paquete para el que desea ver las propiedades.  
  
5.  Haga clic con el botón derecho en el paquete y, después, seleccione **Propiedades**.  
  
##  <a name="configure-the-options"></a><a name="options"></a> Configurar las opciones  
 Utilice la página **General** para ver las propiedades del paquete seleccionado.  
  
 Todas las propiedades que aparecen en la página **General** son de solo lectura.  
  
 **Nombre**  
 Muestra el nombre del paquete.  
  
 **Identificador**  
 Muestra el identificador del paquete.  
  
 **Punto de entrada**  
 El valor de `True` indica que el paquete se inicia directamente. El valor de `False` indica que el paquete debe iniciarse mediante otro paquete con la tarea Ejecutar paquete. El valor predeterminado es `True`.  
  
 Puede establecer esta propiedad en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] tanto para el paquete primario como para los paquetes secundarios. Para ello, haga clic con el botón derecho en el paquete en el Explorador de soluciones y, después, haga clic en **Paquete de punto de entrada**.  
  
 **Descripción**  
 Muestra la descripción opcional del paquete.  
  
  
