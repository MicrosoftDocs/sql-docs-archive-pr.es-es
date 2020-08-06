---
title: Página Permisos o Elementos protegibles | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.common.permissions.f1
- sql12.swb.SecurableAndEffectPermissions.f1
- sql12.swb.availabilitygroupproperties.permission.f1
- sql12.swb.common.columnperm.f1
- sql12.swb.SecurableAndEffectivePermission.f1
ms.assetid: b3bf077a-bec2-4161-ac0c-460586199906
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 80417c720258833850f07eb67f83f5c47f487ad2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745133"
---
# <a name="permissions-or-securables-page"></a>Página Permisos o Elementos protegibles
  Utilice la página **Permisos** o la página **Elementos protegibles** para ver o establecer los permisos de los elementos protegibles. Esta página se puede abrir desde varias ubicaciones. El contenido de la página puede cambiar ligeramente, dependiendo de cómo se abra la página y de su contenido. La cuadrícula superior de la página puede estar rellena al abrir la página, o bien puede estar vacía. Para agregar elementos a la cuadrícula superior, haga clic en **Buscar**. En la cuadrícula superior, seleccione un elemento y luego establezca los permisos apropiados en la pestaña **Explícito** . Para ver los permisos agregados, use la pestaña **Vigente** .  
  
 Para comprender las combinaciones posibles de elementos protegibles y de entidades de seguridad, vea los vínculos de sintaxis específica de los elementos protegibles en el tema [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql). Para más información, consulte [Securables](securables.md).  
  
## <a name="page-header"></a>Encabezado de página  
 El encabezado de la página **Permisos** o **Elementos protegibles** varía en función del elemento protegible o la entidad de seguridad. Muestra información correspondiente al elemento, como su nombre.  
  
## <a name="upper-grid"></a>Cuadrícula superior  
 La cuadrícula superior contiene uno o más elementos para los que se pueden establecer permisos. Este cuadro de diálogo incluye el botón **Buscar** para seleccionar los objetos o entidades de seguridad que se desean agregar a la cuadrícula superior. El nombre de la cuadrícula puede mostrar **Elementos protegibles** o uno o varios tipos de elementos protegibles o entidades de seguridad. Las columnas mostradas en la cuadrícula superior varían dependiendo de la entidad de seguridad o el elemento protegible.  
  
 **Nombre**  
 El nombre de cada entidad de seguridad o elemento protegible que se agrega a la cuadrícula.  
  
 **Tipo**  
 Describe el tipo de cada elemento.  
  
## <a name="explicit-tab"></a>Pestaña Explícito  
 La pestaña **Explícito** presenta los posibles permisos del elemento protegible seleccionados en la cuadrícula superior. Para configurar los permisos, active o desactive las casillas **Conceder** (o **Permitir**), **WITH GRANT**y **Denegar** . No todas las opciones de están disponibles para la totalidad de los permisos explícitos.  
  
 **Permisos**  
 Nombre del permiso.  
  
 **Otorgante de permisos**  
 La entidad de seguridad que concedió el permiso.  
  
 **Conceder**  
 Active esta casilla para conceder el permiso al inicio de sesión. Desactívela para revocar el permiso.  
  
 **WITH GRANT**  
 Refleja el estado de la opción WITH GRANT para el permiso indicado. Este cuadro es de solo lectura. Para aplicar este permiso, use la instrucción [GRANT](/sql/t-sql/statements/grant-transact-sql) .  
  
 **Deny**  
 Active esta casilla para denegar el permiso al inicio de sesión. Desactívela para revocar el permiso.  
  
 **Permisos de columna**  
 Para los objetos que contienen columnas (como tablas, vistas o funciones con valores de tabla), el botón **Permisos de columna** abre el cuadro de diálogo **Permisos de columna** . En este cuadro de diálogo, puede establecer las opciones **Conceder**, **Permitir**o **Denegar** para columnas individuales de la tabla o la vista. Esta opción no está disponible para todos los tipos de objetos o permisos.  
  
## <a name="effective-tab"></a>Pestaña Vigente  
 Los permisos que una entidad de seguridad ha relacionado con un elemento protegible pueden proceder de permisos establecidos para varias entidades de seguridad distintas. Por ejemplo, un inicio de sesión podría recibir permisos de forma individual y también como miembro de un grupo. La pestaña **Vigente** muestra el resultado de combinar los permisos explícitos y los permisos recibidos de pertenencia a grupos o roles. Los permisos Grant están agregados. Un permiso Deny invalida todos los permisos Grant.  
  
 **Permisos**  
 Nombre del permiso.  
  
 **Columna**  
 Los nombres de las columnas afectadas por el permiso.  
  
## <a name="see-also"></a>Consulte también  
 [Roles de nivel de base de datos](authentication-access/database-level-roles.md)   
 [Centro de seguridad para el Motor de base de datos de SQL Server y Azure SQL Database](security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
