---
ms.openlocfilehash: fa472b3a142f55f0cbdd83eabbbb00bddd9786d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235886"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a><span data-ttu-id="7342f-101">Параметр MinFreeMemoryPercentageToActiveService теперь учитывается</span><span class="sxs-lookup"><span data-stu-id="7342f-101">MinFreeMemoryPercentageToActiveService is now respected</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7342f-102">Подробные сведения</span><span class="sxs-lookup"><span data-stu-id="7342f-102">Details</span></span>|<span data-ttu-id="7342f-103">Этот параметр задает минимальный объем памяти, который должен быть доступен на сервере перед активацией службы WCF.</span><span class="sxs-lookup"><span data-stu-id="7342f-103">This setting establishes the minimum memory that must be available on the server before a WCF service can be activated.</span></span> <span data-ttu-id="7342f-104">Он предназначен для предотвращения исключений <xref:System.OutOfMemoryException?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="7342f-104">It is designed to prevent <xref:System.OutOfMemoryException?displayProperty=name> exceptions.</span></span> <span data-ttu-id="7342f-105">В .NET Framework 4.5 этот параметр не оказывал никакого влияния.</span><span class="sxs-lookup"><span data-stu-id="7342f-105">In the .NET Framework 4.5, this setting had no effect.</span></span> <span data-ttu-id="7342f-106">В .NET Framework 4.5.1 этот параметр уже используется.</span><span class="sxs-lookup"><span data-stu-id="7342f-106">In the .NET Framework 4.5.1, the setting is observed.</span></span>|
|<span data-ttu-id="7342f-107">Предложение</span><span class="sxs-lookup"><span data-stu-id="7342f-107">Suggestion</span></span>|<span data-ttu-id="7342f-108">Исключение возникает, если объем свободной памяти на веб-сервере меньше процентного значения, заданного параметром конфигурации.</span><span class="sxs-lookup"><span data-stu-id="7342f-108">An exception occurs if the free memory available on the web server is less than the percentage defined by the configuration setting.</span></span> <span data-ttu-id="7342f-109">Некоторые службы WCF, которые успешно запускались и выполнялись в условиях ограниченной памяти, теперь могут завершаться ошибкой.</span><span class="sxs-lookup"><span data-stu-id="7342f-109">Some WCF services that successfully started and ran in a constrained memory environment may now fail.</span></span>|
|<span data-ttu-id="7342f-110">Область</span><span class="sxs-lookup"><span data-stu-id="7342f-110">Scope</span></span>|<span data-ttu-id="7342f-111">Дополнительный номер</span><span class="sxs-lookup"><span data-stu-id="7342f-111">Minor</span></span>|
|<span data-ttu-id="7342f-112">Версия</span><span class="sxs-lookup"><span data-stu-id="7342f-112">Version</span></span>|<span data-ttu-id="7342f-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="7342f-113">4.5.1</span></span>|
|<span data-ttu-id="7342f-114">Тип</span><span class="sxs-lookup"><span data-stu-id="7342f-114">Type</span></span>|<span data-ttu-id="7342f-115">Среда выполнения</span><span class="sxs-lookup"><span data-stu-id="7342f-115">Runtime</span></span>|
