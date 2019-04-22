---
title: Как выполнить Отображение доступных последовательных портов в Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: 57b3a33fecb6128a10ce903fd26724de98acb8c1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834651"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a><span data-ttu-id="88270-102">Как выполнить Отображение доступных последовательных портов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="88270-102">How to: Show Available Serial Ports in Visual Basic</span></span>
<span data-ttu-id="88270-103">В этом разделе описывается использование объекта `My.Computer.Ports` для отображения доступных последовательных портов компьютера в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="88270-103">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in Visual Basic.</span></span>  
  
 <span data-ttu-id="88270-104">Чтобы дать пользователю возможность выбрать используемый порт, имена последовательных портов отображаются в элементе управления <xref:System.Windows.Forms.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="88270-104">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88270-105">Пример</span><span class="sxs-lookup"><span data-stu-id="88270-105">Example</span></span>  
 <span data-ttu-id="88270-106">В этом примере циклически перебираются все строки, которые возвращает свойство `My.Computer.Ports.SerialPortNames`.</span><span class="sxs-lookup"><span data-stu-id="88270-106">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span></span> <span data-ttu-id="88270-107">Эти строки представляют собой имена доступных последовательных портов на компьютере.</span><span class="sxs-lookup"><span data-stu-id="88270-107">These strings are the names of the available serial ports on the computer.</span></span>  
  
 <span data-ttu-id="88270-108">Как правило, пользователь выбирает, какой последовательный порт приложение должно использовать из списка доступных портов.</span><span class="sxs-lookup"><span data-stu-id="88270-108">Typically, a user selects which serial port the application should use from the list of available ports.</span></span> <span data-ttu-id="88270-109">В этом примере имена последовательных портов хранятся в элементе управления <xref:System.Windows.Forms.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="88270-109">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span></span> <span data-ttu-id="88270-110">Дополнительные сведения см. в разделе [Элемент управления ListBox](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="88270-110">For more information, see [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span></span>  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 <span data-ttu-id="88270-111">Этот пример кода также доступен в качестве фрагмента кода IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="88270-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="88270-112">В средстве выбора фрагмента кода он расположен в разделе **Связь и сеть**.</span><span class="sxs-lookup"><span data-stu-id="88270-112">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="88270-113">Дополнительные сведения см. в статье [Фрагменты кода](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="88270-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="88270-114">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="88270-114">Compiling the Code</span></span>  
 <span data-ttu-id="88270-115">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="88270-115">This example requires:</span></span>  
  
-   <span data-ttu-id="88270-116">Ссылка проекта на System.Windows.Forms.dll.</span><span class="sxs-lookup"><span data-stu-id="88270-116">A project reference to System.Windows.Forms.dll.</span></span>  
  
-   <span data-ttu-id="88270-117">Доступ к членам пространства имен <xref:System.Windows.Forms>.</span><span class="sxs-lookup"><span data-stu-id="88270-117">Access to the members of the <xref:System.Windows.Forms> namespace.</span></span> <span data-ttu-id="88270-118">Добавьте оператор `Imports`, если в коде не используются полные имена членов.</span><span class="sxs-lookup"><span data-stu-id="88270-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="88270-119">Дополнительные сведения см. в статье [Оператор Imports (пространство имен .NET и тип)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="88270-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
-   <span data-ttu-id="88270-120">Ваша форма должна включать элемент управления <xref:System.Windows.Forms.ListBox> с именем `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="88270-120">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="88270-121">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="88270-121">Robust Programming</span></span>  
 <span data-ttu-id="88270-122">Необязательно использовать элемент управления <xref:System.Windows.Forms.ListBox> для отображения имен доступных последовательных портов.</span><span class="sxs-lookup"><span data-stu-id="88270-122">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span></span> <span data-ttu-id="88270-123">Вместо него можно использовать <xref:System.Windows.Forms.ComboBox> или другой элемент управления.</span><span class="sxs-lookup"><span data-stu-id="88270-123">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span></span> <span data-ttu-id="88270-124">Если приложение не требует реакции от пользователя, можно использовать для отображения информации элемент управления <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="88270-124">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88270-125">Имена портов, возвращаемые свойством `My.Computer.Ports.SerialPortNames`, могут быть неверными при выполнении программы в Windows 98.</span><span class="sxs-lookup"><span data-stu-id="88270-125">The port names returned by `My.Computer.Ports.SerialPortNames` may be incorrect when run on Windows 98.</span></span> <span data-ttu-id="88270-126">Во избежание ошибок приложения используйте обработку исключений, например оператор `Try...Catch...Finally` или оператор `Using`, если для открытия портов необходимо использовать их имена.</span><span class="sxs-lookup"><span data-stu-id="88270-126">To prevent application errors, use exception handling, such as the `Try...Catch...Finally` statement or the `Using` statement, when using the port names to open ports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88270-127">См. также</span><span class="sxs-lookup"><span data-stu-id="88270-127">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="88270-128">Практическое руководство. Дозвон при помощи модема, подключенного к последовательному порту компьютера</span><span class="sxs-lookup"><span data-stu-id="88270-128">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="88270-129">Практическое руководство. Отправка строк в последовательные порты</span><span class="sxs-lookup"><span data-stu-id="88270-129">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="88270-130">Практическое руководство. Получение строк из последовательных портов</span><span class="sxs-lookup"><span data-stu-id="88270-130">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
