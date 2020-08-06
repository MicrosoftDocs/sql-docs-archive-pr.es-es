---
title: 'Paso 1: Crear un nuevo proyecto de Integration Services | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f14521b5-941e-443b-8f5e-385f98e37fbf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d6d16d7febcdecb01eb7a93167c2a18d225a9c2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673141"
---
# <a name="step-1-creating-a-new-integration-services-project"></a>Paso 1: Creación de un proyecto de Integration Services
  El primer paso al crear un paquete en [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] es crear un proyecto [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . En este proyecto, se incluyen las plantillas de los objetos (orígenes de datos, vistas de orígenes de datos y paquetes) que se usan en una solución de transformación de datos.  
  
 Los paquetes que creará en este tutorial de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] interpretan los valores de los datos dependientes de la configuración regional. Si no tiene configurado el equipo para usar la opción de configuración regional Inglés (Estados Unidos), debe establecer propiedades adicionales en el paquete. Los paquetes utilizados en las lecciones 2 a 5 se copian del paquete creado en la lección 1, y no necesita actualizar las propiedades dependientes de la configuración regional en los paquetes copiados.  
  
> [!NOTE]  
>  Este tutorial necesita Microsoft SQL Server Data Tools.  
>   
>  Para obtener más información sobre cómo instalar SQL Server Data Tools, consulte [Descargar SQL Server Data Tools](https://msdn.microsoft.com/data/hh297027).  
  
### <a name="to-create-a-new-integration-services-project"></a>Para crear un proyecto de Integration Services  
  
1.  En el menú **Inicio** , elija **Todos los programas**, **Microsoft SQL Server**y, a continuación, haga clic en **SQL Server Data Tools**.  
  
2.  En el menú **Archivo** , seleccione **Nuevo**y haga clic en **Proyecto** para crear un proyecto de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
3.  En el cuadro de diálogo **Nuevo proyecto** , expanda el nodo **Business Intelligence** bajo **Plantillas instaladas**y seleccione **Proyecto de Integration Services** en el panel **Plantillas** .  
  
4.  En el cuadro **Nombre** , cambie el nombre predeterminado por **SSIS Tutorial**. Opcionalmente, desactive la casilla **Crear directorio para la solución** .  
  
5.  Acepte la ubicación predeterminada o haga clic en **Examinar** para desplazarse a la carpeta que desee utilizar. En el cuadro de diálogo **Ubicación del proyecto** , haga clic en la carpeta y, a continuación, haga clic en **Seleccionar carpeta**.  
  
6.  Haga clic en **OK**.  
  
     De forma predeterminada, se creará un paquete vacío, denominado **Package.dtsx**, que se agregará al proyecto bajo Paquetes SSIS.  
  
7.  En la barra de herramientas del **Explorador de soluciones** , haga clic con el botón derecho en **Package.dtsx**, haga clic en **Cambiar nombre**y cambie el nombre del paquete predeterminado por **Lesson 1.dtsx**.  
  
## <a name="next-task-in-lesson"></a>Siguiente tarea de la lección  
 [Paso 2: Adición y configuración de un administrador de conexiones de archivos planos](lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
  
