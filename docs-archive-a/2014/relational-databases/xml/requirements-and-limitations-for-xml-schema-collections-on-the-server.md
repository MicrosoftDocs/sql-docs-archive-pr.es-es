---
title: Requisitos y limitaciones de las colecciones de esquemas XML en el servidor | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- identifiers [XML schema collections]
- XML schema collections [SQL Server], limitations
- substitution groups [XML in SQL Server]
- XML schema collections [SQL Server], guidelines
- lax validation
- enumeration facets [XML in SQL Server]
- decimal precision [XML in SQL Server]
- repeated XML schema collection values
- schema collections [SQL Server], limitations
- time zones [XML in SQL Server]
- precision decimals [XML in SQL Server]
- schema collections [SQL Server], guidelines
- lexical representation
ms.assetid: c2314fd5-4c6d-40cb-a128-07e532b40946
author: rothja
ms.author: jroth
ms.openlocfilehash: 85703ecb59cd7c07eed05347a77e3355dd1ecbdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745074"
---
# <a name="requirements-and-limitations-for-xml-schema-collections-on-the-server"></a>Requisitos y limitaciones de las colecciones de esquemas XML en el servidor
  La validación del lenguaje de definición de esquemas XML (XSD) tiene algunas limitaciones relativas a las columnas SQL que utilizan el tipo de datos `xml`. En la tabla siguiente se proporcionan detalles acerca de estas limitaciones, así como directrices para modificar el esquema XSD para que funcione con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Los temas de esta sección proporcionan información adicional sobre limitaciones específicas y orientación para trabajar con ellas.  
  
|Elemento|Limitación|  
|----------|----------------|  
|**minOccurs** y **maxOccurs**|Los valores de los atributos **minOccurs** y **maxOccurs** deben caber en enteros de 4 bytes. El servidor rechazará los esquemas que no cumplan esta restricción.|  
|**\<xsd:choice>**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rechaza los esquemas que tienen una partícula **\<xsd:choice>** sin elementos secundarios, a menos que el valor del atributo **minOccurs** de la partícula sea igual a cero.|  
|**\<xsd:include>**|Actualmente, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no admite este elemento. El servidor rechaza los esquemas XML que incluyen este elemento.<br /><br /> Para solucionar este problema, los esquemas XML que incluyen la directiva **\<xsd:include>** se pueden procesar previamente para copiar y combinar el contenido de todos los esquemas incluidos en un solo esquema para cargarlo en el servidor. Para obtener más información, vea [Preprocesar un esquema para combinar esquemas incluidos](preprocess-a-schema-to-merge-included-schemas.md).|  
|**\<xsd:key>** , **\<xsd:keyref>** y **\<xsd:unique>**|Actualmente, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no admite estas restricciones basadas en XSD para exigir la unicidad o establecer claves y referencias de claves. Los esquemas XML que contienen estos elementos no se pueden registrar.|  
|**\<xsd:redefine>**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no admite este elemento. Para obtener más información sobre otra manera de actualizar esquemas, vea [Elemento &#60;xsd:redefine&#62;](the-xsd-redefine-element.md).|  
|Valores de **\<xsd:simpleType>**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] solo admite una precisión de milisegundos para los tipos simples que tienen componentes de segundos distintos de `xs:time` y `xs:dateTime`, y una precisión de 100 nanosegundos para `xs:time` y `xs:dateTime`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aplica limitaciones a todas las enumeraciones de tipo simple XSD reconocidas.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no admite el uso del valor "NaN" en las declaraciones de **\<xsd:simpleType>** .<br /><br /> Para obtener más información, vea[Valores de las declaraciones de &#60;xsd:simpleType&#62;](values-for-xsd-simpletype-declarations.md).|  
|**xsi:schemaLocation** y **xsi:noNamespaceSchemaLocation**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no tiene en cuenta estos atributos si están presentes en los datos de instancias XML insertados en una columna o variable del tipo de datos `xml`.|  
|**xs:QName**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no admite los tipos derivados de **xs:QName** que utilizan un elemento de restricción de esquema XML.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no admite tipos de unión con **xs:QName** como elemento del miembro.<br /><br /> Para obtener más información, consulte [The xs:QName Type](the-xs-qname-type.md).|  
|Agregar miembros a un grupo de sustitución existente|No puede agregar miembros a un grupo de sustitución existente en una colección de esquemas XML. Un grupo de sustitución de un esquema XML está restringido en el sentido de que el elemento de encabezado y todos sus elementos miembros se deben definir en la misma instrucción {CREATE &#124; ALTER} XML SCHEMA COLLECTION.|  
|Formas canónicas y restricciones de patrón|La representación canónica de un valor no puede infringir la restricción de patrón de su tipo. Para obtener más información, consulte [Canonical Forms and Pattern Restrictions](canonical-forms-and-pattern-restrictions.md).|  
|Facetas de enumeración|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no admite los esquemas XML con tipos que tienen facetas de patrón o enumeraciones que infringen estas facetas.|  
|Longitud de faceta|Las caras de **longitud**, **minLength**y **MaxLength** se almacenan como un `long` tipo. Este tipo es de 32 bits. Por lo tanto, el intervalo de valores aceptables para estos valores es 2 <sup>^</sup> 31.|  
|Atributo de Id.|Cada componente de esquema XML puede tener un atributo de Id. en él. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] exige la unicidad de las declaraciones de **\<xsd:attribute>** de tipo **ID**, pero no almacena estos valores. El ámbito de aplicación de la unicidad es la instrucción {CREATE &#124; ALTER} XML SCHEMA COLLECTION.|  
|Tipo de Id.|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no admite elementos de tipo **xs:ID**, **xs:IDREF**ni **xs:IDREFS**. Un esquema no puede declarar elementos de este tipo, ni elementos derivados de este tipo por restricción o extensión.|  
|Espacio de nombres local|El espacio de nombres local tiene que especificarse de forma explícita para el elemento **\<xsd:any>** . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rechaza esquemas que usan una cadena vacía ("") como valor para el atributo de espacio de nombres. En su lugar, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requiere la utilización explícita de "##local" para indicar un elemento o atributo no calificado como instancia del carácter comodín.|  
|Contenido simple y de tipo mixto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no admite la restricción de un tipo mixto a un contenido simple. Para obtener más información, consulte [Mixed Type and Simple Content](mixed-type-and-simple-content.md).|  
|Tipo NOTATION|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no admite el tipo NOTATION.|  
|Condiciones de memoria insuficiente|Cuando se trabaja con colecciones de esquemas XML de gran tamaño, puede que se produzca una condición de memoria insuficiente. Para conocer soluciones para este problema, vea [Las condiciones de memoria insuficiente y las grandes colecciones de esquemas XML](large-xml-schema-collections-and-out-of-memory-conditions.md).|  
|Valores repetidos|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rechaza los esquemas en los que el atributo de bloqueo o final tiene valores repetidos como "restriction restriction" y "extension extension".|  
|Identificadores de componentes de esquema|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] limita los identificadores de los componentes de esquema a una longitud máxima de 1.000 caracteres Unicode. Tampoco se admiten los pares de caracteres complementarios en identificadores.|  
|Información de zona horaria|En [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] y versiones posteriores, la información de zona horaria es compatible con los valores `xs:date`, `xs:time` y `xs:dateTime` para la validación de esquemas XML. Con el modo de compatibilidad con versiones anteriores de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , la información de la zona horaria siempre se normaliza a la hora universal coordinada (hora del meridiano de Greenwich). En el caso de los elementos de tipo `dateTime`, el servidor convierte la hora especificada a la hora GMT mediante el valor de desplazamiento ("-05:00") y devuelve la hora GMT correspondiente.|  
|Tipos de unión|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no admite las restricciones de tipos de unión.|  
|Decimales de precisión variable|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no admite los decimales de precisión variable. El tipo **xs:decimal** representa los números decimales de precisión arbitraria. Los procesadores que mínimamente cumplan con XML deben admitir números decimales con un mínimo de `totalDigits=18`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] admite `totalDigits=38,` , pero limita a 10 los dígitos de la fracción. El servidor representa internamente todos los valores con instancias **xs:decimal** mediante el tipo numeric (38, 10) de SQL.|  
  
