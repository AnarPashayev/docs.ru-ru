---
title: Публикация приложения Hello World .NET Core в Visual Studio 2017
description: При публикации создается набор файлов, которые необходимы для запуска приложения .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: f8c37f47cc8dfb999f2371773a50c2dd91e074a5
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660479"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio-2017"></a>Публикация приложения Hello World .NET Core в Visual Studio 2017

Изучая руководство [Создание приложения Hello World на C# с помощью .NET Core в Visual Studio 2017](with-visual-studio.md) или [Создание приложения Hello World на Visual Basic с помощью .NET Core в Visual Studio 2017](vb-with-visual-studio.md), вы создали консольное приложение Hello World. В следующем руководстве [Отладка приложения Hello World на C# в Visual Studio 2017](debugging-with-visual-studio.md) вы протестировали его с помощью отладчика Visual Studio. Теперь вы уверены, что приложение работает правильно, и его можно опубликовать для выполнения другими пользователями. При публикации создается набор файлов, которые необходимы для запуска приложения. Чтобы развернуть приложение, скопируйте эти файлы на целевой компьютер.

Действия для публикации и запуска приложения. 

1. Убедитесь, что в Visual Studio настроен режим сборки для версии выпуска. При необходимости измените конфигурацию сборки на панели инструментов, указав конфигурацию **Выпуск** вместо конфигурации **Отладка**.

   ![Панель инструментов Visual Studio с выбранной сборкой выпуска](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. Щелкните проект **HelloWorld** (не решение HelloWorld) правой кнопкой мыши и выберите **Опубликовать**. Также можно выбрать **Публикация HelloWorld** из раздела **Сборка** в главном меню Visual Studio.

   ![Контекстное меню "Опубликовать" в Visual Studio](media/publishing-with-visual-studio/publish-context-menu.png)

   ![Окно публикации в Visual Studio](media/publishing-with-visual-studio/publish-settings-window.png)

1. Откройте окно консоли. Например, в текстовом поле **Введите здесь текст для поиска** на панели задач Windows введите `Command Prompt` (или `cmd` для краткости), а затем откройте окно консоли с помощью приложения **командной строки** или клавиши ВВОД, если оно выделено в результатах поиска.

1. Перейдите к опубликованному приложению в подкаталоге `bin\release\PublishOutput` проекта приложения. Как показано на следующем рисунке, опубликованные выходные данные включают следующие четыре файла:

      * *HelloWorld.deps.json*

         Файл зависимостей времени выполнения для приложения. Он определяет библиотеки и компоненты .NET Core (включая библиотеку DLL, содержащую приложение), необходимые для запуска приложения. Дополнительные сведения см. в разделе [Файлы конфигурации среды выполнения](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).
 
      * *HelloWorld.dll*

         Файл, содержащий ваше приложение. Это библиотеки DLL, которую можно выполнить, введя команду `dotnet HelloWorld.dll` в окне консоли. 

      * *HelloWorld.pdb* (необязателен для развертывания)

         Файл, содержащий отладочные символы. Этот файл не нужно распространять вместе с приложением, но желательно сохранить его на случай, если придется выполнять отладку опубликованной версии приложения.

      * *HelloWorld.runtimeconfig.json*

         Файл конфигурации времени выполнения для приложения. Он определяет версию платформы .NET Core, для которой предназначено приложение. Дополнительные сведения см. в разделе [Файлы конфигурации среды выполнения](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).  

   ![Окно консоли с опубликованными файлами](media/publishing-with-visual-studio/published-files-output.png)

В ходе публикации создается платформенно-зависимое развертывание. При таком развертывании опубликованное приложение будет выполняться на любой платформе, поддерживаемой .NET Core, при условии, что платформа .NET Core установлена в системе. Пользователи могут запускать приложение командой `dotnet HelloWorld.dll` из окна консоли.

Дополнительные сведения о публикации и развертывании приложений .NET Core см. в статье [Развертывание приложений .NET Core](../deploying/index.md).
