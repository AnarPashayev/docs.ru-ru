---
title: Критические изменения CoreFx — .NET Core
description: Список критических изменений в библиотеке базовых классов .NET CoreFx.
ms.date: 09/20/2019
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7681dadbbbae737cb1cbc260613baea9d34527a8
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002457"
---
# <a name="corefx-breaking-changes"></a><span data-ttu-id="5e174-103">Критические изменения CoreFx</span><span class="sxs-lookup"><span data-stu-id="5e174-103">CoreFx breaking changes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5e174-104">Эта статья находится на стадии разработки.</span><span class="sxs-lookup"><span data-stu-id="5e174-104">This article is under construction.</span></span> <span data-ttu-id="5e174-105">Это не полный список критических изменений .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e174-105">This is not a complete list of .NET Core breaking changes.</span></span> <span data-ttu-id="5e174-106">Дополнительные сведения о критических изменениях .NET Core см. в отдельных [вопросах](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) в репозитории dotnet/docs на GitHub.</span><span class="sxs-lookup"><span data-stu-id="5e174-106">For more information on .NET Core breaking changes, you can examine individual [breaking changes issues](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) in the dotnet/docs repository on GitHub.</span></span>

<span data-ttu-id="5e174-107">Ниже приведен список критических изменений CoreFx по версиям .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e174-107">The following is a list of CoreFx breaking changes by .NET Core version.</span></span> <span data-ttu-id="5e174-108">CoreFx предоставляет примитивы и другие общие типы, используемые в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e174-108">CoreFx provides the primitives and other general types used by .NET Core.</span></span>

## <a name="net-core-30-preview-7"></a><span data-ttu-id="5e174-109">.NET Core 3.0 (предварительная версия 7)</span><span class="sxs-lookup"><span data-stu-id="5e174-109">.NET Core 3.0 Preview 7</span></span>

[!INCLUDE[JsonElement API changes](~/includes/core-changes/corefx/jsonelement-api-changes.md)]

## <a name="net-core-30-preview-8"></a><span data-ttu-id="5e174-110">.NET Core 3.0 (предварительная версия 8)</span><span class="sxs-lookup"><span data-stu-id="5e174-110">.NET Core 3.0 Preview 8</span></span>

[!INCLUDE[Change in semantics of (string)null in Utf8JsonWriter](~/includes/core-changes/corefx/change-in-null-in-utf8jsonwriter.md)]

***

[!INCLUDE[JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument](~/includes/core-changes/corefx/jsonencodedtext-encode-has-additional-argument.md)]

***

[!INCLUDE[JsonFactoryConverter.CreateConverter signature changed](~/includes/core-changes/corefx/jsonfactoryconverter-createconverter.md)]

## <a name="net-core-30-preview-9"></a><span data-ttu-id="5e174-111">.NET Core 3.0 (предварительная версия 9)</span><span class="sxs-lookup"><span data-stu-id="5e174-111">.NET Core 3.0 Preview 9</span></span>

[!INCLUDE[Json serializer exception type changed from JsonException to NotSupportedException](~/includes/core-changes/corefx/serializer-throws-notsupportedexception.md)]

## <a name="net-core-30"></a><span data-ttu-id="5e174-112">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5e174-112">.NET Core 3.0</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/floating-point-changes.md)]

***

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/floating-point-parsing-does-not-overflow.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/ziparchiveentry-and-inconsistent-entry-sizes.md)]
