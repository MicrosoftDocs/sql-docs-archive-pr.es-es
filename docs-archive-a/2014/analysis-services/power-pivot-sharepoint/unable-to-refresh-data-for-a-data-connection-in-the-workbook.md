---
title: 'No pueden actualizar los datos de una conexión de datos del libro. Vuelva a intentarlo o póngase en contacto con el administrador del sistema. No se pudieron actualizar las siguientes conexiones: datos PowerPivot | Microsoft Docs'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0f6fd52d-ac72-43e3-aa08-05a2d2bb873d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9c25c2597bbc7aa16fb8b66d4ffddbf0df14515e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748308"
---
# <a name="unable-to-refresh-data-for-a-data-connection-in-the-workbook-try-again-or-contact-your-system-administrator-the-following-connections-failed-to-refresh-powerpivot-data"></a>No pueden actualizar los datos de una conexión de datos del libro. Vuelva a intentarlo o póngase en contacto con el administrador del sistema. No se pudieron actualizar las siguientes conexiones: datos PowerPivot
  Para los libros de Excel que contienen datos PowerPivot, Excel Services devuelve este error si envía una solicitud de conexión a un servidor PowerPivot y se produce un error en la solicitud.  
  
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Se aplica a:|Instalación de PowerPivot para SharePoint|  
|Versión del producto|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Causa|Vea a continuación.|  
|Texto del mensaje|No pueden actualizar los datos de una conexión de datos del libro. Vuelva a intentarlo o póngase en contacto con el administrador del sistema. No se pudieron actualizar las siguientes conexiones: datos PowerPivot|  
  
## <a name="explanation-and-resolution"></a>Explicación y resolución  
 Excel Services no puede conectarse con los datos PowerPivot o cargarlos. Este error puede producirse por alguna de las condiciones siguientes:  
  
 **Escenario 1: el servicio no se inicia**  
  
 No se ha iniciado la instancia de SQL Server Analysis Services (PowerPivot). Una contraseña caducada hará que el servicio deje de funcionar. Para obtener más información acerca de cómo cambiar la contraseña, vea [configurar las cuentas de servicio PowerPivot](configure-power-pivot-service-accounts.md) e [iniciar o detener un servidor PowerPivot para SharePoint](start-or-stop-a-power-pivot-for-sharepoint-server.md).  
  
 **Escenario 2a: abrir un libro de la versión anterior en el servidor**  
  
 El libro que intenta abrir podría haberse creado en la versión SQL Server 2008 R2 de PowerPivot para Excel. Probablemente, el proveedor de datos de Analysis Services que se especifica en la cadena de conexión de datos no está presente en el equipo que controla la solicitud.  
  
 Si este es el caso, encontrará este mensaje en el registro de ULS: "error al actualizar para ' datos PowerPivot ' en el libro ' \<URL to workbook> '", seguido de "no se puede obtener una conexión".  
  
 Para determinar la versión del libro, ábralo en Excel y compruebe qué proveedor de datos se especifica en la cadena de conexión. Un libro de SQL Server 2008 R2 usa MSOLAP.4 como su proveedor de datos.  
  
 Para evitar este problema, puede actualizar el libro. Opcionalmente, puede instalar las bibliotecas cliente de la versión SQL Server 2008 R2 de Analysis Services en los equipos físicos que ejecutan PowerPivot para SharePoint o Excel Services:  
  
 [Instalar el proveedor OLE DB de Analysis Services en servidores de SharePoint](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)  
  
 **Escenario 2b: Excel Services se ejecuta en un servidor de aplicaciones que tiene una versión incorrecta de las bibliotecas de cliente**  
  
 De forma predeterminada, SharePoint Server 2010 instala la versión SQL Server 2008 del proveedor OLE DB de Analysis Services en los servidores de aplicaciones que ejecutan Excel Services. En una granja de servidores que admite el acceso a datos PowerPivot, todos los servidores físicos que ejecutan aplicaciones que solicitan datos de PowerPivot, por ejemplo, Excel Services y PowerPivot para SharePoint, deben usar una versión posterior del proveedor de datos.  
  
 Los servidores que ejecutan PowerPivot para SharePoint obtienen el proveedor de datos OLE DB actualizado automáticamente. Otros servidores, como los que ejecutan una instancia independiente de Excel Services (sin PowerPivot para SharePoint en el mismo equipo), deben aplicar una revisión para usar las bibliotecas más recientes del cliente. Para más información, consulte [Instalar el proveedor OLE DB de Analysis Services en servidores de SharePoint](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).  
  
 **Escenario 3: el controlador de dominio no está disponible**  
  
 La causa podría ser que un controlador de dominio no está disponible para validar la identidad del usuario. Notificaciones del servicio de token de Windows requiere un controlador de dominio para autenticar al usuario de SharePoint en cada conexión. Notificaciones del servicio de token de Windows no utiliza las credenciales almacenadas en memoria caché. Valida la identidad del usuario para cada conexión.  
  
 Puede confirmar la causa de este error en el archivo de registro de SharePoint. Si los registros de SharePoint incluyen el mensaje "No se puede obtener WindowsIdentity de IClaimsIdentity", la identidad del usuario no se pudo autenticar.  
  
 Para evitar este problema, una el equipo al mismo dominio del servidor PowerPivot o instale un controlador de dominio en el equipo local. La segunda solución, instalar el controlador de dominio, le exigirá que cree cuentas de dominio locales para todos los servicios y usuarios. Tendrá que configurar cuentas de servicio y permisos de SharePoint para las cuentas que defina.  
  
 La instalación de un controlador de dominio en el equipo resulta útil si desea utilizar PowerPivot para SharePoint en un estado sin conexión. Para obtener instrucciones detalladas acerca de cómo usar PowerPivot sin conexión, vea la entrada de blog sobre cómo desconectar el servidor PowerPivot de la red [http://www.powerpivotgeek.com](https://go.microsoft.com/fwlink/?LinkId=184241) .  
  
 **Escenario 4: servidor inestable**  
  
 Uno o más servicios pueden estar en un estado incoherente. En algunos casos, al ejecutar IISRESET, se resolverá el problema.  
  
  
