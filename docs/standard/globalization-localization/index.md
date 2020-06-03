---
title: Глобализация и локализация приложений .NET
ms.date: 06/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- international applications [.NET]
- globalization [.NET], encoding
- global applications
- internationalization
- world-ready applications
- application development [.NET], globalization
- multilingual application development
ms.assetid: 9a59696b-d89b-45bd-946d-c75da4732d02
ms.openlocfilehash: 10d07a02a7ff744a87b920fd97df24b076c22cc3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288294"
---
# <a name="globalizing-and-localizing-net-applications"></a><span data-ttu-id="2aca1-102">Глобализация и локализация приложений .NET</span><span class="sxs-lookup"><span data-stu-id="2aca1-102">Globalizing and localizing .NET applications</span></span>

<span data-ttu-id="2aca1-103">Разработка международного приложения, в том числе приложения, которое можно локализовать на один или несколько языков, включает следующие шаги: глобализацию, анализ локализуемости и локализацию.</span><span class="sxs-lookup"><span data-stu-id="2aca1-103">Developing a world-ready application, including an application that can be localized into one or more languages, involves three steps: globalization, localizability review, and localization.</span></span>

[<span data-ttu-id="2aca1-104">Глобализация</span><span class="sxs-lookup"><span data-stu-id="2aca1-104">Globalization</span></span>](globalization.md)

<span data-ttu-id="2aca1-105">Этот шаг включает проектирование и программирование приложения, не зависящего от языка и региональных параметров и поддерживающего локализованные пользовательские интерфейсы и региональные данные для всех пользователей.</span><span class="sxs-lookup"><span data-stu-id="2aca1-105">This step involves designing and coding an application that is culture-neutral and language-neutral, and that supports localized user interfaces and regional data for all users.</span></span> <span data-ttu-id="2aca1-106">Это предполагает принятие проектных и программных решений, которые не основаны на предположениях в отношении определенного языка или региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="2aca1-106">It involves making design and programming decisions that are not based on culture-specific assumptions.</span></span> <span data-ttu-id="2aca1-107">Хотя глобализованное приложение не локализовано, однако оно разработано и составлено так, чтобы впоследствии его можно было относительно легко локализовать на один или несколько языков.</span><span class="sxs-lookup"><span data-stu-id="2aca1-107">While a globalized application is not localized, it nevertheless is designed and written so that it can be subsequently localized into one or more languages with relative ease.</span></span>

[<span data-ttu-id="2aca1-108">Проверка локализуемости</span><span class="sxs-lookup"><span data-stu-id="2aca1-108">Localizability review</span></span>](localizability-review.md)

<span data-ttu-id="2aca1-109">Этот шаг позволяет проверить код и дизайн приложения, чтобы убедиться в возможности простой локализации приложения и убедиться, что исполняемый код и ресурсы приложения разделены.</span><span class="sxs-lookup"><span data-stu-id="2aca1-109">This step involves reviewing an application's code and design to ensure that it can be localized easily and to identify potential roadblocks for localization, and verifying that the application's executable code is separated from its resources.</span></span> <span data-ttu-id="2aca1-110">Если этап глобализации был эффективным, анализ локализуемости подтвердит проектные решения и решения кодирования, принятые во время глобализации.</span><span class="sxs-lookup"><span data-stu-id="2aca1-110">If the globalization stage was effective, the localizability review will confirm the design and coding choices made during globalization.</span></span> <span data-ttu-id="2aca1-111">На этапе анализа локализуемости можно выявить оставшиеся проблемы, чтобы не пришлось менять исходный код приложения на этапе локализации.</span><span class="sxs-lookup"><span data-stu-id="2aca1-111">The localizability stage may also identify any remaining issues so that an application's source code doesn't have to be modified during the localization stage.</span></span>

[<span data-ttu-id="2aca1-112">Локализация</span><span class="sxs-lookup"><span data-stu-id="2aca1-112">Localization</span></span>](localization.md)

<span data-ttu-id="2aca1-113">Этот этап включает настройку приложения для конкретных языков или регионов.</span><span class="sxs-lookup"><span data-stu-id="2aca1-113">This step involves customizing an application for specific cultures or regions.</span></span> <span data-ttu-id="2aca1-114">Если этапы глобализации и анализа локализуемости были проведены правильно, то локализация заключается главным образом в переводе пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="2aca1-114">If the globalization and localizability steps have been performed correctly, localization consists primarily of translating the user interface.</span></span>

