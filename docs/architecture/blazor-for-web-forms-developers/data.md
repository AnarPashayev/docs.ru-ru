---
title: Доступ к данным и управление ими
description: Узнайте, как получить доступ к данным и работать с ними в веб-формах ASP.NET и Blazor .
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 04/26/2020
ms.openlocfilehash: 4bf9bee21ce1db828dbe0aeb156d5e15cae4f703
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173308"
---
# <a name="work-with-data"></a><span data-ttu-id="35e6d-103">Работа с данными</span><span class="sxs-lookup"><span data-stu-id="35e6d-103">Work with data</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="35e6d-104">Доступ к данным — это основа приложения веб-форм ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="35e6d-104">Data access is the backbone of an ASP.NET Web Forms app.</span></span> <span data-ttu-id="35e6d-105">Что происходит с этими данными при создании форм для Интернета?</span><span class="sxs-lookup"><span data-stu-id="35e6d-105">If you're building forms for the web, what happens to that data?</span></span> <span data-ttu-id="35e6d-106">С помощью веб-форм существовало несколько методов доступа к данным, которые можно использовать для взаимодействия с базой данных:</span><span class="sxs-lookup"><span data-stu-id="35e6d-106">With Web Forms, there were multiple data access techniques you could use to interact with a database:</span></span>

- <span data-ttu-id="35e6d-107">Data Sources</span><span class="sxs-lookup"><span data-stu-id="35e6d-107">Data Sources</span></span>
- <span data-ttu-id="35e6d-108">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="35e6d-108">ADO.NET</span></span>
- <span data-ttu-id="35e6d-109">Entity Framework</span><span class="sxs-lookup"><span data-stu-id="35e6d-109">Entity Framework</span></span>

<span data-ttu-id="35e6d-110">Источники данных — это элементы управления, которые можно разместить на странице веб-форм и настроить аналогично другим элементам управления.</span><span class="sxs-lookup"><span data-stu-id="35e6d-110">Data Sources were controls that you could place on a Web Forms page and configure like other controls.</span></span> <span data-ttu-id="35e6d-111">Visual Studio предоставляет удобный набор диалоговых окон для настройки и привязки элементов управления к страницам веб-форм.</span><span class="sxs-lookup"><span data-stu-id="35e6d-111">Visual Studio provided a friendly set of dialogs to configure and bind the controls to your Web Forms pages.</span></span> <span data-ttu-id="35e6d-112">Разработчики, которые пользуются «низким кодом» или «без кода», предпочитают этот метод при первом выпуске веб-форм.</span><span class="sxs-lookup"><span data-stu-id="35e6d-112">Developers who enjoy a "low code" or "no code" approach preferred this technique when Web Forms was first released.</span></span>

![Data Sources](media/data/datasources.png)

<span data-ttu-id="35e6d-114">ADO.NET — это подход низкого уровня для взаимодействия с базой данных.</span><span class="sxs-lookup"><span data-stu-id="35e6d-114">ADO.NET is the low-level approach to interacting with a database.</span></span> <span data-ttu-id="35e6d-115">Приложения могут создать подключение к базе данных с помощью команд, наборов записей и наборов данных для взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="35e6d-115">Your apps could create a connection to the database with Commands, Recordsets, and Datasets for interacting.</span></span> <span data-ttu-id="35e6d-116">Затем результаты могут быть привязаны к полям на экране без большого объема кода.</span><span class="sxs-lookup"><span data-stu-id="35e6d-116">The results could then be bound to fields on screen without much code.</span></span> <span data-ttu-id="35e6d-117">Недостаток этого подхода заключается в том, что каждый набор объектов ADO.NET ( `Connection` , `Command` и `Recordset` ) был привязан к библиотекам, предоставленным поставщиком базы данных.</span><span class="sxs-lookup"><span data-stu-id="35e6d-117">The drawback of this approach was that each set of ADO.NET objects (`Connection`, `Command`, and `Recordset`) was bound to libraries provided by a database vendor.</span></span> <span data-ttu-id="35e6d-118">Использование этих компонентов сделало код жестким и сложным при переходе на другую базу данных.</span><span class="sxs-lookup"><span data-stu-id="35e6d-118">Use of these components made the code rigid and difficult to migrate to a different database.</span></span>

