---
title: Crear un proveedor de registro personalizado | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom log providers [Integration Services], creating
ms.assetid: fc20af96-9eb8-4195-8d3f-8a4d7c753f24
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c1efb736aece2cc8d118c81326989559f0d17a60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746328"
---
# <a name="creating-a-custom-log-provider"></a>Crear un proveedor de registro personalizado
  El entorno en tiempo de ejecución de [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] incluye amplias funciones de registro. Un registro permite capturar eventos que se generan durante la ejecución del paquete. [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] incluye varios proveedores de registro que permiten crear registros y almacenarlos en diversos formatos como XML, texto, base de datos o en el registro de eventos de Windows. Si uno de estos proveedores o formatos de salida no se ajusta sus necesidades, puede crear un proveedor de registro personalizado.

 Los pasos necesarios para crear un proveedor de registro personalizado son similares a los pasos para crear cualquier otro objeto personalizado para [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]:

-   Cree una clase nueva que herede de la clase base. Para un proveedor de registro, la clase base es <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>.

-   Aplique el atributo que identifica el tipo de objeto para la clase. Para un proveedor de registro, el atributo es <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute>.

-   Invalide la implementación de los métodos y las propiedades de la clase base. Para un proveedor de registro, estos incluyen la propiedad <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> y <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>, los métodos <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> y <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A>.

-   Las interfaces de usuario personalizadas para los proveedores de registro personalizados no están implementadas en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].

## <a name="getting-started-with-a-custom-log-provider"></a>Introducción a un proveedor de registro personalizado

### <a name="creating-projects-and-classes"></a>Crear proyectos y clases
 Dado que todos los proveedores de registro administrados se derivan de la clase base <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>, el primer paso para crear un proveedor de registro personalizado consiste en crear un proyecto de bibliotecas de clases en el lenguaje de programación administrado que prefiera y, a continuación, crear una clase que herede de la clase base. En esta clase derivada se invalidarán los métodos y las propiedades de la clase base para implementar la funcionalidad personalizada.

 Configure el proyecto para firmar el ensamblado que se generará con un archivo de claves del nombre seguro.

> [!NOTE]
>  Muchos proveedores de registro de [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] tienen una interfaz de usuario personalizada que implementa <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI> y reemplaza el cuadro de texto **Configuración** en el cuadro de diálogo **Configurar registros de SSIS** por una lista desplegable filtrada de administradores de conexiones disponibles. Sin embargo, las interfaces de usuario personalizadas para los proveedores de registro personalizados no se implementan en [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].

### <a name="applying-the-dtslogprovider-attribute"></a>Aplicar el atributo DtsLogProvider
 Aplique el atributo <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> a la clase que ha creado para identificarlo como un proveedor de registro. Este atributo proporciona información en tiempo de diseño, como el nombre y la descripción del proveedor de registro. Las `DisplayName` `Description` propiedades y del atributo corresponden al **nombre** y `Description` las columnas que se muestran en el editor **configurar registros de SSIS** , que se muestra al configurar el registro para un paquete en [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] .

> [!IMPORTANT]
>  La propiedad <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.LogProviderType%2A> del atributo no se usa. Sin embargo, debe especificar un valor para la propiedad o el proveedor de registro personalizado no aparecerá en la lista de proveedores de registro disponibles.

> [!NOTE]
>  Desde que las interfaces de usuario personalizadas para los proveedores de registro personalizados no se implementa en [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], especificar un valor para la propiedad <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.UITypeName%2A> de <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> no tiene ningún efecto.

```vb
<DtsLogProvider(DisplayName:="MyLogProvider", Description:="A simple log provider.", LogProviderType:="Custom")> _
Public Class MyLogProvider
     Inherits LogProviderBase
    ' TODO: Override the base class methods.
End Class
```

```csharp
[DtsLogProvider(DisplayName="MyLogProvider", Description="A simple log provider.", LogProviderType="Custom")]
public class MyLogProvider : LogProviderBase
{
    // TODO: Override the base class methods.
}
```

## <a name="building-deploying-and-debugging-a-custom-log-provider"></a>Generar, implementar y depurar un proveedor de registro personalizado
 Los pasos para generar, implementar y depurar un proveedor de registro personalizado en [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] son muy similares a los pasos requeridos para otros tipos de objetos personalizados. Para obtener más información, consulte [Generar, implementar y depurar objetos personalizados](../building-deploying-and-debugging-custom-objects.md).

![Integration Services icono (pequeño)](../../media/dts-16.gif "Icono de Integration Services (pequeño)")  **Manténgase al día con Integration Services**<br /> Para obtener las descargas, artículos, ejemplos y vídeos más recientes de Microsoft, así como soluciones seleccionadas de la comunidad, visite la página de [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] en MSDN:<br /><br /> [Visite la página de Integration Services en MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Para recibir notificaciones automáticas de estas actualizaciones, suscríbase a las fuentes RSS disponibles en la página.

## <a name="see-also"></a>Consulte también
 [Codificar un proveedor de registro personalizado](coding-a-custom-log-provider.md) [desarrollar una interfaz de usuario para un proveedor de registro personalizado](developing-a-user-interface-for-a-custom-log-provider.md)


