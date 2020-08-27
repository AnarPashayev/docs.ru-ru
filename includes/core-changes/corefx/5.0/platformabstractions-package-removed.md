---
ms.openlocfilehash: a635e2ed6a735b5234c92fd8f5ffa1685fe9373e
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558190"
---
### <a name="microsoftdotnetplatformabstractions-package-removed"></a><span data-ttu-id="51a84-101">Удален пакет Microsoft.DotNet.PlatformAbstractions</span><span class="sxs-lookup"><span data-stu-id="51a84-101">Microsoft.DotNet.PlatformAbstractions package removed</span></span>

<span data-ttu-id="51a84-102">Создание новых версий [Microsoft.DotNet.PlatformAbstractions NuGet package](https://www.nuget.org/packages/Microsoft.DotNet.PlatformAbstractions/) не предусматривается.</span><span class="sxs-lookup"><span data-stu-id="51a84-102">No new versions of the [Microsoft.DotNet.PlatformAbstractions NuGet package](https://www.nuget.org/packages/Microsoft.DotNet.PlatformAbstractions/) will be produced.</span></span>

#### <a name="change-description"></a><span data-ttu-id="51a84-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="51a84-103">Change description</span></span>

<span data-ttu-id="51a84-104">Ранее новые версии библиотеки <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> создавались вместе с новыми версиями .NET Core.</span><span class="sxs-lookup"><span data-stu-id="51a84-104">Previously, new versions of the <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> library were produced alongside new versions of .NET Core.</span></span> <span data-ttu-id="51a84-105">В дальнейшем добавление новых функций в библиотеку не предусматривается, как и выпуск новых основных версий.</span><span class="sxs-lookup"><span data-stu-id="51a84-105">Going forward, no new functionality will be added to the library, and no new major versions will be released.</span></span> <span data-ttu-id="51a84-106">Однако работа и обслуживание существующих версий библиотеки не прекращаются.</span><span class="sxs-lookup"><span data-stu-id="51a84-106">However, existing versions of the library will continue to work and be serviced.</span></span>

<span data-ttu-id="51a84-107">Библиотека <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> пересекается с интерфейсами API, которые уже установлены в пространствах имен System\*.</span><span class="sxs-lookup"><span data-stu-id="51a84-107">The <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> library overlaps with APIs that are already established in the System.\* namespaces.</span></span> <span data-ttu-id="51a84-108">Кроме того, некоторые API <xref:Microsoft.DotNet.PlatformAbstractions> не разрабатывались с тем же уровнем детализации и не были рассчитаны на такую же долгосрочную поддержку, что и остальная часть System.\* Необходимо загрузить и установить пакет NuGet LINQ to Twitter для работы с этим учебником.</span><span class="sxs-lookup"><span data-stu-id="51a84-108">Also, some <xref:Microsoft.DotNet.PlatformAbstractions> APIs weren't designed with the same level of scrutiny and long-term supportability as the rest of the System.\* APIs.</span></span> <span data-ttu-id="51a84-109">Например, <xref:Microsoft.DotNet.PlatformAbstractions> использует перечисление `Platform` для описания текущей платформы операционной системы.</span><span class="sxs-lookup"><span data-stu-id="51a84-109">For example, <xref:Microsoft.DotNet.PlatformAbstractions> uses the `Platform` enumeration to describe the current operating system platform.</span></span> <span data-ttu-id="51a84-110">От такой модели перечисления отказались при разработке API <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType>, чтобы обеспечить поддержку новых платформ и гибкую настройку с учетом новых возможностей.</span><span class="sxs-lookup"><span data-stu-id="51a84-110">This enumeration design was explicitly rejected when the <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> API was designed, to allow for new platforms and future flexibility.</span></span>

<span data-ttu-id="51a84-111">Сценарии, которые активируются библиотекой <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName>, теперь могут обходиться без нее.</span><span class="sxs-lookup"><span data-stu-id="51a84-111">The scenarios enabled by the <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> library are now possible without it.</span></span> <span data-ttu-id="51a84-112">Существующие версии будут продолжать работать даже в .NET 5.0 и более поздних версиях и обслуживаться наряду с предыдущими версиями .NET Core.</span><span class="sxs-lookup"><span data-stu-id="51a84-112">Existing versions will continue to work, even in .NET 5.0 and later, and will be serviced along with previous versions of .NET Core.</span></span> <span data-ttu-id="51a84-113">Однако новые функции в библиотеку не добавляются.</span><span class="sxs-lookup"><span data-stu-id="51a84-113">However, new functionality won't be added to the library.</span></span> <span data-ttu-id="51a84-114">Вместо этого новые функции будут добавляться в другие библиотеки и API-интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="51a84-114">Instead, new functionality will be added to other libraries and APIs.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="51a84-115">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="51a84-115">Version introduced</span></span>

<span data-ttu-id="51a84-116">5.0, предварительная версия 6</span><span class="sxs-lookup"><span data-stu-id="51a84-116">5.0 Preview 6</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="51a84-117">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="51a84-117">Recommended action</span></span>

- <span data-ttu-id="51a84-118">Вы сможете по-прежнему использовать более ранние версии библиотеки, если они соответствуют вашим требованиям.</span><span class="sxs-lookup"><span data-stu-id="51a84-118">You can continue to use older versions of the library if they meet your requirements.</span></span>

- <span data-ttu-id="51a84-119">Если старые версии не соответствуют вашим требованиям, замените используемые API `PlatformAbstractions` на рекомендованные версии.</span><span class="sxs-lookup"><span data-stu-id="51a84-119">If the older versions don't meet your requirements, replace usages of the `PlatformAbstractions` APIs with the recommended replacements.</span></span>

  | <span data-ttu-id="51a84-120">API `PlatformAbstractions`</span><span class="sxs-lookup"><span data-stu-id="51a84-120">`PlatformAbstractions` API</span></span> | <span data-ttu-id="51a84-121">Рекомендуемая замена</span><span class="sxs-lookup"><span data-stu-id="51a84-121">Recommended replacement</span></span> |
  |-|-|
  | `ApplicationEnvironment.ApplicationBasePath` | <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> |
  | <xref:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner> | <xref:System.HashCode?displayProperty=nameWithType> |
  | `RuntimeEnvironment.GetRuntimeIdentifier()` | <xref:System.Runtime.InteropServices.RuntimeInformation.RuntimeIdentifier?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemPlatform` | <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> |
  | `RuntimeEnvironment.RuntimeArchitecture` | <xref:System.Runtime.InteropServices.RuntimeInformation.ProcessArchitecture?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystem` | <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemVersion` | <span data-ttu-id="51a84-122"><xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> и <xref:System.Environment.OSVersion?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="51a84-122"><xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> and <xref:System.Environment.OSVersion?displayProperty=nameWithType></span></span> |

  > [!NOTE]
  > <span data-ttu-id="51a84-123">Большинство сценариев использования `RuntimeEnvironment.OperatingSystem` и `RuntimeEnvironment.OperatingSystemVersion` ориентированы на отображение, например на отображение для пользователя, ведение журнала и телеметрических данных.</span><span class="sxs-lookup"><span data-stu-id="51a84-123">Most use cases for `RuntimeEnvironment.OperatingSystem` and `RuntimeEnvironment.OperatingSystemVersion` are for display purposes, for example, displaying to a user, logging, and telemetry.</span></span> <span data-ttu-id="51a84-124">Не рекомендуется принимать решения по среде выполнения, основываясь на версии операционной системы (ОС).</span><span class="sxs-lookup"><span data-stu-id="51a84-124">It's not recommended to make run-time decisions based on an operating system (OS) version.</span></span> <span data-ttu-id="51a84-125"><xref:System.Environment.OSVersion?displayProperty=nameWithType> теперь [возвращает верную версию](../../../../docs/core/compatibility/corefx.md#environmentosversion-returns-the-correct-operating-system-version) для операционных систем Windows и macOS.</span><span class="sxs-lookup"><span data-stu-id="51a84-125"><xref:System.Environment.OSVersion?displayProperty=nameWithType> now [returns the correct version](../../../../docs/core/compatibility/corefx.md#environmentosversion-returns-the-correct-operating-system-version) for Windows and macOS operating systems.</span></span> <span data-ttu-id="51a84-126">Однако в отношении большинства дистрибутивов Unix "версия ОС" не является однозначным понятием.</span><span class="sxs-lookup"><span data-stu-id="51a84-126">However, for most Unix distributions, what is considered to be the "OS version" is not as straightforward.</span></span> <span data-ttu-id="51a84-127">Например, она может указывать на версию ядра Linux или версию дистрибутива.</span><span class="sxs-lookup"><span data-stu-id="51a84-127">For example, it could be the Linux kernel version, or it could be the distro version.</span></span> <span data-ttu-id="51a84-128">Для большинства платформ Unix <xref:System.Environment.OSVersion?displayProperty=nameWithType> и <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> возвращают версию, которая возвращается `uname`.</span><span class="sxs-lookup"><span data-stu-id="51a84-128">For most Unix platforms, <xref:System.Environment.OSVersion?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> return the version that's returned by `uname`.</span></span> <span data-ttu-id="51a84-129">Сведения об имени и версии дистрибутива Linux приведены в файле */etc/os-release*.</span><span class="sxs-lookup"><span data-stu-id="51a84-129">To get the Linux distro name and version information, the recommended approach is to read the */etc/os-release* file.</span></span>

#### <a name="category"></a><span data-ttu-id="51a84-130">Категория</span><span class="sxs-lookup"><span data-stu-id="51a84-130">Category</span></span>

<span data-ttu-id="51a84-131">Библиотеки Core .NET</span><span class="sxs-lookup"><span data-stu-id="51a84-131">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="51a84-132">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="51a84-132">Affected APIs</span></span>

- `Microsoft.DotNet.PlatformAbstractions.ApplicationEnvironment.ApplicationBasePath`
- <xref:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner?displayProperty=fullName>
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.GetRuntimeIdentifier()`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystem`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemPlatform`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemVersion`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.RuntimeArchitecture`

<!--

#### Affected APIs

- `P:Microsoft.DotNet.PlatformAbstractions.ApplicationEnvironment.ApplicationBasePath`
- `T:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner`
- `M:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.GetRuntimeIdentifier`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystem`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemPlatform`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemVersion`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.RuntimeArchitecture`

-->
