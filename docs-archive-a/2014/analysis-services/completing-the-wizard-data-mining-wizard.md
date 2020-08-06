---
title: Finalización del asistente (Asistente para minería de datos) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.finish.f1
ms.assetid: 6aef1548-35eb-42fd-ae87-63650a79eda1
author: minewiskan
ms.author: owend
ms.openlocfilehash: eb5b040099494659dc7c98e98c925d025dbd439e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87670054"
---
# <a name="completing-the-wizard-data-mining-wizard"></a>Finalización del asistente (Asistente para minería de datos)
  Use la página **Finalización del asistente** para revisar la estructura de minería de datos que se creará cuando finalice el asistente. También puede definir el nombre de la estructura de minería de datos.  
  
 Si decidió crear un modelo de minería asociado, también puede establecer el nombre del modelo de minería asociado y habilitar la obtención de detalles en el modelo de minería.  
  
> [!NOTE]  
>  Esta página cambia en función de si se selecciona **A partir de una base de datos relacional o un almacenamiento de datos** o **A partir de un cubo existente** en la página **Seleccionar el método de definición** del asistente.  
  
 **Para obtener más información:** [Asistente para minería de datos &#40;Analysis Services - Minería de datos&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Diseñador de minería de datos](data-mining/data-mining-designer.md), [Crear una estructura de minería de datos relacional](data-mining/create-a-relational-mining-structure.md).  
  
## <a name="options"></a>Opciones  
 **Nombre de la estructura de minería de datos**  
 Escriba el nombre de la estructura de minería de datos definida mediante el **Asistente para minería de datos**.  
  
 **Nombre del modelo de minería de datos**  
 Escriba el nombre del modelo de minería de datos definido mediante el **Asistente para minería de datos**.  
  
 **Permitir obtención de detalles**  
 Seleccione esta opción para admitir la obtención de detalles en el nuevo modelo de minería de datos, si creó uno.  
  
> [!NOTE]  
>  La obtención de detalles en la estructura de minería de datos está habilitada de forma predeterminada.  
  
 Para obtener más información sobre las opciones de obtención de detalles, vea [Consultas de obtención de detalles &#40;minería de datos&#41;](data-mining/drillthrough-queries-data-mining.md).  
  
 **Versión preliminar**  
 Muestra la estructura de minería de datos que se va a crear.  
  
 **Crear dimensión de modelo de minería de datos**  
 Seleccione esta opción para crear una dimensión en función del modelo de minería de datos que se va a crear. Después de seleccionar esta opción, indique el nombre de la dimensión que se va a crear. Si se selecciona esta opción, se habilita **Crear el cubo con la dimensión del modelo de minería de datos**.  
  
> [!NOTE]  
>  Esta opción se encuentra disponible si ha seleccionado **A partir de un cubo existente** en la página **Seleccionar el método de definición** del asistente.  
  
 **Crear el cubo con la dimensión del modelo de minería de datos**  
 Seleccione esta opción para crear un cubo en función del modelo de minería de datos que se va a crear. Después de seleccionar esta opción, indique el nombre del cubo que se va a crear.  
  
> [!NOTE]  
>  Esta opción se encuentra disponible si ha seleccionado **A partir de un cubo existente** en la página **Seleccionar el método de definición** y si ha seleccionado **Crear dimensión de modelo de minería de datos** en la página actual del asistente.  
  
## <a name="see-also"></a>Consulte también  
 [Asistente para minería de datos (ayuda F1) &#40;Analysis Services: minería de datos&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [Seleccionar vista del origen de datos &#40;Asistente para minería de datos&#41;](select-data-source-view-data-mining-wizard.md)   
 [Especificar los datos de entrenamiento &#40;Asistente para minería de datos&#41;](specify-the-training-data-data-mining-wizard.md)  
  
  
