---
title: Conexión con SQL Server para eliminación | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 030b10c2-6b88-4c2c-bf67-22994be25a60
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f5f069f7686e8b6fa9176f92c9e2f47be5f2c71a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669811"
---
# <a name="connection-to-sql-server-for-delete"></a>Conexión con SQL Server para eliminación
  Cuando un inicio de sesión sin un rol de base de datos que incluye el permiso de escritura (por ejemplo, el rol **db_owner** ) para la base de datos MSXDBCDC intenta eliminar una instancia CDC de Oracle, se muestra el cuadro de diálogo Conectar con SQL Server.  
  
 En este cuadro de diálogo debe especificar las credenciales para un inicio de sesión que tenga permiso de escritura para la base de datos MSXDBCDC, como el rol de base de datos **db_owner** para eliminar la instancia CDC de Oracle.  
  
 Escriba la información siguiente en el cuadro de diálogo Conectar con SQL Server.  
  
 **Nombre de servidor**  
 Escriba el nombre del servidor donde se encuentra [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Autenticación**  
 Seleccione uno de los siguientes:  
  
-   **Autenticación de Windows**  
  
-   **Autenticación de SQL Server**: si selecciona esta opción, es necesario que escriba el **Inicio de sesión** y la **Contraseña** del usuario de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] al que se conecta.  
  
 **Opciones**  
 Haga clic en la flecha para ver las opciones disponibles que se pueden configurar. Puede elegir dejar estas opciones con el valor predeterminado. Las opciones disponibles son:  
  
-   **Tiempo de espera de la conexión**: escriba el tiempo (en segundos) que el programa espera hasta que se establezca una conexión con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antes de producir un error de tiempo de espera. El valor predeterminado es **15**.  
  
-   **Tiempo de espera de ejecución**: escriba el tiempo (en segundos) que el programa espera hasta que finalice la ejecución de un comando SQL antes de producir un error de tiempo de espera. El valor predeterminado es **30**.  
  
-   **Cifrar conexión**: seleccione **Cifrar conexión** para asegurarse de que la conexión con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que se establece está cifrada para garantizar la privacidad.  
  
-   **Avanzadas**: haga clic en **Avanzadas** y escriba cualquier propiedad de conexión adicional en el cuadro de diálogo Propiedades avanzadas de conexión, si es necesario.  
  
## <a name="see-also"></a>Consulte también  
 [Permisos de conexión con SQL Server necesarios para el servicio CDC](sql-server-connection-required-permissions-for-the-cdc-service.md)  
  
  