<span data-ttu-id="2aca1-115">Выполнение этих трех этапов обеспечивает два преимущества:</span><span class="sxs-lookup"><span data-stu-id="2aca1-115">Following these three steps provides two advantages:</span></span>

- <span data-ttu-id="2aca1-116">Освобождает от необходимости модифицировать приложение, разработанное для поддержки одного языка и региона, например английского языка (США), чтобы обеспечить поддержку дополнительных языков и регионов.</span><span class="sxs-lookup"><span data-stu-id="2aca1-116">It frees you from having to retrofit an application that is designed to support a single culture, such as U.S. English, to support additional cultures.</span></span>

- <span data-ttu-id="2aca1-117">В результате создаются локализованные приложения, которые более стабильны и содержат меньше ошибок.</span><span class="sxs-lookup"><span data-stu-id="2aca1-117">It results in localized applications that are more stable and have fewer bugs.</span></span>

<span data-ttu-id="2aca1-118">Платформа .NET предоставляет широкие возможности для разработки международных и локализованных приложений.</span><span class="sxs-lookup"><span data-stu-id="2aca1-118">.NET provides extensive support for the development of world-ready and localized applications.</span></span> <span data-ttu-id="2aca1-119">В частности, многие элементы типов в библиотеке классов .NET упрощают глобализацию, возвращая значения, отражающие соглашения языка и региональных параметров текущего либо заданного пользователя.</span><span class="sxs-lookup"><span data-stu-id="2aca1-119">In particular, many type members in the .NET class library aid globalization by returning values that reflect the conventions of either the current user's culture or a specified culture.</span></span> <span data-ttu-id="2aca1-120">Кроме того, платформа .NET поддерживает вспомогательные сборки, ускоряющие процесс локализации приложений.</span><span class="sxs-lookup"><span data-stu-id="2aca1-120">Also, .NET supports satellite assemblies, which facilitate the process of localizing an application.</span></span>

<span data-ttu-id="2aca1-121">Дополнительные сведения см. в [документации по глобализации](/globalization/).</span><span class="sxs-lookup"><span data-stu-id="2aca1-121">For additional information, see the [Globalization documentation](/globalization/).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="2aca1-122">Содержание раздела</span><span class="sxs-lookup"><span data-stu-id="2aca1-122">In this section</span></span>

[<span data-ttu-id="2aca1-123">Глобализация</span><span class="sxs-lookup"><span data-stu-id="2aca1-123">Globalization</span></span>](globalization.md)

<span data-ttu-id="2aca1-124">Описание первого этапа создания международного приложения, который предполагает проектирование и кодирование приложения, не зависящего от языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="2aca1-124">Discusses the first stage of creating a world-ready application, which involves designing and coding an application that is culture-neutral and language-neutral.</span></span>

[<span data-ttu-id="2aca1-125">Глобализация .NET и ICU</span><span class="sxs-lookup"><span data-stu-id="2aca1-125">.NET globalization and ICU</span></span>](globalization-icu.md)

