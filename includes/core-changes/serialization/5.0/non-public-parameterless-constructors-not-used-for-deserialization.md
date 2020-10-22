---
ms.openlocfilehash: 3692848a0cbd4bbbe3c7bb4d2c22a2b19de732e4
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050481"
---
### <a name="non-public-parameterless-constructors-not-used-for-deserialization"></a><span data-ttu-id="322d9-101">Не являющиеся открытыми конструкторы без параметров не используются для десериализации</span><span class="sxs-lookup"><span data-stu-id="322d9-101">Non-public, parameterless constructors not used for deserialization</span></span>

<span data-ttu-id="322d9-102">Чтобы гарантировать согласованность, во всех поддерживаемых моникерах целевой платформы (TFM) не являющиеся открытыми конструкторы без параметров больше не используются для десериализации с помощью <xref:System.Text.Json.JsonSerializer> по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="322d9-102">For consistency across all supported target framework monikers (TFMs), non-public, parameterless constructors are no longer used for deserialization with <xref:System.Text.Json.JsonSerializer>, by default.</span></span>

#### <a name="change-description"></a><span data-ttu-id="322d9-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="322d9-103">Change description</span></span>

<span data-ttu-id="322d9-104">Поведение отдельных [пакетов NuGet System.Text.Json](https://www.nuget.org/packages/System.Text.Json/), которые поддерживают .NET Standard 2.0 и более поздних версий (версии с 4.6.0 по 4.7.2), согласуется со встроенным поведением в .NET Core 3.0 и 3.1.</span><span class="sxs-lookup"><span data-stu-id="322d9-104">The standalone [System.Text.Json NuGet packages](https://www.nuget.org/packages/System.Text.Json/) that support .NET Standard 2.0 and higher, that is, versions 4.6.0-4.7.2, behave inconsistently with the built-in behavior on .NET Core 3.0 and 3.1.</span></span> <span data-ttu-id="322d9-105">В .NET Core 3. x внутренние и закрытые конструкторы можно использовать для десериализации.</span><span class="sxs-lookup"><span data-stu-id="322d9-105">On .NET Core 3.x, internal and private constructors can be used for deserialization.</span></span> <span data-ttu-id="322d9-106">В отдельных пакетах не допускаются конструкторы, не являющиеся открытыми, и создается исключение <xref:System.MissingMethodException>, если не определен открытый конструктор без параметров.</span><span class="sxs-lookup"><span data-stu-id="322d9-106">In the standalone packages, non-public constructors are not allowed, and a <xref:System.MissingMethodException> is thrown if no public, parameterless constructor is defined.</span></span>

<span data-ttu-id="322d9-107">Начиная с .NET 5.0 и версии 5.0.0 пакета NuGet System.Text.Json согласовано поведение между пакетом NuGet и встроенными API.</span><span class="sxs-lookup"><span data-stu-id="322d9-107">Starting with .NET 5.0 and System.Text.Json NuGet package 5.0.0, the behavior is consistent between the NuGet package and the built-in APIs.</span></span> <span data-ttu-id="322d9-108">Сериализатор по умолчанию игнорирует не являющиеся открытыми конструкторы, в том числе конструкторы без параметров.</span><span class="sxs-lookup"><span data-stu-id="322d9-108">Non-public constructors, including parameterless constructors, are ignored by the serializer by default.</span></span> <span data-ttu-id="322d9-109">Сериализатор использует для десериализации один из следующих конструкторов:</span><span class="sxs-lookup"><span data-stu-id="322d9-109">The serializer uses one of the following constructors for deserialization:</span></span>

- <span data-ttu-id="322d9-110">Открытый конструктор, помеченный атрибутом <xref:System.Text.Json.Serialization.JsonConstructorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="322d9-110">Public constructor annotated with <xref:System.Text.Json.Serialization.JsonConstructorAttribute>.</span></span>
- <span data-ttu-id="322d9-111">Открытый конструктор без параметров.</span><span class="sxs-lookup"><span data-stu-id="322d9-111">Public parameterless constructor.</span></span>
- <span data-ttu-id="322d9-112">Открытый параметризованный конструктор (если это единственный открытый конструктор).</span><span class="sxs-lookup"><span data-stu-id="322d9-112">Public parameterized constructor (if it's the only public constructor present).</span></span>

<span data-ttu-id="322d9-113">Если ни один из этих конструкторов не доступен, при попытке десериализовать тип возникает исключение <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="322d9-113">If none of these constructors are available, a <xref:System.NotSupportedException> is thrown if you attempt to deserialize the type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="322d9-114">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="322d9-114">Version introduced</span></span>

<span data-ttu-id="322d9-115">5.0</span><span class="sxs-lookup"><span data-stu-id="322d9-115">5.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="322d9-116">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="322d9-116">Reason for change</span></span>

- <span data-ttu-id="322d9-117">Принудительно обеспечить согласованное поведение между всеми моникерами целевой платформы (TFM), для которых создается <xref:System.Text.Json?displayProperty=fullName> (.NET Core 3.0 и более поздних версий и .NET Standard 2.0)</span><span class="sxs-lookup"><span data-stu-id="322d9-117">To enforce consistent behavior between all target framework monikers (TFMs) that <xref:System.Text.Json?displayProperty=fullName> builds for (.NET Core 3.0 and later versions and .NET Standard 2.0)</span></span>
- <span data-ttu-id="322d9-118">Поскольку <xref:System.Text.Json.JsonSerializer> не должен выполнять вызовы к не являющейся открытой контактной зоне типа, будь то конструктор, свойство или поле.</span><span class="sxs-lookup"><span data-stu-id="322d9-118">Because <xref:System.Text.Json.JsonSerializer> shouldn't call the non-public surface area of a type, whether that's a constructor, a property, or a field.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="322d9-119">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="322d9-119">Recommended action</span></span>

- <span data-ttu-id="322d9-120">Если вы являетесь владельцем типа и это целесообразно, сделайте конструктор без параметров открытым.</span><span class="sxs-lookup"><span data-stu-id="322d9-120">If you own the type and it's feasible, make the parameterless constructor public.</span></span>
- <span data-ttu-id="322d9-121">В противном случае реализуйте для типа `JsonConverter<T>` и обеспечьте контроль десериализации.</span><span class="sxs-lookup"><span data-stu-id="322d9-121">Otherwise, implement a `JsonConverter<T>` for the type and control the deserialization behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="322d9-122">Категория</span><span class="sxs-lookup"><span data-stu-id="322d9-122">Category</span></span>

<span data-ttu-id="322d9-123">Сериализация</span><span class="sxs-lookup"><span data-stu-id="322d9-123">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="322d9-124">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="322d9-124">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
