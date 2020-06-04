---
title: Команда dotnet migrate
description: Команда dotnet migrate переносит проект и все его зависимости.
ms.date: 02/14/2020
ms.openlocfilehash: 2e7f9ae5a1d11c54280d914b04df761f0d5aff99
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284096"
---
# <a name="dotnet-migrate"></a>dotnet migrate

**Эта статья относится к следующему.** ✔️ SDK для .NET Core 2.x

## <a name="name"></a>name

`dotnet migrate` — перемещает проект .NET Core предварительной версии 2 в проект в стиле пакета SDK для .NET Core.

## <a name="synopsis"></a>Краткий обзор

```dotnetcli
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json <REPORT_FILE>]
    [-r|--report-file <REPORT_FILE>] [-s|--skip-project-references [Debug|Release]]
    [--skip-backup] [-t|--template-file <TEMPLATE_FILE>] [-v|--sdk-package-version]
    [-x|--xproj-file]

dotnet migrate -h|--help
```

## <a name="description"></a>Описание

Эта команда отключена. Команда `dotnet migrate` недоступна начиная с пакета SDK для .NET Core 3.0. Она выполняет только миграцию проекта .NET Core (предварительная версия 2) в проект .NET Core 1.x, который не поддерживается.

По умолчанию команда переносит корневой проект и все ссылки, которые он содержит. Это поведение можно отключить во время выполнения с помощью параметра `--skip-project-references`.

Миграция выполняется для следующих ресурсов:

* Отдельный проект посредством указания нужного файла *project.json*.
* Все каталоги, указанные в файле *global.json*, посредством передачи пути в файл *global.json*.
* Файл *solution.sln*, куда переносятся проекты, на которые ссылается решение.
* Рекурсивно все подкаталоги в этом каталоге.

Команда `dotnet migrate` сохраняет перенесенный файл *project.json* в каталоге `backup` (создается, если не существует). Это поведение можно переопределить с помощью параметра `--skip-backup`.

По умолчанию операция миграции выводит состояние процесса миграции в стандартный вывод (STDOUT). Если вы используете параметр `--report-file <REPORT_FILE>`, выходные данные сохраняются в указанном файле.

Команда `dotnet migrate` поддерживает только допустимые проекты предварительной версии 2 на основе *project.json*. Это означает, что она не позволяет перенести проекты DNX или проекты предварительной версии 1 на базе *project.json* непосредственно в проекты MSBuild/CSPROJ. Сначала нужно вручную перенести проект в проект версии 2 на основе *project.json*, а затем воспользоваться командой `dotnet migrate` для переноса проекта.

## <a name="arguments"></a>Аргументы

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

Путь к одному из следующих объектов:

* переносимый файл *project.json*;
* файл *global.json*: переносятся папки, указанные в *global.json*;
* файл *solution.sln*: переносятся проекты, на которые ссылается решение;
* каталог для миграции: выполняется рекурсивный поиск переносимых файлов *project.json* в указанном каталоге.

Если значение не задано, по умолчанию используется текущий каталог.

## <a name="options"></a>Параметры

`--format-report-file-json <REPORT_FILE>`

Вывод отчета о миграции в файл JSON вместо отправки сообщений пользователю.

`-h|--help`

Выводит краткую справку по команде.

`-r|--report-file <REPORT_FILE>`

Вывод отчета о миграции в файл наряду с выводом в консоль.

`-s|--skip-project-references [Debug|Release]`

Пропуск ссылок проекта для миграции. По умолчанию ссылки проекта переносятся рекурсивно.

`--skip-backup`

Пропуск перемещения *project.json*, *global.json* и *\*.xproj* в каталог `backup` после успешной миграции.

`-t|--template-file <TEMPLATE_FILE>`

Файл CSPROJ шаблона для переноса. По умолчанию используется тот же шаблон, что и проигнорированный в `dotnet new console`.

`-v|--sdk-package-version <VERSION>`

Версия пакета SDK, на которую ссылается перенесенное приложение. По умолчанию используется версия пакета SDK в `dotnet new`.

`-x|--xproj-file <FILE>`

Путь к файлу XPROJ, который будет использоваться. Требуется, если в каталоге проекта несколько файлов XPROJ.

## <a name="examples"></a>Примеры

Перенос проекта в текущем каталоге и всех взаимных зависимостей проектов.

`dotnet migrate`

Перенос всех проектов, включенных в файл *global.json*:

`dotnet migrate path/to/global.json`

Перенос только текущего проекта без взаимных зависимостей проектов. Кроме того, используется определенная версия пакета SDK:

`dotnet migrate -s -v 1.0.0-preview4`
