---
title: Транзакции и параллельность
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: ba857031a54374ee295c2bfd724e7fb8651b7c1f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174698"
---
# <a name="transactions-and-concurrency"></a><span data-ttu-id="324c7-102">Транзакции и параллельность</span><span class="sxs-lookup"><span data-stu-id="324c7-102">Transactions and Concurrency</span></span>
<span data-ttu-id="324c7-103">Транзакция состоит из одной команды или группы команд, которые выполняются как пакет.</span><span class="sxs-lookup"><span data-stu-id="324c7-103">A transaction consists of a single command or a group of commands that execute as a package.</span></span> <span data-ttu-id="324c7-104">Транзакции позволяют объединить несколько операций в одну единицу работы.</span><span class="sxs-lookup"><span data-stu-id="324c7-104">Transactions allow you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="324c7-105">Если в какой-либо точке транзакции возникает ошибка, может быть выполнен откат всех обновлений к их состоянию до начала транзакции.</span><span class="sxs-lookup"><span data-stu-id="324c7-105">If a failure occurs at one point in the transaction, all of the updates can be rolled back to their pre-transaction state.</span></span>  
  
 <span data-ttu-id="324c7-106">Для обеспечения согласованности данных транзакция должна соответствовать свойствам ACID (атомарность, согласованность, изоляция и устойчивость).</span><span class="sxs-lookup"><span data-stu-id="324c7-106">A transaction must conform to the ACID properties—atomicity, consistency, isolation, and durability—in order to guarantee data consistency.</span></span> <span data-ttu-id="324c7-107">Большая часть систем реляционных баз данных, таких как Microsoft SQL Server, поддерживает транзакции, предоставляя блокировку, ведение журнала и средства управления транзакцией при выполнении клиентским приложением операций обновления, вставки или удаления.</span><span class="sxs-lookup"><span data-stu-id="324c7-107">Most relational database systems, such as Microsoft SQL Server, support transactions by providing locking, logging, and transaction management facilities whenever a client application performs an update, insert, or delete operation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="324c7-108">Транзакции, которые задействуют множество ресурсов, могут снизить параллелизм, если слишком долго удерживают блокировки.</span><span class="sxs-lookup"><span data-stu-id="324c7-108">Transactions that involve multiple resources can lower concurrency if locks are held too long.</span></span> <span data-ttu-id="324c7-109">Поэтому транзакции следует делать как можно короче.</span><span class="sxs-lookup"><span data-stu-id="324c7-109">Therefore, keep transactions as short as possible.</span></span>  
  
 <span data-ttu-id="324c7-110">В том случае, если в транзакции участвует несколько таблиц одной базы данных или одного сервера, явные транзакции в хранимых процедурах часто выполняются лучше.</span><span class="sxs-lookup"><span data-stu-id="324c7-110">If a transaction involves multiple tables in the same database or server, then explicit transactions in stored procedures often perform better.</span></span> <span data-ttu-id="324c7-111">Транзакции можно создавать в хранимых процедурах SQL Server с использованием инструкций Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION` и `ROLLBACK TRANSACTION`.</span><span class="sxs-lookup"><span data-stu-id="324c7-111">You can create transactions in SQL Server stored procedures by using the Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, and `ROLLBACK TRANSACTION` statements.</span></span> <span data-ttu-id="324c7-112">Дополнительные сведения см. в электронной документации по SQL Server.</span><span class="sxs-lookup"><span data-stu-id="324c7-112">For more information, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="324c7-113">Транзакции, требуются различные диспетчеры ресурсов, например для транзакций между SQL Server и Oracle, необходимо использовать распределенную транзакцию.</span><span class="sxs-lookup"><span data-stu-id="324c7-113">Transactions involving different resource managers, such as a transaction between SQL Server and Oracle, require a distributed transaction.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="324c7-114">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="324c7-114">In This Section</span></span>  
 [<span data-ttu-id="324c7-115">Локальные транзакции</span><span class="sxs-lookup"><span data-stu-id="324c7-115">Local Transactions</span></span>](../../../../docs/framework/data/adonet/local-transactions.md)  
 <span data-ttu-id="324c7-116">Демонстрирует выполнение транзакций на базе данных.</span><span class="sxs-lookup"><span data-stu-id="324c7-116">Demonstrates how to perform transactions against a database.</span></span>  
  
 [<span data-ttu-id="324c7-117">Распределенные транзакции</span><span class="sxs-lookup"><span data-stu-id="324c7-117">Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 <span data-ttu-id="324c7-118">Описывает выполнение распределенных транзакций в ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="324c7-118">Describes how to perform distributed transactions in ADO.NET.</span></span>  
  
 [<span data-ttu-id="324c7-119">Интеграция System.Transactions с SQL Server</span><span class="sxs-lookup"><span data-stu-id="324c7-119">System.Transactions Integration with SQL Server</span></span>](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 <span data-ttu-id="324c7-120">Описывает <xref:System.Transactions> интеграция с SQL Server для работы с распределенные транзакции.</span><span class="sxs-lookup"><span data-stu-id="324c7-120">Describes <xref:System.Transactions> integration with SQL Server for working with distributed transactions.</span></span>  
  
 [<span data-ttu-id="324c7-121">Оптимистическая блокировка</span><span class="sxs-lookup"><span data-stu-id="324c7-121">Optimistic Concurrency</span></span>](../../../../docs/framework/data/adonet/optimistic-concurrency.md)  
 <span data-ttu-id="324c7-122">Описывается оптимистичный и пессимистичный параллелизм и проверка на выявление нарушений параллелизма.</span><span class="sxs-lookup"><span data-stu-id="324c7-122">Describes optimistic and pessimistic concurrency, and how you can test for concurrency violations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="324c7-123">См. также</span><span class="sxs-lookup"><span data-stu-id="324c7-123">See also</span></span>

- [<span data-ttu-id="324c7-124">Основные сведения о транзакциях</span><span class="sxs-lookup"><span data-stu-id="324c7-124">Transaction Fundamentals</span></span>](../../../../docs/framework/data/transactions/transaction-fundamentals.md)
- [<span data-ttu-id="324c7-125">Подключение к источнику данных</span><span class="sxs-lookup"><span data-stu-id="324c7-125">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [<span data-ttu-id="324c7-126">Команды и параметры</span><span class="sxs-lookup"><span data-stu-id="324c7-126">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="324c7-127">Объекты DataAdapter и DataReader</span><span class="sxs-lookup"><span data-stu-id="324c7-127">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="324c7-128">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="324c7-128">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [<span data-ttu-id="324c7-129">Центр разработчиков наборов данных и управляемых поставщиков ADO.NET</span><span class="sxs-lookup"><span data-stu-id="324c7-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
