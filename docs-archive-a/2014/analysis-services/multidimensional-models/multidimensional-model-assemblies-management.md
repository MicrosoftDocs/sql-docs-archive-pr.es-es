---
title: Administración de ensamblados de modelos multidimensionales | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Analysis Services], assemblies
- calling user-defined functions
- user impersonation [Analysis Services]
- impersonation [Analysis Services]
- Data Mining Extensions [Analysis Services], assemblies
- MDX [Analysis Services], assemblies
- user-defined functions [Analysis Services]
- Analysis Services objects, assemblies
- assemblies [Analysis Services]
- application domains [Analysis Services]
ms.assetid: b2645d10-6d17-444e-9289-f111ec48bbfb
author: minewiskan
ms.author: owend
ms.openlocfilehash: b95a3171b3b194e84f10809f71eb72fefb07172b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744395"
---
# <a name="multidimensional-model-assemblies-management"></a>Administración de ensamblados de modelos multidimensionales
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] proporciona una gran cantidad de funciones intrínsecas para su uso con los lenguajes de expresiones multidimensionales (MDX) y extensiones de minería de datos (DMX), diseñadas para lograr todo, desde cálculos estadísticos estándar hasta el recorrido de miembros en una jerarquía. No obstante, al igual que con cualquier otro producto complejo, existe siempre la necesidad de ampliar la funcionalidad.  
  
 Por lo tanto, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] permite agregar ensamblados a una instancia o base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Los ensamblados permiten crear funciones externas definidas por el usuario mediante cualquier lenguaje CLR (Common Language Runtime), como por ejemplo Microsoft Visual Basic .NET o Microsoft Visual C#. También puede utilizar lenguajes de automatización COM (Modelo de objetos componentes), como Microsoft Visual Basic o Microsoft Visual C++.  
  
> [!IMPORTANT]  
>  Los ensamblados COM pueden suponer un riesgo para la seguridad. Debido a esto y a otras consideraciones, los ensamblados COM están en desuso en [!INCLUDE[ssASversion10](../../includes/ssasversion10-md.md)]. Es posible que este tipo de ensamblados no esté disponible en versiones futuras.  
  
 Los ensamblados le permiten ampliar la funcionalidad empresarial de MDX y DMX. Cree la funcionalidad que desee en una biblioteca, como por ejemplo una biblioteca de vínculos dinámicos (DLL), y agregue la biblioteca como ensamblado a una instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o a una base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Los métodos públicos de la biblioteca se ofrecerán como funciones definidas por el usuario a procedimientos, cálculos, acciones, aplicaciones cliente y expresiones de MDX y DMX.  
  
 En el servidor se puede agregar un ensamblado con nuevos procedimientos y funciones. Puede usar los ensamblados para mejorar o agregar funcionalidad personalizada que no proporciona el servidor. Si usa ensamblados, puede agregar las nuevas funciones a las Expresiones multidimensionales (MDX), las Extensiones de minería de datos (DMX) o los procedimientos almacenados. Los ensamblados se cargan desde la ubicación donde se ejecuta la aplicación personalizada; en el servidor se guarda una copia del archivo binario del ensamblado junto con los datos de la base de datos. Cuando se quita un ensamblado, el ensamblado copiado también se quita del servidor.  
  
 Los ensamblados pueden ser de dos tipos diferentes: COM y CLR. Los ensamblados CLR son ensamblados desarrollados en los lenguajes de programación de .NET Framework como C#, Visual Basic .NET, C++ administrado. Los ensamblados COM son bibliotecas COM que se deben registrar en el servidor.  
  
 Los ensamblados se pueden agregar a los objetos <xref:Microsoft.AnalysisServices.Server> o <xref:Microsoft.AnalysisServices.Database> . Cualquier usuario conectado al servidor o a cualquier objeto del servidor puede llamar a los ensamblados de servidor. Solo los objetos o los usuarios conectados a la <xref:Microsoft.AnalysisServices.Database> pueden llamar a los ensamblados de base de datos.  
  
 Un objeto de <xref:Microsoft.AnalysisServices.Assembly> simple se compone de información básica (nombre e id.), una colección de archivos y especificaciones de seguridad.  
  
 La colección de archivos hace referencia a los archivos de ensamblado cargados y sus archivos de depuración (.pdb) correspondientes, si éstos se cargaron con los archivos de ensamblado. Los archivos de ensamblado se cargan desde la ubicación definida por la aplicación ; en el servidor se guarda una copia junto con los datos. La copia del archivo de ensamblado se usa para cargar el ensamblado cada vez que se inicia el servicio.  
  
 Las especificaciones de seguridad incluyen el conjunto de permisos y la suplantación que se usa para ejecutar el ensamblado.  
  
