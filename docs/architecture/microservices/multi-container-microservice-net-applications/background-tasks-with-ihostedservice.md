---
title: Реализация фоновых задач в микрослужбах с помощью IHostedService и класса BackgroundService
description: Архитектура микрослужб .NET для упакованных в контейнеры приложений .NET | Новые варианты использования IHostedService и BackgroundService для реализации фоновых задач в микрослужбах .NET Core.
ms.date: 08/14/2020
ms.openlocfilehash: 279f9e0093deafab51e63d72dce233c8e9466a55
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173358"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a>Реализация фоновых задач в микрослужбах с помощью IHostedService и класса BackgroundService

Фоновые задачи и запланированные задания обычно требуется использовать в любом приложении независимо от того, строится ли оно на основе архитектуры микрослужб. Разница при использовании архитектуры микрослужб в том, что вы можете реализовать фоновую задачу в отдельном процессе или контейнере, чтобы затем масштабировать его по мере необходимости.

Если посмотреть шире, в .NET Core такие задачи называются *размещенными службами*, так как они представляют собой службы или логику, размещаемые в узле, приложении или микрослужбе. Обратите внимание на то, что в этом случае под размещенной службой понимается просто класс с логикой фоновой задачи.

Начиная с версии .NET Core 2.0, платформа предоставляет новый интерфейс <xref:Microsoft.Extensions.Hosting.IHostedService>, который позволяет легко реализовывать размещенные службы. Главная идея заключается в том, что вы можете регистрировать несколько фоновых задач (размещенных служб), которые выполняются в фоновом режиме в процессе работы веб-узла или обычного узла, как показано на рис. 6-26.

![Схема сравнения IWebHost в ASP.NET Core и IHost в .NET Core.](./media/background-tasks-with-ihostedservice/ihosted-service-webhost-vs-host.png)

**Рис. 6-26**. Использование интерфейса IHostedService в классах WebHost и Host

ASP.NET Core версий 1.x и 2.x поддерживает `IWebHost` для фоновых процессов в веб-приложениях. .NET Core 2.1 и более поздних версий поддерживает `IHost` для фоновых процессов с простыми консольными приложениями. Обратите внимание на различие между `WebHost` и `Host`.

`WebHost` (базовый класс, реализующий интерфейс `IWebHost`) в ASP.NET Core 2.0 — это артефакт инфраструктуры, с помощью которого процесс получает доступ к возможностям сервера HTTP, например при реализации веб-приложения MVC или службы веб-интерфейса API. Он предоставляет все новые преимущества инфраструктуры в ASP.NET Core, позволяя использовать внедрение зависимостей, вставлять промежуточные слои в конвейер запросов и т. д. `WebHost` использует те же `IHostedServices` для фоновых задач.

Объект `Host` (базовый класс, реализующий `IHost`) впервые появился в .NET Core 2.1. По существу, класс `Host` обеспечивает практически такую же инфраструктуру, что и класс `WebHost` (внедрение зависимостей, размещенные службы и т. д.), но в этом случае узел должен представлять собой более простой процесс без связанных с MVC веб-интерфейсами API или сервером HTTP возможностей.

Таким образом, вы можете либо создать специальный хост-процесс с помощью `IHost` для реализации только размещенных служб, например микрослужбу, предназначенную для размещения `IHostedServices`, либо расширить существующий в ASP.NET Core класс `WebHost`, например существующий веб-интерфейс API ASP.NET Core или приложение MVC.

Каждый подход имеет свои преимущества и недостатки в зависимости от потребностей бизнеса и требований к масштабируемости. Основной принцип заключается в том, что если фоновые задачи не связаны с HTTP (`IWebHost`), следует использовать интерфейс `IHost`.

## <a name="registering-hosted-services-in-your-webhost-or-host"></a>Регистрация размещенных служб в WebHost или Host

Давайте более подробно разберем интерфейс `IHostedService`, так как его использование в классах `WebHost` и `Host` во многом схоже.

Библиотека SignalR — один из примеров артефактов, использующих размещенные службы, однако ее можно применять и для более простых задач, таких как следующие:

- фоновая задача опроса базы данных для поиска изменений;
- запланированная задача для периодического обновления кэша;
- реализация QueueBackgroundWorkItem, которая позволяет задаче выполняться в фоновом потоке;
- обработка сообщений из очереди сообщений веб-приложения в фоновом режиме при использовании общих служб, таких как `ILogger`;
- фоновая задача, запускаемая с помощью `Task.Run()`.

