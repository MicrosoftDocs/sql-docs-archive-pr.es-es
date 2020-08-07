---
title: Replicación de datos en columnas cifradas (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], replicating data
- encryption [SQL Server replication]
- publishing [SQL Server replication], encrypted columns
ms.assetid: d1f8f586-e5a3-4a71-9391-11198d42bfa3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2e1528d81faa352fdcdf37abe9ad93fda190445c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746241"
---
# <a name="replicate-data-in-encrypted-columns-sql-server-management-studio"></a>Replicar datos en columnas cifradas (SQL Server Management Studio)
  La replicación le permite publicar datos de columna cifrados. Para descifrar y usar estos datos en el suscriptor, la clave usada para cifrar los datos en el publicador también debe estar presente en el suscriptor. La replicación no ofrece un mecanismo de seguridad para transportar las claves de cifrado. Debe volver a crear manualmente la clave de cifrado en el suscriptor. En este tema se muestra cómo cifrar una columna en el publicador y asegurarse de que la clave de cifrado esté disponible en el suscriptor.  
  
 Los pasos básicos son los siguientes:  
  
1.  Cree la clave simétrica en el publicador.  
  
2.  Cifre los datos de la columna con la clave simétrica.  
  
3.  Publique la tabla con la columna cifrada.  
  
4.  Suscríbase a la publicación.  
  
5.  Inicialice la suscripción.  
  
6.  Vuelva a crear la clave simétrica en el suscriptor con los mismos valores para ALGORITHM, KEY_SOURCE e IDENTITY_VALUE que en el paso 1.  
  
7.  Obtenga acceso a los datos de columna cifrados.  
  
> [!NOTE]  
>  Debe usar una clave simétrica para cifrar los datos de columna. La propia clave simétrica puede protegerse mediante distintos métodos en el publicador y el suscriptor.  
  
### <a name="to-create-and-replicate-encrypted-column-data"></a>Para crear y replicar los datos de columna cifrados  
  
1.  En el publicador, ejecute [CREATE SYMMETRIC KEY](/sql/t-sql/statements/create-symmetric-key-transact-sql).  
  
    > [!IMPORTANT]  
    >  El valor de KEY_SOURCE son datos importantes que pueden utilizarse para volver a crear la clave simétrica y descifrar los datos. KEY_SOURCE siempre debe almacenarse y transportarse de forma segura.  
  
2.  Ejecute [OPEN SYMMETRIC KEY](/sql/t-sql/statements/open-symmetric-key-transact-sql) para abrir la nueva clave.  
  
3.  Use la función [EncryptByKey](/sql/t-sql/functions/encryptbykey-transact-sql) para cifrar los datos de columna en el publicador.  
  
4.  Ejecute [CLOSE SYMMETRIC KEY](/sql/t-sql/statements/close-symmetric-key-transact-sql) para cerrar la clave.  
  
5.  Publique la tabla que contiene la columna cifrada. Para obtener más información, vea [Crear una suscripción](../publish/create-a-publication.md).  
  
6.  Suscríbase a la publicación. Para obtener más información, vea [Crear una suscripción de extracción](../create-a-pull-subscription.md) o [Crear una suscripción de inserción](../create-a-push-subscription.md).  
  
7.  Inicialice la suscripción. Para más información, consulte [Crear y aplicar la instantánea inicial](../create-and-apply-the-initial-snapshot.md).  
  
8.  En el suscriptor, ejecute [CREATE SYMMETRIC KEY](/sql/t-sql/statements/create-symmetric-key-transact-sql) con los mismos valores para ALGORITHM, KEY_SOURCE e IDENTITY_VALUE que en el paso 1. Puede especificar un valor distinto para ENCRYPTION BY.  
  
    > [!IMPORTANT]  
    >  El valor de KEY_SOURCE son datos importantes que pueden utilizarse para volver a crear la clave simétrica y descifrar los datos. KEY_SOURCE siempre debe almacenarse y transportarse de forma segura.  
  
9. Ejecute [OPEN SYMMETRIC KEY](/sql/t-sql/statements/open-symmetric-key-transact-sql) para abrir la nueva clave.  
  
10. Use la función [DecryptByKey](/sql/t-sql/functions/decryptbykey-transact-sql) para descifrar los datos replicados en el suscriptor.  
  
11. Ejecute [CLOSE SYMMETRIC KEY](/sql/t-sql/statements/close-symmetric-key-transact-sql) para cerrar la clave.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se crea una clave simétrica, un certificado que se usa para ayudar a proteger la clave simétrica y una clave maestra. Estas claves se crean en la base de datos de publicaciones y, a continuación, se usan para crear una columna cifrada (EncryptedCreditCardApprovalCode) en la tabla `SalesOrderHeader` . Esta columna se publica en la publicación AdvWorksSalesOrdersMerge en lugar de en la columna CreditCardApprovalCode no cifrada. Cuando sea posible, pida a los usuarios que proporcionen credenciales de seguridad en tiempo de ejecución. Si debe almacenar las credenciales en un archivo de script, proteja el archivo para evitar el acceso no autorizado.  
  
 [!code-sql[HowTo#sp_PublishEncryptedColumn](../../../snippets/tsql/SQL15/replication/howto/tsql/publishencryptedcolumn.sql#sp_publishencryptedcolumn)]  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se vuelve a crear la misma clave simétrica en la base de datos de suscripciones con los mismos valores ALGORITHM, KEY_SOURCE e IDENTITY_VALUE del primer ejemplo. En este ejemplo se da por supuesto que ya ha inicializado una suscripción a la publicación AdvWorksSalesOrdersMerge para replicar la columna cifrada. Cuando sea posible, pida a los usuarios que proporcionen credenciales de seguridad en tiempo de ejecución. Si tiene que almacenar credenciales en un archivo de script, debe proteger el archivo durante el almacenamiento y el transporte para evitar el acceso no autorizado.  
  
 [!code-sql[HowTo#sp_SubscriberEncryptedColumn](../../../snippets/tsql/SQL15/replication/howto/tsql/subscriberencryptedcolumn.sql#sp_subscriberencryptedcolumn)]  
  
## <a name="see-also"></a>Consulte también  
 [Seguridad de Replicación de SQL Server](view-and-modify-replication-security-settings.md)   
 [Crear claves simétricas idénticas en dos servidores](../../security/encryption/create-identical-symmetric-keys-on-two-servers.md)  
  
  
