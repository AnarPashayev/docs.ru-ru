---
ms.openlocfilehash: 0b2d3c1383246d4259c6d906ecf9dab927f4bdb1
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721763"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a><span data-ttu-id="1ae40-101">Шрифт элемента управления по умолчанию изменен на Segoe UI 9 пт</span><span class="sxs-lookup"><span data-stu-id="1ae40-101">Default control font changed to Segoe UI 9 pt</span></span>

#### <a name="change-description"></a><span data-ttu-id="1ae40-102">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="1ae40-102">Change description</span></span>

<span data-ttu-id="1ae40-103">В .NET Framework свойству <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> присвоено значение `Microsoft Sans Serif 8 pt`.</span><span class="sxs-lookup"><span data-stu-id="1ae40-103">In .NET Framework, the <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> property was set to `Microsoft Sans Serif 8 pt`.</span></span> <span data-ttu-id="1ae40-104">На следующем рисунке показано окно, в котором используется шрифт по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="1ae40-104">The following image shows a window that uses the default font.</span></span>

![Шрифт по умолчанию для элемента управления в .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

<span data-ttu-id="1ae40-106">Начиная с .NET Core 3.0 шрифтом по умолчанию является `Segoe UI 9 pt` (тот же шрифт, что и <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="1ae40-106">Starting in .NET Core 3.0, the default font is set to `Segoe UI 9 pt` (the same font as <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span></span> <span data-ttu-id="1ae40-107">В результате этого изменения размер форм и элементов управления увеличен на 27 % с учетом увеличенного размера нового шрифта по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="1ae40-107">As a result of this change, forms and controls are sized about 27% larger to account for the larger size of the new default font.</span></span> <span data-ttu-id="1ae40-108">Пример:</span><span class="sxs-lookup"><span data-stu-id="1ae40-108">For example:</span></span>

![Шрифт по умолчанию для элемента управления в .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

<span data-ttu-id="1ae40-110">Это изменение было внесено в соответствии с [рекомендациями по пользовательскому интерфейсу Windows](/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span><span class="sxs-lookup"><span data-stu-id="1ae40-110">This change was made to align with [Windows user experience (UX) guidelines](/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1ae40-111">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1ae40-111">Version introduced</span></span>

<span data-ttu-id="1ae40-112">3,0</span><span class="sxs-lookup"><span data-stu-id="1ae40-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1ae40-113">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="1ae40-113">Recommended action</span></span>

<span data-ttu-id="1ae40-114">Так как размер форм и элементов управления изменился, убедитесь, что приложение отображается правильно.</span><span class="sxs-lookup"><span data-stu-id="1ae40-114">Because of the change in the size of forms and controls, ensure that your application renders correctly.</span></span>

<span data-ttu-id="1ae40-115">Чтобы оставить исходный шрифт, задайте для формы шрифт по умолчанию: `Microsoft Sans Serif 8 pt`.</span><span class="sxs-lookup"><span data-stu-id="1ae40-115">To retain the original font, set your form's default font to `Microsoft Sans Serif 8 pt`.</span></span> <span data-ttu-id="1ae40-116">Пример:</span><span class="sxs-lookup"><span data-stu-id="1ae40-116">For example:</span></span>

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a><span data-ttu-id="1ae40-117">Категория</span><span class="sxs-lookup"><span data-stu-id="1ae40-117">Category</span></span>

- <span data-ttu-id="1ae40-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1ae40-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1ae40-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="1ae40-119">Affected APIs</span></span>

<span data-ttu-id="1ae40-120">Нет.</span><span class="sxs-lookup"><span data-stu-id="1ae40-120">None.</span></span>

<!--

#### Affected APIs

- Not detectable via API analysis

-->
