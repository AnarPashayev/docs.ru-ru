---
title: Перенос службы WCF "запрос — ответ" в gRPC — gRPC для разработчиков WCF
description: Узнайте, как перенести простую службу "запрос — ответ" из WCF в gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 018aa94a15cdcb1e0f559afb7b3a88cd4f915398
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628557"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a><span data-ttu-id="8ae4b-103">Перенос службы WCF "запрос — ответ" в gRPC унарный RPC</span><span class="sxs-lookup"><span data-stu-id="8ae4b-103">Migrate a WCF request-reply service to a gRPC unary RPC</span></span>

<span data-ttu-id="8ae4b-104">В этом разделе описано, как перенести базовую службу "запрос-ответ" в WCF в унарную службу RPC в ASP.NET Core gRPC.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-104">This section covers how to migrate a basic request-reply service in WCF to a unary RPC service in ASP.NET Core gRPC.</span></span> <span data-ttu-id="8ae4b-105">Эти службы являются простейшими типами служб как в Windows Communication Foundation (WCF), так и в gRPC, поэтому лучше всего начать с этого места.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-105">These services are the simplest service types in both Windows Communication Foundation (WCF) and gRPC, so it's an excellent place to start.</span></span> <span data-ttu-id="8ae4b-106">После переноса службы вы узнаете, как создать клиентскую библиотеку из того же файла `.proto`, чтобы использовать службу из клиентского приложения .NET.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-106">After migrating the service, you'll learn how to generate a client library from the same `.proto` file to consume the service from a .NET client application.</span></span>

## <a name="the-wcf-solution"></a><span data-ttu-id="8ae4b-107">Решение WCF</span><span class="sxs-lookup"><span data-stu-id="8ae4b-107">The WCF solution</span></span>

<span data-ttu-id="8ae4b-108">[Решение портфолиоссампле](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) включает в себя простую службу портфеля "запрос-ответ" для загрузки одного портфеля или всех портфелей для конкретного торговца.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-108">The [PortfoliosSample solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) includes a simple request-reply Portfolio service to download either a single portfolio or all portfolios for a given trader.</span></span> <span data-ttu-id="8ae4b-109">Служба определена в интерфейсе `IPortfolioService` атрибутом `ServiceContract`:</span><span class="sxs-lookup"><span data-stu-id="8ae4b-109">The service is defined in the interface `IPortfolioService` with a `ServiceContract` attribute:</span></span>

```csharp
[ServiceContract]
public interface IPortfolioService
{
    [OperationContract]
    Task<Portfolio> Get(Guid traderId, int portfolioId);

    [OperationContract]
    Task<List<Portfolio>> GetAll(Guid traderId);
}
```

<span data-ttu-id="8ae4b-110">Модель `Portfolio` — это простой C# класс, помеченный как [DataContract](xref:System.Runtime.Serialization.DataContractAttribute) и включающий список объектов `PortfolioItem`.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-110">The `Portfolio` model is a simple C# class marked with [DataContract](xref:System.Runtime.Serialization.DataContractAttribute) and including a list of `PortfolioItem` objects.</span></span> <span data-ttu-id="8ae4b-111">Эти модели определяются в проекте `TraderSys.PortfolioData` вместе с классом репозитория, представляющим абстракцию доступа к данным.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-111">These models are defined in the `TraderSys.PortfolioData` project along with a repository class that represents a data access abstraction.</span></span>

```csharp
[DataContract]
public class Portfolio
{
    [DataMember]
    public int Id { get; set; }

    [DataMember]
    public Guid TraderId { get; set; }

    [DataMember]
    public List<PortfolioItem> Items { get; set; }
}

[DataContract]
public class PortfolioItem
{
    [DataMember]
    public int Id { get; set; }

    [DataMember]
    public int ShareId { get; set; }

    [DataMember]
    public int Holding { get; set; }

    [DataMember]
    public decimal Cost { get; set; }
}
```

<span data-ttu-id="8ae4b-112">В реализации `ServiceContract` используется класс репозитория, предоставляемый путем внедрения зависимостей, который возвращает экземпляры типов `DataContract`:</span><span class="sxs-lookup"><span data-stu-id="8ae4b-112">The `ServiceContract` implementation uses a repository class provided via dependency injection that returns instances of the `DataContract` types:</span></span>

```csharp
public class PortfolioService : IPortfolioService
{
    private readonly IPortfolioRepository _repository;

    public PortfolioService(IPortfolioRepository repository)
    {
        _repository = repository;
    }

    public async Task<Portfolio> Get(Guid traderId, int portfolioId)
    {
        return await _repository.GetAsync(traderId, portfolioId);
    }

    public async Task<List<Portfolio>> GetAll(Guid traderId)
    {
        return await _repository.GetAllAsync(traderId);
    }
}
```

