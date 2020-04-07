---
title: Упругий поиск в облачных приложениях
description: Узнайте о добавлении возможностей Elastic Search в облачные приложения.
author: robvet
ms.date: 03/02/2020
ms.openlocfilehash: da6b9402cf266f5a298b05cf837805b2377bc75a
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805562"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a><span data-ttu-id="b153b-103">Elasticsearch в облачно-родном приложении</span><span class="sxs-lookup"><span data-stu-id="b153b-103">Elasticsearch in a cloud-native app</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="b153b-104">Elasticsearch — это распределенная система поиска и аналитики, которая позволяет создавать сложные возможности поиска в различных типах данных.</span><span class="sxs-lookup"><span data-stu-id="b153b-104">Elasticsearch is a distributed search and analytics system that enables complex search capabilities across diverse types of data.</span></span> <span data-ttu-id="b153b-105">Это с открытым исходным кодом и широко популярны.</span><span class="sxs-lookup"><span data-stu-id="b153b-105">It's open source and widely popular.</span></span> <span data-ttu-id="b153b-106">Рассмотрим, как следующие компании интегрируют Elasticsearch в свое приложение:</span><span class="sxs-lookup"><span data-stu-id="b153b-106">Consider how the following companies integrate Elasticsearch into their application:</span></span>

