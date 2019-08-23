---
title: Практическое руководство. Замораживание столбцов элемента управления DataGridView в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], freezing columns
- DataGridView control [Windows Forms], columns always in view
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
ms.openlocfilehash: a83c5078d67be40fda2ae3382b8124594ee78103
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966661"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="54c3f-102">Практическое руководство. Замораживание столбцов элемента управления DataGridView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="54c3f-102">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="54c3f-103">При просмотре пользователями данных, отображаемых в элементе управления Windows Forms <xref:System.Windows.Forms.DataGridView>, им порой требуется часто обращаться к одному столбцу или набору столбцов.</span><span class="sxs-lookup"><span data-stu-id="54c3f-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="54c3f-104">Например, при просмотре таблицы сведений о пользователе, содержащей много столбцов, может быть желательно, чтобы имя пользователя отображалось постоянно при прокручивании остальных столбцов за пределы видимости.</span><span class="sxs-lookup"><span data-stu-id="54c3f-104">For example, when displaying a table of customer information that contains many columns, it is useful to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>  
  
 <span data-ttu-id="54c3f-105">Для этого необходимо закрепить столбцы в элементе управления.</span><span class="sxs-lookup"><span data-stu-id="54c3f-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="54c3f-106">При закреплении столбца все столбцы слева от него (или справа для языков с направлением письма справа налево) также закрепляются.</span><span class="sxs-lookup"><span data-stu-id="54c3f-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="54c3f-107">Закрепленные столбцы остаются на месте в то время, как остальные столбцы можно прокручивать.</span><span class="sxs-lookup"><span data-stu-id="54c3f-107">Frozen columns remain in place while all other columns can scroll.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="54c3f-108">Если разрешено переупорядочивание столбцов, закрепленные столбцы рассматриваются как группа, отличная от группы незакрепленных столбцов.</span><span class="sxs-lookup"><span data-stu-id="54c3f-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="54c3f-109">Пользователи могут переставлять местами столбцы в каждой из групп, но не могут перемещать столбцы из одной группы в другую.</span><span class="sxs-lookup"><span data-stu-id="54c3f-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>  
  
 <span data-ttu-id="54c3f-110">Свойство <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> столбца определяет, должен ли он отображаться в сетке постоянно.</span><span class="sxs-lookup"><span data-stu-id="54c3f-110">The <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property of a column determines whether the column is always visible within the grid.</span></span>  
  
 <span data-ttu-id="54c3f-111">Эта задача поддерживается в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="54c3f-111">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="54c3f-112">Также см. раздел [Как Закрепление столбцов в элементе управления Windows Forms DataGridView с помощью](freeze-columns-in-the-datagrid-using-the-designer.md)конструктора.</span><span class="sxs-lookup"><span data-stu-id="54c3f-112">Also see [How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer](freeze-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-freeze-a-column-programmatically"></a><span data-ttu-id="54c3f-113">Программное закрепление столбца</span><span class="sxs-lookup"><span data-stu-id="54c3f-113">To freeze a column programmatically</span></span>  
  
- <span data-ttu-id="54c3f-114">Задайте для свойства <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> значение `true`.</span><span class="sxs-lookup"><span data-stu-id="54c3f-114">Set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="54c3f-115">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="54c3f-115">Compiling the Code</span></span>  
 <span data-ttu-id="54c3f-116">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="54c3f-116">This example requires:</span></span>  
  
- <span data-ttu-id="54c3f-117">элемент управления <xref:System.Windows.Forms.DataGridView> с именем `dataGridView1`, содержащий столбец с именем `AddToCartButton`;</span><span class="sxs-lookup"><span data-stu-id="54c3f-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `AddToCartButton`.</span></span>  
  
- <span data-ttu-id="54c3f-118">ссылки на сборки <xref:System?displayProperty=nameWithType> и <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="54c3f-118">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54c3f-119">См. также</span><span class="sxs-lookup"><span data-stu-id="54c3f-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="54c3f-120">Базовые характеристики столбцов, строк и ячеек элемента управления DataGridView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="54c3f-120">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="54c3f-121">Практическое руководство. Включение изменения порядка столбцов в элементе управления Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="54c3f-121">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
