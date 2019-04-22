---
title: Реализация прикладного уровня микрослужб с помощью веб-интерфейсов API
description: Архитектура микрослужб .NET для контейнерных приложений .NET | Сведения о внедрении зависимостей и шаблонах медиатора, а также их реализации на прикладном уровне веб-API.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 376b4eca99ed60a54831aa37099108692d8bac6d
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612164"
---
# <a name="implement-the-microservice-application-layer-using-the-web-api"></a><span data-ttu-id="d8b51-103">Реализация прикладного уровня для микрослужб с помощью веб-API</span><span class="sxs-lookup"><span data-stu-id="d8b51-103">Implement the microservice application layer using the Web API</span></span>

## <a name="use-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a><span data-ttu-id="d8b51-104">Внедрение объектов инфраструктуры в прикладной уровень с помощью внедрения зависимостей</span><span class="sxs-lookup"><span data-stu-id="d8b51-104">Use Dependency Injection to inject infrastructure objects into your application layer</span></span>

<span data-ttu-id="d8b51-105">Как упоминалось ранее, прикладной уровень может быть реализован в рамках создаваемого артефакта (сборки), например проекта веб-интерфейса API или проекта веб-приложения MVC.</span><span class="sxs-lookup"><span data-stu-id="d8b51-105">As mentioned previously, the application layer can be implemented as part of the artifact (assembly) you are building, such as within a Web API project or an MVC web app project.</span></span> <span data-ttu-id="d8b51-106">При создании микрослужбы с помощью ASP.NET Core прикладным уровнем обычно является библиотека веб-интерфейсов API.</span><span class="sxs-lookup"><span data-stu-id="d8b51-106">In the case of a microservice built with ASP.NET Core, the application layer will usually be your Web API library.</span></span> <span data-ttu-id="d8b51-107">Чтобы отделить ту часть, которая берется из ASP.NET Core (инфраструктуру и контроллеры), от пользовательского кода прикладного уровня, можно поместить прикладной уровень в отдельную библиотеку классов, хотя это необязательно.</span><span class="sxs-lookup"><span data-stu-id="d8b51-107">If you want to separate what is coming from ASP.NET Core (its infrastructure plus your controllers) from your custom application layer code, you could also place your application layer in a separate class library, but that is optional.</span></span>

<span data-ttu-id="d8b51-108">Например, код прикладного уровня для микрослужбы размещения заказов реализуется непосредственно в рамках проекта **Ordering.API** (проекта веб-интерфейса API ASP.NET Core), как показано на рис. 7-23.</span><span class="sxs-lookup"><span data-stu-id="d8b51-108">For instance, the application layer code of the ordering microservice is directly implemented as part of the **Ordering.API** project (an ASP.NET Core Web API project), as shown in Figure 7-23.</span></span>

![Представление обозревателя решений для микрослужбы Ordering.API, показывающее вложенные папки в папке приложения: Behaviors, Commands, DomainEventHandlers, IntegrationEvents, Models, Queries и Validations.](./media/image20.png)

<span data-ttu-id="d8b51-110">**Рис. 7-23**.</span><span class="sxs-lookup"><span data-stu-id="d8b51-110">**Figure 7-23**.</span></span> <span data-ttu-id="d8b51-111">Прикладной уровень в проекте веб-интерфейса API ASP.NET Core Ordering.API</span><span class="sxs-lookup"><span data-stu-id="d8b51-111">The application layer in the Ordering.API ASP.NET Core Web API project</span></span>

