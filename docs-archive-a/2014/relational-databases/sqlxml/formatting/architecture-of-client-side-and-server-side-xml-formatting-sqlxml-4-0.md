---
title: Arquitectura del formato XML del lado cliente y del lado servidor (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- providers [SQLXML], XML formatting architecture
- SQLOLEDB provider
- client-side XML formatting
- data providers [SQLXML], XML formatting architecture
- SQLNCLI, XML
- server-side XML formatting
- SQL Server Native Client, XML
- SQLXMLOLEDB Provider, XML formatting architecture
ms.assetid: 52440d9e-89fd-4c15-a008-a1ea99f41387
author: rothja
ms.author: jroth
ms.openlocfilehash: ae1a9c60a7a7966f4eff2a08b4557487f5aec58c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674710"
---
# <a name="architecture-of-client-side-and-server-side-xml-formatting-sqlxml-40"></a>Arquitectura de aplicación de formato XML en el cliente y en el servidor (SQLXML 4.0)
  La ilustración siguiente muestra la arquitectura del formato XML en el lado servidor.  
  
 ![Arquitectura de formato XML en el servidor.](../../../database-engine/dev-guide/media/serversidexml.gif "Arquitectura de formato XML en el servidor.")  
  
 En este ejemplo, el comando que se especifica en el cliente se envía al servidor. El servidor genera un documento XML y lo devuelve al cliente. En este caso, el servidor tiene una instancia de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Con el formato XML del lado servidor, puede utilizar el proveedor SQLXMLOLEDB o el proveedor SQLOLEDB.  El proveedor SQLXMLOLEDB utiliza Sqlxml4.dll, incluido en SQLXML 4.0. Al utilizar el proveedor SQLOLEDB, de forma predeterminada obtiene la funcionalidad SQLXML que proporciona Sqlxmlx.dll, incluida con [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows o en Microsoft Data Access Components (MDAC) 2.6 o posterior. Para usar Sqlxml4.dll con SQLOLEDB, debe establecer la propiedad versión de SQLXML en "SQLXML. 4.0" en el objeto de conexión SQLOLEDB. En cualquier caso, el servidor genera el documento XML y lo envía al cliente.  
  
> [!NOTE]  
>  Los diagramas de actualización y las consultas XPath se analizan en el cliente. Para obtener la plantilla XPath o la funcionalidad de diagrama de actualización en SQLXML 4.0, utilice Sqlxml4.dll.  
  
 La ilustración siguiente muestra la arquitectura del formato XML del lado cliente.  
  
 ![Arquitectura de formato XML en el lado cliente.](../../../database-engine/dev-guide/media/clientsidexml.gif "Arquitectura de formato XML en el lado cliente.")  
  
 En este ejemplo, el cliente utiliza el proveedor SQLXMLOLEDB. En la cadena de conexión, la propiedad del proveedor de datos debe establecerse en SQLOLEDB. (Este es el único valor aceptado en SQLXML 4,0). El comando que se ejecuta en el cliente se envía al servidor. El conjunto de filas que se genera en el servidor se envía al cliente. En el cliente se lleva a cabo el formato del documento XML a partir del conjunto de filas.  
  
 En SQLXML 4.0, se pueden utilizar como proveedores de datos [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) o el proveedor SQLOLEDB. Puede tener acceso a cualquier origen de datos. La transformación XML se puede aplicar en el cliente siempre que la consulta devuelva un único conjunto de filas.  
  
  
