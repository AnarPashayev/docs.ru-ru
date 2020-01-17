---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901907"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a><span data-ttu-id="8444b-101">Авторизация. Требование нового метода для реализаций IAuthorizationPolicyProvider</span><span class="sxs-lookup"><span data-stu-id="8444b-101">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>

<span data-ttu-id="8444b-102">В ASP.NET Core 3.0 в `IAuthorizationPolicyProvider` был добавлен новый метод `GetFallbackPolicyAsync`.</span><span class="sxs-lookup"><span data-stu-id="8444b-102">In ASP.NET Core 3.0, a new `GetFallbackPolicyAsync` method was added to `IAuthorizationPolicyProvider`.</span></span> <span data-ttu-id="8444b-103">Эта политика отката используется ПО промежуточного слоя для авторизации, если не указана другая политика.</span><span class="sxs-lookup"><span data-stu-id="8444b-103">This fallback policy is used by the authorization middleware when no policy is specified.</span></span>

<span data-ttu-id="8444b-104">Подробную информацию см. на странице [dotnet/aspnetcore#9759](https://github.com/dotnet/aspnetcore/pull/9759).</span><span class="sxs-lookup"><span data-stu-id="8444b-104">For more information, see [dotnet/aspnetcore#9759](https://github.com/dotnet/aspnetcore/pull/9759).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8444b-105">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="8444b-105">Version introduced</span></span>

<span data-ttu-id="8444b-106">3.0</span><span class="sxs-lookup"><span data-stu-id="8444b-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="8444b-107">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="8444b-107">Old behavior</span></span>

<span data-ttu-id="8444b-108">Реализации `IAuthorizationPolicyProvider` не требовали метод `GetFallbackPolicyAsync`.</span><span class="sxs-lookup"><span data-stu-id="8444b-108">Implementations of `IAuthorizationPolicyProvider` didn't require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="8444b-109">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="8444b-109">New behavior</span></span>

<span data-ttu-id="8444b-110">Реализации `IAuthorizationPolicyProvider` требуют метод `GetFallbackPolicyAsync`.</span><span class="sxs-lookup"><span data-stu-id="8444b-110">Implementations of `IAuthorizationPolicyProvider` require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="8444b-111">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="8444b-111">Reason for change</span></span>

<span data-ttu-id="8444b-112">Новый метод требуется для использования нового ПО `AuthorizationMiddleware`, если политика не указана.</span><span class="sxs-lookup"><span data-stu-id="8444b-112">A new method was needed for the new `AuthorizationMiddleware` to use when no policy is specified.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8444b-113">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="8444b-113">Recommended action</span></span>

<span data-ttu-id="8444b-114">Добавьте метод `GetFallbackPolicyAsync` в реализации `IAuthorizationPolicyProvider`.</span><span class="sxs-lookup"><span data-stu-id="8444b-114">Add the `GetFallbackPolicyAsync` method to your implementations of `IAuthorizationPolicyProvider`.</span></span>

#### <a name="category"></a><span data-ttu-id="8444b-115">Категория</span><span class="sxs-lookup"><span data-stu-id="8444b-115">Category</span></span>

<span data-ttu-id="8444b-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8444b-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8444b-117">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="8444b-117">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
