---
title: Практическое руководство. Обработка ввода с клавиатуры на уровне формы
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input [Windows Forms], at form level
- Windows Forms, handling keyboard input
- keyboards [Windows Forms], form-level input
ms.assetid: d7f8b390-dc91-42d2-ae0f-2ffa388127ad
ms.openlocfilehash: fbb6587dde53592a94887c1ea19562e06c15afe3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135173"
---
# <a name="how-to-handle-keyboard-input-at-the-form-level"></a><span data-ttu-id="023f6-102">Практическое руководство. Обработка ввода с клавиатуры на уровне формы</span><span class="sxs-lookup"><span data-stu-id="023f6-102">How to: Handle Keyboard Input at the Form Level</span></span>
<span data-ttu-id="023f6-103">Windows Forms предоставляет возможность обработки сообщений клавиатуры на уровне формы, прежде чем они достигнут элемента управления.</span><span class="sxs-lookup"><span data-stu-id="023f6-103">Windows Forms provides the ability to handle keyboard messages at the form level, before the messages reach a control.</span></span> <span data-ttu-id="023f6-104">В этом разделе показано, как выполнить данную задачу.</span><span class="sxs-lookup"><span data-stu-id="023f6-104">This topic shows how to accomplish this task.</span></span>  
  
### <a name="to-handle-a-keyboard-message-at-the-form-level"></a><span data-ttu-id="023f6-105">Обработка ввода с клавиатуры на уровне формы</span><span class="sxs-lookup"><span data-stu-id="023f6-105">To handle a keyboard message at the form level</span></span>  
  
-   <span data-ttu-id="023f6-106">Чтобы сообщения клавиатуры принимались формой, прежде чем они достигнут элементов управления в форме, нужно обработать события <xref:System.Windows.Forms.Control.KeyPress> или <xref:System.Windows.Forms.Control.KeyDown> начальной формы и присвоить свойству формы <xref:System.Windows.Forms.Form.KeyPreview%2A> значение `true`.</span><span class="sxs-lookup"><span data-stu-id="023f6-106">Handle the <xref:System.Windows.Forms.Control.KeyPress> or <xref:System.Windows.Forms.Control.KeyDown> event of the startup form, and set the <xref:System.Windows.Forms.Form.KeyPreview%2A> property of the form to `true` so that keyboard messages are received by the form before they reach any controls on the form.</span></span> <span data-ttu-id="023f6-107">В следующем примере кода обрабатывается событие <xref:System.Windows.Forms.Control.KeyPress> посредством обнаружения всех цифровых клавиш и использования "1", "4" и "7".</span><span class="sxs-lookup"><span data-stu-id="023f6-107">The following code example handles the <xref:System.Windows.Forms.Control.KeyPress> event by detecting all of the number keys and consuming '1', '4', and '7'.</span></span>  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="023f6-108">Пример</span><span class="sxs-lookup"><span data-stu-id="023f6-108">Example</span></span>  
 <span data-ttu-id="023f6-109">В следующем примере кода представлено завершенное приложение для предыдущего примера кода.</span><span class="sxs-lookup"><span data-stu-id="023f6-109">The following code example is the entire application for the above example.</span></span> <span data-ttu-id="023f6-110">Приложение включает <xref:System.Windows.Forms.TextBox> и несколько других элементов управления, предназначенных для перемещения фокуса ввода из <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="023f6-110">The application includes a <xref:System.Windows.Forms.TextBox> along with several other controls that allow you to move focus from the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="023f6-111">Событие <xref:System.Windows.Forms.Control.KeyPress> основной формы <xref:System.Windows.Forms.Form> использует "1", "4" и "7", а событие <xref:System.Windows.Forms.Control.KeyPress> в <xref:System.Windows.Forms.TextBox> использует "2", "5" и "8", остальные клавиши отображаются.</span><span class="sxs-lookup"><span data-stu-id="023f6-111">The <xref:System.Windows.Forms.Control.KeyPress> event of the main <xref:System.Windows.Forms.Form> consumes '1', '4', and '7', and the <xref:System.Windows.Forms.Control.KeyPress> event of the <xref:System.Windows.Forms.TextBox> consumes '2', '5', and '8' while displaying the remaining keys.</span></span> <span data-ttu-id="023f6-112">Сравните выходные данные <xref:System.Windows.Forms.MessageBox> при нажатии цифровой клавиши, когда фокус ввода установлен на <xref:System.Windows.Forms.TextBox> с выходными данными <xref:System.Windows.Forms.MessageBox> при нажатии цифровой клавиши, когда фокус ввода установлен на одном из других элементов управления.</span><span class="sxs-lookup"><span data-stu-id="023f6-112">Compare the <xref:System.Windows.Forms.MessageBox> output when you press a number key while the <xref:System.Windows.Forms.TextBox> has focus with the <xref:System.Windows.Forms.MessageBox> output when you press a number key while focus is on one of the other controls.</span></span>  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="023f6-113">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="023f6-113">Compiling the Code</span></span>  
 <span data-ttu-id="023f6-114">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="023f6-114">This example requires:</span></span>  
  
-   <span data-ttu-id="023f6-115">ссылки на сборки System, System.Drawing и System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="023f6-115">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="023f6-116">Сведения о выполнении сборки этого примера из командной строки для Visual Basic или Visual C#, см. в разделе [построение из командной строки](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) или [командной строки создания с помощью csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="023f6-116">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="023f6-117">Можно также сборке этого примера в Visual Studio путем вставки кода в новый проект.</span><span class="sxs-lookup"><span data-stu-id="023f6-117">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  

## <a name="see-also"></a><span data-ttu-id="023f6-118">См. также</span><span class="sxs-lookup"><span data-stu-id="023f6-118">See also</span></span>

- [<span data-ttu-id="023f6-119">Ввод с клавиатуры в приложении Windows Forms</span><span class="sxs-lookup"><span data-stu-id="023f6-119">Keyboard Input in a Windows Forms Application</span></span>](keyboard-input-in-a-windows-forms-application.md)
