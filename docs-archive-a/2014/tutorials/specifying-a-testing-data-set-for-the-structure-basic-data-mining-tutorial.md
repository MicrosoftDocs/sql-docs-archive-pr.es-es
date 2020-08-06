---
title: Especificar un conjunto de datos de prueba para la estructura (tutorial básico de minería de datos) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 75cd508f-b126-418b-848d-3c4c3e6c303f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c1430706a0ec2cd3ddc0eaee18d7001d05fefae1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662420"
---
# <a name="specifying-a-testing-data-set-for-the-structure-basic-data-mining-tutorial"></a>Especificar un conjunto de datos de pruebas para la estructura (Tutorial básico de minería de datos)
  En las pantallas finales del Asistente para minería de datos dividirá los datos en un conjunto de pruebas y en un conjunto de entrenamiento. Después, asignará nombre a la estructura y habilitará la obtención de detalles en el modelo.  
  
## <a name="specifying-a-testing-set"></a>Especificar un conjunto de pruebas  
 Al separar los datos en conjuntos de entrenamiento y de pruebas cuando se crea una estructura de minería de datos, es posible evaluar fácilmente la precisión de los modelos de minería de datos que se crean después. Para obtener más información sobre los conjuntos de pruebas, consulte [conjuntos de datos de entrenamiento y de prueba](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md).  
  
#### <a name="to-specify-the-testing-set"></a>Para especificar el conjunto de pruebas  
  
1.  En la página **crear conjunto de pruebas** , en **porcentaje de datos para pruebas**, deje el valor predeterminado de `30` .  
  
2.  **En número máximo de casos en el conjunto de datos de prueba**, escriba `1000` .  
  
3.  Haga clic en **Next**.  
  
## <a name="specifying-drillthrough"></a>Especificar la obtención de detalles  
 La obtención de detalles puede habilitarse en los modelos y en las estructuras. La casilla de este cuadro de diálogo habilita la obtención de detalles en el modelo con nombre. Una vez procesado el modelo, podrá recuperar información detallada de los datos de entrenamiento usados para crear el modelo.  
  
 Si la estructura de minería de datos subyacente también se ha configurado para permitir la obtención de detalles, puede recuperar información detallada tanto de los casos de modelos como de la estructura, incluidas las columnas que no estaban incluidas en el modelo de minería de datos. Para obtener más información, vea [Consultas de obtención de detalles &#40;minería de datos&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md).  
  
#### <a name="to-name-the-model-and-structure-and-specify-drillthrough"></a>Para denominar el modelo y la estructura, y especificar la obtención de detalles  
  
1.  En la página **finalización del asistente** , en nombre de la **estructura de minería de datos**, escriba `Targeted Mailing` .  
  
2.  En **nombre del modelo de minería de datos**, escriba `TM_Decision_Tree` .  
  
3.  Active la casilla **permitir obtención de detalles** .  
  
4.  Revise el panel de **vista previa** . Observe que solo se muestran las columnas seleccionadas como **clave**, **entrada** o **predicción** . Las otras columnas que seleccionó (por ejemplo, AddressLine1) no se usan para generar el modelo, pero estarán disponibles en la estructura subyacente y se pueden consultar una vez procesado e implementado el modelo.  
  
5.  Haga clic en **Finalizar**  
  
## <a name="previous-task-in-lesson"></a>Tarea anterior de la lección  
 [Especificar el tipo de datos y el tipo de contenido &#40;tutorial básico de minería de datos&#41;](../../2014/tutorials/specifying-the-data-type-and-content-type-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Lección siguiente  
 [Lección 3: Adición y procesamiento de modelos](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
  
## <a name="see-also"></a>Consulte también  
 [Habilitar la obtención de detalles para un modelo de minería de datos](../../2014/analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md)   
 [Consultas de obtención de detalles &#40;&#41;de minería de datos](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)   
 [Especificar los datos de entrenamiento &#40;Asistente para minería de datos&#41;](../../2014/analysis-services/specify-the-training-data-data-mining-wizard.md)  
  
  
