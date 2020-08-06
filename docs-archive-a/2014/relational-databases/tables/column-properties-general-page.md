---
title: Propiedades de columna (página General) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.columnproperties.general.f1
ms.assetid: a745890b-994e-4c23-8028-5c83751e60c4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 29a82df217eef719b4f0efffb3fc0c24b36a27aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87678139"
---
# <a name="column-properties-general-page"></a>Propiedades de columna (página General)
  Utilice esta página para ver propiedades de la columna seleccionada.  
  
 La información de esta página es de solo lectura. Para modificar la columna, cierre el cuadro de diálogo **Propiedades de columna** , expanda la tabla y las columnas en el Explorador de objetos, haga clic con el botón derecho en la columna y, después, haga clic en **Diseño**.  
  
## <a name="options"></a>Opciones  
 **Nombre**  
 Nombre de la columna.  
  
 **Tipo de datos**  
 Tipo de datos que puede contener la columna. Si el tipo de datos es un tipo definido por el usuario, se muestra este tipo. Si el tipo de datos no es un tipo definido por el usuario, se muestra el tipo de datos del sistema. Para obtener más información, vea [Tipos de datos &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).  
  
 **Tipo de sistema**  
 Tipo de datos que puede contener la columna. Si el tipo de datos es un tipo de datos del sistema, se muestra este tipo. Si el tipo de datos es un tipo definido por el usuario, se muestra el tipo de datos del sistema que conforma el tipo de datos definido por el usuario.  
  
 **Clave principal**  
 Indica si la columna es una clave principal. Los valores posibles son **True**o **False**.  
  
 **Permitir valores NULL**  
 Indica si la columna acepta valores NULL. Los valores posibles son **True** o **False**.  
  
 **Se calcula**  
 Indica si el valor de la columna es el resultado de una expresión calculada.  
  
 **Texto calculado**  
 Indica la instrucción utilizada para calcular el texto de la columna. Para obtener más información, vea [Specify Computed Columns in a Table](specify-computed-columns-in-a-table.md).  
  
 **Identidad**  
 Indica si la columna es la columna de identidad de la tabla. Los valores posibles son **True** o **False**.  
  
 **Inicialización de identidad**  
 Indica el valor de fila inicial de una columna de identidad.  
  
 **Incremento de identidad**  
 La propiedad **Incremento de identidad** especifica el valor que [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agrega al valor superior de identidad de fila existente cuando genera un valor de identidad para una fila que se va a insertar.  
  
 **Enlace predeterminado**  
 El valor predeterminado de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enlazado a la columna. Esta opción está en blanco si no existe ningún valor predeterminado enlazado.  
  
 **Esquema predeterminado**  
 Identifica el esquema de base de datos al que pertenece el valor predeterminado enlazado a la columna. Esta opción está en blanco si no existe ningún valor predeterminado enlazado.  
  
 **Regla**  
 Identifica la restricción de integridad de datos enlazada a la columna. Esta opción está en blanco si no existe ninguna regla enlazada.  
  
 **Esquema de la regla**  
 Muestra el esquema de base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] al que pertenece la regla enlazada a la columna referenciada. Esta opción está en blanco si no existe ninguna regla enlazada.  
  
 **Longitud**  
 Indica el número máximo de caracteres o bytes que acepta la columna.  
  
 **Intercalación**  
 Muestra la intercalación actual de la columna. Si está en blanco, la propiedad de intercalación se hereda del objeto.  
  
 **Precisión numérica**  
 Indica el número máximo de dígitos en un tipo de datos numérico de precisión fija.  
  
 **Escala numérica**  
 Indica el número de dígitos a la derecha del punto decimal en un tipo de datos numérico de precisión fija.  
  
 **Espacio de nombres del esquema XML**  
 Define el tipo de la columna XML por medio de la validación del lenguaje de definición de esquemas XML (XSD).  
  
 **Esquema del espacio de nombres del esquema XML**  
 Esquema de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] al que pertenece el espacio de nombres del esquema XML.  
  
> [!NOTE]  
>  Existen varios significados comunes pero diferentes de la palabra esquema. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utiliza esquemas para organizar objetos de base de datos. Es similar a la propiedad. XML utiliza el esquema para definir la organización de la información XML en una serie de espacios de nombres. Es una forma de agrupar código XML relacionado.  
  
 **Is Sparse**  
 Indica si la columna es una columna dispersa. Los valores posibles son **True** o **False**. Para obtener más información, vea [Usar columnas dispersas](use-sparse-columns.md).  
  
 **Es un conjunto de columnas**  
 Indica si la columna es un conjunto de columnas. Los valores posibles son **True** o **False**. Para obtener más información, vea [Usar conjuntos de columnas](use-column-sets.md).  
  
 **Estado de relleno ANSI**  
 Indica si el relleno ANSI está activado o desactivado. Para obtener más información, vea [SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql).  
  
 **Texto completo**  
 Muestra si la columna participa en consultas de texto completo.  
  
 **Semántica estadística**  
 Indica si la búsqueda semántica estadística está habilitada para la columna. Para obtener más información, vea [Búsqueda semántica &#40;SQL Server&#41;](../search/semantic-search-sql-server.md).  
  
 **No disponible para replicación**  
 Especifica si la columna está disponible o no para replicación. Los valores posibles son **True** o **False**.  
  
  
