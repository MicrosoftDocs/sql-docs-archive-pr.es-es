---
title: Compatibilidad con consultas distribuidas en conjuntos de filas de esquema | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- DBPROPSET_SQLSERVERSESSION property
- schema rowsets [OLE DB]
- distributed queries [SQL Server], SQL Server Native Client OLE DB provider
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- rowsets [OLE DB], schema
ms.assetid: 11354bb6-be42-4d8d-854c-42dd3dc38656
author: rothja
ms.author: jroth
ms.openlocfilehash: 48b57bbf40590f8ad5c049268f25fe66d2f94357
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669647"
---
# <a name="distributed-query-support-in-schema-rowsets"></a>Compatibilidad con consultas distribuidas en conjuntos de filas de esquema
  Para admitir [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] las consultas distribuidas, la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] interfaz **IDBSchemaRowset** del proveedor de OLE DB de Native Client devuelve metadatos en servidores vinculados.  
  
 Si la propiedad SSPROP_QUOTEDCATALOGNAMES de DBPROPSET_SQLSERVERSESSION es VARIANT_TRUE, puede especificarse un identificador entrecomillado para el nombre del catálogo (por ejemplo, "my.catalog"). Al restringir la salida del conjunto de filas de esquema por catálogo, el [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client reconoce un nombre de dos partes que contiene el nombre del servidor vinculado y del catálogo. Para los conjuntos de filas de esquema en la tabla siguiente, especifique un nombre de catálogo de dos partes como _linked_server_**.** _Catalog_ restringe la salida al catálogo aplicable del servidor vinculado con nombre.  
  
|Conjunto de filas de esquema|Restricción de catálogo|  
|-------------------|-------------------------|  
|DBSCHEMA_CATALOGS|CATALOG_NAME|  
|DBSCHEMA_COLUMNS|TABLE_CATALOG|  
|DBSCHEMA_PRIMARY_KEYS|TABLE_CATALOG|  
|DBSCHEMA_TABLES|TABLE_CATALOG|  
|DBSCHEMA_FOREIGN_KEYS|PK_TABLE_CATALOG FK_TABLE_CATALOG|  
|DBSCHEMA_INDEXES|TABLE_CATALOG|  
|DBSCHEMA_COLUMN_PRIVILEGES|TABLE_CATALOG|  
|DBSCHEMA_TABLE_PRIVILEGES|TABLE_CATALOG|  
  
> [!NOTE]  
>  Para restringir un conjunto de filas de esquema a todos los catálogos de un servidor vinculado, use la sintaxis *linked_server* (donde el separador de punto forma parte de la especificación del nombre). Esta sintaxis equivale a especificar NULL para la restricción del nombre de catálogo y también se utiliza cuando el servidor vinculado indica un origen de datos que no admite catálogos.  
  
 El [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client define el conjunto de filas de esquema LINKEDSERVERS, y devuelve una lista de OLE DB orígenes de datos registrados como servidores vinculados.  
  
## <a name="see-also"></a>Consulte también  
 [Compatibilidad de conjunto de filas de esquema &#40;OLE DB&#41;](schema-rowset-support-ole-db.md)   
 [LINKEDSERVERS Rowset &#40;OLE DB&#41;](schema-rowsets-linkedservers-rowset.md)  
  
  
