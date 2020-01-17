---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901782"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a><span data-ttu-id="7eb08-101">Размещение. Удаление ObjectPoolProvider из зависимостей WebHostBuilder</span><span class="sxs-lookup"><span data-stu-id="7eb08-101">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>

<span data-ttu-id="7eb08-102">В ходе оптимизации ASP.NET Core `ObjectPoolProvider` был удален из основного набора зависимостей.</span><span class="sxs-lookup"><span data-stu-id="7eb08-102">As part of making ASP.NET Core more pay for play, the `ObjectPoolProvider` was removed from the main set of dependencies.</span></span> <span data-ttu-id="7eb08-103">Отдельные компоненты, зависящие от `ObjectPoolProvider`, теперь добавляют его самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="7eb08-103">Specific components relying on `ObjectPoolProvider` now add it themselves.</span></span>

<span data-ttu-id="7eb08-104">Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#5944](https://github.com/dotnet/aspnetcore/issues/5944).</span><span class="sxs-lookup"><span data-stu-id="7eb08-104">For discussion, see [dotnet/aspnetcore#5944](https://github.com/dotnet/aspnetcore/issues/5944).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7eb08-105">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="7eb08-105">Version introduced</span></span>

<span data-ttu-id="7eb08-106">3.0</span><span class="sxs-lookup"><span data-stu-id="7eb08-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="7eb08-107">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="7eb08-107">Old behavior</span></span>

<span data-ttu-id="7eb08-108">`WebHostBuilder` предоставляет `ObjectPoolProvider` по умолчанию в контейнере DI.</span><span class="sxs-lookup"><span data-stu-id="7eb08-108">`WebHostBuilder` provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="7eb08-109">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="7eb08-109">New behavior</span></span>

<span data-ttu-id="7eb08-110">`WebHostBuilder` не предоставляет `ObjectPoolProvider` по умолчанию в контейнере DI.</span><span class="sxs-lookup"><span data-stu-id="7eb08-110">`WebHostBuilder` no longer provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7eb08-111">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="7eb08-111">Reason for change</span></span>

<span data-ttu-id="7eb08-112">Это изменение было внесено для оптимизации ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="7eb08-112">This change was made to make ASP.NET Core more pay for play.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7eb08-113">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="7eb08-113">Recommended action</span></span>

<span data-ttu-id="7eb08-114">Если компонент требует `ObjectPoolProvider`, его необходимо добавить в зависимости с помощью `IServiceCollection`.</span><span class="sxs-lookup"><span data-stu-id="7eb08-114">If your component requires `ObjectPoolProvider`, it needs to be added to your dependencies via the `IServiceCollection`.</span></span>

#### <a name="category"></a><span data-ttu-id="7eb08-115">Категория</span><span class="sxs-lookup"><span data-stu-id="7eb08-115">Category</span></span>

<span data-ttu-id="7eb08-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7eb08-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7eb08-117">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="7eb08-117">Affected APIs</span></span>

<span data-ttu-id="7eb08-118">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="7eb08-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
