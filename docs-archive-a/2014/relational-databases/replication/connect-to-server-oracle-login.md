---
title: Conexión al servidor (Oracle), Inicio de sesión | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.oracleconnection.login.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 86ed91a1-a07c-46f2-a913-67317ef2255e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 23f5b515fcb1e80416d860e2ff3a2e6be5431819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662838"
---
# <a name="connect-to-server-oracle-login"></a>Conectar al servidor (Oracle), Inicio de sesión
  Use la pestaña **Inicio de sesión** del cuadro de diálogo **Conectar al servidor** para especificar la cuenta desde la que se van a realizar las conexiones del distribuidor de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con el publicador de Oracle. Se debe usar la misma cuenta que se especificó para el esquema de usuario administrativo de replicación al configurar el publicador. Para obtener más información, vea [Configurar un publicador de Oracle](non-sql/configure-an-oracle-publisher.md).  
  
## <a name="options"></a>Opciones  
 **Instancia del servidor**  
 Nombre TNS (Transparent Network Substrate, Sustrato de red transparente) del publicador de Oracle, que se especifica durante la configuración del software de cliente Oracle instalado en el distribuidor.  
  
 **Autenticación**  
 Seleccione **Autenticación estándar de Oracle** (opción recomendada) o **Autenticación de Windows**. Si selecciona **Autenticación de Windows**:  
  
-   El servidor de Oracle debe configurarse de forma que permita conexiones con las credenciales de Windows. Para obtener más información, vea la documentación de Oracle.  
  
-   Debe haber iniciado una sesión con la misma cuenta de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows que especificó para el esquema de usuario administrativo de replicación.  
  
 **Inicio de sesión** y **Contraseña**  
 Si selecciona **Autenticación estándar de Oracle** para la opción **Autenticación** , especifique el nombre de inicio de sesión y la contraseña; deben coincidir con los especificados para el esquema de usuario administrativo de replicación.  
  
## <a name="see-also"></a>Consulte también  
 [Glosario de términos de publicaciones de Oracle](non-sql/glossary-of-terms-for-oracle-publishing.md)  
  
  
