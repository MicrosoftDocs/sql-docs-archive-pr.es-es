---
title: Desinstalar la versión independiente de Generador de informes (Generador de informes) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 009538c6-4941-4393-b14b-9144cffdbdaf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cda13248d1aa14ee3d57a951872d3ad8ded17da9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87675737"
---
# <a name="uninstall-the-stand-alone-version-of-report-builder-report-builder"></a>Desinstalar la versión independiente del Generador de informes (Generador de informes)
  Podrá desinstalar la versión independiente del Generador de informes desde el panel de control o la línea de comandos. No podrá desinstalar la versión [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] del Generador de informes sin desinstalar [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]  
  
 La desinstalación del Generador de informes desde la línea de comandos utiliza una sintaxis que es idéntica a la que se utiliza para instalar el Generador de informes, excepto en que se usa la opción /x en lugar de la opción /i. Las líneas de comandos para desinstalar también pueden incluir la opción /quiet y otras opciones estándar. Si se ha quitado el paquete de Windows Installer para el Generador de informes (ReportBuilder3_x86.msi), no podrá utilizar con facilidad la línea de comandos para desinstalar el Generador de informes. Para obtener información acerca de cómo quitar el Generador de informes utilizando su GUID, consulte la documentación del programa msiexec en la biblioteca de MDSN.  
  
 Si las carpetas utilizadas por el Generador de informes incluyen archivos personalizados, las carpetas y archivos se conservan cuando se quita el Generador de informes. Solamente se quitan los archivos del Generador de informes.  
  
### <a name="to-uninstall-report-builder-from-the-control-panel"></a>Para desinstalar el Generador de informes desde el panel de control  
  
1.  En el menú **Inicio** , haga clic en **Panel de control**.  
  
2.  En el Panel de control, haga clic en **Programas y características**.  
  
3.  Busque Generador de informes de  en la lista Nombre y haga clic en él.  
  
4.  Haga clic en **Desinstalar**.  
  
5.  Si se le solicita que confirme la desinstalación del Generador de informes, haga clic en **Sí**.  
  
### <a name="to-uninstall-report-builder-from-the-command-line"></a>Para desinstalar el Generador de informes desde la línea de comandos  
  
1.  En el menú **Inicio** , haga clic en **Ejecutar**.  
  
2.  En el cuadro de texto **abrir** , escriba`cmd.`  
  
3.  En la ventana del símbolo del sistema, navegue hasta la carpeta con ReportBuilder3_x86.msi.  
  
4.  Escriba una línea de comandos básica similar a esta:  
  
 `msiexec /x ReportBuilder3_x86.msi /quiet /l*v install.log`  
  
 Si puede, utilice una línea de comandos como la siguiente para incluir el registro:  
  
 `msiexec /x ReportBuilder3_x86.msi /quiet /l*v c:\junk\install.log`  
  
1.  Presione **ENTRAR**.  
  
## <a name="see-also"></a>Consulte también  
 [Instalación, desinstalación y compatibilidad Generador de informes](../install-uninstall-and-report-builder-support.md)   
 [Instale la versión independiente de Generador de informes &#40;Generador de informes&#41;](install-report-builder.md)  
  
  
