---
title: Herramientas de configuración de PowerPivot | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f934c51d-01fe-4e67-971d-cd87d7d7ee51
author: minewiskan
ms.author: owend
ms.openlocfilehash: de11cdaf304b3010dcf21725edd2d3cbfa84ae0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676195"
---
# <a name="powerpivot-configuration-tools"></a>PowerPivot Configuration Tools
  Configure, repare o quite un [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] con la herramientas de configuración de PowerPivot.

 El Asistente para la instalación de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] instala la Herramienta de configuración de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint 2010 y una Herramienta de configuración de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint 2013. En este tema se describe el uso general de las dos herramientas y las diferencias existentes entre ellas.

 **[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 | SharePoint 2010

 **En este tema:**

-   [Requisitos para usar las herramientas de configuración](#bkmk_requirements)

-   [Dos versiones de la herramienta de configuración](#bkmk_twoversions)

-   [Información general sobre el uso de herramienta de configuración de PowerPivot](#bkmk_overview)

-   [Iniciar una de las herramientas de configuración de PowerPivot](#bmkm_start_tool)

##  <a name="requirements-for-using-the-configuration-tools"></a><a name="bkmk_requirements"></a>Requisitos para usar el Herramientas de configuración

-   Debe ser un administrador de la granja de servidores.

-   Debe ser administrador del servidor en la instancia de Analysis Services (solo SharePoint 2010).

-   Debe estar db_owner en la base de datos de configuración de la granja.

-   No existen requisitos de puertos TCP/IP para utilizar las herramientas de configuración y, por consiguiente, no debería tener que configurar el firewall para acomodar las herramientas de configuración. La herramienta de configuración espera que las aplicaciones Web y los servicios compartidos estén disponibles como parte de la plataforma de SharePoint. Puede que tenga que configurar el firewall para el servidor de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Para obtener más información, consulte [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).

##  <a name="two-versions-of-the-configuration-tool"></a><a name="bkmk_twoversions"></a>Dos versiones de la herramienta de configuración
 El Asistente para la instalación de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] instala la herramienta de configuración de PowerPivot para SharePoint 2010 y una herramienta de configuración de PowerPivot para SharePoint 2013.

 Las herramientas solo se pueden usar con una instancia de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] o [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] de [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]. No las use con instalaciones de [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] .

|Nombre|Versión admitida de SharePoint|Configuración detallada|
|----------|-------------------------------------|----------------------------|
|Configuración de PowerPivot para SharePoint 2013|SharePoint 2013|[Configurar o reparar 2013 PowerPivot para SharePoint &#40;herramienta de configuración de PowerPivot&#41;](configure-or-repair-power-pivot-for-sharepoint-2013.md)|
|Herramienta de configuración de PowerPivot|SharePoint 2010 con SharePoint 2010|[Configurar o reparar 2010 PowerPivot para SharePoint &#40;herramienta de configuración de PowerPivot&#41;](../configure-repair-powerpivot-sharepoint-2010.md)|

###  <a name="how-the-two-configuration-tools-are-different"></a><a name="bkmk_sum_differences_betweentools"></a> En qué se diferencian las dos herramientas de configuración
 Las dos versiones de la herramienta de configuración son similares pero hay algunas diferencias en los pasos de configuración que ejecutan las dos herramientas. Las diferencias se deben a cambios entre SharePoint 2010 y SharePoint 2013, así como a las diferencias de arquitectura entre la versión de SQL Server 2012 SP1 de PowerPivot para SharePoint y las versiones anteriores de PowerPivot para SharePoint.

 En la tabla siguiente se describen las características nuevas y modificadas de la herramienta **Configuración de PowerPivot para SharePoint 2013** . En la tabla también se describen características de la **Herramienta de configuración de PowerPivot** que no están incluidas en la herramienta de configuración de PowerPivot para SharePoint 2013. Las filas de la tabla están en el mismo orden que las pestañas de las herramientas de configuración.

|Configuración de PowerPivot para SharePoint 2013|Herramienta de configuración de PowerPivot|
|--------------------------------------------------|-----------------------------------|
|La página principal tiene una nueva opción para **Servidor PowerPivot para Excel Services**. La opción admite la nueva arquitectura con [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] que se ejecuta fuera de la granja de SharePoint. Configure Excel Services para usar uno o más servidores de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] que se ejecutan en modo de SharePoint.<br /><br /> ![Servidor PowerPivot en la nueva herramienta de configuración](../media/as-powerpivot-configtool-differences-new-mainpage.gif "Servidor PowerPivot en la nueva herramienta de configuración")||
||La herramienta de 2010 incluye la página **Registrar SQL Server Analysis Services (PowerPivot) en el servidor local** para configurar una instancia local de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Esta página no forma parte de la herramienta de 2013 porque no hay ninguna instancia local de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].<br /><br /> ![Cuenta de servicio AS en la anterior herramienta de configuración](../media/as-powerpivot-configtool-differences-old-register-as-localserver.gif "Cuenta de servicio AS en la anterior herramienta de configuración")|
||La página **Crear una aplicación de servicio PowerPivot** tiene una opción adicional **Actualizar libros antes de habilitar la actualización de datos**. Esta opción no está disponible en la herramienta de 2013.<br /><br /> ![Actualizar libros en la anterior herramienta de configuración](../media/as-powerpivot-configtool-differences-old-uprgadeworkbooks.gif "Actualizar libros en la anterior herramienta de configuración")|
|La herramienta de 2013 tiene una página nueva **Configurar servidores PowerPivot**. Esta página admite la nueva arquitectura de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] que se ejecuta fuera de la granja de servidores de SharePoint. De forma predeterminada, el nombre del servidor que se escribió en la página principal, en el cuadro de texto **Servidor PowerPivot para Excel Services**, también se muestra en **Configurar servidores PowerPivot**.<br /><br /> ![Registrar servidores PowerPivot en la nueva herramienta de configuración](../media/as-powerpivot-configtool-differences-new-powerpivot-servers.gif "Registrar servidores PowerPivot en la nueva herramienta de configuración")||
|La herramienta de 2013 tiene una nueva página **Registrar complemento PowerPivot como herramienta de seguimiento de uso de Excel Services**. Excel Services de SharePoint 2010 no hace un seguimiento de los datos de uso de PowerPivot.||
||La herramienta de 2010 incluye la página **Agregar MSOLAP.5 como proveedor de confianza** para registrar MSOLAP de forma que Excel Services en SharePoint 2010 pueda cargar modelos de PowerPivot. Esta página no forma parte de la herramienta de 2013. Excel Services de SharePoint 2013 no usa el proveedor MSOLAP para cargar modelos.|

##  <a name="overview-of-using-a-powerpivot-configuration-tool"></a><a name="bkmk_overview"></a>Información general sobre el uso de una herramienta de configuración de PowerPivot
 Cuando inicia una de las herramientas de configuración de PowerPivot, la herramienta evalúa la instalación existente para determinar qué operaciones son aplicables. En una instalación nueva, solo está disponible la tarea de configuración. Una vez configurado el servidor, aparece la tarea de quitar. Si empezó con una instancia de [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] , la actualización también se habilitará en la lista de tareas disponibles.

 Si no está familiarizado con Administración central o con Windows PowerShell, puede ejecutar la herramienta de configuración como alternativa a completar una instalación de [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] .

 Además, la herramienta puede detectar si la granja está configurada o faltan las características necesarias. Si los archivos de programa de SharePoint están instalados pero la granja no está configurada, la herramienta proporciona las acciones para configurar la granja y la instalación de [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] .

 Puede revisar la pestaña **Script** para aprender y entender cómo configurar PowerPivot y SharePoint mediante Windows PowerShell. Para obtener más información, vea lo siguiente:

-   [Configuración de PowerPivot mediante Windows PowerShell](power-pivot-configuration-using-windows-powershell.md)

-   [Referencia de PowerShell para PowerPivot para SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)

> [!NOTE]
>  La herramienta no configura Reporting Services. Si va a agregar Reporting Services a su entorno de SharePoint, necesita instalar y configurar Reporting Services por separado. Para obtener más información, vea lo siguiente:
> 
>  -   [Instale Reporting Services modo de SharePoint para sharepoint 2013](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md).
> -   [Instale Reporting Services modo de SharePoint para sharepoint 2010](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).

##  <a name="start-one-of-the-powerpivot-configuration-tools"></a><a name="bmkm_start_tool"></a>Iniciar una de las Herramientas de configuración de PowerPivot

1.  En la pantalla **Inicio** , escriba`powerpivot`

     En la pantalla **Inicio** , escriba `powerpivot` o en el menú **Inicio** , haga clic en todos los **programas**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] , haga clic en **herramientas de configuración**y, a continuación, haga clic en una de las opciones siguientes:

    -   **Herramienta de configuración de PowerPivot**.

    -   **OR**

    -   **Configuración de PowerPivot para SharePoint 2013**.

     ![Dos herramientas de configuración de PowerPivot](../media/as-powerpivot-configtools-bothicons.gif "Dos herramientas de configuración de PowerPivot")

     **Nota** : las herramientas solo están disponibles cuando [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] está instalado en el servidor local.

2.  Al iniciarse, las herramientas de configuración comprueban el estado de la instalación y proporcionan tareas que son válidas para la instalación.

3.  Según el estado actual de la instalación, se pueden realizar una o más de las tareas siguientes:

    1.  Haga clic en **Configurar o reparar PowerPivot para SharePoint** para completar las tareas posteriores a la instalación o reparar una instalación.

    2.  Haga clic en **Quitar características, servicios, aplicaciones y soluciones** para quitar características y soluciones de la granja.

    3.  Haga clic en **Actualizar características, servicios, aplicaciones y soluciones** para actualizar las características y las soluciones instaladas con una versión anterior de [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)].

     Por ejemplo, la imagen muestra la página de inicio de la herramienta de configuración de PowerPivot para SharePoint 2013.

     ![Herramienta de configuración de PowerPivot para SharePoint 2013](../media/ssas-powerpivot-configtool-4-sharepoint2013-choosemode.gif "Herramienta de configuración de PowerPivot para SharePoint 2013")

 Cada tarea se compone de acciones individuales que abordan algún aspecto de la configuración del servidor. Por ejemplo, la tarea de configuración incluye acciones para implementar soluciones, crear una aplicación de servicio PowerPivot, activar características y configurar la actualización de datos. La lista de acciones variará en función del estado actual de la instalación. Si una acción no es necesaria, la herramienta la excluye de la lista de tareas.

 Al hacer clic en ejecutar, la herramienta procesa todas las acciones por lotes. Aunque cada acción aparece como un elemento diferente en la lista de tareas, todas las acciones incluidas en la tarea se procesan juntas. Solo se procesan las acciones que superan una comprobación de validación. Puede que tenga que agregar o cambiar algunos de los valores de entrada para superar la comprobación de validación.

## <a name="related-content"></a>Contenido relacionado
 [Upgrade PowerPivot for SharePoint](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md) Describe el flujo de trabajo que actualiza una instalación existente que ya está en una granja.

 [Uninstall PowerPivot for SharePoint](../../sql-server/install/uninstall-power-pivot-for-sharepoint.md) Describe el flujo de trabajo que quita de una granja servicios, soluciones y páginas de aplicación de PowerPivot para SharePoint.

 [Configuración de PowerPivot mediante Windows PowerShell](power-pivot-configuration-using-windows-powershell.md)

 [Administración y configuración del servidor PowerPivot en Administración central](power-pivot-server-administration-and-configuration-in-central-administration.md)


