---
title: Implementar soluciones de PowerPivot en SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f202a2b7-34e0-43aa-90d5-c9a085a37c32
author: minewiskan
ms.author: owend
ms.openlocfilehash: 043647988598f932b70cc06e6bb5492d66864372
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87675007"
---
# <a name="deploy-powerpivot-solutions-to-sharepoint"></a>Implementar las soluciones de PowerPivot en SharePoint
  Use las instrucciones siguientes para implementar manualmente dos paquetes de soluciones que agregan características de PowerPivot a un entorno de SharePoint Server 2010. La implementación de soluciones es un paso necesario para configurar PowerPivot para SharePoint en un servidor SharePoint 2010. Para ver la lista completa de los pasos necesarios, consulte [Administración y configuración de servidores de PowerPivot en administración central](power-pivot-server-administration-and-configuration-in-central-administration.md).  
  
 O bien, puede usar la Herramienta de configuración de PowerPivot para implementar las soluciones. Usar la herramienta de configuración es más fácil y más eficiente para una única instalación de servidor, pero podría ser conveniente usar Administración central y PowerShell si prefiere usar una herramienta conocida o si va a configurar varias características al mismo tiempo. Para obtener más información acerca del uso de la herramienta de configuración, vea [PowerPivot herramientas de configuración](power-pivot-configuration-tools.md).  
  
 Antes de implementar las soluciones, primero debe instalar PowerPivot para SharePoint usando los medios de instalación de SQL Server 2012. El programa de instalación de SQL Server instala los paquetes de soluciones que está a punto de implementar.  
  
 Este tema contiene las siguientes secciones:  
  
 [Requisito previo: comprobar que la aplicación Web usa la autenticación de modo clásico](#bkmk_classic)  
  
 [Paso 1: implementar la solución de granja de servidores](#bkmk_farm)  
  
 [Pas 2: implementar la solución de aplicación web de PowerPivot para Administración central](#deployCA)  
  
 [Paso 3: implementar la solución de aplicación web de PowerPivot en otras aplicaciones web](#deployUI)  
  
 [Volver a implementar o retirar la solución](#retract)  
  
 [Acerca de las soluciones de PowerPivot](#intro)  
  
##  <a name="prerequisite-verify-the-web-application-uses-classic-mode-authentication"></a><a name="bkmk_classic"></a> Requisitos previos: compruebe que la aplicación web usa el Modo clásico de autenticación  
 PowerPivot para SharePoint solo se admite en las aplicaciones Web que usan el modo clásico de autenticación de Windows. Para comprobar si la aplicación usa el modo clásico, ejecute el siguiente cmdlet de PowerShell desde el **Shell de administración de sharepoint 2010**, reemplazando `http://<top-level site name>` por el nombre de su sitio de SharePoint:  
  
```powershell
Get-SPWebApplication http://<top-level site name> | Format-List UseClaimsAuthentication  
```  
  
 Se debería devolver el valor **false**. Si es **true**, no se puede tener acceso a los datos PowerPivot con esta aplicación Web.  
  
##  <a name="step-1-deploy-the-farm-solution"></a><a name="bkmk_farm"></a> Paso 1: implementar la solución de granja  
 En esta sección se muestra cómo implementar soluciones con PowerShell, pero también puede utilizar la Herramienta de configuración de PowerPivot para completar esta tarea. Para obtener más información, vea [configurar o reparar PowerPivot para SharePoint 2010 &#40;herramienta de configuración de PowerPivot&#41;](../configure-repair-powerpivot-sharepoint-2010.md).  
  
 Esta tarea solo tiene que realizarse una vez, después de instalar PowerPivot para SharePoint.  
  
1.  En un servidor que tenga una instalación de PowerPivot para SharePoint, abra un shell de administración de SharePoint 2010 con la opción **Ejecutar como administrador** .  
  
2.  Ejecute el siguiente cmdlet para agregar la solución de granja.  
  
    ```powershell
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotFarm.wsp"  
    ```  
  
     El cmdlet devuelve el nombre de la solución, su identificador de solución y Deployed=False. En el paso siguiente, implementará la solución.  
  
3.  Ejecute el siguiente cmdlet para implementar la solución de granja:  
  
    ```powershell
    Install-SPSolution -Identity PowerPivotFarm.wsp -GACDeployment -Force  
    ```  
  
##  <a name="step-2-deploy-the-powerpivot-web-application-solution-to-central-administration"></a><a name="deployCA"></a>Paso 2: implementar la solución de aplicación Web de PowerPivot para administración central  
 Después de implementar la solución de granja, debe implementar la solución de aplicación web para Administración central. Este paso agrega el Panel de administración de PowerPivot a Administración central.  
  
1.  Abra un shell de administración de SharePoint 2010 utilizando la opción **Ejecutar como administrador** .  
  
2.  Ejecute el siguiente cmdlet para crear una referencia a Administración central:  
  
    ```powershell
    $centralAdmin = $(Get-SPWebApplication -IncludeCentralAdministration | Where { $_.IsAdministrationWebApplication -eq $TRUE})  
    ```  
  
3.  Ejecute el siguiente cmdlet para agregar la solución de granja.  
  
    ```powershell
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotWebApp.wsp"  
    ```  
  
     El cmdlet devuelve el nombre de la solución, su identificador de solución y Deployed=False. En el paso siguiente, implementará la solución.  
  
4.  Ejecute el siguiente cmdlet para instalar la solución de aplicación web en Administración central.  
  
    ```powershell
    Install-SPSolution -Identity PowerPivotWebApp.wsp -GACDeployment -Force -WebApplication $centralAdmin  
    ```  
  
 Ahora que la solución de aplicación web se implementa en Administración central, puede usar Administración central para completar el resto de pasos de configuración.  
  
##  <a name="step-3-deploy-the-powerpivot-web-application-solution-to-other-web-applications"></a><a name="deployUI"></a>Paso 3: implementar la solución de aplicación Web de PowerPivot en otras aplicaciones Web  
 En la tarea anterior, implementó Powerpivotwebapp.wsp en Administración central. En esta sección, implementa powerpivotwebapp.wsp en cada una de las aplicaciones web existentes que admiten el acceso a datos PowerPivot. Si agrega más aplicaciones web más adelante, asegúrese de repetir este paso para esas aplicaciones web adicionales.  
  
1.  En Administración central, en Configuración del sistema, haga clic en **Administrar soluciones del conjunto de servidores**.  
  
2.  Haga clic en **powerpivotwebapp. wsp**.  
  
3.  Haga clic en **Implementar solución**.  
  
4.  En **¿cómo implementar en?**, seleccione la aplicación Web de SharePoint para la que desea agregar compatibilidad con las características de PowerPivot.  
  
5.  Haga clic en **OK**.  
  
6.  Repita el mismo proceso con las demás aplicaciones web de SharePoint que también admitirán el acceso a datos PowerPivot.  
  
##  <a name="redeploy-or-retract-the-solution"></a><a name="retract"></a> Volver a implementar o retirar la solución  
 Aunque Administración central de SharePoint proporciona la retirada de la solución, no necesita retirar el archivo powerpivotwebapp.wsp a menos que esté solucionando problemas de una instalación o de la implementación de una revisión.  
  
1.  En Administración central de SharePoint 2010, en Configuración del sistema, haga clic en **Administrar las soluciones de la granja**.  
  
2.  Haga clic en **Powerpivotwebapp.wsp**.  
  
3.  Haga clic en **Retirar solución**.  
  
 Si encuentra problemas en la implementación del servidor que se reenvían a la solución de granja de servidores, puede volver a implementarla ejecutando la opción **reparar** en la herramienta de configuración de PowerPivot. Las operaciones de reparación mediante la herramienta se prefieren porque requieren menos pasos por su parte. Para obtener más información, vea [configurar o reparar PowerPivot para SharePoint 2010 &#40;herramienta de configuración de PowerPivot&#41;](../configure-repair-powerpivot-sharepoint-2010.md).  
  
 Si aun así desea implementar de nuevo todas las soluciones, asegúrese de hacerlo en este orden:  
  
1.  Retirar la solución de aplicación web de PowerPivot de todas las aplicaciones web de SharePoint que la utilizan.  
  
2.  Retirar la solución de granja de PowerPivot.  
  
3.  Volver a implementar la solución de granja de PowerPivot.  
  
4.  Volver a implementar la solución de aplicación web de PowerPivot en todas las aplicaciones web de SharePoint.  
  
##  <a name="about-the-powerpivot-solutions"></a><a name="intro"></a>Acerca de las soluciones de PowerPivot  
 PowerPivot para SharePoint usa dos paquetes de soluciones para implementar sus páginas de aplicaciones y archivos de programas en la granja y en aplicaciones web individuales.  
  
-   La solución de granja es global. Se implementa una vez y después se convierte en disponible automáticamente para todos los servidores nuevos de PowerPivot para SharePoint que se agreguen posteriormente a la granja.  
  
-   La solución de aplicación Web es específica de la aplicación y se debe implementar en cada aplicación Web de la granja, incluida la aplicación Web Administración central.  
  
 Cada solución se implementa de forma diferente.  La solución de granja se implementa una vez, tras instalar la primera instancia de PowerPivot para SharePoint. Para implementar la solución de granja, use los cmdlets de PowerShell o la Herramienta de configuración de PowerPivot.  
  
 La solución de aplicación Web se implementa inicialmente en Administración central, seguida de las siguientes implementaciones de la solución en cualquier aplicación Web adicional que vaya a admitir solicitudes de los datos PowerPivot. Para implementar la solución de aplicación web de Administración central, debe usar el cmdlet de PowerShell o de la Herramienta de configuración de PowerPivot. Para todas las demás aplicaciones Web, puede implementar la solución de aplicación Web mediante Administración central o PowerShell.  
  
|Solución|Descripción|  
|--------------|-----------------|  
|Powerpivotfarm.wsp|Agrega los archivos Microsoft.AnalysisServices.SharePoint.Integration.dll al ensamblado global.<br /><br /> Agrega Microsoft.AnalysisServices.ChannelTransport.dll al ensamblado global.<br /><br /> Instala las características y los archivos de recursos, y registra los tipos de contenido.<br /><br /> Agrega plantillas de biblioteca para las bibliotecas Galería de PowerPivot y Fuentes de datos.<br /><br /> Agrega las páginas de aplicación para la configuración de aplicación de servicio, el panel de administración de PowerPivot, actualización de datos y la Galería de PowerPivot.|  
|powerpivotwebapp.wsp|Agrega los archivos de recursos Microsoft.AnalysisServices.SharePoint.Integration.dll a la carpeta de extensiones de servidor web del servidor front-end web.<br /><br /> Agrega el Servicio web PowerPivot al servidor front-end web.<br /><br /> Agrega la generación de imágenes en miniatura para la Galería de PowerPivot.|  
  
## <a name="see-also"></a>Consulte también  
 [PowerPivot para SharePoint de actualización](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)   
 [Administración y configuración del servidor de PowerPivot en administración central](power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [Configuración de PowerPivot mediante Windows PowerShell](power-pivot-configuration-using-windows-powershell.md)  
