---
title: Seguridad del Agente de registro del LOG | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.LRA.f1
helpviewer_keywords:
- Log Reader Agent Security dialog box
ms.assetid: d6981e74-ddb8-41b8-9ea1-56c2ece63b8a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4be41aa9135e20a334616b9cb9d76a773f8d0e9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87749227"
---
# <a name="log-reader-agent-security"></a>Seguridad del Agente de registro del LOG
  El cuadro de diálogo **Seguridad del Agente de registro del LOG** permite especificar:  
  
-   La cuenta de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows con la que se ejecuta el Agente de registro del LOG en el distribuidor. La cuenta de Windows se denomina también *cuenta de proceso*porque el proceso del agente se ejecuta con dicha cuenta.  
  
-   El contexto en el que el Agente de registro del LOG realiza conexiones al publicador de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La conexión se puede realizar suplantando la cuenta de Windows o en el contexto de la cuenta de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que se especifique.  
  
    > [!NOTE]  
    >  El Agente de registro del LOG realiza conexiones al publicador incluso cuando el publicador y el distribuidor se encuentran en el mismo equipo. El Agente de registro del LOG también realiza conexiones al distribuidor; dichas conexiones se llevan a cabo siempre suplantando la cuenta de Windows con la que se ejecuta el agente.  
  
     Para los publicadores de Oracle, especifique el contexto en que el Agente de registro del LOG se conecta al publicador en el cuadro de diálogo **Propiedades del publicador** (disponible en el cuadro de diálogo **Propiedades del distribuidor** ). Para más información, consulte [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).  
  
 Todas las cuentas deben ser válidas y se debe especificar la contraseña correcta para cada cuenta. Las cuentas y las contraseñas se validan cuando se ejecuta el agente.  
  
## <a name="options"></a>Opciones  
 **Cuenta de proceso**  
 Indique la cuenta de Windows con la que se ejecuta el Agente de registro del LOG en el distribuidor. La cuenta de Windows que especifique debe ser, como mínimo, miembro del rol fijo de base de datos **db_owner** de la base de datos de distribución.  
  
 **Contraseña** y **Confirmar contraseña**  
 Escriba la contraseña de la cuenta de Windows.  
  
 **Conectar al publicador**  
 Seleccione si el Agente de registro del LOG debe realizar conexiones al publicador suplantando la cuenta especificada en el cuadro de texto **Cuenta de proceso** o utilizando una cuenta de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Si selecciona utilizar una cuenta de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , especifique una contraseña y un inicio de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] recomienda que se seleccione la opción de suplantar la cuenta de Windows en lugar de utilizar una cuenta de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 La cuenta de Windows o la cuenta de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizada para conectarse debe ser miembro, como mínimo, del rol fijo de base de datos **db_owner** de la base de datos de publicación.  
  
## <a name="see-also"></a>Consulte también  
 [Administrar inicios de sesión y contraseñas en la replicación](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)   
 [Modelo de seguridad del Agente de replicación](security/replication-agent-security-model.md)   
 [Replication Agents Overview](agents/replication-agents-overview.md)  (Información general sobre los agentes de replicación)  
 [Procedimientos recomendados de seguridad de replicación](security/replication-security-best-practices.md)  
  
  
