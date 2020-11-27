---
title: memberInfoCacheCreation MDA
description: Изучите помощник по отладке управляемого кода (MDA) Мемберинфокачекреатион в .NET, который активируется при создании кэша MemberInfo.
ms.date: 03/30/2017
helpviewer_keywords:
- member info cache creation
- MemberInfoCacheCreation MDA
- reflection, run-time errors
- MDAs (managed debugging assistants), cache
- cache [.NET Framework], reflection
- managed debugging assistants (MDAs), cache
- MemberInfo cache
ms.assetid: 5abdad23-1335-4744-8acb-934002c0b6fe
ms.openlocfilehash: 44d279a949ca0b35c46f805e65eb6f61ffb532f1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271165"
---
# <a name="memberinfocachecreation-mda"></a>memberInfoCacheCreation MDA

Помощник по отладке управляемого кода (MDA) `memberInfoCacheCreation` запускается при создании кэша <xref:System.Reflection.MemberInfo>. Это явный признак программы, в которой используются ресурсоемкие функции отражения.  
  
## <a name="symptoms"></a>Симптомы  

 Рабочий набор программы увеличивается, так как в программе используются ресурсоемкие функции отражения.  
  
## <a name="cause"></a>Причина:  

 Операции отражения, которые включают объекты <xref:System.Reflection.MemberInfo>, считаются ресурсоемкими, так как они должны считывать метаданные, которые хранятся на "холодных" страницах. Обычно эти операции означают, что в программе используется какой-либо сценарий позднего связывания.  
  
## <a name="resolution"></a>Разрешение  

 Чтобы определить, в какой точке программы используется отражение, можете включить этот помощник по отладке управляемого кода и запустить код в отладчике или подключиться к отладчику при запуске помощника по отладке управляемого кода. В отладчике появится трассировка стека, в которой будет показано место создания кэша <xref:System.Reflection.MemberInfo>. Так вы сможете определить, в какой точке программы используется отражение.  
  
 Способ решения задачи зависит назначения кода. Этот помощник по отладке управляемого кода предупреждает о том, что в программе используется сценарий позднего связывания. Вы сможете решить, следует ли заменить его на сценарий раннего связывания или сохранить сценарий позднего связывания, так как он обладает достаточной производительностью.  
  
## <a name="effect-on-the-runtime"></a>Влияние на среду выполнения  

 Этот помощник по отладке управляемого кода запускается каждый раз при создании кэша <xref:System.Reflection.MemberInfo>. Влияние на производительность незначительно.  
  
## <a name="output"></a>Выходные данные  

 Помощник по отладке управляемого кода выводит сообщение о создании кэша <xref:System.Reflection.MemberInfo>. Используйте отладчик, чтобы получить трассировку стека, в которой будет показано, где в программе используется отражение.  
  
## <a name="configuration"></a>Конфигурация  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Пример  

 При выполнении кода в этом примере будет запущен помощник по отладке управляемого кода `memberInfoCacheCreation`.  
  
```csharp
using System;  
  
public class Exe  
{  
    public static void Main()  
    {  
        typeof(object).GetMethods();  
    }  
}  
```  
  
## <a name="see-also"></a>См. также

- <xref:System.Reflection.MemberInfo>
- [Диагностика ошибок посредством управляемых помощников по отладке](diagnosing-errors-with-managed-debugging-assistants.md)
