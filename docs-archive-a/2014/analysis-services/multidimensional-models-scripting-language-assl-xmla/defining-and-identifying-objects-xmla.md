---
title: Definir e identificar objetos (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [XML for Analysis]
- identifying objects [XML for Analysis]
- XML for Analysis, objects
- object references [XML for Analysis]
- object identifiers [XML for Analysis]
- object definitions [XML for Analysis]
- XMLA, objects
ms.assetid: 43b65f6d-0123-4556-81f0-c7a0b84361e5
author: minewiskan
ms.author: owend
ms.openlocfilehash: d2fd3263a2f8050c36747a81ab3473f5b405ef21
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676228"
---
# <a name="defining-and-identifying-objects-xmla"></a>Definir e identificar objetos (XMLA)
  Los objetos se identifican en los comandos XML for Analysis (XMLA) mediante identificadores de objetos y referencias a objetos, y se definen mediante los elementos ASSL (Analysis Services Scripting Language) de los comandos XMLA.  
  
## <a name="object-identifiers"></a>Identificadores de objetos  
 Un objeto se identifica mediante el identificador único del objeto tal y como se define en una instancia de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Los identificadores de objetos se pueden especificar o determinar explícitamente por la instancia [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] cuando [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] crea el objeto. Puede usar el método [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) para recuperar los identificadores de objeto para las `Discover` llamadas a métodos posteriores o [ejecutadas](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) .  
  
## <a name="object-references"></a>Referencias a objetos  
 Varios comandos XMLA, como [Delete](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/delete-element-xmla) o [Process](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla), usan una referencia de objeto para hacer referencia a un objeto de una manera inequívoca. Una referencia a objetos contiene el identificador de objetos del objeto en el que se ejecuta un comando y los identificadores de objetos de los antecesores para ese objeto. Por ejemplo, la referencia a objetos para una partición contiene el identificador de objetos de la partición, así como los identificadores de objetos del grupo, cubo y base de datos de medida primario de esa partición.  
  
## <a name="object-definitions"></a>Definiciones de objetos  
 Los comandos [Create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) y [ALTER](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) de XMLA crean o modifican, respectivamente, objetos en una [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instancia de. Las definiciones de estos objetos se representan mediante un elemento [ObjectDefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla) que contiene elementos de ASSL. Los identificadores de objeto se pueden especificar explícitamente para todos los objetos principales y muchos secundarios mediante el elemento [ID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) . Si no se usa el elemento `ID`, la instancia [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] proporciona un identificador único, con una convención de nomenclatura que depende del objeto que se va a identificar. Para obtener más información sobre cómo usar los `Create` `Alter` comandos y para definir objetos, vea [crear y modificar objetos &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects).  
  
## <a name="see-also"></a>Consulte también  
 [Elemento Object &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)   
 [Elemento ParentObject &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)   
 [Elemento de origen &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)   
 [Elemento Target &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla)   
 [Desarrollar con XMLA en Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
