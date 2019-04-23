---
title: Практическое руководство. Индикация места вставки в элементе управления ListView в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ListView control [Windows Forms], drag operations
- graphics [Windows Forms], insertion marks
- drop and drag [Windows Forms], insertion marks
- insertion marks
ms.assetid: 88d0a15b-25fd-4dc3-a685-297351311940
ms.openlocfilehash: 60b775408f5c43ff08fc5c7de72a8302b20b2264
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145617"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a><span data-ttu-id="7f22c-102">Практическое руководство. Индикация места вставки в элементе управления ListView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7f22c-102">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>
<span data-ttu-id="7f22c-103">Метка вставки в элементе управления <xref:System.Windows.Forms.ListView> показывает пользователю, куда будут помещены перетаскиваемые элементы.</span><span class="sxs-lookup"><span data-stu-id="7f22c-103">The insertion mark in the <xref:System.Windows.Forms.ListView> control shows users the point where dragged items will be inserted.</span></span> <span data-ttu-id="7f22c-104">Когда пользователь перетаскивает элемент на точку между двумя другими элементами, метка вставки показывает ожидаемое новое расположение элемента.</span><span class="sxs-lookup"><span data-stu-id="7f22c-104">When a user drags an item to a point between two other items, the insertion mark shows the item's expected new location.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f22c-105">Возможность метки вставки доступна только в [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)], когда приложение вызывает метод <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7f22c-105">The insertion mark feature is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7f22c-106">В предыдущих версиях операционных систем код, связанный с меткой вставки, не действует и метка вставки не отображается.</span><span class="sxs-lookup"><span data-stu-id="7f22c-106">On earlier operating systems, any code relating to the insertion mark has no effect and the insertion mark will not appear.</span></span> <span data-ttu-id="7f22c-107">Дополнительные сведения см. в разделе <xref:System.Windows.Forms.ListViewInsertionMark>.</span><span class="sxs-lookup"><span data-stu-id="7f22c-107">For more information, see <xref:System.Windows.Forms.ListViewInsertionMark>.</span></span>  
  
 <span data-ttu-id="7f22c-108">На рисунке ниже показана метка вставки.</span><span class="sxs-lookup"><span data-stu-id="7f22c-108">The following image shows an insertion mark:</span></span>  
  
 <span data-ttu-id="7f22c-109">![Снимок экрана, показывающий знак вставки ListView. ](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span><span class="sxs-lookup"><span data-stu-id="7f22c-109">![Screenshot that shows a ListView insertion mark.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span></span>  
  
 <span data-ttu-id="7f22c-110">В примере кода ниже показано, как использовать эту возможность.</span><span class="sxs-lookup"><span data-stu-id="7f22c-110">The following code example demonstrates how to use this feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f22c-111">Пример</span><span class="sxs-lookup"><span data-stu-id="7f22c-111">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7f22c-112">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="7f22c-112">Compiling the Code</span></span>  
 <span data-ttu-id="7f22c-113">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="7f22c-113">This example requires:</span></span>  
  
-   <span data-ttu-id="7f22c-114">ссылки на сборки System и System.Windows.Forms;</span><span class="sxs-lookup"><span data-stu-id="7f22c-114">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="7f22c-115">Сведения о выполнении сборки этого примера из командной строки для Visual Basic или Visual C#, см. в разделе [построение из командной строки](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) или [командной строки создания с помощью csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="7f22c-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="7f22c-116">Можно также сборке этого примера в Visual Studio путем вставки кода в новый проект.</span><span class="sxs-lookup"><span data-stu-id="7f22c-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f22c-117">См. также</span><span class="sxs-lookup"><span data-stu-id="7f22c-117">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [<span data-ttu-id="7f22c-118">Элемент управления ListView</span><span class="sxs-lookup"><span data-stu-id="7f22c-118">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="7f22c-119">Общие сведения об элементе управления ListView</span><span class="sxs-lookup"><span data-stu-id="7f22c-119">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="7f22c-120">Пошаговое руководство: Выполнение операции перетаскивания и вставки в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7f22c-120">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
