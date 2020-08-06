---
title: Propiedades del conjunto de datos (cuadro de diálogo), parámetros | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10150"
- sql12.rtp.rptdesigner.datasetproperties.parameters.f1
ms.assetid: 43b00aab-e2c3-4e85-abe1-a2b5a21efeed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0073971de373321ce347f416657671e1f497dd1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751789"
---
# <a name="dataset-properties-dialog-box-parameters"></a>Propiedades del conjunto de datos (cuadro de diálogo), Parámetros
  Seleccione **Parámetros** en el cuadro de diálogo **Propiedades del conjunto de datos** para agregar, cambiar y eliminar parámetros de la consulta, incluso los que vinculan a los parámetros de informe.  
  
 Siempre que se modifica la consulta en la pestaña de consulta, se analiza el comando de consulta. Para cada parámetro de consulta que se identifica, se crea un parámetro de informe con un nombre idéntico que distingue mayúsculas de minúsculas. De forma predeterminada, el parámetro de la consulta se agrega automáticamente a la lista de parámetros de la consulta y se vincula al parámetro de informe correspondiente.  
  
 Si los valores predeterminados de un parámetro de informe tienen dependencias en otro parámetro de informe vinculado a un parámetro de la consulta, el orden de los parámetros de informe (tal como aparecen en el cuadro de diálogo **Propiedades de parámetro de informe** ) es importante. Los parámetros de informe que figuran más abajo en la lista pueden hacer referencia a los parámetros que les preceden en la lista. Para más información sobre parámetros de informe, vea [Parámetros de informe &#40;Generador de informes y Diseñador de informes&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).  
  
## <a name="options"></a>Opciones  
 **Add (Agregar)**  
 Agrega un parámetro nuevo a la lista.  
  
 **Eliminar**  
 Quita el parámetro seleccionado de la lista.  
  
 **Nombre de parámetro**  
 Escriba el nombre de un parámetro de consulta que agregó al conjunto de datos en la pestaña **Consulta** del cuadro de diálogo **Propiedades del conjunto de datos** .  
  
 **Valor del parámetro**  
 Escriba un valor para el parámetro de la consulta. Puede ser un valor estático o una expresión que haga referencia a un objeto del informe, pero no puede hacer referencia a elementos o campos de informe. De forma predeterminada, **Valor** contiene una expresión que apunta a un parámetro de informe.  
  
 **Flecha arriba**  
 Mueve el parámetro seleccionado hacia arriba en la lista.  
  
 **Flecha abajo**  
 Mueve el parámetro seleccionado hacia abajo en la lista.  
  
## <a name="see-also"></a>Consulte también  
 [Parámetros de informe &#40;Generador de informes y Diseñador de informes&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [Agregar datos a un informe &#40;Generador de informes y SSRS&#41;](report-datasets-ssrs.md)   
 [Cambiar el orden de un parámetro de informe &#40;Generador de informes y SSRS&#41;](../report-design/change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)  
  
  
