---
ms.openlocfilehash: 7a7ecf052276fe8e62463498b83230d466630c79
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616299"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a><span data-ttu-id="082f5-101">Определение рабочего процесса XOML и ключи кэша SqlTrackingService переведены с MD5 на SHA256</span><span class="sxs-lookup"><span data-stu-id="082f5-101">Workflow XOML definition and SqlTrackingService cache keys changed from MD5 to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="082f5-102">Подробнее</span><span class="sxs-lookup"><span data-stu-id="082f5-102">Details</span></span>

<span data-ttu-id="082f5-103">Среда выполнения рабочих процессов хранит кэш определений рабочих процессов, определенных в XOML.</span><span class="sxs-lookup"><span data-stu-id="082f5-103">The Workflow Runtime in keeps a cache of workflow definitions defined in XOML.</span></span> <span data-ttu-id="082f5-104">SqlTrackingService также хранит кэш с ключом по строкам.</span><span class="sxs-lookup"><span data-stu-id="082f5-104">The SqlTrackingService also keeps a cache that is keyed by strings.</span></span> <span data-ttu-id="082f5-105">Эти кэши идентифицируются по значениям, которые включают хэш-значение контрольной суммы.</span><span class="sxs-lookup"><span data-stu-id="082f5-105">These caches are keyed by values that include checksum hash value.</span></span> <span data-ttu-id="082f5-106">В .NET Framework 4.7.2 и более ранних версий для хэширования этой контрольной суммы использовался алгоритм MD5, что приводило к проблемам в системах с поддержкой стандарта FIPS.</span><span class="sxs-lookup"><span data-stu-id="082f5-106">In the .NET Framework 4.7.2 and earlier versions, this checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="082f5-107">Начиная с .NET Framework 4.8 используется алгоритм SHA256. Так как значения вычисляются при каждом запуске среды выполнения рабочих процессов и службы SqlTrackingService, не должно возникнуть проблем совместимости с этим изменением.</span><span class="sxs-lookup"><span data-stu-id="082f5-107">Starting with the .NET Framework 4.8, the algorithm used is SHA256.There shouldn't be a compatibility issue with this change because the values are recalculated each time the Workflow Runtime and SqlTrackingService is started.</span></span> <span data-ttu-id="082f5-108">Тем не менее мы предоставили исправления, чтобы позволить клиентам вернуться к использованию устаревшего алгоритма хэширования при необходимости.</span><span class="sxs-lookup"><span data-stu-id="082f5-108">However, we have provided quirks to allow customers to revert back to usage of the legacy hashing algorithm, if necessary.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="082f5-109">Предложение</span><span class="sxs-lookup"><span data-stu-id="082f5-109">Suggestion</span></span>

<span data-ttu-id="082f5-110">Если это изменение вызывает проблему при выполнении рабочих процессов, установите для одного или обоих параметров `AppContext`:</span><span class="sxs-lookup"><span data-stu-id="082f5-110">If this change presents a problem when executing workflows, try setting one or both of the `AppContext` switches:</span></span>

- <span data-ttu-id="082f5-111">&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; значение true.</span><span class="sxs-lookup"><span data-stu-id="082f5-111">&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; to true.</span></span>
- <span data-ttu-id="082f5-112">&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; значение true.</span><span class="sxs-lookup"><span data-stu-id="082f5-112">&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; to true.</span></span>
<span data-ttu-id="082f5-113">В коде:</span><span class="sxs-lookup"><span data-stu-id="082f5-113">In code:</span></span>

<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>

<span data-ttu-id="082f5-114">Или в файле конфигурации (это необходимо сделать в файле конфигурации приложения, который создает объект <xref:System.Workflow.Runtime.WorkflowRuntime>):</span><span class="sxs-lookup"><span data-stu-id="082f5-114">Or in the configuration file (this needs to be in the config file for the application that is creating the <xref:System.Workflow.Runtime.WorkflowRuntime> object):</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="082f5-115">name</span><span class="sxs-lookup"><span data-stu-id="082f5-115">Name</span></span>    | <span data-ttu-id="082f5-116">Значение</span><span class="sxs-lookup"><span data-stu-id="082f5-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="082f5-117">Область</span><span class="sxs-lookup"><span data-stu-id="082f5-117">Scope</span></span>   | <span data-ttu-id="082f5-118">Дополнительный номер</span><span class="sxs-lookup"><span data-stu-id="082f5-118">Minor</span></span>       |
| <span data-ttu-id="082f5-119">Version</span><span class="sxs-lookup"><span data-stu-id="082f5-119">Version</span></span> | <span data-ttu-id="082f5-120">4.8</span><span class="sxs-lookup"><span data-stu-id="082f5-120">4.8</span></span>         |
| <span data-ttu-id="082f5-121">Type</span><span class="sxs-lookup"><span data-stu-id="082f5-121">Type</span></span>    | <span data-ttu-id="082f5-122">Изменение целевой платформы</span><span class="sxs-lookup"><span data-stu-id="082f5-122">Retargeting</span></span> |
