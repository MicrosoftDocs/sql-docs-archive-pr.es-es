---
title: Editor de transformación búsqueda (página general) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.general.f1
ms.assetid: 4bd15e48-0feb-4f95-be91-5df58105dbfb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aa178118f7e090b6a3c15c7ab9347f322461f07b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744769"
---
# <a name="lookup-transformation-editor-general-page"></a>Editor de transformación Búsqueda (página General)
  Utilice la página **General** del cuadro de diálogo Editor de transformación Búsqueda para seleccionar el modo de caché y el tipo de conexión, y especificar cómo administrar las filas sin entradas coincidentes.  
  
 Para obtener más información acerca de la transformación Búsqueda, vea [Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Opciones  
 **Caché completa**  
 Generey cargue el conjunto de datos de referencia en la caché antes de que se ejecute la transformación Búsqueda.  
  
 **Caché parcial**  
 Genere el conjunto de datos de referencia durante la ejecución de la transformación Búsqueda. Cargue en la caché las filas con entradas coincidentes del conjunto de datos de referencia y las que no tienen entradas coincidentes.  
  
 **Sin caché**  
 Genere el conjunto de datos de referencia durante la ejecución de la transformación Búsqueda. No se carga ningún dato en la caché.  
  
 **Administrador de conexiones de caché**  
 Configure la transformación Búsqueda para utilizar un administrador de conexiones de caché. Esta opción solo está disponible si también está seleccionada la opción Caché completa.  
  
 **Administrador de conexiones OLE DB**  
 Configure la transformación Búsqueda para utilizar un administrador de conexiones OLE DB.  
  
 **Especificar cómo administrar las filas sin entradas coincidentes**  
 Seleccione una opción para administrar las filas que no coincidan por lo menos con una entrada del conjunto de datos de referencia.  
  
 Al seleccionar **Redirigir filas a resultados no coincidentes**, las filas se redirigen a un resultado sin coincidencia y no se tratan como errores. La opción **Error** de la página **Salida de error** del cuadro de diálogo **Editor de transformación Búsqueda** no está disponible.  
  
 Al seleccionar cualquier otra opción del cuadro de lista **Especifique cómo administrar las filas sin entradas coincidentes** , las filas se tratan como errores. La opción **Error** de la página **Salida de error** está disponible.  
  
## <a name="external-resources"></a>Recursos externos  
 Entrada del blog, [Lookup cache modes](https://go.microsoft.com/fwlink/?LinkId=219518) en blogs.msdn.com  
  
## <a name="see-also"></a>Consulte también  
 [Administrador de conexiones de caché](connection-manager/cache-connection-manager.md)   
 [Editor de transformación búsqueda &#40;página de conexión&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md)   
 [Editor de transformación búsqueda &#40;página columnas&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md)   
 [Editor de transformación búsqueda &#40;página avanzadas&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md)   
 [Editor de transformación Búsqueda &#40;página Salida de error&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md)  
  
  
