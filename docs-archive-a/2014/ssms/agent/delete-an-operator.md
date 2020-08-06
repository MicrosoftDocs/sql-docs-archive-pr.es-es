---
title: Eliminar un operador | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- canceling operators
- removing operators
- deleting operators
- dropping operators
- jobs [SQL Server Agent], operators
- operators (users) [Database Engine], deleting with Management Studio
ms.assetid: 2b7b8627-082d-4189-8584-abd3a9b604cf
author: stevestein
ms.author: sstein
ms.openlocfilehash: 75bea1c5c5fabff7ce55fe07a5181baa8f99e0fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663279"
---
# <a name="delete-an-operator"></a><span data-ttu-id="3e42b-102">Delete an Operator</span><span class="sxs-lookup"><span data-stu-id="3e42b-102">Delete an Operator</span></span>
  <span data-ttu-id="3e42b-103">En este tema se describe cómo quitar un operador para que deje [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de recibir notificaciones de alerta del agente en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3e42b-103">This topic describes how to remove an operator so they no longer receive [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert notifications in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="3e42b-104">**En este tema**</span><span class="sxs-lookup"><span data-stu-id="3e42b-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3e42b-105">**Antes de empezar:**</span><span class="sxs-lookup"><span data-stu-id="3e42b-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3e42b-106">Limitaciones y restricciones</span><span class="sxs-lookup"><span data-stu-id="3e42b-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="3e42b-107">Seguridad</span><span class="sxs-lookup"><span data-stu-id="3e42b-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3e42b-108">**Para eliminar un operador, utilizando:**</span><span class="sxs-lookup"><span data-stu-id="3e42b-108">**To delete an operator, using:**</span></span>  
  
     [<span data-ttu-id="3e42b-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3e42b-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="3e42b-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3e42b-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3e42b-111">Antes de comenzar</span><span class="sxs-lookup"><span data-stu-id="3e42b-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="3e42b-112">Limitaciones y restricciones</span><span class="sxs-lookup"><span data-stu-id="3e42b-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="3e42b-113">Cuando se quita un operador, se quitan también todas las notificaciones asociadas con él.</span><span class="sxs-lookup"><span data-stu-id="3e42b-113">When an operator is removed, all the notifications associated with the operator are also removed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3e42b-114">Seguridad</span><span class="sxs-lookup"><span data-stu-id="3e42b-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3e42b-115">Permisos</span><span class="sxs-lookup"><span data-stu-id="3e42b-115">Permissions</span></span>  
 <span data-ttu-id="3e42b-116">Los miembros del rol fijo de servidor **sysadmin** pueden eliminar operadores.</span><span class="sxs-lookup"><span data-stu-id="3e42b-116">Members of the **sysadmin** fixed server role can delete operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3e42b-117">Uso de SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3e42b-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-an-operator"></a><span data-ttu-id="3e42b-118">Para eliminar un operador</span><span class="sxs-lookup"><span data-stu-id="3e42b-118">To delete an operator</span></span>  
  
1.  <span data-ttu-id="3e42b-119">En el **Explorador de objetos**, haga clic en el signo más para expandir el servidor que contiene el operador que desea eliminar.</span><span class="sxs-lookup"><span data-stu-id="3e42b-119">In **Object Explorer**, click the plus sign to expand the server that contains the operator you want to delete.</span></span>  
  
2.  <span data-ttu-id="3e42b-120">Haga clic en el signo más para expandir **Agente SQL Server**.</span><span class="sxs-lookup"><span data-stu-id="3e42b-120">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="3e42b-121">Haga clic en el signo más para expandir la carpeta **Operadores** .</span><span class="sxs-lookup"><span data-stu-id="3e42b-121">Click the plus sign to expand the **Operators** folder.</span></span>  
  
4.  <span data-ttu-id="3e42b-122">Haga clic con el botón derecho en el operador que desea eliminar y seleccione **Eliminar**.</span><span class="sxs-lookup"><span data-stu-id="3e42b-122">Right-click the operator that you want to delete and select **Delete**.</span></span>  
  
5.  <span data-ttu-id="3e42b-123">En el cuadro de diálogo **Eliminar objeto** , asegúrese de que está seleccionado el operador correcto y haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="3e42b-123">In the **Delete Object** dialog box, make sure that the correct operator is selected, and then click **OK**.</span></span> <span data-ttu-id="3e42b-124">Para que otro operador reciba las alertas y trabajos enviados al operador eliminado, active **Volver a asignar a** y seleccione un operador de la lista.</span><span class="sxs-lookup"><span data-stu-id="3e42b-124">If you want another operator to receive the alerts and jobs sent to the deleted operator, check **Reassign to** and select an operator in the list.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3e42b-125">Usar Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3e42b-125">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-an-operator"></a><span data-ttu-id="3e42b-126">Para eliminar un operador</span><span class="sxs-lookup"><span data-stu-id="3e42b-126">To delete an operator</span></span>  
  
1.  <span data-ttu-id="3e42b-127">En el **Explorador de objetos**, conéctese a una instancia del [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3e42b-127">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3e42b-128">En la barra de Estándar, haga clic en **Nueva consulta**.</span><span class="sxs-lookup"><span data-stu-id="3e42b-128">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3e42b-129">Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**.</span><span class="sxs-lookup"><span data-stu-id="3e42b-129">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- deletes operator 'Test Operator' and reassigns all alerts and jobs sent to that operator to 'Fran??ois Ajenstat'  
    USE msdb ;  
    GO  
  
    EXEC sp_delete_operator @name = 'Test Operator',  
        @reassign_to_operator = 'Fran??ois Ajenstat';  
    GO  
    ```  
  
 <span data-ttu-id="3e42b-130">Para obtener más información, vea [sp_delete_operator &#40;&#41;de Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-delete-operator-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="3e42b-130">For more information, see [sp_delete_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-operator-transact-sql).</span></span>  
  
  