## <a name="the-portfoliosproto-file"></a><span data-ttu-id="8ae4b-113">Файл портфелей.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-113">The portfolios.proto file</span></span>

<span data-ttu-id="8ae4b-114">Если вы выполнили инструкции из предыдущего раздела, у вас должен быть проект gRPC с файлом `portfolios.proto`, который выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="8ae4b-114">If you followed the instructions in the previous section, you should have a gRPC project with a `portfolios.proto` file that looks like this:</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

<span data-ttu-id="8ae4b-115">Первым шагом является перенос классов `DataContract` в их эквиваленты protobuf.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-115">The first step is to migrate the `DataContract` classes to their Protobuf equivalents.</span></span>

## <a name="convert-the-datacontract-classes-to-grpc-messages"></a><span data-ttu-id="8ae4b-116">Преобразование классов DataContract в сообщения gRPC</span><span class="sxs-lookup"><span data-stu-id="8ae4b-116">Convert the DataContract classes to gRPC messages</span></span>

<span data-ttu-id="8ae4b-117">Сначала класс `PortfolioItem` будет преобразован в сообщение protobuf, так как от него зависит класс `Portfolio`.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-117">The `PortfolioItem` class will be converted to a Protobuf message first, because the `Portfolio` class depends on it.</span></span> <span data-ttu-id="8ae4b-118">Класс прост, а три свойства сопоставляются непосредственно с типами данных gRPC.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-118">The class is simple, and three of the properties map directly to gRPC data types.</span></span> <span data-ttu-id="8ae4b-119">Свойство `Cost`, которое представляет цену, уплаченную для общих ресурсов по закупке, является полем `decimal`.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-119">The `Cost` property, which represents the price paid for the shares at purchase, is a `decimal` field.</span></span> <span data-ttu-id="8ae4b-120">gRPC поддерживает только `float` или `double` для реальных чисел, которые не подходят для валюты.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-120">gRPC supports only `float` or `double` for real numbers, which aren't suitable for currency.</span></span> <span data-ttu-id="8ae4b-121">Так как цены на общий ресурс зависят от минимума одного цента, стоимость может быть выражена в `int32` центов.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-121">Because share prices vary by a minimum of one cent, the cost can be expressed as an `int32` of cents.</span></span>

> [!NOTE]
> <span data-ttu-id="8ae4b-122">Не забудьте использовать camelCase для имен полей в файле `.proto`.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-122">Remember to use camelCase for field names in your `.proto` file.</span></span> <span data-ttu-id="8ae4b-123">Генератор C# кода преобразует их в PascalCase, и пользователи других языков будут поблагодарить вас за соблюдение разных стандартов кодирования.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-123">The C# code generator will convert them to PascalCase for you, and users of other languages will thank you for respecting their different coding standards.</span></span>

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 share_id = 2;
    int32 holding = 3;
    int32 cost_cents = 4;
}
```

<span data-ttu-id="8ae4b-124">Класс `Portfolio` немного сложнее.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-124">The `Portfolio` class is a little more complicated.</span></span> <span data-ttu-id="8ae4b-125">В коде WCF разработчик использовал `Guid` для свойства `TraderId` и содержит `List<PortfolioItem>`.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-125">In the WCF code, the developer used a `Guid` for the `TraderId` property, and contains a `List<PortfolioItem>`.</span></span> <span data-ttu-id="8ae4b-126">В protobuf, который не имеет типа `UUID` первого класса, следует использовать `string` для поля `traderId` и анализировать его в собственном коде.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-126">In Protobuf, which doesn't have a first-class `UUID` type, you should use a `string` for the `traderId` field and parse it in your own code.</span></span> <span data-ttu-id="8ae4b-127">Для списка элементов используйте ключевое слово `repeated` в поле.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-127">For the list of items, use the `repeated` keyword on the field.</span></span>

```protobuf
message Portfolio {
    int32 id = 1;
    string trader_id = 2;
    repeated PortfolioItem items = 3;
}
```

<span data-ttu-id="8ae4b-128">Теперь, когда у вас есть сообщения с данными, можно объявить конечные точки RPC службы.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-128">Now that you have the data messages, you can declare the service RPC endpoints.</span></span>

## <a name="convert-servicecontract-to-a-grpc-service"></a><span data-ttu-id="8ae4b-129">Преобразование ServiceContract в службу gRPC</span><span class="sxs-lookup"><span data-stu-id="8ae4b-129">Convert ServiceContract to a gRPC service</span></span>

<span data-ttu-id="8ae4b-130">Метод `Get` WCF принимает два параметра: `Guid traderId` и `int portfolioId`.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-130">The WCF `Get` method takes two parameters: `Guid traderId` and `int portfolioId`.</span></span> <span data-ttu-id="8ae4b-131">методы службы gRPC могут принимать только один параметр, поэтому необходимо создать сообщение для хранения двух значений.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-131">gRPC service methods can take only a single parameter, so you need to create a message to hold the two values.</span></span> <span data-ttu-id="8ae4b-132">Обычно имена этих объектов запроса имеют то же имя, что и метод, за которым следует суффикс `Request`.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-132">It's common practice to name these request objects with the same name as the method followed by the suffix `Request`.</span></span> <span data-ttu-id="8ae4b-133">Опять же, `string` используется для поля `traderId`, а не `Guid`.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-133">Again, `string` is being used for the `traderId` field instead of `Guid`.</span></span>

<span data-ttu-id="8ae4b-134">Служба может просто вернуть сообщение `Portfolio` напрямую, но опять же это может повлиять на обратную совместимость в будущем.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-134">The service could just return a `Portfolio` message directly, but again, this could affect backward compatibility in the future.</span></span> <span data-ttu-id="8ae4b-135">Рекомендуется определять отдельные `Request` и `Response` сообщения для каждого метода в службе, даже если многие из них одинаковы.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-135">It's a good practice to define separate `Request` and `Response` messages for every method in a service, even if many of them are the same right now.</span></span> <span data-ttu-id="8ae4b-136">Поэтому объявите сообщение `GetResponse` с одним `Portfolio` полем.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-136">So declare a `GetResponse` message with a single `Portfolio` field.</span></span>

<span data-ttu-id="8ae4b-137">В этом примере показано объявление метода службы gRPC с сообщением `GetRequest`:</span><span class="sxs-lookup"><span data-stu-id="8ae4b-137">This example shows the declaration of the gRPC service method with the `GetRequest` message:</span></span>

```protobuf
message GetRequest {
    string trader_id = 1;
    int32 portfolio_id = 2;
}

