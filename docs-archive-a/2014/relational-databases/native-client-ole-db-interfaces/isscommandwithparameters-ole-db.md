---
title: ISSCommandWithParameters (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSCommandWithParameters (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- ISSCommandWithParameters interface
ms.assetid: 3419b7f3-36a3-4863-816e-e641e4e90496
author: rothja
ms.author: jroth
ms.openlocfilehash: 295026497a97b4ce13d1a1a68de48079809390ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87671033"
---
# <a name="isscommandwithparameters-ole-db"></a>ISSCommandWithParameters (OLE DB)
  **ISSCommandWithParameters** expone la compatibilidad con los tipos XML y definidos por el usuario (UDT) de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Ésta es una interfaz opcional que hereda de la interfaz OLE DB **ICommandWithParameters**básica. Además de los tres métodos heredados de **ICommandWithParameters**; **GetParameterInfo**, **MapParameterNames**y **SetParameterInfo**; **ISSCommandWithParameters** proporciona dos nuevos métodos que se utilizan para administrar tipos de datos específicos de servidor.  
  
> [!NOTE]  
>   La interfaz **ISSCommandWithParameters** se puede utilizar cuando se utilizan componentes de servicio, pero los propios componentes de servicio no utilizarán esta interfaz.  
  
|Método|Descripción|  
|------------|-----------------|  
|[ISSCommandWithParameters::GetParameterProperties &#40;OLE DB&#41;](isscommandwithparameters-getparameterproperties-ole-db.md)|Devuelve la estructura del conjunto de propiedades **SSPARAMPROPS** en la matriz de cada parámetro UDT o XML pasado al comando, pero no devuelve nada en los demás tipos de parámetros.|  
|[ISSCommandWithParameters::SetParameterProperties &#40;OLE DB&#41;](isscommandwithparameters-setparameterproperties-ole-db.md)|Establece las propiedades de parámetro por cada parámetro por ordinal o establece propiedades masivas de parámetro mediante la especificación de una matriz de estructuras **SSPARAMPROPS** .|  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)   
 [Usar tipos de datos XML](../native-client/features/using-xml-data-types.md)   
 [Usar tipos definidos por el usuario](../native-client/features/using-user-defined-types.md)  
  
  
