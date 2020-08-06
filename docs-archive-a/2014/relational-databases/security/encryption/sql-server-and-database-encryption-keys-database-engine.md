---
title: SQL Server y claves de cifrado de base de datos (motor de base de datos) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- keys [SQL Server], database encryption
ms.assetid: 15c0a5e8-9177-484c-ae75-8c552dc0dac0
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: f846e74e0afd89c6bb10a4aa9a23a6420b6a613a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87752053"
---
# <a name="sql-server-and-database-encryption-keys-database-engine"></a>SQL Server y claves de cifrado de base de datos (motor de base de datos)
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] usa claves de cifrado para proteger los datos, las credenciales y la información de conexión que se almacena en una base de datos servidor. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tiene dos tipos de claves: *simétricas* y *asimétricas*. Las claves simétricas utilizan la misma contraseña para cifrar y descifrar los datos. Las claves asimétricas usan una contraseña para cifrar los datos (denominada clave *pública* ) y otra para descifrar los datos (denominada clave *privada* ).  
  
 En [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], las claves de cifrado incluyen una combinación de claves públicas, privadas y simétricas que se utilizan para proteger la información confidencial. La clave simétrica se crea durante la inicialización de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] al iniciar por primera vez la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utiliza la clave para cifrar los datos confidenciales que se almacenan en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. El sistema operativo crea las claves públicas y privadas, y éstas se utilizan para proteger la clave simétrica. Para cada instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que almacena datos confidenciales en una base de datos se crea un par de claves pública y privada.  
  
## <a name="applications-for-sql-server-and-database-keys"></a>Aplicaciones para las claves de SQL Server y las claves de las bases de datos  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tiene dos aplicaciones principales para las claves: una *clave maestra de servicio* (SMK) generada en y para una instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , y una *clave maestra de base de datos* (DMK) usada para una base de datos.  
  
 La clave maestra de servicio se genera automáticamente la primera vez que se inicia la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] y se utiliza para cifrar una contraseña de servidor vinculado, las credenciales y la clave maestra de base de datos. La SMK se cifra mediante la clave del equipo local y la API de protección de datos de Windows (DPAPI). La DPAPI utiliza una clave derivada de las credenciales de Windows de la cuenta de servicio de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] y de las credenciales del equipo. La clave maestra de servicio solo puede descifrarse con la cuenta de servicio en la que se creó o con una entidad de seguridad que tenga acceso a las credenciales del equipo.  
  
 La clave maestra de base de datos es una clave simétrica que se utiliza para proteger las claves privadas de certificados y las claves asimétricas presentes en la base de datos. También se puede utilizar para cifrar los datos, pero sus limitaciones de longitud hacen que sea más práctico utilizar una clave simétrica.  
  
 Al crearla, la clave maestra se cifra mediante el algoritmo Triple DES y una contraseña proporcionada por el usuario. Para habilitar el descifrado automático de la clave maestra, se cifra una copia de la clave mediante la SMK. Esta copia se almacena en la base de datos donde se utiliza y en la base de datos del sistema `master`.  
  
 La copia de la DMK almacenada en la base de datos del sistema `master` se actualiza automáticamente siempre que se modifica la DMK. Sin embargo, este comportamiento predeterminado se puede cambiar con la opción `DROP ENCRYPTION BY SERVICE MASTER KEY` de la instrucción `ALTER MASTER KEY`. Para abrir una DMK que no se haya cifrado con la clave maestra de servicio, debe utilizarse la instrucción `OPEN MASTER KEY` y una contraseña.  
  
## <a name="managing-sql-server-and-database-keys"></a>Administrar las claves de SQL Server y las claves de las bases de datos  
 La administración de las claves de cifrado consiste en crear nuevas claves de base de datos, crear una copia de seguridad de las claves del servidor y de las bases de datos, y saber cuándo y cómo se deben restaurar, eliminar o cambiar dichas claves.  
  
 Para administrar las claves simétricas, puede utilizar las herramientas incluidas en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] para hacer lo siguiente:  
  
-   Crear una copia de seguridad de las claves del servidor y de las claves de las bases de datos que se pueda utilizar para recuperar una instalación de un servidor de informes, o como parte de una migración planeada.  
  
