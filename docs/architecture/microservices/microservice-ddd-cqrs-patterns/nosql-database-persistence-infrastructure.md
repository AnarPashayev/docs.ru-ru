---
title: Использование баз данных NoSQL в качестве инфраструктуры сохраняемости
description: Архитектура микрослужб .NET для контейнерных приложений .NET | Использование баз данных NoSql в целом и в Azure Cosmos DB в частности для реализации сохраняемости.
ms.date: 10/08/2018
ms.openlocfilehash: b184586dede6331e0babfa976c6fd641933d018e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2019
ms.locfileid: "73089871"
---
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="06a3d-103">Использование баз данных NoSQL в качестве инфраструктуры сохраняемости</span><span class="sxs-lookup"><span data-stu-id="06a3d-103">Use NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="06a3d-104">При использовании баз данных NoSQL для уровня данных инфраструктуры обычно не используется ORM, например Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="06a3d-104">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="06a3d-105">Вместо этого используйте API, предоставляемый подсистемой NoSQL, например Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB или таблицы хранилищ Azure.</span><span class="sxs-lookup"><span data-stu-id="06a3d-105">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="06a3d-106">Тем не менее при использовании базы данных NoSQL, особенно для документоориентированных баз данных, таких как Azure Cosmos DB, CouchDB или RavenDB, архитектура модели с агрегатами DDD частично похожа на соответствующую архитектуру в EF Core в отношении определения корней агрегации, классов дочерних объектов и классов объектов значений.</span><span class="sxs-lookup"><span data-stu-id="06a3d-106">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="06a3d-107">Но в конечном счете выбор базы данных повлияет на вашу архитектуру.</span><span class="sxs-lookup"><span data-stu-id="06a3d-107">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="06a3d-108">При использовании документоориентированной базы данных агрегат реализуется в виде отдельного документа, сериализованного в JSON или в другом формате.</span><span class="sxs-lookup"><span data-stu-id="06a3d-108">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="06a3d-109">Однако использование базы данных является прозрачным с точки зрения модели предметной области.</span><span class="sxs-lookup"><span data-stu-id="06a3d-109">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="06a3d-110">При использовании баз данных NoSQL вы по-прежнему используете классы сущностей и классы корней агрегации, но с большей гибкостью, чем при использовании EF Core, так как сохраняемость не является реляционной.</span><span class="sxs-lookup"><span data-stu-id="06a3d-110">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="06a3d-111">Различие заключается в том, как реализована сохраняемость для этой модели.</span><span class="sxs-lookup"><span data-stu-id="06a3d-111">The difference is in how you persist that model.</span></span> <span data-ttu-id="06a3d-112">Если модель предметной области реализована на основе классов сущностей POCO, которые не зависят от сохраняемости инфраструктуры, вы можете перейти на другую сохраняемость инфраструктуры, даже с реляционных баз данных на NoSQL.</span><span class="sxs-lookup"><span data-stu-id="06a3d-112">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="06a3d-113">Однако это не должно быть вашей целью.</span><span class="sxs-lookup"><span data-stu-id="06a3d-113">However, that should not be your goal.</span></span> <span data-ttu-id="06a3d-114">В различных технологиях баз данных всегда есть ограничения и компромиссы, поэтому вы не сможете использовать одну и ту же модель для реляционных баз данных и баз данных NoSQL.</span><span class="sxs-lookup"><span data-stu-id="06a3d-114">There are always constraints and trade-offs in the different database technologies, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="06a3d-115">Изменение моделей сохраняемости будет непростой задачей, так как транзакции и операции сохраняемости будут сильно отличаться.</span><span class="sxs-lookup"><span data-stu-id="06a3d-115">Changing persistence models is not a trivial task, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="06a3d-116">Например, в документоориентированной базе данных корень агрегирования может иметь несколько свойств дочерних коллекций.</span><span class="sxs-lookup"><span data-stu-id="06a3d-116">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="06a3d-117">В реляционной базе данных запрос к нескольким свойствам дочерних коллекций нелегко оптимизировать, так как вы получите инструкцию UNION ALL SQL обратно из EF.</span><span class="sxs-lookup"><span data-stu-id="06a3d-117">In a relational database, querying multiple child collection properties is not easily optimized, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="06a3d-118">Использование одной и той же модели предметной области для реляционных баз данных и баз данных NoSQL — непростое, и не стоит стараться этого достичь.</span><span class="sxs-lookup"><span data-stu-id="06a3d-118">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try to do it.</span></span> <span data-ttu-id="06a3d-119">На практике нужно спроектировать свою модель с пониманием того, как данные будут использоваться в каждой конкретной базе данных.</span><span class="sxs-lookup"><span data-stu-id="06a3d-119">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="06a3d-120">Преимущество при использовании баз данных NoSQL заключается в том, что сущности более денормализованы, поэтому вам не нужно настраивать сопоставление таблиц.</span><span class="sxs-lookup"><span data-stu-id="06a3d-120">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="06a3d-121">Модель предметной области может быть более гибкой по сравнению с реляционной базой данных.</span><span class="sxs-lookup"><span data-stu-id="06a3d-121">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="06a3d-122">При проектировании модели предметной области на основе агрегатов переход на NoSQL и документоориентированные базы данных может быть еще проще по сравнению с использованием реляционных баз данных, так как создаваемые вами агрегаты похожи на сериализованные документы в документоориентированной базе данных.</span><span class="sxs-lookup"><span data-stu-id="06a3d-122">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="06a3d-123">Затем вы сможете включить в эти "контейнеры" все необходимые сведения для этого агрегата.</span><span class="sxs-lookup"><span data-stu-id="06a3d-123">Then you can include in those “bags” all the information you might need for that aggregate.</span></span>

