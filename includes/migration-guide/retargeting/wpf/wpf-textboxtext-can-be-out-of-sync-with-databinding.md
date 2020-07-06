---
ms.openlocfilehash: d0de1a262d57c67dd4dfb258d5ac013af5d8783d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617292"
---
### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a><span data-ttu-id="24a70-101">WPF TextBox.Text может быть не синхронизирован с привязкой данных</span><span class="sxs-lookup"><span data-stu-id="24a70-101">WPF TextBox.Text can be out-of-sync with databinding</span></span>

#### <a name="details"></a><span data-ttu-id="24a70-102">Подробнее</span><span class="sxs-lookup"><span data-stu-id="24a70-102">Details</span></span>

<span data-ttu-id="24a70-103">В некоторых случаях свойство <xref:System.Windows.Controls.TextBox.Text> отражает предыдущее значение привязанного к данным свойства, если свойство изменяется во время операции записи с привязкой к данным.</span><span class="sxs-lookup"><span data-stu-id="24a70-103">In some cases, the <xref:System.Windows.Controls.TextBox.Text> property reflects a previous value of the databound property value if the property is modified during a databinding write operation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="24a70-104">Предложение</span><span class="sxs-lookup"><span data-stu-id="24a70-104">Suggestion</span></span>

<span data-ttu-id="24a70-105">Это не должно иметь отрицательных последствий.</span><span class="sxs-lookup"><span data-stu-id="24a70-105">This should have no negative impact.</span></span> <span data-ttu-id="24a70-106">Однако можно восстановить прежнее поведение, установив свойству <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> значение `false`.</span><span class="sxs-lookup"><span data-stu-id="24a70-106">However, you can restore the previous behavior by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> property to `false`.</span></span>

| <span data-ttu-id="24a70-107">name</span><span class="sxs-lookup"><span data-stu-id="24a70-107">Name</span></span>    | <span data-ttu-id="24a70-108">Значение</span><span class="sxs-lookup"><span data-stu-id="24a70-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="24a70-109">Область</span><span class="sxs-lookup"><span data-stu-id="24a70-109">Scope</span></span>   | <span data-ttu-id="24a70-110">Пограничный случай</span><span class="sxs-lookup"><span data-stu-id="24a70-110">Edge</span></span>        |
| <span data-ttu-id="24a70-111">Version</span><span class="sxs-lookup"><span data-stu-id="24a70-111">Version</span></span> | <span data-ttu-id="24a70-112">4.5</span><span class="sxs-lookup"><span data-stu-id="24a70-112">4.5</span></span>         |
|<span data-ttu-id="24a70-113">Type</span><span class="sxs-lookup"><span data-stu-id="24a70-113">Type</span></span>|<span data-ttu-id="24a70-114">Изменение целевой платформы</span><span class="sxs-lookup"><span data-stu-id="24a70-114">Retargeting</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="24a70-115">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="24a70-115">Affected APIs</span></span>

- <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType>
