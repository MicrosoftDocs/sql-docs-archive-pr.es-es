---
title: 'Configuración de Motor de base de datos: FileStream | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], about FILESTREAM
ms.assetid: 641a10a1-ae52-4d26-8f1c-a032a4aeff02
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ab12b507246a3e13ac59be213813604d531d9a28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87747911"
---
# <a name="database-engine-configuration---filestream"></a>Configuración del motor de base de datos - Secuencia de archivo
  Utilice esta página para habilitar FILESTREAM para esta instalación de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. FILESTREAM integra [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] con un sistema de archivos NTFS almacenando los `varbinary(max)` datos de objetos binarios grandes (BLOB) como archivos en el sistema de archivos. [!INCLUDE[tsql](../../includes/tsql-md.md)] pueden insertar, actualizar, consultar, buscar y realizar copias de seguridad de los datos FILESTREAM. Las interfaces del sistema de archivos de Win32 proporcionan el acceso de la transmisión por secuencias a los datos.  
  
## <a name="ui-element-list"></a>Lista de elementos de la interfaz de usuario  
 **Habilitar FILESTREAM para acceso Transact-SQL**  
 Seleccione esta opción para habilitar FILESTREAM para el acceso a [!INCLUDE[tsql](../../includes/tsql-md.md)] . Este control debe comprobarse para que las otras opciones de control estén disponibles.  
  
 **Habilitar FILESTREAM para el acceso de transmisión por secuencias de E/S de archivos**  
 Seleccione esta opción para habilitar el acceso de transmisión por secuencias de Win32 para FILESTREAM.  
  
 **Nombre de recurso compartido de Windows**  
 Utilice este control para escribir el nombre del recurso compartido de Windows en el que los datos de FILESTREAM se almacenarán.  
  
 **Permitir que los clientes remotos tengan acceso de transmisión por secuencias a los datos de FILESTREAM**  
 Seleccione este control para permitir que los clientes remotos tengan acceso a estos datos de FILESTREAM en este servidor.  
  
## <a name="see-also"></a>Consulte también  
 [Habilitar y configurar FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
