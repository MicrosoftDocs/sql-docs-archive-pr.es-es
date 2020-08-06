---
title: MSSQLSERVER_1803 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1803 (Database Engine error)
ms.assetid: d4315390-82f1-4c4c-8d1b-1a4989537cca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 11302f882846c49c6e9998608967e7042ac9860c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674148"
---
# <a name="mssqlserver_1803"></a><span data-ttu-id="372f7-102">MSSQLSERVER_1803</span><span class="sxs-lookup"><span data-stu-id="372f7-102">MSSQLSERVER_1803</span></span>
    
## <a name="details"></a><span data-ttu-id="372f7-103">Detalles</span><span class="sxs-lookup"><span data-stu-id="372f7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="372f7-104">Nombre de producto</span><span class="sxs-lookup"><span data-stu-id="372f7-104">Product Name</span></span>|<span data-ttu-id="372f7-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="372f7-105">SQL Server</span></span>|  
|<span data-ttu-id="372f7-106">Id. de evento</span><span class="sxs-lookup"><span data-stu-id="372f7-106">Event ID</span></span>|<span data-ttu-id="372f7-107">1803</span><span class="sxs-lookup"><span data-stu-id="372f7-107">1803</span></span>|  
|<span data-ttu-id="372f7-108">Origen de eventos</span><span class="sxs-lookup"><span data-stu-id="372f7-108">Event Source</span></span>|<span data-ttu-id="372f7-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="372f7-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="372f7-110">Componente</span><span class="sxs-lookup"><span data-stu-id="372f7-110">Component</span></span>|<span data-ttu-id="372f7-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="372f7-111">SQLEngine</span></span>|  
|<span data-ttu-id="372f7-112">Nombre simbólico</span><span class="sxs-lookup"><span data-stu-id="372f7-112">Symbolic Name</span></span>|<span data-ttu-id="372f7-113">NO_SPACE</span><span class="sxs-lookup"><span data-stu-id="372f7-113">NO_SPACE</span></span>|  
|<span data-ttu-id="372f7-114">Texto del mensaje</span><span class="sxs-lookup"><span data-stu-id="372f7-114">Message Text</span></span>|<span data-ttu-id="372f7-115">Error de CREATE DATABASE.</span><span class="sxs-lookup"><span data-stu-id="372f7-115">CREATE DATABASE failed.</span></span> <span data-ttu-id="372f7-116">El archivo principal debe ser de al menos %d MB para que pueda almacenar una copia de la base de datos de modelos.</span><span class="sxs-lookup"><span data-stu-id="372f7-116">Primary file must be at least %d MB to accommodate a copy of the model database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="372f7-117">Explicación</span><span class="sxs-lookup"><span data-stu-id="372f7-117">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="372f7-118">crea una base de datos realizando una copia de la base de datos de modelo.</span><span class="sxs-lookup"><span data-stu-id="372f7-118">creates a database by making a copy of the model database.</span></span> <span data-ttu-id="372f7-119">A continuación, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cambia el nombre de la copia y amplía la nueva base de datos al tamaño solicitado.</span><span class="sxs-lookup"><span data-stu-id="372f7-119">Then [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] renames the copy, and enlarges the new database to the requested size.</span></span> <span data-ttu-id="372f7-120">En este caso, el usuario ha intentado crear una base de datos menor que la base de datos de modelo.</span><span class="sxs-lookup"><span data-stu-id="372f7-120">In this case, the user tried to create a database smaller than the model database.</span></span> <span data-ttu-id="372f7-121">Se ha producido un error en la operación porque la copia de la base de datos de modelo no cabe en el archivo de datos principal, ya que el archivo es menor que la citada base de datos.</span><span class="sxs-lookup"><span data-stu-id="372f7-121">The operation failed because the copy of the model database could not fit on the primary data file, because the file was smaller than the model database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="372f7-122">Acción del usuario</span><span class="sxs-lookup"><span data-stu-id="372f7-122">User Action</span></span>  
 <span data-ttu-id="372f7-123">Cree la base de datos utilizando un tamaño de archivo de base de datos mayor.</span><span class="sxs-lookup"><span data-stu-id="372f7-123">Create the database by using a larger database file size.</span></span> <span data-ttu-id="372f7-124">A continuación, reduzca la base de datos si lo desea mediante el uso de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o la instrucción DBCC SHRINKDATABASE.</span><span class="sxs-lookup"><span data-stu-id="372f7-124">Then shrink the database if you want by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or the DBCC SHRINKDATABASE statement.</span></span>  
  
  