---
title: Процесс разработки для приложений на основе Docker
description: Общий обзор возможностей для разработки приложений Docker. Использование Visual Studio для Windows, Visual Studio для Mac и Visual Studio Code для поддержки нескольких платформ (Windows, Mac и Linux).
ms.date: 09/27/2018
ms.openlocfilehash: a32b27f3d98ed7ebf63b637ec0c979c22ee8e1e8
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295141"
---
# <a name="development-process-for-docker-based-applications"></a>Процесс разработки для приложений на основе Docker

*Вы можете разрабатывать контейнерные приложения .NET так, как вам нравится: либо с помощью интегрированной среды разработки (IDE) Visual Studio и Средств Visual Studio для Docker, либо с помощью интерфейса командной строки (CLI) и редактора — CLI Docker и Visual Studio Code.*

## <a name="development-environment-for-docker-apps"></a>Среда разработки приложений Docker

### <a name="development-tool-choices-ide-or-editor"></a>Выбор средства разработки: интегрированная среда разработки или редактор

Предпочитаете ли вы использовать полнофункциональную среду IDE или упрощенный редактор, корпорация Майкрософт предлагает средства, с помощью которых можно разрабатывать приложения Docker.

**Visual Studio (для Windows).** При разработке приложений Docker с помощью Visual Studio, мы рекомендуем использовать Visual Studio 2017 начиная с версии 15.7. Этот инструмент уже встроен в средства для Docker. Средства для Docker позволяют разрабатывать, запускать и проверять приложения непосредственно в целевой среде Docker. Нажмите клавишу F5 для запуска и отладки приложения (на основе одного контейнера или нескольких) непосредственно в узле Docker или нажмите клавиши CTRL+F5 для редактирования и обновления приложения без повторной сборки контейнера. Это самый эффективный вариант разработки приложений на основе Docker.

**Visual Studio для Mac.** Это интегрированная среда разработки, дальнейшее развитие Xamarin Studio, которая работает в macOS и поддерживает Docker с середины 2017 года. Она должна быть предпочтительным вариантом для разработчиков, работающих на компьютерах Mac и стремящихся использовать мощную интегрированную среду разработки.

**Visual Studio Code и CLI Docker**. Если вам нужен упрощенный кроссплатформенный редактор, поддерживающий любой язык программирования, то вы можете использовать Microsoft Visual Studio Code (VS Code) и CLI Docker. Таким образом реализуется кроссплатформенный подход к разработке приложений для Mac OS, Linux и Windows. Кроме того, Visual Studio Code поддерживает расширения для Docker, такие как IntelliSense для Dockerfile, и ярлыки для выполнения команд Docker из редактора.

Установив [Docker Desktop Community Edition (CE)](https://hub.docker.com/search/?type=edition&offering=community), вы можете использовать единый интерфейс CLI Docker, чтобы создавать приложения как для Windows, так и для Linux.

### <a name="additional-resources"></a>Дополнительные ресурсы

- **Visual Studio**. Официальный сайт \
  [https://visualstudio.microsoft.com/vs/](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

- **Visual Studio Code**. Официальный сайт \
  <https://code.visualstudio.com/download>

- **Docker Desktop for Windows Community Edition (CE)**  \
  [https://hub.docker.com/editions/community/docker-ce-desktop-windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
  
- **Docker Desktop for Mac Community Edition (CE)**  \
  [https://hub.docker.com/editions/community/docker-ce-desktop-mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>Языки и платформы .NET для контейнеров Docker

Как уже упоминалось в предыдущих разделах этого руководства, при разработке приложений .NET, помещенных в контейнеры Docker, можно использовать .NET Framework, .NET Core или проект Mono с открытым кодом. При разработке приложений на основе контейнеров Linux или Windows можно использовать язык C\#, F\# или Visual Basic в зависимости от применяемой платформы .NET. Дополнительные сведения о языках .NET см. в записи блога [Стратегия .NET в отношении языков](https://devblogs.microsoft.com/dotnet/the-net-language-strategy/).

>[!div class="step-by-step"]
>[Назад](../architect-microservice-container-applications/scalable-available-multi-container-microservice-applications.md)
>[Вперед](docker-app-development-workflow.md)
