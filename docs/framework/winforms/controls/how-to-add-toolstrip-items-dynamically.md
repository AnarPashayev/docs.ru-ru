---
title: Практическое руководство. Динамическое добавление элементов ToolStrip
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrip control [Windows Forms]
- toolbars [Windows Forms], adding items dynamically
- ToolStrip control [Windows Forms]
ms.assetid: 0e8dea56-5f46-408b-914d-7e360341a234
ms.openlocfilehash: 9426c7cb3251dbbd95727b78c57be7a0b71556e2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624017"
---
# <a name="how-to-add-toolstrip-items-dynamically"></a><span data-ttu-id="9cc6f-102">Практическое руководство. Динамическое добавление элементов ToolStrip</span><span class="sxs-lookup"><span data-stu-id="9cc6f-102">How to: Add ToolStrip Items Dynamically</span></span>
<span data-ttu-id="9cc6f-103">Коллекцию пунктов меню элемента управления <xref:System.Windows.Forms.ToolStrip> можно динамически заполнять при открытии меню.</span><span class="sxs-lookup"><span data-stu-id="9cc6f-103">You can dynamically populate the menu item collection of a <xref:System.Windows.Forms.ToolStrip> control when the menu opens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cc6f-104">Пример</span><span class="sxs-lookup"><span data-stu-id="9cc6f-104">Example</span></span>  
 <span data-ttu-id="9cc6f-105">В примере кода ниже демонстрируется динамическое добавление элементов в элемент управления <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="9cc6f-105">The following code example demonstrates how to dynamically add items to a <xref:System.Windows.Forms.ContextMenuStrip> control.</span></span> <span data-ttu-id="9cc6f-106">В примере также показано повторное использование <xref:System.Windows.Forms.ContextMenuStrip> для трех различных элементов управления в форме.</span><span class="sxs-lookup"><span data-stu-id="9cc6f-106">The example also shows how to reuse the same <xref:System.Windows.Forms.ContextMenuStrip> for three different controls on the form.</span></span>  
  
 <span data-ttu-id="9cc6f-107">В примере обработчик событий <xref:System.Windows.Forms.ToolStripDropDown.Opening> заполняет коллекцию пунктов меню.</span><span class="sxs-lookup"><span data-stu-id="9cc6f-107">In the example, an <xref:System.Windows.Forms.ToolStripDropDown.Opening> event handler populates the menu item collection.</span></span> <span data-ttu-id="9cc6f-108">Обработчик событий <xref:System.Windows.Forms.ToolStripDropDown.Opening> анализирует свойства <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> и <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> и добавляет элемент <xref:System.Windows.Forms.ToolStripItem>, описывающий исходный элемент управления.</span><span class="sxs-lookup"><span data-stu-id="9cc6f-108">The <xref:System.Windows.Forms.ToolStripDropDown.Opening> event handler examines the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> properties and adds a <xref:System.Windows.Forms.ToolStripItem> describing the source control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#40)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#40)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9cc6f-109">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="9cc6f-109">Compiling the Code</span></span>  
 <span data-ttu-id="9cc6f-110">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="9cc6f-110">This example requires:</span></span>  
  
- <span data-ttu-id="9cc6f-111">ссылки на сборки System.Drawing и System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="9cc6f-111">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="9cc6f-112">Сведения о выполнении сборки этого примера из командной строки для Visual Basic или Visual C#, см. в разделе [построение из командной строки](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) или [командной строки создания с помощью csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="9cc6f-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="9cc6f-113">Можно также сборке этого примера в Visual Studio путем вставки кода в новый проект.</span><span class="sxs-lookup"><span data-stu-id="9cc6f-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cc6f-114">См. также</span><span class="sxs-lookup"><span data-stu-id="9cc6f-114">See also</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- [<span data-ttu-id="9cc6f-115">Элемент управления ToolStrip</span><span class="sxs-lookup"><span data-stu-id="9cc6f-115">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
