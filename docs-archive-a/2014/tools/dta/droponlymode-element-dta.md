---
title: DropOnlyMode (DTA, elemento) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DropOnlyMode element
ms.assetid: 80960676-7581-4074-889b-80ee665963dd
author: stevestein
ms.author: sstein
ms.openlocfilehash: b274dc394a933308cf2161cc271d09b8391900c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743780"
---
# <a name="droponlymode-element-dta"></a>DropOnlyMode (DTA, elemento)
  Especifica que el Asistente para la optimización de motor de base de datos solo debe quitar índices, vistas indizadas o particiones ya existentes durante la sesión de optimización. Cuando se especifica esta opción de optimización, no se consideran nuevas estructuras de diseño físico.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <DropOnlyMode>...</DropOnlyMode>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|**Tipo y longitud de los datos**|Ninguno.|  
|**Valor predeterminado**|Ninguno.|  
|**Repetición**|Opcional. Se puede utilizar una sola vez por cada elemento `TuningOptions`. No se puede utilizar si se especifican los siguientes elementos en el elemento `TuningOptions`:<br /><br /> [FeatureSet &#40;DTA, elemento&#41;](featureset-element-dta.md)<br /><br /> [Partitioning &#40;DTA, elemento&#41;](partitioning-element-dta.md)<br /><br /> [KeepExisting &#40;DTA, elemento&#41;](keepexisting-element-dta.md) se establece en **ALL**|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elementos|  
|------------------|--------------|  
|**Elemento primario**|[TuningOptions &#40;DTA, elemento&#41;](tuningoptions-element-dta.md)|  
|**Elementos secundarios**|Ninguno.|  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra la sección `TuningOptions` de un archivo de entrada XML del Asistente para la optimización de motor de base de datos donde se especifica `DropOnlyMode`. En este ejemplo, la hora de optimización se limita a 24 horas (1440 minutos) y se considerará la eliminación de todos los clúster y no clúster existentes:  
  
```xml  
<TuningOptions  
  <TuningTimeInMin>1440</Name>  
  <KeepExisting>ALIGNED</KeepExisting>  
  <DropOnlyMode />  
</TuningOptions>  
```  
  
## <a name="see-also"></a>Consulte también  
 [Referencia del archivo de entrada XML &#40;Asistente para la optimización de motor de base de datos&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
