---
title: Установка пакета SDK для .NET Core в Windows, Linux и macOS — .NET Core
description: Сведения об установке .NET Core в Windows, Linux и macOS. Узнайте о зависимостях, необходимых для разработки приложений .NET Core.
author: thraka
ms.author: adegeo
ms.date: 05/04/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 9b170765740600641f96056adc08ff0b69a03338
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768318"
---
# <a name="install-the-net-core-sdk"></a>Установка пакета SDK для .NET Core

В этой статье вы узнаете, как установить пакет SDK для .NET Core. Пакет SDK для .NET Core используется для создания приложений и библиотек .NET Core. Среда выполнения .NET Core всегда устанавливается вместе с пакетом SDK.

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a>Установка с помощью установщика

В Windows есть автономные установщики, которые можно использовать для установки пакета SDK для .NET Core 3.1:

- [Процессоры x64 (64-разрядные)](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [Процессоры x86 (32-разрядные)](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a>Установка с помощью установщика

В macOS есть автономные установщики, которые можно использовать для установки пакета SDK для .NET Core 3.1:

- [Процессоры x64 (64-разрядные)](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a>Скачивание и установка вручную

В качестве альтернативы установщикам macOS для .NET Core можно скачать и вручную установить пакет SDK.

Чтобы извлечь пакет SDK и сделать команды .NET Core CLI доступными в терминале, сначала [скачайте](#all-net-core-downloads) двоичный выпуск .NET Core. Затем откройте терминал и выполните приведенные ниже команды. Предполагается, что среда выполнения скачивается в файл `~/Downloads/dotnet-sdk.pkg`.

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-on-linux"></a>Установка на Linux

Скоро эта статья будет удалена. Вместо нее доступна статья [Установка .NET Core на Linux](linux.md).

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a>Установка с помощью Visual Studio

Если вы используете Visual Studio для разработки приложений .NET Core, в следующей таблице указана минимальная требуемая версия Visual Studio на основе целевой версии пакета SDK для .NET Core.

| Версия пакета SDK для .NET Core | Версия Visual Studio                      |
| --------------------- | ------------------------------------------ |
| 3.1                   | Visual Studio 2019 версии 16.4 или более поздней. |
| 3.0                   | Visual Studio 2019 версии 16.3 или более поздней. |
| 2.2                   | Visual Studio 2017 версии 15.9 или более поздней. |
| 2.1                   | Visual Studio 2017 версии 15.7 или более поздней. |

Если среда Visual Studio уже установлена, вы можете проверить ее версию, выполнив указанные ниже действия.

01. Запустите Visual Studio.
01. Выберите **Справка** > **О Microsoft Visual Studio**.
01. Считайте номер версии из диалогового окна **О программе**.

Visual Studio может установить последнюю пакета SDK для .NET Core и среды выполнения .NET Core.

- [Скачайте Visual Studio.](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

### <a name="select-a-workload"></a>Выбор рабочей нагрузки

При установке или изменении Visual Studio выберите одну или несколько из следующих рабочих нагрузок в зависимости от типа создаваемого приложения:

- рабочая нагрузка **Кроссплатформенная разработка .NET Core** в разделе **Другие наборы инструментов**;
- рабочая нагрузка **ASP.NET и разработка веб-приложений** в разделе **Веб-разработка и облако**;
- рабочая нагрузка **Разработка для Azure** в разделе **Веб-разработка и облако**;
- рабочая нагрузка **Разработка классических приложений .NET** в разделе **Классические и мобильные**.

[![Windows Visual Studio 2019 с рабочей нагрузкой .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

## <a name="download-and-manually-install"></a>Скачивание и установка вручную

Чтобы извлечь среду выполнения и сделать команды .NET Core CLI доступными в терминале, сначала [скачайте](#all-net-core-downloads) двоичный выпуск .NET Core. Затем создайте каталог в котором будете выполнять установку, например `%USERPROFILE%\dotnet`. Наконец, извлеките скачанный ZIP-файл в этот каталог.

По умолчанию команды и приложения .NET Core CLI не будут использовать платформу .NET Core, установленную таким образом. Вам нужно выбрать ее явно. Для этого измените переменные среды, с которыми запускается приложение:

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

Такой подход позволяет установить несколько версий в отдельные расположения, а затем явно выбрать расположение установки, которое должно использовать приложение, запустив приложение с переменными среды, указывающими на это расположение.

Даже если эти переменные среды заданы, .NET Core по-прежнему учитывает глобальное расположение установки по умолчанию при выборе лучшей платформы для запуска приложения. По умолчанию обычно это расположение `C:\Program Files\dotnet`, которое используют установщики. Вы можете указать среде выполнения использовать только пользовательское расположение установки, задав эту переменную среды.

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a>Установка с помощью Visual Studio для Mac

Visual Studio для Mac устанавливает пакет SDK для .NET Core, если выбрана рабочая нагрузка **.NET Core**. Чтобы приступить к разработке в .NET Core на macOS, ознакомьтесь со статьей [Установка Visual Studio 2019 для Mac](/visualstudio/mac/installation). В последнем выпуске .NET Core 3.1 необходимо использовать предварительную версию Visual Studio для Mac 8.4.

[![Visual Studio 2019 для Mac с компонентом рабочей нагрузки .NET Core в macOS](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)

::: zone-end

::: zone pivot="os-windows,os-macos"

## <a name="install-alongside-visual-studio-code"></a>Установка вместе с Visual Studio Code

Visual Studio Code — это эффективный и облегченный редактор исходного кода, который работает на компьютере. Visual Studio Code доступен для Windows, macOS и Linux.

Хотя Visual Studio Code не поставляется с автоматическим установщиком .NET Core, таким как Visual Studio, добавление поддержки .NET Core не вызывает затруднений.

01. [Скачайте и установите Visual Studio Code](https://code.visualstudio.com/Download).
01. [Скачайте и установите пакет SDK для .NET Core](https://dotnet.microsoft.com/download/dotnet-core).
01. [Установите расширение C# из Marketplace для Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>Установка с помощью функции автоматизации PowerShell

[Сценарии dotnet-install](../tools/dotnet-install-script.md) используются для автоматизации установок пакета SDK и их осуществления без прав администратора. Вы можете скачать сценарий со [страницы справочника по сценариям dotnet-install](../tools/dotnet-install-script.md).

Этот сценарий по умолчанию устанавливает последнюю версию [с долгосрочной поддержкой (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core), которой сейчас является .NET Core 3.1. Чтобы установить текущий выпуск .NET Core, запустите сценарий с указанным ниже параметром.

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-bash-automation"></a>Установка с помощью функции автоматизации Bash

[Сценарии dotnet-install](../tools/dotnet-install-script.md) используются для автоматизации установок пакета SDK и их осуществления без прав администратора. Вы можете скачать сценарий со [страницы справочника по сценариям dotnet-install](../tools/dotnet-install-script.md).

Этот сценарий по умолчанию устанавливает последнюю версию [с долгосрочной поддержкой (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core), которой сейчас является .NET Core 3.1. Чтобы установить текущий выпуск .NET Core, запустите сценарий с указанным ниже параметром.

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a>Все скачиваемые файлы для .NET Core

Вы можете скачать и установить .NET Core напрямую, используя одну из следующих ссылок:

- [Скачиваемые файлы для .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [Скачиваемые файлы для .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [Скачиваемые файлы для .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [Скачиваемые файлы для .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

Контейнеры обеспечивают простой способ изоляции приложения от остальной части основной системы. Контейнеры на одном компьютере совместно использую только ядро, а также используют ресурсы, которые передаются в приложение.

.NET Core можно выполнять в контейнере Docker. Официальные образы Docker для .NET Core публикуются в реестре контейнеров Microsoft (MCR) и доступ к ним можно получить в [репозитории Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/). Каждый репозиторий содержит рабочие образы для разных сочетаний .NET (пакета SDK или среды выполнения) и операционной системы.

Корпорация Майкрософт предоставляет образы, которые предназначены для конкретных сценариев. Например [репозиторий ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) содержит образы, которые предназначены для запуска приложений ASP.NET Core в рабочей среде.

Дополнительные сведения об использовании .NET Core в контейнере Docker см. в статьях [Введение в .NET и Docker](../docker/introduction.md) и [Примеры](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>Следующие шаги

::: zone pivot="os-windows"

- [Учебник. Hello World](../tutorials/with-visual-studio.md).
- [Учебник. Создание приложения с помощью Visual Studio Code](../tutorials/with-visual-studio-code.md).
- [Учебник. Контейнеризация приложения .NET Core](../docker/build-container.md).

::: zone-end

::: zone pivot="os-macos"

- [Работа с заверением macOS Catalina](macos-notarization-issues.md).
- [Учебник. Начало работы с macOS](../tutorials/using-on-mac-vs.md).
- [Учебник. Создание приложения с помощью Visual Studio Code](../tutorials/with-visual-studio-code.md).
- [Учебник. Контейнеризация приложения .NET Core](../docker/build-container.md).

::: zone-end

::: zone pivot="os-linux"

- [Учебник. Создание приложения с помощью Visual Studio Code](../tutorials/with-visual-studio-code.md).
- [Учебник. Контейнеризация приложения .NET Core](../docker/build-container.md).

::: zone-end
