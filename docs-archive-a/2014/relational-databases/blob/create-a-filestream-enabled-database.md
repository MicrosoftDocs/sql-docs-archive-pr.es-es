---
title: Creación de una base de datos habilitada para FILESTREAM | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], FILESTREAM-enabled databases
ms.assetid: 0fc16356-76f7-44b8-a58b-f0b7c43694ec
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0fe6e5bc6e4f60bc0703482f3bf4d761104b3c5f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746307"
---
# <a name="create-a-filestream-enabled-database"></a>crear una base de datos habilitada para FILESTREAM
  En este tema se muestra la forma de crear una base de datos que admite FILESTREAM. Dado que FILESTREAM utiliza un tipo especial de grupo de archivos, cuando cree la base de datos, debe especificar la cláusula CONTAINS FILESTREAM para un grupo de archivos como mínimo.  
  
 Un grupo de archivos FILESTREAM puede contener más de un archivo. Para obtener un ejemplo de código en el que se muestra cómo crear un grupo de archivos FILESTREAM que contiene varios archivos, vea [CREATE DATABASE &#40;Transact-SQL de SQL Server&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).  
  
### <a name="to-create-a-filestream-enabled-database"></a>Para crear una base de datos habilitada para FILESTREAM  
  
1.  En [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], haga clic en **Nueva consulta** para mostrar el Editor de consultas.  
  
2.  Copiar el [!INCLUDE[tsql](../../includes/tsql-md.md)] código crea una base de datos habilitada para FileStream denominada Archive.  
  
    > [!NOTE]  
    >  Para este script, debe existir el directorio C:\Data.  
  
3.  Para generar la base de datos, haga clic en **Ejecutar**.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se crea una base de datos con el nombre de `Archive`. La base de datos contiene tres grupos de archivos: `PRIMARY`, `Arch1`y `FileStreamGroup1`. `PRIMARY` and `Arch1` son grupos de archivos normales que no pueden contener datos FILESTREAM. `FileStreamGroup1` es el grupo de archivos `FILESTREAM` .  
  
```sql  
CREATE DATABASE Archive   
ON  
PRIMARY ( NAME = Arch1,  
    FILENAME = 'c:\data\archdat1.mdf'),  
FILEGROUP FileStreamGroup1 CONTAINS FILESTREAM( NAME = Arch3,  
    FILENAME = 'c:\data\filestream1')  
LOG ON  ( NAME = Archlog1,  
    FILENAME = 'c:\data\archlog1.ldf')  
GO  
```  
  
 Para un grupo de archivos `FILESTREAM` , `FILENAME` hace referencia a una ruta de acceso. La ruta de acceso hasta la última carpeta debe existir y la última carpeta no debe existir. En este ejemplo, `c:\data` debe existir. Sin embargo, la subcarpeta `filestream1` no puede existir al ejecutar la instrucción `CREATE DATABASE` . Para obtener más información sobre la sintaxis, vea [CREATE DATABASE &#40;Transact-SQL de SQL Server&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).  
  
 Después de ejecutar el ejemplo anterior, aparecen un archivo filestream.hdr y una carpeta $FSLOG en la carpeta c:\Data\filestream1. El archivo filestream.hdr es un archivo de encabezado para el contenedor de FILESTREAM.  
  
> [!IMPORTANT]  
>  El archivo filestream.hdr es un archivo de sistema importante. Contiene información de encabezado de FILESTREAM. No quite ni modifique este archivo.  
  
 Para las bases de datos existentes, puede usar la instrucción [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) para agregar un grupo de archivos FILESTREAM.  
  
## <a name="see-also"></a>Consulte también  
 [CREATE DATABASE &#40;Transact-SQL de SQL Server&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
