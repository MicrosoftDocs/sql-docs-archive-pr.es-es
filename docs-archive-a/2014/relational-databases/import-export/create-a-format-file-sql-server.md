---
title: Creación de archivos de formato (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- format files [SQL Server], creating
ms.assetid: f680b4a0-630f-4052-9c79-d348c1076f7b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ca9c85bfcac3380ce13ba89fff6de0b5daadbece
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662024"
---
# <a name="create-a-format-file-sql-server"></a>Crear un archivo de formato (SQL Server)
  Cuando se realiza una importación masiva de datos en una tabla de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o una exportación masiva de datos desde una tabla, se puede utilizar un archivo de formato para un sistema flexible de escribir archivos de datos que requiera poca o ninguna modificación para adaptarlos a otros formatos de datos o para leer archivos de datos de otros programas de software.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] admite dos tipos de archivos de formato: XML y no XML. El formato no XML es el formato original compatible con versiones anteriores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Por lo general, los archivos de formato XML y no XML son intercambiables. Sin embargo, es recomendable utilizar la sintaxis XML para los nuevos archivos de formato porque proporciona varias ventajas con relación a los archivos de formato no XML.  
  
> [!NOTE]  
>  La versión de la utilidad **bcp** (Bcp.exe) que se emplee para leer un archivo de formato debe ser la misma versión, o una versión posterior, a la que se use para crear el archivo de formato. Por ejemplo, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] **BCP** puede leer un archivo de formato de la versión 10,0, generado por [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] **BCP**, pero [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] **BCP** no puede leer un archivo de formato de la versión 11,0, generado por [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] **BCP**.  
  
 En este tema se describe cómo utilizar la [utilidad bcp](../../tools/bcp-utility.md) para crear un archivo de formato para una tabla determinada. El archivo de formato se basa en la opción de tipo de datos especificada ( **-n**, **-c**, **-w**o **-N**) y en los delimitadores de la vista o de la tabla.  
  
## <a name="creating-a-non-xml-format-file"></a>Crear un archivo de formato no XML  
 Si quiere usar un comando **BCP** para crear un archivo de formato, especifique el argumento **format** y use **null** en lugar de una ruta de acceso de archivo de datos. La opción **format** también requiere la opción **-f** , como:  
  
 **bcp** _table_or_view_ **format** nul **-f**_format_file_name_  
  
