---
title: virtualCERCall MDA
description: Ознакомьтесь с помощником по отладке управляемого кода Виртуалцеркалл (MDA), который вызывается, если CER содержит вызов виртуального метода, который не может быть подготовлен автоматически.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- virtualCERCall MDA
- virtual CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: 1eb18c7a-f5e0-443f-80fb-67bfbb047da2
ms.openlocfilehash: c3e8060702239c6f87659f48658160e46491542f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257097"
---
# <a name="virtualcercall-mda"></a>virtualCERCall MDA

Помощник по отладке управляемого кода (MDA) `virtualCERCall` активируется как предупреждение, указывающее на то, что точка вызова в графе вызовов для области ограниченного выполнения (CER) относится к виртуальному целевому объекту, то есть к виртуальному вызову неконечного виртуального метода или к вызову с помощью интерфейса. Среда CLR не может спрогнозировать конечный метод этих вызовов только на основании промежуточного языка и анализа метаданных. В результате дерево вызовов невозможно подготовить как часть графа CER и прерывания потока в этом поддереве невозможно блокировать автоматически. Этот помощник по отладке управляемого кода предупреждает о случаях, когда CER требуется расширить с помощью явных вызовов метода <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>, если дополнительные сведения, требуемые для вычисления целевого объекта вызова, известны во время выполнения.  
  
## <a name="symptoms"></a>Симптомы  

 Области CER, которые не выполняются при прерывании потока или при выгрузке домена приложения.  
  
## <a name="cause"></a>Причина:  

 CER содержит вызов виртуального метода, который не удается подготовить автоматически.  
  
## <a name="resolution"></a>Разрешение  

 Следует вызвать <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> для виртуального метода.  
  
## <a name="effect-on-the-runtime"></a>Влияние на среду выполнения  

 Этот помощник отладки управляемого кода не оказывает никакого влияния на среду CLR.  
  
## <a name="output"></a>Выходные данные  
  
```output
Method 'MethodWithCer', while executing within a constrained execution region, makes a call  
at IL offset 0x0024 to 'VirtualMethod', which is virtual and cannot be prepared automatically  
at compile time. The caller must ensure this method is prepared explicitly at  
runtime before entering the constrained execution region.  
method name="VirtualMethod"  
declaringType name="VirtualCERCall+MyClass"  
  declaringModule name="mda"  
    callsite name="MethodWithCer" offset="0x0024"  
```  
  
## <a name="configuration"></a>Конфигурация  
  
```xml  
<mdaConfig>  
  <assistants>  
    <VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Пример  
  
```csharp
class MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    virtual void VirtualMethod()  
    {  
        ...  
    }  
}  
  
class MyDerivedClass : MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    override void VirtualMethod()  
    {  
        ...  
    }  
}  
  
void MethodWithCer(MyClass object)  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    try  
    {  
        ...  
    }  
    finally  
    {  
        // Start of the CER.  
  
        // Cannot tell at analysis time whether object is a MyClass  
        // or a MyDerivedClass, so we do not know which version of
        // VirtualMethod we are going to call.  
        object.VirtualMethod();  
    }  
}  
```  
  
## <a name="see-also"></a>См. также

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Диагностика ошибок посредством управляемых помощников по отладке](diagnosing-errors-with-managed-debugging-assistants.md)
- [Маршалинг взаимодействия](../interop/interop-marshaling.md)
