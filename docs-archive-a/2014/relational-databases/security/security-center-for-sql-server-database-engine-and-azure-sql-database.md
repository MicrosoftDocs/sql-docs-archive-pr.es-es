---
title: Centro de seguridad para el motor de base de datos SQL Server y Azure SQL Database | Microsoft Docs
ms.custom: ''
ms.date: 09/23/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- Security [SQL Server]
helpviewer_keywords:
- SQL Server, security
- security [SQL Server]
- database security [SQL Server]
- databases [SQL Server], security
ms.assetid: dfb39d16-722a-4734-94bb-98e61e014ee7
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 3eeea022cff74d2ca8ddb636d9f83e4d369529bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745122"
---
# <a name="security-center-for-sql-server-database-engine-and-azure-sql-database"></a>Centro de seguridad para el motor de base de datos SQL Server y la base de datos SQL Azure
  En esta página se proporcionan vínculos para ayudarle a buscar la información que necesita sobre seguridad y protección en [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]y [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)].  
  
> [!NOTE]  
>  Las capacidades de [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] siguen mejorando. Consulte la versión más reciente de este tema para obtener la información más actual de [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
|Autenticación: ¿Quién es usted?|Autorización: ¿Qué puede hacer?|Cifrado: Almacenamiento de datos secretos|Seguridad de conexión: Restringir y proteger|Auditoría: Acceso a la grabación|  
|----------------------------------|-------------------------------------|-------------------------------------|---------------------------------------------------|--------------------------------|  
|**¿Quién autentica?**<br /><br /> [![Mapa del Centro de seguridad, autenticación de Windows](../../database-engine/media/security-center-map-windows-authenticaion.png "Mapa del Centro de seguridad, autenticación de Windows")](https://msdn.microsoft.com/library/ms144284.aspx)<br /><br /> <br /><br /> [![Mapa del Centro de seguridad, autenticación de SQL Server](../../database-engine/media/security-center-map-sql-authenticaion.png "Mapa del Centro de seguridad, autenticación de SQL Server")](https://msdn.microsoft.com/library/ms144284.aspx)<br /><br /> **¿Dónde se autentica?**<br /><br /> [![Mapa del Centro de seguridad, inicios de sesión y usuarios](../../database-engine/media/security-center-map-logins-users.png "Mapa del Centro de seguridad, inicios de sesión y usuarios")](https://msdn.microsoft.com/library/aa337562.aspx)<br /><br /> <br /><br /> [![Mapa del Centro de seguridad, usuarios de base de datos independiente](../../database-engine/media/security-center-map-contained-users.png "Mapa del Centro de seguridad, usuarios de base de datos independiente")](https://msdn.microsoft.com/library/ff929188.aspx)<br /><br /> **Utilizando otras identidades**<br /><br /> [![Mapa del Centro de seguridad, credenciales](../../database-engine/media/security-center-map-credentials.png "Mapa del Centro de seguridad, credenciales")](https://msdn.microsoft.com/library/ms161950.aspx)<br /><br /> [![Mapa del Centro de seguridad, operación EXECUTE AS LOGIN](../../database-engine/media/security-center-map-exec-as-login.png "Mapa del Centro de seguridad, operación EXECUTE AS LOGIN")](https://msdn.microsoft.com/library/ms181362.aspx)<br /><br /> [![Mapa del Centro de seguridad, operación EXECUTE AS USER](../../database-engine/media/security-center-map-exec-as-user.png "Mapa del Centro de seguridad, operación EXECUTE AS USER")](https://msdn.microsoft.com/library/ms181362.aspx)<br /><br /> ![Marcador de posición](../../database-engine/media/security-center-map-blankplaceholder.png "Marcador de posición")<br /><br /> ![Marcador de posición](../../database-engine/media/security-center-map-blankplaceholder.png "Marcador de posición")<br /><br /> ![Marcador de posición](../../database-engine/media/security-center-map-blankplaceholder.png "Marcador de posición")<br /><br /> ![Marcador de posición](../../database-engine/media/security-center-map-blankplaceholder.png "Marcador de posición")|**Conceder, revocar y denegar permisos**<br /><br /> [![Mapa del Centro de seguridad, clases protegibles](../../database-engine/media/security-center-map-securable-classes.png "Mapa del Centro de seguridad, clases protegibles")](https://msdn.microsoft.com/library/ms190401.aspx)<br /><br /> [![Mapa del Centro de seguridad, permisos de servidor](../../database-engine/media/security-center-map-srv-perms.png "Mapa del Centro de seguridad, permisos de servidor")](https://msdn.microsoft.com/library/ms191291.aspx)<br /><br /> [![Mapa del Centro de seguridad, permisos de base de datos](../../database-engine/media/security-center-map-db-perms.png "Mapa del Centro de seguridad, permisos de base de datos")](https://msdn.microsoft.com/library/ms191291.aspx)<br /><br /> **Seguridad por roles**<br /><br /> [![Mapa del Centro de seguridad, roles de servidor](../../database-engine/media/security-center-map-srv-roles.png "Mapa del Centro de seguridad, roles de servidor")](https://msdn.microsoft.com/library/ms188659.aspx)<br /><br /> [![Mapa del Centro de seguridad, roles de base de datos](../../database-engine/media/security-center-map-db-roles.png "Mapa del Centro de seguridad, roles de base de datos")](https://msdn.microsoft.com/library/ms189121.aspx)<br /><br /> `Restricting Data Access to Selected Data Elements`<br /><br /> [![Mapa del Centro de seguridad, Vistas y Procedimientos](../../database-engine/media/security-center-map-view-procs.png "Mapa del Centro de seguridad, Vistas y Procedimientos")](https://msdn.microsoft.com/library/ms175503.aspx)<br /><br /> [![Mapa del Centro de seguridad, seguridad a nivel de fila](../../database-engine/media/security-center-map-row-level-sec.png "Mapa del Centro de seguridad, seguridad a nivel de fila")](https://msdn.microsoft.com/library/dn765131.aspx)<br /><br /> [![Mapa del Centro de seguridad, Enmascaramiento dinámico de datos](../../database-engine/media/security-center-map-data-masking.png "Mapa del Centro de seguridad, Enmascaramiento dinámico de datos")](https://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)<br /><br /> [![Mapa del Centro de seguridad, objetos firmados](../../database-engine/media/security-center-map-signed-objects.png "Mapa del Centro de seguridad, objetos firmados")](https://msdn.microsoft.com/library/ms181700.aspx)<br /><br /> ![Marcador de posición](../../database-engine/media/security-center-map-blankplaceholder.png "Marcador de posición")|**Cifrado de archivos:**<br /><br /> [![Mapa del Centro de seguridad, BitLocker](../../database-engine/media/security-center-map-bitlocker.png "Mapa del Centro de seguridad, BitLocker")](https://support.microsoft.com/kb/2855131)<br /><br /> [![Mapa del Centro de seguridad, cifrado de NTFS](../../database-engine/media/security-center-map-ntfs-encryp.png "Mapa del Centro de seguridad, cifrado de NTFS")](https://msdn.microsoft.com/library/dd163562.aspx)<br /><br /> [![Mapa del Centro de seguridad, TDE](../../database-engine/media/security-center-map-tde.png "Mapa del Centro de seguridad, TDE")](https://msdn.microsoft.com/library/bb934049.aspx)<br /><br /> [![Mapa del Centro de seguridad, cifrado de copia de seguridad](../../database-engine/media/security-center-map-backup-encryp.png "Mapa del Centro de seguridad, cifrado de copia de seguridad")](https://msdn.microsoft.com/library/dn449489.aspx)<br /><br /> **Orígenes de cifrado**<br /><br /> [![Mapa del Centro de seguridad, EKM](../../database-engine/media/security-center-map-ekm.png "Mapa del Centro de seguridad, EKM")](https://msdn.microsoft.com/library/bb895340.aspx)<br /><br /> [![Mapa del Centro de seguridad, Azure Key Vault](../../database-engine/media/security-center-map-key-vault.png "Mapa del Centro de seguridad, Azure Key Vault")](https://azure.microsoft.com/documentation/articles/key-vault-get-started/)<br /><br /> **Cifrado de claves de datos & de columnas**<br /><br /> [![Asignación de Security Center cifrar por certificado](../../database-engine/media/security-center-map-cert.png "Asignación de Security Center cifrar por certificado")](https://msdn.microsoft.com/library/ms188061.aspx)<br /><br /> [![Mapa del Centro de seguridad, cifrado mediante clave simétrica](../../database-engine/media/security-center-map-sym-key.png "Mapa del Centro de seguridad, cifrado mediante clave simétrica")](https://msdn.microsoft.com/library/ms174361.aspx)<br /><br /> [![Mapa del Centro de seguridad, cifrado mediante clave asimétrica](../../database-engine/media/security-center-map-asym-key.png "Mapa del Centro de seguridad, cifrado mediante clave asimétrica")](https://msdn.microsoft.com/library/ms186950.aspx)<br /><br /> [![Mapa del Centro de seguridad, cifrado mediante frase de contraseña](../../database-engine/media/security-center-map-passphrase.png "Mapa del Centro de seguridad, cifrado mediante frase de contraseña")](https://msdn.microsoft.com/library/ms190357.aspx)|**Protección de Firewall**<br /><br /> [![Mapa del Centro de seguridad, Firewall de Windows](../../database-engine/media/security-center-map-windows-firewall.png "Mapa del Centro de seguridad, Firewall de Windows")](https://msdn.microsoft.com/library/ms175043.aspx)<br /><br /> [![Mapa del Centro de seguridad, firewall del servicio](../../database-engine/media/security-center-map-service-firewall.png "Mapa del Centro de seguridad, firewall del servicio")](https://msdn.microsoft.com/library/azure/ee621782.aspx)<br /><br /> [![Mapa del Centro de seguridad, firewall de base de datos](../../database-engine/media/security-center-map-db-firewall.png "Mapa del Centro de seguridad, firewall de base de datos")](https://msdn.microsoft.com/library/azure/ee621782.aspx)<br /><br /> **Cifrar los datos en tránsito**<br /><br /> [![Mapa del Centro de seguridad, SSL forzada](../../database-engine/media/security-center-map-forced-ssl.png "Mapa del Centro de seguridad, SSL forzada")](https://msdn.microsoft.com/library/ms191192.aspx)<br /><br /> [![Mapa del Centro de seguridad, SSL opcional](../../database-engine/media/security-center-map-opt-ssl.png "Mapa del Centro de seguridad, SSL opcional")](https://msdn.microsoft.com/library/ms191192.aspx)<br /><br /> ![Marcador de posición](../../database-engine/media/security-center-map-blankplaceholder.png "Marcador de posición")<br /><br /> ![Marcador de posición](../../database-engine/media/security-center-map-blankplaceholder.png "Marcador de posición")<br /><br /> ![Marcador de posición](../../database-engine/media/security-center-map-blankplaceholder.png "Marcador de posición")<br /><br /> ![Marcador de posición](../../database-engine/media/security-center-map-blankplaceholder.png "Marcador de posición")<br /><br /> ![Marcador de posición](../../database-engine/media/security-center-map-blankplaceholder.png "Marcador de posición")<br /><br /> ![Marcador de posición](../../database-engine/media/security-center-map-blankplaceholder.png "Marcador de posición")<br /><br /> ![Marcador de posición](../../database-engine/media/security-center-map-blankplaceholder.png "Marcador de posición")|**Auditoría automatizada**<br /><br /> [![Mapa del Centro de seguridad, auditoría de SQL Server](../../database-engine/media/security-center-map-sql-audit.png "Mapa del Centro de seguridad, auditoría de SQL Server")](https://msdn.microsoft.com/library/cc280386.aspx)<br /><br /> [![Mapa del Centro de seguridad, auditoría de SQL Database](../../database-engine/media/security-center-map-sqldb-audit.png "Mapa del Centro de seguridad, auditoría de SQL Database")](https://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)<br /><br /> **Auditoría personalizada**<br /><br /> ![Marcador de posición](../../database-engine/media/security-center-map-blankplaceholder.png "Marcador de posición")<br /><br /> [![Mapa del Centro de seguridad, desencadenadores](../../database-engine/media/security-center-map-triggers.png "Mapa del Centro de seguridad, desencadenadores")](https://msdn.microsoft.com/library/ms175941.aspx)<br /><br /> **Cumplimiento normativo**<br /><br /> [![SecCtrCompliance](../../database-engine/media/secctrcompliance.png "SecCtrCompliance")](https://azure.microsoft.com/support/trust-center/services/)<br /><br /> ![Marcador de posición](../../database-engine/media/security-center-map-blankplaceholder.png "Marcador de posición")<br /><br /> ![Marcador de posición](../../database-engine/media/security-center-map-blankplaceholder.png "Marcador de posición")<br /><br /> ![Marcador de posición](../../database-engine/media/security-center-map-blankplaceholder.png "Marcador de posición")<br /><br /> ![Marcador de posición](../../database-engine/media/security-center-map-blankplaceholder.png "Marcador de posición")<br /><br /> ![Marcador de posición](../../database-engine/media/security-center-map-blankplaceholder.png "Marcador de posición")<br /><br /> ![Leyenda del Centro de seguridad](../../database-engine/media/security-center-map-legend.png "Leyenda del Centro de seguridad")|  
  
## <a name="links-to-specific-related-topics"></a>Vínculos a temas relacionados específicos  
 ![Icono pequeño de carpeta de archivos](../../integration-services/media/filefolder-small.gif "Icono pequeño de carpeta de archivos") **autenticación: ¿quién es usted?**  
 **¿Quién se autentica? (Windows o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] )**  
  
-   [Elegir un modo de autenticación](choose-an-authentication-mode.md)  
  
 **Autenticación en la base de datos maestra** (inicios de sesión y usuarios de base de datos)  
  
-   [Crear un inicio de sesión de SQL Server](authentication-access/create-a-login.md)  
  
-   [Administración de bases de datos e inicios de sesión en Azure SQL Database](https://msdn.microsoft.com/library/ee336235.aspx)  
  
-   [Crear un usuario de base de datos](authentication-access/create-a-database-user.md)  
  
 **Autenticación en una base de datos de usuario**  
  
-   [Usuarios de base de datos independientes: hacer que la base de datos sea portátil](contained-database-users-making-your-database-portable.md)  
  
 **Utilizando otras identidades**  
  
-   [Credenciales &#40;motor de base de datos&#41;](authentication-access/credentials-database-engine.md)  
  
-   [Ejecutar como otro inicio de sesión](/sql/t-sql/statements/execute-as-transact-sql)  
  
-   [Ejecutar como otro usuario de base de datos](/sql/t-sql/statements/execute-as-transact-sql)  
  
 ![Icono pequeño de carpeta de archivos](../../integration-services/media/filefolder-small.gif "Icono pequeño de carpeta de archivos") **cifrado: almacenamiento de datos secretos**  
 **Cifrado de archivos:**  
  
-   [BitLocker (nivel de unidad)](https://support.microsoft.com/kb/2855131)  
  
-   [Cifrado de NTFS (nivel de carpeta)](https://msdn.microsoft.com/library/dd163562.aspx)  
  
-   [Cifrado de datos transparente (nivel de archivo)](encryption/transparent-data-encryption.md)  
  
-   [Cifrado de copia de seguridad (nivel de archivo)](../backup-restore/backup-encryption.md)  
  
 **Orígenes de cifrado**  
  
-   [Módulo de administración extensible de claves](encryption/extensible-key-management-ekm.md)  
  
-   [Claves almacenadas en el Almacén de claves de Azure](encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
 **Cifrado de columna, datos y claves**  
  
-   [Cifrar mediante certificados](/sql/t-sql/functions/encryptbycert-transact-sql)  
  
-   [Cifrar mediante clave asimétrica](/sql/t-sql/functions/encryptbyasymkey-transact-sql)  
  
-   [Cifrar mediante clave simétrica](/sql/t-sql/functions/encryptbykey-transact-sql)  
  
-   [Cifre mediante frase de contraseña](/sql/t-sql/functions/encryptbypassphrase-transact-sql)  
  
 ![Icono pequeño de carpeta de archivos](../../integration-services/media/filefolder-small.gif "Icono pequeño de carpeta de archivos") **autorización: ¿Qué puede hacer?**  
 **Conceder, revocar y denegar permisos**  
  
-   [Jerarquía de permisos &#40;motor de base de datos&#41;](permissions-hierarchy-database-engine.md)  
  
-   [Permisos](permissions-database-engine.md)  
  
-   [Elementos protegibles](securables.md)  
  
 **Seguridad por roles**  
  
-   [Roles de nivel de servidor](authentication-access/server-level-roles.md)  
  
-   [Roles de nivel de base de datos](authentication-access/database-level-roles.md)  
  
 `Restricting Data Access to Selected Data Elements`  
  
-   Restricción del acceso a datos mediante [Vistas](../views/views.md) y [Procedimientos](../stored-procedures/stored-procedures-database-engine.md)  
  
-   [Seguridad de nivel de fila](https://msdn.microsoft.com/library/azure/dn765131.aspx)  
  
-   [Enmascaramiento de datos dinámicos](https://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)  
  
-   [Objetos firmados](/sql/t-sql/statements/add-signature-transact-sql)  
  
 ![Icono pequeño de carpeta de archivos](../../integration-services/media/filefolder-small.gif "Icono pequeño de carpeta de archivos") **seguridad de conexión: restringir y proteger**  
 **Protección de Firewall**  
  
-   [Configuración de Firewall de Windows para el acceso al motor de base de datos](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)  
  
-   [Configuración de firewall de la base de datos SQL Azure](/sql/relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database)  
  
-   [Configuración de Firewall del servicio Azure](/sql/relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database)  
  
 **Cifrar los datos en tránsito**  
  
-   [Capa de sockets seguros para el motor de base de datos](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)  
  
-   [Capa de sockets seguros para la base de datos SQL](https://msdn.microsoft.com/library/azure/ff394108.aspx)  
  
 ![Icono pequeño de carpeta de archivos](../../integration-services/media/filefolder-small.gif "Icono pequeño de carpeta de archivos") **Auditoría: acceso de grabación**  
 **Auditoría automatizada**  
  
-   [SQL Server Audit &#40;motor de base de datos&#41;](auditing/sql-server-audit-database-engine.md)  
  
-   [Auditoría de base de datos SQL](https://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)  
  
 **Implementación de auditoría personalizada**  
  
-   Crear [DDL Triggers](../triggers/ddl-triggers.md) y [DML Triggers](../triggers/dml-triggers.md)  
  
 ![Icono pequeño de carpeta de archivos](../../integration-services/media/filefolder-small.gif "Icono pequeño de carpeta de archivos") **cumplimiento**  
 **SQL Server**  
  
-   [criterios comunes](https://go.microsoft.com/fwlink/?LinkId=616319)  
  
 **SQL Database**  
  
-   [Centro de confianza de Microsoft Azure: Cumplimiento según la característica](https://azure.microsoft.com/support/trust-center/services/)  
  
## <a name="see-also"></a>Consulte también  
 [Proteger SQL Server](securing-sql-server.md)   
 [Entidades de seguridad &#40;motor de base de datos&#41;](authentication-access/principals-database-engine.md)   
 [Certificados y claves asimétricas de SQL Server](sql-server-certificates-and-asymmetric-keys.md)   
 [Cifrado de SQL Server](encryption/sql-server-encryption.md)   
 [Configuración de Área expuesta](surface-area-configuration.md)   
 [Contraseñas seguras](strong-passwords.md)   
 [Propiedad de base de datos TRUSTWORTHY](trustworthy-database-property.md)   
 [Características y tareas del motor de base de datos](../../database-engine/database-engine-features-and-tasks.md)  
  
  
