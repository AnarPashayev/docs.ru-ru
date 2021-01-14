---
title: Структура проекта для Blazor приложений
description: Узнайте, как сравниваются структуры проекта веб-форм и Blazor проектов ASP.NET.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 11/20/2020
ms.openlocfilehash: ba7113c88db728f30812821deaf7c06a80663d1f
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189093"
---
# <a name="project-structure-for-no-locblazor-apps"></a>Структура проекта для Blazor приложений

Несмотря на существенные различия в структуре проекта, ASP.NET веб-формы и Blazor совместно используют многие схожие концепции. Здесь мы рассмотрим структуру Blazor проекта и сравнив ее с проектом веб-форм ASP.NET.

Чтобы создать свое первое Blazor приложение, следуйте инструкциям в [ Blazor статье Приступая к работе](/aspnet/core/blazor/get-started). Вы можете выполнить инструкции, чтобы создать Blazor серверное приложение или приложение, Blazor WebAssembly размещенное в ASP.NET Core. За исключением логики размещения для конкретной модели, большая часть кода в обоих проектах одинакова.

## <a name="project-file"></a>Файл проекта

Blazor Серверные приложения — это проекты .NET. Файл проекта для Blazor серверного приложения примерно так прост, как он может получить:

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Файл проекта Blazor WebAssembly приложения выглядит немного подробнее (точный номер версии может отличаться):

```xml
<Project Sdk="Microsoft.NET.Sdk.BlazorWebAssembly">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Components.WebAssembly" Version="5.0.0" />
    <PackageReference Include="Microsoft.AspNetCore.Components.WebAssembly.DevServer" Version="5.0.0" PrivateAssets="all" />
    <PackageReference Include="System.Net.Http.Json" Version="5.0.0" />
  </ItemGroup>

</Project>
```

BlazorWebAssemblyпроект ориентирован `Microsoft.NET.Sdk.BlazorWebAssembly` вместо `Microsoft.NET.Sdk.Web` пакета SDK, так как они выполняются в браузере в WebAssembly среде выполнения .NET на основе. Вы не можете установить .NET в веб-браузер, как на сервере или на компьютере разработчика. Следовательно, проект ссылается на Blazor платформу, используя отдельные ссылки на пакеты.

По сравнению, проект веб-форм ASP.NET по умолчанию включает в себя почти 300 строк XML в файле *. csproj* , большинство из которых явно задает в проекте различные файлы кода и содержимого. С выпуском `.NET 5` `Blazor Server` и приложением, и `Blazor WebAssembly` приложение может легко совместно использовать одну единую среду выполнения.

Хотя они поддерживаются, отдельные ссылки на сборки менее распространены в проектах .NET. Большинство зависимостей проектов обрабатываются как ссылки на пакеты NuGet. В проектах .NET необходимо ссылаться только на зависимости пакетов верхнего уровня. Транзитивные зависимости включаются автоматически. Вместо того чтобы использовать файл *packages.config* , который часто встречаются в проектах веб-форм ASP.NET для ссылки на пакеты, ссылки на пакет добавляются в файл проекта с помощью `<PackageReference>` элемента.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a>Точка входа

BlazorТочка входа серверного приложения определяется в файле *Program.CS* , как показано в консольном приложении. При выполнении приложения он создает и запускает экземпляр веб-узла с использованием значений по умолчанию, относящихся к веб-приложениям. Веб-узел управляет Blazor жизненным циклом серверного приложения и настраивает службы на уровне узла. Примерами таких служб являются конфигурация, ведение журнала, внедрение зависимостей и HTTP-сервер. Этот код в основном является шаблоном, и часто остается без изменений.

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        CreateHostBuilder(args).Build().Run();
    }

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureWebHostDefaults(webBuilder =>
            {
                webBuilder.UseStartup<Startup>();
            });
}
```

BlazorWebAssemblyприложения также определяют точку входа в *Program.CS*. Код выглядит немного иначе. Код аналогичен тому, что настраивает узел приложения для предоставления приложению тех же служб уровня узла. WebAssemblyУзел приложения, однако, не настраивает HTTP-сервер, так как он выполняется непосредственно в браузере.

Blazor приложения имеют `Startup` класс, а не файл *Global. asax* для определения логики запуска приложения. `Startup`Класс используется для настройки приложения и всех служб, зависящих от приложения. В Blazor серверном приложении `Startup` класс используется для настройки конечной точки для соединения в режиме реального времени, используемого Blazor между клиентскими браузерами и сервером. В Blazor WebAssembly приложении `Startup` класс определяет корневые компоненты приложения и место, где они должны быть подготовлены к просмотру. Мы подробнее рассмотрим `Startup` класс в разделе [Запуск приложения](./app-startup.md) .

## <a name="static-files"></a>Статические файлы

В отличие от проектов веб-форм ASP.NET, не все файлы Blazor проекта могут запрашиваться как статические файлы. Веб-адресацией могут быть только файлы в папке *wwwroot* . Эта папка называется "корневым веб-приложением". Все, что находится за пределами корневого веб-узла приложения, *не является* веб-адресацией. Эта установка обеспечивает дополнительный уровень безопасности, который предотвращает случайное предоставление файлов проекта через Интернет.

## <a name="configuration"></a>Конфигурация

Конфигурация в приложениях ASP.NET Web Forms обычно обрабатывается с помощью одного или нескольких файлов *web.config* . Blazor приложения обычно не имеют *web.config* файлов. В противном случае файл будет использоваться только для настройки параметров IIS при размещении в службах IIS. Вместо этого Blazor серверные приложения используют абстракции конфигурации ASP.NET Core ( Blazor WebAssembly приложения в настоящее время не поддерживают одни и те же абстракции конфигурации, но это может быть функция, добавленная в будущем). Например, Blazor серверное приложение по умолчанию хранит некоторые параметры в *appsettings.js*.

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "AllowedHosts": "*"
}
```

