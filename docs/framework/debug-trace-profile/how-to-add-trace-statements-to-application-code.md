---
title: Практическое руководство. Добавление операторов трассировки в код приложения
description: Сведения о добавлении операторов трассировки в код приложения в .NET. Методы, наиболее часто используемые для трассировки, — это методы для записи выходных данных в прослушиватели.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework], conditional writes based on switches
- trace statements
- WriteLineIf method
- tracing [.NET Framework], adding trace statements
- Assert method, tracing code
- trace switches, conditional writes based on switches
- WriteIf method
ms.assetid: f3a93fa7-1717-467d-aaff-393e5c9828b4
ms.openlocfilehash: 6beecf39d4372a194a9110ed8942b998443934d4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244214"
---
# <a name="how-to-add-trace-statements-to-application-code"></a><span data-ttu-id="05bfd-104">Практическое руководство. Добавление операторов трассировки в код приложения</span><span class="sxs-lookup"><span data-stu-id="05bfd-104">How to: Add Trace Statements to Application Code</span></span>

<span data-ttu-id="05bfd-105">Методы, наиболее часто используемые для отслеживания, — это методы для записи выходных данных в прослушиватели: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert** и **Fail**.</span><span class="sxs-lookup"><span data-stu-id="05bfd-105">The methods used most often for tracing are the methods for writing output to listeners: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**, and **Fail**.</span></span> <span data-ttu-id="05bfd-106">Эти методы можно разделить на две категории: **Write**, **WriteLine** и **Fail** выдают выходные данные безусловно, в то время как методы **WriteIf**, **WriteLineIf** и **Assert** тестируют условие Boolean и выполняют или не выполняют запись в зависимости от значения условия.</span><span class="sxs-lookup"><span data-stu-id="05bfd-106">These methods can be divided into two categories: **Write**, **WriteLine**, and **Fail** all emit output unconditionally, whereas **WriteIf**, **WriteLineIf**, and **Assert** test a Boolean condition, and write or do not write based on the value of the condition.</span></span> <span data-ttu-id="05bfd-107">**WriteIf** и **WriteLineIf** выдают выходные данные, если условие равно `true`, а **Assert** выдает выходные данные, если условие равно `false`.</span><span class="sxs-lookup"><span data-stu-id="05bfd-107">**WriteIf** and **WriteLineIf** emit output if the condition is `true`, and **Assert** emits output if the condition is `false`.</span></span>  
  
 <span data-ttu-id="05bfd-108">При разработке своей стратегии трассировки и отладки следует подумать о способе представления вывода.</span><span class="sxs-lookup"><span data-stu-id="05bfd-108">When designing your tracing and debugging strategy, you should think about how you want the output to look.</span></span> <span data-ttu-id="05bfd-109">Несколько инструкций **Write** , заполненных несвязанными данными, создают журнал, который трудно прочитать.</span><span class="sxs-lookup"><span data-stu-id="05bfd-109">Multiple **Write** statements filled with unrelated information will create a log that is difficult to read.</span></span> <span data-ttu-id="05bfd-110">С другой стороны, использование метода **WriteLine** для размещения связанных инструкций на отдельных строках может усложнить определение того, какая информация относится к друг другу.</span><span class="sxs-lookup"><span data-stu-id="05bfd-110">On the other hand, using **WriteLine** to put related statements on separate lines may make it difficult to distinguish what information belongs together.</span></span> <span data-ttu-id="05bfd-111">В общем случае следует использовать несколько инструкций **Write** , если нужно объединить данные из нескольких источников для создания одного информативного сообщения, и использовать инструкцию **WriteLine** , если необходимо создать одно сообщение.</span><span class="sxs-lookup"><span data-stu-id="05bfd-111">In general, use multiple **Write** statements when you want to combine information from multiple sources to create a single informative message, and use the **WriteLine** statement when you want to create a single, complete message.</span></span>  
  
### <a name="to-write-a-complete-line"></a><span data-ttu-id="05bfd-112">Запись полной строки</span><span class="sxs-lookup"><span data-stu-id="05bfd-112">To write a complete line</span></span>  
  
