---
title: Практическое руководство. Настройка шрифтов и цветов в элементе управления DataGridView в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- data grids [Windows Forms], customizing cells
- data grids [Windows Forms], font styles
- data grids [Windows Forms], color styles
ms.assetid: 588f2c57-d963-41b1-9c1d-d02d71818113
ms.openlocfilehash: 737a4b943125245a2916bbf6b24b8abdffa8e371
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215350"
---
# <a name="how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="9f5b9-102">Практическое руководство. Настройка шрифтов и цветов в элементе управления DataGridView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f5b9-102">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9f5b9-103">Внешний вид ячеек в элементе управления <xref:System.Windows.Forms.DataGridView> можно определять путем указания свойств класса <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="9f5b9-103">You can specify the visual appearance of cells within a <xref:System.Windows.Forms.DataGridView> control by setting properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> class.</span></span> <span data-ttu-id="9f5b9-104">Экземпляры этого класса можно извлечь из различных свойств класса <xref:System.Windows.Forms.DataGridView> и сопутствующих классов или же можно создать экземпляры объектов <xref:System.Windows.Forms.DataGridViewCellStyle> для назначения этим свойствам.</span><span class="sxs-lookup"><span data-stu-id="9f5b9-104">You can retrieve instances of this class from various properties of the <xref:System.Windows.Forms.DataGridView> class and its companion classes, or you can instantiate <xref:System.Windows.Forms.DataGridViewCellStyle> objects for assignment to these properties.</span></span>  
  
 <span data-ttu-id="9f5b9-105">Приведенные ниже процедуры демонстрируют основные способы настройки внешнего вида ячеек с помощью свойства <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>.</span><span class="sxs-lookup"><span data-stu-id="9f5b9-105">The following procedures demonstrate basic customization of cell appearance using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property.</span></span> <span data-ttu-id="9f5b9-106">Каждая ячейка элемента управления наследует стили, указанные с помощью этого свойства, если они не переопределены на уровне столбца, строки или ячейки.</span><span class="sxs-lookup"><span data-stu-id="9f5b9-106">Every cell in the control inherits the styles specified through this property unless they are overridden at the column, row, or cell level.</span></span> <span data-ttu-id="9f5b9-107">Пример наследования стиля, см. в разделе [как: Установка стилей ячейки по умолчанию для управления DataGridView в Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="9f5b9-107">For an example of style inheritance, see [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span> <span data-ttu-id="9f5b9-108">Информацию о дополнительных способах использования класса <xref:System.Windows.Forms.DataGridViewCellStyle> см. в разделах, перечисленных в разделе "См. также".</span><span class="sxs-lookup"><span data-stu-id="9f5b9-108">For information about additional uses of the <xref:System.Windows.Forms.DataGridViewCellStyle> class, see the topics listed in the See Also section.</span></span>  
  
 <span data-ttu-id="9f5b9-109">В Visual Studio предусмотрена расширенная поддержка данной задачи.</span><span class="sxs-lookup"><span data-stu-id="9f5b9-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="9f5b9-110">Также см. раздел [Как Установка стилей ячейки по умолчанию и форматов данных, для Windows Forms с помощью конструктора элемента управления DataGridView](default-cell-styles-datagridview.md).</span><span class="sxs-lookup"><span data-stu-id="9f5b9-110">Also see [How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer](default-cell-styles-datagridview.md).</span></span>  
  
### <a name="to-specify-the-font-used-by-datagridview-cells"></a><span data-ttu-id="9f5b9-111">Указание шрифта текста для ячеек элемента управления DataGridView</span><span class="sxs-lookup"><span data-stu-id="9f5b9-111">To specify the font used by DataGridView cells</span></span>  
  
-   <span data-ttu-id="9f5b9-112">Задайте свойство <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> элемента <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="9f5b9-112">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="9f5b9-113">В примере кода ниже свойство <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> используется для задания шрифта для всего элемента управления.</span><span class="sxs-lookup"><span data-stu-id="9f5b9-113">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the font for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#101](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#101)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#101](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#101)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-datagridview-cells"></a><span data-ttu-id="9f5b9-114">Указание цветов текста и фона для ячеек элемента управления DataGridView</span><span class="sxs-lookup"><span data-stu-id="9f5b9-114">To specify the foreground and background colors of DataGridView cells</span></span>  
  
-   <span data-ttu-id="9f5b9-115">Задайте свойства <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> и <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> элемента <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="9f5b9-115">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> and <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> properties of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="9f5b9-116">В примере кода ниже свойство <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> используется с целью задания стилей для всего элемента управления.</span><span class="sxs-lookup"><span data-stu-id="9f5b9-116">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set these styles for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#102](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#102)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#102](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#102)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-selected-datagridview-cells"></a><span data-ttu-id="9f5b9-117">Указание цветов текста и фона для выбранных ячеек элемента управления DataGridView</span><span class="sxs-lookup"><span data-stu-id="9f5b9-117">To specify the foreground and background colors of selected DataGridView cells</span></span>  
  
-   <span data-ttu-id="9f5b9-118">Задайте свойства <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A> и <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> элемента <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="9f5b9-118">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A> and <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> properties of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="9f5b9-119">В примере кода ниже свойство <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> используется с целью задания стилей для всего элемента управления.</span><span class="sxs-lookup"><span data-stu-id="9f5b9-119">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set these styles for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#103](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#103)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#103](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#103)]  
  
## <a name="example"></a><span data-ttu-id="9f5b9-120">Пример</span><span class="sxs-lookup"><span data-stu-id="9f5b9-120">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9f5b9-121">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="9f5b9-121">Compiling the Code</span></span>  
 <span data-ttu-id="9f5b9-122">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="9f5b9-122">This example requires:</span></span>  
  
-   <span data-ttu-id="9f5b9-123">элемент управления <xref:System.Windows.Forms.DataGridView> с именем `dataGridView1`;</span><span class="sxs-lookup"><span data-stu-id="9f5b9-123">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="9f5b9-124">ссылки на сборки <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType> и <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9f5b9-124">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9f5b9-125">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="9f5b9-125">Robust Programming</span></span>  
 <span data-ttu-id="9f5b9-126">Для максимальной масштабируемости объекты <xref:System.Windows.Forms.DataGridViewCellStyle> следует распределить по нескольким строкам, столбцам или ячейкам с одинаковыми стилями, чтобы не задавать свойства стилей для каждого элемента в отдельности.</span><span class="sxs-lookup"><span data-stu-id="9f5b9-126">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="9f5b9-127">Дополнительные сведения см. в разделе [масштабирование элемента управления DataGridView в Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="9f5b9-127">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f5b9-128">См. также</span><span class="sxs-lookup"><span data-stu-id="9f5b9-128">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="9f5b9-129">Базовое форматирование и оформление элемента управления DataGridView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f5b9-129">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="9f5b9-130">Стили ячеек элемента управления DataGridView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f5b9-130">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
