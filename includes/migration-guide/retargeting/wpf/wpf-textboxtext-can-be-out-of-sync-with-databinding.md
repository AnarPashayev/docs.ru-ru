---
ms.openlocfilehash: 8b0617d8f021a9534289fd7ae8539cd054684862
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234781"
---
### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a><span data-ttu-id="7548f-101">WPF TextBox.Text может быть не синхронизирован с привязкой данных</span><span class="sxs-lookup"><span data-stu-id="7548f-101">WPF TextBox.Text can be out-of-sync with databinding</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7548f-102">Подробные сведения</span><span class="sxs-lookup"><span data-stu-id="7548f-102">Details</span></span>|<span data-ttu-id="7548f-103">В некоторых случаях свойство <xref:System.Windows.Controls.TextBox.Text> отражает предыдущее значение привязанного к данным свойства, если свойство изменяется во время операции записи с привязкой к данным.</span><span class="sxs-lookup"><span data-stu-id="7548f-103">In some cases, the <xref:System.Windows.Controls.TextBox.Text> property reflects a previous value of the databound property value if the property is modified during a databinding write operation.</span></span>|
|<span data-ttu-id="7548f-104">Предложение</span><span class="sxs-lookup"><span data-stu-id="7548f-104">Suggestion</span></span>|<span data-ttu-id="7548f-105">Это не должно иметь отрицательных последствий.</span><span class="sxs-lookup"><span data-stu-id="7548f-105">This should have no negative impact.</span></span> <span data-ttu-id="7548f-106">Однако можно восстановить прежнее поведение, установив свойству <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> значение <code>false</code>.</span><span class="sxs-lookup"><span data-stu-id="7548f-106">However, you can restore the previous behavior by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> property to <code>false</code>.</span></span>|
|<span data-ttu-id="7548f-107">Область</span><span class="sxs-lookup"><span data-stu-id="7548f-107">Scope</span></span>|<span data-ttu-id="7548f-108">Пограничный случай</span><span class="sxs-lookup"><span data-stu-id="7548f-108">Edge</span></span>|
|<span data-ttu-id="7548f-109">Версия</span><span class="sxs-lookup"><span data-stu-id="7548f-109">Version</span></span>|<span data-ttu-id="7548f-110">4.5</span><span class="sxs-lookup"><span data-stu-id="7548f-110">4.5</span></span>|
|<span data-ttu-id="7548f-111">Тип</span><span class="sxs-lookup"><span data-stu-id="7548f-111">Type</span></span>|<span data-ttu-id="7548f-112">Изменение целевой платформы</span><span class="sxs-lookup"><span data-stu-id="7548f-112">Retargeting</span></span>|
|<span data-ttu-id="7548f-113">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="7548f-113">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType></li></ul>|
