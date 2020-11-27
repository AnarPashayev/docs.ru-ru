---
title: Помощник по отладке управляемого кода invalidVariant
description: Ознакомьтесь с помощником по отладке управляемого кода Инвалидвариант, который вызывается при обнаружении недопустимого варианта в вызове из машинного или неуправляемого в управляемый код.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
ms.openlocfilehash: f0667a54e950ead27000eb6b93ebd547dea1cfb0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281304"
---
# <a name="invalidvariant-mda"></a>Помощник по отладке управляемого кода invalidVariant

Помощник по отладке управляемого кода (MDA) `invalidVariant` активируется, когда во время вызова из машинного или неуправляемого кода обнаруживается недопустимая структура `VARIANT`.  
  
## <a name="symptoms"></a>Симптомы  

 Непредвиденное поведение во время перехода между машинным и управляемым кодом, включающего маршалинг `VARIANT` к объекту.  
  
## <a name="cause"></a>Причина:  

 Машинный код передает в управляемый код структуру `VARIANT` неправильного формата.  Среда выполнения пытается выполнить маршалинг этой структуры `VARIANT` в объект и активирует MDA, если `VARIANT` является недопустимой. Примеры недопустимых структур `VARIANT` включают `VARIANT` с `VARTYPE` VT_EMPTY | VT_BYREF или `VARIANT` с `VARTYPE` VT_VARIANT.  
  
## <a name="resolution"></a>Разрешение  

 Машинный или неуправляемый код, передающий `VARIANT`, должен убедиться, что структура `VARIANT` правильно сформирована и инициализирована.  
  
## <a name="effect-on-the-runtime"></a>Влияние на среду выполнения  

 MDA не оказывает влияния на поведение среды выполнения.  
  
## <a name="output"></a>Выходные данные  

 Сообщение MDA, указывающее, что среда выполнения обнаружила недопустимую структуру `VARIANT`, переданную в управляемый код неуправляемым модулем.  
  
## <a name="configuration"></a>Конфигурация  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>См. также

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Диагностика ошибок посредством управляемых помощников по отладке](diagnosing-errors-with-managed-debugging-assistants.md)
- [Маршалинг взаимодействия](../interop/interop-marshaling.md)
