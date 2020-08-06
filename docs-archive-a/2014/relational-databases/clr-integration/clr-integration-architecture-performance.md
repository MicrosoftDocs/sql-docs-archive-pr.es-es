---
title: Rendimiento de la integración CLR | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], performance
- common language runtime [SQL Server], compilation process
- performance [CLR integration]
ms.assetid: 7ce2dfc0-4b1f-4dcb-a979-2c4f95b4cb15
author: rothja
ms.author: jroth
ms.openlocfilehash: 33e45039ed98ea3df607df1714b3c6108ec17c35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87747619"
---
# <a name="performance-of-clr-integration"></a>Rendimiento de la integración CLR
  En este tema se describen algunas de las opciones de diseño que mejoran el rendimiento de la [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] integración con el [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Common Language Runtime de .NET Framework (CLR).  
  
## <a name="the-compilation-process"></a>El proceso de compilación  
 Durante la compilación de expresiones SQL, cuando se encuentra una referencia a una rutina administrada, se genera un código auxiliar de lenguaje intermedio de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] (MSIL). Este código auxiliar incluye el código para calcular referencias de los parámetros de rutina de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a CLR, invocar la función y devolver el resultado. Este código de "unión" está basado en el tipo y la dirección del parámetro (entrada, salida o referencia).  
  
 El código de unión habilita las optimizaciones específicas del tipo y asegura una eficaz aplicación de la semántica de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], como el control de excepciones estándar, de nulabilidad, de facetas de restricción y por valor. Al generar código para los tipos exactos de los argumentos, se evitan los costos de la conversión de tipos o de la creación de objetos contenedores (denominada "conversión boxing") dentro de los límites de la invocación.  
  
 El código auxiliar generado se compila a continuación en código nativo y se optimiza para la arquitectura de hardware concreta en la que se ejecuta [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], utilizando los servicios de compilación JIT (Just In Time) de CLR. Los servicios JIT se invocan en el nivel de método y permiten al entorno de hospedaje de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] crear una unidad de compilación única que abarca la ejecución de CLR y [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Una vez compilado el código auxiliar, el puntero resultante a la función se convierte en la implementación de la función durante la ejecución. Este enfoque de generación de código garantiza que no haya ningún costo de invocación adicional relacionado con el acceso a los metadatos o el reflejo durante la ejecución.  
  
### <a name="fast-transitions-between-sql-server-and-clr"></a>Transiciones rápidas entre SQL Server y CLR  
 El proceso de compilación produce un puntero a función al que se puede llamar durante la ejecución desde código nativo. En el caso de funciones definidas por el usuario con valores escalares, esta invocación de función se produce fila por fila. Para minimizar el costo de la transición entre [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] y CLR, las instrucciones que contienen cualquier invocación administrada tienen un paso de inicio para identificar el dominio de la aplicación de destino. Este paso de identificación reduce el costo de la transición para cada fila.  
  
## <a name="performance-considerations"></a>Consideraciones de rendimiento  
 A continuación se resumen las consideraciones de rendimiento específicas para la integración CLR en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Puede encontrar información más detallada en "[using CLR Integration in SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=50332)" en el sitio web de MSDN. Puede encontrar información general sobre el rendimiento del código administrado en "[mejorar el rendimiento y la escalabilidad de las aplicaciones .net](https://go.microsoft.com/fwlink/?LinkId=50333)" en el sitio web de MSDN.  
  
### <a name="user-defined-functions"></a>Funciones definidas por el usuario  
 Las funciones CLR se benefician de una ruta de invocación más rápida que la de las funciones definidas por el usuario de [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Además, el código administrado ofrece una gran ventaja de rendimiento con respecto a [!INCLUDE[tsql](../../../includes/tsql-md.md)] en lo que se refiere al código de procedimiento, el cálculo y la manipulación de cadenas. Las funciones de CLR que requieren una gran cantidad de cálculo y que no proporcionan acceso a datos se escriben mejor en código administrado. En cambio, las funciones de [!INCLUDE[tsql](../../../includes/tsql-md.md)] sí proporcionan acceso a datos de forma más eficiente que la integración CLR.  
  
### <a name="user-defined-aggregates"></a>Funciones de agregado definidas por el usuario  
 El código administrado puede mejorar significativamente el rendimiento de la agregación basada en cursor. La realización del código administrado suele ser algo más lenta que la de las funciones de agregado integradas de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Si existe una función de agregado integrada nativa, se recomienda utilizarla. En los casos en que la agregación que se necesita no se admite de forma nativa, piense en utilizar una función de agregado definida por el usuario de CLR en lugar de una implementación basada en cursor para obtener un mejor rendimiento.  
  
### <a name="streaming-table-valued-functions"></a>Funciones con valores de tabla de transmisión por secuencias  
 Después de invocar una función, las aplicaciones suelen necesitar devolver una tabla. Entre los ejemplos se incluye la lectura de datos tabulares de un archivo como parte de una operación de importación y la conversión de valores separados por comas en una representación relacional. Normalmente, esto se puede llevar a cabo materializando y rellenando la tabla de resultados antes de que pueda consumirla el autor de las llamadas. La integración de CLR en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] introduce una función con valores de tabla de transmisión por secuencias (STVF), que es un nuevo mecanismo de extensibilidad. Las STVF administradas funcionan mejor que las implementaciones de procedimiento almacenado extendido comparables.  
  
 Las STVF son funciones administradas que devuelven una interfaz `IEnumerable`. `IEnumerable` tiene métodos para navegar por el conjunto de resultados devuelto por la STVF. Cuando se invoca la STVF, la interfaz `IEnumerable` devuelta se conecta directamente al plan de consulta. El plan de consulta llama a los métodos `IEnumerable` cuando necesita capturar filas. Este modelo de iteración permite utilizar los resultados inmediatamente después de que se genere la primera fila, en lugar de esperar hasta que se rellene la tabla completa. Reduce también significativamente la cantidad de memoria que se utiliza al invocar la función.  
  
### <a name="arrays-vs-cursors"></a>Matrices frente a cursores  
 Cuando los cursores de [!INCLUDE[tsql](../../../includes/tsql-md.md)] deben recorrer datos que se expresan más fácilmente como una matriz, se puede utilizar el código administrado con significativas mejoras del rendimiento.  
  
### <a name="string-data"></a>Datos de cadena  
 Los datos de caracteres de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], como `varchar`, pueden ser del tipo SqlString o SqlChars en funciones administradas. Las variables SqlString crean una instancia del valor completo en la memoria. Las variables SqlChars proporcionan una interfaz de transmisión por secuencias que se puede utilizar para lograr mejores rendimiento y escalabilidad sin crear una instancia del valor completo en la memoria. Esto se vuelve especialmente importante para los datos de objetos grandes (LOB). Además, se puede tener acceso a los datos XML del servidor a través de una interfaz de transmisión por secuencias devuelta por `SqlXml.CreateReader()`.  
  