- <span data-ttu-id="b153b-107">[Википедия](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) для полного текста и инкрементного (поиск по мере ввода) поиска.</span><span class="sxs-lookup"><span data-stu-id="b153b-107">[Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) for full-text and incremental (search as you type) searching.</span></span>
- <span data-ttu-id="b153b-108">[GitHub](https://www.elastic.co/customers/github) для индексирования и разоблачения более 8 миллионов хранилищ кода.</span><span class="sxs-lookup"><span data-stu-id="b153b-108">[GitHub](https://www.elastic.co/customers/github) to index and expose over 8 million code repositories.</span></span>  
- <span data-ttu-id="b153b-109">[Докер](https://www.elastic.co/customers/docker) для того, чтобы сделать его контейнер библиотеки обнаружить.</span><span class="sxs-lookup"><span data-stu-id="b153b-109">[Docker](https://www.elastic.co/customers/docker) for making its container library discoverable.</span></span>

<span data-ttu-id="b153b-110">Elasticsearch построен на вершине полнотекстовый поисковой системы [Apache Lucene.](https://lucene.apache.org/core/)</span><span class="sxs-lookup"><span data-stu-id="b153b-110">Elasticsearch is built on top of the [Apache Lucene](https://lucene.apache.org/core/) full-text search engine.</span></span> <span data-ttu-id="b153b-111">Lucene обеспечивает высокопроизводительную индексацию и запросы документов.</span><span class="sxs-lookup"><span data-stu-id="b153b-111">Lucene provides high-performance document indexing and querying.</span></span> <span data-ttu-id="b153b-112">Он индексирует данные с перевернутой схемой индексирования – вместо отображения страниц на ключевые слова, он отображает ключевые слова на страницах так же, как глоссарий в конце книги.</span><span class="sxs-lookup"><span data-stu-id="b153b-112">It indexes data with an inverted indexing scheme – instead of mapping pages to keywords, it maps keywords to pages just like a glossary at the end of a book.</span></span> <span data-ttu-id="b153b-113">Lucene обладает мощными возможностями синтаксиса запросов и может задавлять данные по следующим данным:</span><span class="sxs-lookup"><span data-stu-id="b153b-113">Lucene has powerful query syntax capabilities and can query data by:</span></span>

- <span data-ttu-id="b153b-114">Срок (полное слово)</span><span class="sxs-lookup"><span data-stu-id="b153b-114">Term (a full word)</span></span>
- <span data-ttu-id="b153b-115">Префикс (начинается со слова)</span><span class="sxs-lookup"><span data-stu-id="b153b-115">Prefix (starts-with word)</span></span>
- <span data-ttu-id="b153b-116">Wildcard (с\*использованием фильтров "или "?"</span><span class="sxs-lookup"><span data-stu-id="b153b-116">Wildcard (using "\*" or "?" filters)</span></span>
- <span data-ttu-id="b153b-117">Фраза (последовательность текста в документе)</span><span class="sxs-lookup"><span data-stu-id="b153b-117">Phrase (a sequence of text in a document)</span></span>
- <span data-ttu-id="b153b-118">Значение Boolean (сложный поиск, объединяющий запросы)</span><span class="sxs-lookup"><span data-stu-id="b153b-118">Boolean value (complex searches combining queries)</span></span>

<span data-ttu-id="b153b-119">В то время как Lucene предоставляет низкоуровневую сантехнику для поиска, Elasticsearch предоставляет сервер, который находится на вершине Lucene.</span><span class="sxs-lookup"><span data-stu-id="b153b-119">While Lucene provides low-level plumbing for searching, Elasticsearch provides the server that sits on top of Lucene.</span></span> <span data-ttu-id="b153b-120">Elasticsearch добавляет функциональность более высокого уровня для упрощения работы Lucene, включая RESTful API для доступа к функциональности индексирования и поиска Lucene.</span><span class="sxs-lookup"><span data-stu-id="b153b-120">Elasticsearch adds higher-level functionality to simplify working Lucene, including a RESTful API to access Lucene's indexing and searching functionality.</span></span> <span data-ttu-id="b153b-121">Он также обеспечивает распределенную инфраструктуру, способную к массовой масштабируемости, толерантности к ошибкам и высокой доступности.</span><span class="sxs-lookup"><span data-stu-id="b153b-121">It also provides a distributed infrastructure capable of massive scalability, fault tolerance, and high availability.</span></span>

<span data-ttu-id="b153b-122">Для более крупных облачных приложений со сложными требованиями к поиску Elasticsearch доступен в качестве управляемого сервиса в Azure.</span><span class="sxs-lookup"><span data-stu-id="b153b-122">For larger cloud-native applications with complex search requirements, Elasticsearch is available as managed service in Azure.</span></span> <span data-ttu-id="b153b-123">В Microsoft Azure Marketplace есть преднастроенные шаблоны, которые разработчики могут использовать для развертывания кластера Elasticsearch в Azure.</span><span class="sxs-lookup"><span data-stu-id="b153b-123">The Microsoft Azure Marketplace features preconfigured templates which developers can use to deploy an Elasticsearch cluster on Azure.</span></span>

<span data-ttu-id="b153b-124">В Microsoft Azure Marketplace разработчики могут использовать предварительно настроенные шаблоны, созданные для быстрого развертывания кластера Elasticsearch в Azure.</span><span class="sxs-lookup"><span data-stu-id="b153b-124">From the Microsoft Azure Marketplace, developers can use preconfigured templates built to quickly deploy an Elasticsearch cluster on Azure.</span></span> <span data-ttu-id="b153b-125">Используя предложение, управляемое Azure, можно развернуть до 50 узлов данных, 20 координационных узлов и три выделенных узла.</span><span class="sxs-lookup"><span data-stu-id="b153b-125">Using the Azure-managed offering, you can deploy up to 50 data nodes, 20 coordinating nodes, and three dedicated master nodes.</span></span>

## <a name="summary"></a><span data-ttu-id="b153b-126">Сводка</span><span class="sxs-lookup"><span data-stu-id="b153b-126">Summary</span></span>

<span data-ttu-id="b153b-127">В этой главе представлен подробный взгляд на данные в облачных системах.</span><span class="sxs-lookup"><span data-stu-id="b153b-127">This chapter presented a detailed look at data in cloud-native systems.</span></span> <span data-ttu-id="b153b-128">Мы начали с противопоставления хранения данных в монолитных приложениях с шаблонами хранения данных в облачных системах.</span><span class="sxs-lookup"><span data-stu-id="b153b-128">We started by contrasting data storage in monolithic applications with data storage patterns in cloud-native systems.</span></span> <span data-ttu-id="b153b-129">Мы рассмотрели шаблоны данных, реализованные в облачных системах, включая запросы о перекрестном обслуживании, распределенные транзакции и шаблоны работы с высокообъемными системами.</span><span class="sxs-lookup"><span data-stu-id="b153b-129">We looked at data patterns implemented in cloud-native systems, including cross-service queries, distributed transactions, and patterns to deal with high-volume systems.</span></span> <span data-ttu-id="b153b-130">Мы сравнили с данными NoS'L данные.</span><span class="sxs-lookup"><span data-stu-id="b153b-130">We contrasted SQL with NoSQL data.</span></span> <span data-ttu-id="b153b-131">Мы рассмотрели варианты хранения данных, доступные в Azure, которые включают как ориентированные на Microsoft, так и варианты с открытым исходным кодом.</span><span class="sxs-lookup"><span data-stu-id="b153b-131">We looked at data storage options available in Azure that include both Microsoft-centric and open-source options.</span></span> <span data-ttu-id="b153b-132">Наконец, мы обсудили кэширование и Elasticsearch в облачном приложении.</span><span class="sxs-lookup"><span data-stu-id="b153b-132">Finally, we discussed caching and Elasticsearch in a cloud-native application.</span></span>

### <a name="references"></a><span data-ttu-id="b153b-133">Ссылки</span><span class="sxs-lookup"><span data-stu-id="b153b-133">References</span></span>

- [<span data-ttu-id="b153b-134">Шаблон CQRS</span><span class="sxs-lookup"><span data-stu-id="b153b-134">Command and Query Responsibility Segregation (CQRS) pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [<span data-ttu-id="b153b-135">Шаблон поиска событий</span><span class="sxs-lookup"><span data-stu-id="b153b-135">Event Sourcing pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [<span data-ttu-id="b153b-136">Почему в теореме CAP не толерантна раздел RDBMS и почему она доступна?</span><span class="sxs-lookup"><span data-stu-id="b153b-136">Why isn't RDBMS Partition Tolerant in CAP Theorem and why is it Available?</span></span>](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [<span data-ttu-id="b153b-137">Материализованный вид</span><span class="sxs-lookup"><span data-stu-id="b153b-137">Materialized View</span></span>](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [<span data-ttu-id="b153b-138">Все, что вам действительно нужно знать о базах данных с открытым исходным кодом</span><span class="sxs-lookup"><span data-stu-id="b153b-138">All you really need to know about open source databases</span></span>](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [<span data-ttu-id="b153b-139">Шаблон компенсирующих транзакций</span><span class="sxs-lookup"><span data-stu-id="b153b-139">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="b153b-140">Шаблон саги</span><span class="sxs-lookup"><span data-stu-id="b153b-140">Saga Pattern</span></span>](https://microservices.io/patterns/data/saga.html)

- [<span data-ttu-id="b153b-141">Сага Шаблоны (ru) Как осуществлять бизнес-операции с помощью микрослужб</span><span class="sxs-lookup"><span data-stu-id="b153b-141">Saga Patterns | How to implement business transactions using microservices</span></span>](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [<span data-ttu-id="b153b-142">Шаблон компенсирующих транзакций</span><span class="sxs-lookup"><span data-stu-id="b153b-142">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="b153b-143">Получение за 9-Ball: Космос DB Последовательность Уровни Разъяснения</span><span class="sxs-lookup"><span data-stu-id="b153b-143">Getting Behind the 9-Ball: Cosmos DB Consistency Levels Explained</span></span>](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [<span data-ttu-id="b153b-144">Изучение различных типов баз данных НоСЗЛ Часть II</span><span class="sxs-lookup"><span data-stu-id="b153b-144">Exploring the different types of NoSQL Databases Part II</span></span>](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [<span data-ttu-id="b153b-145">По базам данных RDBMS, NoS'L и NewS'L. Интервью с Джоном Райаном</span><span class="sxs-lookup"><span data-stu-id="b153b-145">On RDBMS, NoSQL and NewSQL databases. Interview with John Ryan</span></span>](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [<span data-ttu-id="b153b-146">СЗЛ vs НоСЗЛ vs НьюСЗЛ: Полное сравнение</span><span class="sxs-lookup"><span data-stu-id="b153b-146">SQL vs NoSQL vs NewSQL: The Full Comparison</span></span>](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [<span data-ttu-id="b153b-147">DASH: Четыре свойства базы данных Kubernetes-Native</span><span class="sxs-lookup"><span data-stu-id="b153b-147">DASH: Four Properties of Kubernetes-Native Databases</span></span>](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [<span data-ttu-id="b153b-148">ТараканDB</span><span class="sxs-lookup"><span data-stu-id="b153b-148">CockroachDB</span></span>](https://www.cockroachlabs.com/)

- [<span data-ttu-id="b153b-149">TiDB</span><span class="sxs-lookup"><span data-stu-id="b153b-149">TiDB</span></span>](https://pingcap.com/en/)

- [<span data-ttu-id="b153b-150">YugabyteDB</span><span class="sxs-lookup"><span data-stu-id="b153b-150">YugabyteDB</span></span>](https://www.yugabyte.com/)

- [<span data-ttu-id="b153b-151">Витесс</span><span class="sxs-lookup"><span data-stu-id="b153b-151">Vitess</span></span>](https://vitess.io/)

- [<span data-ttu-id="b153b-152">Elasticsearch: The Definitive Guide (Elasticsearch: полное руководство)</span><span class="sxs-lookup"><span data-stu-id="b153b-152">Elasticsearch: The Definitive Guide</span></span>](http://shop.oreilly.com/product/0636920028505.do)
  
- [<span data-ttu-id="b153b-153">Введение в Апач Лусене</span><span class="sxs-lookup"><span data-stu-id="b153b-153">Introduction to Apache Lucene</span></span>](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
><span data-ttu-id="b153b-154">[Назад](azure-caching.md)
>[Вперед](resiliency.md)</span><span class="sxs-lookup"><span data-stu-id="b153b-154">[Previous](azure-caching.md)
[Next](resiliency.md)</span></span> <!-- Next Chapter -->