<span data-ttu-id="06a3d-124">Например, следующий код JSON представляет собой пример реализации агрегата порядка при использовании документоориентированной базы данных.</span><span class="sxs-lookup"><span data-stu-id="06a3d-124">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="06a3d-125">Этот агрегат похож на агрегат порядка, реализованный в примере eShopOnContainers, но не основан на EF Core.</span><span class="sxs-lookup"><span data-stu-id="06a3d-125">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

```json
{
    "id": "2017001",
    "orderDate": "2/25/2017",
    "buyerId": "1234567",
    "address": [
        {
        "street": "100 One Microsoft Way",
        "city": "Redmond",
        "state": "WA",
        "zip": "98052",
        "country": "U.S."
        }
    ],
    "orderItems": [
        {"id": 20170011, "productId": "123456", "productName": ".NET T-Shirt",
        "unitPrice": 25, "units": 2, "discount": 0},
        {"id": 20170012, "productId": "123457", "productName": ".NET Mug",
        "unitPrice": 15, "units": 1, "discount": 0}
    ]
}
```

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a><span data-ttu-id="06a3d-126">Общие сведения об Azure Cosmos DB и о собственном API Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="06a3d-126">Introduction to Azure Cosmos DB and the native Cosmos DB API</span></span>

<span data-ttu-id="06a3d-127">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) — глобально распределенная служба баз данных корпорации Майкрософт для критически важных приложений.</span><span class="sxs-lookup"><span data-stu-id="06a3d-127">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) is Microsoft's globally distributed database service for mission-critical applications.</span></span> <span data-ttu-id="06a3d-128">Azure Cosmos DB предоставляет [глобальное распределение](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [эластичное масштабирование пропускной способности и хранилища](https://docs.microsoft.com/azure/cosmos-db/partition-data) по всему миру, задержку не более десяти миллисекунд на 99-м процентиле, [пять хорошо определенных уровней согласованности](https://docs.microsoft.com/azure/cosmos-db/consistency-levels), гарантированную высокую доступность — и все это с [ведущими в отрасли соглашениями об уровне обслуживания](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span><span class="sxs-lookup"><span data-stu-id="06a3d-128">Azure Cosmos DB provides [turn-key global distribution](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastic scaling of throughput and storage](https://docs.microsoft.com/azure/cosmos-db/partition-data) worldwide, single-digit millisecond latencies at the 99th percentile, [five well-defined consistency levels](https://docs.microsoft.com/azure/cosmos-db/consistency-levels), and guaranteed high availability, all backed by [industry-leading SLAs](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span></span> <span data-ttu-id="06a3d-129">Azure Cosmos DB [автоматически индексирует данные](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) без необходимости иметь дело со схемой и управлением индексами.</span><span class="sxs-lookup"><span data-stu-id="06a3d-129">Azure Cosmos DB [automatically indexes data](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) without requiring you to deal with schema and index management.</span></span> <span data-ttu-id="06a3d-130">Она является мультимодельной и поддерживает следующие модели данных: модель данных документа, модель данных "ключ-значение", модель данных графа и столбцовая модель данных.</span><span class="sxs-lookup"><span data-stu-id="06a3d-130">It is multi-model and supports document, key-value, graph, and columnar data models.</span></span>

![<span data-ttu-id="06a3d-131">Azure Cosmos DB — это глобально распределенная база данных с гарантированно низкой задержкой, доступ к которой можно получить с помощью четырех протоколов API.</span><span class="sxs-lookup"><span data-stu-id="06a3d-131">Azure Cosmos DB is a globally distributed guaranteed low-latency database that can be accessed with four API protocols.</span></span> ](./media/image19.1.png)

<span data-ttu-id="06a3d-132">**Рис. 7–19**.</span><span class="sxs-lookup"><span data-stu-id="06a3d-132">**Figure 7-19**.</span></span> <span data-ttu-id="06a3d-133">Глобальное распределение Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="06a3d-133">Azure Cosmos DB global distribution</span></span>

<span data-ttu-id="06a3d-134">При использовании модели C\# для реализации агрегирования, используемого API Azure Cosmos DB, агрегат может быть похож на классы POCO C\#, используемые в EF Core.</span><span class="sxs-lookup"><span data-stu-id="06a3d-134">When you use a C\# model to implement the aggregate to be used by the Azure Cosmos DB API, the aggregate can be similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="06a3d-135">Различие заключается в использовании классов на уровнях приложения и инфраструктуры, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="06a3d-135">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