message GetResponse {
    Portfolio portfolio = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (GetResponse);
}
```

<span data-ttu-id="8ae4b-138">Метод `GetAll` WCF принимает только один параметр, `traderId`, поэтому может показаться, что в качестве типа параметра можно указать `string`.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-138">The WCF `GetAll` method takes only a single parameter, `traderId`, so it might seem that you could specify `string` as the parameter type.</span></span> <span data-ttu-id="8ae4b-139">Но для gRPC требуется определенный тип сообщений.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-139">But gRPC requires a defined message type.</span></span> <span data-ttu-id="8ae4b-140">Это требование позволяет принудительно использовать пользовательские сообщения для всех входных и выходных данных, чтобы обеспечить обратную совместимость.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-140">This requirement helps to enforce the practice of using custom messages for all inputs and outputs, for future backward compatibility.</span></span>

<span data-ttu-id="8ae4b-141">Метод WCF также возвращает `List<Portfolio>`, но по той же причине он не допускает простые типы параметров, gRPC не допускает `repeated Portfolio` как тип возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-141">The WCF method also returns a `List<Portfolio>`, but for the same reason it doesn't allow simple parameter types, gRPC won't allow `repeated Portfolio` as a return type.</span></span> <span data-ttu-id="8ae4b-142">Вместо этого создайте тип `GetAllResponse` для заключения в список.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-142">Instead, create a `GetAllResponse` type to wrap the list.</span></span>

> [!WARNING]
> <span data-ttu-id="8ae4b-143">Возможно, вы можете создать `PortfolioList` сообщение или нечто похожее и использовать его в нескольких методах службы, но вы должны быть бесискушенияными.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-143">You might be tempted to create a `PortfolioList` message or something similar and use it across multiple service methods, but you should resist this temptation.</span></span> <span data-ttu-id="8ae4b-144">Невозможно понять, как будут развиваться различные методы в службе, чтобы обеспечить их конкретную и четко разделенную.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-144">It's impossible to know how the various methods on a service will evolve, so keep their messages specific and cleanly separated.</span></span>

```protobuf
message GetAllRequest {
    string trader_id = 1;
}