Выполнение любого из этих действий можно перенести в фоновую задачу, которая реализует `IHostedService`.

Для добавления одного или нескольких экземпляров `IHostedServices` в `WebHost` или `Host` их следует зарегистрировать посредством метода расширения <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> в классе ASP.NET Core `WebHost` (или в классе `Host` в .NET Core 2.1 и более поздних версий). Фактически размещенные службы регистрируются в известном методе `ConfigureServices()` класса `Startup`, как в следующем коде типичного класса ASP.NET WebHost:

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    //Other DI registrations;

    // Register Hosted Services
    services.AddHostedService<GracePeriodManagerService>();
    services.AddHostedService<MyHostedServiceB>();
    services.AddHostedService<MyHostedServiceC>();
    //...
}
```

В этом коде размещенная служба `GracePeriodManagerService` представляет собой реальный код микрослужбы размещения заказов в приложении eShopOnContainers, а другие две службы — это просто дополнительные примеры.

Выполнение фоновой задачи `IHostedService` согласуется с временем существования приложения (узла или микрослужбы). Задачи регистрируются при запуске приложения, а при завершении его работы есть возможность произвести надлежащую обработку или очистку.

Фоновый поток можно запускать для выполнения любой задачи и без использования `IHostedService`. Различие именно в том, что будет происходить при завершении работы приложения: поток будет просто завершаться без возможности надлежащей очистки.

## <a name="the-ihostedservice-interface"></a>Интерфейс IHostedService

При регистрации интерфейса `IHostedService` платформа .NET Core вызывает методы `StartAsync()` и `StopAsync()` типа `IHostedService` во время запуска и остановки приложения соответственно. Дополнительные сведения см. в разделе [Интерфейс IHostedService](/aspnet/core/fundamentals/host/hosted-services?tabs=visual-studio&view=aspnetcore-3.1#ihostedservice-interface).

Как было показано ранее, вы можете создать несколько реализаций IHostedService и зарегистрировать их в методе `ConfigureService()` в контейнере внедрения зависимостей. Все эти размещенные службы будут запускаться и останавливаться вместе с приложением или микрослужбой.

Как разработчик, вы несете ответственность за обработку действия завершения своих служб при активации метода `StopAsync()` узлом.

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a>Реализация IHostedService с помощью пользовательского класса размещенной службы, производного от базового класса BackgroundService

Можно пойти дальше и создать пользовательский класс размещенной службы с нуля, реализовав интерфейс `IHostedService`, как это требуется делать в .NET Core 2.0.

Но большинство фоновых задач имеют схожие потребности в отношении управления токенами отмены и других типичных операций, поэтому существует удобный абстрактный базовый класс `BackgroundService`, от которого можно создавать производные классы (доступно с .NET Core 2.1).

Он будет выполнять основную часть работы, связанной с настройкой фоновой задачи.

Следующий код — это абстрактный базовый класс BackgroundService, реализованный в .NET Core.

```csharp
// Copyright (c) .NET Foundation. Licensed under the Apache License, Version 2.0.
/// <summary>
/// Base class for implementing a long running <see cref="IHostedService"/>.
/// </summary>
public abstract class BackgroundService : IHostedService, IDisposable
{
    private Task _executingTask;
    private readonly CancellationTokenSource _stoppingCts =
                                                   new CancellationTokenSource();

    protected abstract Task ExecuteAsync(CancellationToken stoppingToken);

    public virtual Task StartAsync(CancellationToken cancellationToken)
    {
        // Store the task we're executing
        _executingTask = ExecuteAsync(_stoppingCts.Token);

        // If the task is completed then return it,
        // this will bubble cancellation and failure to the caller
        if (_executingTask.IsCompleted)
        {
            return _executingTask;
        }

        // Otherwise it's running
        return Task.CompletedTask;
    }

    public virtual async Task StopAsync(CancellationToken cancellationToken)
    {
        // Stop called without start
        if (_executingTask == null)
        {
            return;
        }

        try
        {
            // Signal cancellation to the executing method
            _stoppingCts.Cancel();
        }
        finally
        {
            // Wait until the task completes or the stop token triggers
            await Task.WhenAny(_executingTask, Task.Delay(Timeout.Infinite,
                                                          cancellationToken));
        }

    }

