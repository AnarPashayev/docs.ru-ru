---
title: gcUnmanagedToManaged MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GC unmanaged to managed
- transitioning threads unmanaged to managed code
- GcUnmanagedToManaged MDA
- threading [.NET Framework], garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
- unmanaged to managed garbage collection
ms.assetid: 103eb3a3-1cf0-4406-8a9a-a7798fdc22d1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1679f87276262a08f5717ea81d263f4600542971
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052763"
---
# <a name="gcunmanagedtomanaged-mda"></a>gcUnmanagedToManaged MDA
Помощник по отладке управляемого кода (MDA) `gcUnmanagedToManaged` вызывает сбор мусора каждый раз, когда поток переходит из неуправляемого в управляемый код.  
  
## <a name="symptoms"></a>Симптомы  
 Приложение, запускающее неуправляемые пользовательские компоненты с помощью модели СОМ и вызова платформы, является причиной недетерминированного нарушения прав доступа в среде CLR.  
  
## <a name="cause"></a>Причина  
 Если приложение выполняет неуправляемые пользовательские компоненты, эти компоненты могут повредить кучу сборки мусора. Это приводит к нарушению прав доступа в среде CLR при попытке сборщика мусора пройти граф объекта.  
  
## <a name="resolution"></a>Решение  
 Включение этого помощника уменьшает время между тем, когда неуправляемый компонент повреждает кучу сборки мусора, и тем, когда происходит нарушение прав доступа принудительным выполнением сборки мусора перед каждой управляемой передачей.  
  
## <a name="effect-on-the-runtime"></a>Влияние на среду выполнения  
 Вызывает сборку мусора каждый раз, когда поток переходит из неуправляемого в управляемый код.  
  
## <a name="output"></a>Вывод  
 Данный MDA не дает результатов.  
  
## <a name="configuration"></a>Конфигурация  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>См. также

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Диагностика ошибок посредством помощников по отладке управляемого кода](diagnosing-errors-with-managed-debugging-assistants.md)
- [gcManagedToUnmanaged](gcmanagedtounmanaged-mda.md)
- [Маршалинг взаимодействия](../interop/interop-marshaling.md)
