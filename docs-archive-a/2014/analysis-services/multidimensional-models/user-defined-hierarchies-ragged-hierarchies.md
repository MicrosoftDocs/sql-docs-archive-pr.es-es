---
title: Jerarquías desiguales | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ragged hierarchies [Analysis Services]
ms.assetid: e40a5788-7ede-4b0f-93ab-46ca33d0cace
author: minewiskan
ms.author: owend
ms.openlocfilehash: 02cbb24b7ae80facf0ddbb1495fccc8f848df377
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87749506"
---
# <a name="ragged-hierarchies"></a>Jerarquías desiguales
  Una jerarquía desigual es una jerarquía definida por el usuario que tiene un número impar de niveles. Por ejemplo, un organigrama donde un director de alto nivel tiene tanto directores de departamento como no directores a su cargo o jerarquías geográficas que constan de País-Región-Ciudad, donde algunas ciudades no tienen un Estado o Provincia primario, como Washington D.C., Ciudad del Vaticano o Nueva Delhi.  
  
 En la mayoría de las jerarquías de una dimensión, cada nivel tiene el mismo número de miembros por encima de él que cualquier otro miembro del mismo nivel. Una jerarquía desigual es diferente en el sentido de que el primario lógico de al menos un miembro no se encuentra en el nivel que está inmediatamente por encima del miembro. Cuando ocurre esto, la jerarquía desciende a distintos niveles de diferentes rutas de obtención de detalles. En una aplicación cliente, esto puede hacer que las rutas de obtención de detalles sean innecesariamente complicadas.  
  
 Las aplicaciones cliente varían en la forma de tratar una jerarquía desigual. Si existen jerarquías desiguales en el modelo, prepárese para realizar un pequeño trabajo adicional con el fin de obtener el comportamiento de representación que espera.  
  
 El primer paso consiste en comprobar la aplicación cliente para ver cómo trata la ruta de obtención de detalles. Por ejemplo, Excel repite los nombres de los elementos primarios como marcadores de posición para los valores que faltan. Para ver este comportamiento, cree una tabla dinámica con la dimensión Sales Territory del modelo multidimensional de Adventure Works. En una tabla dinámica que tiene los atributos Group, Country y Region de Sales Territory, verá que los países en los que falta un valor de región obtendrán un marcador de posición, en este caso una repetición del primario que hay por encima de él (el nombre del país). Este comportamiento deriva de la propiedad de cadena de conexión MDX Compatibility=1, que es fija dentro de Excel. Si el cliente no proporciona de forma natural los comportamientos de obtención de detalles que desea, puede establecer propiedades en el modelo para cambiar al menos algunos de esos comportamientos.  
  
 Este tema contiene las siguientes secciones:  
  
