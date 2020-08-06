---
title: Habilitar conexiones cifradas en el Motor de base de datos (Administrador de configuración de SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], encrypted
- SSL [SQL Server]
- Secure Sockets Layer (SSL)
- encryption [SQL Server], connections
- cryptography [SQL Server], connections
- certificates [SQL Server], installing
- requesting encrypted connections
- installing certificates
- security [SQL Server], encryption
ms.assetid: e1e55519-97ec-4404-81ef-881da3b42006
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e1653df929e3f8bc67158a0685ce07b8ba65de6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750141"
---
# <a name="enable-encrypted-connections-to-the-database-engine-sql-server-configuration-manager"></a>Habilitar conexiones cifradas en el motor de base de datos (Administrador de configuración de SQL Server)
  En este tema se describe cómo habilitar conexiones cifradas para una instancia de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] mediante la especificación de un certificado para el [!INCLUDE[ssDE](../../includes/ssde-md.md)] utilizando el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . El equipo servidor debe tener un certificado y el equipo cliente debe estar configurado para confiar en la entidad de certificación raíz del certificado. La puesta en servicio es el proceso de instalar un certificado mediante su importación en Windows.  
  
 El certificado debe estar emitido para la **Autenticación de servidor**. El nombre del certificado debe ser el nombre de dominio completo (FQDN) del equipo.  
  
 Los certificados se almacenan localmente para los usuarios del equipo. Si desea instalar un certificado para que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]lo utilice, debe ejecutar el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con la misma cuenta de usuario que el servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , a menos que éste se esté ejecutando como LocalSystem, NetworkService o LocalService, en cuyo caso puede utilizar una cuenta administrativa.  
  
 El cliente debe ser capaz de comprobar la propiedad del certificado utilizado por el servidor. Si el cliente tiene el certificado de clave pública de la entidad de certificación que firmó el certificado del servidor, no es necesario realizar una mayor configuración. [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows incluye los certificados de clave pública de muchas entidades de certificación. Si el certificado del servidor lo firmó una entidad de certificación pública o privada para la que el cliente no tiene certificado de clave pública, debe instalar el certificado de clave pública de esta entidad de certificación.  
  
> [!NOTE]  
>  Si desea utilizar el cifrado con un clúster de conmutación por error, debe instalar el certificado del servidor con el nombre DNS completo del servidor virtual en todos los nodos del clúster de conmutación por error. Por ejemplo, si tiene un clúster de dos nodos, con los nodos denominados test1 *\<your company>* . com y test2. *\<your company>* . com, y tiene un servidor virtual denominado virtsql, debe instalar un certificado para *\<your company>* virtsql. com en ambos nodos. Puede establecer el valor de la opción **ForceEncryption**en **Sí**.  
  
 **En este tema**  
  
-   **Para habilitar conexiones cifradas:**  
  
     [Proporcionar (instalar) un certificado en el servidor](#Provision)  
  
     [Exportar el certificado del servidor](#Export)  
  
     [Configurar el servidor de modo que acepte conexiones cifradas](#ConfigureServerConnections)  
  
     [Configurar el cliente para que solicite conexiones cifradas](#ConfigureClientConnections)  
  
     [Cifrar una conexión desde SQL Server Management Studio](#EncryptConnection)  
  
##  <a name="SSMSProcedure"></a>  
  
###  <a name="to-provision-install-a-certificate-on-the-server"></a><a name="Provision"></a> Para proporcionar (instalar) un certificado en el servidor  
  
1.  En el menú **Inicio** , haga clic en **Ejecutar**y, en el cuadro **abrir** , escriba `MMC` y haga clic en **Aceptar**.  
  
2.  En el menú **Archivo** de la consola MMC, haga clic en **Agregar o quitar complemento**.  
  
3.  En el cuadro de diálogo **Agregar o quitar complemento** , haga clic en **Agregar**.  
  
4.  En el cuadro de diálogo **Agregar un complemento independiente** , haga clic en **Certificados**y, después, en **Agregar**.  
  
5.  En el cuadro de diálogo **Complemento de certificados** , haga clic en **Cuenta de equipo**y, después, en **Finalizar**.  
  
6.  En el cuadro de diálogo **Agregar un complemento independiente** , haga clic en **Cerrar.**  
  
7.  En el cuadro de diálogo **Agregar o quitar complemento** , haga clic en **Aceptar**.  
  
8.  En el complemento **Certificados** , expanda **Certificados**, expanda **Personal**. Tras ello, haga clic con el botón derecho en **Certificados**, seleccione **Todas las tareas**y, finalmente, haga clic en **Importar**.  
  
9. Finalice el **Asistente para importación de certificados**para agregar un certificado al equipo y cierre la consola MMC. Para obtener más información acerca de cómo agregar un certificado a un equipo, vea la documentación de Windows.  
  
###  <a name="to-export-the-server-certificate"></a><a name="Export"></a> Para exportar el certificado del servidor  
  
1.  En el complemento **Certificados** , busque el certificado en la carpeta **Certificados** / **Personal** , haga clic con el botón derecho en **Certificado**, seleccione **Todas las tareas**y, luego, haga clic en **Exportar**.  
  
2.  Complete el **Asistente para exportación de certificados**y guarde el archivo del certificado en una ubicación adecuada.  
  
###  <a name="to-configure-the-server-to-accept-encrypted-connections"></a><a name="ConfigureServerConnections"></a> Para configurar el servidor de modo que acepte conexiones cifradas  
  
1.  En el **Administrador de configuración de SQL Server**, expanda **Configuración de red de SQL Server**, haga clic con el botón derecho en **Protocolos de** _\<server instance>_ y, después, seleccione **Propiedades**.  
  
2.  En el cuadro de diálogo **protocolos para** _\<instance name>_ **propiedades** , en la pestaña **certificado** , seleccione el certificado que desee en el menú desplegable del cuadro **certificado** y, a continuación, haga clic en **Aceptar**.  
  
3.  En la pestaña **Marcas** , en el cuadro **ForceEncryption** , seleccione **Sí**y, a continuación, haga clic en **Aceptar** para cerrar el cuadro de diálogo.  
  
4.  Reinicie el servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
###  <a name="to-configure-the-client-to-request-encrypted-connections"></a><a name="ConfigureClientConnections"></a> Para configurar el cliente de modo que solicite conexiones cifradas  
  
1.  Copie el certificado original o el archivo del certificado exportado en el equipo cliente.  
  
2.  En el equipo cliente, use el complemento **Certificados** para instalar el certificado raíz o el archivo del certificado exportado.  
  
3.  En el panel de la consola, haga clic con el botón derecho en **Configuración de SQL Server Native Client**y, después, haga clic en **Propiedades**.  
  
4.  En la página **Marcas** , en el cuadro **Forzar cifrado de protocolo** , haga clic en **Sí**.  
  
###  <a name="to-encrypt-a-connection-from-sql-server-management-studio"></a><a name="EncryptConnection"></a>Para cifrar una conexión desde SQL Server Management Studio  
  
1.  En la barra de herramientas del Explorador de objetos, haga clic en **Conectar**y, a continuación, en **Motor de base de datos**.  
  
2.  En el cuadro de diálogo **Conectar al servidor** , rellene la información de conexión y, a continuación, haga clic en **Opciones**.  
  
3.  En la pestaña **Propiedades de conexión** , haga clic en **Cifrar conexión**.  
  
  
