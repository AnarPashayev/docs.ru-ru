---
ms.openlocfilehash: 0fe07ac21effacffc56d37ccb46a121f443acd20
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620172"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a><span data-ttu-id="8bf17-101">Для совместного доступа к состоянию сеанса с Asp.Net StateServer все серверы на веб-ферме должны использовать одинаковую версию .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8bf17-101">Sharing session state with Asp.Net StateServer requires all servers in the web farm to use the same .NET Framework version</span></span>

#### <a name="details"></a><span data-ttu-id="8bf17-102">Подробнее</span><span class="sxs-lookup"><span data-stu-id="8bf17-102">Details</span></span>

<span data-ttu-id="8bf17-103">При включении состояния сеанса <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName> все серверы на данной веб-ферме должны использовать одинаковую версию платформы .NET Framework, чтобы состояние передавалось должным образом.</span><span class="sxs-lookup"><span data-stu-id="8bf17-103">When enabling <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName> session state, all of the servers in the given web farm must use the same version of the .NET Framework in order for state to be properly shared.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8bf17-104">Предложение</span><span class="sxs-lookup"><span data-stu-id="8bf17-104">Suggestion</span></span>

<span data-ttu-id="8bf17-105">Обновите версии платформы .NET Framework на веб-серверах, которые совместно и одновременно используют состояние.</span><span class="sxs-lookup"><span data-stu-id="8bf17-105">Be sure to upgrade .NET Framework versions on web servers that share state at the same time.</span></span>

| <span data-ttu-id="8bf17-106">name</span><span class="sxs-lookup"><span data-stu-id="8bf17-106">Name</span></span>    | <span data-ttu-id="8bf17-107">Значение</span><span class="sxs-lookup"><span data-stu-id="8bf17-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8bf17-108">Область</span><span class="sxs-lookup"><span data-stu-id="8bf17-108">Scope</span></span>   |<span data-ttu-id="8bf17-109">Пограничный случай</span><span class="sxs-lookup"><span data-stu-id="8bf17-109">Edge</span></span>|
|<span data-ttu-id="8bf17-110">Version</span><span class="sxs-lookup"><span data-stu-id="8bf17-110">Version</span></span>|<span data-ttu-id="8bf17-111">4.5</span><span class="sxs-lookup"><span data-stu-id="8bf17-111">4.5</span></span>|
|<span data-ttu-id="8bf17-112">Type</span><span class="sxs-lookup"><span data-stu-id="8bf17-112">Type</span></span>|<span data-ttu-id="8bf17-113">Среда выполнения</span><span class="sxs-lookup"><span data-stu-id="8bf17-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8bf17-114">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="8bf17-114">Affected APIs</span></span>

-<xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType></li></ul>|
