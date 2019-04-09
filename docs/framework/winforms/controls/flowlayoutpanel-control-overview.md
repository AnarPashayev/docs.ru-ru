---
title: Общие сведения об элементе управления FlowLayoutPanel
ms.date: 03/30/2017
f1_keywords:
- FlowLayoutPanel
helpviewer_keywords:
- forms [Windows Forms], dynamic layout
- layout [Windows Forms], dynamic
- Windows Forms, dynamic layout
- FlowLayoutPanel control [Windows Forms], about FlowLayoutPanel control
ms.assetid: 3883e024-f5a0-456d-9c27-b4dfa1cc9045
ms.openlocfilehash: 260146cd901fe2b80a73c01060ccd55958cd169e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203045"
---
# <a name="flowlayoutpanel-control-overview"></a><span data-ttu-id="039e8-102">Общие сведения об элементе управления FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="039e8-102">FlowLayoutPanel Control Overview</span></span>
<span data-ttu-id="039e8-103">Элемент управления <xref:System.Windows.Forms.FlowLayoutPanel> упорядочивает свое содержимое в горизонтальном или вертикальном направлении.</span><span class="sxs-lookup"><span data-stu-id="039e8-103">The <xref:System.Windows.Forms.FlowLayoutPanel> control arranges its contents in a horizontal or vertical flow direction.</span></span> <span data-ttu-id="039e8-104">Его содержимое может переноситься из одной строки или столбца в следующую строку или столбец.</span><span class="sxs-lookup"><span data-stu-id="039e8-104">You can wrap the control's contents from one row to the next, or from one column to the next.</span></span> <span data-ttu-id="039e8-105">Кроме того, вместо переноса содержимое может обрезаться.</span><span class="sxs-lookup"><span data-stu-id="039e8-105">Alternately, you can clip instead of wrap its contents.</span></span>  
  
 <span data-ttu-id="039e8-106">Чтобы определить направление содержимого, задайте свойство <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="039e8-106">You can specify the flow direction by setting the value of the <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> property.</span></span> <span data-ttu-id="039e8-107">Содержимое элемента управления <xref:System.Windows.Forms.FlowLayoutPanel> размещается правильно при использовании направления справа налево.</span><span class="sxs-lookup"><span data-stu-id="039e8-107">The <xref:System.Windows.Forms.FlowLayoutPanel> control correctly reverses its flow direction in Right-to-Left (RTL) layouts.</span></span> <span data-ttu-id="039e8-108">С помощью свойства <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> можно указать, должно ли содержимое элемента управления <xref:System.Windows.Forms.FlowLayoutPanel> переноситься или обрезаться.</span><span class="sxs-lookup"><span data-stu-id="039e8-108">You can also specify whether the <xref:System.Windows.Forms.FlowLayoutPanel> control's contents are wrapped or clipped by setting the value of the <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> property.</span></span>  
  
 <span data-ttu-id="039e8-109">Если свойству <xref:System.Windows.Forms.Control.AutoSize%2A> присвоено значение `true`, размер элемента управления <xref:System.Windows.Forms.FlowLayoutPanel> автоматически изменяется в соответствии с содержимым.</span><span class="sxs-lookup"><span data-stu-id="039e8-109">The <xref:System.Windows.Forms.FlowLayoutPanel> control automatically sizes to its contents when you set the <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span> <span data-ttu-id="039e8-110">Он также предоставляет **FlowBreak** свойство к его дочерним элементам управления.</span><span class="sxs-lookup"><span data-stu-id="039e8-110">It also provides a **FlowBreak** property to its child controls.</span></span> <span data-ttu-id="039e8-111">Если свойству FlowBreak присвоено значение `true`, элементы управления внутри элемента <xref:System.Windows.Forms.FlowLayoutPanel> перестают размещаться в текущем направлении и переносятся на следующую строку или в следующий столбец.</span><span class="sxs-lookup"><span data-stu-id="039e8-111">Setting the value of the FlowBreak property to `true` causes the <xref:System.Windows.Forms.FlowLayoutPanel> control to stop laying out controls in the current flow direction and wrap to the next row or column.</span></span>  
  
 <span data-ttu-id="039e8-112">Любой элемент управления Windows Forms, включая другие экземпляры <xref:System.Windows.Forms.FlowLayoutPanel>, может быть дочерним относительно элемента <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="039e8-112">Any Windows Forms control can be a child of the <xref:System.Windows.Forms.FlowLayoutPanel> control, including other instances of <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="039e8-113">Это позволяет создавать сложные макеты, которые изменяются в соответствии с размерами формы во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="039e8-113">With this capability, you can construct sophisticated layouts that adapt to your form's dimensions at run time.</span></span>  
  
 <span data-ttu-id="039e8-114">Также см. в разделе [Пошаговое руководство: Упорядочение элементов управления в Windows Forms, с помощью элемента FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="039e8-114">Also see [Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="039e8-115">См. также</span><span class="sxs-lookup"><span data-stu-id="039e8-115">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="039e8-116">Элемент управления FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="039e8-116">FlowLayoutPanel Control</span></span>](flowlayoutpanel-control-windows-forms.md)
