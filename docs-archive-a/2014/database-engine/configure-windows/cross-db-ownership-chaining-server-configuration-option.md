---
title: cross db ownership chaining (opción de configuración del servidor) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cross-database ownership chaining
- cross db ownership chaining option
- chaining ownership
ms.assetid: 7b2d49f2-b91c-4aee-a52b-6cc49bed03af
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cfb768065cc0aa2aaa7aed0f996b18e46f1da7ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673897"
---
# <a name="cross-db-ownership-chaining-server-configuration-option"></a><span data-ttu-id="433cf-102">cross db ownership chaining (opción de configuración del servidor)</span><span class="sxs-lookup"><span data-stu-id="433cf-102">cross db ownership chaining Server Configuration Option</span></span>
  <span data-ttu-id="433cf-103">Use la opción **cross db ownership chaining** para configurar el encadenamiento de propiedad entre bases de datos para una instancia de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="433cf-103">Use the **cross db ownership chaining** option to configure cross-database ownership chaining for an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="433cf-104">Esta opción del servidor permite controlar el encadenamiento de propiedad entre bases de datos en el nivel de base de datos o para todas las bases de datos:</span><span class="sxs-lookup"><span data-stu-id="433cf-104">This server option allows you to control cross-database ownership chaining at the database level or to allow cross-database ownership chaining for all databases:</span></span>  
  
-   <span data-ttu-id="433cf-105">Cuando la opción **Encadenamiento de propiedad entre bases de datos** está desactivada (0) para la instancia, el encadenamiento de propiedad entre bases de datos se deshabilita para todas las bases de datos.</span><span class="sxs-lookup"><span data-stu-id="433cf-105">When **cross db ownership chaining** is off (0) for the instance, cross-database ownership chaining is disabled for all databases.</span></span>  
  
-   <span data-ttu-id="433cf-106">Cuando la opción **Encadenamiento de propiedad entre bases de datos** está activada (1) para la instancia, el encadenamiento de propiedad entre bases de datos se habilita para todas las bases de datos.</span><span class="sxs-lookup"><span data-stu-id="433cf-106">When **cross db ownership chaining** is on (1) for the instance, cross-database ownership chaining is on for all databases.</span></span>  
  
-   <span data-ttu-id="433cf-107">Puede establecer el encadenamiento de propiedad entre bases de datos para bases de datos específicas mediante la cláusula SET de la instrucción ALTER DATABASE.</span><span class="sxs-lookup"><span data-stu-id="433cf-107">You can set cross-database ownership chaining for individual databases using the SET clause of the ALTER DATABASE statement.</span></span> <span data-ttu-id="433cf-108">Si está creando una base de datos, puede establecer la opción de encadenamiento de propiedad entre bases de datos para la nueva base de datos mediante la instrucción CREATE DATABASE.</span><span class="sxs-lookup"><span data-stu-id="433cf-108">If you are creating a new database, you can set the cross-database ownership chaining option for the new database using the CREATE DATABASE statement.</span></span>  
  
     <span data-ttu-id="433cf-109">No se recomienda establecer la opción **Encadenamiento de propiedad entre bases de datos** en 1, a menos que todas las bases de datos hospedadas por la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] participen en el encadenamiento de propiedad entre bases de datos y sepa las implicaciones de seguridad de esta opción.</span><span class="sxs-lookup"><span data-stu-id="433cf-109">Setting **cross db ownership chaining** to 1 is not recommended unless all of the databases hosted by the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must participate in cross-database ownership chaining and you are aware of the security implications of this setting.</span></span>  
  
## <a name="controlling-cross-database-ownership-chaining"></a><span data-ttu-id="433cf-110">Controlar el encadenamiento de propiedad entre bases de datos</span><span class="sxs-lookup"><span data-stu-id="433cf-110">Controlling Cross-Database Ownership Chaining</span></span>  
 <span data-ttu-id="433cf-111">Antes de activar o desactivar el encadenamiento de propiedad entre bases de datos, tenga en cuenta lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="433cf-111">Before turning cross-database ownership chaining on or off, consider the following:</span></span>  
  
-   <span data-ttu-id="433cf-112">Debe ser miembro del rol fijo de servidor **sysadmin** para activar o desactivar el encadenamiento de propiedad entre bases de datos.</span><span class="sxs-lookup"><span data-stu-id="433cf-112">You must be a member of the **sysadmin** fixed server role to turn cross-database ownership chaining on or off.</span></span>  
  
-   <span data-ttu-id="433cf-113">Antes de desactivar el encadenamiento de propiedad entre bases de datos en un servidor de producción, compruebe totalmente todas las aplicaciones, incluidas las aplicaciones de otros fabricantes, para asegurarse de que los cambios no afectan a la funcionalidad de las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="433cf-113">Before turning off cross-database ownership chaining on a production server, fully test all applications, including third-party applications, to ensure that the changes do not affect application functionality.</span></span>  
  
-   <span data-ttu-id="433cf-114">Puede cambiar la opción **Encadenamiento de propiedad entre bases de datos** mientras el servidor se está ejecutando si especifica RECONFIGURE con **sp_configure**.</span><span class="sxs-lookup"><span data-stu-id="433cf-114">You can change the **cross db ownership chaining** option while the server is running if you specify RECONFIGURE with **sp_configure**.</span></span>  
  
-   <span data-ttu-id="433cf-115">Si tiene bases de datos que necesitan el encadenamiento de propiedad entre bases de datos, se recomienda desactivar la opción **Encadenamiento de propiedad entre bases de datos** para la instancia mediante **sp_configure**; después, active el encadenamiento de propiedad entre bases de datos para bases de datos específicas que requieran su uso mediante la instrucción ALTER DATABASE.</span><span class="sxs-lookup"><span data-stu-id="433cf-115">If you have databases that require cross-database ownership chaining, the recommended practice is to turn off the **cross db ownership chaining** option for the instance using **sp_configure**; then turn on cross-database ownership chaining for individual databases that require it using the ALTER DATABASE statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="433cf-116">Consulte también</span><span class="sxs-lookup"><span data-stu-id="433cf-116">See Also</span></span>  
 <span data-ttu-id="433cf-117">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="433cf-117">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="433cf-118">[CREATE DATABASE &#40;Transact-SQL de SQL Server&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="433cf-118">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="433cf-119">[Opciones de configuración de servidor &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="433cf-119">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="433cf-120">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="433cf-120">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="433cf-121">RECONFIGURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="433cf-121">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  