---
title: Elemento Issue (ssbdiagnose) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- issue element
- XML output file format [ssbdiagnose], issue element
- ssbdiagnose
ms.assetid: 2246a886-686b-44ca-9771-b155cedad8be
author: stevestein
ms.author: sstein
ms.openlocfilehash: a178c1323c1c20f84e67d4d7699fc313090a4c71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743723"
---
# <a name="issue-element-ssbdiagnose"></a>Elemento Issue (ssbdiagnose)
  Informa de un problema encontrado por la utilidad **ssbdiagnose** . El archivo de salida XML de **ssbdiagnose** tiene un elemento Issue por cada problema notificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
<Issue  
    type="..."   
    code="..."   
    server="..."   
    database="..."   
    object="...">   
    ...   
</Issue>  
```  
  
## <a name="element-attributes"></a>Atributos del elemento  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`type`|Identifica la categoría del problema sobre el que informa el elemento Issue.<br /><br /> **"Diagnóstico"** Informa de un problema de configuración encontrado al analizar una configuración de [!INCLUDE[ssSB](../../includes/sssb-md.md)] .<br /><br /> **"Problema"** Informa de un problema que ha impedido que **ssbdiagnose** complete el análisis. Corrija el problema y vuelva a ejecutar **ssbdiagnose**.<br /><br /> **"Evento"** Informa de un evento de [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] encontrado al ejecutar una comprobación de **-RUNTIME** . Solo se informa de los eventos si se especifica **-SHOWEVENTS** .|  
|`code`|Identifica el número de error del mensaje.|  
|`server`|Identifica la instancia de [!INCLUDE[ssDE](../../includes/ssde-md.md)] en la que se encontró el problema. Si el problema estaba en una instancia predeterminada, el atributo "server" solo tiene el nombre del equipo. Si el problema estaba en una instancia con nombre, el atributo "server" tiene el formato nombreDeEquipo\nombreDeInstancia.|  
|`database`|Identifica el nombre de la base de datos en la que se encontró el problema.|  
|`object`|Identifica el nombre del objeto en el que se encontró el problema. Si el problema era un problema de nivel de instancia o de base de datos, el atributo "object" repite el nombre de la instancia o de la base de datos.|  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|**Tipo y longitud de los datos**|`string`, la longitud es ilimitada.|  
|**Valor**|Devuelve el texto del mensaje de error.|  
|**Repetición**|Una vez por error notificado.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elementos|  
|------------------|--------------|  
|**Elemento primario**|[Elemento DiagnosticInformation &#40;ssbdiagnose&#41;](diagnosticinformation-element-ssbdiagnose.md)|  
|**Elementos secundarios**|None|  
  
## <a name="example"></a>Ejemplo  
 Este elemento informa de un error 1102 para una base de datos que no tiene una clave maestra, en la que se encontró el error al analizar una configuración de [!INCLUDE[ssSB](../../includes/sssb-md.md)] .  
  
```  
<Issue type="Diagnosis" code="1102" server="TestComputer" database="TargetDB" object="TargetDB">The master key was not found</diagnostic>  
```  
  
## <a name="see-also"></a>Consulte también  
 [Utilidad ssbdiagnose &#40;Service Broker&#41;](ssbdiagnose-utility-service-broker.md)  
  
  
