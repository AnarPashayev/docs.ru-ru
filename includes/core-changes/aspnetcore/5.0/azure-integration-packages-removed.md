---
ms.openlocfilehash: 19ccdb634d4e53ea66c032502f2adb70423ab121
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416279"
---
### <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a><span data-ttu-id="ba63c-101">Azure Пакеты интеграции Azure с префиксом Майкрософт удалены</span><span class="sxs-lookup"><span data-stu-id="ba63c-101">Azure: Microsoft-prefixed Azure integration packages removed</span></span>

<span data-ttu-id="ba63c-102">Следующие пакеты `Microsoft.*`, обеспечивающие интеграцию между ASP.NET Core и пакетами SDK для Azure, не входят в ASP.NET Core 5.0:</span><span class="sxs-lookup"><span data-stu-id="ba63c-102">The following `Microsoft.*` packages that provide integration between ASP.NET Core and Azure SDKs aren't included in ASP.NET Core 5.0:</span></span>

* <span data-ttu-id="ba63c-103">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), который интегрирует [Azure Key Vault](/azure/key-vault/) в [систему конфигурации](/aspnet/core/fundamentals/configuration/).</span><span class="sxs-lookup"><span data-stu-id="ba63c-103">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), which integrates [Azure Key Vault](/azure/key-vault/) into the [Configuration system](/aspnet/core/fundamentals/configuration/).</span></span>
* <span data-ttu-id="ba63c-104">[Microsoft.AspNetCore.Data Protection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), который интегрирует Azure Key Vault в [систему защиты данных ASP.NET Core](/aspnet/core/security/data-protection/introduction).</span><span class="sxs-lookup"><span data-stu-id="ba63c-104">[Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), which integrates Azure Key Vault into the [ASP.NET Core Data Protection system](/aspnet/core/security/data-protection/introduction).</span></span>
* <span data-ttu-id="ba63c-105">[Microsoft.AspNetCore.Data Protection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), который интегрирует [хранилище BLOB-объектов Azure](/azure/storage/blobs/) в систему защиты данных ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="ba63c-105">[Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), which integrates [Azure Blob Storage](/azure/storage/blobs/) into the ASP.NET Core Data Protection system.</span></span>

