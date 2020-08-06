---
title: Propiedades de Protocolos de MSSQLSERVER (pestaña Opciones avanzadas) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: abd5ca68-825f-4c07-b27c-3b3a79d03d74
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1549b773df2fec7dbfece481daeb9228ec35cfd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676287"
---
# <a name="protocols-for-mssqlserver-properties-advanced-tab"></a>Propiedades de Protocolos de MSSQLSERVER (pestaña Opciones avanzadas)
  Utilice la pestaña **Opciones avanzadas** del cuadro de diálogo **Protocolos de las propiedades de MSSQLSERVER** para configurar la **Protección ampliada para la autenticación** para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]. **Protección ampliada** es una característica de los componentes de red implementada por el sistema operativo. **Protección ampliada** está disponible en Windows 7 y Windows Server 2008 R2, y se incluye en los Service Pack para los sistemas operativos anteriores. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] es más seguro cuando las conexiones se realizan con **Extended Protection**. Algunas ventajas de **Protección ampliada** requieren que se seleccione **Forzar cifrado** en la pestaña **Marcadores** .  
  
> [!IMPORTANT]  
>  Windows no habilita la **protección ampliada** de forma predeterminada. Para obtener información acerca de cómo habilitar **Protección ampliada** en Windows, vea el artículo de Knowledge Base, [Protección ampliada para la autenticación](https://go.microsoft.com/fwlink/?LinkId=178431).  
  
 Para obtener más información acerca de cómo configurar otros servicios de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y una descripción completa de **Protección ampliada**, vea la información más reciente de [Microsoft.com](https://go.microsoft.com/fwlink/?LinkId=177752).  
  
 La**Protección ampliada** es plenamente compatible con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client a partir de [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]. Actualmente no se garantiza la compatibilidad de la **Protección ampliada** con otros proveedores de clientes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="options"></a>Opciones  
 **Protección ampliada**  
 Hay tres valores posibles:  
  
-   Cuando se establece en **Desactivado**, **Protección ampliada** se deshabilita. La instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aceptará las conexiones de cualquier cliente independientemente de que esté o no protegido. La configuración**Desactivado** es compatible con los sistemas operativos sin revisiones y anteriores, pero es menos segura. Utilice este valor únicamente cuando sepa que los sistemas operativos clientes no admiten la protección ampliada.  
  
-   Cuando se establece en **Permitido**, la **protección ampliada** se requiere para las conexiones de los sistemas operativos que admiten la **protección ampliada**. Se rechazan las conexiones de las aplicaciones cliente no protegidas que se estén ejecutando en sistemas operativos clientes protegidos. **Protección ampliada** se omite para las conexiones de los sistemas operativos no protegidos. Esta configuración es más segura que **Desactivado**, pero no es la más segura. Utilice esta configuración en entornos mixtos, donde no todos los sistemas operativos o aplicaciones admiten **Protección ampliada** .  
  
-   Cuando se establece en **Requerido**, solo se aceptan las conexiones de las aplicaciones protegidas en sistemas operativos protegidos. Esta configuración es la más segura de las tres opciones, pero los sistemas operativos que no admitan **Protección ampliada** no podrán conectarse a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Se aceptan SPN NTLM**  
 Cuando la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se identifica mediante más de un nombre principal de servicio NTLM (SPN), enumere los SPN aquí como una serie de cadenas separadas por puntos y coma. Por ejemplo, el valor **MSSQLSvc/HostName1.Contoso.com;MSSQLSvc/HostName2.Contoso.com**indica que se permiten los clientes que intentan conectarse a los SPN denominados **MSSQLSvc/HOST1.Contoso.com** y **MSSQLSvc/HOST2.Contoso.com** . La variable tiene una longitud máxima de 2048 caracteres.  
  
## <a name="see-also"></a>Consulte también  
 [Protección ampliada para la autenticación con Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)  
  
  
