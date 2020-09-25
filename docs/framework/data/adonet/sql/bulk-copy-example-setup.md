---
title: Установка примера массового копирования
ms.date: 03/30/2017
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.openlocfilehash: 562d36e0aee72fcc0619ec4ed7362622ba652337
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197486"
---
# <a name="bulk-copy-example-setup"></a><span data-ttu-id="04c28-102">Установка примера массового копирования</span><span class="sxs-lookup"><span data-stu-id="04c28-102">Bulk Copy Example Setup</span></span>

<span data-ttu-id="04c28-103">Класс <xref:System.Data.SqlClient.SqlBulkCopy> можно использовать для записи данных только в таблицы SQL Server.</span><span class="sxs-lookup"><span data-stu-id="04c28-103">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="04c28-104">В примерах кода в этом разделе используется образец базы данных SQL Server **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="04c28-104">The code samples shown in this topic use the SQL Server sample database, **AdventureWorks**.</span></span> <span data-ttu-id="04c28-105">Чтобы не допустить изменения существующих таблиц, примеры кода записывают данные в таблицы, которые сначала необходимо создать.</span><span class="sxs-lookup"><span data-stu-id="04c28-105">To avoid altering the existing tables code samples write data to tables that you must create first.</span></span>  
  
 <span data-ttu-id="04c28-106">Таблицы **BulkCopyDemoMatchingColumns** и **BulkCopyDemoDifferentColumns** основаны на таблице **AdventureWorks** **Production.Products**.</span><span class="sxs-lookup"><span data-stu-id="04c28-106">The **BulkCopyDemoMatchingColumns** and **BulkCopyDemoDifferentColumns** tables are both based on the **AdventureWorks** **Production.Products** table.</span></span> <span data-ttu-id="04c28-107">В примерах кода, использующих эти таблицы, данные добавляются из таблицы **Production. Products** в одну из этих образцов таблиц.</span><span class="sxs-lookup"><span data-stu-id="04c28-107">In code samples that use these tables, data is added from the **Production.Products** table to one of these sample tables.</span></span> <span data-ttu-id="04c28-108">Таблица **булккопидемодифферентколумнс** используется, когда в образце показано, как сопоставлять столбцы из исходных данных с целевой таблицей. **Булккопидемоматчингколумнс** используется для большинства других примеров.</span><span class="sxs-lookup"><span data-stu-id="04c28-108">The **BulkCopyDemoDifferentColumns** table is used when the sample illustrates how to map columns from the source data to the destination table; **BulkCopyDemoMatchingColumns** is used for most other samples.</span></span>  
  
 <span data-ttu-id="04c28-109">Некоторые примеры кода демонстрируют использование одного класса <xref:System.Data.SqlClient.SqlBulkCopy> для записи в несколько таблиц.</span><span class="sxs-lookup"><span data-stu-id="04c28-109">A few of the code samples demonstrate how to use one <xref:System.Data.SqlClient.SqlBulkCopy> class to write to multiple tables.</span></span> <span data-ttu-id="04c28-110">В этих примерах таблицы **BulkCopyDemoOrderHeader** и **BulkCopyDemoOrderDetail** используются в качестве целевых таблиц.</span><span class="sxs-lookup"><span data-stu-id="04c28-110">For these samples, the **BulkCopyDemoOrderHeader** and **BulkCopyDemoOrderDetail** tables are used as the destination tables.</span></span> <span data-ttu-id="04c28-111">Эти таблицы основаны на таблицах **Sales. SalesOrderHeader** и **Sales. SalesOrderDetail** в **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="04c28-111">These tables are based on the **Sales.SalesOrderHeader** and **Sales.SalesOrderDetail** tables in **AdventureWorks**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04c28-112">Образцы кода **SqlBulkCopy** предоставляются только для демонстрации синтаксиса применения **SqlBulkCopy**.</span><span class="sxs-lookup"><span data-stu-id="04c28-112">The **SqlBulkCopy** code samples are provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="04c28-113">Если исходная и целевая таблицы расположены в одном экземпляре SQL Server, будет проще и быстрее использовать инструкцию Transact-SQL `INSERT … SELECT` для копирования данных.</span><span class="sxs-lookup"><span data-stu-id="04c28-113">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
## <a name="table-setup"></a><span data-ttu-id="04c28-114">Подготовка таблиц</span><span class="sxs-lookup"><span data-stu-id="04c28-114">Table Setup</span></span>  

 <span data-ttu-id="04c28-115">Чтобы создать таблицы, необходимые для правильной работы примеров кода, выполните следующие инструкции Transact-SQL в базе данных SQL Server.</span><span class="sxs-lookup"><span data-stu-id="04c28-115">To create the tables necessary for the code samples to run correctly, you must run the following Transact-SQL statements in a SQL Server database.</span></span>  
  
```sql
USE AdventureWorks  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoMatchingColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoMatchingColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoMatchingColumns]([ProductID] [int] IDENTITY(1,1) NOT NULL,  
    [Name] [nvarchar](50) NOT NULL,  
    [ProductNumber] [nvarchar](25) NOT NULL,  
 CONSTRAINT [PK_ProductID] PRIMARY KEY CLUSTERED  
(  
    [ProductID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoDifferentColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoDifferentColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoDifferentColumns]([ProdID] [int] IDENTITY(1,1) NOT NULL,  
    [ProdNum] [nvarchar](25) NOT NULL,  
    [ProdName] [nvarchar](50) NOT NULL,  
 CONSTRAINT [PK_ProdID] PRIMARY KEY CLUSTERED  
(  
    [ProdID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderHeader]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderHeader]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderHeader]([SalesOrderID] [int] IDENTITY(1,1) NOT NULL,  
    [OrderDate] [datetime] NOT NULL,  
    [AccountNumber] [nvarchar](15) NULL,  
 CONSTRAINT [PK_SalesOrderID] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderDetail]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderDetail]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderDetail]([SalesOrderID] [int] NOT NULL,  
    [SalesOrderDetailID] [int] NOT NULL,  
    [OrderQty] [smallint] NOT NULL,  
    [ProductID] [int] NOT NULL,  
    [UnitPrice] [money] NOT NULL,  
 CONSTRAINT [PK_LineNumber] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC,  
    [SalesOrderDetailID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
```  
  
## <a name="see-also"></a><span data-ttu-id="04c28-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="04c28-116">See also</span></span>

- [<span data-ttu-id="04c28-117">Операции массового копирования в SQL Server</span><span class="sxs-lookup"><span data-stu-id="04c28-117">Bulk Copy Operations in SQL Server</span></span>](bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="04c28-118">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="04c28-118">ADO.NET Overview</span></span>](../ado-net-overview.md)
