---
title: Depurar procedimientos almacenados | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- debugging stored procedures [Analysis Services]
- stored procedures [Analysis Services], debugging
ms.assetid: 34f51b85-02b3-40dd-bf93-375a9e522385
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4f5971fe611f06a413ca48b2bc91237a8c87ee8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746039"
---
# <a name="debugging-stored-procedures"></a>Depurar procedimientos almacenados
  Los procedimientos almacenados de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] son bibliotecas CLR o COM (generalmente DLL) escritas en C# (u otro lenguaje de bibliotecas CLR o COM). Por consiguiente, la depuración de un procedimiento almacenado es muy similar a la depuración de cualquier otra aplicación del entorno de depuración de Visual Studio. Los procedimientos almacenados del entorno de desarrollo de Visual Studio pueden depurarse con las funciones de depuración integradas. Con ellas podrá detenerse en ubicaciones de procedimientos, inspeccionar los valores de memoria y registro, cambiar variables, observar el tráfico de mensajes y examinar cómo funciona el código.  
  
### <a name="to-debug-a-stored-procedure"></a>Para depurar un procedimiento almacenado  
  
1.  Abra el proyecto utilizado para crear la DLL en Visual Studio.  
  
2.  Cree puntos de interrupción en el método o función correspondiente al procedimiento que desee depurar.  
  
3.  Utilice Visual Studio para crear una compilación de depuración de una DLL del procedimiento almacenado.  
  
4.  Implemente la DLL en el servidor. Para obtener más información acerca de cómo implementar el archivo DLL en el servidor, vea [crear procedimientos almacenados](creating-stored-procedures.md).  
  
5.  Se necesita una aplicación que llame al procedimiento almacenado que desee probar. Si no dispone de una, puede utilizar el Editor de consultas MDX de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] para crear una consulta MDX que llame al procedimiento almacenado que desee probar.  
  
6.  En Visual Studio, adjunte al proceso de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (Msmdsrv.exe).  
  
    1.  En el menú **depurar** , elija **asociar toProcess**.  
  
    2.  En el cuadro de diálogo **asociar toProcess** , seleccione **Mostrar procesos de todos los usuarios**.  
  
    3.  En la lista **procesos disponibles** , en la columna **proceso** , haga clic en **Msmdsrv.exe**. Si se ejecutase más de una instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en el servidor, necesita identificar el proceso mediante el Id. de la instancia que desee utilizar.  
  
    4.  En el cuadro de texto **adjuntar a** , asegúrese de que está seleccionado el tipo de programa adecuado. Para un archivo DLL de CLR, haga clic en **seleccionar**, elija **depurar estos tipos de código**, haga clic en **administrado**y, a continuación, haga clic en **Aceptar**. Para un archivo DLL COM, haga clic en **seleccionar**, elija **depurar estos tipos de código**, haga clic en **nativo**y, a continuación, haga clic en **Aceptar**.  
  
    5.  Haga clic en **Adjuntar**.  
  
7.  En [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], invoque el programa o el script MDX que llama al procedimiento almacenado. El depurador se interrumpirá al alcanzar una línea que contiene un punto de interrupción. Podrá evaluar variables en la ventana de inspección, ver variables locales y reproducir el código.  
  
 Si experimenta problemas al depurar una biblioteca, compruebe que el archivo de la base de datos del programa (PDB) correspondiente se ha copiado en la ubicación de implementación del servidor. Si no se ha copiado el archivo durante el registro o la implementación, es necesario copiarlo manualmente en la misma ubicación que la DLL. En el código nativo (DLL de COM), el archivo PDB reside en el subdirectorio \debug. En el código administrado (DLL de CLR), reside en el subdirectorio \WINDEBUG.  
  
## <a name="see-also"></a>Consulte también  
 [Administración de ensamblados de modelos multidimensionales](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Definir procedimientos almacenados](defining-stored-procedures.md)  
  
  
