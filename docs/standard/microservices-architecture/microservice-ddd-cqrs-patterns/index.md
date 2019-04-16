---
title: Использование микрослужб с шаблонами DDD и CQRS для решения сложных бизнес-задач
description: Архитектура микрослужб .NET для упакованных в контейнеры приложений .NET | Сведения об использовании микрослужб с шаблонами DDD и CQRS для решения сложных бизнес-задач
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: f17acd6765de96bf8cec28c4e212733822fa0b73
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611111"
---
# <a name="tackle-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a><span data-ttu-id="af3f7-103">Использование микрослужб с шаблонами DDD и CQRS для решения сложных бизнес-задач</span><span class="sxs-lookup"><span data-stu-id="af3f7-103">Tackle Business Complexity in a Microservice with DDD and CQRS Patterns</span></span>

<span data-ttu-id="af3f7-104">*Разработка модели предметной области для каждой микрослужбы или ограниченного контекста, который отражает понимание предметной области бизнеса.*</span><span class="sxs-lookup"><span data-stu-id="af3f7-104">*Design a domain model for each microservice or Bounded Context that reflects understanding of the business domain.*</span></span>

<span data-ttu-id="af3f7-105">Этот раздел посвящен более сложным микрослужбам, которые реализуются для комплексных подсистем, и микрослужбам, создаваемым на основе знаний экспертов в определенной области с учетом постоянно меняющихся бизнес-правил.</span><span class="sxs-lookup"><span data-stu-id="af3f7-105">This section focuses on more advanced microservices that you implement when you need to tackle complex subsystems, or microservices derived from the knowledge of domain experts with ever-changing business rules.</span></span> <span data-ttu-id="af3f7-106">Шаблоны архитектуры, используемые в этом разделе, основаны на принципах проблемно-ориентированного проектирования (DDD) и разделения команд и запросов (CQRS), как показано на рис. 7-1.</span><span class="sxs-lookup"><span data-stu-id="af3f7-106">The architecture patterns used in this section are based on domain-driven design (DDD) and Command and Query Responsibility Segregation (CQRS) approaches, as illustrated in Figure 7-1.</span></span>

![Внешняя архитектура: шаблоны микрослужб, шлюзы API, устойчивый обмен данными, публикации и подписки и т.д. Внутривенная архитектура: управление данными, CRUD, шаблоны DDD, внедрение зависимостей, несколько библиотек и т.д.](./media/image1.png)

<span data-ttu-id="af3f7-108">**Рис. 7-1**.</span><span class="sxs-lookup"><span data-stu-id="af3f7-108">**Figure 7-1**.</span></span> <span data-ttu-id="af3f7-109">Архитектура внешних микрослужб и внутренние шаблоны архитектуры для каждой микрослужбы</span><span class="sxs-lookup"><span data-stu-id="af3f7-109">External microservice architecture versus internal architecture patterns for each microservice</span></span>

<span data-ttu-id="af3f7-110">Но большинство методов, применяемых для микрослужб на основе данных, таких как способы реализации службы веб-API ASP.NET Core или предоставления метаданных Swagger с помощью Swashbuckle или NSwag, также применимы и к более сложным микрослужбам, реализуемым с помощью внутренних шаблонов DDD.</span><span class="sxs-lookup"><span data-stu-id="af3f7-110">However, most of the techniques for data driven microservices, such as how to implement an ASP.NET Core Web API service or how to expose Swagger metadata with Swashbuckle or NSwag, are also applicable to the more advanced microservices implemented internally with DDD patterns.</span></span> <span data-ttu-id="af3f7-111">Этот раздел дополняет предыдущие, так как большинство описанных ранее методов применимы и в этом случае, а также к любой из микрослужб.</span><span class="sxs-lookup"><span data-stu-id="af3f7-111">This section is an extension of the previous sections, because most of the practices explained earlier also apply here or for any kind of microservice.</span></span>

<span data-ttu-id="af3f7-112">В этом разделе сначала приводятся сведения об упрощенных шаблонах CQRS, используемых в образце приложения eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="af3f7-112">This section first provides details on the simplified CQRS patterns used in the eShopOnContainers reference application.</span></span> <span data-ttu-id="af3f7-113">Далее вы получите представление о методах DDD, позволяющих найти общие шаблоны, которые можно повторно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="af3f7-113">Later, you will get an overview of the DDD techniques that enable you to find common patterns that you can reuse in your applications.</span></span>