Дополнительные сведения о конфигурации в ASP.NET Core проектах см. в разделе [конфигурации](./config.md) .

## <a name="razor-components"></a>Компоненты Razor

Большинство файлов в Blazor проектах являются файлами *. Razor* . Razor — это язык шаблонов, основанный на HTML и C#, который используется для динамического создания пользовательского веб-интерфейса. Файлы *. Razor* определяют компоненты, составляющие пользовательский интерфейс приложения. В большинстве случаев компоненты идентичны как для Blazor сервера, так и для Blazor WebAssembly приложений. Компоненты в Blazor являются аналогом пользовательских элементов управления в веб-формах ASP.NET.

Каждый файл компонента Razor компилируется в класс .NET при построении проекта. Созданный класс захватывает состояние компонента, логику отрисовки, методы жизненного цикла, обработчики событий и другую логику. Мы рассмотрим создание компонентов [пользовательского интерфейса с возможностью повторного использования с помощью Blazor ](./components.md) раздела.

Файлы *_Imports. Razor* не являются файлами компонентов Razor. Вместо этого они определяют набор директив Razor для импорта в другие файлы *Razor* в той же папке и ее вложенных папках. Например, файл *_Imports. Razor* — это стандартный способ добавления `using` директив для часто используемых пространств имен:

```razor
@using System.Net.Http
@using Microsoft.AspNetCore.Authorization
@using Microsoft.AspNetCore.Components.Authorization
@using Microsoft.AspNetCore.Components.Forms
@using Microsoft.AspNetCore.Components.Routing
@using Microsoft.AspNetCore.Components.Web
@using Microsoft.JSInterop
@using BlazorApp1
@using BlazorApp1.Shared
```

## <a name="pages"></a>Pages

Где находятся страницы в Blazor приложениях? Blazor не определяет отдельное расширение файла для адресных страниц, например *ASPX* -файлы в ASP.NET Web Forms. Вместо этого страницы определяются путем назначения маршрутов компонентам. Маршрут обычно назначается с помощью `@page` директивы Razor. Например, компонент, `Counter` созданный в файле *pages/Counter. Razor* , определяет следующий маршрут:

```razor
@page "/counter"
```

Маршрутизация в Blazor обрабатывается на стороне клиента, а не на сервере. При переходе пользователя в браузере Blazor перехватывает навигацию, а затем отображает компонент с соответствующим маршрутом.

Маршруты к компонентам в настоящее время не выводятся расположением файлов компонента, как и страницы *ASPX* . Эта функция может быть добавлена в будущем. Каждый маршрут должен быть явно указан в компоненте. Хранение маршрутизируемых компонентов в папке *pages* не имеет особого смысла и является исключительно Соглашением.

Мы более подробно рассмотрим маршрутизацию в Blazor разделе [страницы, маршрутизация и макеты](./pages-routing-layouts.md) .

## <a name="layout"></a>Layout

В приложениях ASP.NET Web Forms общий макет страницы обрабатывается с помощью главных страниц (*site. master*). В Blazor приложениях макет страницы обрабатывается с помощью компонентов макета (*Shared/маинлайаут. Razor*). Компоненты макета будут обсуждаться более подробно в разделе [страница, маршрутизация и макеты](./pages-routing-layouts.md) .

