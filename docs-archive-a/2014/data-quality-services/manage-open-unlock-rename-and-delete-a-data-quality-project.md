---
title: Administrar (abrir, desbloquear, cambiar el nombre y eliminar) un proyecto de calidad de datos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dqproject.opendqproject.f1
helpviewer_keywords:
- data quality project,delete
- data quality project,rename
- data quality project,unlock
- data quality project,open
ms.assetid: de8a2b04-4673-4beb-b4cf-96a28cdf3a93
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 216c95937676954c509890b879abdee8f55b778c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676668"
---
# <a name="manage-open-unlock-rename-and-delete-a-data-quality-project"></a>Administrar (abrir, desbloquear, cambiar nombre y eliminar) un proyecto de calidad de los datos
  En este tema se describe cómo administrar un proyecto de calidad de datos mediante [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , realizando acciones tales como abrirlo, desbloquearlo, cambiarle el nombre y eliminarlo.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Limitaciones y restricciones  
  
-   No es posible abrir un proyecto bloqueado creado por otro usuario.  
  
-   No se puede desbloquear ni eliminar un proyecto de calidad de datos creado por otro usuario, ni tampoco cambiarle el nombre.  
  
-   No es posible eliminar un proyecto de calidad de datos bloqueado. Para poder eliminarlo, primero debe desbloquearlo.  
  
-   Solo se podrán desbloquear los proyectos de calidad de datos creados por uno mismo.  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Requisitos previos  
 Debe disponer al menos de un proyecto de calidad de datos que administrar.  
  
###  <a name="security"></a><a name="Security"></a> Seguridad  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permisos  
 Debe disponer del rol dqs_kb_editor o dqs_kb_operator en la base de datos DQS_MAIN para administrar un proyecto de calidad de datos.  
  
##  <a name="open-a-data-quality-project"></a><a name="Open"></a> Abrir un proyecto de calidad de datos  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Ejecute la aplicación Data Quality Client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  En la [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] pantalla principal, haga clic en **Abrir proyecto de calidad de datos**. Aparece la pantalla **Abrir proyecto** .  
  
     O bien, puede abrir directamente uno de los proyectos de calidad de datos mostrados en el área **Proyecto de calidad de datos reciente** haciendo clic en él.  
  
3.  En la pantalla **Abrir proyecto** , haga clic para seleccionar el proyecto de calidad de datos que desea abrir y, a continuación, haga clic en **Siguiente**.  
  
4.  El proyecto de calidad de datos se abre en el mismo estado de la actividad en que se cerró por última vez. Un proyecto de calidad de datos tiene los estados siguientes:  
  
    -   En la actividad **limpieza** , un proyecto de calidad de datos puede tener los Estados siguientes: **limpieza: asignar**, **limpieza: limpiar**, **limpieza: administrar y ver resultados**y **limpieza-exportar**.  
  
    -   En el caso de la actividad de **búsqueda de coincidencias** , un proyecto de calidad de datos puede tener los siguientes Estados: **coincidencia de asignación** **, coincidencia de coincidencia**, **permanencia de coincidencia**y **búsqueda de coincidencias**.  
  
##  <a name="unlock-a-data-quality-project"></a><a name="Unlock"></a> Desbloquear un proyecto de calidad de datos  
 Cuando se crea un proyecto de calidad de datos, queda bloqueado para evitar su uso o modificación por parte de otros usuarios. Si desea que otros usuarios puedan trabajar en el proyecto de calidad de datos, deberá desbloquearlo después de finalizar su trabajo. Para los proyectos que están bloqueados se muestra un símbolo con un candado.  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Ejecute la aplicación Data Quality Client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  En la [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] pantalla principal, haga clic en **Abrir proyecto de calidad de datos**. Aparece la pantalla **Abrir proyecto** .  
  
3.  En la pantalla **Abrir proyecto** , haga clic con el botón secundario en un proyecto de calidad de datos bloqueado que haya creado y, a continuación, haga clic en **Desbloquear** en el menú contextual. Se muestra una marca de verificación verde que indicará que el proyecto está desbloqueado.  
  
##  <a name="rename-a-data-quality-project"></a><a name="Rename"></a> Cambiar el nombre de un proyecto de calidad de datos  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Ejecute la aplicación Data Quality Client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  En la [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] pantalla principal, haga clic en **Abrir proyecto de calidad de datos**. Aparece la pantalla **Abrir proyecto** .  
  
3.  En la pantalla **Abrir proyecto** , haga clic con el botón secundario en un proyecto de calidad de datos que haya creado y, a continuación, haga clic en **Cambiar nombre** en el menú contextual.  
  
4.  Podrá editar el nombre del proyecto de calidad de datos en la columna **Nombre** . Escriba un nuevo nombre y presione Entrar.  
  
##  <a name="delete-a-data-quality-project"></a><a name="Delete"></a> Eliminar un proyecto de calidad de datos  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Ejecute la aplicación Data Quality Client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  En la [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] pantalla principal, haga clic en **Abrir proyecto de calidad de datos**. Aparece la pantalla **Abrir proyecto** .  
  
3.  En la pantalla **Abrir proyecto** , haga clic con el botón secundario en un proyecto de calidad de datos desbloqueado que haya creado y, a continuación, haga clic en **Eliminar** en el menú contextual.  
  
4.  Aparece un mensaje de confirmación. Haga clic en **Sí**.  
  
  
