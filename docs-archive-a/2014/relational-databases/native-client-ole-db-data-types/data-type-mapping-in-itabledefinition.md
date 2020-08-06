---
title: Asignación de tipos de datos en ITableDefinition | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- SQL Server Native Client OLE DB provider, data types
- ITableDefinition interface
- DBCOLUMNDESC structure
- data types [OLE DB]
- CreateTable function
- OLE DB, data types
ms.assetid: 13292d1f-c17e-4d11-bf98-3460a10cbb18
author: rothja
ms.author: jroth
ms.openlocfilehash: 2e58f61231f3e2acfdccaa52117d360a7ba261f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663457"
---
# <a name="data-type-mapping-in-itabledefinition"></a>Asignación de tipos de datos en ITableDefinition
  Al crear tablas mediante la función **ITableDefinition:: CreateTable** , el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consumidor del proveedor de OLE DB de Native Client puede especificar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipos de datos en el miembro *pwszTypeName* de la matriz DBCOLUMNDESC que se pasa. Si el consumidor especifica el tipo de datos de una columna por nombre, se omite la asignación del tipo de datos de OLE DB, representada por el miembro *wType* de la estructura DBCOLUMNDESC.  
  
 Al especificar los nuevos tipos de datos de columna con OLE DB tipos de datos que usan el miembro *wType* de la estructura DBCOLUMNDESC, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client asigna OLE DB tipos de datos de la siguiente manera.  
  
|Tipo de datos de OLE DB|SQL Server<br /><br /> tipo de datos|Información adicional|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**binary**, **varbinary**, **image** o **varbinary(max)**|El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client inspecciona el miembro *ulColumnSize* de la estructura DBCOLUMNDESC. Basándose en el valor y la versión de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instancia, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client asigna el tipo a **Image**.<br /><br /> Si el valor de *ulColumnSize* es menor que la longitud máxima de una columna de tipo de datos **binarios** , el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client inspecciona el miembro *rgPropertySets* de DBCOLUMNDESC. Si DBPROP_COL_FIXEDLENGTH es VARIANT_TRUE, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client asigna el tipo a **binario**. Si el valor de la propiedad es VARIANT_FALSE, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client asigna el tipo a **varbinary**. En cualquier caso, el miembro *ulColumnSize* de DBCOLUMNDESC determina el ancho de la columna SQL Server creada.|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime**||  
|DBTYPE_GUID|**uniqueidentifier**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**int**||  
|DBTYPE_NUMERIC|**numeric**|El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client inspecciona los miembros miembros *BPrecision* y *bScale* para determinar la precisión y la escala de la columna **numérica** .|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**char**, **varchar**, **text** o **varchar(max)**|El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client inspecciona el miembro *ulColumnSize* de la estructura DBCOLUMNDESC. En función del valor y la versión de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instancia, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client asigna el tipo a **texto**.<br /><br /> Si el valor de *ulColumnSize* es menor que la longitud máxima de una columna de tipo de datos de caracteres multibyte, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client inspecciona el miembro *rgPropertySets* de DBCOLUMNDESC. Si DBPROP_COL_FIXEDLENGTH es VARIANT_TRUE, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client asigna el tipo a **Char**. Si el valor de la propiedad es VARIANT_FALSE, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client asigna el tipo a **VARCHAR**. En cualquier caso, el miembro *ulColumnSize* de DBCOLUMNDESC determina el ancho de la columna [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creada.|  
|DBTYPE_UDT|**UDT**|La siguiente información se usa en las `DBCOLUMNDESC` estructuras de **ITableDefinition:: CreateTable** cuando se requieren columnas UDT:<br /><br /> -   *pwSzTypeName* se omite.<br />-   *rgPropertySets* debe incluir un `DBPROPSET_SQLSERVERCOLUMN` conjunto de propiedades como se describe en la sección sobre el `DBPROPSET_SQLSERVERCOLUMN` [uso de tipos definidos por el usuario](../native-client/features/using-user-defined-types.md).|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_WSTR|**nchar**, **nvarchar**, **ntext** o **nvarchar(max)**|El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client inspecciona el miembro *ulColumnSize* de la estructura DBCOLUMNDESC. Según el valor, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client asigna el tipo a **ntext**.<br /><br /> Si el valor de *ulColumnSize* es menor que la longitud máxima de una columna de tipo de datos de caracteres Unicode, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client inspecciona el miembro *rgPropertySets* de DBCOLUMNDESC. Si DBPROP_COL_FIXEDLENGTH es VARIANT_TRUE, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client asigna el tipo a **nchar**. Si el valor de la propiedad es VARIANT_FALSE, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client asigna el tipo a **nvarchar**. En cualquier caso, el miembro *ulColumnSize* de DBCOLUMNDESC determina el ancho de la columna [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creada.|  
|DBTYPE_XML|**XML**||  
  
> [!NOTE]  
>  Cuando se crea una nueva tabla, el proveedor OLE DB de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client solamente asigna los valores de enumeración del tipo de datos de OLE DB especificado en la tabla anterior. Al intentar crear una tabla con una columna de cualquier otro tipo de datos de OLE DB, se genera un error.  
  
## <a name="see-also"></a>Consulte también  
 [Tipos de datos &#40;OLE DB&#41;](data-types-ole-db.md)  
  
  
