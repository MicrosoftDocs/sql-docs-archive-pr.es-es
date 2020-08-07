---
title: Instrucciones y limitaciones de diagramas XML (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updategrams [SQLXML], about updategrams
ms.assetid: b5231859-14e2-4276-bc17-db2817b6f235
author: rothja
ms.author: jroth
ms.openlocfilehash: 6e01e366edc2889691862de639f69220ac4bb439
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746186"
---
# <a name="guidelines-and-limitations-of-xml-updategrams-sqlxml-40"></a>Instrucciones y limitaciones de los diagramas de actualización XML (SQLXML 4.0)
  Recuerde lo siguiente al utilizar los diagramas de actualización XML:  
  
-   Si usa un diagrama para una operación de inserción con un solo par de **\<before>** **\<after>** bloques y, **\<before>** se puede omitir el bloque. Por el contrario, en el caso de una operación de eliminación, el **\<after>** bloque se puede omitir.  
  
-   Si usa un diagrama con varios **\<before>** **\<after>** bloques y en la **\<sync>** etiqueta, **\<before>** **\<after>** se deben especificar bloques y bloques para formar **\<before>** y **\<after>** pares.  
  
-   Las actualizaciones de un diagrama de actualización se aplican a la vista XML proporcionada por el esquema XML. Por consiguiente, para que la asignación predeterminada sea correcta debe especificar el nombre de archivo del esquema del diagrama de actualización o, si no se proporciona el nombre de archivo, los nombres de atributo y elemento deben coincidir con los nombres de columna y tabla de la base de datos.  
  
-   SQLXML 4.0 requiere que todos los valores de columna de un diagrama de actualización estén asignados explícitamente en el esquema (XDR o XSD) proporcionado para componer la vista XML de sus elementos secundarios. Este comportamiento difiere de las versiones anteriores de SQLXML, que permitían un valor de una columna no asignado en el esquema si estaba implícito como parte de la clave externa de una anotación `sql:relationship`. (Observe que este cambio no afecta a la propagación de los valores de clave principal a los elementos secundarios, que todavía se produce para SQLXML 4.0 si no se especifica ningún valor explícitamente para el elemento secundario).  
  
-   Si usa un diagrama para modificar los datos de una columna binaria (como el [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `image` tipo de datos), debe proporcionar un esquema de asignación en el que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] se debe especificar el tipo de datos (por ejemplo, `sql:datatype="image"` ) y el tipo de datos XML (por ejemplo, `dt:type="binhex"` o `dt:type="binbase64` ). Los datos de la columna binaria se deben especificar en el diagrama de actualización; el diagrama de actualización omite la anotación `sql:url-encode` especificada en el esquema de asignación.  
  
-   Cuando escribe un esquema XSD, si el valor que especifica para la anotación `sql:relation` o `sql:field` incluye un carácter especial, como un carácter de espacio en blanco (por ejemplo, en el nombre de tabla "Detalles de pedido"), este valor se debe incluir entre corchetes (por ejemplo, "[Detalles de pedido]").  
  
-   Al utilizar los diagramas de actualización, no se admiten las relaciones de cadena. Por ejemplo, si las tablas A y C están relacionadas mediante una relación de cadena que utiliza la tabla B, se producirá el error siguiente al intentar ejecutar el diagrama de actualización:  
  
    ```  
    There is an inconsistency in the schema provided.  
    ```  
  
     Aun cuando el esquema y el diagrama de actualización sean correctos y tengan un formato válido, se producirá este error si está presente una relación de cadena.  
  
-   Los diagramas de actualización no permiten el paso de datos del tipo `image` como parámetros durante las actualizaciones.  
  
-   Los tipos de objetos binarios grandes (BLOB) como `text/ntext` y las imágenes no se deben usar en el **\<before>** bloque de cuando se trabaja con diagramas, porque se incluirán para su uso en el control de simultaneidad. Esto puede producir problemas con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] debido a las limitaciones en la comparación para los tipos BLOB. Por ejemplo, la palabra clave LIKE se usa en la cláusula WHERE para comparar entre las columnas del tipo de datos `text`; sin embargo, se producirá un error en las comparaciones en el caso de los tipos BLOB donde el tamaño de los datos supere los 8 K.  
  
-   Los caracteres especiales en los datos `ntext` pueden producir problemas con SQLXML 4.0 debido a las limitaciones en la comparación para los tipos BLOB. Por ejemplo, el uso de "[Serializable]" en el **\<before>** bloque de un diagramas cuando se usa en la comprobación de simultaneidad de una columna de tipo producirá `ntext` un error con la siguiente descripción del error SQLOLEDB:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
## <a name="see-also"></a>Consulte también  
 [Consideraciones de seguridad de diagrama &#40;SQLXML 4,0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
