---
title: Устаревшие компоненты в .NET 5 и более поздних версий
description: Сведения об API-интерфейсах, которые помечены как устаревшие в .NET 5.0 и более поздних версий и приводят к созданию предупреждений компилятора SYSLIB.
ms.date: 10/20/2020
ms.openlocfilehash: aa5716ba8fe46c7c4ae2faafe7cc963551eecef7
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440768"
---
# <a name="obsolete-features-in-net-5"></a><span data-ttu-id="7ea4b-103">Устаревшие компоненты в .NET 5 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="7ea4b-103">Obsolete features in .NET 5</span></span>

<span data-ttu-id="7ea4b-104">Начиная с версии .NET 5.0, некоторые помеченные устаревшими API используют два новых свойства для <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-104">Starting in .NET 5.0, some APIs that are newly marked as obsolete make use of two new properties on <xref:System.ObsoleteAttribute>.</span></span>

- <span data-ttu-id="7ea4b-105">Свойство <xref:System.ObsoleteAttribute.DiagnosticId?displayProperty=nameWithType> указывает компилятору создавать предупреждения сборки с помощью пользовательского идентификатора диагностики.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-105">The <xref:System.ObsoleteAttribute.DiagnosticId?displayProperty=nameWithType> property tells the compiler to generate build warnings using a custom diagnostic ID.</span></span> <span data-ttu-id="7ea4b-106">Пользовательский идентификатор позволяет отключать предупреждения об устаревших элементах отдельно друг от друга.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-106">The custom ID allows for obsoletion warning to be suppressed specifically and separately from one another.</span></span> <span data-ttu-id="7ea4b-107">В случае с устаревшими элементами в .NET 5 и более поздних версий пользовательский идентификатор диагностики имеет формат `SYSLIBxxxx`.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-107">In the case of the .NET 5+ obsoletions, the format for the custom diagnostic ID is `SYSLIBxxxx`.</span></span>

- <span data-ttu-id="7ea4b-108">Свойство <xref:System.ObsoleteAttribute.UrlFormat?displayProperty=nameWithType> указывает компилятору включить URL для получения дополнительных сведений об устаревшем элементе.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-108">The <xref:System.ObsoleteAttribute.UrlFormat?displayProperty=nameWithType> property tells the compiler to include a URL link to learn more about the obsoletion.</span></span>