message PortfolioList {
    repeated Portfolio portfolios = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (Portfolio);
    rpc GetAll(GetAllRequest) returns (GetAllResponse);
}
```

<span data-ttu-id="8ae4b-145">Если сохранить проект с этими изменениями, целевой объект сборки gRPC будет выполняться в фоновом режиме и создавать все типы сообщений protobuf и базовый класс, который можно унаследовать для реализации службы.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-145">If you save your project with these changes, the gRPC build target will run in the background and generate all the Protobuf message types and a base class that you can inherit to implement the service.</span></span>

<span data-ttu-id="8ae4b-146">Откройте класс `Services/GreeterService.cs` и удалите код примера.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-146">Open the `Services/GreeterService.cs` class and delete the example code.</span></span> <span data-ttu-id="8ae4b-147">Теперь можно добавить реализацию службы портфеля.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-147">Now you can add the Portfolio service implementation.</span></span> <span data-ttu-id="8ae4b-148">Созданный базовый класс будет находиться в пространстве имен `Protos` и создан как вложенный класс.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-148">The generated base class will be in the `Protos` namespace and is generated as a nested class.</span></span> <span data-ttu-id="8ae4b-149">gRPC создает статический класс с тем же именем, что и служба в файле `.proto`, и базовый класс с суффиксом `Base` внутри этого статического класса, поэтому полный идентификатор для базового типа — `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-149">gRPC creates a static class with the same name as the service in the `.proto` file and a base class with the suffix `Base` inside that static class, so the full identifier for the base type is `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`.</span></span>

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

<span data-ttu-id="8ae4b-150">Базовый класс объявляет `virtual` методы для `Get` и `GetAll`, которые могут быть переопределены для реализации службы.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-150">The base class declares `virtual` methods for `Get` and `GetAll` that can be overridden to implement the service.</span></span> <span data-ttu-id="8ae4b-151">Методы `virtual`, а не `abstract` поэтому, если их не реализовать, служба может возвращать явный код состояния `Unimplemented` gRPC, подобно тому, что вы можете создать `NotImplementedException` в обычном C# коде.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-151">The methods are `virtual` rather than `abstract` so that if you don't implement them, the service can return an explicit gRPC `Unimplemented` status code, much like you might throw a `NotImplementedException` in regular C# code.</span></span>

<span data-ttu-id="8ae4b-152">Сигнатура для всех методов унарной службы gRPC в ASP.NET Core является единообразной.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-152">The signature for all gRPC unary service methods in ASP.NET Core is consistent.</span></span> <span data-ttu-id="8ae4b-153">Существует два параметра: первый — тип сообщения, объявленный в файле `.proto`, второй — `ServerCallContext`, который работает аналогично `HttpContext` из ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-153">There are two parameters: the first is the message type declared in the `.proto` file, and the second is a `ServerCallContext` that works similarly to the `HttpContext` from ASP.NET Core.</span></span> <span data-ttu-id="8ae4b-154">На самом деле, существует метод расширения, именуемый `GetHttpContext` класса `ServerCallContext`, который можно использовать для получения базовой `HttpContext`, хотя это не должно часто использоваться.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-154">In fact, there's an extension method called `GetHttpContext` on the `ServerCallContext` class that you can use to get the underlying `HttpContext`, although you shouldn't need to use it often.</span></span> <span data-ttu-id="8ae4b-155">Мы рассмотрим `ServerCallContext` далее в этой главе, а также в главе, посвященной проверке подлинности.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-155">We'll take a look at `ServerCallContext` later in this chapter, and also in the chapter that discusses authentication.</span></span>

<span data-ttu-id="8ae4b-156">Тип возвращаемого значения метода — это `Task<T>`, где `T` является типом ответного сообщения.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-156">The method's return type is a `Task<T>`, where `T` is the response message type.</span></span> <span data-ttu-id="8ae4b-157">Все методы службы gRPC являются асинхронными.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-157">All gRPC service methods are asynchronous.</span></span>

## <a name="migrate-the-portfoliodata-library-to-net-core"></a><span data-ttu-id="8ae4b-158">Миграция библиотеки Портфолиодата в .NET Core</span><span class="sxs-lookup"><span data-stu-id="8ae4b-158">Migrate the PortfolioData library to .NET Core</span></span>

<span data-ttu-id="8ae4b-159">На этом этапе проекту требуется репозиторий портфеля и модели, содержащиеся в библиотеке классов `TraderSys.PortfolioData` в решении WCF.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-159">At this point, the project needs the Portfolio repository and models contained in the `TraderSys.PortfolioData` class library in the WCF solution.</span></span> <span data-ttu-id="8ae4b-160">Самый простой способ сделать это — создать новую библиотеку классов с помощью диалогового окна **Новый проект** Visual Studio с шаблоном библиотеки классов (.NET Standard) или из командной строки с помощью .NET Core CLI запуска этих команд из каталога, содержащего файл `TraderSys.sln`:</span><span class="sxs-lookup"><span data-stu-id="8ae4b-160">The easiest way to bring them across is to create a new class library by using either the Visual Studio **New project** dialog box with the Class Library (.NET Standard) template, or from the command line by using the .NET Core CLI, running these commands from the directory that contains the `TraderSys.sln` file:</span></span>

```dotnetcli
dotnet new classlib -o src/TraderSys.PortfolioData
dotnet sln add src/TraderSys.PortfolioData
```

