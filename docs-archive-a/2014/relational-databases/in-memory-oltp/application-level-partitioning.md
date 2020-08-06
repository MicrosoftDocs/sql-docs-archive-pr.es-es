---
title: Creación de particiones en el nivel de aplicación | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 162d1392-39d2-4436-a4d9-ee5c47864c5a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4d7a9f0794bda9fb336c739a0a7add89e9dae361
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663476"
---
# <a name="application-level-partitioning"></a><span data-ttu-id="daaf6-102">Creación de particiones en el nivel de aplicación</span><span class="sxs-lookup"><span data-stu-id="daaf6-102">Application-Level Partitioning</span></span>
  <span data-ttu-id="daaf6-103">Este ejemplo muestra la creación de particiones de nivel de aplicación donde se almacenan los datos en una tabla optimizada en memoria o en una tabla basada en disco dependiendo de si el pedido se encuentra antes o después de una fecha específica.</span><span class="sxs-lookup"><span data-stu-id="daaf6-103">This sample demonstrates application-level partitioning where data is stored in either a memory-optimized table or a disk-based table depending on whether the order falls before or after a specific date.</span></span> <span data-ttu-id="daaf6-104">Todos los pedidos posteriores o iguales a *hotDate* se encuentran en la tabla optimizada en memoria y todos los pedidos antes de *hotDate* se encuentran en la tabla basada en disco.</span><span class="sxs-lookup"><span data-stu-id="daaf6-104">All orders newer or equal to the *hotDate* are in the memory-optimized table and all orders before the *hotDate* are in the disk-based table.</span></span> <span data-ttu-id="daaf6-105">Suponga que hay un carga de trabajo de OLTP extrema con muchas transacciones simultáneas.</span><span class="sxs-lookup"><span data-stu-id="daaf6-105">Assume an extreme OLTP workload with a lot of concurrent transactions.</span></span> <span data-ttu-id="daaf6-106">Esta regla de negocios (pedidos recientes en una tabla optimizada para memoria) se debe aplicar incluso si varias transacciones simultáneas intentan cambiar *hotDate*.</span><span class="sxs-lookup"><span data-stu-id="daaf6-106">This business rule (recent orders in a memory-optimized table) must be enforced even if several concurrent transactions are attempting to change the *hotDate*.</span></span>  
  
 <span data-ttu-id="daaf6-107">Este ejemplo no usa [tablas con particiones](../partitions/partitioned-tables-and-indexes.md) para la tabla basada en disco pero realiza el seguimiento de un punto de división explícito entre dos tablas con una tercera tabla.</span><span class="sxs-lookup"><span data-stu-id="daaf6-107">This sample does not use [Partitioned Tables](../partitions/partitioned-tables-and-indexes.md) for the disk-based table but does track an explicit split point between the two tables using a third table.</span></span> <span data-ttu-id="daaf6-108">El punto de división se puede usar para asegurarse de que los datos recién insertados se insertan siempre en la tabla adecuada según la fecha.</span><span class="sxs-lookup"><span data-stu-id="daaf6-108">The split point can be used to ensure that newly inserted data is always inserted into the appropriate table based on the date.</span></span> <span data-ttu-id="daaf6-109">También se puede usar para determinar dónde buscar datos.</span><span class="sxs-lookup"><span data-stu-id="daaf6-109">It could also be used to determine where to look for data.</span></span> <span data-ttu-id="daaf6-110">Los últimos datos en llegar siguen estando en la tabla adecuada.</span><span class="sxs-lookup"><span data-stu-id="daaf6-110">Late arriving data still goes into the appropriate table.</span></span>  
  
 <span data-ttu-id="daaf6-111">Para obtener un ejemplo relacionado que use tablas con particiones, consulte [Application Pattern for Partitioning Memory-Optimized Tables](memory-optimized-tables.md).</span><span class="sxs-lookup"><span data-stu-id="daaf6-111">For a related sample that uses partitioned tables, see [Application Pattern for Partitioning Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
## <a name="code-listing"></a><span data-ttu-id="daaf6-112">Listado de código</span><span class="sxs-lookup"><span data-stu-id="daaf6-112">Code Listing</span></span>  
  
```sql  
USE MASTER  
GO  
  
IF DB_ID (N'partitionsample2') IS NOT NULL  
DROP DATABASE partitionsample2;  
GO  
  
CREATE DATABASE partitionsample2  
-- Enable the database for In-Memory OLTP.  
ALTER DATABASE partitionsample2 ADD FILEGROUP partitionsample2_mod CONTAINS MEMORY_OPTIMIZED_DATA  
ALTER DATABASE partitionsample2 ADD FILE( NAME = 'partitionsample2_mod' , FILENAME = 'c:\data\partitionsample2_mod') TO FILEGROUP partitionsample2_mod;  
GO  
  
USE partitionsample2  
GO  
  
-- Create a memory-optimized table for current (hot) orders.  
IF OBJECT_ID(N'SalesOrders_hot',N'U') IS NOT NULL  
   DROP TABLE [dbo].[SalesOrders_hot]  
  
CREATE TABLE dbo.SalesOrders_hot (  
   so_id INT NOT NULL PRIMARY KEY NONCLUSTERED,  
   cust_id INT NOT NULL,  
   so_date DATETIME2 NOT NULL INDEX ix_date NONCLUSTERED,  
   so_total MONEY NOT NULL,  
   INDEX ix_date_total NONCLUSTERED (so_date DESC, so_total DESC)  
) WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
-- Create a disk-based table for archiving older (cold) orders.  
IF OBJECT_ID(N'SalesOrders_cold',N'U') IS NOT NULL  
   DROP TABLE [dbo].[SalesOrders_cold]  
  
CREATE TABLE dbo.SalesOrders_cold (  
   so_id INT NOT NULL PRIMARY KEY NONCLUSTERED,  
   cust_id INT NOT NULL,  
   so_date DATETIME2 NOT NULL INDEX ix_date NONCLUSTERED,  
   so_total MONEY NOT NULL,  
   INDEX ix_date_total NONCLUSTERED (so_date DESC, so_total DESC)  
)   
GO  
  
-- The date that splits old and new orders (hotDate)  
-- is stored in this memory-optimized table.  
IF OBJECT_ID(N'SalesOrders_hotDate') IS NOT NULL  
   DROP TABLE [dbo].[SalesOrders_hotDate]  
  
CREATE TABLE dbo.SalesOrders_hotDate (  
   hotDate DATETIME2 not null PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT = 1)  
)  WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
-- STORED PROCEDURES  
  
-- Set the hotDate with SNAPSHOT ISOLATION so if other transactions  
-- try to update the hotDate, they will fail immediately due to a  
-- write/write conflict.  
IF OBJECT_ID(N'usp_SetHotDate') IS NOT NULL  
   DROP PROCEDURE [dbo].[usp_SetHotDate]  
GO  
  
CREATE PROCEDURE dbo.usp_SetHotDate (@newDate DATETIME2)  
   WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
   AS BEGIN ATOMIC WITH  
   (  
      TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
      LANGUAGE = N'english'  
   )  
   DELETE FROM [dbo].[SalesOrders_hotDate]  
   INSERT INTO [dbo].[SalesOrders_hotDate] (hotDate) VALUES (@newDate)  
   END  
GO  
  
-- Get the orders up to the hotDate  
-- (Must be serializable, to prevent deleting rows that are not returned.)  
IF OBJECT_ID(N'usp_getHotData') IS NOT NULL  
   DROP PROCEDURE [dbo].[usp_GetHotData]  
GO  
  
CREATE PROCEDURE dbo.usp_GetHotData (@hotDate DATETIME2)  
   WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
   AS BEGIN ATOMIC WITH  
   (  
      TRANSACTION ISOLATION LEVEL = SERIALIZABLE,  
      LANGUAGE = N'english'  
   )  
   SELECT so_id, cust_id, so_date, so_total FROM dbo.SalesOrders_hot WHERE so_date < @hotDate  
   DELETE FROM dbo.SalesOrders_hot WHERE so_date < @hotDate  
END  
GO  
  
-- Inserts an order into the proper table depending on the current hotDate.  
-- It is important that the SP for retrieving the hotDate is REPEATABLEREAD, in order to ensure that  
-- the hotDate is not changed before the decision is made where to insert the order.  
-- Note that insert operations [in both disk-based and memory-optimized tables] are always fully isolated, so the transaction  
-- isolation level has no impact on the insert operations; this whole transaction is effectively REPEATABLEREAD.  
IF OBJECT_ID(N'usp_InsertOrder') IS NOT NULL  
   DROP PROCEDURE [dbo].[usp_InsertOrder]  
GO  
  
CREATE PROCEDURE dbo.usp_InsertOrder (@id int, @custID nvarchar(10), @orderDate DATETIME2, @orderTotal MONEY)  
   AS BEGIN  
   SET TRANSACTION ISOLATION LEVEL READ COMMITTED  
   BEGIN TRAN  
      -- get hot date under repeatableread isolation; this is to guarantee it does not change before the insert is executed  
      DECLARE @hotDate DATETIME2  
      SET @hotDate = (SELECT hotDate FROM [dbo].[SalesOrders_hotDate] WITH (REPEATABLEREAD))  
  
      IF (@orderDate >= @hotDate) BEGIN  
         INSERT INTO [dbo].[SalesOrders_hot] (so_id, cust_id, so_date, so_total) VALUES (@id, @custID, @orderDate, @orderTotal)  
      END  
      ELSE BEGIN  
         INSERT INTO [dbo].[SalesOrders_cold] (so_id, cust_id, so_date, so_total) VALUES (@id, @custID, @orderDate, @orderTotal)  
      END  
   COMMIT TRAN  
END  
GO  
  
-- Changes the hotDate and moves the rows between the tables as appropriate.  
-- The hotDate is updated in this transaction; this means that if the hotDate is changed by another transaction  
-- the update will fail due to a write/write conflict and the transaction is rolled back  
-- therefore, the initial (SNAPSHOT) access of the hotDate is effectively REPEATABLEREAD.  
IF OBJECT_ID(N'usp_ChangeHotDate') IS NOT NULL  
   DROP PROCEDURE [dbo].[usp_ChangeHotDate]  
GO  
  
CREATE PROCEDURE [dbo].[usp_ChangeHotDate](@newHotDate DATETIME2)  
AS BEGIN  
   SET TRANSACTION ISOLATION LEVEL READ COMMITTED  
   BEGIN TRAN  
      DECLARE @oldHotDate DATETIME2  
      SET @oldHotDate = (SELECT hotDate FROM [dbo].[SalesOrders_hotDate] WITH (SNAPSHOT))  
  
       -- get hot date under repeatableread isolation; this is to guarantee it does not change before the insert is executed  
      IF (@oldHotDate < @newHotDate) BEGIN  
         INSERT INTO [dbo].[SalesOrders_cold] EXEC usp_GetHotData @newHotDate  
      END  
      ELSE BEGIN  
         INSERT INTO [dbo].[SalesOrders_hot] SELECT * FROM SalesOrders_cold WITH (SERIALIZABLE) WHERE so_date >= @newHotDate  
         DELETE FROM [dbo].[SalesOrders_cold] WITH (SERIALIZABLE) WHERE so_date >= @newHotDate  
      END  
      EXEC [dbo].[usp_SetHotDate] @newHotDate  
   COMMIT TRAN  
END  
GO  
  
-- DEMO  
DELETE FROM [dbo].[SalesOrders_cold]  
GO  
  
-- Initialize the order split date.  
EXEC [dbo].[usp_SetHotDate] '2014-1-1'   
GO  
  
-- List the hotDate.  
SELECT * FROM [dbo].[SalesOrders_hotDate]  
GO  
  
EXEC [dbo].[usp_InsertOrder] 1, 1001, '2013-11-14', 150  
EXEC [dbo].[usp_InsertOrder] 2, 1001, '2014-3-4', 100  
EXEC [dbo].[usp_InsertOrder] 3, 1001, '2013-1-23', 250  
EXEC [dbo].[usp_InsertOrder] 4, 1001, '2013-8-6', 200  
EXEC [dbo].[usp_InsertOrder] 5, 1001, '2012-11-1', 150  
EXEC [dbo].[usp_InsertOrder] 6, 1001, '2014-1-9', 150  
EXEC [dbo].[usp_InsertOrder] 7, 1001, '2014-2-14', 95  
EXEC [dbo].[usp_InsertOrder] 8, 1001, '2012-1-17', 125  
EXEC [dbo].[usp_InsertOrder] 9, 1001, '2014-3-8', 100  
EXEC [dbo].[usp_InsertOrder] 10, 1001, '2013-9-24', 100  
GO  
  
-- List contents of the tables.  
-- Query new orders.  
SELECT * FROM [dbo].[SalesOrders_hot] ORDER BY so_date DESC  
  
-- Query old orders.  
SELECT * FROM [dbo].[SalesOrders_cold] ORDER BY so_date DESC  
  
-- Move the hot date to March 1, 2014.   
EXEC [dbo].[usp_ChangeHotDate] '2014-03-01'  
  
-- List the new hotDate  
SELECT * FROM [dbo].[SalesOrders_hotDate]  
GO  
  
-- Verify that all orders before March 1, 2014 were moved  
-- to the older order table and list the data.  
SELECT * FROM [dbo].[SalesOrders_hot] ORDER BY so_date DESC  
  
SELECT * FROM [dbo].[SalesOrders_cold] ORDER BY so_date DESC  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="daaf6-113">Consulte también</span><span class="sxs-lookup"><span data-stu-id="daaf6-113">See Also</span></span>  
 <span data-ttu-id="daaf6-114">[OLTP en memoria &#40;optimización en memoria&#41;](in-memory-oltp-in-memory-optimization.md) </span><span class="sxs-lookup"><span data-stu-id="daaf6-114">[In-Memory OLTP &#40;In-Memory Optimization&#41;](in-memory-oltp-in-memory-optimization.md) </span></span>  
 [<span data-ttu-id="daaf6-115">Ejemplos de código de OLTP en memoria</span><span class="sxs-lookup"><span data-stu-id="daaf6-115">In-Memory OLTP Code Samples</span></span>](in-memory-oltp-code-samples.md)  
  
  
