---
title: Desarrollar tipos específicos de los componentes de script | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], examples
ms.assetid: dfbbe959-6b4e-4b47-b9dd-bcc31929482d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 114c9ddca90ea02a8e1847444b28b9d5876650a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673770"
---
# <a name="developing-specific-types-of-script-components"></a>Desarrollar tipos específicos de los componentes de script
  El componente de script es una herramienta configurable que puede utilizar en el flujo de los datos de un paquete para llenar casi cualquier requisito no cumplido por los orígenes, transformaciones y destinos que se incluyen con [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Esta sección contiene ejemplos de código de componente de script que muestran las cuatro opciones para configurar el componente de script:  
  
-   Como un origen.  
  
-   Como una transformación con salidas sincrónicas.  
  
-   Como una transformación con salidas asincrónicas.  
  
-   Como un destino.  
  
 Para obtener ejemplos adicionales del componente de Script, consulte [Ejemplos de componente de script adicionales](../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).  
  
## <a name="in-this-section"></a>En esta sección  
 [Crear un origen con el componente de script](creating-a-source-with-the-script-component.md)  
 Explica y muestra cómo crear un origen de flujo de datos mediante el componente de script.  
  
 [Crear una transformación sincrónica con el componente de script](creating-a-synchronous-transformation-with-the-script-component.md)  
 Explica y muestra cómo crear una transformación de flujo de datos con salidas sincrónicas mediante el componente de script. Este tipo de transformación modifica filas de datos en su lugar cuando pasan a través del componente.  
  
 [Crear una transformación asincrónica con el componente de script](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)  
 Explica y muestra cómo crear una transformación de flujo de datos con salidas asincrónicas mediante el componente de script. Este tipo de transformación tiene que leer todas las filas de datos antes de poder agregar más información, como agregados calculados, a los datos que pasan a través del componente.  
  
 [Crear un destino con el componente de script](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
 Explica y muestra cómo crear un destino de flujo de datos mediante el componente de script.  
  
![Integration Services icono (pequeño)](../media/dts-16.gif "Icono de Integration Services (pequeño)")  **Manténgase al día con Integration Services**<br /> Para obtener las descargas, artículos, ejemplos y vídeos más recientes de Microsoft, así como soluciones seleccionadas de la comunidad, visite la página de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] en MSDN:<br /><br /> [Visite la página de Integration Services en MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Para recibir notificaciones automáticas de estas actualizaciones, suscríbase a las fuentes RSS disponibles en la página.  
  
## <a name="see-also"></a>Consulte también  
 [Comparar soluciones de scripting y objetos personalizados](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)   
 [Desarrollar tipos específicos de componentes de flujo de datos](../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)  
  
  
