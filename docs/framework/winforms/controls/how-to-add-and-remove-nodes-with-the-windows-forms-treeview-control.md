---
title: Практическое руководство. Добавление и удаление узлов элемента управления TreeView в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: de1b82db-4905-449a-9f59-af271a6b6673
ms.openlocfilehash: 4cbb5fbdb24790a7ddbce5c38060703c7ba7024a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326896"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a><span data-ttu-id="8e31c-102">Практическое руководство. Добавление и удаление узлов элемента управления TreeView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8e31c-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>
<span data-ttu-id="8e31c-103">Windows Forms <xref:System.Windows.Forms.TreeView> элемент управления сохраняет узлы верхнего уровня в его <xref:System.Windows.Forms.TreeView.Nodes%2A> коллекции.</span><span class="sxs-lookup"><span data-stu-id="8e31c-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control stores the top-level nodes in its <xref:System.Windows.Forms.TreeView.Nodes%2A> collection.</span></span> <span data-ttu-id="8e31c-104">Каждый <xref:System.Windows.Forms.TreeNode> также имеет свой собственный <xref:System.Windows.Forms.TreeNode.Nodes%2A> коллекцию для хранения дочерних узлов.</span><span class="sxs-lookup"><span data-stu-id="8e31c-104">Each <xref:System.Windows.Forms.TreeNode> also has its own <xref:System.Windows.Forms.TreeNode.Nodes%2A> collection to store its child nodes.</span></span> <span data-ttu-id="8e31c-105">Оба свойства коллекции имеют тип <xref:System.Windows.Forms.TreeNodeCollection>, который предоставляет стандартные элементы коллекции, которые позволяют добавлять, удалять и изменения порядка узлов на одном уровне иерархии узла.</span><span class="sxs-lookup"><span data-stu-id="8e31c-105">Both collection properties are of type <xref:System.Windows.Forms.TreeNodeCollection>, which provides standard collection members that enable you to add, remove, and rearrange the nodes at a single level of the node hierarchy.</span></span>  
  
### <a name="to-add-nodes-programmatically"></a><span data-ttu-id="8e31c-106">Чтобы добавить узлы программным способом</span><span class="sxs-lookup"><span data-stu-id="8e31c-106">To add nodes programmatically</span></span>  
  
1. <span data-ttu-id="8e31c-107">Используйте <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> метод представления дерева <xref:System.Windows.Forms.TreeView.Nodes%2A> свойство.</span><span class="sxs-lookup"><span data-stu-id="8e31c-107">Use the <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>  
  
    ```vb  
    ' Adds new node as a child node of the currently selected node.  
    Dim newNode As TreeNode = New TreeNode("Text for new node")  
    TreeView1.SelectedNode.Nodes.Add(newNode)  
    ```  
  
    ```csharp  
    // Adds new node as a child node of the currently selected node.  
    TreeNode newNode = new TreeNode("Text for new node");  
    treeView1.SelectedNode.Nodes.Add(newNode);  
    ```  
  
    ```cpp  
    // Adds new node as a child node of the currently selected node.  
    TreeNode ^ newNode = new TreeNode("Text for new node");  
    treeView1->SelectedNode->Nodes->Add(newNode);  
    ```  
  
### <a name="to-remove-nodes-programmatically"></a><span data-ttu-id="8e31c-108">Для удаления узлов программным способом</span><span class="sxs-lookup"><span data-stu-id="8e31c-108">To remove nodes programmatically</span></span>  
  
1. <span data-ttu-id="8e31c-109">Используйте <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> метод представления дерева <xref:System.Windows.Forms.TreeView.Nodes%2A> свойство, чтобы удалить только один узел, или <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> метод, чтобы удалить все узлы.</span><span class="sxs-lookup"><span data-stu-id="8e31c-109">Use the <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property to remove a single node, or the <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> method to clear all nodes.</span></span>  
  
    ```vb  
    ' Removes currently selected node, or root if nothing is selected.  
    TreeView1.Nodes.Remove(TreeView1.SelectedNode)  
    ' Clears all nodes.  
    TreeView1.Nodes.Clear()  
    ```  
  
    ```csharp  
    // Removes currently selected node, or root if nothing   
    // is selected.  
    treeView1.Nodes.Remove(treeView1.SelectedNode);  
    // Clears all nodes.  
    TreeView1.Nodes.Clear();  
    ```  
  
    ```cpp  
    // Removes currently selected node, or root if nothing  
    // is selected.  
    treeView1->Nodes->Remove(treeView1->SelectedNode);  
    // Clears all nodes.  
    treeView1->Nodes->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8e31c-110">См. также</span><span class="sxs-lookup"><span data-stu-id="8e31c-110">See also</span></span>

- [<span data-ttu-id="8e31c-111">Элемент управления TreeView</span><span class="sxs-lookup"><span data-stu-id="8e31c-111">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="8e31c-112">Общие сведения об элементе управления TreeView</span><span class="sxs-lookup"><span data-stu-id="8e31c-112">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="8e31c-113">Практическое руководство. Определение значков для элемента управления TreeView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8e31c-113">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="8e31c-114">Практическое руководство. Перебор узлов элемента управления TreeView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8e31c-114">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="8e31c-115">Практическое руководство. Определить, какой узел элемента управления TreeView была нажата</span><span class="sxs-lookup"><span data-stu-id="8e31c-115">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="8e31c-116">Практическое руководство. Добавление пользовательских данных в элемент управления TreeView или элемент управления ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="8e31c-116">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
