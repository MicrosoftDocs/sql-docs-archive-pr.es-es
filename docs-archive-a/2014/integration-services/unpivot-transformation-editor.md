---
title: Editor de transformación anulación de dinamización | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unpivottransformation.f1
helpviewer_keywords:
- Unpivot Transformation Editor
ms.assetid: 72a36ef0-4070-4f6c-9c74-0720109617dd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6c3b93370b34440b73b4c9c78dc7d19fa4095275
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669735"
---
# <a name="unpivot-transformation-editor"></a>Editor de transformación Anulación de dinamización
  Use el cuadro de diálogo **Editor de transformación Anulación de dinamización** para seleccionar las columnas que se van a dinamizar en filas y especificar la columna de datos y la nueva columna de salida del valor dinámico.  
  
> [!NOTE]  
>   Este tema utiliza el escenario Anulación de dinamización descrito en [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md) para ilustrar el uso de las opciones.  
  
 Para obtener más información acerca de la transformación Anulación de dinamización, vea [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md).  
  
## <a name="options"></a>Opciones  
 **Columnas de entrada disponibles**  
 Especifique las columnas que deben pasar a ser filas mediante las casillas.  
  
 **Nombre**  
 Muestra el nombre de la columna de entrada disponible.  
  
 **Paso a través**  
 Indique si desea incluir la columna en la salida de anulación de dinamización.  
  
 **Columna de entrada**  
 Seleccione de la lista de entradas disponibles las columnas para cada fila. Las selecciones se reflejan en las casillas activadas en la tabla **Columnas de entrada disponibles** .  
  
 En el escenario Anulación de dinamización descrito en [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), las columnas de entrada son las columnas **Ham**, **Soda**, **Milk**, **Beer**y **Chips** .  
  
 **Columna de destino**  
 Escriba un nombre para la columna de datos.  
  
 En el escenario Anulación de dinamización descrito en [Transformación Anulación de dinamización](data-flow/transformations/unpivot-transformation.md), la columna de destino es la columna de cantidad (**Qty**).  
  
 **Valor de clave dinámica**  
 Escriba el nombre del valor de dinamización. El nombre predeterminado es el de la columna de entrada, pero puede elegir cualquier nombre descriptivo único.  
  
 Puede especificar el valor de esta propiedad con una expresión de propiedad.  
  
 En el escenario Anulación de dinamización descrito en [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), los valores de dinamización se mostrarán como valores de texto en la nueva columna Product, designada en la opción **Nombre de la columna del valor de clave dinámica** , como los valores de texto **Ham**, **Soda**, **Milk**, **Beer**y **Chips**.  
  
 **Nombre de la columna del valor de clave dinámica**  
 Escriba un nombre para la columna del valor de dinamización. El valor predeterminado es "Valor de clave dinámica", pero podrá elegir cualquier nombre descriptivo único.  
  
 En el escenario Anulación de dinamización descrito en [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), el Nombre de la columna del valor de clave dinámica es **Product** y designa la nueva columna **Product** en la que se anula la dinamización de las columnas **Ham**, **Soda**, **Milk**, **Beer**y **Chips** .  
  
## <a name="see-also"></a>Consulte también  
 [Referencia de errores y mensajes de Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Transformación dinámica](data-flow/transformations/pivot-transformation.md)  
  
  