## <a name="in-this-section"></a>En esta sección  
  
|Tema|Descripción|  
|-----------|-----------------|  
|[Formas canónicas y restricciones de patrón](canonical-forms-and-pattern-restrictions.md)|Explica las formas canónicas y las restricciones de patrón.|  
|[Componentes comodín y validación del contenido](wildcard-components-and-content-validation.md)|Describe las limitaciones de utilizar caracteres comodín, validación lax y elementos de tipo anyType con colecciones de esquemas XML.|  
|[Elemento &#60;xsd:redefine&#62;](the-xsd-redefine-element.md)|Explica la limitación de uso del elemento \<xsd:redefine> y describe una solución alternativa.|  
|[Tipo xs:QName](the-xs-qname-type.md)|Describe la limitación relacionada con el tipo xs:QName.|  
|[Valores de las declaraciones de &#60;xsd:simpleType&#62;](values-for-xsd-simpletype-declarations.md)|Describe las restricciones que se aplican a las declaraciones de \<xsd:simpleType>.|  
|[Facetas de enumeración](enumeration-facets.md)|Describe la limitación relacionada con las facetas de enumeración.|  
|[Tipo mixto y contenido simple](mixed-type-and-simple-content.md)|Describe la limitación que se produce al restringir un tipo mixto a un contenido simple.|  
|[Las condiciones de memoria insuficiente y las grandes colecciones de esquemas XML](large-xml-schema-collections-and-out-of-memory-conditions.md)|Proporciona soluciones para la condición de falta de memoria que se produce en ocasiones con colecciones de esquemas de gran tamaño.|  
|[Modelos de contenido no determinista](non-deterministic-content-models.md)|Describe las limitaciones relacionadas con los modelos de contenido no deterministas.|  
  
## <a name="see-also"></a>Consulte también  
 [Datos XML &#40;SQL Server&#41;](xml-data-sql-server.md)   
 [Comparar XML con tipo y XML sin tipo](compare-typed-xml-to-untyped-xml.md)   
 [Conceder permisos para una colección de esquemas XML](grant-permissions-on-an-xml-schema-collection.md)   
 [Restricción de atribución de partículas exclusivas](unique-particle-attribution-constraint.md)   
 [Colecciones de esquemas XML &#40;SQL Server&#41;](xml-schema-collections-sql-server.md)  
  
  
