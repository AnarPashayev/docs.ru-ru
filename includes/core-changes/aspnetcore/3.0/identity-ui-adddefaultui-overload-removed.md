---
ms.openlocfilehash: e77312605ee367c159171e305d8f69429f9ac58b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539614"
---
### <a name="identity-adddefaultui-method-overload-removed"></a><span data-ttu-id="cd974-101">Удостоверение: перегрузка метода AddDefaultUI устранена</span><span class="sxs-lookup"><span data-stu-id="cd974-101">Identity: AddDefaultUI method overload removed</span></span>

<span data-ttu-id="cd974-102">Начиная с ASP.NET Core 3.0, перегрузка метода [IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)](/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_) больше не существует.</span><span class="sxs-lookup"><span data-stu-id="cd974-102">Starting with ASP.NET Core 3.0, the [IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)](/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_) method overload no longer exists.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cd974-103">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="cd974-103">Version introduced</span></span>

<span data-ttu-id="cd974-104">3.0</span><span class="sxs-lookup"><span data-stu-id="cd974-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="cd974-105">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="cd974-105">Reason for change</span></span>

<span data-ttu-id="cd974-106">Это изменение было результатом внедрения функции статических веб-ресурсов.</span><span class="sxs-lookup"><span data-stu-id="cd974-106">This change was a result of adoption of the static web assets feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cd974-107">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="cd974-107">Recommended action</span></span>

<span data-ttu-id="cd974-108">Вызывайте <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> вместо перегрузки, принимающей два аргумента.</span><span class="sxs-lookup"><span data-stu-id="cd974-108">Call <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> instead of the overload that takes two arguments.</span></span> <span data-ttu-id="cd974-109">Если вы используете Bootstrap 3, добавьте следующую строку в элемент `<PropertyGroup>` в файле проекта:</span><span class="sxs-lookup"><span data-stu-id="cd974-109">If you're using Bootstrap 3, also add the following line to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="cd974-110">Категория</span><span class="sxs-lookup"><span data-stu-id="cd974-110">Category</span></span>

<span data-ttu-id="cd974-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cd974-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cd974-112">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="cd974-112">Affected APIs</span></span>

[<span data-ttu-id="cd974-113">IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)</span><span class="sxs-lookup"><span data-stu-id="cd974-113">IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)</span></span>](/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
