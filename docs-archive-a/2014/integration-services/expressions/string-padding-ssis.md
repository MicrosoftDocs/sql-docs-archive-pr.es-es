---
title: Rellenar cadenas (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- padding strings [Integration Services]
- expressions [Integration Services], string padding
- string padding
ms.assetid: d3fed73d-e0d4-4c67-9355-fb7083a72dd6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3985fd1b2f29260e2313a761797d2528f5d0e328
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746350"
---
# <a name="string-padding-ssis"></a>Rellenar cadenas (SSIS)
  El evaluador de expresiones no comprueba si una cadena contiene espacios en blanco iniciales y finales, ni rellena cadenas para que tengan la misma longitud antes de compararlas. Si las expresiones requieren rellenar cadenas, puede utilizar el operador + para concatenar valores de columnas y cadenas de espacios en blanco. Para más información, vea [+ &#40;Concatenar&#41; &#40;expresión de SSIS&#41;](concatenate-ssis-expression.md).  
  
 Por otra parte, si desea quitar espacios, el evaluador de expresiones proporciona las funciones LTRIM, RTRIM y TRIM, que quitan los espacios en blanco iniciales o finales, o ambos. Para más información, vea [LTRIM &#40;expresión de SSIS&#41;](trim-ssis-expression.md), [RTRIM &#40;expresión de SSIS&#41;](rtrim-ssis-expression.md) y [TRIM &#40;expresión de SSIS&#41;](trim-ssis-expression.md).  
  
> [!NOTE]  
>  La función LEN incluye en el recuento los espacios en blanco iniciales y finales.  
  
## <a name="related-content"></a>Contenido relacionado  
 Artículo técnico, sobre la [referencia rápida de expresiones de SSIS](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet
), en pragmaticworks.com  
  
  