```csharp
// C# EXAMPLE OF AN ORDER AGGREGATE BEING PERSISTED WITH AZURE COSMOS DB API
// *** Domain Model Code ***
// Aggregate: Create an Order object with its child entities and/or value objects.
// Then, use AggregateRoot’s methods to add the nested objects so invariants and
// logic is consistent across the nested properties (value objects and entities).

Order orderAggregate = new Order
{
    Id = "2017001",
    OrderDate = new DateTime(2005, 7, 1),
    BuyerId = "1234567",
    PurchaseOrderNumber = "PO18009186470"
}

Address address = new Address
{
    Street = "100 One Microsoft Way",
    City = "Redmond",
    State = "WA",
    Zip = "98052",
    Country = "U.S."
}

orderAggregate.UpdateAddress(address);

OrderItem orderItem1 = new OrderItem
{
    Id = 20170011,
    ProductId = "123456",
    ProductName = ".NET T-Shirt",
    UnitPrice = 25,
    Units = 2,
    Discount = 0;
};

//Using methods with domain logic within the entity. No anemic-domain model
orderAggregate.AddOrderItem(orderItem1);
// *** End of Domain Model Code ***

// *** Infrastructure Code using Cosmos DB Client API ***
Uri collectionUri = UriFactory.CreateDocumentCollectionUri(databaseName,
    collectionName);

await client.CreateDocumentAsync(collectionUri, orderAggregate);

// As your app evolves, let's say your object has a new schema. You can insert
// OrderV2 objects without any changes to the database tier.
Order2 newOrder = GetOrderV2Sample("IdForSalesOrder2");
await client.CreateDocumentAsync(collectionUri, newOrder);
```

<span data-ttu-id="06a3d-136">Вы увидите, что ваш способ работы с моделью предметной области может быть похож на ее использование на уровне модели предметной области в инфраструктуре EF.</span><span class="sxs-lookup"><span data-stu-id="06a3d-136">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="06a3d-137">Вы по-прежнему можете использовать те же методы корней агрегации для обеспечения согласованности, инвариантности и для выполнения проверок в агрегатах.</span><span class="sxs-lookup"><span data-stu-id="06a3d-137">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="06a3d-138">Однако при сохранении модели в базе данных NoSQL код и API значительно изменяются по сравнению с кодом EF Core или с любым другим кодом для реляционных баз данных.</span><span class="sxs-lookup"><span data-stu-id="06a3d-138">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

## <a name="implement-net-code-targeting-mongodb-and-azure-cosmos-db"></a><span data-ttu-id="06a3d-139">Реализация кода .NET для MongoDB и Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="06a3d-139">Implement .NET code targeting MongoDB and Azure Cosmos DB</span></span>

### <a name="use-azure-cosmos-db-from-net-containers"></a><span data-ttu-id="06a3d-140">Использование Azure Cosmos DB из контейнеров .NET</span><span class="sxs-lookup"><span data-stu-id="06a3d-140">Use Azure Cosmos DB from .NET containers</span></span>

<span data-ttu-id="06a3d-141">Базы данных Azure Cosmos DB доступны из любого кода .NET, запущенного в контейнерах, точно так же, как из любых других приложений .NET.</span><span class="sxs-lookup"><span data-stu-id="06a3d-141">You can access Azure Cosmos DB databases from .NET code running in containers, like from any other .NET application.</span></span> <span data-ttu-id="06a3d-142">Например, микрослужбы Locations.API и Marketing.API в eShopOnContainers реализованы таким образом, что они могут использовать базы данных Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="06a3d-142">For instance, the Locations.API and Marketing.API microservices in eShopOnContainers are implemented so they can consume Azure Cosmos DB databases.</span></span>

