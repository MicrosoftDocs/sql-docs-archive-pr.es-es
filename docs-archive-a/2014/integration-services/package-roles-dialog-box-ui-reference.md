---
title: Referencia de la interfaz de usuario del cuadro de diálogo roles de paquete | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtsserver.packageroles.f1
helpviewer_keywords:
- Package Roles dialog box
ms.assetid: 63f13416-c0aa-4480-a336-ef1e6e31a860
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 389b29ddee5674af7ecd106f4f82d61bbb3a0f36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87747131"
---
# <a name="package-roles-dialog-box-ui-reference"></a>Referencia de la interfaz de usuario del cuadro de diálogo Roles del paquete
  Use el cuadro de diálogo **Roles de paquete** , disponible en [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], para especificar los roles de base de datos que tienen acceso de lectura al paquete y los roles de base de datos que tienen acceso de escritura al paquete. Los roles de base de datos se aplican solo a paquetes almacenados en la base de datos [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **msdb** database.  
  
 Para obtener más información sobre los roles de base de datos de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] y sus permisos, vea [Roles de Integration Services &#40;servicio SSIS&#41;](security/integration-services-roles-ssis-service.md).  
  
 Los roles enumerados en el cuadro de diálogo son los roles de base de datos actuales de la base de datos del sistema **msdb** . Si no se seleccionan roles, se aplican los roles de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] predeterminados. De manera predeterminada, el rol de lector incluye **db_ssisadmin**, **db_ssisoperator**y el usuario que creó el paquete. Un usuario que sea miembro de uno de estos roles o que haya creado los paquetes puede enumerar, ver, exportar y ejecutar paquetes. De manera predeterminada, el rol de escritor incluye **db_ssisadmin** y el usuario que creó el paquete. Un usuario que sea miembro de este rol y el usuario que creó los paquetes pueden importar, eliminar y cambiar paquetes.  
  
 La columna **ownersid** de la tabla **sysssispackages** contiene el identificador de seguridad único del usuario que creó el paquete.  
  
## <a name="options"></a>Opciones  
 **Nombre del paquete**  
 Especifique el nombre del paquete.  
  
 **Rol de lector**  
 Seleccione un rol de la lista.  
  
 **Rol de escritor**  
 Seleccione un rol de la lista.  
  
## <a name="see-also"></a>Consulte también  
 [Roles de nivel de base de datos](../relational-databases/security/authentication-access/database-level-roles.md)   
 [Información general sobre seguridad &#40;Integration Services&#41;](security/security-overview-integration-services.md)  
  
  