<span data-ttu-id="ba63c-106">Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span><span class="sxs-lookup"><span data-stu-id="ba63c-106">For discussion on this issue, see [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ba63c-107">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="ba63c-107">Version introduced</span></span>

<span data-ttu-id="ba63c-108">5.0 Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="ba63c-108">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ba63c-109">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="ba63c-109">Old behavior</span></span>

<span data-ttu-id="ba63c-110">Пакеты `Microsoft.*` интегрированных служб Azure с API конфигурации и защиты данных.</span><span class="sxs-lookup"><span data-stu-id="ba63c-110">The `Microsoft.*` packages integrated Azure services with the Configuration and Data Protection APIs.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ba63c-111">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="ba63c-111">New behavior</span></span>

<span data-ttu-id="ba63c-112">Новые пакеты `Azure.*` интегрируют службы Azure с API конфигурации и защиты данных.</span><span class="sxs-lookup"><span data-stu-id="ba63c-112">New `Azure.*` packages integrate Azure services with the Configuration and Data Protection APIs.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ba63c-113">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="ba63c-113">Reason for change</span></span>

<span data-ttu-id="ba63c-114">Изменение внесено, поскольку `Microsoft.*` пакеты:</span><span class="sxs-lookup"><span data-stu-id="ba63c-114">The change was made because the `Microsoft.*` packages were:</span></span>

* <span data-ttu-id="ba63c-115">использовали устаревшие версии пакета SDK Azure;</span><span class="sxs-lookup"><span data-stu-id="ba63c-115">Using outdated versions of the Azure SDK.</span></span> <span data-ttu-id="ba63c-116">Простые обновления не были доступны, поскольку новые версии пакета SDK для Azure включали критические изменения.</span><span class="sxs-lookup"><span data-stu-id="ba63c-116">Simple updates weren't possible because the new versions of the Azure SDK included breaking changes.</span></span>
* <span data-ttu-id="ba63c-117">связаны с расписанием выпуска .NET Core;</span><span class="sxs-lookup"><span data-stu-id="ba63c-117">Tied to the .NET Core release schedule.</span></span> <span data-ttu-id="ba63c-118">Передача прав владения пакетами в группу пакета SDK Azure позволяет обновлять пакеты при обновлении пакета SDK для Azure.</span><span class="sxs-lookup"><span data-stu-id="ba63c-118">Transferring ownership of the packages to the Azure SDK team enables package updates as the Azure SDK is updated.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ba63c-119">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="ba63c-119">Recommended action</span></span>

<span data-ttu-id="ba63c-120">В проектах ASP.NET Core 2.1 или более поздней версии замените старые `Microsoft.*` на новые пакеты `Azure.*`.</span><span class="sxs-lookup"><span data-stu-id="ba63c-120">In ASP.NET Core 2.1 or later projects, replace the old `Microsoft.*` with the new `Azure.*` packages.</span></span>

| <span data-ttu-id="ba63c-121">Прежний вариант</span><span class="sxs-lookup"><span data-stu-id="ba63c-121">Old</span></span> | <span data-ttu-id="ba63c-122">Оператор new</span><span class="sxs-lookup"><span data-stu-id="ba63c-122">New</span></span> |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [<span data-ttu-id="ba63c-123">Azure.Extensions.AspNetCore.DataProtection.Keys</span><span class="sxs-lookup"><span data-stu-id="ba63c-123">Azure.Extensions.AspNetCore.DataProtection.Keys</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [<span data-ttu-id="ba63c-124">Azure.Extensions.AspNetCore.DataProtection.Blobs</span><span class="sxs-lookup"><span data-stu-id="ba63c-124">Azure.Extensions.AspNetCore.DataProtection.Blobs</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [<span data-ttu-id="ba63c-125">Azure.Extensions.AspNetCore.Configuration.Secrets</span><span class="sxs-lookup"><span data-stu-id="ba63c-125">Azure.Extensions.AspNetCore.Configuration.Secrets</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.Configuration.Secrets) |

<span data-ttu-id="ba63c-126">Новые пакеты используют новую версию пакета SDK для Azure, включающую критические изменения.</span><span class="sxs-lookup"><span data-stu-id="ba63c-126">The new packages use a new version of the Azure SDK that includes breaking changes.</span></span> <span data-ttu-id="ba63c-127">Шаблоны общего использования не изменяются.</span><span class="sxs-lookup"><span data-stu-id="ba63c-127">The general usage patterns are unchanged.</span></span> <span data-ttu-id="ba63c-128">Некоторые перегрузки и параметры могут отличаться для адаптации к изменениям в базовых API пакета SDK для Azure.</span><span class="sxs-lookup"><span data-stu-id="ba63c-128">Some overloads and options may differ to adapt to changes in the underlying Azure SDK APIs.</span></span>

<span data-ttu-id="ba63c-129">Старые пакеты будут:</span><span class="sxs-lookup"><span data-stu-id="ba63c-129">The old packages will:</span></span>

* <span data-ttu-id="ba63c-130">поддерживаться командой ASP.NET Core в течение времени существования версий .NET Core 2.1 и 3.1;</span><span class="sxs-lookup"><span data-stu-id="ba63c-130">Be supported by the ASP.NET Core team for the lifetime of .NET Core 2.1 and 3.1.</span></span>
* <span data-ttu-id="ba63c-131">исключены в .NET 5.</span><span class="sxs-lookup"><span data-stu-id="ba63c-131">Not be included in .NET 5.</span></span>

<span data-ttu-id="ba63c-132">Для поддержки при обновлении проекта до версии .NET 5 переходите к пакетам `Azure.*`.</span><span class="sxs-lookup"><span data-stu-id="ba63c-132">When upgrading your project to .NET 5, transition to the `Azure.*` packages to maintain support.</span></span>

#### <a name="category"></a><span data-ttu-id="ba63c-133">Категория</span><span class="sxs-lookup"><span data-stu-id="ba63c-133">Category</span></span>

<span data-ttu-id="ba63c-134">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ba63c-134">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ba63c-135">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="ba63c-135">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