<span data-ttu-id="7ea4b-109">Если вы получаете предупреждения или ошибки сборки из-за использования устаревшего API, следуйте указаниям для идентификатора диагностики в разделе [Справочник](#reference).</span><span class="sxs-lookup"><span data-stu-id="7ea4b-109">If you encounter build warnings or errors due to usage of an obsolete API, follow the specific guidance provided for the diagnostic ID listed in the [Reference](#reference) section.</span></span> <span data-ttu-id="7ea4b-110">Предупреждения или ошибки об этих устаревших элементах *нельзя* отключить с помощью [стандартного идентификатора диагностики (CS0618)](../../csharp/language-reference/compiler-messages/cs0618.md) для устаревших типов или членов. Используйте вместо него пользовательский идентификатор диагностики `SYSLIBxxxx`.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-110">Warnings or errors for these obsoletions *can't* be suppressed using the [standard diagnostic ID (CS0618)](../../csharp/language-reference/compiler-messages/cs0618.md) for obsolete types or members; use the custom `SYSLIBxxxx` diagnostic ID values instead.</span></span> <span data-ttu-id="7ea4b-111">Дополнительные сведения см. в разделе [Отключение предупреждений](#suppress-warnings).</span><span class="sxs-lookup"><span data-stu-id="7ea4b-111">For more information, see [Suppress warnings](#suppress-warnings).</span></span>

## <a name="reference"></a><span data-ttu-id="7ea4b-112">Справочник</span><span class="sxs-lookup"><span data-stu-id="7ea4b-112">Reference</span></span>

<span data-ttu-id="7ea4b-113">В следующей таблице представлен индекс устаревших элементов `SYSLIBxxxx` в .NET 5 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-113">The following table provides an index to the `SYSLIBxxxx` obsoletions in .NET 5+.</span></span>

| <span data-ttu-id="7ea4b-114">ИД диагностики</span><span class="sxs-lookup"><span data-stu-id="7ea4b-114">Diagnostic ID</span></span> | <span data-ttu-id="7ea4b-115">Описание</span><span class="sxs-lookup"><span data-stu-id="7ea4b-115">Description</span></span> |
| - | - |
| [<span data-ttu-id="7ea4b-116">SYSLIB0001</span><span class="sxs-lookup"><span data-stu-id="7ea4b-116">SYSLIB0001</span></span>](syslib0001.md) | <span data-ttu-id="7ea4b-117">Кодировка UTF-7 небезопасна и не должна использоваться.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-117">The UTF-7 encoding is insecure and should not be used.</span></span> <span data-ttu-id="7ea4b-118">Вместо нее рекомендуется использовать UTF-8.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-118">Consider using UTF-8 instead.</span></span> |
| [<span data-ttu-id="7ea4b-119">SYSLIB0002</span><span class="sxs-lookup"><span data-stu-id="7ea4b-119">SYSLIB0002</span></span>](syslib0002.md) | <span data-ttu-id="7ea4b-120"><xref:System.Security.Permissions.PrincipalPermissionAttribute> не учитывается средой выполнения и не должен использоваться.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-120"><xref:System.Security.Permissions.PrincipalPermissionAttribute> is not honored by the runtime and must not be used.</span></span> |
| [<span data-ttu-id="7ea4b-121">SYSLIB0003</span><span class="sxs-lookup"><span data-stu-id="7ea4b-121">SYSLIB0003</span></span>](syslib0003.md) | <span data-ttu-id="7ea4b-122">Управление доступом для кода (CAS) не поддерживается или не учитывается средой выполнения.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-122">Code access security (CAS) is not supported or honored by the runtime.</span></span> |
| [<span data-ttu-id="7ea4b-123">SYSLIB0004</span><span class="sxs-lookup"><span data-stu-id="7ea4b-123">SYSLIB0004</span></span>](syslib0004.md) | <span data-ttu-id="7ea4b-124">Функция области ограниченного выполнения (CER) не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-124">The constrained execution region (CER) feature is not supported.</span></span> |
| [<span data-ttu-id="7ea4b-125">SYSLIB0005</span><span class="sxs-lookup"><span data-stu-id="7ea4b-125">SYSLIB0005</span></span>](syslib0005.md) | <span data-ttu-id="7ea4b-126">Глобальный кэш сборок не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-126">The global assembly cache (GAC) is not supported.</span></span> |
| [<span data-ttu-id="7ea4b-127">SYSLIB0006</span><span class="sxs-lookup"><span data-stu-id="7ea4b-127">SYSLIB0006</span></span>](syslib0006.md) | <span data-ttu-id="7ea4b-128"><xref:System.Threading.Thread.Abort?displayProperty=nameWithType> не поддерживается и вызывает <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-128"><xref:System.Threading.Thread.Abort?displayProperty=nameWithType> is not supported and throws <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="7ea4b-129">SYSLIB0007</span><span class="sxs-lookup"><span data-stu-id="7ea4b-129">SYSLIB0007</span></span>](syslib0007.md) | <span data-ttu-id="7ea4b-130">Реализации этого алгоритма шифрования по умолчанию не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-130">The default implementation of this cryptography algorithm is not supported.</span></span> |
| [<span data-ttu-id="7ea4b-131">SYSLIB0008</span><span class="sxs-lookup"><span data-stu-id="7ea4b-131">SYSLIB0008</span></span>](syslib0008.md) | <span data-ttu-id="7ea4b-132">API <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator> не поддерживается и вызывает <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-132">The <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator> API is not supported and throws <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="7ea4b-133">SYSLIB0009</span><span class="sxs-lookup"><span data-stu-id="7ea4b-133">SYSLIB0009</span></span>](syslib0009.md) | <span data-ttu-id="7ea4b-134">Методы <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType> и <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> не поддерживаются и вызывают <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-134">The <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType> and <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> methods are not supported and throw <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="7ea4b-135">SYSLIB0010</span><span class="sxs-lookup"><span data-stu-id="7ea4b-135">SYSLIB0010</span></span>](syslib0010.md) | <span data-ttu-id="7ea4b-136">Некоторые API удаленного взаимодействия не поддерживаются и вызывают <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-136">Some remoting APIs are not supported and throw <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="7ea4b-137">SYSLIB0011</span><span class="sxs-lookup"><span data-stu-id="7ea4b-137">SYSLIB0011</span></span>](syslib0011.md) | <span data-ttu-id="7ea4b-138">Сериализация <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> устарела и не должна использоваться.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-138"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serialization is obsolete and should not be used.</span></span> |
| [<span data-ttu-id="7ea4b-139">SYSLIB0012</span><span class="sxs-lookup"><span data-stu-id="7ea4b-139">SYSLIB0012</span></span>](syslib0012.md) | <span data-ttu-id="7ea4b-140"><xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> и <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> включены только для обеспечения совместимости с .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-140"><xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> and <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> are only included for .NET Framework compatibility.</span></span> <span data-ttu-id="7ea4b-141">Взамен рекомендуется использовать <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-141">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> instead.</span></span> |

