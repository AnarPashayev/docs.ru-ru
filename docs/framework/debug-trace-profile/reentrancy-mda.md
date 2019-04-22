---
title: MDA с возможностью повторного входа
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged code, debugging
- transitioning threads unmanaged to managed code
- reentrancy MDA
- reentrancy without an orderly transition
- managed debugging assistants (MDAs), reentrancy
- illegal reentrancy
- MDAs (managed debugging assistants), reentrancy
- threading [.NET Framework], managed debugging assistants
- managed code, debugging
- native debugging, MDAs
ms.assetid: 7240c3f3-7df8-4b03-bbf1-17cdce142d45
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7de0a869925816da6df8f17e14ab92964aec8d11
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59094220"
---
# <a name="reentrancy-mda"></a><span data-ttu-id="19277-102">MDA с возможностью повторного входа</span><span class="sxs-lookup"><span data-stu-id="19277-102">reentrancy MDA</span></span>
<span data-ttu-id="19277-103">Помощник по отладке управляемого кода `reentrancy` (MDA) активируется при попытке выполнить переход из машинного кода в управляемый в тех случаях, когда ранее не был выполнен упорядоченный переход из управляемого кода в машинный.</span><span class="sxs-lookup"><span data-stu-id="19277-103">The `reentrancy` managed debugging assistant (MDA) is activated when an attempt is made to transition from native to managed code in cases where a prior switch from managed to native code was not performed through an orderly transition.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="19277-104">Симптомы</span><span class="sxs-lookup"><span data-stu-id="19277-104">Symptoms</span></span>  
 <span data-ttu-id="19277-105">При переходе из машинного кода в управляемый повреждается куча объекта или возникает другая серьезная ошибка.</span><span class="sxs-lookup"><span data-stu-id="19277-105">The object heap is corrupted or other serious errors are occurring when transitioning from native to managed code.</span></span>  
  
 <span data-ttu-id="19277-106">Переход в потоке между управляемым и машинным кодом в любом направлении должен быть упорядоченным.</span><span class="sxs-lookup"><span data-stu-id="19277-106">Threads that switch between native and managed code in either direction must perform an orderly transition.</span></span> <span data-ttu-id="19277-107">Тем не менее для некоторых низкоуровневых точек расширения в операционной системе, таких как векторный обработчик исключений, допускается неупорядоченный переход из управляемого кода в машинный.</span><span class="sxs-lookup"><span data-stu-id="19277-107">However, certain low-level extensibility points in the operating system, such as the vectored exception handler, allow switches from managed to native code without performing an orderly transition.</span></span>  <span data-ttu-id="19277-108">Такие переходы осуществляются под управлением операционной системы, а не общеязыковой среды управления (CLR).</span><span class="sxs-lookup"><span data-stu-id="19277-108">These switches are under operating system control, rather than under common language runtime (CLR) control.</span></span>  <span data-ttu-id="19277-109">В любом машинном коде, который выполняется внутри таких точек расширения, не рекомендуется выполнять обратные вызовы управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="19277-109">Any native code that executes inside these extensibility points must avoid calling back into managed code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="19277-110">Причина</span><span class="sxs-lookup"><span data-stu-id="19277-110">Cause</span></span>  
 <span data-ttu-id="19277-111">Низкоуровневая точка расширения операционной системы, например векторный обработчик исключений, активирована при выполнении управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="19277-111">A low-level operating system extensibility point, such as the vectored exception handler, has activated while executing managed code.</span></span>  <span data-ttu-id="19277-112">Код приложения, который вызывается посредством этой точки расширения, пытается выполнить обратный вызов управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="19277-112">The application code that is invoked through that extensibility point is attempting to call back into managed code.</span></span>  
  
 <span data-ttu-id="19277-113">Эта проблема всегда связана с кодом приложения.</span><span class="sxs-lookup"><span data-stu-id="19277-113">This problem is always caused by application code.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="19277-114">Решение</span><span class="sxs-lookup"><span data-stu-id="19277-114">Resolution</span></span>  
 <span data-ttu-id="19277-115">Проверьте трассировку стека для потока, который вызвал помощник по отладке управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="19277-115">Examine the stack trace for the thread that has activated this MDA.</span></span>  <span data-ttu-id="19277-116">Поток пытается выполнить недопустимый вызов управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="19277-116">The thread is attempting to illegally call into managed code.</span></span>  <span data-ttu-id="19277-117">В трассировке стека должны быть представлены код приложения, использующий эту точку расширения, предоставляющий ее код операционной системы, а также управляемый код, который был прерван этой точкой расширения.</span><span class="sxs-lookup"><span data-stu-id="19277-117">The stack trace should reveal the application code using this extensibility point, the operating system code that provides this extensibility point, and the managed code that was interrupted by the extensibility point.</span></span>  
  
 <span data-ttu-id="19277-118">Например, этот помощник по отладке управляемого кода активируется при попытке вызвать управляемый код из векторного обработчика исключений.</span><span class="sxs-lookup"><span data-stu-id="19277-118">For example, you will see the MDA activated in an attempt to call managed code from inside a vectored exception handler.</span></span>  <span data-ttu-id="19277-119">В стеке будут показаны код обработки исключения операционной системы, а также управляемый код, который вызывает исключение, например <xref:System.DivideByZeroException> или <xref:System.AccessViolationException>.</span><span class="sxs-lookup"><span data-stu-id="19277-119">On the stack you will see the operating system exception handling code and some managed code triggering an exception such as a <xref:System.DivideByZeroException> or an <xref:System.AccessViolationException>.</span></span>  
  
 <span data-ttu-id="19277-120">В этом примере следует полностью реализовать векторный обработчик исключений в неуправляемом коде.</span><span class="sxs-lookup"><span data-stu-id="19277-120">In this example, the correct resolution is to implement the vectored exception handler completely in unmanaged code.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="19277-121">Влияние на среду выполнения</span><span class="sxs-lookup"><span data-stu-id="19277-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="19277-122">Этот помощник отладки управляемого кода не оказывает никакого влияния на среду CLR.</span><span class="sxs-lookup"><span data-stu-id="19277-122">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="19277-123">Вывод</span><span class="sxs-lookup"><span data-stu-id="19277-123">Output</span></span>  
 <span data-ttu-id="19277-124">Помощник по отладке управляемого кода сообщает о попытке недопустимого повторного входа.</span><span class="sxs-lookup"><span data-stu-id="19277-124">The MDA reports that illegal reentrancy is being attempted.</span></span>  <span data-ttu-id="19277-125">Проверьте стек потока, чтобы понять, почему это происходит и как решить проблему.</span><span class="sxs-lookup"><span data-stu-id="19277-125">Examine the thread's stack to determine why this is happening and how to correct the problem.</span></span> <span data-ttu-id="19277-126">Далее приводится образец вывода.</span><span class="sxs-lookup"><span data-stu-id="19277-126">The following is sample output.</span></span>  
  
