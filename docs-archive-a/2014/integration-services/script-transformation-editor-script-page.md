---
title: Editor de transformación script (página script) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponent.script.f1
helpviewer_keywords:
- Script Transformation Editor
ms.assetid: 4c6d1901-ef21-4aa7-9d0a-6bbeb7fadf1c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: df89bddd0a2f12e1d0efe0db74f4e10aadd772eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673076"
---
# <a name="script-transformation-editor-script-page"></a>Editor de transformación Script (página Script)
  Use la pestaña **Script** del cuadro de diálogo **Editor de transformación Script** para especificar un script y las propiedades relacionadas.  
  
 Para obtener más información acerca del componente de script, vea [Script Component](data-flow/transformations/script-component.md) y [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md). Para obtener información acerca de cómo programar el componente de script, vea [Ampliar el flujo de datos con el componente de script](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
## <a name="options"></a>Opciones  
 **Propiedades**  
 Vea y modifique las propiedades de la transformación de script. Muchas de las propiedades mostradas son de solo lectura. Puede modificar las siguientes propiedades:  
  
|Value|Descripción|  
|-----------|-----------------|  
|**Descripción**|Describe la transformación del script según su propósito.|  
|**LocaleID**|Especifica la configuración regional para proporcionar información específica de la región para ordenar y para la conversión de fecha y hora.|  
|**Nombre**|Escriba un nombre descriptivo para el componente.|  
|**ValidateExternalMetadata**|Indica si la transformación del script valida metadatos de columna con orígenes de datos externos en tiempo de diseño. El valor `false` retrasa la validación hasta el momento de la ejecución.|  
|**Variables de solo lectura**|Escriba una lista de variables separadas por comas (sin espacios) a la que la transformación del script tenga acceso de solo lectura.<br /><br /> Nota: Los nombres de variables distinguen entre mayúsculas y minúsculas.|  
|**Variables de lectura/escritura**|Escriba una lista de variables separadas por comas (sin espacios) a la que la transformación del script tenga acceso de lectura y escritura.<br /><br /> Nota: Los nombres de variables distinguen entre mayúsculas y minúsculas.|  
|**Lenguaje de script**|Seleccione el lenguaje de script que va a usar el componente de script.<br /><br /> Para establecer el lenguaje de script predeterminado para los componentes Script y las tareas de script, utilice la opción **Lenguaje de scripting** en la página **General** del cuadro de diálogo **Opciones** . Para obtener más información, vea [General Page](general-page-of-integration-services-designers-options.md).|  
|**UserComponentTypeName**|Especifica la clase <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost> y el ensamblado `Microsoft.SqlServer.TxScript` compatibles con la infraestructura de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|  
  
 **Editar script**  
 Use [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA) para crear o modificar un script.  
  
## <a name="see-also"></a>Consulte también  
 [Referencia de errores y mensajes de Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Seleccionar tipo de componente de script](../../2014/integration-services/select-script-component-type.md)   
 [Editor de transformación script &#40;página columnas de entrada&#41;](../../2014/integration-services/script-transformation-editor-input-columns-page.md)   
 [Editor de transformación script &#40;página entradas y salidas&#41;](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md)   
 [Editor de transformación script &#40;página administradores de conexión&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md)   
 [Ejemplos de componente de script adicionales](extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  
