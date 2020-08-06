---
title: Tipos definidos por el usuario CLR | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- validation [CLR integration]
- types [CLR integration]
- UserDefined serialization format [CLR integration]
- null values [CLR integration]
- serialization
- Native serialization format [CLR integration]
- databases [CLR integration]
- building database objects [CLR integration], user-defined types
- user-defined types [CLR integration]
- common language runtime [SQL Server], user-defined types
- UDTs [CLR integration]
- database objects [CLR integration], user-defined types
- turning on CLR functionality
- customizing UDT expression return types [CLR integration]
- UDTs [CLR integration], about UDTs
- comparing UDT values
- annotations [CLR integration]
- user-defined types [CLR integration], about UDTs
- variables [CLR integration]
- invoking UDT methods
- indexes [CLR integration]
ms.assetid: 27c4889b-c543-47a8-a630-ad06804f92df
author: rothja
ms.author: jroth
ms.openlocfilehash: e4e19323eeac9e0a1148924543f71aa7de5619b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87677701"
---
# <a name="clr-user-defined-types"></a>Tipos CLR definidos por el usuario
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ofrece la posibilidad de crear objetos de base de datos programados en un ensamblado creado en Common Language Runtime (CLR) de .NET Framework. Los objetos de base de datos que pueden aprovechar el complejo modelo de programación que proporciona CLR incluyen desencadenadores, procedimientos almacenados, funciones, funciones de agregado y tipos.  
  
> [!NOTE]  
>  La capacidad para ejecutar el código CLR se encuentra desactivada (OFF) de manera predeterminada en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. El CLR se puede habilitar mediante el **sp_configure** procedimiento almacenado del sistema.  
  
 A partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , puede utilizar tipos definidos por el usuario (UDT) para extender el sistema de tipos escalares del servidor, lo que permite el almacenamiento de objetos CLR en una [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de datos. Los UDT pueden contener varios elementos y presentar varios comportamientos, diferenciándose de los tipos de datos de alias adicionales que constan de un tipo de datos del sistema de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] único.  
  
 Dado que el sistema tiene acceso a los UDT como un conjunto, su uso para los tipos de datos complejos puede causar un impacto negativo en el rendimiento. Normalmente, los datos complejos se modelan mejor mediante filas tradicionales y tablas. Los UDT en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se adaptan perfectamente a:  
  
-   Fecha, tiempo, moneda y tipos numéricos extendidos  
  
-   Aplicaciones geoespaciales  
  
-   Datos codificados o cifrados  
  
 El proceso para desarrollar los UDT en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consta de los pasos siguientes:  
  
1.  **Codificar y generar el ensamblado que define los UDT.** Los UDT se definen mediante cualquiera de los lenguajes admitidos en Common Language Runtime (CLR) de .NET Framework que generan código comprobable. Esto incluye Visual C# y Visual Basic .NET. Los datos se exponen como los campos y propiedades de una clase o estructura de .NET Framework, y los métodos de la clase o estructura definen los comportamientos.  
  
2.  **Registrar el ensamblado.** Los UDT pueden implementarse a través de la interfaz de usuario de Visual Studio en un proyecto de base de datos o mediante la instrucción CREATE ASSEMBLY de [!INCLUDE[tsql](../../includes/tsql-md.md)], que copia el ensamblado que contiene la clase o estructura en una base de datos.  
  
3.  **Crear un UDT en SQL Server.** Una vez que un ensamblado se carga en una base de datos host, use la instrucción CREATE TYPE de [!INCLUDE[tsql](../../includes/tsql-md.md)] para crear un UDT y exponer los miembros de la clase o estructura como miembros del UDT. Los UDT únicamente existen en el contexto de una base de datos única y, una vez registrados, no dependen de ninguno de los archivos externos a partir de los que se crearon.  
  
    > [!NOTE]  
    >  Antes de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], no se admitían los UDT creados a partir de los ensamblados de .NET Framework. Sin embargo, todavía puede usar los [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipos de datos de alias mediante **sp_addtype**. La sintaxis CREATE TYPE se puede usar para crear los tipos de datos definidos por el usuario nativos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y los UDT.  
  
4.  **Crear tablas, variables o parámetros con el UDT** A partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , un tipo definido por el usuario se puede utilizar como la definición de columna de una tabla, como una variable de un [!INCLUDE[tsql](../../includes/tsql-md.md)] lote o como un argumento de una [!INCLUDE[tsql](../../includes/tsql-md.md)] función o un procedimiento almacenado.  
  
## <a name="in-this-section"></a>En esta sección  
 [Crear un tipo definido por el usuario](creating-user-defined-types.md)  
 Describe cómo crear los UDT.  
  
 [Registrar tipos definidos por el usuario en SQL Server](registering-user-defined-types-in-sql-server.md)  
 Describe cómo registrar y administrar los UDT en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Trabajar con tipos definidos por el usuario en SQL Server](working-with-user-defined-types-in-sql-server.md)  
 Describe cómo crear consultas mediante los UDT.  
  
 [Acceso a tipos definidos por el usuario en ADO.NET](accessing-user-defined-types-in-ado-net.md)  
 Describe cómo trabajar con los UDT mediante el proveedor de datos de .NET Framework para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en ADO.NET.  
  
  
