---
ms.openlocfilehash: 480cbdecd681408a7e1d6fa366e3f1a4b131ab42
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760706"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="8e5ac-101">Теперь поддерживаются категории стандартной версии Юникода 8.0</span><span class="sxs-lookup"><span data-stu-id="8e5ac-101">Unicode standard version 8.0 categories now supported</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8e5ac-102">Подробные сведения</span><span class="sxs-lookup"><span data-stu-id="8e5ac-102">Details</span></span>|<span data-ttu-id="8e5ac-103">В .NET Framework 4.6.2 данные Юникода были обновлены со стандартной версии 6.3 до версии 8.0.</span><span class="sxs-lookup"><span data-stu-id="8e5ac-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="8e5ac-104">При запросе категорий символов Юникода в .NET Framework 4.6.2 некоторые результаты могут не соответствовать результатам в предыдущих версиях .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8e5ac-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="8e5ac-105">Это изменение в первую очередь влияет на слоги языка чероки, а также знаки гласных и обозначения тонов в новой письменности Тай-Лю.</span><span class="sxs-lookup"><span data-stu-id="8e5ac-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>|
|<span data-ttu-id="8e5ac-106">Предложение</span><span class="sxs-lookup"><span data-stu-id="8e5ac-106">Suggestion</span></span>|<span data-ttu-id="8e5ac-107">Просмотрите код и удалите или измените логику, зависящую от жестко заданных категорий символов Юникода.</span><span class="sxs-lookup"><span data-stu-id="8e5ac-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>|
|<span data-ttu-id="8e5ac-108">Область</span><span class="sxs-lookup"><span data-stu-id="8e5ac-108">Scope</span></span>|<span data-ttu-id="8e5ac-109">Дополнительный номер</span><span class="sxs-lookup"><span data-stu-id="8e5ac-109">Minor</span></span>|
|<span data-ttu-id="8e5ac-110">Версия</span><span class="sxs-lookup"><span data-stu-id="8e5ac-110">Version</span></span>|<span data-ttu-id="8e5ac-111">4.6.2</span><span class="sxs-lookup"><span data-stu-id="8e5ac-111">4.6.2</span></span>|
|<span data-ttu-id="8e5ac-112">Тип</span><span class="sxs-lookup"><span data-stu-id="8e5ac-112">Type</span></span>|<span data-ttu-id="8e5ac-113">Среда выполнения</span><span class="sxs-lookup"><span data-stu-id="8e5ac-113">Runtime</span></span>|
|<span data-ttu-id="8e5ac-114">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="8e5ac-114">Affected APIs</span></span>|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|

