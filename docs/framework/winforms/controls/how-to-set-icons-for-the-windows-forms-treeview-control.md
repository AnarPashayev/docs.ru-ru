---
title: Практическое руководство. Определение значков для элемента управления TreeView в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], node icons
- ImageList component [Windows Forms], adding images
- icons [Windows Forms], setting for TreeView control
- tree nodes in TreeView control [Windows Forms], icons
ms.assetid: c14ddcc0-e5a6-4c21-a2d5-6799fd491781
ms.openlocfilehash: 451f9ab2b35ad1fbbe9401dacbc8aab44e302701
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909808"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a><span data-ttu-id="6e25a-102">Практическое руководство. Определение значков для элемента управления TreeView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6e25a-102">How to: Set Icons for the Windows Forms TreeView Control</span></span>
<span data-ttu-id="6e25a-103">Элемент управления <xref:System.Windows.Forms.TreeView> Windows Forms может отображать значки рядом с каждым узлом.</span><span class="sxs-lookup"><span data-stu-id="6e25a-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control can display icons next to each node.</span></span> <span data-ttu-id="6e25a-104">Значки располагаются непосредственно слева от текста узла.</span><span class="sxs-lookup"><span data-stu-id="6e25a-104">The icons are positioned to the immediate left of the node text.</span></span> <span data-ttu-id="6e25a-105">Для отображения этих значков необходимо связать древовидное представление с <xref:System.Windows.Forms.ImageList> элементом управления.</span><span class="sxs-lookup"><span data-stu-id="6e25a-105">To display these icons, you must associate the tree view with an <xref:System.Windows.Forms.ImageList> control.</span></span> <span data-ttu-id="6e25a-106">Дополнительные сведения о списках изображений см. в разделе [ImageList Component](imagelist-component-windows-forms.md) и [инструкции: Добавление или удаление изображений с помощью компонента](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)Windows Forms ImageList.</span><span class="sxs-lookup"><span data-stu-id="6e25a-106">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e25a-107">Ошибка в Microsoft .NET Framework версии 1,1 предотвращает отображение изображений на <xref:System.Windows.Forms.TreeView> узлах при вызове <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>приложения.</span><span class="sxs-lookup"><span data-stu-id="6e25a-107">A bug in Microsoft .NET Framework version 1.1 prevents images from appearing on <xref:System.Windows.Forms.TreeView> nodes when your application calls <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6e25a-108">Чтобы обойти эту ошибку, вызовите <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> `Main` метод непосредственно после вызова <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>метода.</span><span class="sxs-lookup"><span data-stu-id="6e25a-108">To work around this bug, call <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> in your `Main` method immediately after calling <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span></span> <span data-ttu-id="6e25a-109">Эта ошибка исправлена в .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="6e25a-109">This bug is fixed in .NET Framework 2.0.</span></span>  
  
### <a name="to-display-images-in-a-tree-view"></a><span data-ttu-id="6e25a-110">Отображение изображений в представлении в виде дерева</span><span class="sxs-lookup"><span data-stu-id="6e25a-110">To display images in a tree view</span></span>  
  
1. <span data-ttu-id="6e25a-111">Задайте для <xref:System.Windows.Forms.TreeView.ImageList%2A> свойства <xref:System.Windows.Forms.ImageList> элемента управления существующий элемент управления, который вы хотите использовать. <xref:System.Windows.Forms.TreeView></span><span class="sxs-lookup"><span data-stu-id="6e25a-111">Set the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.ImageList%2A> property to the existing <xref:System.Windows.Forms.ImageList> control you wish to use.</span></span>  
  
     <span data-ttu-id="6e25a-112">Эти свойства можно задать в конструкторе с помощью окно свойств или в коде.</span><span class="sxs-lookup"><span data-stu-id="6e25a-112">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2. <span data-ttu-id="6e25a-113">Задайте свойства узла <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> и <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> .</span><span class="sxs-lookup"><span data-stu-id="6e25a-113">Set the node's <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> and <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> properties.</span></span> <span data-ttu-id="6e25a-114">Свойство определяет изображение, отображаемое для обычных и развернутых состояний узла, <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> а свойство определяет изображение, отображаемое для выбранного состояния узла. <xref:System.Windows.Forms.TreeNode.ImageIndex%2A></span><span class="sxs-lookup"><span data-stu-id="6e25a-114">The <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> property determines the image displayed for the node's normal and expanded states, and the <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> property determines the image displayed for the node's selected state.</span></span>  
  
     <span data-ttu-id="6e25a-115">Эти свойства можно задать в коде или в редакторе TreeNode.</span><span class="sxs-lookup"><span data-stu-id="6e25a-115">These properties can be set in code, or within the TreeNode Editor.</span></span> <span data-ttu-id="6e25a-116">Чтобы открыть редактор TreeNode, нажмите кнопку с многоточием ( ![кнопку с многоточием (...) в окно свойств Visual Studio.](./media/visual-studio-ellipsis-button.png)) рядом со <xref:System.Windows.Forms.TreeView.Nodes%2A> свойством в окно свойств.</span><span class="sxs-lookup"><span data-stu-id="6e25a-116">To open the TreeNode Editor, click the ellipsis button ( ![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property on the Properties window.</span></span>  
  
    ```vb  
    ' (Assumes that ImageList1 contains at least two images and  
    ' the TreeView control contains a selected image.)  
    TreeView1.SelectedNode.ImageIndex = 0  
    TreeView1.SelectedNode.SelectedImageIndex = 1  
    ```  
  
    ```csharp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1.SelectedNode.ImageIndex = 0;  
    treeView1.SelectedNode.SelectedImageIndex = 1;  
    ```  
  
    ```cpp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1->SelectedNode->ImageIndex = 0;  
    treeView1->SelectedNode->SelectedImageIndex = 1;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6e25a-117">См. также</span><span class="sxs-lookup"><span data-stu-id="6e25a-117">See also</span></span>

- [<span data-ttu-id="6e25a-118">Общие сведения об элементе управления TreeView</span><span class="sxs-lookup"><span data-stu-id="6e25a-118">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="6e25a-119">Практическое руководство. Добавление и удаление узлов с помощью элемента управления Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="6e25a-119">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="6e25a-120">Практическое руководство. Перебор всех узлов элемента управления Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="6e25a-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="6e25a-121">Практическое руководство. Определение того, какой узел TreeView был выбран</span><span class="sxs-lookup"><span data-stu-id="6e25a-121">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="6e25a-122">Практическое руководство. Добавление пользовательских сведений в элемент управления TreeView или ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="6e25a-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
