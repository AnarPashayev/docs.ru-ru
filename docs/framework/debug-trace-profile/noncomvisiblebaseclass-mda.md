---
title: nonComVisibleBaseClass MDA
ms.date: 03/30/2017
helpviewer_keywords:
- visible classes
- managed debugging assistants (MDAs), COM visible classes
- nonComVisibleBaseClass MDA
- COM visible classes
- QueryInterface call failures
- MDAs (managed debugging assistants), COM visible classes
ms.assetid: 9ec1af27-604b-477e-9ee2-e833eb10d3ce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb0810a9e0ffce825abecc87eb2698920209d86f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59171812"
---
# <a name="noncomvisiblebaseclass-mda"></a>nonComVisibleBaseClass MDA
Помощник по отладке управляемого кода (MDA) `nonComVisibleBaseClass` активируется при вызове `QueryInterface` машинным или управляемым кодом в вызываемой оболочке COM (CSW) видимого для COM управляемого класса, производного от базового класса, невидимого для COM.  Вызов `QueryInterface` приводит к активации MDA только в тех случаях, когда вызов запрашивает интерфейс класса или `IDispatch` по умолчанию управляемого класса, видимого для COM.  MDA не активируется, когда `QueryInterface` предназначен для явного интерфейса, который имеет примененный атрибут <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> и явно реализован классом, видимым для COM.  
  
## <a name="symptoms"></a>Симптомы  
 Вызов `QueryInterface` выполняется из машинного кода, в котором произошел сбой со значением COR_E_INVALIDOPERATION HRESULT.  Значение HRESULT может возникнуть из-за того, что среда выполнения не разрешает вызовы `QueryInterface`, которые активируют данный MDA.  
  
## <a name="cause"></a>Причина  
 Среда выполнения не может разрешить вызовы `QueryInterface` интерфейса класса или интерфейса `IDispatch` по умолчанию видимого для COM класса, производного от класса, невидимого для COM, из-за потенциальных проблем управления версиями.  Например, если какие-либо открытые члены были добавлены в базовый класс, невидимый для COM, то существующие клиенты COM, использующие производный класс, могут прерваться, поскольку виртуальная таблица производного класса, содержащая члены базового класса, будет изменена в результате такой модификации.  Явные интерфейсы, предоставляемые в COM, не имеют таких проблем, так как они не включают базовые члены интерфейсов в виртуальной таблице.  
  
## <a name="resolution"></a>Решение  
 Не предоставляйте интерфейс класса. Определите явный интерфейс и примените к нему атрибут <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.  
  
## <a name="effect-on-the-runtime"></a>Влияние на среду выполнения  
 Этот помощник отладки управляемого кода не оказывает никакого влияния на среду CLR.  
  
## <a name="output"></a>Вывод  
 Далее приводится пример сообщения для вызова `QueryInterface` в видимом для COM классе `Derived`, производном от невидимого для COM класса `Base`.  
  
```  
A QueryInterface call was made requesting the class interface of COM   
visible managed class 'Derived'. However since this class derives from   
non COM visible class 'Base', the QueryInterface call will fail. This   
is done to prevent the non COM visible base class from being   
constrained by the COM versioning rules.   
```  
  
## <a name="configuration"></a>Параметр Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>См. также

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Диагностика ошибок посредством помощников по отладке управляемого кода](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Маршалинг взаимодействия](../../../docs/framework/interop/interop-marshaling.md)