    public virtual void Dispose()
    {
        _stoppingCts.Cancel();
    }
}
```

Благодаря такой унаследованной реализации при создании собственного класса размещенной службы, производного от приведенного выше абстрактного базового класса, необходимо просто реализовать в нем метод `ExecuteAsync()`. Пример представлен в следующем упрощенном коде из приложения eShopOnContainers, который опрашивает базу данных и при необходимости публикует события интеграции в шине событий.

```csharp
public class GracePeriodManagerService : BackgroundService
{
    private readonly ILogger<GracePeriodManagerService> _logger;
    private readonly OrderingBackgroundSettings _settings;

    private readonly IEventBus _eventBus;

    public GracePeriodManagerService(IOptions<OrderingBackgroundSettings> settings,
                                     IEventBus eventBus,
                                     ILogger<GracePeriodManagerService> logger)
    {
        // Constructor's parameters validations...
    }

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        _logger.LogDebug($"GracePeriodManagerService is starting.");

        stoppingToken.Register(() =>
            _logger.LogDebug($" GracePeriod background task is stopping."));

        while (!stoppingToken.IsCancellationRequested)
        {
            _logger.LogDebug($"GracePeriod task doing background work.");

            // This eShopOnContainers method is querying a database table
            // and publishing events into the Event Bus (RabbitMQ / ServiceBus)
            CheckConfirmedGracePeriodOrders();

            await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
        }

        _logger.LogDebug($"GracePeriod background task is stopping.");
    }

    .../...
}
```

В этом конкретном примере eShopOnContainers выполняет метод приложения, который отправляет запрос к таблице базы данных для поиска заказов с определенным состоянием, а при применении изменений публикует события интеграции через шину событий (она может быть основана на RabbitMQ или служебной шине Azure).

Естественно, вместо этого можно выполнять любую другую фоновую бизнес-задачу.

По умолчанию для токена отмены задается время ожидания, равное 5 секундам, хотя это значение можно изменить при создании `WebHost` с помощью расширения `UseShutdownTimeout` интерфейса `IWebHostBuilder`. Это означает, что отмена службы ожидается в течение 5 секунд. В противном случае ее работа будет завершена внезапно.

В следующем коде это время изменяется на 10 секунд:

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a>Сводная диаграмма классов

На приведенном ниже рисунке представлена наглядная сводка классов и интерфейсов, которые задействованы в реализации IHostedService.

![Схема, на которой показано, что в IWebHost и IHost может размещаться много служб.](./media/background-tasks-with-ihostedservice/class-diagram-custom-ihostedservice.png)

**Рис. 6-27**. Диаграмма классов и интерфейсов, связанных с IHostedService

Диаграмма классов: IWebHost и IHost могут разместить много служб, наследующих от BackgroundService, который реализует IHostedService.

### <a name="deployment-considerations-and-takeaways"></a>Основные положения и моменты, связанные с развертыванием

Важно отметить, что способ развертывания узла `WebHost` в ASP.NET Core или `Host` в .NET Core может влиять на конечное решение. Например, если вы развертываете `WebHost` в службах IIS или обычной службе приложений Azure, работа узла может быть завершена из-за перезапуска пула приложений. Однако если вы развертываете узел как контейнер в оркестраторе, таком как Kubernetes, вы можете контролировать гарантированное число активных экземпляров узла. Кроме того, в облачной среде можно рассмотреть другие подходы, особенно предназначенные для таких сценариев, как Функции Azure. Если же требуется, чтобы служба работала постоянно и была развернута в Windows Server, используйте службу Windows.

Даже при развертывании `WebHost` в пуле приложений применим ряд сценариев, таких как повторное заполнение или сброс кэша в памяти для приложения.

Интерфейс `IHostedService` предоставляет удобный способ запуска фоновых задач в веб-приложении ASP.NET Core (в .NET Core 2.0 или более поздних версий) или в любом процессе или узле (при использовании `IHost` начиная с .NET Core 2.1). Его главное преимущество — это возможность надлежащей отмены с целью очистки кода фоновых задач при завершении работы самого узла.

## <a name="additional-resources"></a>Дополнительные ресурсы

- **Building a scheduled task in ASP.NET Core/Standard 2.0** (Создание запланированной задачи в ASP.NET Core или Standard 2.0) \
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- **Implementing IHostedService in ASP.NET Core 2.0** (Реализация интерфейса IHostedService в ASP.NET Core 2.0) \
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- **Пример GenericHost с ASP.NET Core 2.1** \
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

> [!div class="step-by-step"]
> [Назад](test-aspnet-core-services-web-apps.md)
> [Вперед](implement-api-gateways-with-ocelot.md)