<span data-ttu-id="2aca1-126">Описание использования библиотек Юникода [International Components for Unicode (ICU)](http://site.icu-project.org/home) в глобализации .NET.</span><span class="sxs-lookup"><span data-stu-id="2aca1-126">Describes how .NET globalization uses [International Components for Unicode (ICU)](http://site.icu-project.org/home).</span></span>

[<span data-ttu-id="2aca1-127">Проверка локализуемости</span><span class="sxs-lookup"><span data-stu-id="2aca1-127">Localizability review</span></span>](localizability-review.md)

<span data-ttu-id="2aca1-128">Описание второго этапа создания международного приложения, который предполагает выявление потенциальных препятствий для локализации.</span><span class="sxs-lookup"><span data-stu-id="2aca1-128">Discusses the second stage of creating a localized application, which involves identifying potential roadblocks to localization.</span></span>

[<span data-ttu-id="2aca1-129">Локализация</span><span class="sxs-lookup"><span data-stu-id="2aca1-129">Localization</span></span>](localization.md)

<span data-ttu-id="2aca1-130">Описание заключительного этапа создания локализованного приложения, который предполагает настройку пользовательского интерфейса приложения для конкретных регионов или языков и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="2aca1-130">Discusses the final stage of creating a localized application, which involves customizing an application's user interface for specific regions or cultures.</span></span>

[<span data-ttu-id="2aca1-131">Операции со строками без учета языка и региональных параметров</span><span class="sxs-lookup"><span data-stu-id="2aca1-131">Culture-insensitive string operations</span></span>](culture-insensitive-string-operations.md)

<span data-ttu-id="2aca1-132">Статья описывает, как использовать методы и классы .NET, которые по умолчанию учитывают язык и региональные параметры, для получения результатов без их учета.</span><span class="sxs-lookup"><span data-stu-id="2aca1-132">Describes how to use .NET methods and classes that are culture-sensitive by default to obtain culture-insensitive results.</span></span>

[<span data-ttu-id="2aca1-133">Рекомендации по разработке международных приложений</span><span class="sxs-lookup"><span data-stu-id="2aca1-133">Best practices for developing world-ready applications</span></span>](best-practices-for-developing-world-ready-apps.md)

<span data-ttu-id="2aca1-134">Описание лучших методик по глобализации, локализации и разработке международных приложений ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2aca1-134">Describes the best practices to follow for globalization, localization, and developing world-ready ASP.NET applications.</span></span>

## <a name="reference"></a><span data-ttu-id="2aca1-135">Справочник</span><span class="sxs-lookup"><span data-stu-id="2aca1-135">Reference</span></span>

- <span data-ttu-id="2aca1-136">Пространство имен <xref:System.Globalization?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="2aca1-136"><xref:System.Globalization?displayProperty=nameWithType> namespace</span></span>

   <span data-ttu-id="2aca1-137">Содержит классы, определяющие сведения, относящиеся к культуре, такие как язык, название страны, используемые календари, шаблоны форматирования дат, денежных единиц и чисел, а также порядок сортировки строк.</span><span class="sxs-lookup"><span data-stu-id="2aca1-137">Contains classes that define culture-related information, including the language, the country/region, the calendars in use, the format patterns for dates, currency, and numbers, and the sort order for strings.</span></span>

- <span data-ttu-id="2aca1-138">Пространство имен <xref:System.Resources></span><span class="sxs-lookup"><span data-stu-id="2aca1-138"><xref:System.Resources> namespace</span></span>

   <span data-ttu-id="2aca1-139">Предоставляет классы для создания и использования ресурсов, а также управления ими.</span><span class="sxs-lookup"><span data-stu-id="2aca1-139">Provides classes for creating, manipulating, and using resources.</span></span>

- <span data-ttu-id="2aca1-140">Пространство имен <xref:System.Text></span><span class="sxs-lookup"><span data-stu-id="2aca1-140"><xref:System.Text> namespace</span></span>

   <span data-ttu-id="2aca1-141">Содержит классы, представляющие ASCII, ANSI, Юникод и другие форматы кодировки символов.</span><span class="sxs-lookup"><span data-stu-id="2aca1-141">Contains classes representing ASCII, ANSI, Unicode, and other character encodings.</span></span>

- [<span data-ttu-id="2aca1-142">Resgen.exe (генератор файлов ресурсов)</span><span class="sxs-lookup"><span data-stu-id="2aca1-142">Resgen.exe (Resource File Generator)</span></span>](../../framework/tools/resgen-exe-resource-file-generator.md)

   <span data-ttu-id="2aca1-143">Описание использования программы Resgen.exe для преобразования файлов .txt и .resx и файлов формата XML (.resx) в двоичные файлы .resources общей среды исполнения.</span><span class="sxs-lookup"><span data-stu-id="2aca1-143">Describes how to use Resgen.exe to convert .txt files and XML-based resource format (.resx) files to common language runtime binary .resources files.</span></span>

- [<span data-ttu-id="2aca1-144">Winres.exe (редактор ресурсов Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="2aca1-144">Winres.exe (Windows Forms Resource Editor)</span></span>](../../framework/tools/winres-exe-windows-forms-resource-editor.md)

   <span data-ttu-id="2aca1-145">Описание использования Winres.exe для локализации форм Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2aca1-145">Describes how to use Winres.exe to localize Windows Forms forms.</span></span>
