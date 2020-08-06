---
title: Transformar datos con transformaciones | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data flow [Integration Services], transformations
- transformations [Integration Services], about transformations
- transforming data [Integration Services]
ms.assetid: e1340b6f-ef75-4b14-af6f-823586eff0ed
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 952d8ea4eeea2dd8010a17a2b3deba41447b6231
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87677226"
---
# <a name="transform-data-with-transformations"></a>Transformar datos con transformaciones
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] incluye tres tipos de componentes de flujo de datos: orígenes, transformaciones y destinos.  
  
 El siguiente diagrama muestra un flujo de datos simple que tiene un origen, dos transformaciones y un destino.  
  
 ![Flujo de datos](../../media/mw-dts-08.gif "flujo de datos")  
  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ofrecen la siguiente funcionalidad:  
  
-   Dividir, copiar y combinar conjuntos de filas y realizar operaciones de búsqueda.  
  
-   Actualizar valores de columnas y crear nuevas columnas aplicando transformaciones tales como cambio de minúsculas por mayúsculas.  
  
-   Operaciones de inteligencia empresarial tales como limpiar datos, realizar minería de texto y ejecutar consultas de predicción de minería de datos.  
  
-   Crear nuevos conjuntos de filas que se componen de valores agregados u ordenados, datos de muestra o datos dinamizados y de anulación de dinamización.  
  
-   Realizar tareas tales como exportar e importar datos, proporcionar información de auditoría y trabajar con dimensiones de variación lenta.  
  
 Para más información, consulte [Integration Services Transformations](integration-services-transformations.md).  
  
 También puede escribir transformaciones personalizadas. Para más información, vea [Desarrollar un componente de flujo de datos personalizado](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) y [Desarrollar tipos específicos de componentes de flujo de datos](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md).  
  
 Después de agregar la transformación al diseñador de flujo de datos, pero antes de configurar la transformación, debe conectar la transformación al flujo de datos conectando la salida de otra transformación u origen del flujo de datos a la entrada de esta transformación. El conector entre dos componentes de flujo de datos se denomina ruta. Para más información sobre la conexión de componentes y el trabajo con rutas, vea [Conectar componentes con rutas de acceso](../../connect-components-with-paths.md).  
  
### <a name="to-add-a-transformation-to-a-data-flow"></a>Para agregar una transformación a un flujo de datos  
  
-   [Agregar o eliminar un componente en un flujo de datos](../add-or-delete-a-component-in-a-data-flow.md)  
  
### <a name="to-connect-a-transformation-to-a-data-flow"></a>Para conectar una transformación a un flujo de datos  
  
-   [Conectar componentes de un flujo de datos](../connect-components-in-a-data-flow.md)  
  
### <a name="to-set-the-properties-of-a-transformation"></a>Para establecer las propiedades de una transformación  
  
-   [Establecer las propiedades de un componente de flujo de datos](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="see-also"></a>Consulte también  
 [Tarea Flujo de datos](../../control-flow/data-flow-task.md)   
 [Flujo de datos](../data-flow.md)   
 [Conectar componentes con rutas de acceso](../../connect-components-with-paths.md)   
 [Control de errores en los datos](../error-handling-in-data.md)   
 [Flujo de datos](../data-flow.md)  
  
  
