---
title: Conectar con el Explorador de objetos y Servidores registrados | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: d6b3911f-68b4-4483-831b-df89d6400add
author: stevestein
ms.author: sstein
ms.openlocfilehash: b4bc75ad7f3682765dc102064a5621cd541ccd12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743869"
---
# <a name="connect-with-registered-servers-and-object-explorer"></a>Conectar con el Explorador de objetos y Servidores registrados
  Este tutorial muestra el uso de Servidores registrados y del Explorador de objetos.  
  
 En este tutorial se usa la base de datos [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Con el objeto de mejorar la seguridad, las bases de datos de ejemplo no se instalan de forma predeterminada. Para obtener más información, vea la página sobre [cómo instalar ejemplos y bases de datos de ejemplo de SQL Server](http://sqlserversamples.codeplex.com).  
  
## <a name="connecting-to-servers"></a>Conectar con servidores  
 La barra de herramientas del componente Servidores registrados contiene botones para [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]e [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Puede registrar uno o más de estos tipos de servidor para una administración práctica. Realice el siguiente ejercicio para registrar la base de datos [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
#### <a name="to-register-the-database"></a>Para registrar la base de datos  
  
1.  En la barra de herramientas de Servidores registrados, haga clic en **Motor de base de datos** , si es necesario. Es posible que ya esté seleccionado.  
  
2.  Expanda **Motor de base de datos**.  
  
3.  Haga clic con el botón secundario en **Grupos de servidores locales**y, después, haga clic en **Nuevo registro de servidor**.  
  
4.  En el cuadro de diálogo **Nuevo registro de servidor** , en el cuadro de texto **Nombre del servidor** , escriba el nombre de la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
5.  En el cuadro **Nombre del servidor registrado** , escriba [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
6.  En la pestaña **propiedades de conexión** , en la lista **conectar con base de datos** , seleccione **\<Browse server...>** .  
  
7.  En el cuadro de diálogo **Buscar bases de datos** , haga clic en **Sí**.  
  
8.  En el cuadro de diálogo **Buscar base de datos en el servidor** , seleccione [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]y, a continuación, haga clic en **Aceptar**.  
  
9. Para comprobar que el servidor se ha registrado correctamente, haga clic en **Probar**.  
  
10. En el cuadro de diálogo **Nuevo registro de servidor** , haga clic en **Guardar**.  
  
## <a name="connecting-with-object-explorer"></a>Conectar con el Explorador de objetos  
 Al igual que Servidores registrados, el Explorador de objetos puede conectarse a [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]y [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
#### <a name="to-connect-with-object-explorer"></a>Para conectar con el Explorador de objetos  
  
1.  En la barra de herramientas del Explorador de objetos, haga clic en **Conectar** para obtener la lista de tipos de conexión posibles y, a continuación, seleccione **Motor de base de datos**.  
  
2.  En el cuadro de diálogo **Conectar al servidor** , en el cuadro de texto **Nombre del servidor** , escriba el nombre de la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3.  Haga clic en **Opciones** para explorar las opciones elegidas.  
  
4.  Para conectar con el servidor, haga clic en **Conectar**. Si ya estaba conectado, volverá al Explorador de objetos y el foco se establecerá en ese servidor.  
  
     El Explorador de objetos permite administrar la seguridad de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , la replicación y el correo electrónico de base de datos. El Explorador de objetos solamente puede administrar algunas características de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]y [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Cada uno de estos componentes cuenta con herramientas especializadas adicionales.  
  
5.  En el Explorador de objetos, expanda la carpeta **Bases de datos** y seleccione [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
     Observe que [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] incluye las bases de datos del sistema en una carpeta separada.  
  
## <a name="next-task-in-lesson"></a>Siguiente tarea de la lección  
 [Cambiar el diseño del entorno](lesson-1-3-change-the-environment-layout.md)  
  
  
