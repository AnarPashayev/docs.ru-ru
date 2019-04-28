---
title: Практическое руководство. Определение нажатой управляющей клавиши
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input
- shift keys
- events [Windows Forms], mouse
- Keys.ControlKey enumeration member
- keys [Windows Forms], control keys
- user input [Windows Forms], checking for keyboard
- keys [Windows Forms], determining last pressed
- keys [Windows Forms], shift keys
- keys [Windows Forms], modifier keys
- control keys
- keys [Windows Forms], alt keys
- alt keys
- Keys.Shift enumeration member
- events [Windows Forms], keyboard
- keyboards [Windows Forms], keyboard input
- Keys.Alt enumeration member
- modifier keys
ms.assetid: 1e184048-0ae3-4067-a200-d4ba31dbc2cb
ms.openlocfilehash: 571af49cdf82b876cfb72a7c7636874c8d155fb7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803146"
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="d1ff8-102">Практическое руководство. Определение нажатой управляющей клавиши</span><span class="sxs-lookup"><span data-stu-id="d1ff8-102">How to: Determine Which Modifier Key Was Pressed</span></span>
<span data-ttu-id="d1ff8-103">При создании приложения, которое принимает нажатия клавиш пользователем, можно также отслеживать за нажатием клавиш клавиши SHIFT, ALT и CTRL.</span><span class="sxs-lookup"><span data-stu-id="d1ff8-103">When you create an application that accepts the user's keystrokes, you may also want to monitor for modifier keys such as the SHIFT, ALT, and CTRL keys.</span></span> <span data-ttu-id="d1ff8-104">При нажатии в сочетании с другими клавишами или с помощью щелчков мыши, приложение может реагировать соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="d1ff8-104">When a modifier key is pressed in combination with other keys, or with mouse clicks, your application can respond appropriately.</span></span> <span data-ttu-id="d1ff8-105">Например если нажата буквы S, это может просто вызвать «s» для отображения на экране, но при нажатии клавиш CTRL + S, текущий документ может быть сохранен.</span><span class="sxs-lookup"><span data-stu-id="d1ff8-105">For example, if the letter S is pressed, this may simply cause an "s" to appear on the screen, but if the keys CTRL+S are pressed, the current document may be saved.</span></span> <span data-ttu-id="d1ff8-106">Если вы обрабатываете <xref:System.Windows.Forms.Control.KeyDown> событий, <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> свойство <xref:System.Windows.Forms.KeyEventArgs> полученных событием обработчик определяет нажатии клавиши-модификаторы.</span><span class="sxs-lookup"><span data-stu-id="d1ff8-106">If you handle the <xref:System.Windows.Forms.Control.KeyDown> event, the <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> received by the event handler specifies which modifier keys are pressed.</span></span> <span data-ttu-id="d1ff8-107">Кроме того <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> свойство <xref:System.Windows.Forms.KeyEventArgs> определяет символ, который также была нажата в сочетании с операцию побитового или любые клавиши-модификаторы.</span><span class="sxs-lookup"><span data-stu-id="d1ff8-107">Alternatively, the <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> property of <xref:System.Windows.Forms.KeyEventArgs> specifies the character that was pressed as well as any modifier keys combined with a bitwise OR.</span></span> <span data-ttu-id="d1ff8-108">Тем не менее если обрабатывается <xref:System.Windows.Forms.Control.KeyPress> события или события мыши, обработчик событий не получает эти сведения.</span><span class="sxs-lookup"><span data-stu-id="d1ff8-108">However, if you are handling the <xref:System.Windows.Forms.Control.KeyPress> event or a mouse event, the event handler does not receive this information.</span></span> <span data-ttu-id="d1ff8-109">В этом случае необходимо использовать <xref:System.Windows.Forms.Control.ModifierKeys%2A> свойство <xref:System.Windows.Forms.Control> класса.</span><span class="sxs-lookup"><span data-stu-id="d1ff8-109">In this case, you must use the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="d1ff8-110">В любом случае необходимо выполнить операцию побитового и соответствующего <xref:System.Windows.Forms.Keys> значения и значения, вы тестируете.</span><span class="sxs-lookup"><span data-stu-id="d1ff8-110">In either case, you must perform a bitwise AND of the appropriate <xref:System.Windows.Forms.Keys> value and the value you are testing.</span></span> <span data-ttu-id="d1ff8-111"><xref:System.Windows.Forms.Keys> Перечисление предоставляет варианты каждого ключа модификатор, поэтому очень важно выполнить побитового и с правильным значением.</span><span class="sxs-lookup"><span data-stu-id="d1ff8-111">The <xref:System.Windows.Forms.Keys> enumeration offers variations of each modifier key, so it is important that you perform the bitwise AND with the correct value.</span></span> <span data-ttu-id="d1ff8-112">Например, клавиша SHIFT представляется <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> и <xref:System.Windows.Forms.Keys.LShiftKey> правильное значение для тестирования является клавиша SHIFT <xref:System.Windows.Forms.Keys.Shift>.</span><span class="sxs-lookup"><span data-stu-id="d1ff8-112">For example, the SHIFT key is represented by <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> and <xref:System.Windows.Forms.Keys.LShiftKey> The correct value to test SHIFT as a modifier key is <xref:System.Windows.Forms.Keys.Shift>.</span></span> <span data-ttu-id="d1ff8-113">Аналогичным образом, для проверки CTRL и ALT качестве модификаторов вы должны использовать <xref:System.Windows.Forms.Keys.Control> и <xref:System.Windows.Forms.Keys.Alt> соответственно.</span><span class="sxs-lookup"><span data-stu-id="d1ff8-113">Similarly, to test for CTRL and ALT as modifiers you should use the <xref:System.Windows.Forms.Keys.Control> and <xref:System.Windows.Forms.Keys.Alt> values, respectively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1ff8-114">Программистов Visual Basic также доступны сведения о ключе через <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> свойство</span><span class="sxs-lookup"><span data-stu-id="d1ff8-114">Visual Basic programmers can also access key information through the <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> property</span></span>  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="d1ff8-115">Чтобы определение нажатой управляющей клавиши</span><span class="sxs-lookup"><span data-stu-id="d1ff8-115">To determine which modifier key was pressed</span></span>  
  