## <a name="entity-framework"></a><span data-ttu-id="35e6d-119">Entity Framework</span><span class="sxs-lookup"><span data-stu-id="35e6d-119">Entity Framework</span></span>

<span data-ttu-id="35e6d-120">Entity Framework (EF) — это инфраструктура объектно-реляционного сопоставления с открытым исходным кодом, поддерживаемая .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="35e6d-120">Entity Framework (EF) is the open source object-relational mapping framework maintained by the .NET Foundation.</span></span> <span data-ttu-id="35e6d-121">Первоначально выпущенная с .NET Framework, EF позволяет создавать код для подключений к базе данных, схем хранилища и взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="35e6d-121">Initially released with .NET Framework, EF allows for generating code for the database connections, storage schemas, and interactions.</span></span> <span data-ttu-id="35e6d-122">Эта абстракция позволяет сосредоточиться на бизнес-правилах приложения и разрешать управление базой данных с помощью доверенного администратора базы данных.</span><span class="sxs-lookup"><span data-stu-id="35e6d-122">With this abstraction, you can focus on your app's business rules and allow the database to be managed by a trusted database administrator.</span></span> <span data-ttu-id="35e6d-123">В .NET Core можно использовать обновленную версию EF, именуемую EF Core.</span><span class="sxs-lookup"><span data-stu-id="35e6d-123">In .NET Core, you can use an updated version of EF called EF Core.</span></span> <span data-ttu-id="35e6d-124">EF Core помогает создавать и обслуживать взаимодействия между кодом и базой данных с помощью ряда команд, доступных для вас при помощи `dotnet ef` программы командной строки.</span><span class="sxs-lookup"><span data-stu-id="35e6d-124">EF Core helps generate and maintain the interactions between your code and the database with a series of commands that are available for you using the `dotnet ef` command-line tool.</span></span> <span data-ttu-id="35e6d-125">Давайте рассмотрим несколько примеров для работы с базой данных.</span><span class="sxs-lookup"><span data-stu-id="35e6d-125">Let's take a look at a few samples to get you working with a database.</span></span>

### <a name="ef-code-first"></a><span data-ttu-id="35e6d-126">EF Code First</span><span class="sxs-lookup"><span data-stu-id="35e6d-126">EF Code First</span></span>

<span data-ttu-id="35e6d-127">Чтобы быстро приступить к созданию взаимодействия с базой данных, начните с объектов класса, с которыми вы хотите работать.</span><span class="sxs-lookup"><span data-stu-id="35e6d-127">A quick way to get started building your database interactions is to start with the class objects you want to work with.</span></span> <span data-ttu-id="35e6d-128">EF предоставляет средство, помогающее создать соответствующий код базы данных для классов.</span><span class="sxs-lookup"><span data-stu-id="35e6d-128">EF provides a tool to help generate the appropriate database code for your classes.</span></span> <span data-ttu-id="35e6d-129">Этот подход называется разработкой «Code First».</span><span class="sxs-lookup"><span data-stu-id="35e6d-129">This approach is called "Code First" development.</span></span> <span data-ttu-id="35e6d-130">Рассмотрим следующий `Product` класс для примера приложения витрины, которое мы хотим хранить в реляционной базе данных, например Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="35e6d-130">Consider the following `Product` class for a sample storefront app that we want to store in a relational database like Microsoft SQL Server.</span></span>

