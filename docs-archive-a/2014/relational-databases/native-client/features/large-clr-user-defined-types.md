---
title: Tipos definidos por el usuario de CLR grandes (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types
ms.assetid: b65eb61d-ccf6-49c0-98e7-9a4ef4b2f790
author: rothja
ms.author: jroth
ms.openlocfilehash: 27f0c13caea8c4aca63d78238509c6d05f1bf7bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745255"
---
# <a name="large-clr-user-defined-types"></a>Tipos definidos por el usuario de CLR grandes
  En SQL Server 2005, los tipos definidos por el usuario (UDT) en Common Language Runtime (CLR) estaban restringidos a un tamaño de 8.000 bytes. Esta restricción se soluciona en [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] y versiones posteriores. Los UDT CLR se tratan ahora de una manera similar a los tipos de objeto grandes (LOB). Es decir, los UDT con un tamaño menor o igual que 8.000 bytes se comportan de la misma manera que en SQL Server 2005, pero se admiten UDT de mayor tamaño y notifican su tamaño como "ilimitado".  
  
 Para obtener más información, vea [tipos CLR grandes definidos por el usuario &#40;OLE DB&#41;](../ole-db/large-clr-user-defined-types-ole-db.md) y [tipos CLR grandes definidos por el usuario &#40;&#41;ODBC ](../odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="use-cases"></a>Casos de uso  
 Para ODBC, la compatibilidad con UDT grandes incluye la capacidad de enviar los valores de UDT en partes como parámetros de datos en ejecución. Esto se hace mediante SQLPutData.  
  
 Para OLE DB, la compatibilidad con UDT grandes incluye la capacidad de transmitir en secuencias los valores del UDT a y desde el servidor mediante el enlace ISequentialStream.  
  
 Los UDT con un tamaño menor o igual que 8.000 se comportarán como lo hacían en SQL Server 2005. Para OLE DB, puede transmitir en secuencias todavía los UDT pequeños usando el enlace ISequentialStream.  
  
 A veces el código nativo tendrá que entender el contenido de los UDT CLR, pero no tendrá que crear instancias de los objetos administrados. Si éste es el caso, puede utilizar la serialización personalizada para convertir los valores de UDT en el servidor en un formato bien conocido para los clientes.  
  
 Para las aplicaciones que tienen código de acceso a datos existente, puede aprovechar el comportamiento de los UDT CLR en el cliente recuperando los UDT a través de API nativas y creando instancias de ellos utilizando la interoperabilidad de C++ CLI en aplicaciones de modo mixto.  
  
## <a name="see-also"></a>Consulte también  
 [Características de SQL Server Native Client](sql-server-native-client-features.md)  
  
  
