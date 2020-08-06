---
title: Asociar un parámetro de consulta a un parámetro de informe (Generador de informes y SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- queries [Reporting Services], parameters
- parameters [Reporting Services], queries
ms.assetid: 6d297e1a-ff71-472a-addc-349e863092b5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f65aa36e8910378d68963c8c9990518b661025ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745065"
---
# <a name="associate-a-query-parameter-with-a-report-parameter-report-builder-and-ssrs"></a>Asociar un parámetro de consulta a un parámetro de informe (Generador de informes y SSRS)
  Cuando define una consulta de conjunto de datos que contiene una variable de consulta, se analiza el comando de consulta. Para cada variable de consulta, se crea un parámetro de informe y un parámetro de conjunto de datos correspondientes. El parámetro de conjunto de datos señala el parámetro de informe. Esto permite al usuario especificar un valor que pasa directamente a la consulta. Cada vez que se modifica el comando de consulta, se realiza el mismo proceso.  
  
 Si cambia el nombre de un parámetro de informe que está enlazado a un parámetro de consulta, deberá vincular manualmente los parámetros de consulta al parámetro de informe con el nuevo nombre; para ello, deberá seguir el procedimiento descrito en este tema.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-associate-a-query-parameter-with-a-report-parameter"></a>Para asociar un parámetro de consulta a un parámetro de informe  
  
1.  En el panel Datos de informe, haga clic con el botón derecho en el conjunto de datos, haga clic en **Propiedades del conjunto de datos**y, después, haga clic en **Parámetros**.  
  
    > [!NOTE]  
    >   Si el panel Datos de informe no está visible, haga clic en **Datos de informe** en el menú **Ver** .  
  
2.  En la columna **Nombre de parámetro**, busque el nombre del parámetro de consulta. Los nombres de los parámetros se rellenan automáticamente basándose en la consulta. Cada vez que cambia la consulta, la consulta se comprueba para ver si existen nuevos parámetros de consulta. Los parámetros de consulta creados manualmente no cambian cuando cambia la consulta.  
  
    -   En **Nombre de parámetro**, busque el nombre del parámetro de consulta tal y como existe en la consulta. También puede agregar manualmente un nuevo parámetro de consulta y escribir un nombre.  
  
    -   En **Valor de parámetro**, escriba o seleccione una expresión que se evalúe como el valor que se va a pasar al parámetro de consulta. Éste es normalmente el nombre del parámetro de informe.  
  
        > [!NOTE]  
        >  El valor de los parámetros de consulta no está limitado a parámetros de informe. Como valor del parámetro se puede utilizar cualquier expresión que se evalúe como un valor.  
  
3.  Repita el paso 2 para otros parámetros de consulta.  
  
## <a name="see-also"></a>Consulte también  
 [Conjuntos de valores integrados de informe y conjuntos de recursos compartidos &#40;Generador de informes y SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Concepto de parámetros de informe &#40;Generador de informes y SSRS&#41;](../report-design/report-parameters-concepts-report-builder-and-ssrs.md)  
  
  