```csharp
public class Product
{
    public int Id { get; set; }

    [Required]
    public string Name { get; set; }

    [MaxLength(4000)]
    public string Description { get; set; }

    [Range(0, 99999,99)]
    [DataType(DataType.Currency)]
    public decimal Price { get; set; }
}
```

<span data-ttu-id="35e6d-131">У продукта есть первичный ключ и три дополнительных поля, которые будут созданы в нашей базе данных:</span><span class="sxs-lookup"><span data-stu-id="35e6d-131">Product has a primary key and three additional fields that would be created in our database:</span></span>  

- <span data-ttu-id="35e6d-132">EF будет обозначать `Id` свойство как первичный ключ по соглашению.</span><span class="sxs-lookup"><span data-stu-id="35e6d-132">EF will identify the `Id` property as a primary key by convention.</span></span>
- <span data-ttu-id="35e6d-133">`Name`будет храниться в столбце, настроенном для хранения текста.</span><span class="sxs-lookup"><span data-stu-id="35e6d-133">`Name` will be stored in a column configured for text storage.</span></span> <span data-ttu-id="35e6d-134">Атрибут, определяющий `[Required]` это свойство, добавит `not null` ограничение, чтобы обеспечить соблюдение этого объявленного поведения свойства.</span><span class="sxs-lookup"><span data-stu-id="35e6d-134">The `[Required]` attribute decorating this property will add a `not null` constraint to help enforce this declared behavior of the property.</span></span>
- <span data-ttu-id="35e6d-135">`Description`будет храниться в столбце, настроенном для хранения текста, и иметь максимальную длину, настроенную на 4000 символов в соответствии с `[MaxLength]` атрибутом.</span><span class="sxs-lookup"><span data-stu-id="35e6d-135">`Description` will be stored in a column configured for text storage, and have a maximum length configured of 4000 characters as dictated by the `[MaxLength]` attribute.</span></span> <span data-ttu-id="35e6d-136">Схема базы данных будет настроена с использованием столбца с именем `MaxLength` Data Type `varchar(4000)` .</span><span class="sxs-lookup"><span data-stu-id="35e6d-136">The database schema will be configured with a column named `MaxLength` using data type `varchar(4000)`.</span></span>
- <span data-ttu-id="35e6d-137">`Price`Свойство будет храниться как валюта.</span><span class="sxs-lookup"><span data-stu-id="35e6d-137">The `Price` property will be stored as currency.</span></span> <span data-ttu-id="35e6d-138">`[Range]`Атрибут создаст соответствующие ограничения для предотвращения хранения данных за пределами минимального и максимального числа объявленных значений.</span><span class="sxs-lookup"><span data-stu-id="35e6d-138">The `[Range]` attribute will generate appropriate constraints to prevent data storage outside of the minimum and maximum values declared.</span></span>

<span data-ttu-id="35e6d-139">Нам нужно добавить этот `Product` класс в класс контекста базы данных, который определяет операции подключения и преобразования в нашей базе данных.</span><span class="sxs-lookup"><span data-stu-id="35e6d-139">We need to add this `Product` class to a database context class that defines the connection and translation operations with our database.</span></span>

```csharp
public class MyDbContext : DbContext
{
    public DbSet<Product> Products { get; set; }
}
```

<span data-ttu-id="35e6d-140">`MyDbContext`Класс предоставляет одно свойство, определяющее доступ и перевод для `Product` класса.</span><span class="sxs-lookup"><span data-stu-id="35e6d-140">The `MyDbContext` class provides the one property that defines the access and translation for the `Product` class.</span></span>  <span data-ttu-id="35e6d-141">Приложение настраивает этот класс для взаимодействия с базой данных, используя следующие записи в `Startup` `ConfigureServices` методе класса:</span><span class="sxs-lookup"><span data-stu-id="35e6d-141">Your application configures this class for interaction with the database using the following entries in the `Startup` class's `ConfigureServices` method:</span></span>

```csharp
services.AddDbContext<MyDbContext>(options =>
    options.UseSqlServer("MY DATABASE CONNECTION STRING"));
```

