---
title: Especificar funciones booleanas en consultas XPath (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], Boolean functions
- false function
- not function [SQLXML]
- true function
- Boolean functions
ms.assetid: c72cd333-9294-4d41-84f2-1748bf20e3eb
author: rothja
ms.author: jroth
ms.openlocfilehash: d230c7cd8792066732085b9ce501c0794687d17d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662753"
---
# <a name="specifying-boolean-functions-in-xpath-queries-sqlxml-40"></a>Especificar funciones booleanas en consultas XPath (SQLXML 4.0)
  Los ejemplos siguientes muestran cómo se especifican funciones booleanas en consultas XPath. Las consultas XPath de estos ejemplos se especifican en el esquema de asignación que se incluye en SampleSchema1.xml. Para obtener información acerca de este esquema de ejemplo, vea [ejemplo de esquema XSD anotado para los ejemplos de XPath &#40;SQLXML 4,0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).  
  
## <a name="examples"></a>Ejemplos  
  
## <a name="a-specify-the-not-boolean-function"></a>A. Especificar la función booleana not()  
 Esta consulta devuelve todos los **\<Customer>** elementos secundarios del nodo de contexto que no tienen **\<Order>** elementos secundarios:  
  
```  
/child::Customer[not(child::Order)]  
```  
  
 El eje `child` es el valor predeterminado. Por lo tanto, la consulta puede especificarse como:  
  
```  
/Customer[not(Order)]  
```  
  
#### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>Para probar la consulta XPath en el esquema de asignación  
  
1.  Copie el [código de esquema de ejemplo](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) y péguelo en un archivo de texto. Guarde el archivo como SampleSchema1.xml.  
  
2.  Cree la siguiente plantilla (BooleanFunctionsA.xml) y guárdela en el directorio donde esté guardado el archivo SampleSchema1.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        Customer[not(Order)]  
    </sql:xpath-query>  
    </ROOT>  
    ```  
  
     La ruta de acceso al directorio especificada para el esquema de asignación (SampleSchema1.xml) es relativa al directorio donde se guarda la plantilla. También puede especificarse una ruta de acceso absoluta como, por ejemplo:  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Cree y use el script de prueba SQLXML 4.0 (Sqlxml4test.vbs) para ejecutar la plantilla.  
  
     Para obtener más información, vea [usar ado para ejecutar consultas SQLXML 4,0](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Este es el conjunto parcial de resultados de ejecución de la plantilla:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="13" SalesPersonID="286" TerritoryID="7" AccountNumber="13" CustomerType="S" />   
  <Customer CustomerID="32" SalesPersonID="289" TerritoryID="8" AccountNumber="32" CustomerType="S" />   
  <Customer CustomerID="35" SalesPersonID="275" TerritoryID="2" AccountNumber="35" CustomerType="S" />   
  ...  
</ROOT>  
```  
  
## <a name="b-specify-the-true-and-false-boolean-functions"></a>B. Especificar las funciones booleanas true () y false ()  
 Esta consulta devuelve todos los elementos **\<Customer>** secundarios del nodo de contexto que no tienen **\<Order>** elementos secundarios. En términos relacionales, esta consulta devuelve todos los clientes que no han realizado ningún pedido.  
  
```  
/child::Customer[child::Order=false()]  
```  
  
 El eje `child` es el valor predeterminado. Por lo tanto, la consulta puede especificarse como:  
  
```  
/Customer[Order=false()]  
```  
  
 Esta consulta equivale a lo siguiente:  
  
```  
/Customer[not(Order)]  
```  
  
 La consulta siguiente devuelve todos los clientes que han realizado al menos un pedido:  
  
```  
/Customer[Order=true()]  
```  
  
 Esta consulta equivale a ésta:  
  
```  
/Customer[Order]  
```  
  
#### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>Para probar la consulta XPath en el esquema de asignación  
  
1.  Copie el [código de esquema de ejemplo](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) y péguelo en un archivo de texto. Guarde el archivo como SampleSchema1.xml.  
  
2.  Cree la siguiente plantilla (BooleanFunctionsB.xml) y guárdela en el directorio donde esté guardado el archivo SampleSchema1.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[Order=false()]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     La ruta de acceso al directorio especificada para el esquema de asignación (SampleSchema1.xml) es relativa al directorio donde se guarda la plantilla. También puede especificarse una ruta de acceso absoluta como, por ejemplo:  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Cree y use el script de prueba SQLXML 4.0 (Sqlxml4test.vbs) para ejecutar la plantilla.  
  
     Para obtener más información, vea [usar ado para ejecutar consultas SQLXML 4,0](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Este es el conjunto parcial de resultados de ejecución de la plantilla:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="13" SalesPersonID="286" TerritoryID="7" AccountNumber="13" CustomerType="S" />   
  <Customer CustomerID="32" SalesPersonID="289" TerritoryID="8" AccountNumber="32" CustomerType="S" />   
  <Customer CustomerID="35" SalesPersonID="275" TerritoryID="2" AccountNumber="35" CustomerType="S" />   
  ...  
</ROOT>  
```  
  
  
