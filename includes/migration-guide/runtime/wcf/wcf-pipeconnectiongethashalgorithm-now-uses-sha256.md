---
ms.openlocfilehash: 318609c15d2e0b9a7ee59b38463735b33ef87974
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236218"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="0a0f1-101">WCF PipeConnection.GetHashAlgorithm теперь использует SHA256</span><span class="sxs-lookup"><span data-stu-id="0a0f1-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0a0f1-102">Подробные сведения</span><span class="sxs-lookup"><span data-stu-id="0a0f1-102">Details</span></span>|<span data-ttu-id="0a0f1-103">Начиная с версии .NET Framework 4.7.1 Windows Communication Foundation использует хэш SHA256 для формирования случайных имен для именованных каналов.</span><span class="sxs-lookup"><span data-stu-id="0a0f1-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="0a0f1-104">В .NET Framework 4.7 и более ранних версиях используется хэш SHA-1.</span><span class="sxs-lookup"><span data-stu-id="0a0f1-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>|
|<span data-ttu-id="0a0f1-105">Предложение</span><span class="sxs-lookup"><span data-stu-id="0a0f1-105">Suggestion</span></span>|<span data-ttu-id="0a0f1-106">Если из-за этого изменения в .NET Framework 4.7.1 или более поздних версий вы сталкиваетесь с проблемами совместимости, вы можете отключить это изменение, добавив следующую строку в раздел <code>&lt;runtime&gt;</code> файла app.config:</span><span class="sxs-lookup"><span data-stu-id="0a0f1-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the <code>&lt;runtime&gt;</code> section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="0a0f1-107">Область</span><span class="sxs-lookup"><span data-stu-id="0a0f1-107">Scope</span></span>|<span data-ttu-id="0a0f1-108">Дополнительный номер</span><span class="sxs-lookup"><span data-stu-id="0a0f1-108">Minor</span></span>|
|<span data-ttu-id="0a0f1-109">Версия</span><span class="sxs-lookup"><span data-stu-id="0a0f1-109">Version</span></span>|<span data-ttu-id="0a0f1-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="0a0f1-110">4.7.1</span></span>|
|<span data-ttu-id="0a0f1-111">Тип</span><span class="sxs-lookup"><span data-stu-id="0a0f1-111">Type</span></span>|<span data-ttu-id="0a0f1-112">Среда выполнения</span><span class="sxs-lookup"><span data-stu-id="0a0f1-112">Runtime</span></span>|
