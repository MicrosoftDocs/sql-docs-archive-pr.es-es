---
title: 'Lección 3: agregar registro | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 64cd24cc-ba8e-4bd7-b10b-6b80d8b04af6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 58fcc29759f19ad215a76a1b9ed9bf313b4c869c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672174"
---
# <a name="lesson-3-adding-logging"></a>Lección 3: Adición de registro
  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] incluye características de registro que permiten supervisar y solucionar los problemas de ejecución de paquetes mediante el seguimiento de eventos de tarea y de contenedor. La características de registro son flexibles, pueden habilitarse en el nivel de paquete o en tareas y contendores individuales del paquete. Puede seleccionar qué eventos deben registrarse y crear varios registros para un único paquete.  
  
 El registro lo proporciona un proveedor de registro. Cada proveedor de registro puede escribir información de registro en distintos formatos y tipos de destino. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] proporciona los siguientes proveedores de registro:  
  
-   Archivo de texto  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]  
  
-   Registro de eventos de Windows  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   Archivo XML  
  
 En esta lección, creará una copia del paquete que creó en la [Lección 2: agregar bucles](lesson-2-adding-looping-with-ssis.md). Utilizando este nuevo paquete, luego agregará y configurará el registro para supervisar eventos específicos durante la ejecución del paquete. Si no ha finalizado cualquiera de las lecciones anteriores, también puede copiar el paquete de la lección 2 finalizada incluido en el tutorial.  
  
> [!IMPORTANT]  
>  Para este tutorial, se necesita la base de datos de ejemplo **AdventureWorksDW2012** . Para obtener más información sobre cómo instalar e implementar **AdventureWorksDW2012**, [Reporting Services ejemplos de productos en github](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).  
  
## <a name="lesson-tasks"></a>Tareas de la lección  
 Esta lección contiene las siguientes tareas:  
  
-   [Paso 1: Copia del paquete de la lección 2](lesson-3-1-copying-the-lesson-2-package.md)  
  
-   [Paso 2: Adición y configuración de registro](lesson-3-2-adding-and-configuring-logging.md)  
  
-   [Paso 3: Prueba del paquete del tutorial de la lección 3](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Iniciar la lección  
 [Paso 1: Copia del paquete de la lección 2](lesson-3-1-copying-the-lesson-2-package.md)  
  
  
