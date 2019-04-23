---
title: Руководство по .NET Core
description: .NET Core — это модульная высокопроизводительная реализация .NET для создания приложений Windows, Linux и Mac. Для начала получите дополнительную информацию о .NET Core.
author: richlander
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: 79a0c09074159160dd01b0c7970612f7058cc3fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614457"
---
# <a name="net-core-guide"></a><span data-ttu-id="2e19a-104">Руководство по .NET Core</span><span class="sxs-lookup"><span data-stu-id="2e19a-104">.NET Core Guide</span></span>

<span data-ttu-id="2e19a-105">[.NET Core](about.md) — это универсальная платформа разработки с [открытым кодом](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), которую поддерживает корпорация Майкрософт и сообщество .NET на сайте [GitHub](https://github.com/dotnet/core).</span><span class="sxs-lookup"><span data-stu-id="2e19a-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="2e19a-106">Она является кроссплатформенной (поддерживает Windows, macOS и Linux) и может использоваться для создания приложений для устройств, облака и Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="2e19a-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="2e19a-107">Дополнительные сведения о среде .NET Core, включая ее характеристики, поддерживаемые языки и платформы, а также основные API-интерфейсы, см. в [этой статье](about.md).</span><span class="sxs-lookup"><span data-stu-id="2e19a-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="2e19a-108">Просмотрите [руководства по .NET Core](tutorials/index.md), чтобы узнать, как создать простое приложение .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2e19a-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="2e19a-109">На создание и запуск первого приложения потребуется буквально несколько минут.</span><span class="sxs-lookup"><span data-stu-id="2e19a-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="2e19a-110">Если вы хотите попробовать поработать с .NET Core в браузере, перейдите на страницу онлайн-руководства [Числа в C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml).</span><span class="sxs-lookup"><span data-stu-id="2e19a-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core-22"></a><span data-ttu-id="2e19a-111">Скачать .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="2e19a-111">Download .NET Core 2.2</span></span>

<span data-ttu-id="2e19a-112">Скачайте [пакет SDK для .NET Core 2.2](https://www.microsoft.com/net/download), чтобы опробовать .NET Core на компьютере под управлением Windows, macOS или Linux.</span><span class="sxs-lookup"><span data-stu-id="2e19a-112">Download the [.NET Core  2.2 SDK](https://www.microsoft.com/net/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="2e19a-113">Если вы предпочитаете использовать контейнеры Docker, перейдите на страницу [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="2e19a-113">Visit [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) if you prefer to use Docker containers.</span></span>

<span data-ttu-id="2e19a-114">Если вам нужна другая версия .NET Core, все версии доступны на [странице скачиваемых файлов .NET Core](https://www.microsoft.com/net/download/archives).</span><span class="sxs-lookup"><span data-stu-id="2e19a-114">All .NET Core versions are available at [.NET Core Downloads](https://www.microsoft.com/net/download/archives) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-22"></a><span data-ttu-id="2e19a-115">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="2e19a-115">.NET Core 2.2</span></span>

<span data-ttu-id="2e19a-116">[.NET Core 2.2](whats-new/dotnet-core-2-2.md) — самая новая версия .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2e19a-116">The latest version is [.NET Core 2.2](whats-new/dotnet-core-2-2.md).</span></span> <span data-ttu-id="2e19a-117">Ее новые возможности: развертывание с учетом платформ, перехватчики при запуске, проверка подлинности AAD в Azure SQL и поддержка Windows ARM32.</span><span class="sxs-lookup"><span data-stu-id="2e19a-117">New features include: framework-dependent deployments, startup hooks, AAD authentication with Azure SQL, and support for Windows ARM32.</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="2e19a-118">Создание первого приложения</span><span class="sxs-lookup"><span data-stu-id="2e19a-118">Create your first application</span></span>

<span data-ttu-id="2e19a-119">После установки пакета SDK для .NET Core откройте командную строку.</span><span class="sxs-lookup"><span data-stu-id="2e19a-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="2e19a-120">Для создания и запуска приложения C# введите следующие команды `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="2e19a-120">Type the following `dotnet` commands to create and run a C# application.</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="2e19a-121">Должны выводиться следующие данные:</span><span class="sxs-lookup"><span data-stu-id="2e19a-121">You should see the following output:</span></span>

```console
Hello World!
```

## <a name="support"></a><span data-ttu-id="2e19a-122">Поддержка</span><span class="sxs-lookup"><span data-stu-id="2e19a-122">Support</span></span>

<span data-ttu-id="2e19a-123">Поддержкой платформы .NET Core занимается [корпорация Майкрософт](https://www.microsoft.com/net/support/policy). Поддержка предоставляется для операционных систем Windows, macOS и Linux.</span><span class="sxs-lookup"><span data-stu-id="2e19a-123">.NET Core is [supported by Microsoft](https://www.microsoft.com/net/support/policy), on Windows, macOS and Linux.</span></span> <span data-ttu-id="2e19a-124">Для повышения безопасности и качества платформа обновляется несколько раз в год, обычно ежемесячно.</span><span class="sxs-lookup"><span data-stu-id="2e19a-124">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="2e19a-125">Двоичные дистрибутивы .NET Core собираются и тестируются в Azure на серверах Майкрософт и поддерживаются наравне с другими продуктами Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="2e19a-125">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="2e19a-126">[Red Hat поддерживает .NET Core](http://redhatloves.net/) в операционной системе Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="2e19a-126">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="2e19a-127">Red Hat собирает .NET Core из исходного кода и публикует сборки на сайте [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="2e19a-127">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="2e19a-128">Red Hat и Майкрософт совместно занимаются обеспечением беспроблемной работы .NET Core в RHEL.</span><span class="sxs-lookup"><span data-stu-id="2e19a-128">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
