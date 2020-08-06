---
title: Cuadro de diálogo Crear nueva condición o Abrir condición, página General | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.condition.f1
ms.assetid: 106954bf-e4ba-412b-9c1a-907d06153dcd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 72e4a77df553ac8e97609e82bd51c8fd93b64b23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87677597"
---
# <a name="create-new-condition-or-open-condition-dialog-box-general-page"></a>Cuadro de diálogo Crear nueva condición o Abrir condición, página General
  Utilice este cuadro de diálogo para crear o cambiar una condición de la administración basada en directivas. Una condición es una expresión booleana que especifica un conjunto de estados permitidos de un destino administrado mediante la administración basada en directivas con respecto a las facetas. Las propiedades que se pueden seleccionar en el cuadro **Expresión/Campo** dependen de la faceta que se use. Para obtener más información sobre cómo se relacionan las condiciones con las facetas y las directivas, vea [Administrar servidores mediante administración basada en directivas](administer-servers-by-using-policy-based-management.md).  
  
## <a name="options"></a>Opciones  
 **Nombre**  
 Si la condición es nueva, escriba un nombre para ella. Si la condición ya existe, se muestra el nombre.  
  
 **Faceta**  
 Faceta usada por esta condición.  
  
 **Y/O**  
 Al agregar varias expresiones, indica si las expresiones deben combinarse con **AND** u **OR**. Permanece en blanco cuando solo hay una expresión.  
  
 **Campo**  
 Cada faceta expone una o varias propiedades que se pueden establecer. En el cuadro de campo, seleccione una propiedad de la lista de propiedades disponibles para crear una expresión para esta condición.  
  
 **Operador**  
 Seleccione un operador de comparación para esta expresión. Los operadores son: =, !=, >, >=, <, <=, [NOT]LIKE, [NOT]IN. No todos los operadores están disponibles para algunas propiedades.  
  
 **Valor**  
 Configuración del valor para esta expresión. Los valores permitidos dependen de la faceta. Los valores pueden ser TRUE/FALSE, de tipo cadena o de tipo numérico. Los valores de tipo cadena se deben incluir entre comillas sencillas, por ejemplo: **'AdventureWorks'**. No todos los operadores están disponibles para algunas propiedades.  
  
## <a name="group-clauses"></a>Agrupar cláusulas  
 Las cláusulas se pueden agrupar para que operen como una sola unidad independiente del resto de la consulta; el resultado es similar al que se obtiene colocando unos paréntesis en torno a una expresión en una ecuación matemática o una instrucción lógica. La agrupación de cláusulas resulta útil cuando se crean consultas complejas.  
  
 **Para agrupar cláusulas**  
  
-   Presione la tecla Mayús o Ctrl, y a continuación haga clic en dos o más cláusulas para seleccionar un intervalo. Haga clic con el botón derecho en el área seleccionada y luego haga clic en **Agrupar cláusulas**.  
  
## <a name="see-also"></a>Consulte también  
 [Administrar servidores mediante administración basada en directivas](administer-servers-by-using-policy-based-management.md)  
  
  