<span data-ttu-id="d8b51-112">ASP.NET Core содержит простой [встроенный контейнер IoC](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (представленный интерфейсом IServiceProvider), поддерживающий внедрение через конструктор по умолчанию, а ASP.NET предоставляет посредством внедрения зависимостей определенные службы.</span><span class="sxs-lookup"><span data-stu-id="d8b51-112">ASP.NET Core includes a simple [built-in IoC container](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (represented by the IServiceProvider interface) that supports constructor injection by default, and ASP.NET makes certain services available through DI.</span></span> <span data-ttu-id="d8b51-113">В ASP.NET Core под термином *служба* понимаются любые зарегистрированные типы, которые будут внедряться посредством внедрения зависимостей.</span><span class="sxs-lookup"><span data-stu-id="d8b51-113">ASP.NET Core uses the term *service* for any of the types you register that will be injected through DI.</span></span> <span data-ttu-id="d8b51-114">Настроить службы встроенного контейнера можно в методе ConfigureServices в классе Startup вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="d8b51-114">You configure the built-in container's services in the ConfigureServices method in your application's Startup class.</span></span> <span data-ttu-id="d8b51-115">Зависимости реализуются в службах, которые требуются типу и которые вы регистрируете в контейнере IoC.</span><span class="sxs-lookup"><span data-stu-id="d8b51-115">Your dependencies are implemented in the services that a type needs and that you register in the IoC container.</span></span>

<span data-ttu-id="d8b51-116">Как правило, необходимо внедрить зависимости, реализующие объекты инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="d8b51-116">Typically, you want to inject dependencies that implement infrastructure objects.</span></span> <span data-ttu-id="d8b51-117">Типичной внедряемой зависимостью является репозиторий.</span><span class="sxs-lookup"><span data-stu-id="d8b51-117">A very typical dependency to inject is a repository.</span></span> <span data-ttu-id="d8b51-118">Однако можно внедрять и любые другие имеющиеся зависимости инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="d8b51-118">But you could inject any other infrastructure dependency that you may have.</span></span> <span data-ttu-id="d8b51-119">Чтобы упростить реализацию, можно напрямую внедрить объект на основе шаблона "Единица работы" (объект EF DbContext), так как DBContext также является реализацией сохраняемых объектов инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="d8b51-119">For simpler implementations, you could directly inject your Unit of Work pattern object (the EF DbContext object), because the DBContext is also the implementation of your infrastructure persistence objects.</span></span>

<span data-ttu-id="d8b51-120">В приведенном ниже примере показано, как платформа .NET Core внедряет необходимые объекты репозитория посредством конструктора.</span><span class="sxs-lookup"><span data-stu-id="d8b51-120">In the following example, you can see how .NET Core is injecting the required repository objects through the constructor.</span></span> <span data-ttu-id="d8b51-121">Класс представляет собой обработчик команд, о котором мы поговорим в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="d8b51-121">The class is a command handler, which we will cover in the next section.</span></span>

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

<span data-ttu-id="d8b51-122">Этот класс использует внедренные репозитории для выполнения транзакции и сохранения изменений состояния.</span><span class="sxs-lookup"><span data-stu-id="d8b51-122">The class uses the injected repositories to execute the transaction and persist the state changes.</span></span> <span data-ttu-id="d8b51-123">Не имеет значения, является ли класс обработчиком команд, методом контроллера веб-интерфейса API ASP.NET Core или [службой приложения DDD](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span><span class="sxs-lookup"><span data-stu-id="d8b51-123">It does not matter whether that class is a command handler, an ASP.NET Core Web API controller method, or a [DDD Application Service](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span></span> <span data-ttu-id="d8b51-124">В любом случае он представляет собой простой класс, который использует репозитории, сущности домена и другие средства координации приложения подобно тому, как это делает обработчик команд.</span><span class="sxs-lookup"><span data-stu-id="d8b51-124">It is ultimately a simple class that uses repositories, domain entities, and other application coordination in a fashion similar to a command handler.</span></span> <span data-ttu-id="d8b51-125">Внедрение зависимостей работает одинаково для всех перечисленных выше классов, как в этом примере, в котором внедрение зависимостей основано на конструкторе.</span><span class="sxs-lookup"><span data-stu-id="d8b51-125">Dependency Injection works the same way for all the mentioned classes, as in the example using DI based on the constructor.</span></span>

### <a name="register-the-dependency-implementation-types-and-interfaces-or-abstractions"></a><span data-ttu-id="d8b51-126">Регистрация типов и интерфейсов или абстракций для реализации зависимостей</span><span class="sxs-lookup"><span data-stu-id="d8b51-126">Register the dependency implementation types and interfaces or abstractions</span></span>

<span data-ttu-id="d8b51-127">Прежде чем использовать объекты, внедренные посредством конструкторов, необходимо знать, где следует зарегистрировать интерфейсы и классы, которые предоставляют объекты, внедренные в приложение с помощью внедрения зависимостей</span><span class="sxs-lookup"><span data-stu-id="d8b51-127">Before you use the objects injected through constructors, you need to know where to register the interfaces and classes that produce the objects injected into your application classes through DI.</span></span> <span data-ttu-id="d8b51-128">(например, в случае внедрения зависимостей на основе конструктора, показанного выше).</span><span class="sxs-lookup"><span data-stu-id="d8b51-128">(Like DI based on the constructor, as shown previously.)</span></span>

#### <a name="use-the-built-in-ioc-container-provided-by-aspnet-core"></a><span data-ttu-id="d8b51-129">Использование встроенного контейнера IoC, предоставляемого платформой ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d8b51-129">Use the built-in IoC container provided by ASP.NET Core</span></span>

<span data-ttu-id="d8b51-130">При использовании встроенного контейнера IoC, предоставляемого платформой ASP.NET Core, типы, которые нужно внедрить, регистрируются в методе ConfigureServices в файле Startup.cs, как в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="d8b51-130">When you use the built-in IoC container provided by ASP.NET Core, you register the types you want to inject in the ConfigureServices method in the Startup.cs file, as in the following code:</span></span>

```csharp
// Registration of types into ASP.NET Core built-in container
public void ConfigureServices(IServiceCollection services)
{
    // Register out-of-the-box framework services.
    services.AddDbContext<CatalogContext>(c =>
    {
        c.UseSqlServer(Configuration["ConnectionString"]);
    },
    ServiceLifetime.Scoped
    );
    services.AddMvc();
    // Register custom application dependencies.
    services.AddScoped<IMyCustomRepository, MyCustomSQLRepository>();
}
```

<span data-ttu-id="d8b51-131">Чаще всего типы регистрируются в контейнере IoC парами, состоящими из интерфейса и связанного с ним класса реализации.</span><span class="sxs-lookup"><span data-stu-id="d8b51-131">The most common pattern when registering types in an IoC container is to register a pair of types—an interface and its related implementation class.</span></span> <span data-ttu-id="d8b51-132">Затем при запросе объекта из контейнера IoC посредством любого конструктора вы запрашиваете объект определенного типа интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d8b51-132">Then when you request an object from the IoC container through any constructor, you request an object of a certain type of interface.</span></span> <span data-ttu-id="d8b51-133">Например, в предыдущем примере в последней строке указано, что когда любой из конструкторов имеет зависимость от IMyCustomRepository (интерфейса или абстракции), контейнер IoC внедряет экземпляр класса реализации MyCustomSQLServerRepository.</span><span class="sxs-lookup"><span data-stu-id="d8b51-133">For instance, in the previous example, the last line states that when any of your constructors have a dependency on IMyCustomRepository (interface or abstraction), the IoC container will inject an instance of the MyCustomSQLServerRepository implementation class.</span></span>

#### <a name="use-the-scrutor-library-for-automatic-types-registration"></a><span data-ttu-id="d8b51-134">Автоматическая регистрация типов с помощью библиотеки Scrutor</span><span class="sxs-lookup"><span data-stu-id="d8b51-134">Use the Scrutor library for automatic types registration</span></span>

<span data-ttu-id="d8b51-135">При использовании внедрения зависимостей в .NET Core может потребоваться проверить сборку и автоматически зарегистрировать ее типы в соответствии с соглашением.</span><span class="sxs-lookup"><span data-stu-id="d8b51-135">When using DI in .NET Core, you might want to be able to scan an assembly and automatically register its types by convention.</span></span> <span data-ttu-id="d8b51-136">Эта возможность в настоящее время недоступна в ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d8b51-136">This feature is not currently available in ASP.NET Core.</span></span> <span data-ttu-id="d8b51-137">Однако для этого можно использовать библиотеку [Scrutor](https://github.com/khellang/Scrutor).</span><span class="sxs-lookup"><span data-stu-id="d8b51-137">However, you can use the [Scrutor](https://github.com/khellang/Scrutor) library for that.</span></span> <span data-ttu-id="d8b51-138">Такой подход удобен в случае, если имеются десятки типов, которые необходимо зарегистрировать в контейнере IoC.</span><span class="sxs-lookup"><span data-stu-id="d8b51-138">This approach is convenient when you have dozens of types that need to be registered in your IoC container.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="d8b51-139">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="d8b51-139">Additional resources</span></span>

- <span data-ttu-id="d8b51-140">**Мэтью Кинг (Matthew King). Регистрация служб в Scrutor** \\</span><span class="sxs-lookup"><span data-stu-id="d8b51-140">**Matthew King. Registering services with Scrutor** \\</span></span>
  <https://www.mking.net/blog/registering-services-with-scrutor>

- <span data-ttu-id="d8b51-141">**Кристиан Хелланг (Kristian Hellang). Scrutor.**</span><span class="sxs-lookup"><span data-stu-id="d8b51-141">**Kristian Hellang. Scrutor.**</span></span> <span data-ttu-id="d8b51-142">Репозиторий GitHub.</span><span class="sxs-lookup"><span data-stu-id="d8b51-142">GitHub repo.</span></span> \
  <https://github.com/khellang/Scrutor>

#### <a name="use-autofac-as-an-ioc-container"></a><span data-ttu-id="d8b51-143">Использование Autofac в качестве контейнера IoC</span><span class="sxs-lookup"><span data-stu-id="d8b51-143">Use Autofac as an IoC container</span></span>

<span data-ttu-id="d8b51-144">Вы также можете использовать дополнительные контейнеры IoC и подключить их к конвейеру ASP.NET Core, как в случае с микрослужбой размещения заказов в eShopOnContainers, которая использует [Autofac](https://autofac.org/).</span><span class="sxs-lookup"><span data-stu-id="d8b51-144">You can also use additional IoC containers and plug them into the ASP.NET Core pipeline, as in the ordering microservice in eShopOnContainers, which uses [Autofac](https://autofac.org/).</span></span> <span data-ttu-id="d8b51-145">При использовании Autofac типы, как правило, регистрируются посредством модулей, что позволяет разделить типы регистрации на несколько файлов в зависимости от местонахождения типов, так же как типы приложения распределяются по нескольким библиотекам классов.</span><span class="sxs-lookup"><span data-stu-id="d8b51-145">When using Autofac you typically register the types via modules, which allow you to split the registration types between multiple files depending on where your types are, just as you could have the application types distributed across multiple class libraries.</span></span>

<span data-ttu-id="d8b51-146">Например, ниже приведен [модуль приложения Autofac](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) для проекта [веб-интерфейса API Ordering.API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) с типами, которые потребуется внедрить.</span><span class="sxs-lookup"><span data-stu-id="d8b51-146">For example, the following is the [Autofac application module](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) for the [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) project with the types you will want to inject.</span></span>

```csharp
public class ApplicationModule : Autofac.Module
{
    public string QueriesConnectionString { get; }
    public ApplicationModule(string qconstr)
    {
        QueriesConnectionString = qconstr;
    }

    protected override void Load(ContainerBuilder builder)
    {
        builder.Register(c => new OrderQueries(QueriesConnectionString))
            .As<IOrderQueries>()
            .InstancePerLifetimeScope();
        builder.RegisterType<BuyerRepository>()
            .As<IBuyerRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<OrderRepository>()
            .As<IOrderRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<RequestManager>()
            .As<IRequestManager>()
            .InstancePerLifetimeScope();
   }
}
```

<span data-ttu-id="d8b51-147">Autofac также может [сканировать сборки и регистрировать типы в соответствии с соглашениями об именовании](https://autofac.readthedocs.io/en/latest/register/scanning.html).</span><span class="sxs-lookup"><span data-stu-id="d8b51-147">Autofac also has a feature to [scan assemblies and register types by name conventions](https://autofac.readthedocs.io/en/latest/register/scanning.html).</span></span>

<span data-ttu-id="d8b51-148">Принципы и процесс регистрации очень похожи на регистрацию типов с помощью встроенного контейнера IoC ASP.NET Core, но синтаксис при использовании Autofac немного иной.</span><span class="sxs-lookup"><span data-stu-id="d8b51-148">The registration process and concepts are very similar to the way you can register types with the built-in ASP.NET Core IoC container, but the syntax when using Autofac is a bit different.</span></span>

<span data-ttu-id="d8b51-149">В примере кода абстракция IOrderRepository регистрируется вместе с классом реализации OrderRepository.</span><span class="sxs-lookup"><span data-stu-id="d8b51-149">In the example code, the abstraction IOrderRepository is registered along with the implementation class OrderRepository.</span></span> <span data-ttu-id="d8b51-150">Это означает, что каждый раз, когда в конструкторе объявляется зависимость посредством абстракции или интерфейса IOrderRepository, контейнер IoC внедряет экземпляр класса OrderRepository.</span><span class="sxs-lookup"><span data-stu-id="d8b51-150">This means that whenever a constructor is declaring a dependency through the IOrderRepository abstraction or interface, the IoC container will inject an instance of the OrderRepository class.</span></span>

<span data-ttu-id="d8b51-151">Тип области экземпляра определяет то, как экземпляр используется совместно при запросах к одной и той же службе или зависимости.</span><span class="sxs-lookup"><span data-stu-id="d8b51-151">The instance scope type determines how an instance is shared between requests for the same service or dependency.</span></span> <span data-ttu-id="d8b51-152">При запросе зависимости контейнер IoC может вернуть следующее:</span><span class="sxs-lookup"><span data-stu-id="d8b51-152">When a request is made for a dependency, the IoC container can return the following:</span></span>

- <span data-ttu-id="d8b51-153">один экземпляр для каждой области времени существования (в контейнере IoC ASP.NET Core такой экземпляр называется экземпляром *с заданной областью*);</span><span class="sxs-lookup"><span data-stu-id="d8b51-153">A single instance per lifetime scope (referred to in the ASP.NET Core IoC container as *scoped*).</span></span>

- <span data-ttu-id="d8b51-154">новый экземпляр для каждой зависимости (в контейнере IoC ASP.NET Core такой экземпляр называется *временным*);</span><span class="sxs-lookup"><span data-stu-id="d8b51-154">A new instance per dependency (referred to in the ASP.NET Core IoC container as *transient*).</span></span>

- <span data-ttu-id="d8b51-155">один общий экземпляр для всех объектов, использующих контейнер IoC (в контейнере IoC ASP.NET Core такой экземпляр называется *единичным*).</span><span class="sxs-lookup"><span data-stu-id="d8b51-155">A single instance shared across all objects using the IoC container (referred to in the ASP.NET Core IoC container as *singleton*).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="d8b51-156">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="d8b51-156">Additional resources</span></span>

- <span data-ttu-id="d8b51-157">**Общие сведения о внедрении зависимостей в ASP.NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="d8b51-157">**Introduction to Dependency Injection in ASP.NET Core** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection](/aspnet/core/fundamentals/dependency-injection)

- <span data-ttu-id="d8b51-158">**Autofac.**</span><span class="sxs-lookup"><span data-stu-id="d8b51-158">**Autofac.**</span></span> <span data-ttu-id="d8b51-159">Официальная документация.</span><span class="sxs-lookup"><span data-stu-id="d8b51-159">Official documentation.</span></span> \
  <https://docs.autofac.org/en/latest/>

- <span data-ttu-id="d8b51-160">**Сравнение времени существования службы контейнеров IoC ASP.NET Core с областями действия экземпляра контейнера IoC Autofac. Сезар де ла Торре (Cesar de la Torre).**</span><span class="sxs-lookup"><span data-stu-id="d8b51-160">**Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes - Cesar de la Torre.**</span></span> \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="implement-the-command-and-command-handler-patterns"></a><span data-ttu-id="d8b51-161">Реализация шаблонов команд и обработчиков команд</span><span class="sxs-lookup"><span data-stu-id="d8b51-161">Implement the Command and Command Handler patterns</span></span>

<span data-ttu-id="d8b51-162">В примере внедрения зависимостей через конструктор в предыдущем разделе контейнер IoC внедрял репозитории через конструктор в классе.</span><span class="sxs-lookup"><span data-stu-id="d8b51-162">In the DI-through-constructor example shown in the previous section, the IoC container was injecting repositories through a constructor in a class.</span></span> <span data-ttu-id="d8b51-163">Но куда именно они внедрялись?</span><span class="sxs-lookup"><span data-stu-id="d8b51-163">But exactly where were they injected?</span></span> <span data-ttu-id="d8b51-164">В простом веб-API (например, микрослужбе каталога в eShopOnContainers) они внедряются на уровне контроллеров MVC в конструкторе контроллера как часть конвейера запросов в ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d8b51-164">In a simple Web API (for example, the catalog microservice in eShopOnContainers), you inject them at the MVC controllers’ level, in a controller constructor, as part of the request pipeline of ASP.NET Core.</span></span> <span data-ttu-id="d8b51-165">Однако в коде, приведенном в начале этого раздела (класс [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) из службы Ordering.API в eShopOnContainers), внедрение зависимостей производится через конструктор определенного обработчика команд.</span><span class="sxs-lookup"><span data-stu-id="d8b51-165">However, in the initial code of this section (the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) class from the Ordering.API service in eShopOnContainers), the injection of dependencies is done through the constructor of a particular command handler.</span></span> <span data-ttu-id="d8b51-166">Давайте рассмотрим, что такое обработчик команд и зачем его использовать.</span><span class="sxs-lookup"><span data-stu-id="d8b51-166">Let us explain what a command handler is and why you would want to use it.</span></span>

<span data-ttu-id="d8b51-167">Шаблон команды, по сути, связан с шаблоном CQRS, который был представлен ранее в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="d8b51-167">The Command pattern is intrinsically related to the CQRS pattern that was introduced earlier in this guide.</span></span> <span data-ttu-id="d8b51-168">CQRS имеет два аспекта.</span><span class="sxs-lookup"><span data-stu-id="d8b51-168">CQRS has two sides.</span></span> <span data-ttu-id="d8b51-169">Первый аспект — это запросы, причем используются упрощенные запросы на основе микро-ORM [Dapper](https://github.com/StackExchange/dapper-dot-net), который был рассмотрен ранее.</span><span class="sxs-lookup"><span data-stu-id="d8b51-169">The first area is queries, using simplified queries with the [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, which was explained previously.</span></span> <span data-ttu-id="d8b51-170">Второй аспект — это команды, которые являются отправной точкой для транзакций, и канал входных данных извне службы.</span><span class="sxs-lookup"><span data-stu-id="d8b51-170">The second area is commands, which are the starting point for transactions, and the input channel from outside the service.</span></span>

<span data-ttu-id="d8b51-171">Как показано на рис. 7-24, шаблон основан на принятии команд со стороны клиента, их обработке на основе правил модели предметной области и, наконец, сохранении состояний с помощью транзакций.</span><span class="sxs-lookup"><span data-stu-id="d8b51-171">As shown in Figure 7-24, the pattern is based on accepting commands from the client side, processing them based on the domain model rules, and finally persisting the states with transactions.</span></span>

![Представление высокого уровня стороны записи в CQRS: приложение пользовательского интерфейса отправляет команду через API, которая получает CommandHandler, зависящий от модели предметной области и инфраструктуры для обновления базы данных.](./media/image21.png)

<span data-ttu-id="d8b51-173">**Рис. 7-24**.</span><span class="sxs-lookup"><span data-stu-id="d8b51-173">**Figure 7-24**.</span></span> <span data-ttu-id="d8b51-174">Общее представление команд или "уровня транзакций" в шаблоне CQRS</span><span class="sxs-lookup"><span data-stu-id="d8b51-174">High-level view of the commands or “transactional side” in a CQRS pattern</span></span>

### <a name="the-command-class"></a><span data-ttu-id="d8b51-175">Класс команд</span><span class="sxs-lookup"><span data-stu-id="d8b51-175">The command class</span></span>

<span data-ttu-id="d8b51-176">Команда — это запрос к системе на выполнение действия, которое изменяет состояние системы.</span><span class="sxs-lookup"><span data-stu-id="d8b51-176">A command is a request for the system to perform an action that changes the state of the system.</span></span> <span data-ttu-id="d8b51-177">Команды являются императивными и должны обрабатываться только один раз.</span><span class="sxs-lookup"><span data-stu-id="d8b51-177">Commands are imperative, and should be processed just once.</span></span>

<span data-ttu-id="d8b51-178">Так как команды являются императивами, в их именах обычно есть глагол в повелительном наклонении (например, create или update) и может присутствовать тип агрегата, например CreateOrderCommand.</span><span class="sxs-lookup"><span data-stu-id="d8b51-178">Since commands are imperatives, they are typically named with a verb in the imperative mood (for example, "create" or "update"), and they might include the aggregate type, such as CreateOrderCommand.</span></span> <span data-ttu-id="d8b51-179">В отличие от события, команда не связана с фактом в прошлом. Это всего лишь запрос, который может быть отклонен.</span><span class="sxs-lookup"><span data-stu-id="d8b51-179">Unlike an event, a command is not a fact from the past; it is only a request, and thus may be refused.</span></span>

<span data-ttu-id="d8b51-180">Команды могут поступать из пользовательского интерфейса в результате инициации запроса пользователем или из диспетчера процессов, когда он предписывает агрегату выполнить действие.</span><span class="sxs-lookup"><span data-stu-id="d8b51-180">Commands can originate from the UI as a result of a user initiating a request, or from a process manager when the process manager is directing an aggregate to perform an action.</span></span>

<span data-ttu-id="d8b51-181">Важной особенностью команды является то, что она должна обрабатываться только один раз одним получателем.</span><span class="sxs-lookup"><span data-stu-id="d8b51-181">An important characteristic of a command is that it should be processed just once by a single receiver.</span></span> <span data-ttu-id="d8b51-182">Связано это с тем, что команда представляет собой одно действие или транзакцию, которую нужно выполнить в приложении.</span><span class="sxs-lookup"><span data-stu-id="d8b51-182">This is because a command is a single action or transaction you want to perform in the application.</span></span> <span data-ttu-id="d8b51-183">Например, одну и ту же команду создания заказа не следует обрабатывать несколько раз.</span><span class="sxs-lookup"><span data-stu-id="d8b51-183">For example, the same order creation command should not be processed more than once.</span></span> <span data-ttu-id="d8b51-184">Это важное различие между командами и событиями.</span><span class="sxs-lookup"><span data-stu-id="d8b51-184">This is an important difference between commands and events.</span></span> <span data-ttu-id="d8b51-185">События могут обрабатываться несколько раз, так как одно событие может представлять интерес для множества систем или микрослужб.</span><span class="sxs-lookup"><span data-stu-id="d8b51-185">Events may be processed multiple times, because many systems or microservices might be interested in the event.</span></span>

<span data-ttu-id="d8b51-186">Кроме того, важно, чтобы команда обрабатывалась только одни раз, если она не является идемпотентной.</span><span class="sxs-lookup"><span data-stu-id="d8b51-186">In addition, it is important that a command be processed only once in case the command is not idempotent.</span></span> <span data-ttu-id="d8b51-187">Команда является идемпотентной, если она может выполняться несколько раз с одинаковым результатом либо из-за самого ее характера, либо из-за способа обработки команды системой.</span><span class="sxs-lookup"><span data-stu-id="d8b51-187">A command is idempotent if it can be executed multiple times without changing the result, either because of the nature of the command, or because of the way the system handles the command.</span></span>

<span data-ttu-id="d8b51-188">Команды имеет смысл делать идемпотентными, если этого требуют бизнес-правила и инварианты предметной области.</span><span class="sxs-lookup"><span data-stu-id="d8b51-188">It is a good practice to make your commands and updates idempotent when it makes sense under your domain’s business rules and invariants.</span></span> <span data-ttu-id="d8b51-189">Продолжая приведенный выше пример, если по какой-либо причине (логика повтора, взлом и т. д.) одна и та же команда CreateOrder поступает в систему несколько раз, необходимо иметь возможность определить такую ситуацию и предотвратить создание нескольких заказов.</span><span class="sxs-lookup"><span data-stu-id="d8b51-189">For instance, to use the same example, if for any reason (retry logic, hacking, etc.) the same CreateOrder command reaches your system multiple times, you should be able to identify it and ensure that you do not create multiple orders.</span></span> <span data-ttu-id="d8b51-190">Для этого в операции необходимо включить какой-либо идентификатор, чтобы определять, были ли команда или обновление уже обработаны.</span><span class="sxs-lookup"><span data-stu-id="d8b51-190">To do so, you need to attach some kind of identity in the operations and identify whether the command or update was already processed.</span></span>

<span data-ttu-id="d8b51-191">Команда отправляется одному получателю. Она не публикуется.</span><span class="sxs-lookup"><span data-stu-id="d8b51-191">You send a command to a single receiver; you do not publish a command.</span></span> <span data-ttu-id="d8b51-192">Публикуются события, сообщающие некий факт — что произошло что-то, что может представлять интерес для получателей событий.</span><span class="sxs-lookup"><span data-stu-id="d8b51-192">Publishing is for events that state a fact—that something has happened and might be interesting for event receivers.</span></span> <span data-ttu-id="d8b51-193">Издателя событий не интересует, какие приемники получат событие и что они будут с ним делать.</span><span class="sxs-lookup"><span data-stu-id="d8b51-193">In the case of events, the publisher has no concerns about which receivers get the event or what they do it.</span></span> <span data-ttu-id="d8b51-194">Однако с событиями интеграции или предметной области дело обстоит иначе, о чем уже говорилось в предыдущих разделах.</span><span class="sxs-lookup"><span data-stu-id="d8b51-194">But domain or integration events are a different story already introduced in previous sections.</span></span>

<span data-ttu-id="d8b51-195">Команда реализуется с помощью класса, который содержит поля данных или коллекции со всеми сведениями, необходимыми для выполнения этой команды.</span><span class="sxs-lookup"><span data-stu-id="d8b51-195">A command is implemented with a class that contains data fields or collections with all the information that is needed in order to execute that command.</span></span> <span data-ttu-id="d8b51-196">Команда — это объект передачи данных (DTO) особого типа, предназначенный специально для запроса изменений или транзакций.</span><span class="sxs-lookup"><span data-stu-id="d8b51-196">A command is a special kind of Data Transfer Object (DTO), one that is specifically used to request changes or transactions.</span></span> <span data-ttu-id="d8b51-197">Сама по себе команда основана только на тех сведениях, которые необходимы для ее обработки, и ни на чем больше.</span><span class="sxs-lookup"><span data-stu-id="d8b51-197">The command itself is based on exactly the information that is needed for processing the command, and nothing more.</span></span>

<span data-ttu-id="d8b51-198">В приведенном ниже примере показан упрощенный класс CreateOrderCommand.</span><span class="sxs-lookup"><span data-stu-id="d8b51-198">The following example shows the simplified CreateOrderCommand class.</span></span> <span data-ttu-id="d8b51-199">Это неизменяемая команда, которая используется в микрослужбе размещения заказов в eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="d8b51-199">This is an immutable command that is used in the ordering microservice in eShopOnContainers.</span></span>

```csharp
// DDD and CQRS patterns comment
// Note that we recommend that you implement immutable commands
// In this case, immutability is achieved by having all the setters as private
// plus being able to update the data just once, when creating the object
// through the constructor.
// References on immutable commands:
// http://cqrs.nu/Faq
// https://docs.spine3.org/motivation/immutability.html
// http://blog.gauffin.org/2012/06/griffin-container-introducing-command-support/
// https://msdn.microsoft.com/library/bb383979.aspx
[DataContract]
public class CreateOrderCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    private readonly List<OrderItemDTO> _orderItems;
    [DataMember]
    public string City { get; private set; }
    [DataMember]
    public string Street { get; private set; }
    [DataMember]
    public string State { get; private set; }
    [DataMember]
    public string Country { get; private set; }
    [DataMember]
    public string ZipCode { get; private set; }
    [DataMember]
    public string CardNumber { get; private set; }
    [DataMember]
    public string CardHolderName { get; private set; }
    [DataMember]
    public DateTime CardExpiration { get; private set; }
    [DataMember]
    public string CardSecurityNumber { get; private set; }
    [DataMember]
    public int CardTypeId { get; private set; }
    [DataMember]
    public IEnumerable<OrderItemDTO> OrderItems => _orderItems;

    public CreateOrderCommand()
    {
        _orderItems = new List<OrderItemDTO>();
    }

    public CreateOrderCommand(List<BasketItem> basketItems, string city,
        string street,
        string state, string country, string zipcode,
        string cardNumber, string cardHolderName, DateTime cardExpiration,
        string cardSecurityNumber, int cardTypeId) : this()
    {
        _orderItems = MapToOrderItems(basketItems);
        City = city;
        Street = street;
        State = state;
        Country = country;
        ZipCode = zipcode;
        CardNumber = cardNumber;
        CardHolderName = cardHolderName;
        CardSecurityNumber = cardSecurityNumber;
        CardTypeId = cardTypeId;
        CardExpiration = cardExpiration;
    }

    public class OrderItemDTO
    {
        public int ProductId { get; set; }
        public string ProductName { get; set; }
        public decimal UnitPrice { get; set; }
        public decimal Discount { get; set; }
        public int Units { get; set; }
        public string PictureUrl { get; set; }
    }
}
```

<span data-ttu-id="d8b51-200">По существу, класс команды содержит все данные, необходимые для выполнения бизнес-транзакции с помощью объектов модели предметной области.</span><span class="sxs-lookup"><span data-stu-id="d8b51-200">Basically, the command class contains all the data you need for performing a business transaction by using the domain model objects.</span></span> <span data-ttu-id="d8b51-201">Таким образом, команды — это попросту структуры данных, которые содержат доступные только для чтения данные, но не алгоритмы.</span><span class="sxs-lookup"><span data-stu-id="d8b51-201">Thus, commands are simply data structures that contain read-only data, and no behavior.</span></span> <span data-ttu-id="d8b51-202">Имя команды указывает на ее назначение.</span><span class="sxs-lookup"><span data-stu-id="d8b51-202">The command’s name indicates its purpose.</span></span> <span data-ttu-id="d8b51-203">Во многих языках, например в C#, команды представлены классами, но они не являются настоящими классами в объектно-ориентированном смысле.</span><span class="sxs-lookup"><span data-stu-id="d8b51-203">In many languages like C#, commands are represented as classes, but they are not true classes in the real object-oriented sense.</span></span>

<span data-ttu-id="d8b51-204">Дополнительной характеристикой команд является неизменяемость, так как предполагается, что они обрабатываются непосредственно моделью предметной области.</span><span class="sxs-lookup"><span data-stu-id="d8b51-204">As an additional characteristic, commands are immutable, because the expected usage is that they are processed directly by the domain model.</span></span> <span data-ttu-id="d8b51-205">Они не должны изменяться в течение предполагаемого времени существования.</span><span class="sxs-lookup"><span data-stu-id="d8b51-205">They do not need to change during their projected lifetime.</span></span> <span data-ttu-id="d8b51-206">В классе C# неизменяемость может обеспечиваться благодаря отсутствию методов задания или других методов, которые изменяют внутреннее состояние.</span><span class="sxs-lookup"><span data-stu-id="d8b51-206">In a C# class, immutability can be achieved by not having any setters or other methods that change internal state.</span></span>

<span data-ttu-id="d8b51-207">Если предполагается, что команды будут проходить процесс сериализации/десериализации, свойства должны иметь закрытый метод задания и атрибут `[DataMember]` (или `[JsonProperty]`), в противном случае десериализатор не сможет восстановить объект в месте назначения с необходимыми значениями.</span><span class="sxs-lookup"><span data-stu-id="d8b51-207">Bear in mind that if you intend or expect commands will be going through a serializing/deserializing process, the properties must have private setter, and the `[DataMember]` (or `[JsonProperty]`) attribute, otherwise the deserializer will not be able to reconstruct the object at destination with the required values.</span></span>

<span data-ttu-id="d8b51-208">Например, в плане данных класс команды для создания заказа может быть аналогичен создаваемому заказу, однако, вероятно, требуемые атрибуты могут различаться.</span><span class="sxs-lookup"><span data-stu-id="d8b51-208">For example, the command class for creating an order is probably similar in terms of data to the order you want to create, but you probably do not need the same attributes.</span></span> <span data-ttu-id="d8b51-209">Например, команда CreateOrderCommand не включает в себя идентификатор заказа, так как заказ еще не создан.</span><span class="sxs-lookup"><span data-stu-id="d8b51-209">For instance, CreateOrderCommand does not have an order ID, because the order has not been created yet.</span></span>

<span data-ttu-id="d8b51-210">Многие классы команд могут быть простыми и требуют лишь несколько полей, связанных с изменяемым состоянием.</span><span class="sxs-lookup"><span data-stu-id="d8b51-210">Many command classes can be simple, requiring only a few fields about some state that needs to be changed.</span></span> <span data-ttu-id="d8b51-211">Например, это верно в случае изменения состояния заказа с "обрабатывается" на "оплачен" или "отправлен" с помощью команды наподобие следующей:</span><span class="sxs-lookup"><span data-stu-id="d8b51-211">That would be the case if you are just changing the status of an order from “in process” to “paid” or “shipped” by using a command similar to the following:</span></span>

```csharp
[DataContract]
public class UpdateOrderStatusCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    public string Status { get; private set; }

    [DataMember]
    public string OrderId { get; private set; }

    [DataMember]
    public string BuyerIdentityGuid { get; private set; }
}
```

<span data-ttu-id="d8b51-212">Некоторые разработчики разделяют объекты запросов пользовательского интерфейса и объекты DTO команд, но это всего лишь вопрос предпочтений.</span><span class="sxs-lookup"><span data-stu-id="d8b51-212">Some developers make their UI request objects separate from their command DTOs, but that is just a matter of preference.</span></span> <span data-ttu-id="d8b51-213">Такое разделение требует значительных усилий, а преимущества невелики, причем объекты очень схожи по сути.</span><span class="sxs-lookup"><span data-stu-id="d8b51-213">It is a tedious separation with not much added value, and the objects are almost exactly the same shape.</span></span> <span data-ttu-id="d8b51-214">Например, в eShopOnContainers некоторые команды поступают непосредственно со стороны клиента.</span><span class="sxs-lookup"><span data-stu-id="d8b51-214">For instance, in eShopOnContainers, some commands come directly from the client side.</span></span>

### <a name="the-command-handler-class"></a><span data-ttu-id="d8b51-215">Класс обработчика команд</span><span class="sxs-lookup"><span data-stu-id="d8b51-215">The Command Handler class</span></span>

<span data-ttu-id="d8b51-216">Для каждой команды следует реализовать класс обработчика команд.</span><span class="sxs-lookup"><span data-stu-id="d8b51-216">You should implement a specific command handler class for each command.</span></span> <span data-ttu-id="d8b51-217">Этого требует шаблон, и именно в этом классе будут использоваться объект команды, объекты предметной области и объекты репозиториев инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="d8b51-217">That is how the pattern works, and it is where you will use the command object, the domain objects, and the infrastructure repository objects.</span></span> <span data-ttu-id="d8b51-218">Обработчик команд — это, по сути, центральный элемент прикладного уровня в рамках CQRS и DDD.</span><span class="sxs-lookup"><span data-stu-id="d8b51-218">The command handler is in fact the heart of the application layer in terms of CQRS and DDD.</span></span> <span data-ttu-id="d8b51-219">Однако вся логика предметной области должна содержаться в классах предметной области — корневых объектах агрегатов (корневых сущностях), дочерних сущностях или [службах предметной области](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), но не в обработчике команд, который представляет собой класс прикладного уровня.</span><span class="sxs-lookup"><span data-stu-id="d8b51-219">However, all the domain logic should be contained within the domain classes—within the aggregate roots (root entities), child entities, or [domain services](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), but not within the command handler, which is a class from the application layer.</span></span>

<span data-ttu-id="d8b51-220">Класс обработчика команд предоставляет надежную основу для реализации принципа единой ответственности (SRP), упомянутого в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="d8b51-220">The command handler class offers a strong stepping stone in the way to achieve the Single Responsibility Principle (SRP) mentioned in a previous section.</span></span>

<span data-ttu-id="d8b51-221">Обработчик команд принимает команду и получает результат из используемого агрегата.</span><span class="sxs-lookup"><span data-stu-id="d8b51-221">A command handler receives a command and obtains a result from the aggregate that is used.</span></span> <span data-ttu-id="d8b51-222">Результатом должно быть успешное выполнение команды или исключение.</span><span class="sxs-lookup"><span data-stu-id="d8b51-222">The result should be either successful execution of the command, or an exception.</span></span> <span data-ttu-id="d8b51-223">В случае исключения состояние системы не должно меняться.</span><span class="sxs-lookup"><span data-stu-id="d8b51-223">In the case of an exception, the system state should be unchanged.</span></span>

<span data-ttu-id="d8b51-224">Обработчик команд обычно выполняет следующие действия:</span><span class="sxs-lookup"><span data-stu-id="d8b51-224">The command handler usually takes the following steps:</span></span>

- <span data-ttu-id="d8b51-225">получает объект команды, например DTO (от [медиатора](https://en.wikipedia.org/wiki/Mediator_pattern) или другого объекта инфраструктуры);</span><span class="sxs-lookup"><span data-stu-id="d8b51-225">It receives the command object, like a DTO (from the [mediator](https://en.wikipedia.org/wiki/Mediator_pattern) or other infrastructure object).</span></span>

- <span data-ttu-id="d8b51-226">проверяет допустимость команды (если она не была проверена медиатором);</span><span class="sxs-lookup"><span data-stu-id="d8b51-226">It validates that the command is valid (if not validated by the mediator).</span></span>

- <span data-ttu-id="d8b51-227">создает экземпляр корневой сущности агрегата, являющийся целевым для текущей команды;</span><span class="sxs-lookup"><span data-stu-id="d8b51-227">It instantiates the aggregate root instance that is the target of the current command.</span></span>

- <span data-ttu-id="d8b51-228">выполняет метод экземпляра корневой сущности агрегата, получая необходимые данные из команды;</span><span class="sxs-lookup"><span data-stu-id="d8b51-228">It executes the method on the aggregate root instance, getting the required data from the command.</span></span>

- <span data-ttu-id="d8b51-229">сохраняет новое состояние агрегата в связанной с ним базе данных.</span><span class="sxs-lookup"><span data-stu-id="d8b51-229">It persists the new state of the aggregate to its related database.</span></span> <span data-ttu-id="d8b51-230">Эта последняя операция и является транзакцией.</span><span class="sxs-lookup"><span data-stu-id="d8b51-230">This last operation is the actual transaction.</span></span>

<span data-ttu-id="d8b51-231">Как правило, обработчик команд работает с одним агрегатом, определяемым корневым объектом агрегата (корневой сущностью).</span><span class="sxs-lookup"><span data-stu-id="d8b51-231">Typically, a command handler deals with a single aggregate driven by its aggregate root (root entity).</span></span> <span data-ttu-id="d8b51-232">Если принимаемая команда должна влиять на несколько агрегатов, можно использовать события предметной области для распространения состояний или действий в нескольких агрегатах.</span><span class="sxs-lookup"><span data-stu-id="d8b51-232">If multiple aggregates should be impacted by the reception of a single command, you could use domain events to propagate states or actions across multiple aggregates.</span></span>

<span data-ttu-id="d8b51-233">Важным моментом является то, что при обработке команды вся логика предметной области должна находиться внутри модели предметной области (агрегатов), причем она должна быть полностью инкапсулирована и готова для модульного тестирования.</span><span class="sxs-lookup"><span data-stu-id="d8b51-233">The important point here is that when a command is being processed, all the domain logic should be inside the domain model (the aggregates), fully encapsulated and ready for unit testing.</span></span> <span data-ttu-id="d8b51-234">Обработчик команд служит лишь для того, чтобы получить модель предметной области из базы данных и (на последнем этапе) сообщить уровню инфраструктуры (репозиториям) о необходимости сохранить изменения в случае изменения модели.</span><span class="sxs-lookup"><span data-stu-id="d8b51-234">The command handler just acts as a way to get the domain model from the database, and as the final step, to tell the infrastructure layer (repositories) to persist the changes when the model is changed.</span></span> <span data-ttu-id="d8b51-235">Преимуществом такого подхода является возможность рефакторинга логики предметной области в рамках изолированной, полностью инкапсулированной поведенческой модели предметной области без изменения кода на прикладном уровне или уровне инфраструктуры, то есть на связующем уровне (обработчики команд, веб-интерфейс API, репозитории и т. д.).</span><span class="sxs-lookup"><span data-stu-id="d8b51-235">The advantage of this approach is that you can refactor the domain logic in an isolated, fully encapsulated, rich, behavioral domain model without changing code in the application or infrastructure layers, which are the plumbing level (command handlers, Web API, repositories, etc.).</span></span>

<span data-ttu-id="d8b51-236">Если обработчики команд становятся слишком сложными, содержащими слишком много логики, это может быть признаком плохого кода.</span><span class="sxs-lookup"><span data-stu-id="d8b51-236">When command handlers get complex, with too much logic, that can be a code smell.</span></span> <span data-ttu-id="d8b51-237">Проверьте их и, если найдете логику предметной области, выполните рефакторинг кода, чтобы переместить эту логику в методы объектов предметной области (корневая сущность агрегата и дочерняя сущность).</span><span class="sxs-lookup"><span data-stu-id="d8b51-237">Review them, and if you find domain logic, refactor the code to move that domain behavior to the methods of the domain objects (the aggregate root and child entity).</span></span>

<span data-ttu-id="d8b51-238">В приведенном ниже коде в качестве примера класса обработчика команд показан тот же класс CreateOrderCommandHandler, который вы уже видели в начале этой главы.</span><span class="sxs-lookup"><span data-stu-id="d8b51-238">As an example of a command handler class, the following code shows the same CreateOrderCommandHandler class that you saw at the beginning of this chapter.</span></span> <span data-ttu-id="d8b51-239">В этом случае мы хотим привлечь внимание к методу Handle и операциям с объектами и агрегатами модели предметной области.</span><span class="sxs-lookup"><span data-stu-id="d8b51-239">In this case, we want to highlight the Handle method and the operations with the domain model objects/aggregates.</span></span>

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

<span data-ttu-id="d8b51-240">Обработчик команд должен выполнять следующие дополнительные действия:</span><span class="sxs-lookup"><span data-stu-id="d8b51-240">These are additional steps a command handler should take:</span></span>

- <span data-ttu-id="d8b51-241">использовать данные команды для взаимодействия с методами и поведением корневой сущности агрегата;</span><span class="sxs-lookup"><span data-stu-id="d8b51-241">Use the command’s data to operate with the aggregate root’s methods and behavior.</span></span>

- <span data-ttu-id="d8b51-242">вызывать события предметной области внутри объектов предметной области во время выполнения транзакции прозрачным с точки зрения обработчика команд образом;</span><span class="sxs-lookup"><span data-stu-id="d8b51-242">Internally within the domain objects, raise domain events while the transaction is executed, but that is transparent from a command handler point of view.</span></span>

- <span data-ttu-id="d8b51-243">в случае успешного результата операции агрегата вызывать события интеграции после завершения транзакции.</span><span class="sxs-lookup"><span data-stu-id="d8b51-243">If the aggregate’s operation result is successful and after the transaction is finished, raise integration events.</span></span> <span data-ttu-id="d8b51-244">(Эти события могут также вызываться классами инфраструктуры, такими как репозитории.)</span><span class="sxs-lookup"><span data-stu-id="d8b51-244">(These might also be raised by infrastructure classes like repositories.)</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="d8b51-245">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="d8b51-245">Additional resources</span></span>

- <span data-ttu-id="d8b51-246">**Марк Симанн (Mark Seemann). Граничный слой приложения не является объектно-ориентированным** \\</span><span class="sxs-lookup"><span data-stu-id="d8b51-246">**Mark Seemann. At the Boundaries, Applications are Not Object-Oriented** \\</span></span>
  <https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/>

- <span data-ttu-id="d8b51-247">**Команды и события** \\</span><span class="sxs-lookup"><span data-stu-id="d8b51-247">**Commands and events** \\</span></span>
  <http://cqrs.nu/Faq/commands-and-events>

- <span data-ttu-id="d8b51-248">**Что делает обработчик команд?**</span><span class="sxs-lookup"><span data-stu-id="d8b51-248">**What does a command handler do?**</span></span> \
  <http://cqrs.nu/Faq/command-handlers>

- <span data-ttu-id="d8b51-249">**Джимми Богард (Jimmy Bogard). Шаблоны команд домена — обработчики** \\</span><span class="sxs-lookup"><span data-stu-id="d8b51-249">**Jimmy Bogard. Domain Command Patterns – Handlers** \\</span></span>
  <https://jimmybogard.com/domain-command-patterns-handlers/>

- <span data-ttu-id="d8b51-250">**Джимми Богард (Jimmy Bogard). Шаблоны команд домена — проверка** \\</span><span class="sxs-lookup"><span data-stu-id="d8b51-250">**Jimmy Bogard. Domain Command Patterns – Validation** \\</span></span>
  <https://jimmybogard.com/domain-command-patterns-validation/>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a><span data-ttu-id="d8b51-251">Конвейер обработки команд: активация обработчика команд</span><span class="sxs-lookup"><span data-stu-id="d8b51-251">The Command process pipeline: how to trigger a command handler</span></span>

<span data-ttu-id="d8b51-252">Следующий вопрос заключается в том, как вызывается обработчик команд.</span><span class="sxs-lookup"><span data-stu-id="d8b51-252">The next question is how to invoke a command handler.</span></span> <span data-ttu-id="d8b51-253">Его можно вызывать из каждого связанного контроллера ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d8b51-253">You could manually call it from each related ASP.NET Core controller.</span></span> <span data-ttu-id="d8b51-254">Однако такой подход требует слишком большого количества связей и не идеален.</span><span class="sxs-lookup"><span data-stu-id="d8b51-254">However, that approach would be too coupled and is not ideal.</span></span>

<span data-ttu-id="d8b51-255">Другие два варианта, которые рекомендуются, представлены ниже:</span><span class="sxs-lookup"><span data-stu-id="d8b51-255">The other two main options, which are the recommended options, are:</span></span>

- <span data-ttu-id="d8b51-256">посредством артефакта шаблона медиатора в памяти;</span><span class="sxs-lookup"><span data-stu-id="d8b51-256">Through an in-memory Mediator pattern artifact.</span></span>

- <span data-ttu-id="d8b51-257">с помощью асинхронной очереди сообщений между контроллерами и обработчиками.</span><span class="sxs-lookup"><span data-stu-id="d8b51-257">With an asynchronous message queue, in between controllers and handlers.</span></span>

### <a name="use-the-mediator-pattern-in-memory-in-the-command-pipeline"></a><span data-ttu-id="d8b51-258">Использование шаблона медиатора (в памяти) в конвейере команд</span><span class="sxs-lookup"><span data-stu-id="d8b51-258">Use the Mediator pattern (in-memory) in the command pipeline</span></span>

<span data-ttu-id="d8b51-259">Как показано на рис. 7-25, в рамках подхода на основе CQRS используется интеллектуальный медиатор, похожий на шину в памяти, который может осуществлять перенаправление в нужный обработчик команд в соответствии с типом полученной команды или объекта DTO.</span><span class="sxs-lookup"><span data-stu-id="d8b51-259">As shown in Figure 7-25, in a CQRS approach you use an intelligent mediator, similar to an in-memory bus, which is smart enough to redirect to the right command handler based on the type of the command or DTO being received.</span></span> <span data-ttu-id="d8b51-260">Одиночные черные стрелки между компонентами представляют зависимости между объектами (которые часто внедряются посредством внедрения зависимостей) и соответствующие взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="d8b51-260">The single black arrows between components represent the dependencies between objects (in many cases, injected through DI) with their related interactions.</span></span>

![Детальное изображение фрагмента предыдущего рисунка: контроллер ASP.NET Core отправляет команду в конвейер команд MediatR, чтобы они попали в соответствующий обработчик.](./media/image22.png)

<span data-ttu-id="d8b51-262">**Рис. 7-25**.</span><span class="sxs-lookup"><span data-stu-id="d8b51-262">**Figure 7-25**.</span></span> <span data-ttu-id="d8b51-263">Использование шаблона медиатора в процессе обработки в отдельной микрослужбе CQRS</span><span class="sxs-lookup"><span data-stu-id="d8b51-263">Using the Mediator pattern in process in a single CQRS microservice</span></span>

<span data-ttu-id="d8b51-264">Основанием для применения шаблона медиатора является то, что в корпоративных приложениях обработка запросов может становиться сложной.</span><span class="sxs-lookup"><span data-stu-id="d8b51-264">The reason that using the Mediator pattern makes sense is that in enterprise applications, the processing requests can get complicated.</span></span> <span data-ttu-id="d8b51-265">Вам может требоваться добавить сквозную функциональность, например ведения журнала, проверки, аудит и безопасность.</span><span class="sxs-lookup"><span data-stu-id="d8b51-265">You want to be able to add an open number of cross-cutting concerns like logging, validations, audit, and security.</span></span> <span data-ttu-id="d8b51-266">В таком случае вы можете применить конвейер медиатора (см. статью [Шаблон медиатора](https://en.wikipedia.org/wiki/Mediator_pattern)) в качестве средства для реализации дополнительной сквозной функциональности или поведения.</span><span class="sxs-lookup"><span data-stu-id="d8b51-266">In these cases, you can rely on a mediator pipeline (see [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern)) to provide a means for these extra behaviors or cross-cutting concerns.</span></span>

<span data-ttu-id="d8b51-267">Медиатор — это объект, который инкапсулирует методы выполнения этого процесса: он координирует выполнение на основе состояния, способы вызова обработчика команд и полезные данные, предоставляемые ему.</span><span class="sxs-lookup"><span data-stu-id="d8b51-267">A mediator is an object that encapsulates the “how” of this process: it coordinates execution based on state, the way a command handler is invoked, or the payload you provide to the handler.</span></span> <span data-ttu-id="d8b51-268">С помощью медиатора вы можете применять сквозную функциональность централизованным и прозрачным образом, применяя декораторы (или [расширения функциональности конвейера](https://github.com/jbogard/MediatR/wiki/Behaviors) начиная с [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)).</span><span class="sxs-lookup"><span data-stu-id="d8b51-268">With a mediator component you can apply cross-cutting concerns in a centralized and transparent way by applying decorators (or [pipeline behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) since [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)).</span></span> <span data-ttu-id="d8b51-269">Дополнительную информацию см. в статье [Шаблон декоратора](https://en.wikipedia.org/wiki/Decorator_pattern).</span><span class="sxs-lookup"><span data-stu-id="d8b51-269">For more information, see the [Decorator pattern](https://en.wikipedia.org/wiki/Decorator_pattern).</span></span>

<span data-ttu-id="d8b51-270">Декораторы и расширения функциональности похожи на [аспектно-ориентированное программирование (АОП)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), но применяются к определенному конвейеру обработки, управляемому медиатором.</span><span class="sxs-lookup"><span data-stu-id="d8b51-270">Decorators and behaviors are similar to [Aspect Oriented Programming (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), only applied to a specific process pipeline managed by the mediator component.</span></span> <span data-ttu-id="d8b51-271">Аспекты в АОП, которые реализуют сквозную функциональность, применяются на основе *средств внедрения аспектов*, внедряемых во время компиляции или с помощью перехвата вызовов объектов.</span><span class="sxs-lookup"><span data-stu-id="d8b51-271">Aspects in AOP that implement cross-cutting concerns are applied based on *aspect weavers* injected at compilation time or based on object call interception.</span></span> <span data-ttu-id="d8b51-272">Иногда говорят, что оба подхода АОП работают "волшебным образом", так как их применение трудно проследить.</span><span class="sxs-lookup"><span data-stu-id="d8b51-272">Both typical AOP approaches are sometimes said to work "like magic," because it is not easy to see how AOP does its work.</span></span> <span data-ttu-id="d8b51-273">В случае серьезных проблем или ошибок отладка в АОП может вызывать трудности.</span><span class="sxs-lookup"><span data-stu-id="d8b51-273">When dealing with serious issues or bugs, AOP can be difficult to debug.</span></span> <span data-ttu-id="d8b51-274">С другой стороны, эти декораторы и расширения функциональности являются явными и применяются только в контексте медиатора, поэтому отладка является гораздо более предсказуемой и легкой.</span><span class="sxs-lookup"><span data-stu-id="d8b51-274">On the other hand, these decorators/behaviors are explicit and applied only in the context of the mediator, so debugging is much more predictable and easy.</span></span>

<span data-ttu-id="d8b51-275">Например, в микрослужбе размещения заказов eShopOnContainers реализованы два образца расширений функциональности: класс [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) и класс [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs).</span><span class="sxs-lookup"><span data-stu-id="d8b51-275">For example, in the eShopOnContainers ordering microservice, we implemented two sample behaviors, a [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class and a [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class.</span></span> <span data-ttu-id="d8b51-276">Реализация расширений функциональности рассмотрена в следующем разделе. В нем показано, как в eShopOnContainers используются [расширения функциональности](https://github.com/jbogard/MediatR/wiki/Behaviors) [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0).</span><span class="sxs-lookup"><span data-stu-id="d8b51-276">The implementation of the behaviors is explained in the next section by showing how eShopOnContainers uses [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors).</span></span>

### <a name="use-message-queues-out-of-proc-in-the-commands-pipeline"></a><span data-ttu-id="d8b51-277">Использование очередей сообщений (внепроцессных) в конвейере команд</span><span class="sxs-lookup"><span data-stu-id="d8b51-277">Use message queues (out-of-proc) in the command’s pipeline</span></span>

<span data-ttu-id="d8b51-278">Еще один вариант — это использование асинхронных сообщений на основе брокеров или очередей сообщений, как показано на рис. 7-26.</span><span class="sxs-lookup"><span data-stu-id="d8b51-278">Another choice is to use asynchronous messages based on brokers or message queues, as shown in Figure 7-26.</span></span> <span data-ttu-id="d8b51-279">Его можно использовать в сочетании с компонентом медиатора непосредственно перед обработчиком команд.</span><span class="sxs-lookup"><span data-stu-id="d8b51-279">That option could also be combined with the mediator component right before the command handler.</span></span>

![Конвейер команды также может обрабатываться очередью сообщений высокой доступности для доставки команд соответствующему обработчику.](./media/image23.png)

<span data-ttu-id="d8b51-281">**Рис. 7-26**.</span><span class="sxs-lookup"><span data-stu-id="d8b51-281">**Figure 7-26**.</span></span> <span data-ttu-id="d8b51-282">Использование очередей сообщений (внепроцессное и внутрипроцессное взаимодействие) с командами CQRS</span><span class="sxs-lookup"><span data-stu-id="d8b51-282">Using message queues (out of process and inter-process communication) with CQRS commands</span></span>

<span data-ttu-id="d8b51-283">Использование очередей сообщений для принятия команд может еще более усложнить конвейер команд, так как вам может потребоваться разделить его на два процесса, связанных посредством внешней очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="d8b51-283">Using message queues to accept the commands can further complicate your command’s pipeline, because you will probably need to split the pipeline into two processes connected through the external message queue.</span></span> <span data-ttu-id="d8b51-284">Однако его следует использовать, если вам нужно повысить масштабируемость и производительность с помощью асинхронных сообщений.</span><span class="sxs-lookup"><span data-stu-id="d8b51-284">Still, it should be used if you need to have improved scalability and performance based on asynchronous messaging.</span></span> <span data-ttu-id="d8b51-285">Представьте, что в ситуации, продемонстрированной на рис. 7-26, контроллер просто отправляет сообщение команды в очередь и возвращает управление.</span><span class="sxs-lookup"><span data-stu-id="d8b51-285">Consider that in the case of Figure 7-26, the controller just posts the command message into the queue and returns.</span></span> <span data-ttu-id="d8b51-286">В этом случае обработчики команд обрабатывают сообщения в удобном для себя темпе.</span><span class="sxs-lookup"><span data-stu-id="d8b51-286">Then the command handlers process the messages at their own pace.</span></span> <span data-ttu-id="d8b51-287">Это важное преимущество очередей: очередь сообщений может служить буфером в случае, когда требуется высочайшая масштабируемость, например в сценариях с большим объемом входящих данных.</span><span class="sxs-lookup"><span data-stu-id="d8b51-287">That is a great benefit of queues: the message queue can act as a buffer in cases when hyper scalability is needed, such as for stocks or any other scenario with a high volume of ingress data.</span></span>

<span data-ttu-id="d8b51-288">Однако из-за асинхронного характера очередей сообщений необходимо продумать способ, который позволит сообщать клиентскому приложению об успешном или неудачном выполнении процесса команды.</span><span class="sxs-lookup"><span data-stu-id="d8b51-288">However, because of the asynchronous nature of message queues, you need to figure out how to communicate with the client application about the success or failure of the command’s process.</span></span> <span data-ttu-id="d8b51-289">Как правило, не следует использовать команды, выполняющиеся в автономном режиме.</span><span class="sxs-lookup"><span data-stu-id="d8b51-289">As a rule, you should never use “fire and forget” commands.</span></span> <span data-ttu-id="d8b51-290">Каждому бизнес-приложению требуется знать, была ли команда обработана успешно или по крайней мере была ли она проверена и принята.</span><span class="sxs-lookup"><span data-stu-id="d8b51-290">Every business application needs to know if a command was processed successfully, or at least validated and accepted.</span></span>

<span data-ttu-id="d8b51-291">Таки образом, возможность предоставления ответа клиенту после проверки сообщения команды, отправленного в асинхронную очередь, повышает сложность системы по сравнению с внутрипроцессной обработкой команды, при которой результат операции возвращается после выполнения транзакции.</span><span class="sxs-lookup"><span data-stu-id="d8b51-291">Thus, being able to respond to the client after validating a command message that was submitted to an asynchronous queue adds complexity to your system, as compared to an in-process command process that returns the operation’s result after running the transaction.</span></span> <span data-ttu-id="d8b51-292">При использовании очередей может требоваться возвращать результат обработки команды посредством других сообщений о результате операции, для чего в системе необходимы дополнительные компоненты и пользовательские сообщения.</span><span class="sxs-lookup"><span data-stu-id="d8b51-292">Using queues, you might need to return the result of the command process through other operation result messages, which will require additional components and custom communication in your system.</span></span>

<span data-ttu-id="d8b51-293">Кроме того, асинхронные команды являются односторонними, что во многих случаях не требуется. Об этом говорят Алексей Бурцев (Burtsev Alexey) и Грег Янг (Greg Young) в этой интересной [беседе в Интернете](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span><span class="sxs-lookup"><span data-stu-id="d8b51-293">Additionally, async commands are one-way commands, which in many cases might not be needed, as is explained in the following interesting exchange between Burtsev Alexey and Greg Young in an [online conversation](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span></span>

> <span data-ttu-id="d8b51-294">\[Алексей Бурцев\] Мне часто встречается код, в котором асинхронная обработка команд или односторонние сообщения команд используются без всякой причины (в нем не выполняются длительные операции или внешний асинхронный код; в нем даже не пересекаются границы приложения для использования шины сообщений).</span><span class="sxs-lookup"><span data-stu-id="d8b51-294">\[Burtsev Alexey\] I find lots of code where people use async command handling or one way command messaging without any reason to do so (they are not doing some long operation, they are not executing external async code, they do not even cross application boundary to be using message bus).</span></span> <span data-ttu-id="d8b51-295">Зачем это излишнее усложнение?</span><span class="sxs-lookup"><span data-stu-id="d8b51-295">Why do they introduce this unnecessary complexity?</span></span> <span data-ttu-id="d8b51-296">В действительности мне еще не встречался пример кода CQRS с блокирующими обработчиками команд, хотя в большинстве случаев они вполне применимы.</span><span class="sxs-lookup"><span data-stu-id="d8b51-296">And actually, I haven't seen a CQRS code example with blocking command handlers so far, though it will work just fine in most cases.</span></span>
>
> <span data-ttu-id="d8b51-297">\[Грег Янг\] \[...\] асинхронных команд не существует; они по сути являются событиями.</span><span class="sxs-lookup"><span data-stu-id="d8b51-297">\[Greg Young\] \[...\] an asynchronous command doesn't exist; it's actually another event.</span></span> <span data-ttu-id="d8b51-298">Если я должен принять то, что вы мне отправили, и породить событие в случае несогласия, значит, вы уже не указываете, что мне нужно что-то сделать \[то есть, это не команда\].</span><span class="sxs-lookup"><span data-stu-id="d8b51-298">If I must accept what you send me and raise an event if I disagree, it's no longer you telling me to do something \[that is, it’s not a command\].</span></span> <span data-ttu-id="d8b51-299">Вы сообщаете мне, что что-то было сделано.</span><span class="sxs-lookup"><span data-stu-id="d8b51-299">It's you telling me something has been done.</span></span> <span data-ttu-id="d8b51-300">Сначала разница кажется небольшой, но она имеет множество последствий.</span><span class="sxs-lookup"><span data-stu-id="d8b51-300">This seems like a slight difference at first, but it has many implications.</span></span>

<span data-ttu-id="d8b51-301">Асинхронные команды значительно повышают сложность системы, так как нет простого способа сообщать о сбоях.</span><span class="sxs-lookup"><span data-stu-id="d8b51-301">Asynchronous commands greatly increase the complexity of a system, because there is no simple way to indicate failures.</span></span> <span data-ttu-id="d8b51-302">Поэтому асинхронные команды рекомендуются только при высоких требованиях к масштабируемости или в особых случаях, когда взаимодействие с внутренними микрослужбами осуществляется посредством сообщений.</span><span class="sxs-lookup"><span data-stu-id="d8b51-302">Therefore, asynchronous commands are not recommended other than when scaling requirements are needed or in special cases when communicating the internal microservices through messaging.</span></span> <span data-ttu-id="d8b51-303">В этих ситуациях необходимо спроектировать отдельную систему для информирования о сбоях и восстановления.</span><span class="sxs-lookup"><span data-stu-id="d8b51-303">In those cases, you must design a separate reporting and recovery system for failures.</span></span>

<span data-ttu-id="d8b51-304">В первоначальной версии eShopOnContainers было решено использовать синхронную обработку команд, начиная с HTTP-запросов, на основе шаблона медиатора.</span><span class="sxs-lookup"><span data-stu-id="d8b51-304">In the initial version of eShopOnContainers, we decided to use synchronous command processing, started from HTTP requests and driven by the Mediator pattern.</span></span> <span data-ttu-id="d8b51-305">Это позволяет легко возвращать результат процесса (успех или неудача), как в реализации [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs).</span><span class="sxs-lookup"><span data-stu-id="d8b51-305">That easily allows you to return the success or failure of the process, as in the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementation.</span></span>

<span data-ttu-id="d8b51-306">В любом случае решение должно приниматься на основе бизнес-требований к приложению или микрослужбе.</span><span class="sxs-lookup"><span data-stu-id="d8b51-306">In any case, this should be a decision based on your application’s or microservice’s business requirements.</span></span>

## <a name="implement-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a><span data-ttu-id="d8b51-307">Реализация конвейера обработки команд с помощью шаблона медиатора (MediatR)</span><span class="sxs-lookup"><span data-stu-id="d8b51-307">Implement the command process pipeline with a mediator pattern (MediatR)</span></span>

<span data-ttu-id="d8b51-308">В качестве примера реализации в этом руководстве используется внутрипроцессный конвейер на основе шаблона медиатора, обеспечивающий прием команд и их маршрутизацию в памяти в соответствующие обработчики команд.</span><span class="sxs-lookup"><span data-stu-id="d8b51-308">As a sample implementation, this guide proposes using the in-process pipeline based on the Mediator pattern to drive command ingestion and route commands, in memory, to the right command handlers.</span></span> <span data-ttu-id="d8b51-309">В руководстве также предлагается применять [расширения функциональности](https://github.com/jbogard/MediatR/wiki/Behaviors) для разделения сквозной функциональности.</span><span class="sxs-lookup"><span data-stu-id="d8b51-309">The guide also proposes applying [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) in order to separate cross-cutting concerns.</span></span>

<span data-ttu-id="d8b51-310">Для реализации в .NET Core доступно множество библиотек с открытым кодом, которые реализуют шаблон медиатора.</span><span class="sxs-lookup"><span data-stu-id="d8b51-310">For implementation in .NET Core, there are multiple open-source libraries available that implement the Mediator pattern.</span></span> <span data-ttu-id="d8b51-311">В этом руководстве применяется библиотека [MediatR](https://github.com/jbogard/MediatR) с открытым кодом (созданная Джимми Богардом (Jimmy Bogard)), но можно выбрать и другой подход.</span><span class="sxs-lookup"><span data-stu-id="d8b51-311">The library used in this guide is the [MediatR](https://github.com/jbogard/MediatR) open-source library (created by Jimmy Bogard), but you could use another approach.</span></span> <span data-ttu-id="d8b51-312">MediatR — это небольшая простая библиотека, которая позволяет обрабатывать сообщения в памяти как команды, применяя декораторы или расширения функциональности.</span><span class="sxs-lookup"><span data-stu-id="d8b51-312">MediatR is a small and simple library that allows you to process in-memory messages like a command, while applying decorators or behaviors.</span></span>

<span data-ttu-id="d8b51-313">Использование шаблона медиатора помогает уменьшить количество связей и изолировать функциональность, связанную с запрашиваемой работой. При этом вы можете автоматически подключаться к обработчику, который выполняет эту работу — в данном случае к обработчику команд.</span><span class="sxs-lookup"><span data-stu-id="d8b51-313">Using the Mediator pattern helps you to reduce coupling and to isolate the concerns of the requested work, while automatically connecting to the handler that performs that work—in this case, to command handlers.</span></span>

<span data-ttu-id="d8b51-314">Еще одна причина для использования шаблона медиатора была раскрыта Джимми Богардом при рецензировании этого руководства:</span><span class="sxs-lookup"><span data-stu-id="d8b51-314">Another good reason to use the Mediator pattern was explained by Jimmy Bogard when reviewing this guide:</span></span>

> <span data-ttu-id="d8b51-315">"Я думаю, здесь стоит упомянуть тестирование — вы получаете ясное и согласованное представление о поведении системы".</span><span class="sxs-lookup"><span data-stu-id="d8b51-315">I think it might be worth mentioning testing here – it provides a nice consistent window into the behavior of your system.</span></span> <span data-ttu-id="d8b51-316">Запрос поступает, ответ выдается — этот принцип оказался очень полезным при разработке согласованно работающих тестов.</span><span class="sxs-lookup"><span data-stu-id="d8b51-316">Request-in, response-out. We’ve found that aspect quite valuable in building consistently behaving tests.</span></span>

<span data-ttu-id="d8b51-317">Сначала рассмотрим пример контроллера WebAPI, в котором будет использоваться объект медиатора.</span><span class="sxs-lookup"><span data-stu-id="d8b51-317">First, let’s look at a sample WebAPI controller where you actually would use the mediator object.</span></span> <span data-ttu-id="d8b51-318">Если бы объект медиатора не применялся, потребовалось бы внедрить все зависимости для контроллера, такие как средство ведения журнала и другие.</span><span class="sxs-lookup"><span data-stu-id="d8b51-318">If you were not using the mediator object, you would need to inject all the dependencies for that controller, things like a logger object and others.</span></span> <span data-ttu-id="d8b51-319">Поэтому конструктор был бы весьма сложным.</span><span class="sxs-lookup"><span data-stu-id="d8b51-319">Therefore, the constructor would be quite complicated.</span></span> <span data-ttu-id="d8b51-320">Если же вы используете объект медиатора, конструктор контроллера может быть гораздо проще. Он может иметь всего лишь несколько зависимостей вместо множества, как в случае, когда для каждой сквозной операции имеется отдельная зависимость. Это показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="d8b51-320">On the other hand, if you use the mediator object, the constructor of your controller can be a lot simpler, with just a few dependencies instead of many dependencies if you had one per cross-cutting operation, as in the following example:</span></span>

```csharp
public class MyMicroserviceController : Controller
{
    public MyMicroserviceController(IMediator mediator,
                                    IMyMicroserviceQueries microserviceQueries)
    // ...
```

<span data-ttu-id="d8b51-321">Как можно видеть, медиатор обеспечивает простой контроллер веб-интерфейса API, в котором нет ничего лишнего.</span><span class="sxs-lookup"><span data-stu-id="d8b51-321">You can see that the mediator provides a clean and lean Web API controller constructor.</span></span> <span data-ttu-id="d8b51-322">Кроме того, в методах контроллера код для отправки команды объекту медиатора ограничивается практически одной строкой:</span><span class="sxs-lookup"><span data-stu-id="d8b51-322">In addition, within the controller methods, the code to send a command to the mediator object is almost one line:</span></span>

```csharp
[Route("new")]
[HttpPost]
public async Task<IActionResult> ExecuteBusinessOperation([FromBody]RunOpCommand
                                                               runOperationCommand)
{
    var commandResult = await _mediator.SendAsync(runOperationCommand);

    return commandResult ? (IActionResult)Ok() : (IActionResult)BadRequest();
}
```

### <a name="implement-idempotent-commands"></a><span data-ttu-id="d8b51-323">Реализация идемпотентных команд</span><span class="sxs-lookup"><span data-stu-id="d8b51-323">Implement idempotent Commands</span></span>

<span data-ttu-id="d8b51-324">Более сложным примером по сравнению с приведенным выше в приложении **eShopOnContainers** является отправка объекта CreateOrderCommand из микрослужбы размещения заказов.</span><span class="sxs-lookup"><span data-stu-id="d8b51-324">In **eShopOnContainers**, a more advanced example than the above is submitting a CreateOrderCommand object from the Ordering microservice.</span></span> <span data-ttu-id="d8b51-325">Однако поскольку бизнес-процесс размещения заказов является немного более сложным и в данном случае он фактически начинается в микрослужбе Basket, действие отправки объекта CreateOrderCommand выполняется из обработчика событий интеграции с именем >UserCheckoutAcceptedIntegrationEvent.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs), а не из простого контроллера WebAPI, вызываемого из клиентского приложения, как в предыдущем более простом примере.</span><span class="sxs-lookup"><span data-stu-id="d8b51-325">But since the Ordering business process is a bit more complex and, in our case, it actually starts in the Basket microservice, this action of submitting the CreateOrderCommand object is performed from an integration-event handler named >UserCheckoutAcceptedIntegrationEvent.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) instead of a simple WebAPI controller called from the client App as in the previous simpler example.</span></span>

<span data-ttu-id="d8b51-326">Тем не менее действие отправки команды в MediatR по многом схоже, как показано в приведенном ниже коде.</span><span class="sxs-lookup"><span data-stu-id="d8b51-326">Nevertheless, the action of submitting the Command to MediatR is pretty similar, as shown in the following code.</span></span>

```csharp
var createOrderCommand = new CreateOrderCommand(eventMsg.Basket.Items,
                                                eventMsg.UserId, eventMsg.City,
                                                eventMsg.Street, eventMsg.State,
                                                eventMsg.Country, eventMsg.ZipCode,
                                                eventMsg.CardNumber,
                                                eventMsg.CardHolderName,
                                                eventMsg.CardExpiration,
                                                eventMsg.CardSecurityNumber,
                                                eventMsg.CardTypeId);

var requestCreateOrder = new IdentifiedCommand<CreateOrderCommand,bool>(createOrderCommand,
                                                                        eventMsg.RequestId);
result = await _mediator.Send(requestCreateOrder);
```

<span data-ttu-id="d8b51-327">Этот случай также немного сложнее, так как мы реализуем идемпотентные команды.</span><span class="sxs-lookup"><span data-stu-id="d8b51-327">However, this case is also a little bit more advanced because we’re also implementing idempotent commands.</span></span> <span data-ttu-id="d8b51-328">Процесс CreateOrderCommand должен быть идемпотентным, чтобы в случае повторной передачи по сети одного и того же сообщения по какой-либо причине, например из-за выполнения повторных попыток, заказ обрабатывался бы только один раз.</span><span class="sxs-lookup"><span data-stu-id="d8b51-328">The CreateOrderCommand process should be idempotent, so if the same message comes duplicated through the network, because of any reason, like retries, the same business order will be processed just once.</span></span>

<span data-ttu-id="d8b51-329">Для этого бизнес-команда (в данном случае CreateOrderCommand) упаковывается и внедряется в универсальный класс IdentifiedCommand, отслеживаемый по идентификатору каждого поступающего по сети сообщения, которое должно быть идемпотентным.</span><span class="sxs-lookup"><span data-stu-id="d8b51-329">This is implemented by wrapping the business command (in this case CreateOrderCommand) and embedding it into a generic IdentifiedCommand which is tracked by an ID of every message coming through the network that has to be idempotent.</span></span>

<span data-ttu-id="d8b51-330">В приведенном ниже коде видно, что IdentifiedCommand — это просто объект DTO с идентификатором и объектом упакованной бизнес-команды.</span><span class="sxs-lookup"><span data-stu-id="d8b51-330">In the code below, you can see that the IdentifiedCommand is nothing more than a DTO with and ID plus the wrapped business command object.</span></span>

```csharp
public class IdentifiedCommand<T, R> : IRequest<R>
    where T : IRequest<R>
{
    public T Command { get; }
    public Guid Id { get; }
    public IdentifiedCommand(T command, Guid id)
    {
        Command = command;
        Id = id;
    }
}
```

<span data-ttu-id="d8b51-331">Затем обработчик CommandHandler для IdentifiedCommand с именем [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) проверяет, имеется ли уже идентификатор, полученный в сообщении, в таблице.</span><span class="sxs-lookup"><span data-stu-id="d8b51-331">Then the CommandHandler for the IdentifiedCommand named [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) will basically check if the ID coming as part of the message already exists in a table.</span></span> <span data-ttu-id="d8b51-332">Если он имеется, команда не будет обработана повторно, то есть она является идемпотентной.</span><span class="sxs-lookup"><span data-stu-id="d8b51-332">If it already exists, that command won’t be processed again, so it behaves as an idempotent command.</span></span> <span data-ttu-id="d8b51-333">Этот код инфраструктуры выполняется в результате вызова метода `_requestManager.ExistAsync`, приведенного ниже.</span><span class="sxs-lookup"><span data-stu-id="d8b51-333">That infrastructure code is performed by the `_requestManager.ExistAsync` method call below.</span></span>

```csharp
// IdentifiedCommandHandler.cs
public class IdentifiedCommandHandler<T, R> :
                                   IAsyncRequestHandler<IdentifiedCommand<T, R>, R>
                                   where T : IRequest<R>
{
    private readonly IMediator _mediator;
    private readonly IRequestManager _requestManager;

    public IdentifiedCommandHandler(IMediator mediator,
                                    IRequestManager requestManager)
    {
        _mediator = mediator;
        _requestManager = requestManager;
    }

    protected virtual R CreateResultForDuplicateRequest()
    {
        return default(R);
    }

    public async Task<R> Handle(IdentifiedCommand<T, R> message)
    {
        var alreadyExists = await _requestManager.ExistAsync(message.Id);
        if (alreadyExists)
        {
            return CreateResultForDuplicateRequest();
        }
        else
        {
            await _requestManager.CreateRequestForCommandAsync<T>(message.Id);

            // Send the embedded business command to mediator
            // so it runs its related CommandHandler
            var result = await _mediator.Send(message.Command);

            return result;
        }
    }
}
```

<span data-ttu-id="d8b51-334">Объект IdentifiedCommand выступает в роли конверта для бизнес-команды, поэтому когда бизнес-команда должна быть обработана в случае, если идентификатор не повторяется, этот объект берет внутреннюю бизнес-команду и повторно передает ее в медиатор. Это продемонстрировано в последней части приведенного выше кода, в которой выполняется метод `_mediator.Send(message.Command)` из [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span><span class="sxs-lookup"><span data-stu-id="d8b51-334">Since the IdentifiedCommand acts like a business command’s envelope, when the business command needs to be processed because it is not a repeated Id, then it takes that inner business command and re-submits it to Mediator, as in the last part of the code shown above when running `_mediator.Send(message.Command)`, from the [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span></span>

<span data-ttu-id="d8b51-335">При этом выполняется связывание с обработчиком бизнес-команд и его запуск. В данном случае это обработчик [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs), который выполняет транзакции в базе данных Ordering, как показано в приведенном ниже коде.</span><span class="sxs-lookup"><span data-stu-id="d8b51-335">When doing that, it will link and run the business command handler, in this case, the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) which is running transactions against the Ordering database, as shown in the following code.</span></span>

```csharp
// CreateOrderCommandHandler.cs
public class CreateOrderCommandHandler
                                   : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Add/Update the Buyer AggregateRoot
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

### <a name="register-the-types-used-by-mediatr"></a><span data-ttu-id="d8b51-336">Регистрация типов, используемых библиотекой MediatR</span><span class="sxs-lookup"><span data-stu-id="d8b51-336">Register the types used by MediatR</span></span>

<span data-ttu-id="d8b51-337">Чтобы сообщить библиотеке MediatR об используемых классах обработчиков команд, необходимо зарегистрировать классы медиаторов и обработчиков команд в контейнере IoC.</span><span class="sxs-lookup"><span data-stu-id="d8b51-337">In order for MediatR to be aware of your command handler classes, you need to register the mediator classes and the command handler classes in your IoC container.</span></span> <span data-ttu-id="d8b51-338">По умолчанию библиотека MediatR использует Autofac в качестве контейнера IoC, но вы также можете использовать встроенный контейнер IoC в ASP.NET Core или любой другой контейнер, поддерживаемый MediatR.</span><span class="sxs-lookup"><span data-stu-id="d8b51-338">By default, MediatR uses Autofac as the IoC container, but you can also use the built-in ASP.NET Core IoC container or any other container supported by MediatR.</span></span>

<span data-ttu-id="d8b51-339">В приведенном ниже коде показано, как зарегистрировать типы и команды Mediator при использовании модулей Autofac.</span><span class="sxs-lookup"><span data-stu-id="d8b51-339">The following code shows how to register Mediator’s types and commands when using Autofac modules.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IAsyncRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IAsyncRequestHandler<,>));
        // Other types registration
        //...
    }
}
```

<span data-ttu-id="d8b51-340">Именно в нем творится вся магия MediatR.</span><span class="sxs-lookup"><span data-stu-id="d8b51-340">This is where “the magic happens” with MediatR.</span></span>

<span data-ttu-id="d8b51-341">Так как каждый обработчик команд реализует универсальный интерфейс `IAsyncRequestHandler<T>`, при регистрации сборок код регистрирует в `RegisteredAssemblyTypes` все типы, помеченные как `IAsyncRequestHandler`. При этом он связывает обработчики `CommandHandlers` с `Commands` посредством отношения, определенного в классе `CommandHandler`, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="d8b51-341">Because each command handler implements the generic `IAsyncRequestHandler<T>` interface, when registering the assemblies, the code registers with `RegisteredAssemblyTypes` all the types marked as `IAsyncRequestHandler` while relating the `CommandHandlers` with their `Commands`, thanks to the relationship stated at the `CommandHandler` class, as in the following example:</span></span>

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

<span data-ttu-id="d8b51-342">Этот код сопоставляет команды с обработчиками команд.</span><span class="sxs-lookup"><span data-stu-id="d8b51-342">That is the code that correlates commands with command handlers.</span></span> <span data-ttu-id="d8b51-343">Обработчик представляет собой простой класс, но он наследуется от `RequestHandler<T>`, где T обозначает тип команды, и библиотека MediatR обеспечивает его вызов с надлежащими полезными данными (командой).</span><span class="sxs-lookup"><span data-stu-id="d8b51-343">The handler is just a simple class, but it inherits from `RequestHandler<T>`, where T is the command type, and MediatR makes sure it is invoked with the correct payload (the command).</span></span>

## <a name="apply-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-mediatr"></a><span data-ttu-id="d8b51-344">Применение сквозной функциональности при обработке команд с помощью расширений функциональности в MediatR</span><span class="sxs-lookup"><span data-stu-id="d8b51-344">Apply cross-cutting concerns when processing commands with the Behaviors in MediatR</span></span>

<span data-ttu-id="d8b51-345">Есть еще одна возможность: применение сквозной функциональности к конвейеру медиатора.</span><span class="sxs-lookup"><span data-stu-id="d8b51-345">There is one more thing: being able to apply cross-cutting concerns to the mediator pipeline.</span></span> <span data-ttu-id="d8b51-346">В конце кода модуля регистрации Autofac можно заметить, что он регистрирует тип расширения функциональности, а именно: пользовательский класс LoggingBehavior и класс ValidatorBehavior.</span><span class="sxs-lookup"><span data-stu-id="d8b51-346">You can also see at the end of the Autofac registration module code how it registers a behavior type, specifically, a custom LoggingBehavior class and a ValidatorBehavior class.</span></span> <span data-ttu-id="d8b51-347">Вы также можете добавить другие пользовательские расширения функциональности.</span><span class="sxs-lookup"><span data-stu-id="d8b51-347">But you could add other custom behaviors, too.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IAsyncRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IAsyncRequestHandler<,>));
        // Other types registration
        //...
        builder.RegisterGeneric(typeof(LoggingBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
        builder.RegisterGeneric(typeof(ValidatorBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
    }
}
```

<span data-ttu-id="d8b51-348">Класс [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) может быть реализован в виде приведенного ниже кода, который записывает в журнал сведения о выполняемом обработчике команд и результате его выполнения (успех или неудача).</span><span class="sxs-lookup"><span data-stu-id="d8b51-348">That [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class can be implemented as the following code, which logs information about the command handler being executed and whether it was successful or not.</span></span>

```csharp
public class LoggingBehavior<TRequest, TResponse>
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly ILogger<LoggingBehavior<TRequest, TResponse>> _logger;
    public LoggingBehavior(ILogger<LoggingBehavior<TRequest, TResponse>> logger) =>
                                                                  _logger = logger;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        _logger.LogInformation($"Handling {typeof(TRequest).Name}");
        var response = await next();
        _logger.LogInformation($"Handled {typeof(TResponse).Name}");
        return response;
    }
}
```

<span data-ttu-id="d8b51-349">Если реализовать этот класс расширения функциональности и зарегистрировать его в конвейере (в MediatorModule в примере выше), в журнал будут записываться сведения о выполнении всех команд, обрабатываемых посредством MediatR.</span><span class="sxs-lookup"><span data-stu-id="d8b51-349">Just by implementing this behavior class and by registering it in the pipeline (in the MediatorModule above), all the commands processed through MediatR will be logging information about the execution.</span></span>

<span data-ttu-id="d8b51-350">В микрослужбе размещения заказов eShopOnContainers применяется еще одно расширение функциональности для проведения базовых проверок. Это класс [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs), основанный на библиотеке [FluentValidation](https://github.com/JeremySkinner/FluentValidation) и показанный в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="d8b51-350">The eShopOnContainers ordering microservice also applies a second behavior for basic validations, the [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class that relies on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, as shown in the following code:</span></span>

```csharp
public class ValidatorBehavior<TRequest, TResponse>
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly IValidator<TRequest>[] _validators;
    public ValidatorBehavior(IValidator<TRequest>[] validators) =>
                                                         _validators = validators;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        var failures = _validators
            .Select(v => v.Validate(request))
            .SelectMany(result => result.Errors)
            .Where(error => error != null)
            .ToList();

        if (failures.Any())
        {
            throw new OrderingDomainException(
                $"Command Validation Errors for type {typeof(TRequest).Name}",
                        new ValidationException("Validation exception", failures));
        }

        var response = await next();
        return response;
    }
}
```

<span data-ttu-id="d8b51-351">Здесь расширение функциональности вызывает исключение при сбое проверки, но вы также можете возвращать результирующий объект, содержащий результат команды в случае успеха или сообщение проверки в случае сбоя.</span><span class="sxs-lookup"><span data-stu-id="d8b51-351">The behavior here is raising an exception if validation fails, but you could also return a result object, containing the command result if it succeeded or the validation messages in case it didn’t.</span></span> <span data-ttu-id="d8b51-352">Возможно, это упростит отображение результатов проверки для пользователя.</span><span class="sxs-lookup"><span data-stu-id="d8b51-352">This would probably make it easier to display validation results to the user.</span></span>

<span data-ttu-id="d8b51-353">Затем на основе [FluentValidation](https://github.com/JeremySkinner/FluentValidation) была реализована проверка данных, передаваемых с помощью команды CreateOrderCommand, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="d8b51-353">Then, based on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, we created validation for the data passed with CreateOrderCommand, as in the following code:</span></span>

```csharp
public class CreateOrderCommandValidator : AbstractValidator<CreateOrderCommand>
{
    public CreateOrderCommandValidator()
    {
        RuleFor(command => command.City).NotEmpty();
        RuleFor(command => command.Street).NotEmpty();
        RuleFor(command => command.State).NotEmpty();
        RuleFor(command => command.Country).NotEmpty();
        RuleFor(command => command.ZipCode).NotEmpty();
        RuleFor(command => command.CardNumber).NotEmpty().Length(12, 19);
        RuleFor(command => command.CardHolderName).NotEmpty();
        RuleFor(command => command.CardExpiration).NotEmpty().Must(BeValidExpirationDate).WithMessage("Please specify a valid card expiration date");
        RuleFor(command => command.CardSecurityNumber).NotEmpty().Length(3);
        RuleFor(command => command.CardTypeId).NotEmpty();
        RuleFor(command => command.OrderItems).Must(ContainOrderItems).WithMessage("No order items found");
    }

    private bool BeValidExpirationDate(DateTime dateTime)
    {
        return dateTime >= DateTime.UtcNow;
    }

    private bool ContainOrderItems(IEnumerable<OrderItemDTO> orderItems)
    {
        return orderItems.Any();
    }
}

```

<span data-ttu-id="d8b51-354">Можно создать дополнительные проверки.</span><span class="sxs-lookup"><span data-stu-id="d8b51-354">You could create additional validations.</span></span> <span data-ttu-id="d8b51-355">Это очень простой и изящный способ реализации проверок команд.</span><span class="sxs-lookup"><span data-stu-id="d8b51-355">This is a very clean and elegant way to implement your command validations.</span></span>

<span data-ttu-id="d8b51-356">Аналогичным образом можно реализовать дополнительные расширения функциональности для других аспектов или сквозной функциональности, которые требуется применять к командам во время их обработки.</span><span class="sxs-lookup"><span data-stu-id="d8b51-356">In a similar way, you could implement other behaviors for additional aspects or cross-cutting concerns that you want to apply to commands when handling them.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="d8b51-357">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="d8b51-357">Additional resources</span></span>

##### <a name="the-mediator-pattern"></a><span data-ttu-id="d8b51-358">Шаблон медиатора</span><span class="sxs-lookup"><span data-stu-id="d8b51-358">The mediator pattern</span></span>

- <span data-ttu-id="d8b51-359">**Шаблон медиатора** \\</span><span class="sxs-lookup"><span data-stu-id="d8b51-359">**Mediator pattern** \\</span></span>
  [https://en.wikipedia.org/wiki/Mediator\_pattern](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a><span data-ttu-id="d8b51-360">Шаблон декоратора</span><span class="sxs-lookup"><span data-stu-id="d8b51-360">The decorator pattern</span></span>

- <span data-ttu-id="d8b51-361">**Шаблон декоратора** \\</span><span class="sxs-lookup"><span data-stu-id="d8b51-361">**Decorator pattern** \\</span></span>
  [https://en.wikipedia.org/wiki/Decorator\_pattern](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a><span data-ttu-id="d8b51-362">MediatR (Джимми Богард (Jimmy Bogard))</span><span class="sxs-lookup"><span data-stu-id="d8b51-362">MediatR (Jimmy Bogard)</span></span>

- <span data-ttu-id="d8b51-363">**MediatR.**</span><span class="sxs-lookup"><span data-stu-id="d8b51-363">**MediatR.**</span></span> <span data-ttu-id="d8b51-364">Репозиторий GitHub.</span><span class="sxs-lookup"><span data-stu-id="d8b51-364">GitHub repo.</span></span> \
  <https://github.com/jbogard/MediatR>

- <span data-ttu-id="d8b51-365">**CQRS с MediatR и AutoMapper** \\</span><span class="sxs-lookup"><span data-stu-id="d8b51-365">**CQRS with MediatR and AutoMapper** \\</span></span>
  <https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/>

- <span data-ttu-id="d8b51-366">**Сажаем контроллеры на диету: запросы POST и команды**.</span><span class="sxs-lookup"><span data-stu-id="d8b51-366">**Put your controllers on a diet: POSTs and commands.**</span></span> \
  <https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/>

- <span data-ttu-id="d8b51-367">**Обеспечение сквозной функциональности с помощью конвейера медиатора** \\</span><span class="sxs-lookup"><span data-stu-id="d8b51-367">**Tackling cross-cutting concerns with a mediator pipeline** \\</span></span>
  <https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/>

- <span data-ttu-id="d8b51-368">**CQRS и REST: идеальная пара** \\</span><span class="sxs-lookup"><span data-stu-id="d8b51-368">**CQRS and REST: the perfect match** \\</span></span>
  <https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/>

- <span data-ttu-id="d8b51-369">**Примеры конвейера MediatR** \\</span><span class="sxs-lookup"><span data-stu-id="d8b51-369">**MediatR Pipeline Examples** \\</span></span>
  <https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/>

- <span data-ttu-id="d8b51-370">**Средства тестирования вертикальных срезов для MediatR и ASP.NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="d8b51-370">**Vertical Slice Test Fixtures for MediatR and ASP.NET Core** \\</span></span>
  <https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>

- <span data-ttu-id="d8b51-371">**Объявление о выпуске расширений MediatR для внедрения зависимостей Майкрософт** \\</span><span class="sxs-lookup"><span data-stu-id="d8b51-371">**MediatR Extensions for Microsoft Dependency Injection Released** \\</span></span>
  <https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/>

##### <a name="fluent-validation"></a><span data-ttu-id="d8b51-372">Плавная проверка</span><span class="sxs-lookup"><span data-stu-id="d8b51-372">Fluent validation</span></span>

- <span data-ttu-id="d8b51-373">**Джереми Скиннер (Jeremy Skinner). FluentValidation.**</span><span class="sxs-lookup"><span data-stu-id="d8b51-373">**Jeremy Skinner. FluentValidation.**</span></span> <span data-ttu-id="d8b51-374">Репозиторий GitHub.</span><span class="sxs-lookup"><span data-stu-id="d8b51-374">GitHub repo.</span></span> \
  <https://github.com/JeremySkinner/FluentValidation>

> [!div class="step-by-step"]
> <span data-ttu-id="d8b51-375">[Назад](microservice-application-layer-web-api-design.md)
> [Вперед](../implement-resilient-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="d8b51-375">[Previous](microservice-application-layer-web-api-design.md)
[Next](../implement-resilient-applications/index.md)</span></span>