<span data-ttu-id="8ae4b-161">После создания библиотеки и добавления ее в решение удалите созданный файл `Class1.cs` и скопируйте файлы из библиотеки решения WCF в папку новой библиотеки классов, сохранив структуру папок:</span><span class="sxs-lookup"><span data-stu-id="8ae4b-161">After you've created the library and added it to the solution, delete the generated `Class1.cs` file and copy the files from the WCF solution's library into the new class library's folder, keeping the folder structure:</span></span>

```
Models
  Portfolio.cs
  PortfolioItem.cs
IPortfolioRepository.cs
PortfolioRepository.cs
```

<span data-ttu-id="8ae4b-162">Проекты .NET в стиле пакета SDK автоматически включают в себя любые `.cs` файлы в или в собственном каталоге, поэтому не нужно явно добавлять их в проект.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-162">SDK-style .NET projects automatically include any `.cs` files in or under their own directory, so you don't need to explicitly add them to the project.</span></span> <span data-ttu-id="8ae4b-163">Осталось только удалить `DataContract` и `DataMember` атрибуты из классов `Portfolio` и `PortfolioItem`, чтобы они были простыми старыми C# классами:</span><span class="sxs-lookup"><span data-stu-id="8ae4b-163">The only step remaining is to remove the `DataContract` and `DataMember` attributes from the `Portfolio` and `PortfolioItem` classes so they're plain old C# classes:</span></span>

```csharp
public class Portfolio
{
    public int Id { get; set; }
    public Guid TraderId { get; set; }
    public List<PortfolioItem> Items { get; set; }
}

public class PortfolioItem
{
    public int Id { get; set; }
    public int ShareId { get; set; }
    public int Holding { get; set; }
    public decimal Cost { get; set; }
}
```

## <a name="use-aspnet-core-dependency-injection"></a><span data-ttu-id="8ae4b-164">Использование внедрения зависимостей ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8ae4b-164">Use ASP.NET Core dependency injection</span></span>

<span data-ttu-id="8ae4b-165">Теперь можно добавить ссылку на эту библиотеку в проект приложения gRPC и использовать класс `PortfolioRepository` с помощью внедрения зависимостей в реализации службы gRPC.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-165">Now you can add a reference to this library to the gRPC application project and consume the `PortfolioRepository` class by using dependency injection in the gRPC service implementation.</span></span> <span data-ttu-id="8ae4b-166">В приложении WCF внедрение зависимостей было предоставлено контейнером IoC Autofac.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-166">In the WCF application, dependency injection was provided by the Autofac IoC container.</span></span> <span data-ttu-id="8ae4b-167">ASP.NET Core помогут с внедрением зависимостей в.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-167">ASP.NET Core has dependency injection baked in.</span></span> <span data-ttu-id="8ae4b-168">Зарегистрировать репозиторий можно в методе `ConfigureServices` класса `Startup`:</span><span class="sxs-lookup"><span data-stu-id="8ae4b-168">You can register the repository in the `ConfigureServices` method in the `Startup` class:</span></span>

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Register the repository class as a scoped service (instance per request)
        services.AddScoped<IPortfolioRepository, PortfolioRepository>();

        services.AddGrpc();
    }

    // ...
}
```

<span data-ttu-id="8ae4b-169">Теперь можно указать `IPortfolioRepository` реализацию в качестве параметра конструктора в классе `PortfolioService`, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-169">The `IPortfolioRepository` implementation can now be specified as a constructor parameter in the `PortfolioService` class, as follows:</span></span>

```csharp
public class PortfolioService : Protos.Portfolios.PortfoliosBase
{
    private readonly IPortfolioRepository _repository;

