---
title: dangerousThreadingAPI MDA
description: Ознакомьтесь с помощником по отладке управляемого кода Данжерауссреадингапи (MDA), который активируется при вызове Thread. Suspend в потоке, отличном от текущего потока.
ms.date: 03/30/2017
helpviewer_keywords:
- suspending threads
- DangerousThreadingAPI MDA
- managed debugging assistants (MDAs), dangerous threading operations
- threading [.NET Framework], suspending
- MDAs (managed debugging assistants), dangerous threading operations
- Suspend method
- threading [.NET Framework], managed debugging assistants
ms.assetid: 3e5efbc5-92e4-4229-b31f-ce368a1adb96
ms.openlocfilehash: 9069ccb6f106c83db94f88bc464bc0888d28586c
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416009"
---
# <a name="dangerousthreadingapi-mda"></a>dangerousThreadingAPI MDA
Помощник по отладке управляемого кода `dangerousThreadingAPI` (MDA) активируется, если метод <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> вызывается не для текущего потока.  
  
## <a name="symptoms"></a>Симптомы  
 Приложение не отвечает или зависает на неопределенное время. Данные системы или приложения могут остаться в непредсказуемом состоянии на какое-то время или даже после завершения работы приложения. Некоторые операции не завершаются должным образом.  
  
 Из-за случайного характера возникновения этой проблемы ее симптомы могут быть самыми разными.  
  
## <a name="cause"></a>Причина  
 Поток асинхронно приостанавливается другим потоком, использующим метод <xref:System.Threading.Thread.Suspend%2A>. Определить, безопасно ли приостанавливать другой поток, который в текущий момент времени может выполнять другие операции, невозможно. Приостановка потока может привести к повреждению данных или нарушению инвариантов. Если поток приостанавливается и впоследствии не возобновляется с помощью метода <xref:System.Threading.Thread.Resume%2A>, приложение может зависнуть на неопределенное время, что может привести к повреждению его данных. Эти методы помечены как устаревшие.  
  
 Если целевой поток удерживает примитивы синхронизации, они остаются в этом состоянии на протяжении всего времени приостановки. Это может привести к взаимоблокировкам в тех случаях, когда другой поток, например поток, выполняющий <xref:System.Threading.Thread.Suspend%2A>, пытается получить блокировку примитива. В этой ситуации проблема проявляется в виде взаимоблокировки.  
  
## <a name="resolution"></a>Решение  
 По возможности не используйте в коде методы <xref:System.Threading.Thread.Suspend%2A> и <xref:System.Threading.Thread.Resume%2A>. Чтобы обеспечить взаимодействие между потоками, используйте примитивы синхронизации, например <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex> или оператор `lock` C#. Если эти методы все же необходимо использовать, постарайтесь свести к минимуму продолжительность приостановки потока и объем кода, выполняемого в это время.  
  
## <a name="effect-on-the-runtime"></a>Влияние на среду выполнения  
 Этот помощник отладки управляемого кода не оказывает никакого влияния на среду CLR. Он только сообщает сведения о небезопасных потоковых операциях.  
  
## <a name="output"></a>Вывод  
 Этот помощник идентифицирует небезопасный потоковый метод, который стал причиной его активации.  
  
## <a name="configuration"></a>Параметр Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Пример  
 В следующем примере кода демонстрируется вызов метода <xref:System.Threading.Thread.Suspend%2A>, в результате которого активируется помощник `dangerousThreadingAPI`.  
  
```csharp
using System.Threading;  
void FireMda()  
{  
Thread t = new Thread(delegate() { Thread.Sleep(1000); });  
    t.Start();  
    // The following line activates the MDA.  
    t.Suspend();
    t.Resume();  
    t.Join();  
}  
```  
  
## <a name="see-also"></a>См. также

- <xref:System.Threading.Thread>
- [Диагностика ошибок посредством управляемых помощников по отладке](diagnosing-errors-with-managed-debugging-assistants.md)
- [Оператор lock](../../csharp/language-reference/keywords/lock-statement.md)