1. <span data-ttu-id="05bfd-113">Вызовите метод <xref:System.Diagnostics.Trace.WriteLine%2A> или <xref:System.Diagnostics.Trace.WriteLineIf%2A>.</span><span class="sxs-lookup"><span data-stu-id="05bfd-113">Call the <xref:System.Diagnostics.Trace.WriteLine%2A> or <xref:System.Diagnostics.Trace.WriteLineIf%2A> method.</span></span>  
  
     <span data-ttu-id="05bfd-114">Символ возврата каретки добавляется в конец сообщения, возвращаемого этим методом, чтобы следующее сообщение, возвращаемое методом **Write**, **WriteIf**, **WriteLine** или **WriteLineIf**, начиналось со следующей строки:</span><span class="sxs-lookup"><span data-stu-id="05bfd-114">A carriage return is appended to the end of the message this method returns, so that the next message returned by **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the following line:</span></span>  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteLine("Error in AppendData procedure.")  
    Trace.WriteLineIf(errorFlag, "Error in AppendData procedure.")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteLine ("Error in AppendData procedure.");  
    System.Diagnostics.Trace.WriteLineIf(errorFlag,
       "Error in AppendData procedure.");  
    ```  
  
### <a name="to-write-a-partial-line"></a><span data-ttu-id="05bfd-115">Запись частичной строки</span><span class="sxs-lookup"><span data-stu-id="05bfd-115">To write a partial line</span></span>  
  
1. <span data-ttu-id="05bfd-116">Вызовите метод <xref:System.Diagnostics.Trace.Write%2A> или <xref:System.Diagnostics.Trace.WriteIf%2A>.</span><span class="sxs-lookup"><span data-stu-id="05bfd-116">Call the <xref:System.Diagnostics.Trace.Write%2A> or <xref:System.Diagnostics.Trace.WriteIf%2A> method.</span></span>  
  
     <span data-ttu-id="05bfd-117">Следующее сообщение, выдаваемое оператором **Write**, **WriteIf**, **WriteLine** или **WriteLineIf**, начинается на той же строке, что и сообщение, выданное оператором **Write** или **WriteIf**:</span><span class="sxs-lookup"><span data-stu-id="05bfd-117">The next message put out by a **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the same line as the message put out by the **Write** or **WriteIf** statement:</span></span>  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteIf(errorFlag, "Error in AppendData procedure.")  
    Debug.WriteIf(errorFlag, "Transaction abandoned.")  
    Trace.Write("Invalid value for data request")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteIf(errorFlag,
       "Error in AppendData procedure.");  
    System.Diagnostics.Debug.WriteIf(errorFlag, "Transaction abandoned.");  
    Trace.Write("Invalid value for data request");  
    ```  
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a><span data-ttu-id="05bfd-118">Проверка наличия определенного условия до или после выполнения метода</span><span class="sxs-lookup"><span data-stu-id="05bfd-118">To verify that certain conditions exist either before or after you execute a method</span></span>  
  
1. <span data-ttu-id="05bfd-119">Вызовите метод <xref:System.Diagnostics.Trace.Assert%2A>.</span><span class="sxs-lookup"><span data-stu-id="05bfd-119">Call the <xref:System.Diagnostics.Trace.Assert%2A> method.</span></span>  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="05bfd-120">Оператор **Assert** можно использовать и для отладки, и для трассировки.</span><span class="sxs-lookup"><span data-stu-id="05bfd-120">You can use **Assert** with both tracing and debugging.</span></span> <span data-ttu-id="05bfd-121">В этом примере стек вызовов выводится в любой прослушиватель в коллекции **Listeners**.</span><span class="sxs-lookup"><span data-stu-id="05bfd-121">This example outputs the call stack to any listener in the **Listeners** collection.</span></span> <span data-ttu-id="05bfd-122">Дополнительные сведения см. в разделах [Утверждения в управляемом коде](/visualstudio/debugger/assertions-in-managed-code) и <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="05bfd-122">For more information, see [Assertions in Managed Code](/visualstudio/debugger/assertions-in-managed-code) and <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05bfd-123">См. также</span><span class="sxs-lookup"><span data-stu-id="05bfd-123">See also</span></span>

- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [<span data-ttu-id="05bfd-124">Трассировка и инструментирование приложений</span><span class="sxs-lookup"><span data-stu-id="05bfd-124">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="05bfd-125">Практическое руководство. Создание, инициализация и настройка переключателей трассировки</span><span class="sxs-lookup"><span data-stu-id="05bfd-125">How to: Create, Initialize and Configure Trace Switches</span></span>](how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="05bfd-126">Переключатели трассировки</span><span class="sxs-lookup"><span data-stu-id="05bfd-126">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="05bfd-127">Прослушиватели трассировки</span><span class="sxs-lookup"><span data-stu-id="05bfd-127">Trace Listeners</span></span>](trace-listeners.md)