## <a name="suppress-warnings"></a><span data-ttu-id="7ea4b-142">Отключение предупреждений</span><span class="sxs-lookup"><span data-stu-id="7ea4b-142">Suppress warnings</span></span>

<span data-ttu-id="7ea4b-143">Если вам необходимо использовать устаревшие API, а диагностика `SYSLIBxxxx` не возвращает ошибку, можно отключить предупреждение в коде или в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-143">If you must use the obsolete APIs and the `SYSLIBxxxx` diagnostic does not surface as an error, you can suppress the warning in code or in your project file.</span></span>

<span data-ttu-id="7ea4b-144">В коде:</span><span class="sxs-lookup"><span data-stu-id="7ea4b-144">In code:</span></span>

```csharp
// Disable the warning.
#pragma warning disable SYSLIB0001
// Code that uses obsolete API.
...
// Re-enable the warning.
#pragma warning restore SYSLIB0001
```

<span data-ttu-id="7ea4b-145">Файл проекта:</span><span class="sxs-lookup"><span data-stu-id="7ea4b-145">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
   <TargetFramework>net5.0</TargetFramework>
   <!-- NoWarn below suppresses SYSLIB0001 project-wide -->
   <NoWarn>$(NoWarn);SYSLIB0001</NoWarn>
   <!-- To suppress multiple warnings, you can use multiple NoWarn elements -->
   <NoWarn>$(NoWarn);SYSLIB0002</NoWarn>
   <NoWarn>$(NoWarn);SYSLIB0003</NoWarn>
   <!-- Alternatively, you can suppress multiple warnings by using a semicolon-delimited list -->
   <NoWarn>$(NoWarn);SYSLIB0001;SYSLIB0002;SYSLIB0003</NoWarn>
  </PropertyGroup>
</Project>
```

> [!NOTE]
> <span data-ttu-id="7ea4b-146">Таким образом, отключается только конкретное предупреждение об устаревшем элементе.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-146">Suppressing warnings in this way only disables the obsoletion warnings you specify.</span></span> <span data-ttu-id="7ea4b-147">Любые другие предупреждения, в том числе и об устаревших элементах с другими идентификаторами диагностики, не отключаются.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-147">It doesn't disable any other warnings, including obsoletion warnings with different diagnostic IDs.</span></span>