-   Restaurar una clave guardada previamente en una base de datos. Esto permite el acceso de una nueva instancia del servidor a datos existentes que no cifró originalmente.  
  
-   Eliminar los datos cifrados en una base de datos, en el caso poco probable de que ya no se tenga acceso a datos cifrados.  
  
-   Volver a crear claves y volver a cifrar datos en el caso poco probable de que la clave esté en unas circunstancias comprometidas. Como práctica recomendada de seguridad, se deberían volver a crear las claves periódicamente (por ejemplo, cada cierto número de meses) para proteger el servidor de ataques que traten de descifrar las claves.  
  
-   Agregar o quitar una instancia del servidor de una implementación escalada de este servidor en la que varios servidores comparten una sola base de datos y la clave que proporciona el cifrado reversible para dicha base de datos.  
  
## <a name="important-security-information"></a>Información de seguridad importante  
 Para tener acceso a los objetos protegidos por la clave maestra de servicio, es necesaria la cuenta de servicio de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que se utilizó para crear la clave o la cuenta del equipo. Es decir, el equipo vinculado al sistema donde se creó la clave. Puede cambiar la cuenta de servicio de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]*o* la cuenta del equipo sin perder el acceso a la clave. Sin embargo, si cambia ambas, perderá el acceso a la clave maestra de servicio. Si pierde el acceso a la clave maestra de servicio sin uno de estos dos elementos, no podrá descifrar los datos y los objetos cifrados mediante la clave original.  
  
 Las conexiones protegidas con la clave maestra de servicio no se pueden restaurar sin dicha clave.  
  
 El acceso a los objetos y los datos protegidos con la clave maestra de base de datos únicamente requiere la contraseña que se utiliza para proteger la clave.  
  
> [!CAUTION]  
>  Si pierde todo tipo de acceso a las claves descritas anteriormente, también perderá el acceso a los objetos, las conexiones y los datos protegidos mediante esas claves. Puede restaurar la clave maestra de servicio, tal y como se describe en los vínculos que se muestran a continuación, o puede regresar al sistema de cifrado original para recuperar el acceso. No hay ninguna "puerta trasera" para recuperar el acceso.  
  
## <a name="in-this-section"></a>En esta sección  
 [Clave maestra de servicio](service-master-key.md)  
 Proporciona una breve explicación de la clave maestra de servicio y las prácticas recomendadas.  
  
 [Administración extensible de claves &#40;EKM&#41;](extensible-key-management-ekm.md)  
 Explica cómo usar los sistemas de administración de claves de terceros con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="related-tasks"></a>Related Tasks  
 [Hacer una copia de seguridad de la clave maestra de servicio](back-up-the-service-master-key.md)  
  
 [Restaurar la clave maestra de servicio](restore-the-service-master-key.md)  
  
 [Crear la clave maestra de una base de datos](create-a-database-master-key.md)  
  
 [Hacer copias de seguridad de una clave maestra de una base de datos](back-up-a-database-master-key.md)  
  
 [Restaurar una clave maestra de base de datos](restore-a-database-master-key.md)  
  
 [Crear claves simétricas idénticas en dos servidores](create-identical-symmetric-keys-on-two-servers.md)  
  
 [Administración extensible de claves con el Almacén de claves de Azure &#40;SQL Server&#41;](extensible-key-management-using-azure-key-vault-sql-server.md)  
  
 [Habilitar TDE con EKM](enable-tde-on-sql-server-using-ekm.md)  
  
## <a name="related-content"></a>Contenido relacionado  
 [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql)  
  
 [ALTER SERVICE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-service-master-key-transact-sql)  
  
 [Restaurar una clave maestra de base de datos](restore-a-database-master-key.md)  
  
## <a name="see-also"></a>Consulte también  
 [Hacer copia de seguridad y restaurar claves de cifrado de Reporting Services](../../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)   
 [Eliminar y volver a crear claves de cifrado &#40;Administrador de configuración de SSRS&#41;](../../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md)   
 [Agregar y quitar claves de cifrado para implementaciones escaladas &#40;Administrador de configuración de SSRS&#41;](../../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md)   
 [Cifrado de datos transparente &#40;TDE&#41;](transparent-data-encryption.md)  
  
  