```  
Additional Information: Attempting to call into managed code without   
transitioning out first.  Do not attempt to run managed code inside   
low-level native extensibility points. Managed Debugging Assistant   
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a><span data-ttu-id="19277-127">Параметр Configuration</span><span class="sxs-lookup"><span data-stu-id="19277-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="19277-128">Пример</span><span class="sxs-lookup"><span data-stu-id="19277-128">Example</span></span>  
 <span data-ttu-id="19277-129">В следующем примере кода возникает исключение <xref:System.AccessViolationException>.</span><span class="sxs-lookup"><span data-stu-id="19277-129">The following code example causes an <xref:System.AccessViolationException> to be thrown.</span></span>  <span data-ttu-id="19277-130">В версиях Windows, которые поддерживают векторную обработку исключений, будет вызван управляемый векторный обработчик исключений.</span><span class="sxs-lookup"><span data-stu-id="19277-130">On versions of Windows that support vectored exception handling, this will cause the managed vectored exception handler to be called.</span></span>  <span data-ttu-id="19277-131">Если помощник по отладке управляемого кода `reentrancy` включен, он будет активирован при попытке выполнить вызов `MyHandler` из кода векторной обработки исключений операционной системы.</span><span class="sxs-lookup"><span data-stu-id="19277-131">If the `reentrancy` MDA is enabled, the MDA will activate during the attempted call to `MyHandler` from the operating system's vectored exception handling support code.</span></span>  
  
```csharp
using System;  
public delegate int ExceptionHandler(IntPtr ptrExceptionInfo);  
  
public class Reenter   
{  
    public static ExceptionHandler keepAlive;  
  
    [System.Runtime.InteropServices.DllImport("kernel32", ExactSpelling=true,   
        CharSet=System.Runtime.InteropServices.CharSet.Auto)]  
    public static extern IntPtr AddVectoredExceptionHandler(int bFirst,   
        ExceptionHandler handler);  
  
    static int MyHandler(IntPtr ptrExceptionInfo)   
    {  
        // EXCEPTION_CONTINUE_SEARCH  
        return 0;  
    }  
    void Run() {}  
  
    static void Main()   
    {  
        keepAlive = new ExceptionHandler(Reenter.MyHandler);  
        IntPtr ret = AddVectoredExceptionHandler(1, keepAlive);  
        try   
        {  
            // Dispatch on null should AV.  
            Reenter r = null;   
            r.Run();  
        }   
        catch { }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="19277-132">См. также</span><span class="sxs-lookup"><span data-stu-id="19277-132">See also</span></span>

- [<span data-ttu-id="19277-133">Диагностика ошибок посредством помощников по отладке управляемого кода</span><span class="sxs-lookup"><span data-stu-id="19277-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
