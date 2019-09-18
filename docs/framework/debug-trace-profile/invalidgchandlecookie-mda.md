---
title: invalidGCHandleCookie MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid cookies
- cookies, invalid
- managed debugging assistants (MDAs), invalid cookies
- InvalidGCHandleCookie MDA
- invalid cookies
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7452ae28d63c89845b45bf500c02e771f0b8f4df
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052614"
---
# <a name="invalidgchandlecookie-mda"></a>invalidGCHandleCookie MDA
Помощник по отладке управляемого кода (MDA) `invalidGCHandleCookie` активируется при попытке преобразования из недопустимого файла cookie <xref:System.IntPtr> в <xref:System.Runtime.InteropServices.GCHandle>.  
  
## <a name="symptoms"></a>Симптомы  
 Неопределенное поведение, например нарушения прав доступа и повреждение памяти, при попытке использовать или получить <xref:System.Runtime.InteropServices.GCHandle> из <xref:System.IntPtr>.  
  
## <a name="cause"></a>Причина  
 Возможно, файл cookie является недопустимым, так как он не был изначально создан из <xref:System.Runtime.InteropServices.GCHandle>, представляет <xref:System.Runtime.InteropServices.GCHandle>, который уже был освобожден, является файлом cookie для <xref:System.Runtime.InteropServices.GCHandle> в другом домене приложения или был упакован в собственный код как <xref:System.Runtime.InteropServices.GCHandle>, но передан обратно в среду CLR в качестве <xref:System.IntPtr>, где была выполнена попытка приведения к типу.  
  
## <a name="resolution"></a>Решение  
 Укажите допустимый файл cookie <xref:System.IntPtr> для <xref:System.Runtime.InteropServices.GCHandle>.  
  
## <a name="effect-on-the-runtime"></a>Влияние на среду выполнения  
 Если этот MDA включен, отладчик больше не может отслеживать корни обратно в их объекты, поскольку значения файла cookie, переданные обратно, отличаются от значений, возвращаемых при отключенном MDA.  
  
## <a name="output"></a>Вывод  
 Указывается значение недопустимого файла cookie <xref:System.IntPtr>.  
  
## <a name="configuration"></a>Конфигурация  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>См. также

- <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>
- <xref:System.Runtime.InteropServices.GCHandle>
- [Диагностика ошибок посредством помощников по отладке управляемого кода](diagnosing-errors-with-managed-debugging-assistants.md)
