---
ms.openlocfilehash: edd194fef27d97976f1ff45daec1cd56382bbb55
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804924"
---
### <a name="new-enum-values-in-wpfs-pagerangeselection"></a><span data-ttu-id="5c360-101">Новые значения перечисления в перечислении PageRangeSelection WPF</span><span class="sxs-lookup"><span data-stu-id="5c360-101">New enum values in WPF's PageRangeSelection</span></span>

|   |   |
|---|---|
|<span data-ttu-id="5c360-102">Подробные сведения</span><span class="sxs-lookup"><span data-stu-id="5c360-102">Details</span></span>|<span data-ttu-id="5c360-103">Было добавлено два новых члена (<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=name> и <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=name>) в перечисление <xref:System.Windows.Controls.PageRangeSelection?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="5c360-103">Two new members (<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=name> and <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=name>) have been added to the <xref:System.Windows.Controls.PageRangeSelection?displayProperty=name> enum.</span></span>|
|<span data-ttu-id="5c360-104">Предложение</span><span class="sxs-lookup"><span data-stu-id="5c360-104">Suggestion</span></span>|<span data-ttu-id="5c360-105">В большинстве случаев эти изменения не влияют на код пользователя.</span><span class="sxs-lookup"><span data-stu-id="5c360-105">In most cases, these changes won't impact user code.</span></span> <span data-ttu-id="5c360-106">Однако следует изменить код, зависящий от конкретного числа элементов, существующих в вызовах <xref:System.Enum.GetNames(System.Type)> или <xref:System.Enum.GetValues(System.Type)> к типу <xref:System.Windows.Controls.PageRangeSelection?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="5c360-106">Code that depends on a particular number of elements existing in <xref:System.Enum.GetNames(System.Type)> or <xref:System.Enum.GetValues(System.Type)> calls on the <xref:System.Windows.Controls.PageRangeSelection?displayProperty=name> type should be modified, though.</span></span>|
|<span data-ttu-id="5c360-107">Область</span><span class="sxs-lookup"><span data-stu-id="5c360-107">Scope</span></span>|<span data-ttu-id="5c360-108">Пограничный случай</span><span class="sxs-lookup"><span data-stu-id="5c360-108">Edge</span></span>|
|<span data-ttu-id="5c360-109">Версия</span><span class="sxs-lookup"><span data-stu-id="5c360-109">Version</span></span>|<span data-ttu-id="5c360-110">4.5</span><span class="sxs-lookup"><span data-stu-id="5c360-110">4.5</span></span>|
|<span data-ttu-id="5c360-111">Тип</span><span class="sxs-lookup"><span data-stu-id="5c360-111">Type</span></span>|<span data-ttu-id="5c360-112">Среда выполнения</span><span class="sxs-lookup"><span data-stu-id="5c360-112">Runtime</span></span>|
|<span data-ttu-id="5c360-113">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="5c360-113">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.PageRangeSelection?displayProperty=nameWithType></li></ul>|
