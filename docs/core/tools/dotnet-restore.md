---
title: Команда dotnet restore
description: Вы узнаете, как восстановить зависимости и связанные с проектом средства при помощи команды dotnet restore.
ms.date: 05/29/2018
ms.openlocfilehash: 055a4250755af02ad392877663985f86a647f892
ms.sourcegitcommit: 992f80328b51b165051c42ff5330788627abe973
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2019
ms.locfileid: "72275747"
---
# <a name="dotnet-restore"></a>dotnet restore

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>name

`dotnet restore` — восстанавливает зависимости и средства проекта.

## <a name="synopsis"></a>Краткий обзор

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```dotnetcli
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity] [--interactive]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```dotnetcli
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a>ОПИСАНИЕ

Команда `dotnet restore` использует NuGet для восстановления зависимостей, а также связанных с проектом средств, которые указаны в файле проекта. По умолчанию восстановление зависимостей и средств производится параллельно.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Для восстановления зависимостей NuGet требуются каналы, где находятся пакеты. Каналы обычно предоставляются посредством файла конфигурации *nuget.config*. Файл конфигурации по умолчанию предоставляется при установке средств CLI. Вы можете указать дополнительные веб-каналы, создав собственный файл *nuget.config* в каталоге проекта. Можно также указать дополнительные веб-каналы на вызов из командной строки.

Для зависимостей можно указать, куда помещаются восстанавливаемые пакеты во время операции восстановления, с помощью аргумента `--packages`. Если значение не указано, используется кэш пакетов NuGet по умолчанию. Он находится в каталоге `.nuget/packages` в домашнем каталоге пользователя во всех операционных системах. Например, */home/user1* на Linux или *C:\Users\user1* в Windows.

Для связанных с проектом средств `dotnet restore` сначала восстанавливает пакет, в котором упаковано средство, а затем — зависимости средства, указанные в файле проекта.

### <a name="nugetconfig-differences"></a>Различия nuget.config

На поведение команды `dotnet restore` влияют параметры в файле *nuget.config*, если он существует. Например, если установить параметр `globalPackagesFolder` в файле *nuget.config*, то восстановленные пакеты NuGet будут помещены в указанную папку. Для получения того же результата можно указать параметр `--packages` команды `dotnet restore`. Дополнительные сведения см. в [справочнике по файлу nuget.config](/nuget/schema/nuget-config-file).

Существует три конкретных параметра, которые `dotnet restore` игнорирует:

