---
title: Editor del administrador de conexiones FTP | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftpconnectionmanager.f1
helpviewer_keywords:
- FTP Connection Manager Editor
ms.assetid: 874b6585-255b-4a43-8396-bb08c3e8ac2b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d14635a4d90c267801f6d372dda5c7bcc7f4869f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87752265"
---
# <a name="ftp-connection-manager-editor"></a>Editor del administrador de conexiones FTP
  Utilice el cuadro de diálogo **Editor del administrador de conexiones FTP** para especificar propiedades de conexión con un servidor FTP.  
  
> [!IMPORTANT]  
>  El administrador de conexiones FTP solo admite la autenticación anónima y la autenticación básica. No es compatible con la autenticación de Windows.  
  
 Para obtener más información acerca del administrador de conexiones FTP, vea [FTP Connection Manager](connection-manager/ftp-connection-manager.md).  
  
## <a name="options"></a>Opciones  
 **Nombre del servidor**  
 Proporcione el nombre del servidor FTP.  
  
 **Puerto de servidor**  
 Especifique el número de puerto del servidor FTP que va a utilizar en la conexión. El valor predeterminado de esta propiedad es **21**.  
  
 **Nombre de usuario**  
 Indique un nombre de usuario para tener acceso al servidor FTP. El valor predeterminado de esta propiedad es **anonymous**.  
  
 **Contraseña**  
 Indique la contraseña para tener acceso al servidor FTP.  
  
 **Tiempo de espera (en segundos)**  
 Especifique el número de segundos que tarda la tarea en agotarse el tiempo de espera. Un valor de **0** indica una cantidad de tiempo infinita. El valor predeterminado de esta propiedad es **60**.  
  
 **Usar modo pasivo**  
 Especifique si inicia la conexión el servidor o el cliente. El servidor inicia la conexión en modo activo y el cliente en modo pasivo. El valor predeterminado de esta propiedad es **active mode**.  
  
 **Reintentos**  
 Especifique el número de veces que la tarea intenta establecer la conexión. Un valor de **0** indica que no existe límite en el número de intentos.  
  
 **Tamaño del fragmento (en KB)**  
 Indique un tamaño de fragmento en kilobytes para transmitir datos.  
  
 **Probar conexión**  
 Después de configurar el Administrador de conexiones FTP, haga clic en **Probar conexión**para confirmar que la conexión es viable.  
  
## <a name="see-also"></a>Consulte también  
 [Referencia de errores y mensajes de Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