    public PortfolioService(IPortfolioRepository repository)
    {
        _repository = repository;
    }
}
```

## <a name="implement-the-grpc-service"></a><span data-ttu-id="8ae4b-170">Реализация службы gRPC</span><span class="sxs-lookup"><span data-stu-id="8ae4b-170">Implement the gRPC service</span></span>

<span data-ttu-id="8ae4b-171">Теперь, когда вы объявили сообщения и службу в файле `portfolios.proto`, необходимо реализовать методы службы в классе `PortfolioService`, который наследуется от класса `Portfolios.PortfoliosBase`, созданного gRPC.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-171">Now that you've declared your messages and your service in the `portfolios.proto` file, you have to implement the service methods in the `PortfolioService` class that inherits from the gRPC-generated `Portfolios.PortfoliosBase` class.</span></span> <span data-ttu-id="8ae4b-172">Методы объявляются как `virtual` в базовом классе.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-172">The methods are declared as `virtual` in the base class.</span></span> <span data-ttu-id="8ae4b-173">Если вы не переопределяете их, они возвращают код состояния gRPC "не реализован" по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-173">If you don't override them, they'll return a gRPC "Not Implemented" status code by default.</span></span>

<span data-ttu-id="8ae4b-174">Начните с реализации метода `Get`.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-174">Start by implementing the `Get` method.</span></span> <span data-ttu-id="8ae4b-175">Переопределение по умолчанию выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="8ae4b-175">The default override looks like this example:</span></span>

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

<span data-ttu-id="8ae4b-176">Первая проблема заключается в том, что `request.TraderId` является строкой, а для службы требуется `Guid`.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-176">The first problem is that `request.TraderId` is a string, and the service requires a `Guid`.</span></span> <span data-ttu-id="8ae4b-177">Несмотря на то, что ожидаемый формат строки `UUID`, код должен иметь дело с возможностью, когда вызывающий объект отправил недопустимое значение и отвечал соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-177">Even though the expected format for the string is `UUID`, the code has to deal with the possibility that a caller has sent an invalid value and respond appropriately.</span></span> <span data-ttu-id="8ae4b-178">Служба может реагировать на ошибки, вызывая `RpcException` и использовать стандартный код состояния `InvalidArgument` для выражения проблемы:</span><span class="sxs-lookup"><span data-stu-id="8ae4b-178">The service can respond with errors by throwing an `RpcException` and use the standard `InvalidArgument` status code to express the problem:</span></span>

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    return base.Get(request, context);
}
```

<span data-ttu-id="8ae4b-179">После получения верного значения `Guid` для `traderId`можно использовать репозиторий, чтобы получить портфель и вернуть его клиенту:</span><span class="sxs-lookup"><span data-stu-id="8ae4b-179">After there's a proper `Guid` value for `traderId`, you can use the repository to retrieve the Portfolio and return it to the client:</span></span>

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a><span data-ttu-id="8ae4b-180">Сопоставьте внутренние модели с gRPC сообщениями</span><span class="sxs-lookup"><span data-stu-id="8ae4b-180">Map internal models to gRPC messages</span></span>

<span data-ttu-id="8ae4b-181">Предыдущий код не работает, так как репозиторий возвращает собственную модель POCO `Portfolio`, но для gRPC требуется собственное сообщение protobuf `Portfolio`.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-181">The previous code doesn't actually work because the repository is returning its own POCO model `Portfolio`, but gRPC needs its own Protobuf message `Portfolio`.</span></span> <span data-ttu-id="8ae4b-182">Как и при сопоставлении типов Entity Framework с типами передачи данных, лучшим решением будет обеспечение преобразования между ними.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-182">As when you map Entity Framework types to data transfer types, the best solution is to provide a conversion between the two.</span></span> <span data-ttu-id="8ae4b-183">Поместите код для этого преобразования в создаваемый protobuf класс, который объявлен как класс `partial`, чтобы его можно было расширить:</span><span class="sxs-lookup"><span data-stu-id="8ae4b-183">A good place to put the code for this conversion is in the Protobuf-generated class, which is declared as a `partial` class so it can be extended:</span></span>

```csharp
namespace TraderSys.Portfolios.Protos
{
    public partial class PortfolioItem
    {
        public static PortfolioItem FromRepositoryModel(PortfolioData.Models.PortfolioItem source)
        {
            if (source is null) return null;

            return new PortfolioItem
            {
                Id = source.Id,
                ShareId = source.ShareId,
                Holding = source.Holding,
                CostCents = (int)(source.Cost * 100)
            };
        }
    }

    public partial class Portfolio
    {
        public static Portfolio FromRepositoryModel(PortfolioData.Models.Portfolio source)
        {
            if (source is null) return null;

            var target = new Portfolio
            {
                Id = source.Id,
                TraderId = source.TraderId.ToString(),
            };

            target.Items.AddRange(source.Items.Select(PortfolioItem.FromRepositoryModel));

            return target;
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="8ae4b-184">Можно использовать библиотеку [, например Автопреобразование, для](https://automapper.org/) обработки преобразования из внутренних классов модели в типы protobuf, если вы настроили преобразования типов нижнего уровня, такие как `string`/`Guid` или `decimal`/`double` и сопоставление списка.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-184">You could use a library like [AutoMapper](https://automapper.org/) to handle this conversion from internal model classes to Protobuf types, as long as you configure the lower-level type conversions like `string`/`Guid` or `decimal`/`double` and the list mapping.</span></span>

<span data-ttu-id="8ae4b-185">Теперь, когда имеется код преобразования, можно выполнить реализацию `Get` метода:</span><span class="sxs-lookup"><span data-stu-id="8ae4b-185">Now that you have the conversion code in place, you can complete the `Get` method implementation:</span></span>

```csharp
public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    var portfolio = await _repository.GetAsync(traderId, request.PortfolioId);

    return new GetResponse
    {
        Portfolio = Portfolio.FromRepositoryModel(portfolio)
    };
}

