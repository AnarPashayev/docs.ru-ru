---
title: Разработка библиотек с помощью кроссплатформенных средств
description: Узнайте, как создавать библиотеки для .NET Core с помощью инструментов .NET Core CLI. Вы создадите библиотеку, которая поддерживает несколько платформ.
author: cartermp
ms.date: 05/01/2017
ms.custom: seodec18
ms.openlocfilehash: 90d960c996acd5a34ffb2215344e123dabad1014
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849477"
---
# <a name="developing-libraries-with-cross-platform-tools"></a><span data-ttu-id="be1ca-104">Разработка библиотек с помощью кроссплатформенных средств</span><span class="sxs-lookup"><span data-stu-id="be1ca-104">Developing Libraries with Cross Platform Tools</span></span>

<span data-ttu-id="be1ca-105">В этой статье рассматривается создание библиотек для .NET с помощью кроссплатформенных средств интерфейса командной строки (CLI).</span><span class="sxs-lookup"><span data-stu-id="be1ca-105">This article covers how to write libraries for .NET using cross-platform CLI tools.</span></span> <span data-ttu-id="be1ca-106">CLI предоставляет эффективный и низкоуровневый интерфейс, работающий в любых поддерживаемых операционных системах.</span><span class="sxs-lookup"><span data-stu-id="be1ca-106">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="be1ca-107">Вы по-прежнему можете создавать библиотеки с помощью Visual Studio. Если вы предпочитаете такой способ, обратитесь к [руководству по Visual Studio](libraries-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="be1ca-107">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](libraries-with-vs.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="be1ca-108">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="be1ca-108">Prerequisites</span></span>

<span data-ttu-id="be1ca-109">На компьютере должны быть установлены [пакет SDK и интерфейс CLI для .NET Core ](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="be1ca-109">You need [the .NET Core SDK and CLI](https://dotnet.microsoft.com/download) installed on your machine.</span></span>

<span data-ttu-id="be1ca-110">При работе с разделами, в которых используются различные версии .NET Framework, на компьютере с ОС Windows должна быть установлена платформа [.NET Framework](https://dotnet.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="be1ca-110">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](https://dotnet.microsoft.com) installed on a Windows machine.</span></span>

<span data-ttu-id="be1ca-111">Кроме того, если необходимо поддерживать целевые платформы .NET Framework предыдущих версий, требуется установить целевые пакеты и пакеты для разработчиков, предназначенные для предыдущих версий платформы, со [страницы с доступными для скачивания архивами для .NET](https://dotnet.microsoft.com/download/archives).</span><span class="sxs-lookup"><span data-stu-id="be1ca-111">Additionally, if you wish to support older .NET Framework targets, you need to install targeting/developer packs for older framework versions from the [.NET download archives page](https://dotnet.microsoft.com/download/archives).</span></span> <span data-ttu-id="be1ca-112">См. таблицу ниже.</span><span class="sxs-lookup"><span data-stu-id="be1ca-112">Refer to this table:</span></span>

| <span data-ttu-id="be1ca-113">Версия платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="be1ca-113">.NET Framework Version</span></span> | <span data-ttu-id="be1ca-114">Скачиваемые компоненты</span><span class="sxs-lookup"><span data-stu-id="be1ca-114">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="be1ca-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="be1ca-115">4.6.1</span></span>                  | <span data-ttu-id="be1ca-116">.NET Framework 4.6.1 Targeting Pack</span><span class="sxs-lookup"><span data-stu-id="be1ca-116">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="be1ca-117">4.6</span><span class="sxs-lookup"><span data-stu-id="be1ca-117">4.6</span></span>                    | <span data-ttu-id="be1ca-118">.NET Framework 4.6 Targeting Pack</span><span class="sxs-lookup"><span data-stu-id="be1ca-118">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="be1ca-119">4.5.2</span><span class="sxs-lookup"><span data-stu-id="be1ca-119">4.5.2</span></span>                  | <span data-ttu-id="be1ca-120">.NET Framework 4.5.2 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="be1ca-120">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="be1ca-121">4.5.1</span><span class="sxs-lookup"><span data-stu-id="be1ca-121">4.5.1</span></span>                  | <span data-ttu-id="be1ca-122">.NET Framework 4.5.1 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="be1ca-122">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="be1ca-123">4.5</span><span class="sxs-lookup"><span data-stu-id="be1ca-123">4.5</span></span>                    | <span data-ttu-id="be1ca-124">Пакет средств разработки программного обеспечения Windows для Windows 8</span><span class="sxs-lookup"><span data-stu-id="be1ca-124">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="be1ca-125">4.0</span><span class="sxs-lookup"><span data-stu-id="be1ca-125">4.0</span></span>                    | <span data-ttu-id="be1ca-126">Пакет SDK для Windows 7 и .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="be1ca-126">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="be1ca-127">2.0, 3.0 и 3.5</span><span class="sxs-lookup"><span data-stu-id="be1ca-127">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="be1ca-128">Среда выполнения .NET Framework 3.5 с пакетом обновления 1 (SP1) (либо версия для Windows 8 или более поздняя)</span><span class="sxs-lookup"><span data-stu-id="be1ca-128">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-the-net-standard"></a><span data-ttu-id="be1ca-129">Нацеливание на .NET Standard</span><span class="sxs-lookup"><span data-stu-id="be1ca-129">How to target the .NET Standard</span></span>

<span data-ttu-id="be1ca-130">Если вы недостаточно хорошо знакомы с платформой .NET Standard, дополнительные сведения см. в [этом разделе](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="be1ca-130">If you're not quite familiar with the .NET Standard, refer to the [.NET Standard](../../standard/net-standard.md) to learn more.</span></span>

<span data-ttu-id="be1ca-131">В этом разделе есть таблица, в которой версии .NET Standard сопоставляются с различными реализациями:</span><span class="sxs-lookup"><span data-stu-id="be1ca-131">In that article, there is a table which maps .NET Standard versions to various implementations:</span></span>

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

<span data-ttu-id="be1ca-132">Вот что значит эта таблица в контексте создания библиотеки:</span><span class="sxs-lookup"><span data-stu-id="be1ca-132">Here's what this table means for the purposes of creating a library:</span></span>

<span data-ttu-id="be1ca-133">Версия .NET Standard, которую вы выберете, будет компромиссом между наличием новейших API-интерфейсов и возможностью нацеливать приложение на большее количество реализаций .NET и версий .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="be1ca-133">The version of the .NET Standard you pick will be a tradeoff between access to the newest APIs and the ability to target more .NET implementations and .NET Standard versions.</span></span> <span data-ttu-id="be1ca-134">Диапазон целевых платформ и версий определяется выбранной версией `netstandardX.X` (где `X.X` — это номер версии), которая добавляется в файл проекта (`.csproj` или `.fsproj`).</span><span class="sxs-lookup"><span data-stu-id="be1ca-134">You control the range of targetable platforms and versions by picking a version of `netstandardX.X` (Where `X.X` is a version number) and adding it to your project file (`.csproj` or `.fsproj`).</span></span>

<span data-ttu-id="be1ca-135">При нацеливании на платформу .NET Standard есть три основных варианта, выбор которых зависит от ваших потребностей.</span><span class="sxs-lookup"><span data-stu-id="be1ca-135">You have three primary options when targeting the .NET Standard, depending on your needs.</span></span>

1. <span data-ttu-id="be1ca-136">Вы можете использовать версию .NET Standard по умолчанию, которая предоставляется шаблонами `netstandard1.4` и обеспечивает доступ к большинству API-интерфейсов .NET Standard, сохраняя совместимость с UWP, .NET Framework 4.6.1 и новой платформой .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="be1ca-136">You can use the default version of the .NET Standard supplied by templates - `netstandard1.4` - which gives you access to most APIs on .NET Standard while still being compatible with UWP, .NET Framework 4.6.1, and the forthcoming .NET Standard 2.0.</span></span>

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. <span data-ttu-id="be1ca-137">Можно использовать более раннюю или более позднюю версию .NET Standard, изменив значение в узле `TargetFramework` файла проекта.</span><span class="sxs-lookup"><span data-stu-id="be1ca-137">You can use a lower or higher version of the .NET Standard by modifying the value in the `TargetFramework` node of your project file.</span></span>

    <span data-ttu-id="be1ca-138">Версии .NET Standard обладают обратной совместимостью.</span><span class="sxs-lookup"><span data-stu-id="be1ca-138">.NET Standard versions are backward compatible.</span></span> <span data-ttu-id="be1ca-139">Это означает, что библиотеки `netstandard1.0` выполняются на платформах `netstandard1.1` и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="be1ca-139">That means that `netstandard1.0` libraries run on `netstandard1.1` platforms and higher.</span></span> <span data-ttu-id="be1ca-140">Однако прямой совместимости нет: более ранние платформы .NET Standard не могут ссылаться на более поздние.</span><span class="sxs-lookup"><span data-stu-id="be1ca-140">However, there is no forward compatibility - lower .NET Standard platforms cannot reference higher ones.</span></span> <span data-ttu-id="be1ca-141">Это значит, что библиотеки `netstandard1.0` не могут ссылаться на библиотеки, предназначенные для `netstandard1.1` или более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="be1ca-141">This means that `netstandard1.0` libraries cannot reference libraries targeting `netstandard1.1` or higher.</span></span> <span data-ttu-id="be1ca-142">Выберите версию Standard, которая предоставляет подходящее сочетание интерфейсов API и поддерживаемых платформ для ваших потребностей.</span><span class="sxs-lookup"><span data-stu-id="be1ca-142">Select the Standard version that has the right mix of APIs and platform support for your needs.</span></span> <span data-ttu-id="be1ca-143">Сейчас рекомендуем использовать версию `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="be1ca-143">We recommend `netstandard1.4` for now.</span></span>

3. <span data-ttu-id="be1ca-144">Если требуется нацеливание на .NET Framework версии 4.0 или более ранней или использование интерфейса API, доступного в .NET Framework, но не в .NET Standard (например, `System.Drawing`), прочитайте следующие подразделы, чтобы узнать, как осуществляется настройка для разных версий.</span><span class="sxs-lookup"><span data-stu-id="be1ca-144">If you want to target the .NET Framework versions 4.0 or below, or you wish to use an API available in the .NET Framework but not in the .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-the-net-framework"></a><span data-ttu-id="be1ca-145">Нацеливание на .NET Framework</span><span class="sxs-lookup"><span data-stu-id="be1ca-145">How to target the .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="be1ca-146">В этих инструкциях предполагается, что на компьютере установлена платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="be1ca-146">These instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="be1ca-147">Чтобы установить зависимости, обратитесь к разделу [Предварительные требования](#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="be1ca-147">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="be1ca-148">Имейте в виду, что некоторые используемые здесь версии .NET Framework больше не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="be1ca-148">Keep in mind that some of the .NET Framework versions used here are no longer in support.</span></span> <span data-ttu-id="be1ca-149">Сведения о неподдерживаемых версиях см. в статье [Вопросы и ответы о политике по срокам поддержки Microsoft .NET Framework](https://support.microsoft.com/gp/framework_faq/en-us).</span><span class="sxs-lookup"><span data-stu-id="be1ca-149">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="be1ca-150">Чтобы охватить максимальное количество разработчиков и проектов, используйте .NET Framework 4.0 в качестве базовой целевой платформы.</span><span class="sxs-lookup"><span data-stu-id="be1ca-150">If you want to reach the maximum number of developers and projects, use the .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="be1ca-151">Для нацеливания на .NET Framework сначала необходимо использовать моникер целевой платформы (TFM), соответствующий версии .NET Framework, которая должна поддерживаться.</span><span class="sxs-lookup"><span data-stu-id="be1ca-151">To target the .NET Framework, you will need to begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

| <span data-ttu-id="be1ca-152">Версия платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="be1ca-152">.NET Framework version</span></span> | <span data-ttu-id="be1ca-153">TFM</span><span class="sxs-lookup"><span data-stu-id="be1ca-153">TFM</span></span>      |
| ---------------------- | -------- |
| <span data-ttu-id="be1ca-154">.NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="be1ca-154">.NET Framework 2.0</span></span>     | `net20`  |
| <span data-ttu-id="be1ca-155">.NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="be1ca-155">.NET Framework 3.0</span></span>     | `net30`  |
| <span data-ttu-id="be1ca-156">.NET Framework 3,5</span><span class="sxs-lookup"><span data-stu-id="be1ca-156">.NET Framework 3.5</span></span>     | `net35`  |
| <span data-ttu-id="be1ca-157">.NET Framework 4.0</span><span class="sxs-lookup"><span data-stu-id="be1ca-157">.NET Framework 4.0</span></span>     | `net40`  |
| <span data-ttu-id="be1ca-158">.NET Framework 4,5</span><span class="sxs-lookup"><span data-stu-id="be1ca-158">.NET Framework 4.5</span></span>     | `net45`  |
| <span data-ttu-id="be1ca-159">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="be1ca-159">.NET Framework 4.5.1</span></span>   | `net451` |
| <span data-ttu-id="be1ca-160">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="be1ca-160">.NET Framework 4.5.2</span></span>   | `net452` |
| <span data-ttu-id="be1ca-161">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="be1ca-161">.NET Framework 4.6</span></span>     | `net46`  |
| <span data-ttu-id="be1ca-162">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="be1ca-162">.NET Framework 4.6.1</span></span>   | `net461` |
| <span data-ttu-id="be1ca-163">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="be1ca-163">.NET Framework 4.6.2</span></span>   | `net462` |
| <span data-ttu-id="be1ca-164">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="be1ca-164">.NET Framework 4.7</span></span>     | `net47`  |
| <span data-ttu-id="be1ca-165">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="be1ca-165">.NET Framework 4.8</span></span>     | `net48`  |

<span data-ttu-id="be1ca-166">Вставьте этот моникер целевой платформы в раздел `TargetFramework` файла проекта.</span><span class="sxs-lookup"><span data-stu-id="be1ca-166">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="be1ca-167">Например, вот как создать библиотеку, предназначенную для .NET Framework 4.0:</span><span class="sxs-lookup"><span data-stu-id="be1ca-167">For example, here's how you would write a library which targets the .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="be1ca-168">Вот и все!</span><span class="sxs-lookup"><span data-stu-id="be1ca-168">And that's it!</span></span> <span data-ttu-id="be1ca-169">Хотя эта библиотека компилируется только для .NET Framework 4, ее можно использовать в более поздних версиях .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="be1ca-169">Although this compiled only for the .NET Framework 4, you can use the library on newer versions of the .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="be1ca-170">Настройка для различных версий</span><span class="sxs-lookup"><span data-stu-id="be1ca-170">How to Multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="be1ca-171">В приведенных ниже инструкциях предполагается, что на компьютере установлена платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="be1ca-171">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="be1ca-172">Сведения о зависимостях, которые необходимо установить, и о том, где их можно скачать, см. в разделе [Предварительные требования](#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="be1ca-172">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="be1ca-173">Если проект поддерживает как .NET Framework, так и .NET Core, может потребоваться нацеливание на более старые версии .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="be1ca-173">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET Core.</span></span> <span data-ttu-id="be1ca-174">В такой ситуации, если вам нужно применять более новые интерфейсы API и языковые конструкции для новых целевых платформ, используйте директивы `#if` в коде.</span><span class="sxs-lookup"><span data-stu-id="be1ca-174">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="be1ca-175">Кроме того, может потребоваться добавить разные пакеты и зависимости для каждой целевой платформы, чтобы включить различные интерфейсы API, необходимые в каждом случае.</span><span class="sxs-lookup"><span data-stu-id="be1ca-175">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="be1ca-176">Предположим, имеется библиотека, выполняющая сетевые операции по протоколу HTTP.</span><span class="sxs-lookup"><span data-stu-id="be1ca-176">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="be1ca-177">Для .NET Standard и .NET Framework версии 4.5 или более поздней можно использовать класс `HttpClient` из пространства имен `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="be1ca-177">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="be1ca-178">Однако в более ранних версиях .NET Framework нет класса `HttpClient`, поэтому вместо него можно использовать класс `WebClient` из пространства имен `System.Net`.</span><span class="sxs-lookup"><span data-stu-id="be1ca-178">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="be1ca-179">Файл проекта может выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="be1ca-179">Your project file could look like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.0 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net40'">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.5 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net45'">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="be1ca-180">Вы заметите три основных изменения:</span><span class="sxs-lookup"><span data-stu-id="be1ca-180">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="be1ca-181">Узел `TargetFramework` был заменен на `TargetFrameworks`, внутри которого содержатся три моникера целевой платформы.</span><span class="sxs-lookup"><span data-stu-id="be1ca-181">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="be1ca-182">Добавлен узел `<ItemGroup>` для целевой платформы `net40`, который извлекает одну ссылку на .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="be1ca-182">There is an `<ItemGroup>` node for the `net40` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="be1ca-183">Добавлен узел `<ItemGroup>` для целевой платформы `net45`, который извлекает две ссылки на .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="be1ca-183">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="be1ca-184">Система сборки распознает следующие символы препроцессора, используемые в директивах `#if`:</span><span class="sxs-lookup"><span data-stu-id="be1ca-184">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

<span data-ttu-id="be1ca-185">Ниже приведен пример использования условной компиляции для каждого целевого объекта:</span><span class="sxs-lookup"><span data-stu-id="be1ca-185">Here is an example making use of conditional compilation per-target:</span></span>

```csharp
using System;
using System.Text.RegularExpressions;
#if NET40
// This only compiles for the .NET Framework 4 targets
using System.Net;
#else
 // This compiles for all other targets
using System.Net.Http;
using System.Threading.Tasks;
#endif

namespace MultitargetLib
{
    public class Library
    {
#if NET40
        private readonly WebClient _client = new WebClient();
        private readonly object _locker = new object();
#else
        private readonly HttpClient _client = new HttpClient();
#endif

#if NET40
        // .NET Framework 4.0 does not have async/await
        public string GetDotNetCount()
        {
            string url = "https://www.dotnetfoundation.org/";

            var uri = new Uri(url);

            string result = "";

            // Lock here to provide thread-safety.
            lock(_locker)
            {
                result = _client.DownloadString(uri);
            }

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"Dotnet Foundation mentions .NET {dotNetCount} times!";
        }
#else
        // .NET 4.5+ can use async/await!
        public async Task<string> GetDotNetCountAsync()
        {
            string url = "https://www.dotnetfoundation.org/";

            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
}
```

<span data-ttu-id="be1ca-186">При сборке этого проекта с `dotnet build` вы увидите, что в папке `bin/` появились три каталога:</span><span class="sxs-lookup"><span data-stu-id="be1ca-186">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard1.4/
```

<span data-ttu-id="be1ca-187">Каждый из них содержит файлы `.dll` для соответствующего целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="be1ca-187">Each of these contain the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net-core"></a><span data-ttu-id="be1ca-188">Тестирование библиотек в .NET Core</span><span class="sxs-lookup"><span data-stu-id="be1ca-188">How to test libraries on .NET Core</span></span>

<span data-ttu-id="be1ca-189">Необходимо иметь возможность тестирования проектов на различных платформах.</span><span class="sxs-lookup"><span data-stu-id="be1ca-189">It's important to be able to test across platforms.</span></span> <span data-ttu-id="be1ca-190">Вы можете использовать [xUnit](https://xunit.github.io/) или MSTest без дополнительной настройки.</span><span class="sxs-lookup"><span data-stu-id="be1ca-190">You can use either [xUnit](https://xunit.github.io/) or MSTest out of the box.</span></span> <span data-ttu-id="be1ca-191">Обе платформы тестирования идеально подходят для модульного тестирования библиотеки в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="be1ca-191">Both are perfectly suitable for unit testing your library on .NET Core.</span></span> <span data-ttu-id="be1ca-192">Настройка тестовых проектов для решения зависит от [его структуры](#structuring-a-solution).</span><span class="sxs-lookup"><span data-stu-id="be1ca-192">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="be1ca-193">В следующем примере предполагается, что каталог с тестами и каталог с исходным кодом находятся в одном и том же каталоге верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="be1ca-193">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="be1ca-194">В этом примере используются некоторые [команды интерфейса командной строки .NET Core](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="be1ca-194">This uses some [.NET Core CLI commands](../tools/index.md).</span></span> <span data-ttu-id="be1ca-195">Дополнительные сведения см. в разделах [dotnet new](../tools/dotnet-new.md) и [dotnet sln](../tools/dotnet-sln.md).</span><span class="sxs-lookup"><span data-stu-id="be1ca-195">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="be1ca-196">Настройте решение.</span><span class="sxs-lookup"><span data-stu-id="be1ca-196">Set up your solution.</span></span> <span data-ttu-id="be1ca-197">Это можно сделать с помощью следующих команд:</span><span class="sxs-lookup"><span data-stu-id="be1ca-197">You can do so with the following commands:</span></span>

   ```bash
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="be1ca-198">Эти команды создадут проекты и объединят их в решение.</span><span class="sxs-lookup"><span data-stu-id="be1ca-198">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="be1ca-199">Ваш каталог для `SolutionWithSrcAndTest` должен выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="be1ca-199">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="be1ca-200">Перейдите в каталог тестового проекта и добавьте ссылку на `MyProject.Test` из `MyProject`.</span><span class="sxs-lookup"><span data-stu-id="be1ca-200">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```bash
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="be1ca-201">Восстановите пакеты и соберите проекты:</span><span class="sxs-lookup"><span data-stu-id="be1ca-201">Restore packages and build projects:</span></span>

   ```bash
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. <span data-ttu-id="be1ca-202">Убедитесь, что xUnit запущен, выполнив команду `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="be1ca-202">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="be1ca-203">Если вы решили использовать MSTest, запустите средство запуска консоли MSTest вместо xUnit.</span><span class="sxs-lookup"><span data-stu-id="be1ca-203">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>

<span data-ttu-id="be1ca-204">Вот и все!</span><span class="sxs-lookup"><span data-stu-id="be1ca-204">And that's it!</span></span> <span data-ttu-id="be1ca-205">Теперь вы можете протестировать библиотеку для всех платформ с помощью средств командной строки.</span><span class="sxs-lookup"><span data-stu-id="be1ca-205">You can now test your library across all platforms using command line tools.</span></span> <span data-ttu-id="be1ca-206">Теперь, когда все настроено, протестировать библиотеку очень легко:</span><span class="sxs-lookup"><span data-stu-id="be1ca-206">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="be1ca-207">Внесите изменения в библиотеку.</span><span class="sxs-lookup"><span data-stu-id="be1ca-207">Make changes to your library.</span></span>
1. <span data-ttu-id="be1ca-208">Выполните тесты в тестовом каталоге из командной строки с помощью команды `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="be1ca-208">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="be1ca-209">При вызове команды `dotnet test` будет автоматически выполнена повторная сборка кода.</span><span class="sxs-lookup"><span data-stu-id="be1ca-209">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="be1ca-210">Использование нескольких проектов</span><span class="sxs-lookup"><span data-stu-id="be1ca-210">How to use multiple projects</span></span>

<span data-ttu-id="be1ca-211">В случае с более крупными библиотеками, как правило, требуется реализовывать функциональность в разных проектах.</span><span class="sxs-lookup"><span data-stu-id="be1ca-211">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="be1ca-212">Представим, что необходимо создать библиотеку, которую можно использовать в идиоматичном коде на языках C# и F#.</span><span class="sxs-lookup"><span data-stu-id="be1ca-212">Imagine you wished to build a library which could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="be1ca-213">Это означает, что библиотека будет использоваться способами, естественными для языков C# и F#.</span><span class="sxs-lookup"><span data-stu-id="be1ca-213">That would mean that consumers of your library consume them in ways which are natural to C# or F#.</span></span> <span data-ttu-id="be1ca-214">Например, в C# можно использовать библиотеку следующим образом:</span><span class="sxs-lookup"><span data-stu-id="be1ca-214">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="be1ca-215">В F# это может выглядеть так.</span><span class="sxs-lookup"><span data-stu-id="be1ca-215">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="be1ca-216">Подобные сценарии использования предполагают, что интерфейсы API, к которым осуществляется доступ, должны иметь разную структуру для C# и F#.</span><span class="sxs-lookup"><span data-stu-id="be1ca-216">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="be1ca-217">Стандартным подходом к решению этой задачи является факторинг всей логики библиотеки в базовом проекте и определение в проектах C# и F# уровней API, которые вызывают этот базовый проект.</span><span class="sxs-lookup"><span data-stu-id="be1ca-217">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="be1ca-218">Далее в этом разделе будут использоваться следующие имена:</span><span class="sxs-lookup"><span data-stu-id="be1ca-218">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="be1ca-219">**AwesomeLibrary.Core** — базовый проект, содержащий всю логику библиотеки;</span><span class="sxs-lookup"><span data-stu-id="be1ca-219">**AwesomeLibrary.Core** - A core project which contains all logic for the library</span></span>
* <span data-ttu-id="be1ca-220">**AwesomeLibrary.CSharp** — проект с открытыми интерфейсами API, предназначенными для использования в коде на языке C#</span><span class="sxs-lookup"><span data-stu-id="be1ca-220">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="be1ca-221">**AwesomeLibrary.FSharp** — проект с открытыми интерфейсами API, предназначенными для использования в коде на языке F#</span><span class="sxs-lookup"><span data-stu-id="be1ca-221">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="be1ca-222">Чтобы получить ту же структуру каталогов, что и в этом руководстве, выполните следующие команды в окне терминала:</span><span class="sxs-lookup"><span data-stu-id="be1ca-222">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

```console
mkdir AwesomeLibrary && cd AwesomeLibrary
dotnet new sln
mkdir AwesomeLibrary.Core && cd AwesomeLibrary.Core && dotnet new classlib
cd ..
mkdir AwesomeLibrary.CSharp && cd AwesomeLibrary.CSharp && dotnet new classlib
cd ..
mkdir AwesomeLibrary.FSharp && cd AwesomeLibrary.FSharp && dotnet new classlib -lang F#
cd ..
dotnet sln add AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
dotnet sln add AwesomeLibrary.CSharp/AwesomeLibrary.CSharp.csproj
dotnet sln add AwesomeLibrary.FSharp/AwesomeLibrary.FSharp.fsproj
```

<span data-ttu-id="be1ca-223">Эти команды добавят три указанные выше проекта и файл решения, который связывает их вместе.</span><span class="sxs-lookup"><span data-stu-id="be1ca-223">This will add the three projects above and a solution file which links them together.</span></span> <span data-ttu-id="be1ca-224">Создание файла решения и связывание проектов позволит вам собирать и восстанавливать проекты из верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="be1ca-224">Creating the solution file and linking projects will allow you to restore and build projects from a top-level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="be1ca-225">Ссылки проектов на проекты</span><span class="sxs-lookup"><span data-stu-id="be1ca-225">Project-to-project referencing</span></span>

<span data-ttu-id="be1ca-226">Ссылку на проект лучше всего добавить с помощью интерфейса командной строки .NET Core.</span><span class="sxs-lookup"><span data-stu-id="be1ca-226">The best way to reference a project is to use the .NET Core CLI to add a project reference.</span></span> <span data-ttu-id="be1ca-227">Из каталогов проекта **AwesomeLibrary.CSharp** и **AwesomeLibrary.FSharp** выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="be1ca-227">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```console
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="be1ca-228">Теперь файлы **AwesomeLibrary.CSharp** и **AwesomeLibrary.FSharp** будут ссылаться на **AwesomeLibrary.Core** в качестве целевого объекта `ProjectReference`.</span><span class="sxs-lookup"><span data-stu-id="be1ca-228">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="be1ca-229">Чтобы это проверить, просмотрите файлы проектов, и вы увидите в них следующий код:</span><span class="sxs-lookup"><span data-stu-id="be1ca-229">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="be1ca-230">Если вы не хотите использовать интерфейс командной строки .NET Core, можете добавить этот раздел в каждый файл проекта вручную.</span><span class="sxs-lookup"><span data-stu-id="be1ca-230">You can add this section to each project file manually if you prefer not to use the .NET Core CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="be1ca-231">Структурирование решения</span><span class="sxs-lookup"><span data-stu-id="be1ca-231">Structuring a solution</span></span>

<span data-ttu-id="be1ca-232">Еще один важный аспект решений с несколькими проектами — правильное формирование общей структуры.</span><span class="sxs-lookup"><span data-stu-id="be1ca-232">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="be1ca-233">Код можно упорядочить так, как вам удобно. Если каждый проект связан с файлом решения с помощью `dotnet sln add`, вы сможете запускать команды `dotnet restore` и `dotnet build` на уровне проекта.</span><span class="sxs-lookup"><span data-stu-id="be1ca-233">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