-   [Enfoques para modificar la navegación de obtención de detalles en una jerarquía desigual](#bkmk_approach)  
  
-   [Establecer HideMemberIf para ocultar miembros en una jerarquía normal](#bkmk_Hide)  
  
-   [Establecer MDX Compatibility para determinar cómo se representan los marcadores de posición en las aplicaciones cliente](#bkmk_Mdx)  
  
##  <a name="approaches-for-modifying-drilldown-navigation-in-a-ragged-hierarchy"></a><a name="bkmk_approach"></a> Enfoques para modificar la navegación de obtención de detalles en una jerarquía desigual  
 La presencia de una jerarquía desigual se convierte en un problema cuando la navegación de obtención de detalles no devuelve los valores esperados o se percibe como difícil de usar. Para corregir los problemas de navegación resultantes de jerarquías desiguales, considere las siguientes opciones:  
  
-   Use una jerarquía normal pero establezca la propiedad `HideMemberIf` en cada nivel para especificar si un nivel que falta se muestra al usuario. Al establecer `HideMemberIf`, debe establecer también `MDXCompatibility` en la cadena de conexión para reemplazar los comportamientos de navegación predeterminados. En este tema se ofrecen instrucciones para establecer estas propiedades.  
  
-   Cree una jerarquía de elementos primarios y secundarios que administre explícitamente los miembros del nivel. Para conocer esta técnica, vea la entrada de blog [Ragged Hierarchy in SSAS (Jerarquía desigual en SSAS)](http://dwbi1.wordpress.com/2011/03/30/ragged-hierarchy-in-ssas/). Para obtener más información en los libros en pantalla, vea [jerarquía de elementos primarios y secundarios](parent-child-dimension.md). Las desventajas de crear una jerarquía de elementos primarios y secundarios son que solo puede tener una por dimensión y que normalmente disminuye el rendimiento cuando se calculan agregaciones para los miembros intermedios.  
  
 Si la dimensión contiene más de una jerarquía desigual, debe usar el primer enfoque y establecer `HideMemberIf`. Los desarrolladores de BI que tienen experiencia práctica en el trabajo con jerarquías desiguales van más allá y son partidarios de realizar cambios adicionales en las tablas de datos físicas, creando tablas diferentes para cada nivel. Vea [las jerarquías desiguales (blog) de Martin Mason de la parte 1A del cubo financiero de SSAS](http://martinmason.wordpress.com/2012/03/03/the-ssas-financial-cubepart-1aragged-hierarchies-cont/) para más información sobre esta técnica.  
  
##  <a name="set-hidememberif-to-hide-members-in-a-regular-hierarchy"></a><a name="bkmk_Hide"></a> Establecer HideMemberIf para ocultar miembros en una jerarquía normal  
 En la tabla de una dimensión desigual, los miembros que faltan de manera lógica se pueden representar de distintos modos. Las celdas de la tabla pueden contener valores NULL o cadenas vacías o bien pueden contener el mismo valor que su elemento primario para servir de marcador de posición. La representación de los marcadores de posición está determinada por el estado de los marcadores de posición de los miembros secundarios, según determina la propiedad `HideMemberIf`, y la propiedad de cadena de conexión `MDX Compatibility` de la aplicación cliente.  
  
 En aplicaciones cliente que admiten la visualización de jerarquías desiguales, puede usar estas propiedades para ocultar de forma lógica los miembros que faltan.  
  
1.  En SSDT, haga doble clic en una dimensión para abrirla en el Diseñador de dimensiones. La primera pestaña, Estructura de dimensión, muestra las jerarquías de atributo en el panel Jerarquías.  
  
2.  Haga clic con el botón derecho en un miembro dentro de la jerarquía y seleccione **Propiedades**. Establezca `HideMemberIf` en uno de los valores que se describen a continuación.  
  
    |Configuración de HideMemberIf|Descripción|  
    |--------------------------|-----------------|  
    |`Never`|Los miembros del nivel nunca están ocultos. Este es el valor predeterminado.|  
    |**OnlyChildWithNoName**|Un miembro del nivel está oculto cuando es el único elemento secundario de su elemento primario y su nombre es nulo o es una cadena vacía.|  
    |**OnlyChildWithParentName**|Un miembro del nivel está oculto cuando es el único elemento secundario de su elemento primario y su nombre es el mismo que el de su primario.|  
    |**NoName**|Un miembro del nivel está oculto cuando su nombre está vacío.|  
    |**ParentName**|Un miembro del nivel está oculto cuando su nombre es idéntico al de su primario.|  
  
##  <a name="set-mdx-compatibility-to-determine-how-placeholders-are-represented-in-client-applications"></a><a name="bkmk_Mdx"></a>Establecer la compatibilidad de MDX para determinar cómo se representan los marcadores de posición en las aplicaciones cliente  
 Después de establecer `HideMemberIf` en un nivel de jerarquía, debe establecer también la propiedad `MDX Compatibility` en la cadena de conexión enviada desde la aplicación cliente. El valor de `MDX Compatibility` determina si se usa `HideMemberIf` o no.  
  
|Valor de MDX Compatibility|Descripción|Uso|  
|-------------------------------|-----------------|-----------|  
|**1**|Mostrar un valor de marcador de posición.|Es el valor predeterminado utilizado por Excel, SSDT y SSMS. Indica al servidor que devuelva los valores de marcador de posición al obtener detalles de niveles vacíos en una jerarquía desigual. Si hace clic en el valor de marcador de posición, puede seguir profundizando hasta obtener los nodos secundarios (hoja).<br /><br /> Excel posee la cadena de conexión usada para conectarse a Analysis Services y siempre establece `MDX Compatibility` en 1 en todas las conexiones nuevas. Este comportamiento conserva la compatibilidad con versiones anteriores.|  
|**2**|Ocultar un valor de marcador de posición (un valor NULL o un duplicado del nivel primario), pero mostrar otros niveles y nodos que tengan los valores pertinentes.|`MDX Compatibility`=2 se suele considerar el valor preferido para las jerarquías desiguales. Un informe de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] y algunas aplicaciones cliente de terceros pueden conservar este valor.|  
  
## <a name="see-also"></a>Consulte también  
 [Crear jerarquías definidas por el usuario](user-defined-hierarchies-create.md)   
 [Jerarquías de usuario](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)   
 [Jerarquía de elementos primarios y secundarios](parent-child-dimension.md)   
 [Propiedades de cadena de conexión &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/instances/connection-string-properties-analysis-services)  
  
  