<span data-ttu-id="35e6d-142">Приведенный выше код будет подключаться к SQL Server базе данных с указанной строкой подключения.</span><span class="sxs-lookup"><span data-stu-id="35e6d-142">The preceding code will connect to a SQL Server database with the specified connection string.</span></span> <span data-ttu-id="35e6d-143">Строку подключения можно поместить в *appsettings.jsдля* файла, переменных среды или других мест хранения конфигурации и соответствующим образом заменить эту внедренную строку.</span><span class="sxs-lookup"><span data-stu-id="35e6d-143">You can place the connection string in your *appsettings.json* file, environment variables, or other configuration storage locations and replace this embedded string appropriately.</span></span>

<span data-ttu-id="35e6d-144">Затем можно создать таблицу базы данных, подходящую для этого класса, с помощью следующих команд:</span><span class="sxs-lookup"><span data-stu-id="35e6d-144">You can then generate the database table appropriate for this class using the following commands:</span></span>

```dotnetcli
dotnet ef migrations add 'Create Product table'
dotnet ef database update
```

<span data-ttu-id="35e6d-145">Первая команда определяет изменения, внесенные в схему базы данных в качестве новой миграции EF `Create Product table` .</span><span class="sxs-lookup"><span data-stu-id="35e6d-145">The first command defines the changes you're making to the database schema as a new EF Migration called `Create Product table`.</span></span>  <span data-ttu-id="35e6d-146">Миграция определяет способ применения и удаления новых изменений базы данных.</span><span class="sxs-lookup"><span data-stu-id="35e6d-146">A Migration defines how to apply and remove your new database changes.</span></span>

<span data-ttu-id="35e6d-147">После применения вы получите простую `Product` таблицу в базе данных и некоторые новые классы, добавленные в проект, помогающие управлять схемой базы данных.</span><span class="sxs-lookup"><span data-stu-id="35e6d-147">Once applied, you have a simple `Product` table in your database and some new classes added to the project that help manage the database schema.</span></span>  <span data-ttu-id="35e6d-148">Созданные классы по умолчанию можно найти в новой папке, именуемой *миграцией*.</span><span class="sxs-lookup"><span data-stu-id="35e6d-148">You can find these generated classes, by default, in a new folder called *Migrations*.</span></span>  <span data-ttu-id="35e6d-149">При внесении изменений в `Product` класс или добавлении дополнительных связанных классов для взаимодействия с базой данных необходимо снова выполнить команды командной строки с новым именем миграции.</span><span class="sxs-lookup"><span data-stu-id="35e6d-149">When you make changes to the `Product` class or add more related classes you would like interacting with your database, you need to run the command-line commands again with a new name of the migration.</span></span>  <span data-ttu-id="35e6d-150">Эта команда создаст другой набор классов миграции для обновления схемы базы данных.</span><span class="sxs-lookup"><span data-stu-id="35e6d-150">This command will generate another set of migration classes to update your database schema.</span></span>

### <a name="ef-database-first"></a><span data-ttu-id="35e6d-151">EF Database First</span><span class="sxs-lookup"><span data-stu-id="35e6d-151">EF Database First</span></span>

<span data-ttu-id="35e6d-152">Для существующих баз данных можно создать классы для EF Core с помощью программ командной строки .NET.</span><span class="sxs-lookup"><span data-stu-id="35e6d-152">For existing databases, you can generate the classes for EF Core by using the .NET command-line tools.</span></span> <span data-ttu-id="35e6d-153">Для формирования шаблонов классов используйте разновидность следующей команды:</span><span class="sxs-lookup"><span data-stu-id="35e6d-153">To scaffold the classes, use a variation of the following command:</span></span>

```dotnetcli
dotnet ef dbcontext scaffold "CONNECTION STRING" Microsoft.EntityFrameworkCore.SqlServer -c MyDbContext -t Product -t Customer
```

