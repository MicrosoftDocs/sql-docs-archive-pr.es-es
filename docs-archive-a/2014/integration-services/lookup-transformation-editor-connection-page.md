---
title: Editor de transformación búsqueda (página conexión) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.referencetable.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: e90d6b69-5a26-43c5-8433-5c3c9588e08c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 381378ac1aca85c6bca825033bc439ebc39fb063
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673098"
---
# <a name="lookup-transformation-editor-connection-page"></a>Editor de transformación Búsqueda (página Conexión)
  Utilice la página **Conexión** del cuadro de diálogo **Editor de transformación Búsqueda** para seleccionar un administrador de conexiones. Si selecciona un administrador de conexiones OLE DB, también selecciona una consulta, tabla o vista para generar el conjunto de datos de referencia.  
  
 Para obtener más información acerca de la transformación Búsqueda, vea [Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Opciones  
 Las opciones siguientes están disponibles al seleccionar **Caché completa** y **Administrador de conexiones de caché** en la página General del cuadro de diálogo **Editor de transformación Búsqueda** .  
  
 **Administrador de conexiones de caché**  
 Seleccione un administrador de conexiones de caché de la lista o cree una conexión haciendo clic en **Nueva**.  
  
 **Nuevo**  
 Cree una conexión mediante el cuadro de diálogo **Editor del administrador de conexiones de caché** .  
  
 Las opciones siguientes están disponibles al seleccionar **Caché completa**, **Caché parcial**o **Sin caché**, y **Administrador de conexiones OLE DB**en la página General del cuadro de diálogo **Editor de transformación Búsqueda** .  
  
 **Administrador de conexiones OLE DB**  
 Seleccione un administrador de conexiones OLE DB de la lista o cree una conexión haciendo clic en **Nueva**.  
  
 **Nuevo**  
 Cree una conexión mediante el cuadro de diálogo **Configurar el administrador de conexiones OLE DB** .  
  
 **Usar una tabla o una vista**  
 Seleccione una tabla o vista existente de la lista o cree una nueva tabla haciendo clic en **nueva**.  
  
> [!NOTE]  
>  Si especifica una instrucción SQL en la página **Avanzadas** del **Editor de transformación Búsqueda**, esa instrucción SQL invalida y reemplaza el nombre de tabla seleccionado aquí. Para obtener más información, vea [Editor de transformación Búsqueda &#40;página Avanzadas&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md).  
  
 **Nuevo**  
 Permite crear una tabla con el cuadro de diálogo **Crear tabla** .  
  
 **Usar los resultados de una consulta SQL**  
 Elija esta opción para buscar una consulta preexistente, generar una consulta nueva, comprobar la sintaxis de consulta y obtener una vista previa de los resultados de la consulta.  
  
 **Generar consulta**  
 Cree la instrucción Transact-SQL para ejecutarla mediante el **Generador de consultas**, herramienta gráfica que se usa para crear consultas examinando datos.  
  
 **Browse**  
 Utilice esta opción para examinar una consulta preexistente guardada como un archivo.  
  
 **Analizar consulta**  
 Compruebe la sintaxis de la consulta.  
  
 **Versión preliminar**  
 Obtenga una vista previa de los resultados mediante el cuadro de diálogo **Vista previa de los resultados de la consulta** . Esta opción muestra hasta 200 filas.  
  
## <a name="external-resources"></a>Recursos externos  
 Entrada del blog, [Lookup cache modes](https://go.microsoft.com/fwlink/?LinkId=219518) en blogs.msdn.com  
  
## <a name="see-also"></a>Consulte también  
 [Editor de transformación búsqueda &#40;página general&#41;](general-page-of-integration-services-designers-options.md)   
 [Editor de transformación búsqueda &#40;página columnas&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md)   
 [Editor de transformación búsqueda &#40;página avanzadas&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md)   
 [Editor de transformación búsqueda &#40;página salida de error&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md)   
 [Búsqueda aproximada, transformación](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  
