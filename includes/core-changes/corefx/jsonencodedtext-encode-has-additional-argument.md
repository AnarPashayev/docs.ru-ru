---
ms.openlocfilehash: 375a6f57a867c2a11fe95753c1085d6d708db2bd
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237450"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a><span data-ttu-id="81620-101">Методы JsonEncodedText.Encode содержат дополнительный аргумент JavaScriptEncoder</span><span class="sxs-lookup"><span data-stu-id="81620-101">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>

<span data-ttu-id="81620-102">Начиная с .NET Core 3.0 (предварительная версия 8) методы <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> содержат необязательный аргумент <xref:System.Text.Encodings.Web.JavaScriptEncoder>.</span><span class="sxs-lookup"><span data-stu-id="81620-102">Starting with .NET Core 3.0 Preview 8, the <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> methods contain an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.</span></span>

#### <a name="change-description"></a><span data-ttu-id="81620-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="81620-103">Change description</span></span>

<span data-ttu-id="81620-104">.NET Core 3.0 включает новый тип xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="81620-104">.NET Core 3.0 includes a new type, xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="81620-105">Начиная с .NET Core 3 0 (предварительная версия 8) сигнатура всех перегрузок метода <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> включает необязательный параметр <xref:System.Text.Encodings.Web.JavaScriptEncoder>.</span><span class="sxs-lookup"><span data-stu-id="81620-105">Starting with .NET Core 3.0 Preview 8, the signature of all <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> method overloads has changed to include an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> parameter.</span></span> <span data-ttu-id="81620-106">Это изменение позволяет использовать другой или пользовательский кодировщик.</span><span class="sxs-lookup"><span data-stu-id="81620-106">This change was made to allow for a different or custom encoder.</span></span>

<span data-ttu-id="81620-107">Сигнатура методов `Encode` в NET Core 3.0 (предварительная версия 7):</span><span class="sxs-lookup"><span data-stu-id="81620-107">The signature of the `Encode` methods in .NET Core 3.0 Preview 7 is:</span></span>

```csharp
namespace System.Text.Json
{
    public readonly struct JsonEncodedText
    {
        public static JsonEncodedText Encode(ReadOnlySpan<byte> utf8Value);
        public static JsonEncodedText Encode(ReadOnlySpan<char> value);
        public static JsonEncodedText Encode(string value);
    }
}
```

<span data-ttu-id="81620-108">Сигнатура тех же методов `Encode` в NET Core 3.0 (предварительная версия 8 и последующие версии):</span><span class="sxs-lookup"><span data-stu-id="81620-108">The signature of the same `Encode` methods in .NET Core 3.0 Preview 8 and later versions is:</span></span>

```csharp
namespace System.Text.Json
{
    public readonly struct JsonEncodedText
    {
        public static JsonEncodedText Encode(ReadOnlySpan<byte> utf8Value, JavaScriptEncoder encoder = null);
        public static JsonEncodedText Encode(ReadOnlySpan<char> value, JavaScriptEncoder encoder = null);
        public static JsonEncodedText Encode(string value, JavaScriptEncoder encoder = null);
    }
}
```

#### <a name="version-introduced"></a><span data-ttu-id="81620-109">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="81620-109">Version introduced</span></span>

<span data-ttu-id="81620-110">.NET Core 3.0 (предварительная версия 8)</span><span class="sxs-lookup"><span data-stu-id="81620-110">.NET Core 3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="81620-111">Рекомендуемое действие</span><span class="sxs-lookup"><span data-stu-id="81620-111">Recommended action</span></span>

<span data-ttu-id="81620-112">Это критическое изменение касается только двоичного кода. При повторной компиляции для .NET Core 3.0 (предварительная версия 8 и последующие версии) все проблемы среды выполнения будут исправлены.</span><span class="sxs-lookup"><span data-stu-id="81620-112">This is a binary breaking change only; a recompile against .NET Core 3.0 Preview 8 or a later version will fix any runtime issues.</span></span>

#### <a name="category"></a><span data-ttu-id="81620-113">Категория</span><span class="sxs-lookup"><span data-stu-id="81620-113">Category</span></span>

<span data-ttu-id="81620-114">CoreFX</span><span class="sxs-lookup"><span data-stu-id="81620-114">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="81620-115">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="81620-115">Affected APIs</span></span>

<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->
