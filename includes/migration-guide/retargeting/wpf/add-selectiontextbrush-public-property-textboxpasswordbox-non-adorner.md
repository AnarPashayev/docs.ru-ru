---
ms.openlocfilehash: aade03c29ff16053a97683499cf719a98ae33f3f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616308"
---
### <a name="add-selectiontextbrush-public-property-to-textboxpasswordbox-non-adorner-selection"></a><span data-ttu-id="dfaf0-101">Добавление открытого свойства SelectionTextBrush при выделении текстового поля или поля пароля без графического элемента</span><span class="sxs-lookup"><span data-stu-id="dfaf0-101">Add SelectionTextBrush public property to TextBox/PasswordBox non-adorner selection</span></span>

#### <a name="details"></a><span data-ttu-id="dfaf0-102">Подробнее</span><span class="sxs-lookup"><span data-stu-id="dfaf0-102">Details</span></span>

<span data-ttu-id="dfaf0-103">В приложениях WPF при [выделении текста без графических элементов](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) для <xref:System.Windows.Controls.TextBox> и <xref:System.Windows.Controls.PasswordBox> разработчики теперь могут задать новое свойство SelectionTextBrush, чтобы изменить отрисовку выбранного текста.</span><span class="sxs-lookup"><span data-stu-id="dfaf0-103">In WPF applications using [non-adorner based text selection](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) for <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox>, developers may now set the newly added SelectionTextBrush property in order to alter the rendering of the selected text.</span></span>  <span data-ttu-id="dfaf0-104">По умолчанию этот цвет меняется с <xref:System.Windows.SystemColors.HighlightTextBrushKey>.</span><span class="sxs-lookup"><span data-stu-id="dfaf0-104">By default, this color changes with <xref:System.Windows.SystemColors.HighlightTextBrushKey>.</span></span>  <span data-ttu-id="dfaf0-105">Если выделение текста без использования графического элемента не включено, это свойство ничего не делает.</span><span class="sxs-lookup"><span data-stu-id="dfaf0-105">If non-adorner based text selection is not enabled, this property does nothing.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="dfaf0-106">Предложение</span><span class="sxs-lookup"><span data-stu-id="dfaf0-106">Suggestion</span></span>

<span data-ttu-id="dfaf0-107">Если выделение текста без графического элемента включено, вы можете использовать свойство <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> и <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> для изменения внешнего вида выбранного текста.</span><span class="sxs-lookup"><span data-stu-id="dfaf0-107">Once non-adorner based text selection is enabled, you can use the <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> and <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> property to change the appearance of the selected text.</span></span> <span data-ttu-id="dfaf0-108">Это можно сделать с помощью XAML:</span><span class="sxs-lookup"><span data-stu-id="dfaf0-108">This can be achieved using XAML:</span></span>

<pre><code class="lang-xaml">&lt;TextBox SelectionBrush=&quot;Red&quot; SelectionTextBrush=&quot;White&quot;  SelectionOpacity=&quot;0.5&quot;&#13;&#10;Foreground=&quot;Blue&quot; CaretBrush=&quot;Blue&quot;&gt;&#13;&#10;This is some text.&#13;&#10;&lt;/TextBox&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="dfaf0-109">name</span><span class="sxs-lookup"><span data-stu-id="dfaf0-109">Name</span></span>    | <span data-ttu-id="dfaf0-110">Значение</span><span class="sxs-lookup"><span data-stu-id="dfaf0-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="dfaf0-111">Область</span><span class="sxs-lookup"><span data-stu-id="dfaf0-111">Scope</span></span>   | <span data-ttu-id="dfaf0-112">Значительно</span><span class="sxs-lookup"><span data-stu-id="dfaf0-112">Major</span></span>       |
| <span data-ttu-id="dfaf0-113">Version</span><span class="sxs-lookup"><span data-stu-id="dfaf0-113">Version</span></span> | <span data-ttu-id="dfaf0-114">4.8</span><span class="sxs-lookup"><span data-stu-id="dfaf0-114">4.8</span></span>         |
| <span data-ttu-id="dfaf0-115">Type</span><span class="sxs-lookup"><span data-stu-id="dfaf0-115">Type</span></span>    | <span data-ttu-id="dfaf0-116">Изменение целевой платформы</span><span class="sxs-lookup"><span data-stu-id="dfaf0-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="dfaf0-117">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="dfaf0-117">Affected APIs</span></span>

- <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrushProperty?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush?displayProperty=nameWithType>
- [<span data-ttu-id="dfaf0-118">System.Windows.Controls.TextBox</span><span class="sxs-lookup"><span data-stu-id="dfaf0-118">System.Windows.Controls.TextBox</span></span>](xref:System.Windows.Controls.TextBox)
- [<span data-ttu-id="dfaf0-119">System.Windows.Controls.PasswordBox</span><span class="sxs-lookup"><span data-stu-id="dfaf0-119">System.Windows.Controls.PasswordBox</span></span>](xref:System.Windows.Controls.PasswordBox)
