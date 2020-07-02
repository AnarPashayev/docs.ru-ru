---
title: MDA с возможностью повторного входа
description: Ознакомьтесь с помощником по отладке управляемого кода (MDA), который может быть активирован, если куча объектов повреждена или возникли другие серьезные ошибки при переходе от машинного кода к управляемому.
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
ms.openlocfilehash: f666e505b8382b0bec8dcfdb34c775850e46c429
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803109"
---
# <a name="reentrancy-mda"></a>MDA с возможностью повторного входа
Помощник по отладке управляемого кода `reentrancy` (MDA) активируется при попытке выполнить переход из машинного кода в управляемый в тех случаях, когда ранее не был выполнен упорядоченный переход из управляемого кода в машинный.  
  
## <a name="symptoms"></a>Симптомы  
 При переходе из машинного кода в управляемый повреждается куча объекта или возникает другая серьезная ошибка.  
  
 Переход в потоке между управляемым и машинным кодом в любом направлении должен быть упорядоченным. Тем не менее для некоторых низкоуровневых точек расширения в операционной системе, таких как векторный обработчик исключений, допускается неупорядоченный переход из управляемого кода в машинный.  Такие переходы осуществляются под управлением операционной системы, а не общеязыковой среды управления (CLR).  В любом машинном коде, который выполняется внутри таких точек расширения, не рекомендуется выполнять обратные вызовы управляемого кода.  
  
## <a name="cause"></a>Причина  
 Низкоуровневая точка расширения операционной системы, например векторный обработчик исключений, активирована при выполнении управляемого кода.  Код приложения, который вызывается посредством этой точки расширения, пытается выполнить обратный вызов управляемого кода.  
  
 Эта проблема всегда связана с кодом приложения.  
  
## <a name="resolution"></a>Решение  
 Проверьте трассировку стека для потока, который вызвал помощник по отладке управляемого кода.  Поток пытается выполнить недопустимый вызов управляемого кода.  В трассировке стека должны быть представлены код приложения, использующий эту точку расширения, предоставляющий ее код операционной системы, а также управляемый код, который был прерван этой точкой расширения.  
  
 Например, этот помощник по отладке управляемого кода активируется при попытке вызвать управляемый код из векторного обработчика исключений.  В стеке будут показаны код обработки исключения операционной системы, а также управляемый код, который вызывает исключение, например <xref:System.DivideByZeroException> или <xref:System.AccessViolationException>.  
  
 В этом примере следует полностью реализовать векторный обработчик исключений в неуправляемом коде.  
  
## <a name="effect-on-the-runtime"></a>Влияние на среду выполнения  
 Этот помощник отладки управляемого кода не оказывает никакого влияния на среду CLR.  
  
## <a name="output"></a>Вывод  
 Помощник по отладке управляемого кода сообщает о попытке недопустимого повторного входа.  Проверьте стек потока, чтобы понять, почему это происходит и как решить проблему. Далее приводится образец вывода.  
  
```output
Additional Information: Attempting to call into managed code without
transitioning out first.  Do not attempt to run managed code inside
low-level native extensibility points. Managed Debugging Assistant
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a>Параметр Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Пример  
 В следующем примере кода возникает исключение <xref:System.AccessViolationException>.  В версиях Windows, которые поддерживают векторную обработку исключений, будет вызван управляемый векторный обработчик исключений.  Если помощник по отладке управляемого кода `reentrancy` включен, он будет активирован при попытке выполнить вызов `MyHandler` из кода векторной обработки исключений операционной системы.  
  
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
  
## <a name="see-also"></a>См. также

- [Диагностика ошибок посредством управляемых помощников по отладке](diagnosing-errors-with-managed-debugging-assistants.md)
