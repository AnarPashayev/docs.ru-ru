---
title: Практическое руководство. Создание формы MDI путем слияния меню и с применением и элементов управления ToolStrip
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
ms.assetid: 64992ed9-44af-4baf-b45f-863e6ab35711
ms.openlocfilehash: 3e2c85486144a5009f08c7b6ecfd056c7cd86fcf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64612007"
---
# <a name="how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="b084f-102">Практическое руководство. Создание формы MDI путем слияния меню и с применением и элементов управления ToolStrip</span><span class="sxs-lookup"><span data-stu-id="b084f-102">How to: Create an MDI Form with Menu Merging and ToolStrip Controls</span></span>
<span data-ttu-id="b084f-103">Пространство имен <xref:System.Windows.Forms?displayProperty=nameWithType> поддерживает приложения с интерфейсом MDI, а элемент управления <xref:System.Windows.Forms.MenuStrip> поддерживает слияние меню.</span><span class="sxs-lookup"><span data-stu-id="b084f-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="b084f-104">Формы MDI также могут содержать элементы управления <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="b084f-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="b084f-105">Имеется широкая поддержка этой возможности в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b084f-105">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="b084f-106">Также см. в разделе [Пошаговое руководство: Создание формы MDI путем слияния меню и элементов управления ToolStrip](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="b084f-106">Also see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b084f-107">Пример</span><span class="sxs-lookup"><span data-stu-id="b084f-107">Example</span></span>  
 <span data-ttu-id="b084f-108">В примере кода ниже показано использование элементов управления <xref:System.Windows.Forms.ToolStripPanel> с формой MDI.</span><span class="sxs-lookup"><span data-stu-id="b084f-108">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="b084f-109">Форма также поддерживает слияние меню с вложенными меню.</span><span class="sxs-lookup"><span data-stu-id="b084f-109">The form also supports menu merging with child menus.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b084f-110">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="b084f-110">Compiling the Code</span></span>  
 <span data-ttu-id="b084f-111">Для этого примера кода требуются:</span><span class="sxs-lookup"><span data-stu-id="b084f-111">This code example requires:</span></span>  
  
- <span data-ttu-id="b084f-112">ссылки на сборки System.Drawing и System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="b084f-112">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="b084f-113">Сведения о выполнении сборки этого примера из командной строки для Visual Basic или Visual C#, см. в разделе [построение из командной строки](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) или [командной строки создания с помощью csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b084f-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b084f-114">Можно также сборке этого примера в Visual Studio путем вставки кода в новый проект.</span><span class="sxs-lookup"><span data-stu-id="b084f-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b084f-115">См. также</span><span class="sxs-lookup"><span data-stu-id="b084f-115">See also</span></span>

- [<span data-ttu-id="b084f-116">Элемент управления ToolStrip</span><span class="sxs-lookup"><span data-stu-id="b084f-116">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
