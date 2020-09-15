---
ms.openlocfilehash: 2aa424ff5e3308b730c22cb865993d4100f193cc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616300"
---
### <a name="workflow-xoml-file-checksums-changed-from-md5-to-sha256"></a><span data-ttu-id="441e7-101">Контрольные суммы файла XOML рабочего процесса переведены с MD5 на SHA256</span><span class="sxs-lookup"><span data-stu-id="441e7-101">Workflow XOML file checksums changed from MD5 to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="441e7-102">Подробнее</span><span class="sxs-lookup"><span data-stu-id="441e7-102">Details</span></span>

<span data-ttu-id="441e7-103">Для поддержки отладки рабочих процессов на основе XOML с помощью Visual Studio при сборке проектов рабочих процессов, содержащих файлы XOML, контрольная сумма содержимого файла XOML включается в сгенерированный код как значение <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="441e7-103">To support debugging XOML-based workflows with Visual Studio, when workflow projects containing XOML files build, a checksum of the contents of the XOML file is included in the code generated as a <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> value.</span></span> <span data-ttu-id="441e7-104">В .NET Framework 4.7.2 и более ранних версий для хэширования этой контрольной суммы использовался алгоритм MD5, что приводило к проблемам в системах с поддержкой стандарта FIPS.</span><span class="sxs-lookup"><span data-stu-id="441e7-104">In the .NET Framework 4.7.2 and earlier versions, this checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="441e7-105">Начиная с .NET Framework 4.8 используется алгоритм SHA256.</span><span class="sxs-lookup"><span data-stu-id="441e7-105">Starting with the .NET Framework 4.8, the algorithm used is SHA256.</span></span> <span data-ttu-id="441e7-106">Для совместимости с WorkflowMarkupSourceAttribute.MD5Digest используются только первые 16 байт сгенерированной контрольной суммы. Это может приводить к проблемам при отладке.</span><span class="sxs-lookup"><span data-stu-id="441e7-106">To be compatibile with the WorkflowMarkupSourceAttribute.MD5Digest, only the first 16 bytes of the generated checksum are used.This may cause problems during debugging.</span></span> <span data-ttu-id="441e7-107">Может потребоваться повторная сборка проекта.</span><span class="sxs-lookup"><span data-stu-id="441e7-107">You may need to re-build your project.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="441e7-108">Предложение</span><span class="sxs-lookup"><span data-stu-id="441e7-108">Suggestion</span></span>

<span data-ttu-id="441e7-109">Если повторная сборка проекта не помогла решить проблему, попробуйте задать для параметра `AppContext`&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; значение true. В коде:</span><span class="sxs-lookup"><span data-stu-id="441e7-109">If re-building your project does not solve the problem, try setting the `AppContext` switch &quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; to true.In code:</span></span>

<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot;, true);&#13;&#10;</code></pre>

<span data-ttu-id="441e7-110">Или в файле конфигурации (это должен быть файл MSBuild.exe.config для используемой программы MSBuild.exe):</span><span class="sxs-lookup"><span data-stu-id="441e7-110">Or in a configuration file (this needs to be in MSBuild.exe.config for the MSBuild.exe that you are using):</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="441e7-111">name</span><span class="sxs-lookup"><span data-stu-id="441e7-111">Name</span></span>    | <span data-ttu-id="441e7-112">Значение</span><span class="sxs-lookup"><span data-stu-id="441e7-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="441e7-113">Область</span><span class="sxs-lookup"><span data-stu-id="441e7-113">Scope</span></span>   | <span data-ttu-id="441e7-114">Дополнительный номер</span><span class="sxs-lookup"><span data-stu-id="441e7-114">Minor</span></span>       |
| <span data-ttu-id="441e7-115">Version</span><span class="sxs-lookup"><span data-stu-id="441e7-115">Version</span></span> | <span data-ttu-id="441e7-116">4.8</span><span class="sxs-lookup"><span data-stu-id="441e7-116">4.8</span></span>         |
| <span data-ttu-id="441e7-117">Type</span><span class="sxs-lookup"><span data-stu-id="441e7-117">Type</span></span>    | <span data-ttu-id="441e7-118">Изменение целевой платформы</span><span class="sxs-lookup"><span data-stu-id="441e7-118">Retargeting</span></span> |
