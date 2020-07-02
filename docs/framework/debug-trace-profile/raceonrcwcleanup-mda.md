---
title: Помощник по отладке управляемого кода raceOnRCWCleanup
description: Ознакомьтесь с помощником по отладке управляемого кода Рацеонрквклеануп (MDA), который активируется, если RCW используется в другом потоке или в стеке освобождения потоков в .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
ms.openlocfilehash: e86ef96bebb648c7927ae5fec8b68fc4429b268b
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803655"
---
# <a name="raceonrcwcleanup-mda"></a>Помощник по отладке управляемого кода raceOnRCWCleanup
Помощник по отладке управляемого кода (MDA) `raceOnRCWCleanup` активируется, когда среда CLR обнаруживает, что используется [вызываемая оболочка времени выполнения](../../standard/native-interop/runtime-callable-wrapper.md) (RCW), когда выполняется вызов освобождения с помощью команды, такой как метод <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>.  
  
## <a name="symptoms"></a>Симптомы  
 Нарушение прав доступа или повреждение памяти во время или после освобождения RCW с помощью метода <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> или аналогичным способом.  
  
## <a name="cause"></a>Причина  
 RCW используется в другом потоке или в стеке высвобождения потоков.  RCW, которая используется, не может быть освобождена.  
  
## <a name="resolution"></a>Решение  
 Не освобождайте RCW, которая может использоваться в текущем или в других потоках.  
  
## <a name="effect-on-the-runtime"></a>Влияние на среду выполнения  
 Этот помощник отладки управляемого кода не оказывает никакого влияния на среду CLR.  
  
## <a name="output"></a>Вывод  
 Сообщение, описывающее ошибку.  
  
## <a name="configuration"></a>Параметр Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>См. также

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Диагностика ошибок посредством управляемых помощников по отладке](diagnosing-errors-with-managed-debugging-assistants.md)
- [Маршалинг взаимодействия](../interop/interop-marshaling.md)
