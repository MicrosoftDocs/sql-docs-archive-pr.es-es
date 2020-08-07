---
title: Restaurar una copia de seguridad de base de datos en el modelo de recuperación simple (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full backups [SQL Server]
- database restores [SQL Server], full backups
- backing up databases [SQL Server], full backups
- database backups [SQL Server], full backups
- restoring databases [SQL Server], full backups
ms.assetid: a928fa36-e285-476f-9a7b-6840a8bb7283
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e264dd380c3dff40dacc4eb576d34af5195dec01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745338"
---
# <a name="restore-a-database-backup-under-the-simple-recovery-model-transact-sql"></a>Restaurar una copia de seguridad de base de datos en el modelo de recuperación simple (Transact-SQL)
  En este tema se explica cómo restaurar una copia de seguridad completa de la base de datos.  
  
> [!IMPORTANT]  
>  El administrador del sistema encargado de restaurar la copia de seguridad de la base de datos completa debe ser la única persona que esté utilizando la base de datos que se va a restaurar.  
  
## <a name="prerequisites-and-recommendations"></a>Requisitos previos y recomendaciones  
  
-   Para restaurar una base de datos cifrada, debe tener acceso al certificado o la clave asimétrica que se usó para cifrarla. La base de datos no se puede restaurar sin el certificado o la clave asimétrica. Como resultado, se debe conservar el certificado que se usa para cifrar la clave de cifrado de base de datos mientras se necesite la copia de seguridad. Para obtener más información, consulte [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).  
  
-   Por razones de seguridad, se recomienda no adjuntar ni restaurar bases de datos de orígenes desconocidos o que no sean de confianza. Es posible que dichas bases de datos contengan código malintencionado que podría ejecutar código [!INCLUDE[tsql](../../includes/tsql-md.md)] no deseado o provocar errores al modificar el esquema o la estructura de la base de datos física. Para usar una base de datos desde un origen desconocido o que no sea de confianza, ejecute [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) en la base de datos de un servidor que no sea de producción y examine también el código, como procedimientos almacenados u otro código definido por el usuario, en la base de datos.  
  
## <a name="database-compatibility-level-after-upgrade"></a>Nivel de compatibilidad de la base de datos después de la actualización  
 Los niveles de compatibilidad de las bases de datos **tempdb**, **model**, **msdb** y **Resource** quedan establecidos en el nivel de compatibilidad de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] después de la actualización. La base de datos del sistema **master** conserva el nivel de compatibilidad que tenía antes de la actualización, a menos que dicho nivel sea inferior a 100. Si el nivel de compatibilidad de la base de datos **master** era inferior a 100 antes de la actualización, se establece en 100 después de la misma.  
  
 Si el nivel de compatibilidad de una base de datos de usuario era 100 o superior antes de la actualización, permanece igual después de la misma. Si el nivel de compatibilidad era 90 antes de la actualización, en la base de datos actualizada, el nivel de compatibilidad se establece en 100, que es el nivel de compatibilidad mínimo admitido en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
> [!NOTE]  
>  Las nuevas bases de datos de usuario heredarán el nivel de compatibilidad de la base de datos **model** .  
  
## <a name="procedures"></a>Procedimientos  
  
#### <a name="to-restore-a-full-database-backup"></a>Para restaurar una copia de seguridad completa de la base de datos  
  
1.  Ejecute la instrucción RESTORE DATABASE para restaurar la copia de seguridad completa de la base de datos; para ello, especifique:  
  
    -   El nombre de la base de datos que se va a restaurar.  
  
    -   El dispositivo de copia de seguridad desde el que se restaurará la copia de seguridad completa de la base de datos.  
  
    -   La cláusula NORECOVERY si va a aplicar una copia de seguridad del registro de transacciones o una copia de seguridad diferencial de la base de datos después de restaurar la copia de seguridad completa de la base de datos.  
  
    > [!IMPORTANT]  
    >  Para restaurar una base de datos cifrada, debe tener acceso al certificado o la clave asimétrica que se usó para cifrarla. La base de datos no se puede restaurar sin el certificado o la clave asimétrica. Como resultado, se debe conservar el certificado que se usa para cifrar la clave de cifrado de base de datos mientras se necesite la copia de seguridad. Para obtener más información, consulte [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).  
  
2.  Opcionalmente, especifique:  
  
    -   La cláusula FILE para identificar el conjunto de copia de seguridad en el dispositivo de copia de seguridad con el que se realizará la restauración.  
  
> [!NOTE]  
>  Si restaura una base de datos de una versión anterior en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], la base de datos se actualiza automáticamente. Normalmente, la base de datos está disponible inmediatamente. Pero si la base de datos de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] tiene índices de texto completo, el proceso de actualización los importa, los restablece o los vuelve a generar, en función del valor de la propiedad del servidor  **upgrade_option** . Si la opción de actualización se establece en importar (**upgrade_option** = 2) o en volver a generar (**upgrade_option** = 0), los índices de texto completo no estarán disponibles durante la actualización. Dependiendo de la cantidad de datos que se indicen, la importación puede requerir varias horas y volver a generar puede requerir hasta diez veces más. Observe también que cuando la opción de actualización se establece en importar, se vuelven a generar los índices de texto completo asociados si no se dispone de un catálogo de texto completo. Para cambiar el valor de la propiedad de servidor **upgrade_option** , use [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql).  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 En este ejemplo se restaura la copia de seguridad completa de la base de datos [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] desde una cinta.  
  
### <a name="example"></a>Ejemplo  
  
```  
USE master;  
GO  
RESTORE DATABASE AdventureWorks2012  
   FROM TAPE = '\\.\Tape0';  
GO  
```  
  
## <a name="see-also"></a>Consulte también  
 [Restauraciones de base de datos completas &#40;modelo de recuperación completa&#41;](complete-database-restores-full-recovery-model.md)   
 [Restauraciones de base de datos completas &#40;modelo de recuperación simple&#41;](complete-database-restores-simple-recovery-model.md)   
 [Copias de seguridad completas de bases de datos &#40;SQL Server&#41;](full-database-backups-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [Historial de copias de seguridad e información de encabezados &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md)   
 [Volver a generar bases de datos del sistema](../databases/system-databases.md)  
  
  