<span data-ttu-id="af3f7-114">DDD — это обширная тема, по которой доступно множество учебных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="af3f7-114">DDD is a large topic with a rich set of resources for learning.</span></span> <span data-ttu-id="af3f7-115">Вы можете начать знакомство с ней с книги [Domain-Driven Design](https://domainlanguage.com/ddd/) (Проблемно-ориентированное проектирование) Эрика Эванса (Eric Evans) и дополнительных материалов от Вона Вернона (Vaughn Vernon), Джимми Нилссона (Jimmy Nilsson), Грега Янга (Greg Young), Уди Дахана (Udi Dahan), Джимми Богарда (Jimmy Bogard) и многих других экспертов по DDD и CQRS.</span><span class="sxs-lookup"><span data-stu-id="af3f7-115">You can start with books like [Domain-Driven Design](https://domainlanguage.com/ddd/) by Eric Evans and additional materials from Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, and many other DDD/CQRS experts.</span></span> <span data-ttu-id="af3f7-116">Но учиться применять приемы DDD следует в первую очередь в процессе общения, проведения телеконференций и сеансов моделирования предметных областей с экспертами.</span><span class="sxs-lookup"><span data-stu-id="af3f7-116">But most of all you need to try to learn how to apply DDD techniques from the conversations, whiteboarding, and domain modeling sessions with the experts in your concrete business domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="af3f7-117">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="af3f7-117">Additional resources</span></span>

##### <a name="ddd-domain-driven-design"></a><span data-ttu-id="af3f7-118">DDD (проблемно-ориентированное проектирование)</span><span class="sxs-lookup"><span data-stu-id="af3f7-118">DDD (Domain-Driven Design)</span></span>

- <span data-ttu-id="af3f7-119">**Эрик Эванс (Eric Evans). Предметно-ориентированный язык**  \\</span><span class="sxs-lookup"><span data-stu-id="af3f7-119">**Eric Evans. Domain Language** \\</span></span>
  <https://domainlanguage.com/>

- <span data-ttu-id="af3f7-120">**Мартин Фоулер (Martin Fowler). Предметно-ориентированное проектирование** \\</span><span class="sxs-lookup"><span data-stu-id="af3f7-120">**Martin Fowler. Domain-Driven Design** \\</span></span>
  <https://martinfowler.com/tags/domain%20driven%20design.html>

- <span data-ttu-id="af3f7-121">**Джимми Богард (Jimmy Bogard). Усиление предметной области: руководство для начинающих** \\</span><span class="sxs-lookup"><span data-stu-id="af3f7-121">**Jimmy Bogard. Strengthening your domain: a primer** \\</span></span>
  <https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/>

##### <a name="ddd-books"></a><span data-ttu-id="af3f7-122">Книги по DDD</span><span class="sxs-lookup"><span data-stu-id="af3f7-122">DDD books</span></span>

- <span data-ttu-id="af3f7-123">**Эрик Эванс (Eric Evans). Domain-Driven Design: Tackling Complexity in the Heart of Software** \ (Предметно-ориентированное проектирование. Структуризация сложных программных систем)</span><span class="sxs-lookup"><span data-stu-id="af3f7-123">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software** \\</span></span>
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- <span data-ttu-id="af3f7-124">**Эрик Эванс (Eric Evans). Справочник по предметно-ориентированному проектированию: Определения и обзор шаблонов** \\</span><span class="sxs-lookup"><span data-stu-id="af3f7-124">**Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries** \\</span></span>
  <https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/>

- <span data-ttu-id="af3f7-125">**Вон Вернон (Vaughn Vernon). Реализация проблемно-ориентированного проектирования** \\</span><span class="sxs-lookup"><span data-stu-id="af3f7-125">**Vaughn Vernon. Implementing Domain-Driven Design** \\</span></span>
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- <span data-ttu-id="af3f7-126">**Вон Вернон (Vaughn Vernon). Основные сведения о предметно-ориентированном проектировании** \\</span><span class="sxs-lookup"><span data-stu-id="af3f7-126">**Vaughn Vernon. Domain-Driven Design Distilled** \\</span></span>
  <https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/>

- <span data-ttu-id="af3f7-127">**Джимми Нилссон (Jimmy Nilsson). Применение предметно-ориентированного проектирования и шаблонов** \\</span><span class="sxs-lookup"><span data-stu-id="af3f7-127">**Jimmy Nilsson. Applying Domain-Driven Design and Patterns** \\</span></span>
  <https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/>

- <span data-ttu-id="af3f7-128">**Сезар де ла Торре (Cesar de la Torre). Руководство по N-уровневой предметно-ориентированной архитектуре на .NET** \\</span><span class="sxs-lookup"><span data-stu-id="af3f7-128">**Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET** \\</span></span>
  <https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/>

- <span data-ttu-id="af3f7-129">**Абель Аврам (Abel Avram) и Флойд Маринеску (Floyd Marinescu). Кратко о предметно-ориентированном проектировании** \\</span><span class="sxs-lookup"><span data-stu-id="af3f7-129">**Abel Avram and Floyd Marinescu. Domain-Driven Design Quickly** \\</span></span>
  <https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/>

- <span data-ttu-id="af3f7-130">**Скотт Миллетт (Scott Millett), Ник Тюн (Nick Tune). Шаблоны, принципы и методы предметно-ориентированного проектирования** \\</span><span class="sxs-lookup"><span data-stu-id="af3f7-130">**Scott Millett, Nick Tune - Patterns, Principles, and Practices of Domain-Driven Design** \\</span></span>
  <http://www.wrox.com/WileyCDA/WroxTitle/Patterns-Principles-and-Practices-of-Domain-Driven-Design.productCd-1118714709.html>

##### <a name="ddd-training"></a><span data-ttu-id="af3f7-131">Обучение по DDD</span><span class="sxs-lookup"><span data-stu-id="af3f7-131">DDD training</span></span>

- <span data-ttu-id="af3f7-132">**Джули Лерман (Julie Lerman) и Стив Смит (Steve Smith). Основы предметно-ориентированного проектирования** \\</span><span class="sxs-lookup"><span data-stu-id="af3f7-132">**Julie Lerman and Steve Smith. Domain-Driven Design Fundamentals** \\</span></span>
  <https://bit.ly/PS-DDD>

>[!div class="step-by-step"]
><span data-ttu-id="af3f7-133">[Назад](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
>[Вперед](apply-simplified-microservice-cqrs-ddd-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="af3f7-133">[Previous](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
[Next](apply-simplified-microservice-cqrs-ddd-patterns.md)</span></span>
