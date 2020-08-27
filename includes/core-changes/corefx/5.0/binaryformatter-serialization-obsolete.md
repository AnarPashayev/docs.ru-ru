---
ms.openlocfilehash: 7cb146d19486618a4cee9976abe2220ea4b72790
ms.sourcegitcommit: d337df55f83325918cbbd095eb573400bea49064
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2020
ms.locfileid: "88204094"
---
### <a name="binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps"></a><span data-ttu-id="45e4f-101">Методы сериализации BinaryFormatter устарели и запрещены в приложениях ASP.NET</span><span class="sxs-lookup"><span data-stu-id="45e4f-101">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>

<span data-ttu-id="45e4f-102">Методы `Serialize` и `Deserialize` в <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, <xref:System.Runtime.Serialization.Formatter> и <xref:System.Runtime.Serialization.IFormatter> теперь считаются устаревшими.</span><span class="sxs-lookup"><span data-stu-id="45e4f-102">`Serialize` and `Deserialize` methods on <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, <xref:System.Runtime.Serialization.Formatter>, and <xref:System.Runtime.Serialization.IFormatter> are now obsolete.</span></span> <span data-ttu-id="45e4f-103">Кроме того, сериализация <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> по умолчанию запрещена для приложений ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="45e4f-103">Additionally, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serialization is prohibited by default for ASP.NET apps.</span></span>

#### <a name="change-description"></a><span data-ttu-id="45e4f-104">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="45e4f-104">Change description</span></span>

<span data-ttu-id="45e4f-105">Из-за [уязвимостей системы безопасности](../../../../docs/standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) в <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> следующие методы считаются устаревшими.</span><span class="sxs-lookup"><span data-stu-id="45e4f-105">Due to [security vulnerabilities](../../../../docs/standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) in <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, the following methods are now obsolete.</span></span> <span data-ttu-id="45e4f-106">Кроме того, в приложениях ASP.NET Core 5.0 и более поздних версий они вызовут исключение <xref:System.NotSupportedException>, если только веб-приложение не включило повторно функциональные возможности <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span><span class="sxs-lookup"><span data-stu-id="45e4f-106">Additionally, in ASP.NET Core 5.0 and later apps, they will throw a <xref:System.NotSupportedException>, unless the web app has re-enabled <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> functionality.</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>

<span data-ttu-id="45e4f-107">Эти методы объявлены устаревшими в рамках мер по отказу от использования <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> в экосистеме .NET.</span><span class="sxs-lookup"><span data-stu-id="45e4f-107">These methods are marked obsolete as part of an effort to wind down usage of <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> within the .NET ecosystem.</span></span>

<span data-ttu-id="45e4f-108">Следующие методы сериализации также считаются устаревшими, но изменений в их поведении не произошло:</span><span class="sxs-lookup"><span data-stu-id="45e4f-108">The following serialization methods are also now obsolete, but have no behavioral changes:</span></span>

- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

#### <a name="version-introduced"></a><span data-ttu-id="45e4f-109">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="45e4f-109">Version introduced</span></span>

<span data-ttu-id="45e4f-110">5.0, предварительная версия 8</span><span class="sxs-lookup"><span data-stu-id="45e4f-110">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="45e4f-111">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="45e4f-111">Recommended action</span></span>

- <span data-ttu-id="45e4f-112">Не используйте в коде <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span><span class="sxs-lookup"><span data-stu-id="45e4f-112">Stop using <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> in your code.</span></span> <span data-ttu-id="45e4f-113">Рассмотрите возможность использования <xref:System.Text.Json.JsonSerializer> или <xref:System.Xml.Serialization.XmlSerializer> вместо них.</span><span class="sxs-lookup"><span data-stu-id="45e4f-113">Instead, consider using <xref:System.Text.Json.JsonSerializer> or <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="45e4f-114">Дополнительные сведения см. в статье [Руководство по безопасности BinaryFormatter](../../../../docs/standard/serialization/binaryformatter-security-guide.md).</span><span class="sxs-lookup"><span data-stu-id="45e4f-114">For more information, see [BinaryFormatter security guide](../../../../docs/standard/serialization/binaryformatter-security-guide.md).</span></span>

