---
title: Configurar alertas para notificar los errores de directiva a los administradores de directivas | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, configure alerts
ms.assetid: e8e60159-d5b0-49d5-91f3-af8e9cb994c1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9eb84ced3bb6313dd5920deaf479925556f08fc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744066"
---
# <a name="configure-alerts-to-notify-policy-administrators-of-policy-failures"></a>Configurar alertas para notificar los errores de directiva a los administradores de directivas
  Cuando las directivas de administración basada en directivas se ejecutan en uno de los tres modos de evaluación automatizados, si se produce la infracción de una directiva, se escribe un mensaje en el registro de eventos. Para que se le notifique cuando este mensaje se escribe en el registro de eventos, puede crear una alerta que se active al detectar el mensaje y permita realizar una acción. La alerta debería detectar los mensajes que se muestran en la tabla siguiente.  
  
|Modo de ejecución|Número de mensaje|  
|--------------------|--------------------|  
|Al cambiar: impedir<br /><br /> (si es Automático)|34050|  
|Al cambiar: impedir<br /><br /> (si es A petición)|34051|  
|Al programar|34052|  
|Al cambiar|34053|  
  
 Si desea configurar una alerta para responder a los mensajes de error de administración basada en directivas, vea los temas siguientes:  
  
-   [Crear un operador](../../ssms/agent/create-an-operator.md)  
  
-   [Create an Alert Using an Error Number](../../ssms/agent/create-an-alert-using-an-error-number.md)  
  
-   [Asignar alertas a un operador](../../ssms/agent/assign-alerts-to-an-operator.md)  
  
## <a name="permissions"></a>Permisos  
 Cuando las directivas se evalúan a petición, se ejecutan en el contexto de seguridad del usuario. Para escribir en el registro de errores, el usuario debe tener los permisos ALTER TRACE o ser miembro del rol fijo de servidor sysadmin. Las directivas que evalúe un usuario que tenga menos privilegios no escribirán en el registro de eventos y no desencadenarán una alerta.  
  
 Los modos de ejecución automatizados se ejecutan como un miembro del rol sysadmin. Esto permite que la directiva se escriba en el registro de errores y se genere una alerta.  
  
## <a name="additional-considerations-about-alerts"></a>Consideraciones adicionales sobre las alertas  
 Tenga en cuenta las consideraciones adicionales siguientes acerca de las alertas:  
  
-   Las alertas solo se generan para las directivas que están habilitadas. Dado que las directivas **A petición** no pueden estar habilitadas, no se generan alertas para las directivas que se ejecutan a petición.  
  
-   Si la acción que desea tomar incluye enviar un mensaje de correo electrónico, debe configurar una cuenta de correo. Recomendamos usar Correo electrónico de base de datos. Para obtener más información sobre cómo configurar Correo electrónico de base de datos, vea [Crear una nueva cuenta de Correo electrónico de base de datos](../database-mail/create-a-database-mail-account.md).  
  
  