```

<span data-ttu-id="8ae4b-186">Реализация метода `GetAll` аналогична.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-186">The implementation of the `GetAll` method is similar.</span></span> <span data-ttu-id="8ae4b-187">Обратите внимание, что поля `repeated` в сообщениях protobuf создаются как `readonly` свойства типа `RepeatedField<T>`, поэтому необходимо добавить элементы в них с помощью метода `AddRange`, как в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="8ae4b-187">Note that the `repeated` fields on Protobuf messages are generated as `readonly` properties of type `RepeatedField<T>`, so you have to add items to them by using the `AddRange` method, like in this example:</span></span>

```csharp
public override async Task<GetAllResponse> GetAll(GetAllRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    var portfolios = await _repository.GetAllAsync(traderId);

    var response = new GetAllResponse();
    response.Portfolios.AddRange(portfolios.Select(Portfolio.FromRepositoryModel));

    return response;
}
```

<span data-ttu-id="8ae4b-188">После успешного переноса службы WCF "запрос — ответ" в gRPC рассмотрим создание клиента для него из файла `.proto`.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-188">Having successfully migrated the WCF request-reply service to gRPC, let's look at creating a client for it from the `.proto` file.</span></span>

## <a name="generate-client-code"></a><span data-ttu-id="8ae4b-189">Создание клиентского кода</span><span class="sxs-lookup"><span data-stu-id="8ae4b-189">Generate client code</span></span>

<span data-ttu-id="8ae4b-190">Создайте .NET Standard библиотеку классов в том же решении, в котором будет содержаться клиент.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-190">Create a .NET Standard class library in the same solution to contain the client.</span></span> <span data-ttu-id="8ae4b-191">Это, в первую очередь, пример создания клиентского кода, но можно упаковать такую библиотеку с помощью NuGet и распространить ее во внутреннем репозитории для использования другими командами .NET.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-191">This is primarily an example of creating client code, but you could package such a library by using NuGet and distribute it on an internal repository for other .NET teams to consume.</span></span> <span data-ttu-id="8ae4b-192">Добавьте новую библиотеку классов .NET Standard с именем `TraderSys.Portfolios.Client` в решение и удалите файл `Class1.cs`.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-192">Go ahead and add a new .NET Standard class library called `TraderSys.Portfolios.Client` to the solution and delete the `Class1.cs` file.</span></span>

> [!CAUTION]
> <span data-ttu-id="8ae4b-193">Для пакета NuGet [.NET. Client GRPC](https://www.nuget.org/packages/Grpc.Net.Client) требуется .net Core 3,0 (или другая .NET Standard 2,1-совместимая среда выполнения).</span><span class="sxs-lookup"><span data-stu-id="8ae4b-193">The [Grpc.Net.Client](https://www.nuget.org/packages/Grpc.Net.Client) NuGet package requires .NET Core 3.0 (or another .NET Standard 2.1-compliant runtime).</span></span> <span data-ttu-id="8ae4b-194">Более ранние версии .NET Framework и .NET Core поддерживаются пакетом NuGet [GRPC. Core](https://www.nuget.org/packages/Grpc.Core) .</span><span class="sxs-lookup"><span data-stu-id="8ae4b-194">Earlier versions of .NET Framework and .NET Core are supported by the [Grpc.Core](https://www.nuget.org/packages/Grpc.Core) NuGet package.</span></span>

<span data-ttu-id="8ae4b-195">В Visual Studio 2019 можно добавить ссылки на службы gRPC так же, как вы добавите ссылки на службы в проекты WCF в более ранних версиях Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-195">In Visual Studio 2019, you can add references to gRPC services in a way that's similar to how you'd add service references to WCF projects in earlier versions of Visual Studio.</span></span> <span data-ttu-id="8ae4b-196">Ссылки на службы и подключенные службы управляются в одном пользовательском интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-196">Service references and connected services are all managed under the same UI now.</span></span> <span data-ttu-id="8ae4b-197">Чтобы получить доступ к пользовательскому интерфейсу, щелкните правой кнопкой мыши узел **зависимости** в проекте `TraderSys.Portfolios.Client` в Обозреватель решений и выберите команду **Добавить подключенную службу**.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-197">You can access the UI by right-clicking the **Dependencies** node in the `TraderSys.Portfolios.Client` project in Solution Explorer and selecting **Add Connected Service**.</span></span> <span data-ttu-id="8ae4b-198">В появившемся окне инструментов выберите раздел ссылки на **службу** , а затем щелкните **Добавить новую ссылку на службу gRPC**:</span><span class="sxs-lookup"><span data-stu-id="8ae4b-198">In the tool window that appears, select the **Service References** section and then select **Add new gRPC service reference**:</span></span>

![Подключенные службы пользовательский интерфейс в Visual Studio 2019](media/migrate-request-reply/add-connected-service.png)

<span data-ttu-id="8ae4b-200">Перейдите к файлу `portfolios.proto` в проекте `TraderSys.Portfolios`, оставьте **клиент** в разделе **выберите тип создаваемого класса**и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-200">Browse to the `portfolios.proto` file in the `TraderSys.Portfolios` project, leave **Client** under **Select the type of class to be generated**, and then select **OK**:</span></span>

![Диалоговое окно "Добавление новой ссылки на службу gRPC" в Visual Studio 2019](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> <span data-ttu-id="8ae4b-202">Обратите внимание, что в этом диалоговом окне также есть поле URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-202">Notice that this dialog box also provides a URL field.</span></span> <span data-ttu-id="8ae4b-203">Если ваша организация поддерживает доступ к веб-каталогу `.proto` файлов, можно создать клиенты, просто задав этот URL-адрес.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-203">If your organization maintains a web-accessible directory of `.proto` files, you can create clients just by setting this URL address.</span></span>

<span data-ttu-id="8ae4b-204">При использовании компонента Visual Studio **Add Connected Service** файл `portfolios.proto` добавляется в проект библиотеки классов как *связанный файл* , а не копируется, поэтому изменения в файле проекта службы будут автоматически применены в клиентском проекте.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-204">When you use the Visual Studio **Add Connected Service** feature, the `portfolios.proto` file is added to the class library project as a *linked file* rather than copied, so changes to the file in the service project will automatically be applied in the client project.</span></span> <span data-ttu-id="8ae4b-205">Элемент `<Protobuf>` в файле `csproj` выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="8ae4b-205">The `<Protobuf>` element in the `csproj` file looks like this:</span></span>

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

> [!TIP]
> <span data-ttu-id="8ae4b-206">Если вы не используете Visual Studio или предпочитаете работать из командной строки, можно использовать глобальное средство `dotnet-grpc` для управления ссылками protobuf в проекте .NET gRPC.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-206">If you're not using Visual Studio or prefer to work from the command line, you can use the `dotnet-grpc` global tool to manage Protobuf references in a .NET gRPC project.</span></span> <span data-ttu-id="8ae4b-207">Дополнительные сведения см. в [документации по`dotnet-grpc`](/aspnet/core/grpc/dotnet-grpc).</span><span class="sxs-lookup"><span data-stu-id="8ae4b-207">For more information, see the [`dotnet-grpc` documentation](/aspnet/core/grpc/dotnet-grpc).</span></span>

### <a name="use-the-portfolios-service-from-a-client-application"></a><span data-ttu-id="8ae4b-208">Использование службы "портфолио" из клиентского приложения</span><span class="sxs-lookup"><span data-stu-id="8ae4b-208">Use the Portfolios service from a client application</span></span>

<span data-ttu-id="8ae4b-209">Следующий код является кратким примером использования созданного клиента в консольном приложении.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-209">The following code is a brief example of how to use the generated client in a console application.</span></span> <span data-ttu-id="8ae4b-210">Более подробное изучение кода клиента gRPC находится в конце этой главы.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-210">A more detailed exploration of the gRPC client code is at the end of this chapter.</span></span>

```csharp
public class Program
{
    public async Task Main(string[] args)
    {
        GetResponse response;

        using (var channel = GrpcChannel.ForAddress("https://localhost:5001"))
        {
            var client = new Protos.Portfolios.PortfoliosClient(channel);

            response = await client.GetAsync(new GetRequest
            {
                TraderId = args[0],
                PortfolioId = int.Parse(args[1])
            });
        }

        foreach (var item in response.Portfolio.Items)
        {
            Console.WriteLine($"Holding {item.Holding} of Share ID {item.ShareId}.");
        }
    }
}
```

<span data-ttu-id="8ae4b-211">Теперь вы перенесли базовое приложение WCF в службу ASP.NET Core gRPC и создали клиент для использования службы из приложения .NET.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-211">You've now migrated a basic WCF application to an ASP.NET Core gRPC service and created a client to consume the service from a .NET application.</span></span> <span data-ttu-id="8ae4b-212">В следующем разделе будут рассмотрены более используемые Дуплексные службы.</span><span class="sxs-lookup"><span data-stu-id="8ae4b-212">The next section will cover the more involved duplex services.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8ae4b-213">[Назад](create-project.md)
>[Вперед](migrate-duplex-services.md)</span><span class="sxs-lookup"><span data-stu-id="8ae4b-213">[Previous](create-project.md)
[Next](migrate-duplex-services.md)</span></span>
