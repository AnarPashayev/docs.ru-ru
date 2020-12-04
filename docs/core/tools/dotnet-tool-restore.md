---
title: Команда dotnet tool restore
description: Команда dotnet tool restore устанавливает на компьютере локальные средства .NET, которые доступны для текущего каталога.
ms.date: 02/14/2020
ms.openlocfilehash: 3425bc6b78fd53f578c209013f83b006305dbb81
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242933"
---
# <a name="dotnet-tool-restore"></a>dotnet tool restore

**Эта статья относится к следующему.** ✔️ SDK для .NET Core 3.0 и более поздних версий

## <a name="name"></a>name

`dotnet tool restore` — устанавливает локальные средства .NET, которые доступны для текущего каталога.

## <a name="synopsis"></a>Краткий обзор

```dotnetcli
dotnet tool restore
    [--configfile <FILE>] [--add-source <SOURCE>]
    [tool-manifest <PATH_TO_MANIFEST_FILE>] [--disable-parallel]
    [--ignore-failed-sources] [--no-cache] [--interactive]
    [-v|--verbosity <LEVEL>]

dotnet tool restore -h|--help
```

## <a name="description"></a>Описание

Команда `dotnet tool restore` находит файл манифеста средства, который доступен для текущего каталога, и устанавливает перечисленные в нем средства. Сведения о файлах манифеста см. в разделе [Установка локального средства](global-tools.md#install-a-local-tool) и [Вызов локального средства](global-tools.md#invoke-a-local-tool).

## <a name="options"></a>Параметры

- **`--configfile <FILE>`**

  Файл конфигурации NuGet (*nuget.config*), который будет использоваться.

- **`--add-source <SOURCE>`**

  Добавляет дополнительный источник пакета NuGet для использования во время установки.

- **`--tool-manifest <PATH>`**

  Путь к файлу манифеста.

- **`--disable-parallel`**

  Блокирует параллельное восстановление множества проектов.

- **`--ignore-failed-sources`**

  Обрабатывать сбои источников пакетов как предупреждения.

- **`--no-cache`**

  Не кэшировать пакеты и HTTP-запросы.

- **`--interactive`**

  Позволяет остановить команду и дождаться, пока пользователь введет данные или выполнит действие (например, завершит проверку подлинности).

- **`-h|--help`**

  Выводит краткую справку по команде.

- **`-v|--verbosity <LEVEL>`**

  Задает уровень детализации команды. Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`.

## <a name="example"></a>Пример

- **`dotnet tool restore`**

  Восстанавливает локальные средства для текущего каталога.

## <a name="see-also"></a>См. также

- [Средства .NET](global-tools.md)
- [Учебник. Установка и использование локального средства .NET с помощью интерфейса командной строки .NET](local-tools-how-to-use.md)
