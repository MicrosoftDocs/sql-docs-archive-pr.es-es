---
title: Administrador de conexiones OData | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3caa4372-aff3-4c0f-9ecd-97870948b8d0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 46eedaa008b284661fd1d364d2e2bc87c373a9f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674261"
---
# <a name="odata-connection-manager"></a>Administrador de conexiones OData
  Un administrador de conexiones OData permite que un paquete se conecte a un origen OData. Un componente de origen OData se conecta a un origen OData mediante un administrador de conexiones OData y usa datos del servicio. Vea la sección [OData Source](../data-flow/odata-source.md)para obtener información detallada, incluidas las instrucciones de instalación de estos componentes.  
  
## <a name="adding-connection-manager-to-an-ssis-package"></a>Agregar un administrador de conexiones a un paquete SSIS  
 Hay tres formas de agregar un nuevo administrador de conexiones OData a un paquete SSIS:  
  
-   Haga clic en el botón **Nuevo…** en el **Editor de origen de OData**.  
  
-   Haga clic con el botón secundario en la carpeta **Administradores de conexiones** en el **Explorador de soluciones** y, a continuación, haga clic en **Nuevo administrador de conexiones**. Seleccione **ODATA** en **Tipo de administrador de conexión**.  
  
-   Haga clic con el botón derecho en el panel **administradores de conexiones** en la parte inferior del diseñador de paquetes y seleccione **nueva conexión..**.. Seleccione **ODATA** en **tipo de administrador de conexiones**.  
  
## <a name="connection-manager-authentication"></a>Autenticación del administrador de conexiones  
 El administrador de conexiones OData admite dos modos de autenticación.  
  
-   Autenticación de Windows  
  
-   Autenticación básica (nombre de usuario y contraseña)  
  
 Para el acceso anónimo, seleccione la opción Autenticación de Windows  
  
### <a name="specifying-and-securing-credentials"></a>Especificar y proteger las credenciales  
 Si el servicio OData requiere autenticación básica, puede especificar un nombre de usuario y una contraseña en el [OData Connection Manager Editor](../odata-connection-manager-editor.md). Los valores que especifica en el editor se conservan en el paquete. El valor de contraseña se cifra según el nivel de protección del paquete.  
  
 Hay varias maneras de externalizar/parametrizar los valores de nombre de usuario y contraseña. Las dos métodos principales de hacerlo en [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] son mediante parámetros o estableciendo las propiedades del administrador de conexiones directamente al ejecutar el paquete con SQL Server Management Studio.  
  
## <a name="odata-connection-manager-properties"></a>Propiedades del administrador de conexiones OData  
 En la lista siguiente se describen algunas de las propiedades del administrador de conexiones OData que quizás desee cambiar.  
  
|||  
|-|-|  
|Propiedad|Descripción|  
|Url|Dirección URL al documento de servicio.|  
|UserName|Nombre de usuario que se va a usar para la autenticación básica.|  
|Contraseña|Contraseña que se va a usar para la autenticación básica.|  
|ConnectionString|Refleja otras propiedades del administrador de conexiones.|  
  
## <a name="see-also"></a>Consulte también  
 [Editor del administrador de conexiones OData](../odata-connection-manager-editor.md)  
  
  