### <a name="clr-vs-extended-stored-procedures"></a>CLR frente a los procedimientos almacenados extendidos  
 Las interfaces de programación de aplicaciones (API) de Microsoft.SqlServer.Server que permiten a los procedimientos administrados devolver conjuntos de resultados al cliente funcionan mejor que las API de Servicios abiertos de datos (ODS) utilizadas por los procedimientos almacenados extendidos. Además, las API de System.Data.SqlServer admiten tipos de datos como `xml`, `varchar(max)`, `nvarchar(max)` y `varbinary(max)` introducidos en [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], mientras que las API de ODS no se han ampliado para admitir los nuevos tipos de datos.  
  
 Con código administrado, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] administra el uso de los recursos como la memoria, los subprocesos y la sincronización. Esto se debe a que las API administradas que exponen estos recursos se implementan sobre el administrador de recursos de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. En cambio, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] no tiene ninguna vista o control sobre el uso de recursos del procedimiento almacenado extendido. Por ejemplo, si un procedimiento almacenado extendido usa demasiados recursos de la CPU o de la memoria, con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] no hay ninguna manera de detectarlo o controlarlo. Sin embargo, con el código administrado, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] puede detectar que un subproceso determinado no ha producido resultados durante un largo período de tiempo y, a continuación, puede obligar a la tarea a producir resultados para que se pueda programar otro trabajo. Por consiguiente, el uso de código administrado aporta una mayor escalabilidad y una mejor utilización de los recursos del sistema.  
  
 El código administrado puede hacer que se produzca una sobrecarga adicional necesaria para mantener el entorno de ejecución y realizar comprobaciones de seguridad. Así ocurre, por ejemplo, cuando se ejecuta en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] y se requieren numerosas transacciones de código administrado a código nativo (ya que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] necesita llevar a cabo un mantenimiento adicional en los valores específicos de los subprocesos al salir del código nativo y volver al mismo. Por ello, los procedimientos almacenados extendidos pueden obtener resultados bastante mejores que el código administrado que se ejecuta en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cuando hay transiciones frecuentes entre código administrado y código nativo.  
  
> [!NOTE]  
>  No se recomienda desarrollar nuevos procedimientos almacenados extendidos, puesto que esta característica ha quedado desusada.  
  
### <a name="native-serialization-for-user-defined-types"></a>Serialización nativa para los tipos definidos por el usuario  
 Los tipos definidos por el usuario (UDT) están diseñados como un mecanismo de extensibilidad para el sistema de tipo escalar. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] implementa un formato de serialización para UDT denominado `Format.Native`. Durante la compilación se examina la estructura del tipo para generar el MSIL personalizado para esa definición de tipo concreta.  
  
 La serialización nativa es la implementación predeterminada para [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La serialización definida por el usuario invoca un método definido por el autor de tipo para realizar la serialización. Se debe utilizar la serialización `Format.Native` siempre que sea posible para obtener el máximo rendimiento.  
  
### <a name="normalization-of-comparable-udts"></a>Normalización de tipos definidos por el usuario comparables  
 Las operaciones relacionales, como ordenar y comparar tipos definidos por el usuario (UDT), funcionan directamente en la representación binaria del valor. Esto se logra almacenando en disco una representación normalizada (ordenada de forma binaria) del estado del UDT.  
  
 La normalización tiene dos ventajas: abarata considerablemente la operación de comparación al evitar la creación de la instancia de tipo y la sobrecarga de la invocación de métodos; y crea un dominio binario para el UDT que permite la creación de histogramas, índices e histogramas para los valores del tipo. Por consiguiente, los UDT normalizados tienen un perfil de rendimiento muy similar al de los tipos integrados nativos para las operaciones que no implican la invocación de métodos.  
  
### <a name="scalable-memory-usage"></a>Uso de memoria escalable  
 Para que la recolección de elementos no utilizados administrada se ejecute y escale correctamente en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], evite grandes asignaciones únicas. Las asignaciones con un tamaño superior a 88 kilobytes (KB) se colocarán en el montón de objeto grande, lo que hará que la recolección de elementos no utilizados se ejecute y escale mucho peor que muchas asignaciones más pequeñas. Por ejemplo, si necesita asignar una matriz multidimensional grande, es preferible asignar una matriz escalonada (dispersa).  
  
## <a name="see-also"></a>Consulte también  
 [Tipos definidos por el usuario CLR](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
  
  
