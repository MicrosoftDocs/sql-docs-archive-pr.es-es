---
title: 'Procedimientos: Depuración de ensamblados personalizados | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom assemblies [Reporting Services], debugging
- debugging custom assemblies [Reporting Services]
- troubleshooting [Reporting Services], custom assemblies
ms.assetid: 3a3215b3-548c-4474-81ba-3a98dd3912bf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1b5f9f5a4595d59cce98da4f753422cd07529926
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746790"
---
# <a name="how-to-debug-custom-assemblies"></a>Procedimientos: Depuración de ensamblados personalizados
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Proporciona varias herramientas de depuración que pueden ayudarle a analizar el código de ensamblado personalizado y encontrar errores en él. La mejor herramienta para utilizar dependerá de lo que intente llevar a cabo. En este ejemplo se usa [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)].  
  
 La manera recomendada de diseñar, desarrollar y probar los ensamblados personalizados para [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] es crear una solución que contenga tanto los informes de prueba como el ensamblado personalizado.  
  
### <a name="to-debug-assemblies-using-a-single-instance-of-visual-studio"></a>Para depurar ensamblados con una única instancia de Visual Studio  
  
1.  Cree un nuevo proyecto de informe mediante [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
     Cuando se crea un proyecto de informe, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] también se crea una solución que lo contiene.  
  
2.  Agregue un nuevo proyecto de biblioteca de clases a la solución existente. Asegúrese de que el proyecto de informe se establece como proyecto de inicio. Para obtener más información sobre cómo llevarlo a cabo, vea la documentación de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
3.  En el Explorador de soluciones, seleccione la solución.  
  
4.  En el menú **Ver**, haga clic en **Páginas de propiedades**.  
  
     Se abre el cuadro de diálogo **Páginas de propiedades de la solución**.  
  
5.  En el panel izquierdo, expanda **Propiedades comunes** si fuera necesario y haga clic en **Dependencias del proyecto**. Seleccione el proyecto de informe en la lista desplegable **Proyecto**. Seleccione el proyecto de ensamblado en la lista **Depende de**.  
  
6.  Haga clic en **Aceptar** para guardar los cambios y cierre el cuadro de diálogo **Páginas de propiedades**.  
  
7.  En el Explorador de soluciones, seleccione su proyecto de ensamblado personalizado.  
  
8.  En el menú **Ver**, haga clic en **Páginas de propiedades**.  
  
     Se abre el cuadro de diálogo **Páginas de propiedades**.  
  
9. Haga clic en la pestaña **Generar** si se encuentra en un proyecto C# o en la pestaña **Compilar** si se encuentra en un proyecto de [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].  
  
10. En la **Build** / página**compilar** compilación, escriba la ruta de acceso a la carpeta diseñador de informes. De forma predeterminada, es C:\Archivos de programa\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE en el cuadro de texto **Ruta de acceso de salida**. De esta forma se genera e implementa directamente una versión actualizada del ensamblado personalizado para el Diseñador de informes antes de que se ejecute el informe.  
  
11. Cuando haya diseñado el informe y desarrollado el ensamblado personalizado, establezca puntos de interrupción en el código de ensamblado personalizado.  
  
12. Ejecute el informe en el modo **DebugLocal** al presionar tecla F5. Cuando el informe se ejecuta en la ventana de la vista previa emergente, el depurador se para en los puntos de interrupción que se corresponden con el código ejecutable del ensamblado. Utilice F11 para recorrer el código de ensamblado personalizado.  
  
### <a name="to-debug-assemblies-using-two-instances-of-visual-studio"></a>Para depurar los ensamblados con dos instancias de Visual Studio  
  
1.  Inicie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] y abra el proyecto de ensamblado personalizado.  
  
2.  Genere el proyecto e implemente el ensamblado personalizado y el archivo .pdb acompañante para el Generador de informes. Para más información sobre la implementación, vea [Implementar un ensamblado personalizado](deploying-a-custom-assembly.md).  
  
3.  Abra un proyecto de informe que use el ensamblado personalizado mientras deja el código de ensamblado personalizado abierto en una instancia independiente de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
4.  Navegue a la instancia de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] que contiene el proyecto de ensamblado personalizado y establezca algunos puntos de interrupción en el código.  
  
5.  Con el proyecto de ensamblado personalizado aún en la ventana activa, haga clic en **Asociar al proceso** en el menú **Depurar**.  
  
     Se abre el cuadro de diálogo **Asociar al proceso**.  
  
6.  En la lista de procesos, seleccione el proceso devenv.exe que corresponda al proyecto de informe y haga clic en **Asociar**.  
  
7.  Defina las expresiones que utilizará en el informe desde su ensamblado personalizado y diseñe el informe.  
  
8.  Cuando termine de diseñar el informe, haga clic en la pestaña **Vista previa**.  
  
     El informe se ejecuta y el código de ensamblado personalizado debería detenerse en los puntos de interrupción predefinidos.  
  
    > [!NOTE]  
    >  El uso de la pestaña **Vista previa** no exige permisos de código para el ensamblado. Para realizar una prueba completa que incluya algún error de seguridad de acceso del código, inicie el proyecto de informe con la opción de configuración **DebugLocal**.  
  
9. Recorra el código con la tecla F11. Para obtener más información acerca de cómo depurar con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], vea la documentación de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Consulte también  
 [Usar ensamblados personalizados con informes](using-custom-assemblies-with-reports.md)  
  
  