## <a name="calling-user-defined-functions"></a>Llamar a funciones definidas por el usuario  
 La llamada a una función definida por el usuario en un ensamblado se realiza de la misma forma que la llamada a una función intrínseca, salvo que se deba utilizar un nombre completo. Por ejemplo, una función definida por el usuario que devuelva un tipo esperado por MDX se incluye en una consulta MDX, como se muestra en el siguiente ejemplo:  
  
```  
Select MyAssembly.MyClass.MyStoredProcedure(a, b, c) on 0 from Sales  
```  
  
 También se puede llamar a las funciones definidas por el usuario mediante la palabra clave CALL. Debe utilizar la palabra clave CALL con funciones definidas por el usuario que devuelvan conjuntos de registros o valores nulos, y no podrá utilizarla si la función definida por el usuario depende de un objeto del contexto del script o instrucción MDX o DMX, como el modelo de minería de datos o el cubo actual. Un uso común de una función llamada fuera de una consulta MDX o DMX es utilizar el modelo de objetos AMO para realizar funciones administrativas. Si, por ejemplo, desea utilizar la función `MyVoidProcedure(a, b, c)` en una instrucción MDX, se utilizaría la siguiente sintaxis:  
  
```  
Call MyAssembly.MyClass.MyVoidProcedure(a, b, c)  
```  
  
 Los ensamblados simplifican el desarrollo de la base de datos al permitir que se desarrolle una sola vez el código común y se almacene en una ubicación única. Los desarrolladores cliente pueden crear bibliotecas de funciones para [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] y distribuirlas por sus aplicaciones.  
  
 Los ensamblados y las funciones definidas por el usuario pueden duplicar los nombres de función de la biblioteca de funciones de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o de otros ensamblados. Siempre que se llame a la función definida por el usuario con su nombre completo, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilizará el procedimiento correcto. Por razones de seguridad y para eliminar la posibilidad de llamar a un nombre duplicado de una biblioteca de clases diferente, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] requiere que se utilicen solo nombres completos para procedimientos almacenados.  
  
 Para llamar a una función definida por el usuario desde un ensamblado CLR, la función definida por el usuario estará precedida por el nombre del ensamblado, el nombre de clase completo y el nombre de procedimiento, como se muestra a continuación:  
  
 *AssemblyName*. *FullClassName*. *Nombreprocedimiento*(*argumento1*, *Argument2*,...)  
  
 Por razones de compatibilidad con versiones anteriores de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], se acepta también la siguiente sintaxis:  
  
 *nombreDeEnsamblado*!*nombreDeClaseCompleto*!*nombreDeProcedimiento*(*Argumento1*, *Argumento2*…)  
  
 Si una biblioteca COM admite varias interfaces, también se puede utilizar el Id. de interfaz para resolver el nombre de procedimiento, como se muestra a continuación:  
  
 *nombreDeEnsamblado*!*idDeInterfaz*!*nombreDeProcedimiento*(*Argumento1*, *Argumento2*…)  
  
## <a name="security"></a>Seguridad  
 La seguridad de los ensamblados depende del modelo de seguridad de .NET Framework, que es un modelo de seguridad de acceso del código. .NET Framework admite un mecanismo de seguridad de acceso del código que presupone que el tiempo de ejecución puede hospedar código de plena confianza y código parcialmente de confianza. Los recursos protegidos por la seguridad de acceso del código de .NET Framework se suelen empaquetar mediante código administrado que solicita el permiso correspondiente antes de permitir el acceso al recurso. La solicitud de permiso solo se satisface si todos los que llaman (en el nivel de ensamblado) de la pila de llamadas tienen el permiso correspondiente para el recurso.  
  
 En el caso de los ensamblados, el permiso de ejecución se pasa con la propiedad `PermissionSet` del objeto `Assembly`. Los permisos que recibe el código administrado vienen determinados por la directiva de seguridad activa. Existen tres niveles de directiva activos en un entorno que no esté hospedado en[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] : organización, equipo y usuario. La lista real de permisos que el código recibe queda determinada por la intersección de los permisos obtenidos por estos tres niveles.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] proporciona un nivel de directiva de seguridad de nivel de host a la biblioteca CLR mientras lo hospeda; esta directiva es un nivel de directiva adicional por debajo de los tres niveles de directiva que siempre están activos. Esta directiva se establece para cada dominio de aplicación creado por [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 La directiva de nivel de host de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] es una combinación de la directiva fija de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] para ensamblados de sistema y de la directiva especificada por el usuario para ensamblados de usuario. La parte especificada por el usuario de la directiva de host de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] depende del propietario de ensamblado que especifique uno de los tres depósitos de permisos para cada ensamblado:  
  