- <span data-ttu-id="45e4f-115">Можно временно отключить появляющееся во время компиляции предупреждение об использовании <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> (`SYSLIB0011`).</span><span class="sxs-lookup"><span data-stu-id="45e4f-115">You can temporarily suppress the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> compile-time warning, which is `SYSLIB0011`.</span></span> <span data-ttu-id="45e4f-116">Перед этим мы рекомендуем тщательно оценить риски для кода.</span><span class="sxs-lookup"><span data-stu-id="45e4f-116">We recommend that you thoroughly assess your code for risks before choosing this option.</span></span> <span data-ttu-id="45e4f-117">Самый простой способ отключить предупреждения — обособить отдельные места вызова директивами `#pragma`.</span><span class="sxs-lookup"><span data-stu-id="45e4f-117">The easiest way to suppress the warnings is to surround the individual call site with `#pragma` directives.</span></span>

  ```csharp
  // Now read the purchase order back from disk
  using (var readStream = new FileStream("myfile.bin", FileMode.Open))
  {
      var formatter = new BinaryFormatter();
  #pragma warning disable SYSLIB0011
      return (PurchaseOrder)formatter.Deserialize(readStream);
  #pragma warning restore SYSLIB0011
  }
  ```

  <span data-ttu-id="45e4f-118">Предупреждение можно также отключить в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="45e4f-118">You can also suppress the warning in the project file.</span></span>

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "BinaryFormatter is obsolete" warnings for entire project -->
    <NoWarn>$(NoWarn);SYSLIB0011</NoWarn>
  </PropertyGroup>
  ```

  <span data-ttu-id="45e4f-119">В этом случае предупреждение будет отключено во всех файлах с кодом в проекте.</span><span class="sxs-lookup"><span data-stu-id="45e4f-119">If you suppress the warning in the project file, the warning is suppressed for all code files in the project.</span></span> <span data-ttu-id="45e4f-120">Подавление SYSLIB0011 не приводит к отключению предупреждений, вызванных использованием других устаревших API.</span><span class="sxs-lookup"><span data-stu-id="45e4f-120">Suppressing SYSLIB0011 does not suppress warnings caused by using other obsolete APIs.</span></span>

- <span data-ttu-id="45e4f-121">Чтобы продолжить использование <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> в приложениях ASP.NET, можно повторно включить их в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="45e4f-121">To continue using <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> in ASP.NET apps, you can re-enable it in the project file.</span></span> <span data-ttu-id="45e4f-122">Но делать это настоятельно не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="45e4f-122">However, it's strongly recommended not to do this.</span></span> <span data-ttu-id="45e4f-123">Дополнительные сведения см. в статье [Руководство по безопасности BinaryFormatter](../../../../docs/standard/serialization/binaryformatter-security-guide.md).</span><span class="sxs-lookup"><span data-stu-id="45e4f-123">For more information, see [BinaryFormatter security guide](../../../../docs/standard/serialization/binaryformatter-security-guide.md).</span></span>

  ```xml
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Warning: Setting the following switch is *NOT* recommended in web apps. -->
    <EnableUnsafeBinaryFormatterSerialization>true</EnableUnsafeBinaryFormatterSerialization>
  </PropertyGroup>
  ```

<span data-ttu-id="45e4f-124">Дополнительные сведения о рекомендуемых действиях см. в статье [Устранение ошибок, связанных с устареванием и отключением BinaryFormatter](https://aka.ms/binaryformatter).</span><span class="sxs-lookup"><span data-stu-id="45e4f-124">For more information about recommended actions, see [Resolving BinaryFormatter obsoletion and disablement errors](https://aka.ms/binaryformatter).</span></span>

#### <a name="category"></a><span data-ttu-id="45e4f-125">Категория</span><span class="sxs-lookup"><span data-stu-id="45e4f-125">Category</span></span>

- <span data-ttu-id="45e4f-126">Библиотеки Core .NET</span><span class="sxs-lookup"><span data-stu-id="45e4f-126">Core .NET libraries</span></span>
- <span data-ttu-id="45e4f-127">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="45e4f-127">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="45e4f-128">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="45e4f-128">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize`
- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`
- `M:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)`
- `M:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)`

-->