- <span data-ttu-id="d1ff8-116">Используйте побитовый `AND` оператор с <xref:System.Windows.Forms.Control.ModifierKeys%2A> свойство и значение <xref:System.Windows.Forms.Keys> перечисления, чтобы определить, нажата ли клавиша определенного модификатор.</span><span class="sxs-lookup"><span data-stu-id="d1ff8-116">Use the bitwise `AND` operator with the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property and a value of the <xref:System.Windows.Forms.Keys> enumeration to determine whether a particular modifier key is pressed.</span></span> <span data-ttu-id="d1ff8-117">В следующем примере кода показано, как определить, нажата ли клавиша SHIFT в <xref:System.Windows.Forms.Control.KeyPress> обработчик событий.</span><span class="sxs-lookup"><span data-stu-id="d1ff8-117">The following code example shows how to determine whether the SHIFT key is pressed within a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="d1ff8-118">См. также</span><span class="sxs-lookup"><span data-stu-id="d1ff8-118">See also</span></span>

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.ModifierKeys%2A>
- [<span data-ttu-id="d1ff8-119">Ввод с клавиатуры в приложении Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d1ff8-119">Keyboard Input in a Windows Forms Application</span></span>](keyboard-input-in-a-windows-forms-application.md)
- <span data-ttu-id="d1ff8-120">[Практическое руководство. Определить, что если CapsLock включен в Visual Basic](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d1ff8-120">[How to: Determine If CapsLock is On in Visual Basic](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))</span></span>
