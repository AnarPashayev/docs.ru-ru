---
title: Приостановка и прерывание потоков
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interrupting threads
- threading [.NET Framework], pausing
- pausing threads
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
ms.openlocfilehash: 369631603791d90c51244c1dc9907b9d8ec17364
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291166"
---
# <a name="pausing-and-interrupting-threads"></a>Приостановка и прерывание потоков

Наиболее распространенными способами синхронизации действий потоков являются блокировка и освобождение потоков или блокировка объектов или областей кода. Подробнее об этих механизмах фиксации и блокировки см. в разделе [Обзор примитивов синхронизации](overview-of-synchronization-primitives.md).  
  
 Также можно организовать перевод потоков в спящий режим. Если потоки заблокированы или находятся в спящем режиме, можно использовать <xref:System.Threading.ThreadInterruptedException> для вывода потоков из состояния ожидания.  
  
## <a name="the-threadsleep-method"></a>Метод Thread.Sleep

 Вызов метода <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> приводит к немедленной блокировке текущего потока на определенное количество миллисекунд, переданное этому методу, вследствие чего остаток среза времени передается другому потоку. По истечении этого интервала времени спящий поток возобновляет выполнение.  
  
 Поток не может вызвать метод <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> для другого потока.  Статический метод <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> всегда переводит текущий поток в спящий режим.  
  
 Вызов метода <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> с аргументом <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> переводит поток в спящий режим до того момента, пока он не будет прерван другим потоком путем вызова метода <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> или завершен путем вызова метода <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.  В следующем примере показаны оба метода прерывания спящего потока.  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a>Прерывание потоков

 Ожидающий поток можно прервать, вызвав метод <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> для заблокированного потока. Это действие создает исключение <xref:System.Threading.ThreadInterruptedException>, которое выводит поток из вызова блокировки. Поток должен перехватить исключение <xref:System.Threading.ThreadInterruptedException> и выполнить соответствующие действия для продолжения работы. Если поток пропускает исключение, среда выполнения перехватывает его и останавливает поток.  
  
> [!NOTE]
> Если целевой поток не заблокирован при вызове метода <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>, поток не прерывается до блокировки. Если поток никогда не блокируется, он может завершиться, не будучи прерванным.  
  
 Если ожидание является управляемым, методы <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> и <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> незамедлительно выводят поток из спящего режима. Если ожидание является неуправляемым (как, например, вызов неуправляемого кода функции Win32 [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject)), то методы <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> и <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> не могут управлять потоком, пока он не вернется в управляемый код или не вызовет управляемый код. В управляемом коде это поведение выглядит следующим образом:  
  
- <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> выводит поток из состояния ожидания, в котором он может находиться, и приводит к созданию исключения <xref:System.Threading.ThreadInterruptedException> в целевом потоке.  
  
- <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> выводит поток из состояния ожидания, в котором он может находиться, и приводит к созданию исключения <xref:System.Threading.ThreadAbortException> в этом потоке. Подробнее см. в разделе [Уничтожение потоков](destroying-threads.md).  
  
## <a name="see-also"></a>См. также раздел

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadInterruptedException>
- <xref:System.Threading.ThreadAbortException>
- [Работа с потоками](index.md)
- [Использование потоков и работа с потоками](using-threads-and-threading.md)
- [Обзор примитивов синхронизации](overview-of-synchronization-primitives.md)
