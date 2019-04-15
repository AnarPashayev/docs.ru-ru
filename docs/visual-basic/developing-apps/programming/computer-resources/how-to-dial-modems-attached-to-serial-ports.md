---
title: Практическое руководство. Дозвон при помощи модема, подключенного к последовательному порту компьютера, в Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: db482af7750012d8805d4f834063a2c82224cf67
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59337036"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a><span data-ttu-id="4936c-102">Практическое руководство. Дозвон при помощи модема, подключенного к последовательному порту компьютера, в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4936c-102">How to: Dial Modems Attached to Serial Ports in Visual Basic</span></span>
<span data-ttu-id="4936c-103">В этом разделе описывается использование `My.Computer.Ports` для дозвона с помощью модема в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4936c-103">This topic describes how to use `My.Computer.Ports` to dial a modem in Visual Basic.</span></span>  
  
 <span data-ttu-id="4936c-104">Как правило, модем подключен к одному из последовательных портов на компьютере.</span><span class="sxs-lookup"><span data-stu-id="4936c-104">Typically, the modem is connected to one of the serial ports on the computer.</span></span> <span data-ttu-id="4936c-105">Чтобы приложение могло взаимодействовать с модемом, оно должно отправлять команды на соответствующий последовательный порт.</span><span class="sxs-lookup"><span data-stu-id="4936c-105">For your application to communicate with the modem, it must send commands to the appropriate serial port.</span></span>  
  
### <a name="to-dial-a-modem"></a><span data-ttu-id="4936c-106">Набор номера модема</span><span class="sxs-lookup"><span data-stu-id="4936c-106">To dial a modem</span></span>  
  
1. <span data-ttu-id="4936c-107">Определите, к какому последовательному порту подключен модем.</span><span class="sxs-lookup"><span data-stu-id="4936c-107">Determine which serial port the modem is connected to.</span></span> <span data-ttu-id="4936c-108">В этом примере предполагается, что модем подключен к порту COM1.</span><span class="sxs-lookup"><span data-stu-id="4936c-108">This example assumes the modem is on COM1.</span></span>  
  
2. <span data-ttu-id="4936c-109">Воспользуйтесь методом `My.Computer.Ports.OpenSerialPort`, чтобы получить ссылку на порт.</span><span class="sxs-lookup"><span data-stu-id="4936c-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="4936c-110">Для получения дополнительной информации см. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="4936c-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="4936c-111">Блок `Using` позволяет приложению закрыть последовательный порт даже в том случае, если он создает исключение.</span><span class="sxs-lookup"><span data-stu-id="4936c-111">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="4936c-112">В блоке `Try...Catch...Finally` должен отображаться весь код, управляющий последовательным портом.</span><span class="sxs-lookup"><span data-stu-id="4936c-112">All code that manipulates the serial port should appear within this block, or within a `Try...Catch...Finally` block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3. <span data-ttu-id="4936c-113">Задайте свойство `DtrEnable`, чтобы указать, что компьютер готов принять входящие данные от модема.</span><span class="sxs-lookup"><span data-stu-id="4936c-113">Set the `DtrEnable` property to indicate that the computer is ready to accept an incoming transmission from the modem.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4. <span data-ttu-id="4936c-114">Отправьте команду вызова и номер телефона на модем через последовательный порт с помощью метода <xref:System.IO.Ports.SerialPort.Write%2A>.</span><span class="sxs-lookup"><span data-stu-id="4936c-114">Send the dial command and the phone number to the modem through the serial port by means of the <xref:System.IO.Ports.SerialPort.Write%2A> method.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="4936c-115">Пример</span><span class="sxs-lookup"><span data-stu-id="4936c-115">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 <span data-ttu-id="4936c-116">Этот пример кода также доступен в качестве фрагмента кода IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="4936c-116">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="4936c-117">В средстве выбора фрагмента кода он расположен в разделе **Связь и сеть**.</span><span class="sxs-lookup"><span data-stu-id="4936c-117">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="4936c-118">Дополнительные сведения см. в статье [Фрагменты кода](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="4936c-118">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4936c-119">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="4936c-119">Compiling the Code</span></span>  
 <span data-ttu-id="4936c-120">В этом примере нужна ссылка на пространство имен <xref:System?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4936c-120">This example requires a reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="4936c-121">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="4936c-121">Robust Programming</span></span>  
 <span data-ttu-id="4936c-122">В этом примере предполагается, что модем подключен к порту COM1.</span><span class="sxs-lookup"><span data-stu-id="4936c-122">This example assumes the modem is connected to COM1.</span></span> <span data-ttu-id="4936c-123">Рекомендуется, чтобы код позволял пользователю выбирать нужный последовательный порт из списка доступных портов.</span><span class="sxs-lookup"><span data-stu-id="4936c-123">We recommend that your code allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="4936c-124">Дополнительные сведения см. в разделе [Как Отображение доступных последовательных портов](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="4936c-124">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="4936c-125">В этом примере блок `Using` позволяет сделать так, чтобы приложение закрыло порт, даже если он создает исключение.</span><span class="sxs-lookup"><span data-stu-id="4936c-125">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="4936c-126">Дополнительные сведения см. в разделе [Оператор using](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4936c-126">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
 <span data-ttu-id="4936c-127">В этом примере приложение отключает последовательный порт после вызова модема.</span><span class="sxs-lookup"><span data-stu-id="4936c-127">In this example, the application disconnects the serial port after it dials the modem.</span></span> <span data-ttu-id="4936c-128">В действительности вам потребуется передать данные на модем и получить их от него.</span><span class="sxs-lookup"><span data-stu-id="4936c-128">Realistically, you will want to transfer data to and from the modem.</span></span> <span data-ttu-id="4936c-129">Дополнительные сведения см. в разделе [Как Получение строк из последовательных портов](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="4936c-129">For more information, see [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4936c-130">См. также</span><span class="sxs-lookup"><span data-stu-id="4936c-130">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="4936c-131">Практическое руководство. Отправка строк в последовательные порты</span><span class="sxs-lookup"><span data-stu-id="4936c-131">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="4936c-132">Практическое руководство. Получение строк из последовательных портов</span><span class="sxs-lookup"><span data-stu-id="4936c-132">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
- [<span data-ttu-id="4936c-133">Практическое руководство. Отображение доступных последовательных портов</span><span class="sxs-lookup"><span data-stu-id="4936c-133">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
