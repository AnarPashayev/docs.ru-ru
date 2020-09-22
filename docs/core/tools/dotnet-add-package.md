---
title: Команда dotnet add package
description: Команду dotnet add package удобно использовать для добавления ссылки на пакет NuGet в проект.
ms.date: 02/14/2020
ms.openlocfilehash: 1bdda241c1301b926ba2fd322f969407038b7b62
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538072"
---
# <a name="dotnet-add-package"></a>dotnet add package

**Эта статья относится к следующему:** ✔️ пакет SDK для .NET Core 2.x и более поздних версий

## <a name="name"></a>name

`dotnet add package` — добавляет ссылку на пакет в файл проекта.

## <a name="synopsis"></a>Краткий обзор

```dotnetcli
dotnet add [<PROJECT>] package <PACKAGE_NAME>
    [-f|--framework <FRAMEWORK>] [--interactive]
    [-n|--no-restore] [--package-directory <PACKAGE_DIRECTORY>]
    [-s|--source <SOURCE>] [-v|--version <VERSION>]

dotnet add package -h|--help
```

## <a name="description"></a>Описание

Команда `dotnet add package` предоставляет удобный способ для добавления ссылки на пакет в файл проекта. После запуска этой команды выполняется проверка совместимости, чтобы убедиться, что пакет совместим со всеми платформами в проекте. Если проверка проходит успешно, в файл проекта добавляется элемент `<PackageReference>` и выполняется команда [dotnet restore](dotnet-restore.md).

Например, при добавлении `Newtonsoft.Json` в *ToDo.csproj* создаются выходные данные примерно следующего вида:

```console
Writing C:\Users\me\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\Temp\projects\consoleproj\consoleproj.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 79ms
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg 232ms
log  : Installing Newtonsoft.Json 12.0.1.
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '12.0.1' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

Файл *ToDo.csproj* теперь содержит элемент [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) для пакета, на который указывает ссылка.

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

### <a name="implicit-restore"></a>Неявное восстановление

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

## <a name="arguments"></a>Аргументы

- **`PROJECT`**

  Указывает файл проекта. Если он не указан, команда ищет текущий каталог для него.

- **`PACKAGE_NAME`**

  Добавляемая ссылка на пакет.

## <a name="options"></a>Параметры

- **`-f|--framework <FRAMEWORK>`**

  Добавляет ссылку на пакет только при ориентации на конкретную [платформу](../../standard/frameworks.md).

- **`-h|--help`**

  Выводит краткую справку по команде.

- **`--interactive`**

  Позволяет остановить команду и дождаться, пока пользователь введет данные или выполнит действие (например, завершит проверку подлинности). Доступно с версии пакета SDK 2.1 для .NET Core версии 2.1.400 или более поздней версии.

- **`-n|--no-restore`**

  Добавляет ссылку на пакет без предварительного просмотра восстановления и проверки совместимости.

- **`--package-directory <PACKAGE_DIRECTORY>`**

  Каталог, в который нужно восстановить пакеты. Расположение по умолчанию для восстановления пакетов — `%userprofile%\.nuget\packages` в Windows и `~/.nuget/packages` в macOS и Linux. Дополнительные сведения см. в статье [Управление папкой установки глобальных пакетов, кэшем и временными папками](/nuget/consume-packages/managing-the-global-packages-and-cache-folders).

- **`-s|--source <SOURCE>`**

  URI источника пакета NuGet для использования во время операции восстановления.

- **`-v|--version <VERSION>`**

  Версия пакета. См. статью [Package versioning](/nuget/reference/package-versioning) (Управление версиями пакета).

## <a name="examples"></a>Примеры

- Добавление пакета NuGet `Newtonsoft.Json` в проект:

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- Добавление определенной версии пакета в проект:

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- Добавление пакета с помощью определенного источника NuGet:

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a>См. также

- [Управление папкой установки глобальных пакетов, кэшем и временными папками](/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [Управление версиями пакета NuGet](/nuget/reference/package-versioning)
