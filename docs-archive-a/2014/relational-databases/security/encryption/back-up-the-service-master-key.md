---
title: Realizar una copia de seguridad de la clave maestra de servicio | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- service master key [SQL Server], exporting
ms.assetid: f60b917c-6408-48be-b911-f93b05796904
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: b79212040df67c22ae7e34cd380a1a1f1bd10773
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750618"
---
# <a name="back-up-the-service-master-key"></a>Hacer una copia de seguridad de la clave maestra de servicio
  En este tema se describe cómo realizar una copia de seguridad de la clave maestra de servicio en [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mediante [!INCLUDE[tsql](../../../includes/tsql-md.md)]. La clave maestra de servicio es la raíz de la jerarquía de cifrado. Debe realizar una copia de seguridad de la clave maestra de servicio y almacenarla en una ubicación segura y fuera de las instalaciones. Crear esta copia de seguridad debe ser una de las primeras acciones de administración que se realicen en el servidor.  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Limitaciones y restricciones](#Restrictions)  
  
     [Seguridad](#Security)  
  
-   [Para realizar una copia de seguridad de la clave maestra de servicio](#Procedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitaciones y restricciones  
  
-   Es necesario abrir la clave maestra y, por tanto, descifrarla antes de realizar una copia de seguridad de la misma. Si está cifrada con la clave maestra de servicio, la clave maestra no tiene que abrirse explícitamente; sin embargo, si la clave maestra está cifrada únicamente con una contraseña, debe abrirse explícitamente.  
  
-   Se recomienda realizar una copia de seguridad de la clave maestra inmediatamente después de crearla y guardarla en un lugar seguro y alejado de las instalaciones.  
  
###  <a name="security"></a><a name="Security"></a> Seguridad  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permisos  
 Necesita el permiso CONTROL en la base de datos.  
  
##  <a name="using-transact-sql"></a><a name="Procedure"></a> Usar Transact-SQL  
  
#### <a name="to-back-up-the-service-master-key"></a>Para realizar una copia de seguridad de la clave maestra de servicio  
  
1.  En [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], conéctese a la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que contenga la clave maestra de servicio de la que desea hacer una copia de seguridad.  
  
2.  Elija una contraseña que se utilizará para cifrar la clave maestra de servicio en el medio de la copia de seguridad. Esta contraseña se somete a comprobaciones de complejidad. Para obtener más información, vea [Password Policy](../password-policy.md).  
  
3.  Hágase con un medio de copia de seguridad extraíble para guardar una copia de seguridad de la clave.  
  
4.  Identifique un directorio NTFS en el que va a crear la copia de seguridad de la clave. En este directorio creará el archivo indicado en el paso siguiente. El directorio debe estar protegido mediante listas de control de acceso (ACL) muy restrictivas.  
  
5.  En el **Explorador de objetos**, conéctese a una instancia del [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
6.  En la barra de Estándar, haga clic en **Nueva consulta**.  
  
7.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**.  
  
    ```  
    -- Creates a backup of the "AdventureWorks2012" master key.  
    -- Because this master key is not encrypted by the service master key, a password must be specified when it is opened.  
    USE AdventureWorks2012;  
    GO  
    BACKUP SERVICE MASTER KEY TO FILE = 'c:\temp_backups\keys\service_master_ key'   
        ENCRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';  
    GO  
    ```  
  
    > [!NOTE]  
    >  La ruta de acceso de archivo a la clave y la contraseña de la clave (si existe) serán distintas de las que se indica más arriba. Asegúrese de que ambas son específicas para la instalación del servidor y de la clave.  
  
8.  Copie el archivo en el medio de copia de seguridad y compruebe que la copia es correcta.  
  
9. Guarde la copia de seguridad en una ubicación segura fuera de las instalaciones.  
  
 Para obtener más información, vea [OPEN MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/open-master-key-transact-sql) y [BACKUP MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql).  
  
  