<span data-ttu-id="35e6d-154">Предыдущая команда подключается к базе данных, используя указанную строку соединения и `Microsoft.EntityFrameworkCore.SqlServer` поставщик.</span><span class="sxs-lookup"><span data-stu-id="35e6d-154">The preceding command connects to the database using the specified connection string and the `Microsoft.EntityFrameworkCore.SqlServer` provider.</span></span> <span data-ttu-id="35e6d-155">После подключения создается класс контекста базы данных с именем `MyDbContext` .</span><span class="sxs-lookup"><span data-stu-id="35e6d-155">Once connected, a database context class named `MyDbContext` is created.</span></span> <span data-ttu-id="35e6d-156">Кроме того, вспомогательные классы создаются для `Product` таблиц и `Customer` , которые были указаны с помощью `-t` параметров.</span><span class="sxs-lookup"><span data-stu-id="35e6d-156">Additionally, supporting classes are created for the `Product` and `Customer` tables that were specified with the `-t` options.</span></span> <span data-ttu-id="35e6d-157">Существует множество параметров конфигурации этой команды для создания иерархии классов, подходящей для вашей базы данных.</span><span class="sxs-lookup"><span data-stu-id="35e6d-157">There are many configuration options for this command to generate the class hierarchy appropriate for your database.</span></span> <span data-ttu-id="35e6d-158">Полный справочник см. [в документации по команде](/ef/core/miscellaneous/cli/dotnet#dotnet-ef-dbcontext-scaffold).</span><span class="sxs-lookup"><span data-stu-id="35e6d-158">For a complete reference, see [the command's documentation](/ef/core/miscellaneous/cli/dotnet#dotnet-ef-dbcontext-scaffold).</span></span>

<span data-ttu-id="35e6d-159">Дополнительные сведения о [EF Core](/ef/core/) можно найти на сайте документация Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="35e6d-159">More information about [EF Core](/ef/core/) can be found on the Microsoft Docs site.</span></span>

## <a name="interact-with-web-services"></a><span data-ttu-id="35e6d-160">Взаимодействие с веб-службами</span><span class="sxs-lookup"><span data-stu-id="35e6d-160">Interact with web services</span></span>

<span data-ttu-id="35e6d-161">При первом выпуске ASP.NET службы SOAP были предпочтительнее для веб-серверов и клиентов обмениваться данными.</span><span class="sxs-lookup"><span data-stu-id="35e6d-161">When ASP.NET was first released, SOAP services were the preferred way for web servers and clients to exchange data.</span></span> <span data-ttu-id="35e6d-162">С тех пор изменились с момента этого времени, и предпочтительные взаимодействия со службами были сдвинуты к взаимодействию с клиентами HTTP.</span><span class="sxs-lookup"><span data-stu-id="35e6d-162">Much has changed since that time, and the preferred interactions with services have shifted to direct HTTP client interactions.</span></span> <span data-ttu-id="35e6d-163">С помощью ASP.NET Core и Blazor можно зарегистрировать конфигурацию `HttpClient` в `Startup` `ConfigureServices` методе класса.</span><span class="sxs-lookup"><span data-stu-id="35e6d-163">With ASP.NET Core and Blazor, you can register the configuration of your `HttpClient` in the `Startup` class's `ConfigureServices` method.</span></span> <span data-ttu-id="35e6d-164">Используйте эту конфигурацию, когда необходимо взаимодействовать с конечной точкой HTTP.</span><span class="sxs-lookup"><span data-stu-id="35e6d-164">Use that configuration when you need to interact with the HTTP endpoint.</span></span> <span data-ttu-id="35e6d-165">Рассмотрим следующий код конфигурации:</span><span class="sxs-lookup"><span data-stu-id="35e6d-165">Consider the following configuration code:</span></span>

```csharp
services.AddHttpClient("github", client =>
{
    client.BaseAddress = new Uri("http://api.github.com/");
    // Github API versioning
    client.DefaultRequestHeaders.Add("Accept", "application/vnd.github.v3+json");
    // Github requires a user-agent
    client.DefaultRequestHeaders.Add("User-Agent", "BlazorWebForms-Sample");
});
```

<span data-ttu-id="35e6d-166">При необходимости доступа к данным из GitHub Создайте клиент с именем `github` .</span><span class="sxs-lookup"><span data-stu-id="35e6d-166">Whenever you need to access data from GitHub, create a client with a name of `github`.</span></span> <span data-ttu-id="35e6d-167">Клиент настраивается с базовым адресом, а заголовки запроса задаются соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="35e6d-167">The client is configured with the base address, and the request headers are set appropriately.</span></span> <span data-ttu-id="35e6d-168">Вставьте в `IHttpClientFactory` Blazor компоненты с помощью `@inject` директивы или `[Inject]` атрибута в свойстве.</span><span class="sxs-lookup"><span data-stu-id="35e6d-168">Inject the `IHttpClientFactory` into your Blazor components with the `@inject` directive or an `[Inject]` attribute on a property.</span></span> <span data-ttu-id="35e6d-169">Создайте именованный клиент и взаимодействуйте со службами, используя следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="35e6d-169">Create your named client and interact with services using the following syntax:</span></span>

```razor
@inject IHttpClientFactory factory

...

@code {
    protected override async Task OnInitializedAsync()
    {
        var client = factory.CreateClient("github");
        var response = await client.GetAsync("repos/dotnet/docs/issues");
        response.EnsureStatusCode();
        var content = async response.Content.ReadAsStringAsync();
    }
}
```

<span data-ttu-id="35e6d-170">Этот метод возвращает строку, описывающую коллекцию проблем в репозитории *DotNet/документацию* GitHub.</span><span class="sxs-lookup"><span data-stu-id="35e6d-170">This method returns the string describing the collection of issues in the *dotnet/docs* GitHub repository.</span></span> <span data-ttu-id="35e6d-171">Он возвращает содержимое в формате JSON и десериализуется в соответствующие объекты проблем GitHub.</span><span class="sxs-lookup"><span data-stu-id="35e6d-171">It returns content in JSON format and is deserialized into appropriate GitHub issue objects.</span></span> <span data-ttu-id="35e6d-172">Существует множество способов настройки `HttpClientFactory` для предоставления предварительно настроенных `HttpClient` объектов.</span><span class="sxs-lookup"><span data-stu-id="35e6d-172">There are many ways that you can configure the `HttpClientFactory` to deliver preconfigured `HttpClient` objects.</span></span> <span data-ttu-id="35e6d-173">Попробуйте настроить несколько `HttpClient` экземпляров с разными именами и конечными точками для различных веб-служб, с которыми вы работаете.</span><span class="sxs-lookup"><span data-stu-id="35e6d-173">Try configuring multiple `HttpClient` instances with different names and endpoints for the various web services you work with.</span></span> <span data-ttu-id="35e6d-174">Этот подход сделает взаимодействие с этими службами проще для работы на каждой странице.</span><span class="sxs-lookup"><span data-stu-id="35e6d-174">This approach will make your interactions with those services easier to work with on each page.</span></span> <span data-ttu-id="35e6d-175">Дополнительные сведения см. [в документации по ихттпклиентфактори](/aspnet/core/fundamentals/http-requests).</span><span class="sxs-lookup"><span data-stu-id="35e6d-175">For more details, read [the documentation for the IHttpClientFactory](/aspnet/core/fundamentals/http-requests).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="35e6d-176">[Назад](forms-validation.md)
>[Вперед](middleware.md)</span><span class="sxs-lookup"><span data-stu-id="35e6d-176">[Previous](forms-validation.md)
[Next](middleware.md)</span></span>
