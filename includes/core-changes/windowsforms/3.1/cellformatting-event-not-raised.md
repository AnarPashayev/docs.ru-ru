---
ms.openlocfilehash: 4a34a64eba72ea24c1d830566565ce4fbee8e5b7
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721525"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a><span data-ttu-id="83307-101">Событие CellFormatting не возникает при отображении подсказки</span><span class="sxs-lookup"><span data-stu-id="83307-101">CellFormatting event not raised if tooltip is shown</span></span>

<span data-ttu-id="83307-102"><xref:System.Windows.Forms.DataGridView> теперь отображает всплывающие подсказки для ошибок и текста в ячейке при наведении указателя мыши и при выборе с помощью клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="83307-102">A <xref:System.Windows.Forms.DataGridView> now shows a cell's text and error tooltips when hovered by a mouse and when selected via the keyboard.</span></span> <span data-ttu-id="83307-103">Если подсказка отображается, событие <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> не возникает.</span><span class="sxs-lookup"><span data-stu-id="83307-103">If a tooltip is shown, the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event is not raised.</span></span>

#### <a name="change-description"></a><span data-ttu-id="83307-104">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="83307-104">Change description</span></span>

<span data-ttu-id="83307-105">До .NET Core 3.1 <xref:System.Windows.Forms.DataGridView>, у которого для свойства <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> было задано значение `true`, отображал подсказку для ошибок и текста в ячейке при наведении указателя мыши на эту ячейку.</span><span class="sxs-lookup"><span data-stu-id="83307-105">Prior to .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that had the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` showed a tooltip for a cell's text and errors when the cell was hovered by a mouse.</span></span> <span data-ttu-id="83307-106">Подсказки не отображались при выборе ячейки с помощью клавиатуры (например, с помощью клавиши TAB, сочетаний клавиш или клавиш со стрелками).</span><span class="sxs-lookup"><span data-stu-id="83307-106">Tooltips were not shown when a cell was selected via the keyboard (for example, by using the Tab key, shortcut keys, or arrow navigation).</span></span> <span data-ttu-id="83307-107">Если пользователь изменил ячейку, а затем, пока <xref:System.Windows.Forms.DataGridView> находился в режиме редактирования, навел указатель на ячейку, для которой не задано свойство <xref:System.Windows.Forms.DataGridViewCell.ToolTipText>, возникало событие <xref:System.Windows.Forms.DataGridView.CellFormatting> для форматирования текста ячейки, отображаемого в ней.</span><span class="sxs-lookup"><span data-stu-id="83307-107">If the user edited a cell, and then, while the <xref:System.Windows.Forms.DataGridView> was still in edit mode, hovered over a cell that did not have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set, a <xref:System.Windows.Forms.DataGridView.CellFormatting> event was raised to format the cell's text for display in the cell.</span></span>

<span data-ttu-id="83307-108">Чтобы удовлетворить требованиям стандартов специальных возможностей, начиная с .NET Core 3.1, <xref:System.Windows.Forms.DataGridView>, у которого для свойства <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> задано значение `true`, отображает подсказки для ошибок и текста ячейки не только при наведении указателя мыши, но и при выборе ячейки с помощью клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="83307-108">To meet accessibility standards, starting in .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that has the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` shows tooltips for a cell's text and errors not only when the cell is hovered, but also when it's selected via the keyboard.</span></span> <span data-ttu-id="83307-109">Как следствие этого изменения событие <xref:System.Windows.Forms.DataGridView.CellFormatting>*не* возникает, когда указатель наводится на ячейки, для которых не задано свойство <xref:System.Windows.Forms.DataGridViewCell.ToolTipText>, пока <xref:System.Windows.Forms.DataGridView> находится в режиме редактирования.</span><span class="sxs-lookup"><span data-stu-id="83307-109">As a consequence of this change, the <xref:System.Windows.Forms.DataGridView.CellFormatting> event is *not* raised when cells that don't have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set are hovered while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span> <span data-ttu-id="83307-110">Событие не возникает, так как содержимое ячейки, на которую наведен указатель, выводится в виде подсказки, а не отображается в ячейке.</span><span class="sxs-lookup"><span data-stu-id="83307-110">The event is not raised because the content of the hovered cell is shown as a tooltip instead of being displayed in the cell.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="83307-111">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="83307-111">Version introduced</span></span>

<span data-ttu-id="83307-112">3.1</span><span class="sxs-lookup"><span data-stu-id="83307-112">3.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="83307-113">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="83307-113">Recommended action</span></span>

<span data-ttu-id="83307-114">Выполните рефакторинг всего кода, зависящего от события <xref:System.Windows.Forms.DataGridView.CellFormatting>, когда <xref:System.Windows.Forms.DataGridView> находится в режиме редактирования.</span><span class="sxs-lookup"><span data-stu-id="83307-114">Refactor any code that depends on the <xref:System.Windows.Forms.DataGridView.CellFormatting> event while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span>

#### <a name="category"></a><span data-ttu-id="83307-115">Категория</span><span class="sxs-lookup"><span data-stu-id="83307-115">Category</span></span>

<span data-ttu-id="83307-116">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="83307-116">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="83307-117">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="83307-117">Affected APIs</span></span>

<span data-ttu-id="83307-118">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="83307-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->
