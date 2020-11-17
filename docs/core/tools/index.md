---
title: Интерфейс командной строки.NET
titleSuffix: ''
description: Общие сведения об интерфейсе командной строки .NET и его возможностях.
ms.topic: overview
ms.date: 02/13/2020
ms.openlocfilehash: 6a12e2d16afe36092c10e14a7465fa3bdbb23f32
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2020
ms.locfileid: "94633860"
---
# <a name="net-cli-overview"></a>Обзор интерфейса командной строки .NET

**Эта статья относится к следующему.** ✔️ SDK для .NET Core 2.1 и более поздних версий

Интерфейс командной строки (CLI) .NET — это кроссплатформенная цепочка инструментов для разработки, сборки, запуска и публикации приложений .NET.

Интерфейс командной строки .NET входит в [пакет SDK для .NET](../sdk.md). Сведения об установке пакета SDK для .NET см. в статье [Установка .NET Core](../install/windows.md).

## <a name="cli-commands"></a>Команды CLI

По умолчанию устанавливаются следующие команды:

### <a name="basic-commands"></a>Основные команды

- [`new`](dotnet-new.md)
- [`restore`](dotnet-restore.md)
- [`build`](dotnet-build.md)
- [`publish`](dotnet-publish.md)
- [`run`](dotnet-run.md)
- [`test`](dotnet-test.md)
- [`vstest`](dotnet-vstest.md)
- [`pack`](dotnet-pack.md)
- [`migrate`](dotnet-migrate.md)
- [`clean`](dotnet-clean.md)
- [`sln`](dotnet-sln.md)
- [`help`](dotnet-help.md)
- [`store`](dotnet-store.md)

### <a name="project-modification-commands"></a>Команды для изменения проекта

- [`add package`](dotnet-add-package.md)
- [`add reference`](dotnet-add-reference.md)
- [`remove package`](dotnet-remove-package.md)
- [`remove reference`](dotnet-remove-reference.md)
- [`list reference`](dotnet-list-reference.md)

### <a name="advanced-commands"></a>Расширенные команды

- [`nuget delete`](dotnet-nuget-delete.md)
- [`nuget locals`](dotnet-nuget-locals.md)
- [`nuget push`](dotnet-nuget-push.md)
- [`msbuild`](dotnet-msbuild.md)
- [`dotnet install script`](dotnet-install-script.md)

### <a name="tool-management-commands"></a>Команды управления средством

- [`tool install`](dotnet-tool-install.md)
- [`tool list`](dotnet-tool-list.md)
- [`tool update`](dotnet-tool-update.md)
- [`tool restore`](global-tools.md#install-a-local-tool) (доступна, начиная с пакета SDK для .NET Core 3.0)
- [`tool run`](global-tools.md#invoke-a-local-tool) (доступна, начиная с пакета SDK для .NET Core 3.0)
- [`tool uninstall`](dotnet-tool-uninstall.md)

Средства — это консольные приложения, которые устанавливаются из пакетов NuGet и вызываются из командной строки. Вы можете писать средства самостоятельно или устанавливать средства, написанные другими. Средства также называются глобальными средствами, средствами пути к средству и локальными средствами. Дополнительные сведения см. в [обзоре средств .NET](global-tools.md).

## <a name="command-structure"></a>Структура команд

Структура команд CLI состоит из [драйвера ("dotnet")](#driver), [самой команды](#command) и ее возможных [аргументов](#arguments) и [параметров](#options). Этот шаблон используется в большинстве операций интерфейса командной строки, таких как создание консольного приложения и его запуск из командной строки, как показывают следующие команды при выполнении из каталога *my_app*:

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a>Драйвер

Драйвер называется [dotnet](dotnet.md) и имеет два вида ответственности — выполнение [платформозависимого приложения](../deploying/index.md) или выполнение команды.

Для запуска платформозависимого приложения укажите его драйвера, например `dotnet /path/to/my_app.dll`. При выполнении команды из папки, где находится библиотека DLL приложения, просто выполните `dotnet my_app.dll`. Если вы хотите использовать конкретную версию среды выполнения .NET, используйте параметр `--fx-version <VERSION>` (см. справку по [команде dotnet](dotnet.md)).

При указании команды для драйвера `dotnet.exe` запускает процесс выполнения команды CLI. Пример:

```dotnetcli
dotnet build
```

Сначала драйвер определяет нужную версию пакета SDK. Если файл [global.json](global-json.md) отсутствует, используется последняя доступная версия пакета SDK. Это может быть предварительная или стабильная версия, в зависимости от того, какая версия является последней на компьютере.  После определения версии пакета SDK он выполняет команду.

### <a name="command"></a>Команда

Команда выполняет действие. Например, `dotnet build` проводит сборку кода. `dotnet publish` публикует код. Команды реализуются как консольное приложение с использованием соглашения `dotnet {command}`.

### <a name="arguments"></a>Аргументы

Аргументы, указываемые в командной строке, передаются непосредственно в вызываемую команду. Например, если выполнить `dotnet publish my_app.csproj`, аргумент `my_app.csproj` указывает публикуемый проект и передается в команду `publish`.

### <a name="options"></a>Параметры

Параметры, указываемые в командной строке, передаются непосредственно в вызываемую команду. Например, при выполнении `dotnet publish --output /build_output` параметр `--output` и его значение передаются в команду `publish`.

## <a name="see-also"></a>См. также

- [Репозиторий GitHub dotnet/sdk](https://github.com/dotnet/sdk/)
- [Руководство по установке .NET](../install/windows.md)