|Configuración de permisos|Descripción|  
|------------------------|-----------------|  
|`Safe`|Proporciona permiso de cálculo interno. Este depósito de permisos no asigna permisos para el acceso a los recursos protegidos en .NET Framework. Se trata del depósito de permisos predeterminado para un ensamblado si no se especifica ninguno con la propiedad `PermissionSet`.|  
|`ExternalAccess`|Proporciona el mismo acceso que la configuración `Safe`, con la posibilidad adicional de permitir el acceso a los recursos externos del sistema. Este depósito de permisos no ofrece garantías de seguridad (aunque se puede proteger este escenario), pero ofrece garantías de confiabilidad.|  
|`Unsafe`|Sin restricciones. No se pueden ofrecer garantías de seguridad ni confiabilidad al código administrado que se ejecute en este conjunto de permisos. Otorga cualquier permiso al código que se ejecute en este nivel de confianza, incluso un permiso personalizado incluido por el administrador.|  
  
 Si CLR es hospedado por [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], la comprobación de permisos basada en el recorrido de la pila se detiene en el límite con el código de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] nativo. Cualquier código administrado en los ensamblados de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] queda siempre en una de las tres categorías de permiso descritas anteriormente.  
  
 Las rutinas de ensamblado COM (o no administradas) no admiten el modelo de seguridad de CLR.  
  
### <a name="impersonation"></a>Suplantación  
 Siempre que exista código administrado que tenga acceso a cualquier recurso externo a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sigue las reglas asociadas a la configuración de la propiedad `ImpersonationMode` del ensamblado para asegurar que el acceso se produce en un contexto de seguridad de Windows adecuado. Dado que los ensamblados que utilizan la configuración de permisos `Safe` no tienen acceso a los recursos externos a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], estas reglas solo se aplican a ensamblados que utilicen la configuración de permisos `ExternalAccess` y `Unsafe`.  
  
-   Si el contexto de ejecución actual corresponde al inicio de sesión autenticado de Windows y es el mismo contexto del autor de la llamada original (es decir, EXECUTE AS no se encuentra en el medio), [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] suplantará el inicio de sesión autenticado de Windows para tener acceso al recurso.  
  
-   Si hay un EXECUTE AS intermedio que ha cambiado el contexto del llamador original, se producirá un error al intentar obtener acceso al recurso externo.  
  
 La propiedad `ImpersonationMode` se puede establecer en `ImpersonateCurrentUser` o `ImpersonateAnonymous`. La configuración predeterminada, `ImpersonateCurrentUser`, ejecuta un ensamblado en la cuenta de inicio de sesión en red del usuario actual. Si `ImpersonateAnonymous` se usa la configuración, el contexto de ejecución corresponde a la cuenta de usuario de inicio de sesión de Windows IUSER_*ServerName* en el servidor. Se trata de la cuenta de invitado para Internet, que tiene privilegios limitados en el servidor. Un ensamblado que se ejecute en este contexto solamente podrá tener acceso a recursos limitados del servidor local.  
  
### <a name="application-domains"></a>Dominios de aplicación  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] no ofrece dominios de aplicación directamente. Dado que un conjunto de ensamblados se ejecuta en el mismo dominio de aplicación, los dominios de aplicación podrán descubrirse entre ellos en el tiempo de ejecución mediante el espacio de nombres `System.Reflection` de .NET Framework o de alguna otra forma, y podrán realizar en ellos llamadas enlazadas en tiempo de ejecución. Tales llamadas estarán sujetas a las comprobaciones de permiso utilizadas por la seguridad basada en autorizaciones de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 No debe confiarse en la búsqueda de ensamblados en el mismo dominio de aplicación, porque la implementación define el límite del dominio de aplicación y los ensamblados que van en cada dominio.  
  
## <a name="see-also"></a>Consulte también  
 [Establecer la seguridad de los procedimientos almacenados](../multidimensional-models-extending-olap-stored-procedures/setting-security-for-stored-procedures.md)   
 [Definir procedimientos almacenados](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
