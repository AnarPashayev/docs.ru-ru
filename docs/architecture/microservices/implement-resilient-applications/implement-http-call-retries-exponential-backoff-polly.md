---
title: Реализация повторных попыток вызова HTTP с экспоненциальной выдержкой с помощью библиотеки Polly
description: Узнайте, как обрабатывать сбои HTTP-запросов с помощью Polly и HttpClientFactory.
ms.date: 01/07/2019
ms.openlocfilehash: aa500b5525eff9f0bbf91bf98de8945f7c84704f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674571"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a>Реализация повторных попыток вызова HTTP с экспоненциальной выдержкой с помощью HttpClientFactory и политик Polly

Рекомендуемый подход к выполнению повторных попыток с экспоненциальной выдержкой заключается в использовании расширенных библиотек .NET, таких как [библиотека Polly](https://github.com/App-vNext/Polly) с открытым кодом.

Polly — это библиотека .NET, которая предоставляет возможности обеспечения отказоустойчивости и обработки временных сбоев. Эти возможности можно реализовать путем применения политик Polly, таких как политики повтора, размыкателя цепи, изоляции отсеков, времени ожидания и отката. Polly предназначена для .NET 4.x и библиотеки .NET Standard 1.0 (поддерживает .NET Core).

Тем не менее использовать библиотеку Polly с вашим кодом с помощью HttpClient может быть довольно сложно. В исходной версии eShopOnContainers существовал [стандартный блок ResilientHttpClient](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) на базе Polly. Но с появлением [HttpClientFactory](use-httpclientfactory-to-implement-resilient-http-requests.md) стало гораздо проще реализовывать устойчивое соединение по протоколу HTTP, так что этот стандартный блок был исключен из eShopOnContainers. 

Ниже показано, как можно использовать повторные HTTP-запросы через Polly с интеграцией HttpClientFactory, как описано в предыдущем разделе.

**Ссылка на пакеты ASP.NET Core 2.2**

`HttpClientFactory` доступно с версии .NET Core 2.1, но мы рекомендуем использовать последние пакеты ASP.NET Core 2.2 из NuGet в проекте. Обычно вам нужен метапакет `AspNetCore` и пакет расширений `Microsoft.Extensions.Http.Polly`.

**Настройка клиента с помощью политики повтора Polly в параметрах запуска**

Как показано в предыдущих разделах, необходимо определить конфигурацию HttpClient именованного или типизированного клиента в стандартном методе Startup.ConfigureServices(...), но теперь вам потребуется добавочный код, указывающий политику для повторных HTTP-запросов с экспоненциальной выдержкой, как показано ниже:

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

Метод **AddPolicyHandler()** добавляет политики для объектов `HttpClient`, которые вы будете использовать. В этом случае он добавляет политику Polly для повторных HTTP-запросов с экспоненциальной задержкой.

Для реализации более модульного подхода политику повтора HTTP-запросов можно определить в отдельном методе в файле `Startup.cs`, как в следующем примере.

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2,
                                                                    retryAttempt)));
}
```

С помощью Polly вы определяете политику повтора с числом повторных попыток, конфигурацией экспоненциальной задержки и действиями, которые необходимо выполнить в случае исключения HTTP (например, запись ошибки в журнал). В этом случае политика настроена на шесть попыток с экспоненциальной выдержкой, начиная с двух секунд. 

Будет предпринято шесть попыток, и период между попытками будет экспоненциально возрастать начиная с двух секунд.

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a>Добавление стратегии обработки колебания задержки в политику повтора

Обычная политика повтора может влиять на работу системы в случае высокого уровня параллелизма и масштабируемости, а также в условиях интенсивного состязания за ресурсы. Чтобы решить проблему с большим числом повторных запросов, поступающих от множества клиентов в случае частичного отказа системы, можно добавить стратегию в отношении колебания задержки в алгоритм или политику повтора. Это может повысить общую производительность всей системы благодаря тому, что экспоненциальная задержка становится более случайной. При возникновении проблем пики размываются. При использовании простой политики Polly код для реализации колебания задержки может выглядеть следующим образом:

```csharp
Random jitterer = new Random(); 
Policy
  .Handle<HttpResponseException>() // etc
  .WaitAndRetry(5,    // exponential back-off plus some jitter
      retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                    + TimeSpan.FromMilliseconds(jitterer.Next(0, 100)) 
  );
```

## <a name="additional-resources"></a>Дополнительные ресурсы

- **Шаблон повтора**  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- **Использование Polly и HttpClientFactory**  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- **Polly (библиотека для обеспечения отказоустойчивости .NET и обработки временных сбоев)**  
  <https://github.com/App-vNext/Polly>

- **Марк Брукер (Marc Brooker). Колебания. Оптимизация с помощью случайности**  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
>[Назад](explore-custom-http-call-retries-exponential-backoff.md)
>[Вперед](implement-circuit-breaker-pattern.md)