<span data-ttu-id="06a3d-143">Однако с точки зрения разработки для Docker, в Azure Cosmos DB есть ограничение.</span><span class="sxs-lookup"><span data-stu-id="06a3d-143">However, there’s a limitation in Azure Cosmos DB from a Docker development environment point of view.</span></span> <span data-ttu-id="06a3d-144">Даже при наличии локального [эмулятора Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/local-emulator), который можно запустить на локальном компьютере разработчика (например на ПК), на конец 2017 г. этот эмулятор поддерживает только Windows, но не Linux.</span><span class="sxs-lookup"><span data-stu-id="06a3d-144">Even when there’s a on-premises [Azure Cosmos DB Emulator](https://docs.microsoft.com/azure/cosmos-db/local-emulator) able to run in a local development machine (like a PC), as of late 2017, it just supports Windows, not Linux.</span></span>

<span data-ttu-id="06a3d-145">Этот эмулятор также можно запустить в Docker, но только в контейнерах Windows, а не в контейнерах Linux.</span><span class="sxs-lookup"><span data-stu-id="06a3d-145">There is also the possibility to run this emulator on Docker, but just on Windows Containers, not with Linux Containers.</span></span> <span data-ttu-id="06a3d-146">Это начальное ограничение среды разработки в том случае, если ваше приложение развертывается в виде контейнеров Linux, так как сейчас вы не можете одновременно развернуть контейнеры Linux и Windows в Docker для Windows.</span><span class="sxs-lookup"><span data-stu-id="06a3d-146">That is an initial handicap for the development environment if your application is deployed as Linux containers, since, currently, you cannot deploy Linux and Windows Containers on Docker for Windows at the same time.</span></span> <span data-ttu-id="06a3d-147">Все контейнеры должны быть развернуты либо в Linux, либо в Windows.</span><span class="sxs-lookup"><span data-stu-id="06a3d-147">Either all containers being deployed have to be for Linux or for Windows.</span></span>

<span data-ttu-id="06a3d-148">Идеальный и более простой вариант решения для разработки и тестирования — возможность развертывания систем баз данных в качестве контейнеров вместе с вашими пользовательскими контейнерами, таким образом среды разработки и тестирования всегда будут согласованы.</span><span class="sxs-lookup"><span data-stu-id="06a3d-148">The ideal and more straightforward deployment for a dev/test solution is to be able to deploy your database systems as containers along with your custom containers so your dev/test environments are always consistent.</span></span>

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a><span data-ttu-id="06a3d-149">Использование API MongoDB для локальных контейнеров разработки и тестирования Linux/Windows и Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="06a3d-149">Use MongoDB API for local dev/test Linux/Windows containers plus Azure Cosmos DB</span></span>

<span data-ttu-id="06a3d-150">Базы данных Cosmos DB поддерживают API MongoDB для .NET, а также собственный коммутации MongoDB.</span><span class="sxs-lookup"><span data-stu-id="06a3d-150">Cosmos DB databases support MongoDB API for .NET as well as the native MongoDB wire protocol.</span></span> <span data-ttu-id="06a3d-151">Это означает, что ваше приложение MongoDB сейчас сможет взаимодействовать с Cosmos DB и использовать базы данных Cosmos DB вместо баз данных MongoDB с использованием существующих драйверов, как показано на рис. 7-20.</span><span class="sxs-lookup"><span data-stu-id="06a3d-151">This means that by using existing drivers, your application written for MongoDB can now communicate with Cosmos DB and use Cosmos DB databases instead of MongoDB databases, as shown in Figure 7-20.</span></span>

![Cosmos DB поддерживает API MongoDB для .NET и протокол связи MongoDB, вы можете легко переключиться с MongoDB на Cosmos DB.](./media/image19.2.png)

<span data-ttu-id="06a3d-153">**Рис. 7-20**.</span><span class="sxs-lookup"><span data-stu-id="06a3d-153">**Figure 7-20**.</span></span> <span data-ttu-id="06a3d-154">Использование API и протокола MongoDB для доступа к Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="06a3d-154">Using MongoDB API and protocol to access Azure Cosmos DB</span></span>

<span data-ttu-id="06a3d-155">Это очень удобный подход для подтверждения концепций в средах Docker с контейнерами Linux, так как [образ Docker MongoDB](https://hub.docker.com/r/_/mongo/) — это образ с поддержкой нескольких архитектур. Он поддерживает как контейнеры Linux, так и контейнеры Windows в Docker.</span><span class="sxs-lookup"><span data-stu-id="06a3d-155">This is a very convenient approach for proof of concepts in Docker environments with Linux containers because the [MongoDB Docker image](https://hub.docker.com/r/_/mongo/) is a multi-arch image that supports Docker Linux containers and Docker Windows containers.</span></span>

<span data-ttu-id="06a3d-156">Как показано на следующем рисунке, eShopOnContainers поддерживает контейнеры Windows и Linux MongoDB для локальной среды разработки с API MongoDB. Но вы можете перейти на масштабируемое облачное решение PaaS, такое как Azure Cosmos DB, просто [изменив строку подключения MongoDB, так чтобы она указывала на Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="06a3d-156">As shown in the following image, by using the MongoDB API, eShopOnContainers supports MongoDB Linux and Windows containers for the local development environment but then, you can move to a scalable, PaaS cloud solution as Azure Cosmos DB by simply [changing the MongoDB connection string to point to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

![Микрослужба расположения в eShopOnContainers реализуется с помощью MongoDB, но можно переключится на Cosmos DB, просто изменив строку подключения.](./media/image20-bis.png)

<span data-ttu-id="06a3d-158">**Рис. 7-21**.</span><span class="sxs-lookup"><span data-stu-id="06a3d-158">**Figure 7-21**.</span></span> <span data-ttu-id="06a3d-159">Решение eShopOnContainers, использующее контейнеры MongoDB для среды разработки и Azure Cosmos DB для рабочей среды</span><span class="sxs-lookup"><span data-stu-id="06a3d-159">eShopOnContainers using MongoDB containers for dev-env or Azure Cosmos DB for production</span></span>

<span data-ttu-id="06a3d-160">Рабочая база данных Azure Cosmos DB была бы запущена в облаке Azure как PaaS и масштабируемая служба.</span><span class="sxs-lookup"><span data-stu-id="06a3d-160">The production Azure Cosmos DB would be running in Azure’s cloud as a PaaS and scalable service.</span></span>

<span data-ttu-id="06a3d-161">Пользовательские контейнеры .NET Core можно запустить на локальном узле Docker (на котором используется Docker для Windows на компьютере Windows 10) или развернуть в рабочей среде, например, в Kubernetes в Azure AKS или в Azure Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="06a3d-161">Your custom .NET Core containers can run on a local development Docker host (that is using Docker for Windows in a Windows 10 machine) or be deployed into a production environment, like Kubernetes in Azure AKS or Azure Service Fabric.</span></span> <span data-ttu-id="06a3d-162">Во второй среде вы разворачиваете только пользовательские контейнеры .NET Core, но не контейнер MongoDB, так как вы будете использовать Azure Cosmos DB в облаке для обработки данных в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="06a3d-162">In this second environment, you would deploy only the .NET Core custom containers but not the MongoDB container since you’d be using Azure Cosmos DB in the cloud for handling the data in production.</span></span>

<span data-ttu-id="06a3d-163">Очевидное преимущество API MongoDB — в том, что ваше решение можно запустить как в MongoDB, так и в Azure Cosmos DB, поэтому перенос в другую среду не должен представлять сложностей.</span><span class="sxs-lookup"><span data-stu-id="06a3d-163">A clear benefit of using the MongoDB API is that your solution could run in both database engines, MongoDB or Azure Cosmos DB, so migrations to different environments should be easy.</span></span> <span data-ttu-id="06a3d-164">Однако иногда стоит использовать собственный API (то есть собственный API Cosmos DB), чтобы получить полный набор возможностей конкретной СУБД.</span><span class="sxs-lookup"><span data-stu-id="06a3d-164">However, sometimes it is worthwhile to use a native API (that is the native Cosmos DB API) in order to take full advantage of the capabilities of a specific database engine.</span></span>

<span data-ttu-id="06a3d-165">Дальнейшее сравнение простого использования MongoDB и Cosmos DB в облаке см. в разделе [Преимущества использования Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction) на этой странице.</span><span class="sxs-lookup"><span data-stu-id="06a3d-165">For further comparison between simply using MongoDB versus Cosmos DB in the cloud, see the [Benefits of using Azure Cosmos DB in this page](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).</span></span>

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a><span data-ttu-id="06a3d-166">Анализ подходов для приложений в рабочей среде: сравнение API MongoDB и API Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="06a3d-166">Analyze your approach for production applications: MongoDB API vs. Cosmos DB API</span></span>

<span data-ttu-id="06a3d-167">В eShopOnContainers мы используем API MongoDB, так как нашим главным приоритетом была согласованная среда разработки и тестирования с использованием базы данных NoSQL, которая могла бы также работать с Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="06a3d-167">In eShopOnContainers, we’re using MongoDB API because our priority was fundamentally to have a consistent dev/test environment using a NoSQL database that could also work with Azure Cosmos DB.</span></span>

<span data-ttu-id="06a3d-168">Тем не менее если вы планируете использовать API MongoDB для доступа к Azure Cosmos DB в Azure из приложений в рабочей среде, следует проанализировать различия в возможностях и производительности при использовании API MongoDB для доступа к базам данных Azure Cosmos DB по сравнению с использованием собственного API Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="06a3d-168">However, if you planning to use MongoDB API to access Azure Cosmos DB in Azure for production applications, you should analyze the differences in capabilities and performance when using MongoDB API to access Azure Cosmos DB databases compared to using the native Azure Cosmos DB API.</span></span> <span data-ttu-id="06a3d-169">Если возможности и производительность сопоставимы, вы можете использовать API MongoDB и получите поддержку двух СУБД NoSQL одновременно.</span><span class="sxs-lookup"><span data-stu-id="06a3d-169">If it is similar you can use MongoDB API and you get the benefit of supporting two NoSQL database engines at the same time.</span></span>

<span data-ttu-id="06a3d-170">Также можно использовать кластеры MongoDB в рабочей базе данных в облаке Azure с помощью [службы MongoDB Azure](https://www.mongodb.com/scale/mongodb-azure-service).</span><span class="sxs-lookup"><span data-stu-id="06a3d-170">You could also use MongoDB clusters as the production database in Azure’s cloud, too, with [MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service).</span></span> <span data-ttu-id="06a3d-171">Однако эта служба — не служба PaaS, предоставляемая Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="06a3d-171">But that is not a PaaS service provided by Microsoft.</span></span> <span data-ttu-id="06a3d-172">В этом случае в Azure просто размещается решение MongoDB.</span><span class="sxs-lookup"><span data-stu-id="06a3d-172">In this case, Azure is just hosting that solution coming from MongoDB.</span></span>

<span data-ttu-id="06a3d-173">По сути, это просто предупреждение о том, что не следует всегда выбирать API MongoDB в сравнении с Azure Cosmos DB, как мы сделали в eShopOnContainers, так как API MongoDB хорошо подходит для контейнеров Linux.</span><span class="sxs-lookup"><span data-stu-id="06a3d-173">Basically, this is just a disclaimer stating that you shouldn’t always use MongoDB API against Azure Cosmos DB, as we did in eShopOnContainers because it was a convenient choice for Linux containers.</span></span> <span data-ttu-id="06a3d-174">При принятии решения следует учитывать конкретные потребности и провести конкретные проверки для приложения в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="06a3d-174">The decision should be based on the specific needs and tests you need to do for your production application.</span></span>

### <a name="the-code-use-mongodb-api-in-net-core-applications"></a><span data-ttu-id="06a3d-175">Код. Использование API MongoDB в приложениях .NET Core</span><span class="sxs-lookup"><span data-stu-id="06a3d-175">The code: Use MongoDB API in .NET Core applications</span></span>

<span data-ttu-id="06a3d-176">API MongoDB для .NET основан на пакетах NuGet, которые необходимо добавить в свои проекты, например проект Locations.API, показанный на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="06a3d-176">MongoDB API for .NET is based on NuGet packages that you need to add to your projects, like in the Locations.API project shown in the following figure.</span></span>

![Представление обозревателя решений, показывающее зависимости пакетов MongoDB NuGet.](./media/image21-bis.png)

<span data-ttu-id="06a3d-178">**Рис. 7-22**.</span><span class="sxs-lookup"><span data-stu-id="06a3d-178">**Figure 7-22**.</span></span> <span data-ttu-id="06a3d-179">Ссылки на пакеты NuGet для API MongoDB в проекте .NET Core</span><span class="sxs-lookup"><span data-stu-id="06a3d-179">MongoDB API NuGet packages references in a .NET Core project</span></span>

<span data-ttu-id="06a3d-180">Давайте рассмотрим код, приведенный в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="06a3d-180">Let's investigate the code in the following sections.</span></span>

#### <a name="a-model-used-by-mongodb-api"></a><span data-ttu-id="06a3d-181">Модель, используемая API MongoDB</span><span class="sxs-lookup"><span data-stu-id="06a3d-181">A Model used by MongoDB API</span></span>

<span data-ttu-id="06a3d-182">Во-первых, необходимо определить модель, которая будет содержать данные, поступающие из базы данных в пространство памяти приложения.</span><span class="sxs-lookup"><span data-stu-id="06a3d-182">First, you need to define a model that will hold the data coming from the database in your application’s memory space.</span></span> <span data-ttu-id="06a3d-183">Ниже приведен пример модели, используемой для расположений в eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="06a3d-183">Here’s an example of the model used for Locations at eShopOnContainers.</span></span>

```csharp
using MongoDB.Bson;
using MongoDB.Bson.Serialization.Attributes;
using MongoDB.Driver.GeoJsonObjectModel;
using System.Collections.Generic;

public class Locations
{
    [BsonId]
    [BsonRepresentation(BsonType.ObjectId)]
    public string Id { get; set; }
    public int LocationId { get; set; }
    public string Code { get; set; }
    [BsonRepresentation(BsonType.ObjectId)]
    public string Parent_Id { get; set; }
    public string Description { get; set; }
    public double Latitude { get; set; }
    public double Longitude { get; set; }
    public GeoJsonPoint<GeoJson2DGeographicCoordinates> Location
                                                             { get; private set; }
    public GeoJsonPolygon<GeoJson2DGeographicCoordinates> Polygon
                                                             { get; private set; }
    public void SetLocation(double lon, double lat) => SetPosition(lon, lat);
    public void SetArea(List<GeoJson2DGeographicCoordinates> coordinatesList)
                                                    => SetPolygon(coordinatesList);

    private void SetPosition(double lon, double lat)
    {
        Latitude = lat;
        Longitude = lon;
        Location = new GeoJsonPoint<GeoJson2DGeographicCoordinates>(
            new GeoJson2DGeographicCoordinates(lon, lat));
    }

    private void SetPolygon(List<GeoJson2DGeographicCoordinates> coordinatesList)
    {
        Polygon = new GeoJsonPolygon<GeoJson2DGeographicCoordinates>(
                  new GeoJsonPolygonCoordinates<GeoJson2DGeographicCoordinates>(
                  new GeoJsonLinearRingCoordinates<GeoJson2DGeographicCoordinates>(
                                                                 coordinatesList)));
    }
}
```

<span data-ttu-id="06a3d-184">Как вы видите, в ней есть несколько атрибутов и типов из пакетов NuGet MongoDB.</span><span class="sxs-lookup"><span data-stu-id="06a3d-184">You can see there are a few attributes and types coming from the MongoDB NuGet packages.</span></span>

<span data-ttu-id="06a3d-185">Базы данных NoSQL обычно очень хорошо подходят для работы с нереляционными иерархическими данными.</span><span class="sxs-lookup"><span data-stu-id="06a3d-185">NoSQL databases are usually very well suited for working with non-relational hierarchical data.</span></span> <span data-ttu-id="06a3d-186">В этом примере мы используем типы MongoDB, специально предназначенные для географических расположений, например `GeoJson2DGeographicCoordinates`.</span><span class="sxs-lookup"><span data-stu-id="06a3d-186">In this example, we are using MongoDB types especially made for geo-locations, like `GeoJson2DGeographicCoordinates`.</span></span>

#### <a name="retrieve-the-database-and-the-collection"></a><span data-ttu-id="06a3d-187">Получение базы данных и коллекции</span><span class="sxs-lookup"><span data-stu-id="06a3d-187">Retrieve the database and the collection</span></span>

<span data-ttu-id="06a3d-188">В eShopOnContainers мы создали пользовательский контекст базы данных, в котором реализовали код для получения базы данных и коллекций MongoCollections, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="06a3d-188">In eShopOnContainers, we have created a custom database context where we implement the code to retrieve the database and the MongoCollections, as in the following code.</span></span>

```csharp
public class LocationsContext
{
    private readonly IMongoDatabase _database = null;

    public LocationsContext(IOptions<LocationSettings> settings)
    {
        var client = new MongoClient(settings.Value.ConnectionString);
        if (client != null)
            _database = client.GetDatabase(settings.Value.Database);
    }

    public IMongoCollection<Locations> Locations
    {
        get
        {
            return _database.GetCollection<Locations>("Locations");
        }
    }
}
```

#### <a name="retrieve-the-data"></a><span data-ttu-id="06a3d-189">Получение данных</span><span class="sxs-lookup"><span data-stu-id="06a3d-189">Retrieve the data</span></span>

<span data-ttu-id="06a3d-190">В коде C#, например, в контроллерах веб-API или в реализации пользовательских репозиториев вы можете использовать похожий код для выполнения запросов с помощью API MongoDB.</span><span class="sxs-lookup"><span data-stu-id="06a3d-190">In C# code, like Web API controllers or custom Repositories implementation, you can write similar code to the following when querying through the MongoDB API.</span></span> <span data-ttu-id="06a3d-191">Обратите внимание, что объект `_context` является экземпляром предыдущего класса `LocationsContext`.</span><span class="sxs-lookup"><span data-stu-id="06a3d-191">Note that the `_context` object is an instance of the previous `LocationsContext` class.</span></span>

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a><span data-ttu-id="06a3d-192">Использование переменной среды в файле docker-compose.override.yml для строки подключения MongoDB</span><span class="sxs-lookup"><span data-stu-id="06a3d-192">Use an env-var in the docker-compose.override.yml file for the MongoDB connection string</span></span>

<span data-ttu-id="06a3d-193">При создании объекта MongoClient необходимо указать фундаментальный параметр, который представляет собой параметр `ConnectionString`, указывающий на нужную базу данных.</span><span class="sxs-lookup"><span data-stu-id="06a3d-193">When creating a MongoClient object, it needs a fundamental parameter which is precisely the `ConnectionString` parameter pointing to the right database.</span></span> <span data-ttu-id="06a3d-194">Для eShopOnContainers строка подключения может указывать на локальный контейнер MongoDB Docker или на "рабочую" базу данных Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="06a3d-194">In the case of eShopOnContainers, the connection string can point to a local MongoDB Docker container or to a “production” Azure Cosmos DB database.</span></span>  <span data-ttu-id="06a3d-195">Эта строка подключения берется из переменных среды, заданных в файлах `docker-compose.override.yml`, используемых при развертывании с помощью docker-compose или Visual Studio, как показано в следующем коде YML.</span><span class="sxs-lookup"><span data-stu-id="06a3d-195">That connection string comes from the environment variables defined in the `docker-compose.override.yml` files used when deploying with docker-compose or Visual Studio, as in the following yml code.</span></span>

```yml
# docker-compose.override.yml
version: '3.4'
services:
  # Other services
  locations.api:
    environment:
      # Other settings
      - ConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosql.data}

```

<span data-ttu-id="06a3d-196">Переменная среды `ConnectionString` разрешается следующим образом: если в файле `.env` определена глобальная переменная `ESHOP_AZURE_COSMOSDB` со строкой подключения Azure Cosmos DB, эта строка подключения будет использована для обращения к базе данных Azure Cosmos DB в облаке.</span><span class="sxs-lookup"><span data-stu-id="06a3d-196">The `ConnectionString` environment variable is resolved this way: If the `ESHOP_AZURE_COSMOSDB` global variable is defined in the `.env` file with the Azure Cosmos DB connection string, it will use it to access the Azure Cosmos DB database in the cloud.</span></span> <span data-ttu-id="06a3d-197">Если она не определена, будет использоваться значение `mongodb://nosql.data` и контейнер разработки mongodb.</span><span class="sxs-lookup"><span data-stu-id="06a3d-197">If it’s not defined, it will take the `mongodb://nosql.data` value and use the development mongodb container.</span></span>

<span data-ttu-id="06a3d-198">В следующем коде показан файл `.env` с глобальной переменной среды для строки подключения Azure Cosmos DB, так, как это было реализовано в решении eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="06a3d-198">The following code shows the `.env` file with the Azure Cosmos DB connection string global environment variable, as implemented in eShopOnContainers:</span></span>

```yml
# .env file, in eShopOnContainers root folder
# Other Docker environment variables

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost
ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=<YourDockerHostIP>

#ESHOP_AZURE_COSMOSDB=<YourAzureCosmosDBConnData>

#Other environment variables for additional Azure infrastructure assets
#ESHOP_AZURE_REDIS_BASKET_DB=<YourAzureRedisBasketInfo>
#ESHOP_AZURE_STORAGE_CATALOG_URL=<YourAzureStorage_Catalog_BLOB_URL>
#ESHOP_AZURE_SERVICE_BUS=<YourAzureServiceBusInfo>
```

<span data-ttu-id="06a3d-199">Раскомментируйте строку ESHOP_AZURE_COSMOSDB и замените ее на строку подключения к Azure Cosmos DB, полученную на портале Azure в соответствии с инструкциями в разделе [Подключение приложения MongoDB к Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="06a3d-199">You should uncomment the ESHOP_AZURE_COSMOSDB line and update it with your Azure Cosmos DB connection string obtained from the Azure portal as explained in [Connect a MongoDB application to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

<span data-ttu-id="06a3d-200">Если глобальная переменная `ESHOP_AZURE_COSMOSDB` пуста, т. е. закомментирована в файле `.env`, то контейнер использует строку подключения MongoDB по умолчанию, указывающую на локальный контейнер MongoDB, развернутый в eShopOnContainers, который имеет имя `nosql.data` и определен в файле docker-compose, как показано в следующем коде YML.</span><span class="sxs-lookup"><span data-stu-id="06a3d-200">If the `ESHOP_AZURE_COSMOSDB` global variable is empty, meaning that it is commented out in the `.env` file, then the container uses a default MongoDB connection string pointing to the local MongoDB container deployed in eShopOnContainers which is named `nosql.data` and was defined at the docker-compose file, as shown in the following .yml code.</span></span>

``` yml
# docker-compose.yml
version: '3.4'
services:
  # ...Other services...
  nosql.data:
    image: mongo
```

#### <a name="additional-resources"></a><span data-ttu-id="06a3d-201">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="06a3d-201">Additional resources</span></span>

- <span data-ttu-id="06a3d-202">**Моделирование документальных данных в базах данных NoSQL** </span><span class="sxs-lookup"><span data-stu-id="06a3d-202">**Modeling document data for NoSQL databases** </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/modeling-data>

- <span data-ttu-id="06a3d-203">**Вон Вернон (Vaughn Vernon). Идеальное хранилище агрегатов, созданное с помощью предметно-ориентированного проектирования?**</span><span class="sxs-lookup"><span data-stu-id="06a3d-203">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**</span></span> \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- <span data-ttu-id="06a3d-204">**Введение в Azure Cosmos DB: API для MongoDB**  </span><span class="sxs-lookup"><span data-stu-id="06a3d-204">**Introduction to Azure Cosmos DB: API for MongoDB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction>

- <span data-ttu-id="06a3d-205">**Azure Cosmos DB. Разработка веб-приложения API MongoDB с помощью .NET и портала Azure**  </span><span class="sxs-lookup"><span data-stu-id="06a3d-205">**Azure Cosmos DB: Build a MongoDB API web app with .NET and the Azure portal**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet>

- <span data-ttu-id="06a3d-206">**Использование эмулятора Azure Cosmos DB для разработки и тестирования в локальной среде**  </span><span class="sxs-lookup"><span data-stu-id="06a3d-206">**Use the Azure Cosmos DB Emulator for local development and testing**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/local-emulator>

- <span data-ttu-id="06a3d-207">**Подключение приложения MongoDB к Azure Cosmos DB**  </span><span class="sxs-lookup"><span data-stu-id="06a3d-207">**Connect a MongoDB application to Azure Cosmos DB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account>

- <span data-ttu-id="06a3d-208">**Образ Docker эмулятора Cosmos DB (контейнер для Windows)**   </span><span class="sxs-lookup"><span data-stu-id="06a3d-208">**The Cosmos DB Emulator Docker image (Windows Container)**  </span></span>\
  <https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/>

- <span data-ttu-id="06a3d-209">**Образ Docker MongoDB (контейнер для Linux и Windows)**   </span><span class="sxs-lookup"><span data-stu-id="06a3d-209">**The MongoDB Docker image (Linux and Windows Container)**  </span></span>\
  <https://hub.docker.com/_/mongo/>

- <span data-ttu-id="06a3d-210">**Использование MongoChef (Studio 3T) с Azure Cosmos DB: API для учетной записи MongoDB**  </span><span class="sxs-lookup"><span data-stu-id="06a3d-210">**Use MongoChef (Studio 3T) with an Azure Cosmos DB: API for MongoDB account**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef>

>[!div class="step-by-step"]
><span data-ttu-id="06a3d-211">[Назад](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
>[Вперед](microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="06a3d-211">[Previous](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
[Next](microservice-application-layer-web-api-design.md)</span></span>
