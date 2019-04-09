---
title: Помощник по отладке управляемого кода reportAvOnComRelease
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), reference counting errors
- exceptions, reference counting errors
- ReportAvOnComRelease MDA
- COM release access violations
- user reference counting errors
- managed debugging assistants (MDAs), reference counting errors
- report access violation on Com release
- reference counting errors
ms.assetid: a2b86b63-08b2-4943-b344-3c2cf46ccd31
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0ecb05dba70dc9c8aba7f04928fd0ab49c900c8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125584"
---
# <a name="reportavoncomrelease-mda"></a>Помощник по отладке управляемого кода reportAvOnComRelease
Помощник отладки управляемого кода (MDA) `reportAvOnComRelease` активируется при возникновении исключений, вызванных ошибками подсчета пользовательских ссылок при выполнении COM-взаимодействия и использовании метода <xref:System.Runtime.InteropServices.Marshal.Release%2A> или <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> в сочетании с необработанными вызовами COM.  
  
## <a name="symptoms"></a>Симптомы  
 Нарушения прав доступа и повреждение памяти.  
  
## <a name="cause"></a>Причина  
 Иногда исключение возникает в связи с ошибками подсчета пользовательских ссылок при выполнении COM-взаимодействия и использовании метода <xref:System.Runtime.InteropServices.Marshal.Release%2A> или <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> в сочетании с необработанными вызовами COM. Обычно это исключение отменяется, так как в противном случае в среде CLR произойдет нарушение прав доступа, и работа среды будет завершена. Когда этот помощник включен, такие исключения вместо простой отмены можно обнаруживать и выводить в отчетах.  
  
## <a name="resolution"></a>Решение  
 Изучите свой код подсчета ссылок для поиска ошибок и проверки собственных клиентов объекта на наличие ошибок подсчета ссылок.  
  
## <a name="effect-on-the-runtime"></a>Влияние на среду выполнения  
 Доступно два режима. Если атрибут `allowAv` имеет значение `true`, помощник запрещает среде выполнения отменить нарушение прав доступа. Если `allowAv` имеет значение `false`, которое используется по умолчанию, среды выполнения отменяет нарушение прав доступа, однако пользователь получает предупреждение о возникновении и отмене исключения.  
  
## <a name="output"></a>Вывод  
 Когда это возможно, выходные данные содержат исходный vtable указателя интерфейса COM. В противном случае отображается информационное сообщение.  
  
## <a name="configuration"></a>Параметр Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>См. также

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Диагностика ошибок посредством управляемых помощников по отладке](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Маршалинг взаимодействия](../../../docs/framework/interop/interop-marshaling.md)
