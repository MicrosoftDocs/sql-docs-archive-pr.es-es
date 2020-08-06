---
title: Usar parámetros de instrucción | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, parameters
- parameters [SQL Server Native Client], ODBC
- ODBC, parameters
- statements [ODBC], parameters
- parameter markers [ODBC]
- SQL Server Native Client ODBC driver, statements
- ODBC applications, statements
ms.assetid: 2427d886-ec6c-49d7-b0b6-0d998b64cdb9
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b7e207416e60af94efd59555980a0edff68a38b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662863"
---
# <a name="using-statement-parameters"></a>Usar parámetros de instrucciones
  Un parámetro es una variable en una instrucción SQL que puede habilitar una aplicación ODBC:  
  
-   Proporcionando de forma eficaz valores para las columnas de una tabla.  
  
-   Mejorando la interacción del usuario para construir criterios de consulta.  
  
-   Administrar datos de tipo **Text**, **ntext**e **Image** y [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipos de datos de C específicos.  
  
 Por ejemplo, una tabla **Parts** tiene columnas **denominadas**el nombre del campo, la **Descripción**y el **precio**. Para agregar una parte sin parámetros se requiere la construcción de una instrucción SQL como:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (2100, 'Drive shaft', 50.00)  
```  
  
 Aunque esta instrucción es aceptable para insertar una fila con un conjunto conocido de valores, resulta complicado cuando se requiere que una aplicación inserte varias filas. ODBC soluciona esto permitiendo que una aplicación reemplace cualquier valor de datos en una instrucción SQL mediante un creador de parámetro. Esto se indica mediante un signo de interrogación (?). En el ejemplo siguiente, tres valores de datos se reemplazan con marcadores de parámetros:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Los marcadores de parámetros se enlazan a variables de aplicación. Para insertar una nueva fila, la aplicación únicamente tiene que establecer los valores de las variables y ejecutar la instrucción. Después, el controlador recupera los valores actuales de las variables y los envía al origen de datos. Si se ejecuta la instrucción varias veces, la aplicación puede hacer que el proceso mejore al preparar la instrucción.  
  
 Cada número ordinal asignado a los parámetros de izquierda a derecha hace referencia a su marcador de parámetro. El marcador de parámetros del extremo izquierdo de una instrucción SQL tiene un valor ordinal de 1; el siguiente es el ordinal 2, etc.  
  
## <a name="in-this-section"></a>En esta sección  
  
-   [Enlazar parámetros](using-statement-parameters-binding-parameters.md)  
  
## <a name="see-also"></a>Consulte también  
 [Ejecutar consultas &#40;&#41;ODBC](executing-queries-odbc.md)  
  
  