> [!NOTE]  
>  Para distinguir un archivo de formato no XML, se recomienda utilizar .fmt como extensión del nombre de archivo, por ejemplo, miTabla.fmt.  
  
 Para obtener más información sobre la estructura y los campos de los archivos de formato no XML, vea [Archivos de formato no XML &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
### <a name="examples"></a>Ejemplos  
 Esta sección contiene los siguientes ejemplos que muestran cómo se usan los comandos de **bcp** para crear un archivo de formato no XML:  
  
-   A. Crear un archivo de formato no XML para datos nativos  
  
-   B. Crear un archivo de formato no XML para datos de caracteres  
  
-   C. Crear un archivo de formato no XML para datos nativos Unicode  
  
-   D. Crear un archivo de formato no XML para datos de caracteres Unicode  
  
 Los ejemplos utilizan la tabla `HumanResources.Department` de la base de datos de ejemplo [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . La tabla `HumanResources.Department` tiene cuatro columnas: `DepartmentID`, `Name`, `GroupName`y `ModifiedDate`.  
  
#### <a name="a-creating-a-non-xml-format-file-for-native-data"></a>A. Crear un archivo de formato no XML para datos nativos  
 En el ejemplo siguiente se crea un archivo de formato XML, `Department-n.xml`, para la tabla [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]`HumanResources.Department` . El archivo de formato utiliza tipos de datos nativos. El contenido del archivo de formato generado se presenta después del comando.  
  
 El comando **bcp** contiene los calificadores siguientes.  
  
|Calificadores|Descripción|  
|----------------|-----------------|  
|**formatnul-f** _format_file_|Especifica el archivo de formato no XML.|  
|**-n**|Especifica tipos de datos nativos.|  
|**-T**|Especifica que la utilidad **bcp** se conecta a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con una conexión de confianza utilizando la seguridad integrada. Si no se especifica **-T** , es necesario especificar **-U** y **-P** para poder iniciar sesión correctamente.|  
  
 En el símbolo del sistema de Windows, escriba el siguiente comando `bcp` :  
  
```  
bcp AdventureWorks2012.HumanResources.Department format nul -T -n -f Department-n.fmt  
```  
  
 El archivo de formato generado, `Department-n.fmt`, contiene la siguiente información:  
  
```  
12.0  
4  
1       SQLSMALLINT   0       2       ""   1     DepartmentID                 ""  
2       SQLNCHAR      2       100     ""   2     Name                         SQL_Latin1_General_CP1_CI_AS  
3       SQLNCHAR      2       100     ""   3     GroupName                    SQL_Latin1_General_CP1_CI_AS  
4       SQLDATETIME   0       8       ""   4     ModifiedDate                 ""  
```  
  
 Para obtener más información, vea [Archivos de formato no XML &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
#### <a name="b-creating-a-non-xml-format-file-for-character-data"></a>B. Crear un archivo de formato no XML para datos de caracteres  
 En el ejemplo siguiente se crea un archivo de formato XML, `Department.fmt`, para la tabla [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]`HumanResources.Department` . El archivo de formato usa formatos de datos de caracteres y un terminador de campo no predeterminado (`,`). El contenido del archivo de formato generado se presenta después del comando.  
  
 El comando **bcp** contiene los calificadores siguientes.  
  
|Calificadores|Descripción|  
|----------------|-----------------|  
|**formatnul-f** _format_file_|Especifica un archivo de formato no XML.|  
|**-c**|Especifica los datos de caracteres.|  
|**-T**|Especifica que la utilidad **bcp** se conecta a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con una conexión de confianza utilizando la seguridad integrada. Si no se especifica **-T** , es necesario especificar **-U** y **-P** para poder iniciar sesión correctamente.|  
  
 En el símbolo del sistema de Windows, escriba el siguiente comando `bcp` :  
  
```  
bcp AdventureWorks2012.HumanResources.Department format nul -c -f Department-c.fmt -T  
```  
  
 El archivo de formato generado, `Department-c.fmt`, contiene la siguiente información:  
  
```  
12.0  
4  
1       SQLCHAR       0       7       "\t"     1     DepartmentID                 ""  
2       SQLCHAR       0       100     "\t"     2     Name                         SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       100     "\t"     3     GroupName                    SQL_Latin1_General_CP1_CI_AS  
4       SQLCHAR       0       24      "\r\n"   4     ModifiedDate                 ""  
```  
  
 Para obtener más información, vea [Archivos de formato no XML &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
#### <a name="c-creating-a-non-xml-format-file-for-unicode-native-data"></a>C. Crear un archivo de formato no XML para datos nativos Unicode  
 Para crear un archivo de formato no XML para datos nativos Unicode para la tabla `HumanResources.Department`, utilice el comando siguiente:  
  
```  
bcp AdventureWorks2012.HumanResources.Department format nul -T -N -f Department-n.fmt  
```  
  
 Para obtener más información sobre cómo usar datos nativos Unicode, vea [Usar el formato nativo Unicode para importar o exportar datos &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md).  
  
#### <a name="d-creating-a-non-xml-format-file-for-unicode-character-data"></a>D. Crear un archivo de formato no XML para datos de caracteres Unicode  
 Para crear un archivo de formato no XML para datos de caracteres Unicode para la tabla `HumanResources.Department` que usa terminadores predeterminados, use el comando siguiente:  
  
```  
bcp AdventureWorks2012.HumanResources.Department format nul -T -w -f Department-w.fmt  
```  
  
 Para obtener más información sobre cómo usar datos de caracteres Unicode, vea [Usar el formato de caracteres Unicode para importar o exportar datos &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md).  
  
## <a name="creating-an-xml-format-file"></a>Crear un archivo de formato XML  
 Si quiere usar un comando **BCP** para crear un archivo de formato, especifique el argumento **format** y use **null** en lugar de una ruta de acceso de archivo de datos. La opción **format** siempre requiere la opción **-f** y, para crear un archivo de formato XML, también debe especificar la opción **-x** , como:  
  
 **bcp** _table_or_view_ **format nul-f** _format_file_name_ **-x**  
  
> [!NOTE]  
>  Para distinguir un archivo de formato XML, se recomienda utilizar .xml como extensión de archivo, por ejemplo, miTabla.xml.  
  
 Para obtener más información sobre la estructura y los campos de los archivos de formato XML, vea [XML, archivos de formato &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
### <a name="examples"></a>Ejemplos  
 Esta sección contiene los siguientes ejemplos, en los que se muestran cómo se usan los comandos **bcp** para crear un archivo de formato XML:  
  
-   A. Crear un archivo de formato XML para datos de caracteres  
  
-   B. Crear un archivo de formato XML para datos nativos  
  
 Los ejemplos utilizan la tabla `HumanResources.Department` de la base de datos de ejemplo [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . La tabla `HumanResources.Department` tiene cuatro columnas: `DepartmentID`, `Name`, `GroupName`y `ModifiedDate`.  
  
> [!NOTE]  
>  [!INCLUDE[ssSampleDBdesc](../../includes/sssampledbdesc-md.md)]  
  
#### <a name="a-creating-an-xml-format-file-for-character-data"></a>A. Crear un archivo de formato XML para datos de caracteres  
 En el ejemplo siguiente se crea un archivo de formato XML, `Department.xml`, para la tabla [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]`HumanResources.Department` . El archivo de formato usa formatos de datos de caracteres y un terminador de campo no predeterminado (`,`). El contenido del archivo de formato generado se presenta después del comando.  
  
 El comando **bcp** contiene los calificadores siguientes.  
  
|Calificadores|Descripción|  
|----------------|-----------------|  
|**formatnul-f** _format_file_ **-x**|Especifica el archivo de formato XML.|  
|**-c**|Especifica los datos de caracteres.|  
|**-t** `,`|Especifica una coma ( **,** ) como terminador de campo.<br /><br /> Nota: Si el archivo de datos usa el terminador de campo predeterminado (`\t`), no es necesario el modificador **-t**.|  
|**-T**|Especifica que la utilidad **bcp** se conecta a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con una conexión de confianza utilizando la seguridad integrada. Si no se especifica **-T** , es necesario especificar **-U** y **-P** para poder iniciar sesión correctamente.|  
  
 En el símbolo del sistema de Windows, escriba el siguiente comando `bcp` :  
  
```  
bcp AdventureWorks2012.HumanResources.Department format nul -c -x -f Department-c..xml -t, -T  
```  
  
 El archivo de formato generado, `Department-c.xml`, contiene los elementos XML siguientes:  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>  
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="24"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="DepartmentID" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Name" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="3" NAME="GroupName" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="ModifiedDate" xsi:type="SQLDATETIME"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
 Para obtener más información sobre la sintaxis de este archivo de formato, vea [XML, archivos de formato &#40;SQL Server&#41;](xml-format-files-sql-server.md). Para obtener más información sobre los datos de caracteres, vea [Usar el formato de caracteres para importar o exportar datos &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md).  
  
#### <a name="b-creating-an-xml-format-file-for-native-data"></a>B. Crear un archivo de formato XML para datos nativos  
 En el ejemplo siguiente se crea un archivo de formato XML, `Department-n.xml`, para la tabla `HumanResources.Department` . El archivo de formato utiliza tipos de datos nativos. El contenido del archivo de formato generado se presenta después del comando.  
  
 El comando **bcp** contiene los calificadores siguientes.  
  
|Calificadores|Descripción|  
|----------------|-----------------|  
|**formatnul-f** _format_file_ **-x**|Especifica el archivo de formato XML.|  
|**-n**|Especifica tipos de datos nativos.|  
|**-T**|Especifica que la utilidad **bcp** se conecta a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con una conexión de confianza utilizando la seguridad integrada. Si no se especifica **-T** , es necesario especificar **-U** y **-P** para poder iniciar sesión correctamente.|  
  
 En el símbolo del sistema de Windows, escriba el siguiente comando `bcp` :  
  
```  
bcp AdventureWorks2012.HumanResources.Department format nul -x -f Department-n..xml -n -T  
```  
  
 El archivo de formato generado, `Department-n.xml`, contiene los elementos XML siguientes:  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="NativeFixed" LENGTH="2"/>  
  <FIELD ID="2" xsi:type="NCharPrefix" PREFIX_LENGTH="2" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="NCharPrefix" PREFIX_LENGTH="2" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="4" xsi:type="NativeFixed" LENGTH="8"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="DepartmentID" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Name" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="3" NAME="GroupName" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="ModifiedDate" xsi:type="SQLDATETIME"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
 Para obtener más información sobre la sintaxis de este archivo de formato, vea [XML, archivos de formato &#40;SQL Server&#41;](xml-format-files-sql-server.md). Para obtener más información sobre cómo usar datos nativos, vea [Usar el formato nativo para importar o exportar datos &#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md).  
  
## <a name="mapping-data-fields-to-table-columns"></a>Asignar campos de datos a columnas de tabla  
 Al igual que cuando se crea mediante **bcp**, un archivo de formato describe todas las columnas de tabla en orden. Puede modificar un archivo de formato para reorganizar u omitir filas de la tabla. Esto permite personalizar un archivo de formato en un archivo de datos cuyos campos no se asignan directamente a las columnas de la tabla. Para obtener más información, vea los temas siguientes:  
  
-   [Usar un archivo de formato para omitir una columna de tabla &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [Usar un archivo de formato para omitir un campo de datos &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [Usar un archivo de formato para asignar columnas de tabla a campos de un archivo de datos &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="see-also"></a>Consulte también  
 [bcp (utilidad)](../../tools/bcp-utility.md)   
 [Usar un archivo de formato para asignar columnas de tabla a campos de un archivo de datos &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)   
 [Usar un archivo de formato para omitir una columna de tabla &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)   
 [Usar un archivo de formato para omitir un campo de datos &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md)   
 [Archivos de formato no XML &#40;SQL Server&#41;](xml-format-files-sql-server.md)   
 [XML, archivos de formato &#40;SQL Server&#41;](xml-format-files-sql-server.md)  
  
  
