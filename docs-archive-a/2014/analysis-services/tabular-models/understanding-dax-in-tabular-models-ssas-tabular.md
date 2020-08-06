---
title: Descripción de DAX en modelos tabulares (SSAS tabular) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b2693985-1bea-4861-a100-cea4761ba809
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4bf7dc2f41a1d42e8b565459c3b094479d937a91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676183"
---
# <a name="understanding-dax-in-tabular-models-ssas-tabular"></a>Descripción de DAX en modelos tabulares (SSAS tabular)
  Expresiones de análisis de datos (DAX) es el lenguaje de fórmulas empleado para crear cálculos personalizados en [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para libros de Microsoft Excel y proyectos de modelos tabulares de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Las fórmulas DAX incluyen funciones, operadores y valores para realizar cálculos avanzados sobre datos de tablas y columnas.  
  
 Si bien DAX se aplica tanto a los proyectos de modelos tabulares como a libros de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , este tema se aplica más a los proyectos de modelos tabulares creados en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Antes de leer este tema, debe tener un buen conocimiento de los modelos tabulares y del entorno de creación de proyectos de modelo tabular en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Secciones de este tema:  
  
-   [DAX en modelos tabulares](#bkmk_DAXintm)  
  
-   [Fórmulas DAX en columnas calculadas, medidas y filtros de fila](#bkmk_DAX)  
  
-   [Tipos de datos de DAX](#bkmk_DAX_datatypes)  
  
-   [Operadores DAX](#bkmk_DAX_opertors)  
  
-   [Fórmulas DAX](#bkmk_DAX_Formulas)  
  
-   [Funciones DAX](#bkmk_DAX_functions)  
  
-   [Contexto de las fórmulas DAX](#bkmk_context)  
  
-   [Fórmulas y el modelo tabular](#bkmk_RelModel)  
  
-   [Trabajar con tablas y columnas](#bkmk_tables)  
  
-   [Actualizar los resultados de fórmulas (Proceso)](#bkmk_RefreshRecalc)  
  
-   [Solucionar errores en fórmulas](#bkmk_troubleshoot)  
  
-   [Recursos adicionales](#bkmk_addional_resources)  
  
##  <a name="dax-in-tabular-models"></a><a name="bkmk_DAXintm"></a>DAX en modelos tabulares  
 Tanto en [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] como en los modelos tabulares, no hay ninguna diferencia desde el punto de vista funcional en cómo las fórmulas DAX calculan valores de sus respectivos conjuntos de datos. Sin embargo, el lugar donde se crean las fórmulas DAX en las herramientas de creación de libros y modelos es diferente, así como el lugar donde se evalúa el contexto en determinadas medidas.  
  
 En [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], las fórmulas de cálculo las crean normalmente el usuario de los libros para el análisis de Business Intelligence de autoservicio. Las columnas calculadas se crean para una tabla en la ventana de PowerPivot y las medidas se crean en tablas dinámicas o en el área de cálculo. A diferencia de los proyectos de modelos tabulares, los libros PowerPivot no proporcionan seguridad basada en roles, que pueden usar fórmulas DAX para proteger los datos.  
  
 En los proyectos de modelo tabular, las fórmulas de cálculo las crean los autores del modelo en el diseñador de modelos de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] . Aunque los valores de las columnas calculadas mediante fórmulas DAX aparecen inmediatamente en la tabla en el diseñador de modelos (a excepción de la característica de vista previa de medidas de la cuadrícula de medidas), las medidas no se calculan hasta que el usuario especifica un filtro en un cliente de informes como [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] o en tablas dinámicas en Microsoft Excel.  
  
 Si importa un libro PowerPivot en un nuevo proyecto de modelo tabular utilizando la función de importación de la plantilla de proyecto de PowerPivot, las fórmulas DAX para columnas calculadas se crearán automáticamente en el nuevo modelo tabular. Las fórmulas DAX para las medidas implícitas y explícitas en el libro se crearán automáticamente en el nuevo modelo tabular como medidas explícitas. Dado que la funcionalidad del rol y del filtro de filas seguras ya no existe en los libros PowerPivot, deberá crear al menos un rol en el nuevo modelo tabular para proporcionar a los miembros de roles acceso a los datos del modelo. Las fórmulas DAX en filtros de fila solo son necesarias si se desea proteger los datos de la tabla en el nivel de fila.  
  
##  <a name="dax-formulas-in-calculated-columns-measures-and-row-filters"></a><a name="bkmk_DAX"></a>Fórmulas DAX en columnas calculadas, medidas y filtros de fila  
 Para los modelos tabulares creados en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], las fórmulas DAX se usan en columnas calculadas, medidas y filtros de fila.  
  
### <a name="calculated-columns"></a>Columnas calculadas  
 Una columna calculada es una columna que se agrega a una tabla existente (en el diseñador de modelos), creándose después una fórmula DAX que define los valores de la columna. Puede crear fórmulas para columnas calculadas en el diseñador de modelos utilizando la barra de fórmulas.  
  
> [!NOTE]  
>  Las columnas calculadas no se admiten para los modelos que recuperan datos de un origen de datos relacional mediante el modo DirectQuery.  
  
 Cuando una columna calculada contiene una fórmula DAX válida, los valores se calculan para cada fila tan pronto como se escribe la fórmula. Los valores se almacenan en la base de datos. Por ejemplo, en una tabla de fechas, cuando se escribe la fórmula `=[Calendar Year] & " Q" & [Calendar Quarter]` en la barra de fórmulas, para calcular un valor en cada fila de la tabla se toman los valores de la columna Calendar Year (en la misma tabla de fechas), se agrega un espacio y la letra Q mayúscula, y después se agregan los valores de la columna Calendar Quarter (en la misma tabla de fechas). El resultado para cada fila de la columna calculada se calcula inmediatamente y aparece, por ejemplo, como **2010 Q1**. Los valores de columna solo se vuelven a calcular si se procesan de nuevo los datos.  
  
 Para más información, vea [Columnas calculadas &#40;SSAS tabular&#41;](ssas-calculated-columns.md).  
  
### <a name="measures"></a>Medidas  
 Las medidas son fórmulas dinámicas donde los resultados cambian según el contexto. Las medidas se usan en formatos de informe que admiten la combinación y filtrado de datos del modelo mediante varios atributos, como un informe de [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] , una tabla dinámica o un gráfico dinámico de Excel. En los proyectos de modelo tabular, las medidas las define el autor del modelo utilizando la cuadrícula de medida (y la barra de fórmulas) en el diseñador de modelos en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Una fórmula en una medida puede usar las funciones de agregación estándar creadas automáticamente mediante la característica de autosuma, como COUNT o SUM, o bien puede definir su propia fórmula mediante DAX. Al definir una fórmula para una medida en la barra de fórmulas, una característica de información sobre herramientas muestra una vista previa de cuáles serían los resultados para total en el contexto actual, pero de lo contrario no se generan los resultados inmediatamente en ninguna parte. Otros detalles de la medida también aparecen en el panel **Propiedades** .  
  
 La razón por la que no se pueden ver los resultados (filtrados) del cálculo inmediatamente es que el resultado de una medida no se puede determinar sin el contexto. Evaluar una medida requiere una aplicación cliente de informes que pueda proporcionar el contexto necesario para recuperar los datos pertinentes de cada celda y, a continuación, evaluar la expresión para cada celda. Ese cliente podría ser una tabla dinámica o un gráfico dinámico de Excel, un informe de [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] o una consulta MDX. Con independencia del cliente de informes, se ejecuta una consulta independiente para cada celda de los resultados. Es decir, cada combinación de encabezados de columna y fila de una tabla dinámica, o cada selección de segmentación de datos y filtros de un informe de [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] , genera un subconjunto de datos diferente para los que se calcula la medida. Por ejemplo, en una medida con la fórmula `Total Sales:=SUM([Sales Amount])`, cuando un usuario coloca la medida Total Sales en la ventana Values en una tabla dinámica y coloca después la columna Product Category de una tabla Product en la ventana Filters, la suma de Sales Amount se calcula y se muestra para cada categoría de producto.  
  
 A diferencia de las columnas calculadas y los filtros de fila, la sintaxis de una medida incluye el nombre de la medida antes de la fórmula. En el ejemplo que se acaba de proporcionar, el nombre **Total Sales:** precede a la fórmula. Después de haber creado una medida, el nombre y su definición aparecen en la lista de campos de la aplicación cliente de informes y, según las perspectivas y roles, están disponibles para todos los usuarios del modelo.  
  
 Para más información, vea [Medidas &#40;SSAS tabular&#41;](measures-ssas-tabular.md).  
  
### <a name="row-filters"></a>Filtros de fila  
 Los filtros de fila definen las filas de una tabla que pueden ver los miembros de un rol determinado. Los filtros de fila se pueden crear para cada tabla de un modelo mediante fórmulas DAX. Los filtros de fila se crean para un rol determinado utilizando rol el administrador de roles en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Los filtros de fila también se pueden definir para un modelo implementado mediante las propiedades de rol en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 En un filtro de fila, una fórmula DAX, que se debe evaluar como una condición Booleana TRUE/FALSE, define qué filas pueden devolver los miembros de ese rol concreto en los resultados de una consulta. Las filas no incluidas en la fórmula DAX no se podrán devolver. Por ejemplo, en el caso de la tabla Customers con la siguiente fórmula DAX, `=Customers[Country] = "USA"`, los miembros del rol Sales solo podrán ver los datos de los clientes de Estados Unidos, y sus agregados, como SUM, solo se devuelven para los clientes de Estados Unidos.  
  
 Al definir un filtro de fila mediante una fórmula de DAX, se crea un conjunto de filas permitidas. Esto no deniega el acceso a otras filas; en su lugar, no se devuelven solo como parte del conjunto de filas permitido. Otros roles pueden permitir el acceso a las filas excluidas por la fórmula de DAX. Si un usuario es miembro de otro rol y los filtros de fila de ese rol permiten el acceso a ese conjunto de filas específico, el usuario podrá ver los datos de esa fila.  
  
 Los filtros de fila se aplican a las filas especificadas y también a las filas relacionadas. Cuando una tabla tiene varias relaciones, los filtros aplican seguridad para la relación activa. Los filtros de fila se intersecarán con otros filtros de fila definidos para las tablas relacionadas.  
  
 Para obtener más información, vea [Roles &#40;SSAS tabular&#41;](roles-ssas-tabular.md).  
  
##  <a name="dax-data-types"></a><a name="bkmk_DAX_datatypes"></a>Tipos de datos de DAX  
 Puede importar datos en un modelo de varios orígenes de datos diferentes que podrían admitir tipos de datos diferentes. Al importar los datos en un modelo, se convierten a uno de los tipos de datos del modelo tabular. Cuando se usa el modelo de datos en un cálculo, los datos se convierten a un tipo de datos DAX para la duración y el resultado del cálculo. Cuando se crea una fórmula DAX, los términos usados en la fórmula determinarán automáticamente el tipo de datos de valor devuelto.  
  
 Los modelos tabulares, y DAX, admiten tipos de datos siguientes:  
  
|Tipo de datos en el modelo|Tipo de datos en DAX|Descripción|  
|------------------------|----------------------|-----------------|  
|Whole Number|Valor entero de 64 bits (ocho bytes) <sup>1, 2</sup>|Números que no tienen posiciones decimales. Los enteros pueden ser números positivos o negativos, pero deben ser números enteros comprendidos entre -9.223.372.036.854.775.808 (-2^63) y 9.223.372.036.854.775.807 (2^63-1).|  
|Decimal Number|Número real de 64 bits (ocho bytes) <sup>1, 2</sup>|Los números reales son aquellos que pueden tener posiciones decimales. Abarcan un amplio intervalo de valores:<br /><br /> Valores negativos de -1,79E +308 a -2,23E -308<br /><br /> Cero<br /><br /> Valores positivos desde 2,23E -308 hasta 1,79E + 308<br /><br /> Sin embargo, el número de dígitos significativos se limita a 17 dígitos decimales.|  
|Boolean|Boolean|Valor True o False.|  
|Texto|String|Cadena de datos de carácter Unicode. Pueden ser cadenas, números o fechas representados en un formato de texto.|  
|Date|Fecha y hora|Fechas y horas en una representación de fecha y hora aceptada.<br /><br /> Las fechas válidas son todas las fechas posteriores al 1 de marzo de 1900.|  
|Moneda|Moneda|El tipo de datos de moneda permite los valores comprendidos entre -922.337.203.685.477,5808 y 922.337.203.685.477,5807 con cuatro dígitos decimales de precisión fija.|  
|N/D|En blanco|Un tipo en blanco es un tipo de datos de DAX que representa y reemplaza los valores NULL de SQL. Un valor en blanco se puede crear con la función BLANK y se puede comprobar si es tal con la función lógica ISBLANK.|  
  
 Los modelos tabulares también incluyen el tipo de datos de tabla como entrada o salida para muchas funciones DAX. Por ejemplo, la función FILTER toma una tabla como entrada y genera otra tabla de salida que contiene solo las filas que cumplen las condiciones del filtro. Mediante la combinación de funciones de tabla con funciones de agregación, se pueden realizar cálculos complejos en conjuntos de datos definidos dinámicamente.  
  
 Como los tipos de datos suelen establecerse automáticamente, es importante entender los tipos de datos y cómo se aplican, en particular, a las fórmulas DAX. Los errores en fórmulas o los resultados inesperados, por ejemplo, suelen producirse cuando se usa un operador determinado que no se puede utilizar con un tipo de datos especificado en un argumento. por ejemplo, la fórmula `= 1 & 2`devuelve un resultado de cadena de 12. Sin embargo, la fórmula `= "1" + "2"`devuelve un resultado entero de 3.  
  
 Para obtener información detallada sobre los tipos de datos en modelos tabulares y las conversiones explícitas e implícitas de tipos de datos en DAX, vea [Tipos de datos compatibles &#40;SSAS tabular&#41;](data-types-supported-ssas-tabular.md).  
  
##  <a name="dax-operators"></a><a name="bkmk_DAX_opertors"></a>Operadores DAX  
 El lenguaje DAX usa cuatro tipos diferentes de operadores de cálculo en las fórmulas:  
  
-   Operadores de comparación para comparar valores y devolver un valor lógico TRUE\FALSE.  
  
-   Operadores aritméticos para realizar cálculos aritméticos que devuelven valores numéricos.  
  
-   Operadores de concatenación de texto para combinar dos o más cadenas de texto.  
  
-   Operadores lógicos que combinan dos o más expresiones para devolver un único resultado.  
  
 Para obtener información detallada sobre los operadores utilizados en fórmulas DAX, vea [DAX Operator Reference for PowerPivot](/dax/dax-operator-reference).  
  
##  <a name="dax-formulas"></a><a name="bkmk_DAX_Formulas"></a>Fórmulas DAX  
 Las fórmulas DAX son fundamentales para crear cálculos en columnas calculadas y medidas, y proteger los datos utilizando filtros de nivel de fila. Para crear fórmulas para columnas calculadas y medidas, utilizará la barra de fórmulas situada en la parte superior de la ventana del diseñador de modelos. Para crear fórmulas para filtros de fila, utilizará el cuadro de diálogo Administrador de roles. La información de esta sección está diseñada para iniciarse en la comprensión de los conceptos básicos de las fórmulas DAX.  
  
###  <a name="formula-basics"></a><a name="basics"></a>Conceptos básicos de las fórmulas  
 DAX permite a los autores de modelos tabulares definir cálculos personalizados en ambas tablas de modelos, como parte de columnas calculadas, y como medidas asociadas a tablas pero no apareciendo directamente en ellas. DAX también permite a los autores de modelos proteger los datos mediante la creación de cálculos que devuelven un valor booleano que define qué filas de una tabla concreta o relacionada pueden ser consultadas por los usuarios de miembro del rol asociado.  
  
 Las fórmulas DAX pueden ser muy simples o muy complejas. En la siguiente tabla se muestran algunos ejemplos de fórmulas simples que se podrían utilizar en una columna calculada.  
  
|||  
|-|-|  
|Fórmula|Descripción|  
|`=TODAY()`|Inserta la fecha de hoy en cada fila de la columna.|  
|`=3`|Inserta el valor 3 en cada fila de la columna.|  
|`=[Column1] + [Column2]`|Agrega los valores en la misma fila de [Column1] y [Column2] y coloca los resultados en la columna calculada de la misma fila.|  
  
 Ya sea simple o compleja la fórmula que se crea, pueden utilizarse los siguientes pasos para crear una fórmula:  
  
1.  Cada fórmula debe comenzar con un signo igual.  
  
2.  Puede escribir o seleccionar un nombre de función o escribir una expresión.  
  
3.  Empiece a escribir las primeras letras de la función o del nombre que quiera y Autocompletar muestra una lista de las funciones, tablas y columnas disponibles. Presione la tecla TAB para agregar un elemento de la lista Autocompletar a la fórmula.  
  
     También puede hacer clic en el botón **Fx** para mostrar una lista de funciones disponibles. Para seleccionar una función de la lista desplegable, use las teclas de dirección para resaltar el elemento y haga clic en **Aceptar** para agregar la función a la fórmula.  
  
4.  Proporcione los argumentos a la función; para ello, selecciónelos en una lista desplegable de posibles tablas y columnas, o escriba valores.  
  
5.  Compruebe si hay errores de sintaxis: asegúrese de que todos los paréntesis están cerrados y que se hace referencia correctamente a las columnas, las tablas y los valores.  
  
6.  Presione ENTRAR para aceptar la fórmula.  
  
> [!NOTE]  
>  En una columna calculada, en cuanto se acepta y se valida la fórmula, la columna se rellena con valores. En una medida, al presionar ENTRAR se guarda la definición de la medida en la cuadrícula de medidas con la tabla. Si una fórmula no es válida, se mostrará un error.  
  
 En este ejemplo, examinaremos una fórmula más compleja en una medida denominada Days in Current Quarter:  
  
```  
Days in Current Quarter:=COUNTROWS( DATESBETWEEN( 'Date'[Date], STARTOFQUARTER( LASTDATE('Date'[Date])), ENDOFQUARTER('Date'[Date])))  
```  
  
 Esta medida se utiliza para crear una relación de comparación entre un período incompleto y el período anterior. La fórmula debe tener en cuenta la parte del período que ha transcurrido y compararla con la misma parte del período anterior. En este caso, [Días del trimestre actual hasta la fecha]/[Días del trimestre actual] da como resultado la parte transcurrida del período actual.  
  
 Esta fórmula contiene los elementos siguientes:  
  
|Elemento de la fórmula|Descripción|  
|---------------------|-----------------|  
|`Days in Current Quarter:=`|El nombre de la medida.|  
|`=`|El signo igual (=) comienza la fórmula.|  
|`COUNTROWS`|La [función COUNTROWS &#40;DAX&#41;](/dax/countrows-function-dax) cuenta el número de filas de la tabla Date|  
|`()`|El paréntesis de apertura y cierre especifica argumentos.|  
|`DATESBETWEEN`|La función DATESBETWEEN devuelve las fechas entre la última fecha para cada valor de la columna Date en la tabla Date.|  
|`'Date'`|Especifica la tabla Date. Las tablas están entre comillas simples.|  
|`[Date]`|Especifica la columna Date en la tabla de fechas. Las columnas están entre corchetes.|  
|`,`||  
|`STARTOFQUARTER`|La función STARTOFQUARTER devuelve la fecha de inicio del trimestre.|  
|`LASTDATE`|La función LASTDATE devuelve la última fecha del trimestre.|  
|`'Date'`|Especifica la tabla Date.|  
|`[Date]`|Especifica la columna Date en la tabla de fechas.|  
|`,`||  
|`ENDOFQUARTER`|La función ENDOFQUARTER|  
|`'Date'`|Especifica la tabla Date.|  
|`[Date]`|Especifica la columna Date en la tabla de fechas.|  
  
#### <a name="using-formula-autocomplete"></a>Usar la función Autocompletar fórmula  
 Tanto la barra de fórmulas en el diseñador de modelos como la ventana Filtros de fila de la fórmula en el cuadro de diálogo Administrador de roles proporcionan una característica Autocompletar. La función Autocompletar ayuda a escribir una sintaxis de fórmula válida proporcionando las opciones para cada elemento de la fórmula.  
  
-   Puede usar la función Autocompletar fórmula en medio de una fórmula existente con funciones anidadas. El texto situado inmediatamente antes del punto de inserción se usa para mostrar los valores de la lista desplegable, mientras que todo el texto situado después del punto de inserción se mantiene inalterado.  
  
-   La función Autocompletar no agrega el paréntesis de cierre de las funciones, ni hace coincidir automáticamente los paréntesis. Debe asegurarse de que cada función sea correcta sintácticamente ya que, de lo contrario, no podrá guardar o usar la fórmula.  
  
#### <a name="using-multiple-functions-in-a-formula"></a>Usar varias funciones en una fórmula  
 Las funciones se pueden anidar, es decir, puede usar los resultados de una función como argumento de otra función. Puede anidar hasta 64 niveles de funciones en columnas calculadas. Sin embargo, el anidamiento puede dificultar la creación de fórmulas o la solución de sus problemas.  
  
 Muchas funciones están diseñadas para usarse exclusivamente como funciones anidadas. Estas funciones devuelven una tabla, que no se puede guardar directamente como un resultado, pero que se debe proporcionar como entrada de una función de tabla. Por ejemplo, las funciones SUMX, AVERAGEX y MINX requieren una tabla como primer argumento.  
  
> [!NOTE]  
>  El anidamiento de funciones está sujeto a algunas limitaciones dentro de las medidas para asegurar que los numerosos cálculos requeridos por las dependencias entre columnas no afecten al rendimiento.  
  
##  <a name="dax-functions"></a><a name="bkmk_DAX_functions"></a>Funciones DAX  
 En esta sección se proporciona información general de los *tipos* de funciones admitidos en DAX. Para obtener información detallada, consulte [Referencia de funciones DAX](/dax/dax-function-reference).  
  
 DAX proporciona una variedad de funciones que se pueden usar para realizar cálculos utilizando fechas y horas, crear valores condicionales, trabajar con cadenas y realizar búsquedas basadas en relaciones, y la capacidad para iterar en una tabla con el fin de realizar cálculos recursivos. Si conoce las fórmulas de Excel, muchas de estas funciones le parecerán muy similares; sin embargo, las fórmulas DAX son diferentes en los siguientes aspectos importantes:  
  
-   Una función de DAX siempre hace referencia a una columna completa o una tabla. Si solo desea usar valores concretos de una tabla o columna, puede agregar filtros a la fórmula.  
  
-   Si necesita personalizar los cálculos fila a fila, DAX dispone de funciones que permiten usar el valor de la fila actual o un valor relacionado como un tipo de parámetro, para realizar cálculos que varían según el contexto. Para entender cómo funcionan estas funciones, vea el contexto en fórmulas DAX más adelante en este tema.  
  
-   DAX incluye muchas funciones que devuelven una tabla, en lugar de un valor. La tabla no se muestra en un cliente del informes, sino que se utiliza para proporcionar la entrada a otras funciones. Por ejemplo, puede recuperar una tabla y, a continuación, contar los valores distintos que contiene, o calcular sumas dinámicas en tablas o columnas filtradas.  
  
-   Las funciones DAX incluyen una serie de funciones de *inteligencia de tiempo* . Estas funciones le permiten definir o seleccionar rangos de fechas y realizar cálculos dinámicos basados en dichas fechas o rangos. Por ejemplo, puede comparar sumas en períodos paralelos.  
  
### <a name="date-and-time-functions"></a>Funciones de fecha y hora  
 Las funciones de fecha y hora en DAX son similares a las funciones de fecha y hora en Microsoft Excel. Sin embargo, las funciones de DAX se basan en los tipos de datos `datetime` usados por Microsoft SQL Server. Para obtener más información, vea [funciones de fecha y hora &#40;&#41;Dax ](/dax/date-and-time-functions-dax).  
  
### <a name="filter-functions"></a>Funciones de filtro  
 Las funciones de filtro de DAX devuelven tipos de datos específicos, valores de búsqueda en tablas relacionadas, además de la capacidad de filtrar por valores relacionados. Las funciones de búsqueda usan tablas y relaciones, como una base de datos. Las funciones de filtrado permiten manipular el contexto de los datos para crear cálculos dinámicos. Para obtener más información, vea [funciones de filtro &#40;&#41;de Dax ](/dax/filter-functions-dax).  
  
### <a name="information-functions"></a>Funciones de información  
 Una función de información examina la celda o fila que se proporciona como argumento e indica si el valor coincide con el tipo esperado. Por ejemplo, la función ISERROR devuelve TRUE si el valor al que se hace referencia contiene un error. Para obtener más información, vea [funciones de información &#40;&#41;de Dax ](/dax/information-functions-dax).  
  
### <a name="logical-functions"></a>Funciones lógicas  
 Las funciones lógicas actúan sobre una expresión para devolver información acerca de los valores de la expresión. Por ejemplo, la función TRUE permite saber si una expresión que se está evaluando devuelve un valor TRUE. Para obtener más información, vea [funciones lógicas &#40;&#41;de Dax ](/dax/logical-functions-dax).  
  
### <a name="mathematical-and-trigonometric-functions"></a>Funciones matemáticas y trigonométricas  
 Las funciones matemáticas en DAX son muy parecidas a las funciones matemáticas y trigonométricas de Excel. Existen pequeñas diferencias en los tipos de datos numéricos usados por funciones de DAX. Para obtener más información, vea [funciones matemáticas y trigonométricas &#40;&#41;de Dax ](/dax/math-and-trig-functions-dax).  
  
### <a name="statistical-functions"></a>Funciones estadísticas  
 DAX proporciona funciones estadísticas que realizan agregaciones. Además de crear sumas y medias, o buscar valores máximos y mínimos, en DAX también puede filtrar una columna antes de agregar o crear agregaciones basadas en tablas relacionadas. Para obtener más información, vea [funciones estadísticas &#40;&#41;de Dax ](/dax/statistical-functions-dax).  
  
### <a name="text-functions"></a>Funciones de texto  
 Las funciones de texto de DAX son muy similares a sus homólogas en Excel. Puede devolver parte de una cadena, buscar texto dentro de una cadena o concatenar valores de una cadena. DAX también proporciona funciones para controlar los formatos para las fechas, horas y números. Para obtener más información, vea [funciones de texto &#40;&#41;de Dax ](/dax/text-functions-dax).  
  
### <a name="time-intelligence-functions"></a>Funciones de inteligencia de tiempo  
 Las funciones de inteligencia de tiempo proporcionadas en DAX le permiten crear cálculos que usan el conocimiento integrado acerca de calendarios y fechas. El uso de intervalos de fecha y de hora en combinación con agregaciones o cálculos permite crear comparaciones significativas a lo largo de períodos de tiempo comparables relativos a ventas, inventarios, etc. Para obtener más información, vea [funciones de inteligencia de tiempo &#40;&#41;de Dax ](/dax/time-intelligence-functions-dax).  
  
###  <a name="table-valued-functions"></a><a name="bkmk_TableFunc"></a>Funciones con valores de tabla  
 Hay funciones DAX que generan tablas de salida, usan tablas como entrada, o ambas acciones. Dado que una tabla puede tener una columna única, las funciones con valores de tabla también usan columnas únicas como entradas. La comprensión del funcionamiento de estas funciones con valores de tabla es importante para sacar el mayor rendimiento posible de las fórmulas de DAX. DAX incluye los siguientes tipos de funciones con valores de tabla:  
  
 **Funciones de filtro** Devuelven una columna, tabla o valores relacionados con la fila actual.  
  
 **Funciones de agregación** Agregan cualquier expresión a las filas de una tabla.  
  
 **Funciones de inteligencia de tiempo** Devuelven una tabla de fechas o usan una tabla de fechas para calcular una agregación.  
  
##  <a name="context-in-dax-formulas"></a><a name="bkmk_context"></a>Contexto en fórmulas DAX  
 El*contexto* es un concepto importante que hay que entender cuando se crean fórmulas con DAX. El contexto es lo que permite realizar análisis dinámicos, ya que los resultados de una fórmula cambian para reflejar la selección de fila o celda actual, y también los datos relacionados. Entender lo que es el contexto y usarlo eficazmente es esencial para generar análisis dinámicos y muy eficaces, y para solucionar los posibles problemas de las fórmulas.  
  
 Las fórmulas de modelos tabulares se pueden evaluar en un contexto diferente, dependiendo de otros elementos de diseño:  
  
-   Filtros aplicados en una Tabla dinámica o informe  
  
-   Filtros definidos dentro de una fórmula  
  
-   Relaciones especificadas utilizando funciones especiales dentro de una fórmula  
  
 Hay diferentes tipos de contexto: *contexto de fila*, *contexto de consulta*y *contexto de filtro*.  
  
###  <a name="row-context"></a><a name="bkmk_row_context"></a>Contexto de fila  
 El *contexto de fila* se puede considerar como "la fila actual". Si crea una fórmula en una columna calculada, el contexto de la fila para esa fórmula incluye los valores de todas las columnas en la fila actual. Si la tabla se relaciona con otra tabla, el contenido también incluye todos los valores de la otra tabla que están relacionados con la fila actual.  
  
 Por ejemplo, suponga que crea una columna calculada `=[Freight] + [Tax]`que suma los valores de dos columnas, Freight y Tax, de la misma tabla. Esta fórmula obtiene automáticamente solo los valores de la fila actual en las columnas especificadas.  
  
 El contexto de fila también sigue cualquier relación definida entre las tablas, incluidas las relaciones definidas dentro de una columna calculada utilizando fórmulas DAX, para determinar qué filas de las tablas relacionadas están asociadas a la fila actual.  
  
 Por ejemplo, la fórmula siguiente utiliza la función RELATED para capturar un valor de impuesto de una tabla relacionada, en función de la región a la que se envió el pedido. El valor del impuesto se determina utilizando el valor para la región en la tabla actual, para ello, se busca la región en la tabla relacionada y, posteriormente, se obtiene la tasa impositiva para esa región de la tabla relacionada.  
  
```  
= [Freight] + RELATED('Region'[TaxRate])  
```  
  
 Esta fórmula obtiene la tasa impositiva para la región actual de la tabla de regiones y la agrega al valor de la columna Freight. En las fórmulas de DAX, no necesita conocer o especificar la relación específica que conecta las tablas.  
  
#### <a name="multiple-row-context"></a>Contexto de varias filas  
 DAX incluye funciones que iteran los cálculos sobre una tabla. Estas funciones pueden tener varias filas actuales, cada una con su propio contexto de fila.  Básicamente, estas funciones permiten crear fórmulas que realizan operaciones sobre un bucle interno y externo de forma recursiva.  
  
 Por ejemplo, suponga que un modelo contiene una tabla **Products** y una tabla **Sales** . Es posible que los usuarios deseen pasar por la tabla de ventas completa, la cual está llena de transacciones que implican a varios productos, y encontrar la cantidad más grande que se haya pedido para cada producto en cualquiera de las transacciones.  
  
 Con DAX puede compilar una fórmula única que devuelve el valor correcto y los resultados se actualizan automáticamente cada vez que un usuario agrega datos a las tablas.  
  
```  
=MAXX(FILTER(Sales,[ProdKey]=EARLIER([ProdKey])),Sales[OrderQty])  
```  
  
 Para obtener un tutorial detallado de esta fórmula, vea la [función anterior](/dax/earlier-function-dax).  
  
 En resumen, la función EARLIER almacena el contexto de fila de la operación anterior a la operación actual. En todo momento, la función almacena en memoria dos conjuntos de contexto: un conjunto de contexto representa la fila actual para el bucle interno de la fórmula y el otro conjunto de contexto representa la fila actual para el bucle externo de la fórmula. DAX alimenta automáticamente los valores entre los dos bucles de forma que puede crear agregados complejos.  
  
####  <a name="query-context"></a><a name="bkmk_query_context"></a>Contexto de la consulta  
 *Contexto de la consulta* hace referencia al subconjunto de datos que se recuperan implícitamente para una fórmula. Cuando un usuario coloca una medida u otro campo de valor en una tabla dinámica o en un informe basado en un modelo tabular, el motor examina los encabezados de columna y fila, la segmentación de datos y los filtros de informe para determinar el contexto. A continuación, se ejecutan las consultas necesarias en el origen de datos para obtener el subconjunto de datos correcto, se realizan los cálculos definidos por la fórmula y, a continuación, se rellena cada celda de la tabla dinámica o informe. El conjunto de datos que se recupera es el contexto de la consulta para cada celda.  
  
> [!WARNING]  
>  En el caso de un modelo en modo DirectQuery, el contexto se evalúa y, a continuación, se establecen las operaciones para recuperar el subconjunto correcto de datos y los resultados del cálculo se traducen a instrucciones SQL. Estas instrucciones se ejecutan directamente en el almacén de datos relacional. Por consiguiente, aunque el método para obtener los datos y calcular los resultados es diferente, el contexto no cambia.  
  
 Dado que el contexto cambia dependiendo de dónde se coloca la fórmula, los resultados de la fórmula también pueden cambiar.  
  
 Por ejemplo, suponga que crea una fórmula que suma los valores de la columna **Profit** de la tabla **Sales** : `=SUM('Sales'[Profit])`.  Si utiliza esta fórmula en una columna calculada dentro de la tabla **Sales** , los resultados para la fórmula serán los mismos que para la tabla completa, porque el contexto de la consulta para la fórmula siempre es el conjunto de datos completo de la tabla **Sales** . Los resultados reflejarán beneficios en todas las regiones, todos los productos, todos los años, etc.  
  
 Sin embargo, los usuarios normalmente no desean ver los mismos resultados cientos de veces, pero desean obtener la ganancia correspondiente a un año determinado, un país determinado, un producto determinado o alguna combinación de estos y, posteriormente, obtener un total general.  
  
 En una tabla dinámica, se puede cambiar el contexto agregando o quitando encabezados de columna y de fila y agregando o quitando segmentaciones de datos. Cada vez que los usuarios agregan encabezados de columna o de fila a la tabla dinámica, cambian el contexto de la consulta en el que se evalúa la medida. Las operaciones de segmentación de datos y filtrado también afectan al contexto. Por consiguiente, la misma fórmula, que se utiliza en una medida, se evalúa en un *contexto de la consulta* diferente para cada celda.  
  
####  <a name="filter-context"></a><a name="bkmk_filter_context"></a>Contexto de filtro  
 El*contexto de filtro* es el conjunto de valores permitido en cada columna o en los valores recuperados de una tabla relacionada. Los filtros se pueden aplicar a la columna en el diseñador o en el nivel de presentación (informes y tablas dinámicas). Las expresiones de filtro también pueden definir explícitamente filtros dentro de la fórmula.  
  
 El contexto del filtro se agrega al especificar las restricciones de filtro en el conjunto de valores permitido en una columna o tabla, utilizando los argumentos para una fórmula. El contexto del filtro se aplica sobre otros contextos, como el contexto de la fila o el de la consulta.  
  
 En los modelos tabulares hay muchas maneras de crear el contexto de filtro. En el contexto de clientes que pueden consumir el modelo, como los informes [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] , los usuarios pueden crear filtros sobre la marcha si se agrega segmentación de datos o filtros de informe en los encabezados de columna y fila. También puede especificar directamente las expresiones de filtro dentro de la fórmula, para especificar valores relacionados, filtrar las tablas que se usan como entradas u obtener dinámicamente el contexto de los valores utilizados en los cálculos. También puede borrar por completo o de forma selectiva los filtros en columnas específicas. Esto resulta muy útil al crear fórmulas que calculan totales generales.  
  
 Para obtener más información sobre cómo crear filtros dentro de las fórmulas, vea la [función Filter](/dax/filter-function-dax).  
  
 Para obtener un ejemplo de cómo se pueden borrar los filtros para crear totales generales, vea la [función All](/dax/all-function-dax).  
  
 Para obtener ejemplos de Cómo borrar y aplicar los filtros de forma selectiva en las fórmulas, vea la [función ALLEXCEPT](/dax/allexcept-function-dax).  
  
####  <a name="determining-context-in-formulas"></a><a name="bkmk_determine_context"></a> Determinar el contexto de las fórmulas  
 Al crear una fórmula DAX, se comprueba primero que la fórmula tiene una sintaxis válida y después se prueba para asegurarse de que los nombres de las columnas y tablas incluidas en la fórmula se pueden encontrar en el contexto actual. Si no se puede encontrar alguna columna o tabla especificada por la fórmula, se devuelve un error.  
  
 El contexto durante la validación (y las operaciones de recálculo) se determina, según se describió en las secciones anteriores, utilizando las tablas disponibles en el modelo, cualquier relación entre las tablas y cualquier filtro que se haya aplicado.  
  
 Por ejemplo, si ha importado recientemente algunos datos en una tabla nueva y no está relacionada con ninguna otra tabla (y no ha aplicado ningún filtro), el *contexto actual* será todo el conjunto de columnas de la tabla. Si la tabla está vinculada mediante relaciones con otras tablas, el contexto actual incluirá las tablas relacionadas. Si agrega una columna de la tabla a un informe que tiene segmentación de datos y quizá algún filtro de informe, el contexto de la fórmula es el subconjunto de datos de cada celda del informe.  
  
 El contexto es un concepto eficaz que también puede dificultar la solución de los problemas con las fórmulas. Se recomienda comenzar con fórmulas y relaciones simples para ver cómo funciona el contexto. La siguiente sección proporciona algunos ejemplos de cómo las fórmulas utilizan tipos diferentes de contexto para devolver resultados de forma dinámica.  
  
##### <a name="examples-of-context-in-formulas"></a>Ejemplos de contexto en fórmulas  
  
1.  La función [RELATED Function](/dax/related-function-dax) expande el contexto de la fila actual para incluir los valores en una columna relacionada. Esto le permite realizar búsquedas. El ejemplo de este tema muestra la interacción del filtrado con el contexto de la fila.  
  
2.  La función de [función Filter](/dax/filter-function-dax) permite especificar las filas que se van a incluir en el contexto actual. Los ejemplos de este tema también muestran cómo incrustar los filtros dentro de otras funciones que realizan los agregados.  
  
3.  La función [All](/dax/all-function-dax) establece el contexto dentro de una fórmula. Puede utilizarlo para invalidar los filtros que se aplican como resultado del contexto de la consulta.  
  
4.  La función [ALLEXCEPT](/dax/allexcept-function-dax) permite quitar todos los filtros excepto uno que especifique. Ambos temas incluyen ejemplos que le guían en el proceso de generación de fórmulas y le ayudan a entender los contextos complejos.  
  
5.  La [función anterior](/dax/earlier-function-dax) y las funciones de [función más tempranas](/dax/earliest-function-dax) permiten recorrer las tablas mediante cálculos, al tiempo que se hace referencia a un valor de un bucle interno. Si conoce el concepto de recursividad y los bucles internos y externos, apreciará la eficacia que proporcionan las funciones EARLIER y EARLIEST. Si estos conceptos son nuevos para usted, debería seguir los pasos del ejemplo con atención para ver cómo se utilizan los contextos internos y externos en los cálculos.  
  
##  <a name="formulas-and-the-tabular-model"></a><a name="bkmk_RelModel"></a>Fórmulas y el modelo tabular  
 El diseñador de modelos de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]es un área donde se puede trabajar con varias tablas de datos y conectar las tablas en un modelo tabular. En este modelo, las tablas se unen mediante relaciones en columnas con valores comunes (claves). El modelo tabular permite vincular valores a columnas de otras tablas y crear cálculos más interesantes. Al igual que en una base de datos relacional, puede conectar muchos niveles de tablas relacionadas y usar columnas de cualquiera de las tablas en los resultados.  
  
 Por ejemplo, se puede vincular una tabla de ventas, una tabla de productos y una tabla de categorías de producto y los usuarios pueden utilizar diversas combinaciones de las columnas en tablas dinámicas e informes. Los campos relacionados se pueden utilizar para filtrar las tablas conectadas o para crear cálculos en los subconjuntos. (Si no está familiarizado con las bases de datos relacionales y el trabajo con tablas y combinaciones, vea [Relaciones &#40;SSAS tabular&#41;](relationships-ssas-tabular.md)).  
  
 Los modelos tabulares admiten varias relaciones entre tablas. Para evitar confusiones o malos resultados, solo se designa una relación cada vez como relación activa, pero se puede cambiar la relación activa como sea necesario para recorrer diferentes conexiones de los datos en los cálculos. La [función USERELATIONSHIP &#40;&#41;Dax](/dax/userelationship-function-dax) se puede usar para especificar una o más relaciones que se van a usar en un cálculo específico.  
  
 En un modelo tabular, se deben observar estas reglas de diseño de fórmulas:  
  
-   Cuando las tablas están conectadas mediante una relación, debe asegurarse de que las dos columnas utilizadas como claves tienen valores que coinciden. Sin embargo, dado que no se aplica la integridad referencial, es posible tener valores no coincidentes en una columna de clave y aún crear una relación. Si ocurre esto, debe ser consciente de que la presencia de espacios en blanco o valores no coincidentes podría afectar a los resultados de las fórmulas.  
  
-   Al vincular tablas en el modelo mediante relaciones, amplía el ámbito, o *contexto*, en el que se evalúan las fórmulas. Los cambios del contexto como resultado de la incorporación de nuevas tablas, nuevas relaciones o de cambios en la relación activa pueden hacer que los resultados cambien de forma imprevista. Para obtener más información, vea [Contexto de las fórmulas DAX](#bkmk_context) más adelante en este tema.  
  
##  <a name="working-with-tables-and-columns"></a><a name="bkmk_tables"></a>Trabajar con tablas y columnas  
 Las tablas en los modelos tabulares son similares a las de Excel, pero diferentes en la forma en que trabajan con datos y con fórmulas:  
  
-   Las fórmulas solo funcionan con tablas y columnas, pero no con celdas individuales, referencias a rangos ni matrices.  
  
-   Las fórmulas pueden usar relaciones para obtener valores de las tablas relacionadas. Los valores que se recuperan siempre se relacionan con el valor de fila actual.  
  
-   No puede tener datos irregulares o "desiguales", como puede haber en una hoja de cálculo de Excel. Cada fila de una tabla debe contener el mismo número de columnas. Sin embargo, puede tener valores vacíos en algunas columnas. Las tablas de datos de Excel y de los modelos tabulares no son intercambiables.  
  
-   Debido a que se establece un tipo de datos para cada columna, cada valor de esa columna debe ser del mismo tipo.  
  
### <a name="referring-to-tables-and-columns-in-formulas"></a>Hacer referencia a tablas y columnas en fórmulas  
 Puede hacer referencia a cualquier tabla y columna mediante el nombre. Por ejemplo, en la siguiente fórmula se muestra cómo hacer referencia a las columnas de dos tablas utilizando el nombre *completo* :  
  
```  
=SUM('New Sales'[Amount]) + SUM('Past Sales'[Amount])  
```  
  
 Al evaluar una fórmula, el diseñador de modelos comprueba primero la sintaxis general y, a continuación, compara los nombres de las columnas y las tablas proporcionadas con las posibles columnas y las tablas del contexto actual. Si el nombre es ambiguo o si no se puede encontrar la columna o tabla, obtendrá un error en su fórmula (una #cadena ERROR en lugar de un valor de datos en las celdas donde el error se produce). Para obtener más información sobre los requisitos de nomenclatura para las tablas, columnas y otros objetos, vea "requisitos de nomenclatura" en [especificación de sintaxis de Dax para PowerPivot](/dax/dax-syntax-reference).  
  
### <a name="table-relationships"></a>Relaciones de tabla  
 La creación de relaciones entre tablas ofrece la posibilidad de buscar datos en otra tabla y usar valores relacionados para realizar cálculos complejos. Por ejemplo, puede utilizar una columna calculada para buscar todos los registros de envío relacionados con el distribuidor actual y, a continuación, sumar los costos del envío para cada uno. En muchos casos, sin embargo, puede no ser necesaria una relación. Puede usar la función LOOKUPVALUE en una fórmula para devolver el valor de *result_columnName* de la fila que cumple los criterios especificados en los parámetros *search_column* y *search_value* .  
  
 Muchas funciones de DAX requieren que exista una relación entre las tablas, o entre varias tablas, para localizar las columnas a las que se ha hecho referencia y devolver resultados que tengan sentido. Otras funciones intentarán identificar la relación; sin embargo, para obtener los mejores resultados, debería crear una relación siempre que sea posible. Para obtener más información, vea [Fórmulas y el modelo tabular](#bkmk_RelModel) más adelante en este tema.  
  
##  <a name="updating-the-results-of-formulas-process"></a><a name="bkmk_RefreshRecalc"></a>Actualizar los resultados de fórmulas (proceso)  
 El*proceso de datos* y el *recálculo* son dos operaciones diferentes pero relacionadas. Debe entender perfectamente estos conceptos a la hora de diseñar un modelo que contiene fórmulas complejas, cantidades grandes de datos o datos que se obtienen de orígenes de datos externos.  
  
 El*procesamiento de datos* es el proceso de actualizar los datos de un modelo con nuevos datos de un origen de datos externo.  
  
 El*recálculo* es el proceso de actualizar los resultados de las fórmulas para reflejar cualquier cambio en las propias las fórmulas y cualquier cambio en los datos subyacentes. El recálculo puede afectar al rendimiento de las siguientes maneras:  
  
-   Los valores de una columna calculada se calculan y se almacenan en el modelo. Para actualizar los valores de la columna calculada, debe procesar el modelo mediante uno de los tres comandos de procesamiento: proceso completo, procesar datos o procesar recálculo. El resultado de la fórmula se debe recalcular siempre para la columna completa, cada vez que cambia la fórmula.  
  
-   Los valores calculados mediante medidas se evalúan dinámicamente siempre que un usuario agrega la medida a una tabla dinámica o abre un informe; a medida que el usuario modifica el contexto, los valores devueltos por la medida cambian. Los resultados de la medida siempre reflejan el valor más reciente de la memoria caché en memoria.  
  
 El procesamiento y el recálculo no tienen ningún efecto en las fórmulas de filtro de fila, a menos que el resultado de un recálculo devuelva un valor diferente, con lo que hace que los miembros del rol puedan consultar o no la fila.  
  
 Para más información, vea [Procesar datos &#40;SSAS tabular&#41;](../process-data-ssas-tabular.md).  
  
##  <a name="troubleshooting-errors-in-formulas"></a><a name="bkmk_troubleshoot"></a>Solucionar errores en fórmulas  
 Si recibe un error al definir una fórmula, esta podría contener un *error sintáctico*, un *error semántico*o un *error de cálculo*.  
  
 Los errores sintácticos son más fáciles de resolver. Normalmente, se deben a que falta un paréntesis o una coma. Para obtener ayuda con la sintaxis de cada función, consulte [Referencia de funciones DAX](/dax/dax-function-reference).  
  
 El otro tipo de error se produce cuando la sintaxis es correcta, pero el valor o la columna a los que se hace referencia no tienen sentido en el contexto de la fórmula. Estos errores semánticos y de cálculo se pueden deber a uno de los problemas siguientes:  
  
-   La fórmula hace referencia a una columna, tabla o función que no existe.  
  
-   La fórmula parece ser correcta, pero cuando el motor de datos captura los datos detecta que los tipos no coinciden y genera un error.  
  
-   La fórmula pasa un número o tipo incorrecto de parámetros a una función.  
  
-   La fórmula hace referencia a otra columna que tiene un error y, en consecuencia, sus valores no son válidos.  
  
-   La fórmula hace referencia a una columna que no se ha procesado, lo que significa que tiene metadatos pero ningún dato real que se pueda utilizar para los cálculos.  
  
 En los cuatro primeros casos, DAX marca la columna completa que contiene la fórmula no válida. En el último caso, DAX hace que la columna se muestre en gris para indicar que se encuentra en estado no procesado.  
  
##  <a name="additional-resources"></a><a name="bkmk_addional_resources"></a> Recursos adicionales  
 [Creación de modelos tabulares &#40;tutorial de Adventure Works&#41;](../tabular-modeling-adventure-works-tutorial.md) proporciona instrucciones paso a paso sobre cómo crear un modelo tabular que incluya varios cálculos en columnas calculadas, medidas y filtros de fila. Para la mayoría de las fórmulas, se proporciona una descripción sobre el significado de la fórmula.  
  
 El [blog del equipo de Analysis Services y PowerPivot](https://go.microsoft.com/fwlink/?LinkID=220949&clcid=0x409) proporciona información, sugerencias, noticias y avisos sobre [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] y PowerPivot.  
  
 El [Centro de recursos de DAX](https://go.microsoft.com/fwlink/?LinkID=220966&clcid=0x409) proporciona información interna y externa sobre DAX, incluidas numerosas soluciones de DAX enviadas por destacados profesionales de Business Intelligence.  
  
## <a name="see-also"></a>Consulte también  
 [Expresiones de análisis de datos &#40;referencia de&#41; DAX](/dax/data-analysis-expressions-dax-reference)   
 [Medidas &#40;&#41;tabular de SSAS](measures-ssas-tabular.md)   
 [Columnas calculadas &#40;&#41;tabular de SSAS](ssas-calculated-columns.md)   
 [Roles &#40;SSAS tabular&#41;](roles-ssas-tabular.md)   
 [KPI &#40;&#41;tabular de SSAS](kpis-ssas-tabular.md)   
 [Orígenes de datos compatibles &#40;SSAS tabular&#41;](data-sources-supported-ssas-tabular.md)  
  
  
