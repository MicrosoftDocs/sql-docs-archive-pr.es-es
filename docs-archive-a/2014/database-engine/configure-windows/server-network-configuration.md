---
title: Configuración de red del servidor| Microsoft Docs
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Named Pipes [SQL Server], configuring
- connections [SQL Server], server network configuration
- Database Engine [SQL Server], network configurations
- server network configuration [SQL Server]
- protocols [SQL Server], choosing
- ports [SQL Server], changing
- server configuration [SQL Server]
ms.assetid: 890c09a1-6dad-4931-aceb-901c02ae34c5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 97acd6deaa251d4eea9ef1e00c0554c13011c469
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748907"
---
# <a name="server-network-configuration"></a>Configuración de red del servidor
  Entre las tareas de configuración de red del servidor se incluyen las siguientes: habilitar protocolos, modificar el puerto o canalización usados por un protocolo, configurar el cifrado, configurar el servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser, mostrar u ocultar [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] en la red y registrar el nombre de la entidad de seguridad del servidor. La mayoría de las veces, no es necesario cambiar la configuración de red del servidor. Solo debe volver a configurar los protocolos de red del servidor si la red tiene requisitos especiales.  
  
 La configuración de red de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se realiza mediante el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Para versiones anteriores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], utilice la Herramienta de red de servidor que se incluye con dichos productos.  
  
## <a name="protocols"></a>Protocolos  
 Utilice el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para habilitar o deshabilitar los protocolos utilizados por [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]y configurar las opciones disponibles para los protocolos. Se puede habilitar más de un protocolo. Debe habilitar todos los protocolos que desea que utilicen los clientes. Todos los protocolos tienen el mismo acceso al servidor. Para obtener información sobre los protocolos que debe usar, vea [Habilitar o deshabilitar un protocolo de red de servidor](enable-or-disable-a-server-network-protocol.md).  
  
### <a name="changing-a-port"></a>Cambiar un puerto  
 Puede configurar los protocolos TCP/IP para que escuchen en un puerto designado. De manera predeterminada, la instancia predeterminada de [!INCLUDE[ssDE](../../includes/ssde-md.md)] escucha en el puerto TCP 1433. Las instancias con nombre de [!INCLUDE[ssDE](../../includes/ssde-md.md)] y [!INCLUDE[ssEW](../../includes/ssew-md.md)] están configuradas para puertos dinámicos. Esto significa que seleccionan un puerto disponible cuando se inicia el servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . El servicio Explorador de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ayuda a los clientes a identificar el puerto cuando se conectan.  
  
 Si se utiliza la configuración para puertos dinámicos, el puerto usado por [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] puede cambiar cada vez que se inicia. Si se conecta a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a través de un firewall, debe abrir el puerto usado por [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para que utilice un puerto específico, así podrá configurar el firewall para que permita la comunicación con el servidor. Para obtener más información, vea [Configurar un servidor para que escuche en un puerto TCP específico &#40;Administrador de configuración de SQL Server&#41;](configure-a-server-to-listen-on-a-specific-tcp-port.md).  
  
### <a name="changing-a-named-pipe"></a>Cambiar una canalización con nombre  
 Puede configurar el protocolo de canalizaciones con nombre para que escuche en una canalización con nombre designada. De forma predeterminada, la instancia predeterminada de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] escucha en la canalización \\\\.\pipe\sql\query para la instancia predeterminada y en \\\\.\pipe\MSSQL$ *\<instancename>* \sql\query para una instancia con nombre. El [!INCLUDE[ssDE](../../includes/ssde-md.md)] solo puede escuchar en una canalización con nombre, pero puede cambiar la canalización a otro nombre si lo desea. El servicio Explorador de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ayuda a los clientes a identificar la canalización cuando se conectan. Para obtener más información, vea [Configurar un servidor para escuchar en una canalización alternativa &#40;Administrador de configuración de SQL Server&#41;](configure-a-server-to-listen-on-an-alternate-pipe.md).  
  
## <a name="force-encryption"></a>Forzar el cifrado  
 El [!INCLUDE[ssDE](../../includes/ssde-md.md)] se puede configurar para requerir el cifrado al comunicarse con aplicaciones cliente. Para obtener más información, vea [Habilitar conexiones cifradas en el motor de base de datos &#40;Administrador de configuración de SQL Server&#41;](enable-encrypted-connections-to-the-database-engine.md).  
  
## <a name="extended-protection-for-authentication"></a>Protección ampliada para la autenticación  
 La compatibilidad con Protección ampliada para la autenticación mediante el uso del enlace de canal y el enlace de servicio está disponible en los sistemas operativos que admiten Protección ampliada. Para obtener más información, vea [Conectar al motor de base de datos con protección ampliada](connect-to-the-database-engine-using-extended-protection.md).  
  
## <a name="authenticating-by-using-kerberos"></a>Autenticar mediante Kerberos  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] admite la autenticación Kerberos. Para obtener más información, vea [Registrar un nombre de entidad de seguridad de servicio para las conexiones con Kerberos](register-a-service-principal-name-for-kerberos-connections.md) y [Microsoft Kerberos Configuration Manager para SQL Server](https://www.microsoft.com/download/details.aspx?id=39046).  
  
### <a name="registering-a-server-principal-name-spn"></a>Registrar un nombre de la entidad de seguridad del servidor (SPN)  
 El servicio de autenticación de Kerberos usa un SPN para autenticar un servicio. Para obtener más información, vea [Registrar un nombre de entidad de seguridad de servicio para las conexiones con Kerberos](register-a-service-principal-name-for-kerberos-connections.md).  
  
 Los SPN también se pueden utilizar para hacer que la autenticación del cliente sea más segura al conectar con NTLM. Para obtener más información, vea [Conectar al motor de base de datos con protección ampliada](connect-to-the-database-engine-using-extended-protection.md).  
  
## <a name="sql-server-browser-service"></a>servicio SQL Server Browser  
 El servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser se ejecuta en el servidor y ayuda a los equipos cliente a encontrar instancias de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. No es necesario configurar el servicio Explorador de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], pero se debe ejecutar según ciertos escenarios de conexión. Para obtener más información sobre cómo usar el Explorador de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vea [Servicio SQL Server Browser &#40;motor de base de datos y SSAS&#41;](sql-server-browser-service-database-engine-and-ssas.md).  
  
## <a name="hiding-sql-server"></a>Ocultar SQL Server  
 Al ejecutarse, el Explorador de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] responde a consultas, con la información de nombre, versión y conexión por cada instancia instalada. Para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la marca **HideInstance** especifica que el Explorador de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no debería responder con información acerca de esta instancia del servidor. Las aplicaciones cliente todavía se pueden conectar, pero deben conocer la información de conexión necesaria. Para obtener más información, vea [Ocultar una instancia del motor de base de datos de SQL Server](../sql-server-database-engine-overview.md).  
  
## <a name="related-content"></a>Contenido relacionado  
 [Configuración de red de cliente](client-network-configuration.md)  
  
 [Administrar el servicio del motor de base de datos](manage-the-database-engine-services.md)  
  
  