## <a name="bootstrap-no-locblazor"></a>Загрузке Blazor

Для начальной загрузки Blazor приложение должно:

- Укажите, где на странице следует визуализировать корневой компонент (*app. Razor*).
- Добавьте соответствующий Blazor скрипт платформы.

В Blazor серверном приложении страница узла корневого компонента определена в файле *_Host. cshtml* . Этот файл определяет страницу Razor, а не компонент. Razor Pages использовать синтаксис Razor для определения серверной страницы, которая во многом аналогична странице *. aspx* . `Html.RenderComponentAsync<TComponent>(RenderMode)`Метод используется для определения места, где должен быть визуализирован компонент корневого уровня. `RenderMode`Параметр указывает способ подготовки компонента к просмотру. В следующей таблице приведены поддерживаемые `RenderMode` Параметры.

|Параметр                        |Описание       |
|------------------------------|------------------|
|`RenderMode.Server`           |Интерактивный просмотр после установки соединения с браузером|
|`RenderMode.ServerPrerendered`|Первая предварительно визуализированная и отображаемая в интерактивном режиме|
|`RenderMode.Static`           |Отображается как статическое содержимое|

Ссылка на скрипт для *_framework/blazor.server.js* устанавливает подключение к серверу в режиме реального времени, а затем обрабатывает все взаимодействия с пользователем и обновления пользовательского интерфейса.

```razor
@page "/"
@namespace BlazorApp1.Pages
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>BlazorApp1</title>
    <base href="~/" />
    <link rel="stylesheet" href="css/bootstrap/bootstrap.min.css" />
    <link href="css/site.css" rel="stylesheet" />
</head>
<body>
    <app>
        @(await Html.RenderComponentAsync<App>(RenderMode.ServerPrerendered))
    </app>

    <script src="_framework/blazor.server.js"></script>
</body>
</html>
```

В Blazor WebAssembly приложении страница узла представляет собой простой статический HTML-файл в каталоге *wwwroot/index.html*. `<div>`Элемент с именем ID `app` используется для указания места, где должен быть визуализирован корневой компонент.

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
    <title>BlazorApp2</title>
    <base href="/" />
    <link href="css/bootstrap/bootstrap.min.css" rel="stylesheet" />
    <link href="css/app.css" rel="stylesheet" />
    <link href="blazor-web.styles.css" rel="stylesheet" />
</head>

<body>
    <div id="app">Loading...</div>

    <div id="blazor-error-ui">
        An unhandled error has occurred.
        <a href="" class="reload">Reload</a>
        <a class="dismiss">🗙</a>
    </div>
    <script src="_framework/blazor.webassembly.js"></script>
</body>

</html>

```

Корневой компонент для подготовки к просмотру указывается в `Program.Main` методе приложения с гибкостью для регистрации служб посредством внедрения зависимостей. Дополнительные сведения см. в разделе [ASP.NET Core Blazor внедрения зависимостей](/aspnet/core/blazor/fundamentals/dependency-injection?pivots=webassembly).

```csharp
public class Program
{
    public static async Task Main(string[] args)
    {
        var builder = WebAssemblyHostBuilder.CreateDefault(args);
        builder.RootComponents.Add<App>("#app");

        ....
        ....
    }
}
```

## <a name="build-output"></a>Выходные данные при создании

При Blazor сборке проекта все файлы компонента и кода Razor компилируются в одну сборку. В отличие от проектов веб-форм ASP.NET Blazor не поддерживает компиляцию логики пользовательского интерфейса во время выполнения.

## <a name="run-the-app"></a>Запуск приложения

Чтобы запустить Blazor серверное приложение, нажмите `F5` в Visual Studio. Blazor приложения не поддерживают компиляцию во время выполнения. Чтобы просмотреть результаты изменений разметки кода и компонентов, перестройте и перезапустите приложение с подключенным отладчиком. Если запустить без отладчика ( `Ctrl+F5` ), Visual Studio следит за изменениями файлов и перезапускает приложение при внесении изменений. Вы вручную обновляете браузер по мере внесения изменений.

Чтобы запустить Blazor WebAssembly приложение, выберите один из следующих подходов:

- Запустите клиентский проект непосредственно с помощью сервера разработки.
- Запустите серверный проект при размещении приложения с ASP.NET Core.

BlazorWebAssemblyприложения можно отлаживать как в браузере, так и в Visual Studio. Дополнительные сведения см. в [ASP.NET Core Blazor WebAssembly отладки](/aspnet/core/blazor/debug) .

>[!div class="step-by-step"]
>[Назад](hosting-models.md)
>[Вперед](app-startup.md)