- [bindingRedirects](/nuget/schema/nuget-config-file#bindingredirects-section)

  Перенаправления привязок не работают с элементами `<PackageReference>`, а .NET Core поддерживает только элементы `<PackageReference>` для пакетов NuGet.

- [solution](/nuget/schema/nuget-config-file#solution-section)

  Этот параметр относится только к Visual Studio и не применяется к .NET Core. .NET Core не использует файл `packages.config`. Вместо этого он использует элементы `<PackageReference>` для пакетов NuGet.

- [trustedSigners](/nuget/schema/nuget-config-file#trustedsigners-section)

  Этот параметр не применяется, так как [NuGet пока не поддерживает кроссплатформенную проверку](https://github.com/NuGet/Home/issues/7939) доверенных пакетов.

## <a name="implicit-dotnet-restore"></a>Неявное выполнение `dotnet restore`

Начиная с версии .NET Core 2.0, команда `dotnet restore` выполняется неявно при выполнении следующих команд:

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

В большинстве случаев использовать команду `dotnet restore` явным образом не требуется.

Иногда неудобно запускать `dotnet restore` неявным образом. Например, некоторые автоматизированные системы, такие как системы сборки, должны явно вызывать `dotnet restore`, чтобы контролировать процесс восстановления и, следовательно, отслеживать использование сетевых ресурсов. Чтобы избежать неявного выполнения команды `dotnet restore`, с любой из приведенных выше команд можно использовать флаг `--no-restore` для отключения неявного восстановления.

## <a name="arguments"></a>Аргументы

`ROOT`

Дополнительный путь к файлу проекта для восстановления.

## <a name="options"></a>Параметры

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`--configfile <FILE>`

Файл конфигурации NuGet (*nuget.config*), используемый для операции восстановления.

`--disable-parallel`

Отключает параллельное восстановление нескольких проектов.

`--force`

Принудительное разрешение всех зависимостей, даже если последнее восстановление прошло успешно. Указание этого флага дает тот же результат, что удаление файла *project.assets.json*.

`-h|--help`

Выводит краткую справку по команде.

`--ignore-failed-sources`

Предупреждение о сбоях источников выдается только при наличии пакетов, соответствующих требованию к версии.

`--no-cache`

Отключает кэширование пакетов и HTTP-запросов.

`--no-dependencies`

При восстановлении проекта с перекрестными ссылками между проектами восстанавливает только корневой проект, но не ссылки.

`--packages <PACKAGES_DIRECTORY>`

Задает каталог для восстановленных пакетов.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Задает среду выполнения для восстановления пакетов. Это позволяет восстановить пакеты для сред выполнения, явно не указанных в теге `<RuntimeIdentifiers>` файла *CSPROJ*. Список идентификаторов сред выполнения (RID) см. в [каталоге RID](../rid-catalog.md). Чтобы указать несколько идентификаторов RID, задайте этот параметр несколько раз.

`-s|--source <SOURCE>`

Указывает источник пакета NuGet для использования во время операции восстановления. Этот параметр переопределяет все источники, указанные в файлах *nuget.config*. Чтобы указать несколько источников, задайте этот параметр несколько раз.

`--verbosity <LEVEL>`

Задает уровень детализации команды. Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`. Значение по умолчанию — `minimal`.

`--interactive`

Позволяет остановить команду и дождаться, пока пользователь введет данные или выполнит действие (например, завершит проверку подлинности). Начиная с .NET Core 2.1.400.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--configfile <FILE>`

Файл конфигурации NuGet (*nuget.config*), используемый для операции восстановления.

`--disable-parallel`

Отключает параллельное восстановление нескольких проектов.

`-h|--help`

Выводит краткую справку по команде.

`--ignore-failed-sources`

Предупреждение о сбоях источников выдается только при наличии пакетов, соответствующих требованию к версии.

`--no-cache`

Отключает кэширование пакетов и HTTP-запросов.

`--no-dependencies`

При восстановлении проекта с перекрестными ссылками между проектами восстанавливает только корневой проект, но не ссылки.

`--packages <PACKAGES_DIRECTORY>`

Задает каталог для восстановленных пакетов.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Задает среду выполнения для восстановления пакетов. Это позволяет восстановить пакеты для сред выполнения, явно не указанных в теге `<RuntimeIdentifiers>` файла *CSPROJ*. Список идентификаторов сред выполнения (RID) см. в [каталоге RID](../rid-catalog.md). Чтобы указать несколько идентификаторов RID, задайте этот параметр несколько раз.

`-s|--source <SOURCE>`

Указывает источник пакета NuGet для использования во время операции восстановления. Это переопределяет все источники, указанные в файлах *nuget.config*, фактически файл *nuget.config* считывается так, как если бы элемент `<packageSource>` отсутствовал. Чтобы указать несколько источников, задайте этот параметр несколько раз.

`--verbosity <LEVEL>`

Задает уровень детализации команды. Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`. Значение по умолчанию — `minimal`.

---

## <a name="examples"></a>Примеры

Восстановление зависимостей и средств для проекта в текущем каталоге:

`dotnet restore`

Восстановление зависимостей и средств для проекта `app1` по указанному пути:

`dotnet restore ~/projects/app1/app1.csproj`

Восстановление зависимостей и средств для проекта в текущем каталоге с использованием пути к файлу, заданного в качестве источника:

`dotnet restore -s c:\packages\mypackages`

Восстановление зависимостей и средств для проекта в текущем каталоге с использованием двух путей к файлу, заданных в качестве источника:

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

Восстановление зависимостей и средств для проекта в текущем каталоге с подробными выходными данными:

`dotnet restore --verbosity detailed`
