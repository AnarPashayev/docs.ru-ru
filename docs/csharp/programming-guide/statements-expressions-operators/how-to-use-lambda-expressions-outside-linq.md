---
title: Практическое руководство. Использование лямбда-выражений вне LINQ (Руководство по программированию на C#)
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
ms.openlocfilehash: c66dea393ad2351402f54b2391d424701208eba2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619825"
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a><span data-ttu-id="9dae7-102">Практическое руководство. Использование лямбда-выражений вне LINQ (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="9dae7-102">How to: Use Lambda Expressions Outside LINQ (C# Programming Guide)</span></span>
<span data-ttu-id="9dae7-103">Лямбда-выражения не ограничиваются запросами [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9dae7-103">Lambda expressions are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="9dae7-104">Их можно использовать везде, где ожидается значение делегата, т. е. там, где можно использовать анонимный метод.</span><span class="sxs-lookup"><span data-stu-id="9dae7-104">You can use them anywhere a delegate value is expected, that is, wherever an anonymous method can be used.</span></span> <span data-ttu-id="9dae7-105">В представленном ниже примере показано, как использовать лямбда-выражение в обработчике событий Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="9dae7-105">The following example shows how to use a lambda expression in a Windows Forms event handler.</span></span> <span data-ttu-id="9dae7-106">Обратите внимание на то, что типы входных данных (<xref:System.Object> и <xref:System.Windows.Forms.MouseEventArgs>) выводятся компилятором и не требуют прямого указания параметров лямбда-выражений.</span><span class="sxs-lookup"><span data-stu-id="9dae7-106">Notice that the types of the inputs (<xref:System.Object> and <xref:System.Windows.Forms.MouseEventArgs>) are inferred by the compiler and do not have to be explicitly given in the lambda input parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9dae7-107">Пример</span><span class="sxs-lookup"><span data-stu-id="9dae7-107">Example</span></span>  
  
```csharp  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
       this.Click += (s, e) => { MessageBox.Show(((MouseEventArgs)e).Location.ToString());};  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="9dae7-108">См. также</span><span class="sxs-lookup"><span data-stu-id="9dae7-108">See also</span></span>

- [<span data-ttu-id="9dae7-109">Лямбда-выражения</span><span class="sxs-lookup"><span data-stu-id="9dae7-109">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="9dae7-110">Анонимные методы</span><span class="sxs-lookup"><span data-stu-id="9dae7-110">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
- [<span data-ttu-id="9dae7-111">Синтаксис LINQ</span><span class="sxs-lookup"><span data-stu-id="9dae7-111">Language Integrated Query (LINQ))</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
