---
title: Editor de origen de ODBC (página Administrador de conexiones) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.connection.f1
ms.assetid: e2c8dc83-6394-4d6c-9232-97e94be72431
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c8b54ce4a1c1b3fea0afb51f1cbf7447971ccab4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87747134"
---
# <a name="odbc-source-editor-connection-manager-page"></a>Editor de origen de ODBC (página Administrador de conexiones)
  Use la página **Administrador de conexiones** del cuadro de diálogo **Editor de origen de ODBC** para seleccionar el administrador de conexiones de ODBC para el origen. Esta página también permite seleccionar una tabla o vista de la base de datos.  
  
 Para obtener más información acerca del origen de ODBC, vea [ODBC Source](data-flow/odbc-source.md).  
  
## <a name="task-list"></a>Lista de tareas  
 **Para abrir la página Administrador de conexiones del Editor de origen de ODBC**  
  
-   En [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], abra el paquete [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] que tiene el origen de ODBC.  
  
-   En la pestaña **Flujo de datos** , haga doble clic en el origen de ODBC.  
  
## <a name="options"></a>Opciones  
  
### <a name="connection-manager"></a>Administrador de conexiones  
 Seleccione un administrador de conexiones ODBC existente en la lista o haga clic en **nuevo** para crear una nueva conexión. La conexión puede ser a cualquier base de datos compatible con ODBC.  
  
### <a name="new"></a>Nuevo  
 Haga clic en **Nueva**. Se abrirá el cuadro de diálogo **Configurar el administrador de conexiones ODBC** , donde puede crear un administrador de conexiones ODBC nuevo.  
  
### <a name="data-access-mode"></a>Modo de acceso a datos  
 Elija el método para la selección de datos desde el origen. Las opciones se muestran en la tabla siguiente:  
  
|Opción|Descripción|  
|------------|-----------------|  
|Nombre de la tabla|Recupera datos de una tabla o vista del origen de datos de ODBC. Cuando seleccione esta opción, seleccione un valor de la lista para lo siguiente:|  
||**Nombre de la tabla o la vista**: seleccione una tabla o vista disponible en la lista o escriba una expresión regular para identificar la tabla.|  
||Esta lista contiene solo las 1000 primeras tablas. Si la base de datos contiene más de 1000 tablas, puede escribir el principio de un nombre de tabla o usar el comodín (*) para escribir cualquier parte del nombre con el fin de mostrar la tabla o las tablas que desea usar.|  
|Comando SQL|Recupera datos del origen de datos de ODBC mediante una consulta SQL. Debe escribir la consulta con la sintaxis de la base de datos de origen con la que está trabajando. Cuando seleccione esta opción, escriba una consulta de una de las siguientes maneras:|  
||Escriba el texto de la consulta SQL en el campo de **Texto de comando SQL** .|  
||Haga clic en **Examinar** para cargar la consulta SQL desde un archivo de texto.|  
||Haga clic en **Analizar consulta** para comprobar la sintaxis del texto de la consulta.|  
  
### <a name="preview"></a>Versión preliminar  
 Haga clic en **Vista previa** para ver hasta las 200 primeras filas de los datos extraídos de la tabla o la vista seleccionada.  
  
## <a name="see-also"></a>Consulte también  
 [Propiedades personalizadas del origen ODBC](data-flow/odbc-source-custom-properties.md)   
 [Editor de origen ODBC &#40;página columnas&#41;](../../2014/integration-services/odbc-source-editor-columns-page.md)   
 [Editor de orígenes ODBC &#40;página Salida de error&#41;](../../2014/integration-services/odbc-source-editor-error-output-page.md)  
  
  
