---
title: Administrador de conexiones SMTP | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], SMTP
- SMTP connection manager [Integration Services]
- connection managers [Integration Services], SMTP
ms.assetid: 3795d442-714b-4bbb-9acd-75bf277a468a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f3c090ab672790901baae01ae86f8d22e008b4ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750086"
---
# <a name="smtp-connection-manager"></a>Administrador de conexiones SMTP
  Un administrador de conexiones SMTP permite a un paquete conectarse a un servidor de Protocolo simple de transferencia de correo (SMTP). La tarea Enviar correo que incluye [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] usa un administrador de conexiones SMTP.  
  
 Si utiliza Microsoft Exchange como servidor SMTP, es posible que necesite configurar el administrador de conexiones SMTP para que utilice la autenticación de Windows. Es posible que los servidores Exchange estén configurados para no permitir conexiones SMTP no autenticadas.  
  
## <a name="configuration-the-smtp-connection-manager"></a>Configuración del administrador de conexiones SMTP  
 Cuando agrega un administrador de conexiones SMTP a un paquete, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crea un administrador de conexiones que se resuelve como una conexión SMTP en tiempo de ejecución, establece las propiedades del administrador de conexiones y agrega el administrador de conexiones a la colección `Connections` del paquete. La propiedad `ConnectionManagerType` del administrador de conexiones se establece en `SMTP`.  
  
 Puede configurar el administrador de conexiones SMTP de las maneras siguientes:  
  
-   Proporcionar una cadena de conexión.  
  
-   Especificar el nombre de un servidor SMTP.  
  
-   Especificar el método de autenticación que se va a utilizar.  
  
    > [!IMPORTANT]  
    >  El administrador de conexiones SMTP solo es compatible con la autenticación anónima y la autenticación de Windows. No admite la autenticación básica.  
  
-   Especificar si la comunicación se cifrará mediante SSL (Capa de sockets seguros) al enviar mensajes de correo electrónico.  
  
 Puede establecer propiedades a través del Diseñador de [!INCLUDE[ssIS](../../includes/ssis-md.md)] o mediante programación.  
  
 Para obtener más información sobre las propiedades que puede configurar en el Diseñador de [!INCLUDE[ssIS](../../includes/ssis-md.md)] , vea [Editor del administrador de conexiones SMTP](../smtp-connection-manager-editor.md).  
  
 Para obtener información sobre la configuración de un administrador de conexiones mediante programación, vea <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> y [Agregar conexiones mediante programación](../building-packages-programmatically/adding-connections-programmatically.md).  
  
  
