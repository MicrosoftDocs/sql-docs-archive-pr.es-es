---
title: Restricción de atribución de partículas exclusivas | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
f1_keywords:
- unique particle attribution
helpviewer_keywords:
- schema collections [SQL Server], unique particle attribution
- XML schema collections [SQL Server], unique particle attribution
- UPA constraint rule
- unique particle attribution constraint rule
ms.assetid: 6bb879e9-a5ee-402e-94e4-fe8cec5966b0
author: rothja
ms.author: jroth
ms.openlocfilehash: 7416aa4ea14539f3bf633207768783aa439ec818
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744007"
---
# <a name="unique-particle-attribution-constraint"></a>Restricción de atribución de partículas exclusivas
  En XSD, los modelos de contenido complejos están restringidos por la regla de restricción de atribución de partículas exclusivas (UPA). Esta regla requiere que cada elemento de un documento de una instancia se corresponda sin ambigüedades exactamente con una partícula `<xsd:element>` o `<xsd:any>` en el modelo de contenido de su elemento principal. Cualquier esquema que contenga un tipo con un modelo de contenido potencialmente ambiguo se rechaza.  
  
 Las causas más comunes de ambigüedad son los caracteres comodín `<xsd:any>` y las partículas con intervalos de repetición variables, como minOccurs < maxOccurs. Por ejemplo, el siguiente modelo de contenido es ambiguo, porque un elemento <`e1`> puede corresponderse con el elemento `<xsd:element>` o el elemento `<xsd:any>`.  
  
```  
<xsd:element name="root">  
    <xsd:complexType>  
        <xsd:choice>  
            <xsd:element name="e1"/>  
            <xsd:any namespace="##any"/>  
        </xsd:choice>  
    </xsd:complexType>  
</xsd:element>  
```  
  
 El siguiente modelo de contenido también es ambiguo:  
  
```  
<xsd:element name="root">  
    <xsd:complexType>  
        <xsd:sequence>  
            <xsd:element name="e1" maxOccurs="2"/>  
            <xsd:element name="e2" minOccurs="0"/>  
            <xsd:element name="e1"/>  
        </xsd:sequence>  
    </xsd:complexType>  
</xsd:element>  
```  
  
 Aunque un documento como `<root><e1/><e2/><e1/></root>` se puede validar sin ambigüedades, este no es el caso de otro documento como `<root><e1/><e1/></root>` , ya que no está claro a qué `<xsd:element>` corresponde el segundo `<e1/>` . Aunque algunos documentos se pueden validar sin ambigüedades, el esquema se rechazará debido a la posible ambigüedad.  
  
 Tenga en cuenta que, para que un modelo de contenido sea válido, debe ser posible validar cualquier instancia sin ambigüedades sin mirar hacia delante. Considere, por ejemplo, el siguiente modelo de contenido:  
  
```  
<xsd:element name="root">  
    <xsd:complexType>  
        <xsd:choice>  
           <xsd:sequence>  
               <xsd:element name="e1"/>  
               <xsd:element name="e2"/>  
           </xsd:sequence>  
           <xsd:sequence>  
               <xsd:element name="e1"/>  
               <xsd:element name="e3"/>  
           </xsd:sequence>  
       </xsd:choice>  
    </xsd:complexType>  
</xsd:element>  
```  
  
 Para un documento como `<root><e1/><e3/></root>`, la secuencia `<e1/><e3/>` se corresponde sin ambigüedades con el segundo `<xsd:sequence>`. Sin embargo, dado que el `<xsd:element>` al que corresponde `<e1/>` no se puede determinar sin mirar hacia delante a `<e3/>`, el modelo de contenido infringe la regla de restricción UPA.  
  
## <a name="finding-more-information"></a>Buscar más información  
 El World Wide Web Consortium (W3C) publica el siguiente documento, que contiene la descripción técnica de la restricción de atribución de partículas exclusivas:  
  
 "XML Schema Part 1: Segunda edición de estructuras, recomendación editada propuesta por la W3C":  
  
-   Sección 3.8.6: Restricciones en los componentes del esquema de grupo de modelos  
  
-   Apéndice H: Análisis de la restricción de la atribución de partículas únicas (no normativa)  
  
 Para ver el documento, visite [http://www.w3.org/TR/xmlschema-1](https://go.microsoft.com/fwlink/?linkid=48881).  
  
## <a name="see-also"></a>Consulte también  
 [Colecciones de esquemas XML &#40;SQL Server&#41;](xml-schema-collections-sql-server.md)  
  
  
