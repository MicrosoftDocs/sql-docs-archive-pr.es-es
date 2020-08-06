---
title: Implementar un ensamblado personalizado | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- deploying custom assemblies [Reporting Services]
- custom assemblies [Reporting Services], deploying
- custom assemblies [Reporting Services], updating
- updating custom assemblies
ms.assetid: c6674cd8-0de7-4a5a-9e7c-12ffa49f6fd2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3d88e1db844304b5cbb51f4af52b4715ef7e8c1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750537"
---
# <a name="deploying-a-custom-assembly"></a>Implementar un ensamblado personalizado
  Para implementar un ensamblado personalizado en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , coloque el ensamblado en las carpetas de aplicación de diseñador de informes y del servidor de informes. De forma predeterminada, a los ensamblados personalizados se les concede el permiso `Execution` en [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Para conceder privilegios a los ensamblados personalizados a parte del permiso Ejecutar, tendrá que modificar el archivo de configuración rssrvpolicy.config para el servidor de informes y el archivo de configuración rspreviewpolicy.config para la ventana de vista previa del Diseñador de informes. Otra opción es instalar el ensamblado personalizado en la memoria caché de ensamblados global (GAC).  
  
> [!NOTE]  
>  Hay dos modos de vista previa para el Diseñador de informes: la pestaña Vista previa y la ventana de vista previa emergente que se inician cuando se inicia el proyecto de informe en modo `DebugLocal`. La pestaña Vista previa ejecuta todas las expresiones de informe usando el conjunto de permisos `FullTrust` y no aplica la configuración de la directiva de seguridad. La ventana de vista previa emergente está pensada para simular la funcionalidad del servidor de informes y, por consiguiente, tiene un archivo de configuración de directiva que usted o un administrador deben modificar para utilizar ensamblados en el Diseñador de informes. Esta vista previa emergente también bloquea el ensamblado personalizado. Por consiguiente, es necesario cerrar la ventana de vista previa para modificar o actualizar el código de ensamblado personalizado.  
  
###### <a name="to-deploy-a-custom-assembly-in-reporting-services"></a>Para implementar un ensamblado personalizado en Reporting Services  
  
1.  Copie el ensamblado personalizado desde la ubicación de compilación a la carpeta bin del servidor de informes o a la carpeta del Diseñador de informes. La ubicación predeterminada de la carpeta bin del servidor de informes es %Archivos de programa%\Microsoft SQL Server\ MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin. La ubicación predeterminada del Diseñador de informes es %Archivos de programa%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.  
  
     Si coloca el ensamblado personalizado en la carpeta bin del servidor de informes, podrá publicar informes que hagan referencia a ese ensamblado personalizado; si lo colocar en la carpeta del Diseñador de informes, podrá ejecutar y depurar informes que hagan referencia al ensamblado personalizado en el Diseñador de informes.  
  
     Si necesita conceder permisos de código de ensamblado personalizados además de los permisos de ejecución predeterminados:  
  
2.  Abra el archivo de configuración adecuado. La ubicación predeterminada del archivo rssrvpolicy.config es %Archivos de programa%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer. La ubicación predeterminada del archivo rspreviewpolicy.config es %Archivos de programa%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.  
  
3.  Agregue un grupo de código para el ensamblado personalizado. Para más información, vea [Desarrollo seguro &#40;Reporting Services&#41;](../extensions/secure-development/secure-development-reporting-services.md).  
  
## <a name="updating-custom-assemblies"></a>Actualizar ensamblados personalizados  
 En algún momento, puede que tenga que actualizar una versión de un ensamblado personalizado al que varios informes publicados hagan referencia en ese instante. Si ese ensamblado ya existe en el directorio bin del servidor de informes o del Diseñador de informes, y el número de versión del ensamblado se incrementa o se cambia de alguna manera, los informes publicados actualmente ya no funcionarán de forma correcta. Tendrá que actualizar la versión del ensamblado al que se hace referencia en el elemento `CodeModules` de la definición de informe y volver a publicar los informes. Si sabe que va a actualizar con frecuencia un ensamblado personalizado y los informes publicados actualmente necesitan hacer referencia al nuevo ensamblado, puede que sea conveniente usar el mismo número de versión a través de todas las actualizaciones de un ensamblado determinado.  
  
 Si no necesita que los informes publicados hagan referencia a la nueva versión del ensamblado, puede implementar el ensamblado personalizado en la memoria caché de ensamblados global. La memoria caché de ensamblados global puede mantener varias versiones del mismo ensamblado, de modo que los informes actuales puedan hacer referencia a la versión anterior del ensamblado y los informes publicados recientemente puedan hacer referencia al ensamblado actualizado. Otro enfoque más sería establecer la redirección obligatoria del servidor de informes para forzar una redirección de todas las solicitudes para el ensamblado anterior al nuevo ensamblado. Necesitaría modificar los archivos Web.config y ReportService.exe.config del servidor de informes. La entrada podría tener la apariencia siguiente:  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte también  
 [Usar ensamblados personalizados con informes](using-custom-assemblies-with-reports.md)   
 [Trabajar con ensamblados y la memoria caché global de ensamblados](https://go.microsoft.com/fwlink/?LinkId=63912)  
  
  
