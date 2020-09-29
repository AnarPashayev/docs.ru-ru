---
title: Использование вариативности в делегатах (C#)
description: Узнайте, как использовать вариативность в делегатах с помощью приведенных примеров кода ковариации и контрвариантности.
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 6704c3bf09dd854335f1e2719ccc8462cb7cde26
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176322"
---
# <a name="using-variance-in-delegates-c"></a>Использование вариативности в делегатах (C#)

При назначении метода делегату *ковариация* и *контравариантость* обеспечивают гибкость сопоставления типа делегата с сигнатурой метода. Ковариация позволяет методу иметь тип возвращаемого значения, степень наследования которого больше, чем указано в делегате. Контравариантность позволяет использовать метод с типами параметров, степень наследования которых меньше, чем у типа делегата.  
  
## <a name="example-1-covariance"></a>Пример 1. Ковариантность  
  
### <a name="description"></a>Описание  

 В этом примере демонстрируется использование делегатов с методами, типы возвращаемых значений которых являются производными от типа возвращаемого значения в сигнатуре делегата. Тип данных, возвращаемый `DogsHandler`, является типом `Dogs`, производным от определенного в делегате типа `Mammals`.  
  
### <a name="code"></a>Код  
  
```csharp  
class Mammals {}  
class Dogs : Mammals {}  
  
class Program  
{  
    // Define the delegate.  
    public delegate Mammals HandlerMethod();  
  
    public static Mammals MammalsHandler()  
    {  
        return null;  
    }  
  
    public static Dogs DogsHandler()  
    {  
        return null;  
    }  
  
    static void Test()  
    {  
        HandlerMethod handlerMammals = MammalsHandler;  
  
        // Covariance enables this assignment.  
        HandlerMethod handlerDogs = DogsHandler;  
    }  
}  
```  
  
## <a name="example-2-contravariance"></a>Пример 2: Контрвариантность  
  
### <a name="description"></a>Описание

В этом примере демонстрируется использование делегатов с методами, параметры типа которых являются базовыми типами типа параметра сигнатуры делегата. Контравариантность позволяет использовать один обработчик событий вместо нескольких. В следующем примере используется два делегата:

- Делегат <xref:System.Windows.Forms.KeyEventHandler>, определяющий сигнатуру события [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown). Его сигнатура:

   ```csharp
   public delegate void KeyEventHandler(object sender, KeyEventArgs e)
   ```

- Делегат <xref:System.Windows.Forms.MouseEventHandler>, определяющий сигнатуру события [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown). Его сигнатура:

   ```csharp
   public delegate void MouseEventHandler(object sender, MouseEventArgs e)
   ```

В примере определяется обработчик событий с параметром <xref:System.EventArgs>, который используется для обработки событий `Button.KeyDown` и `Button.MouseClick`. Это можно сделать, поскольку <xref:System.EventArgs> является базовым типом <xref:System.Windows.Forms.KeyEventArgs> и <xref:System.Windows.Forms.MouseEventArgs>.
  
### <a name="code"></a>Код  
  
```csharp  
// Event handler that accepts a parameter of the EventArgs type.  
private void MultiHandler(object sender, System.EventArgs e)  
{  
    label1.Text = System.DateTime.Now.ToString();  
}  
  
public Form1()  
{  
    InitializeComponent();  
  
    // You can use a method that has an EventArgs parameter,  
    // although the event expects the KeyEventArgs parameter.  
    this.button1.KeyDown += this.MultiHandler;  
  
    // You can use the same method
    // for an event that expects the MouseEventArgs parameter.  
    this.button1.MouseClick += this.MultiHandler;  
  
}  
```  
  
## <a name="see-also"></a>См. также

- [Вариативность в делегатах (C#)](./variance-in-delegates.md)
- [Использование вариативности в универсальных методах-делегатах Func и Action (C#)](./using-variance-for-func-and-action-generic-delegates.md)
